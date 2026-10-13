# Business System 360: iOS release report (2026-10-13)

**Status: NOT READY TO SUBMIT.** Only Apple can approve the app. Nothing here was submitted, published, merged or charged, and no customer was contacted.

| Item | Value |
|---|---|
| App | Base44 "Business System 360" (`6ab05c7ef41997717fcc898a`) |
| Branch | `app-store-remediation-2026-10-13` (`6ace3319806ab7fbc60714c3`); main and the live site are untouched |
| Checkpoint | `6ace432f78b221eac971ad08` (commit `720d0d3`), base `c79a1e7` |
| Size | 93 files changed |

## How to read the evidence column

| Code | Meaning |
|---|---|
| **U** | Unit/mock: the real source run against fakes (`tests/security/remediation-functions.test.mjs`, `tests/app-store/ios-store-policy.test.mjs`) |
| **E** | Emulated iOS: the built native bundle served from a non-Base44 origin, with Capacitor's iOS signal injected, in headless Chromium, against the **real** Base44 backend (`tests/native-e2e/`). This is not the Simulator. |
| **L** | Live backend call with synthetic accounts |
| **S** | Provider sandbox (Apple StoreKit / App Store Connect) |
| **D** | Simulator or device |
| **P** | Production |

Nothing has reached **S**, **D** or **P** yet. Those need a Mac, App Store Connect access and your release approval.

Statuses:
- **FIXED:** the code is changed and checked at the levels named.
- **VERIFIED:** the result was observed at a live level (L/E).
- **BLOCKED:** needs a person or access I don't have.
- **NOT RUN:** the test exists but couldn't run here.

## Release-blocking items, highest risk first

| # | Finding | Status | Evidence | Remaining dependency → next action |
|---|---|---|---|---|
| 1 | The iOS bundle can't reach the backend (empty `serverUrl`, `preview` functions, `iosScheme: 'https'`) | **FIXED / VERIFIED (E)** · Simulator **NOT RUN** | See "Native connectivity" below | Mac owner: `docs/IOS_BUILD_AND_DEVICE_TEST.md` §1–2 |
| 2 | A web buildout purchase unlocked the subscription workspace (3.1.1) | **FIXED** (U) | Static test + code | None. On merge, buildout-only customers see the intake only |
| 3 | iOS showed web offers, web trials, web pricing and "card is charged" text (3.1.1, 3.1.2) | **FIXED / VERIFIED (E)** | Journeys J2, J3 ×6, J4 | None |
| 4 | Subscription disclosures, live price, period, EULA, Apple cancellation, trial eligibility | **FIXED** (U, E: copy). StoreKit **NOT RUN** | J4 screenshot; unit tests on price/trial formatting | App Store Connect products and intro offer → owner; sandbox journeys → Mac |
| 5 | Account deletion only created a request; unpaid users couldn't reach it | **FIXED.** Request **VERIFIED (L/E)**; executor **U**; live execution **BLOCKED** | See "Account deletion" below | **Owner (admin)** runs Inventory → Delete for `taxmaxsoftware+bs360e2e02@gmail.com` on the branch preview's Admin → Account deletions, then purges the trash |
| 6 | Third-party AI sharing without disclosure or consent (5.1.2(i)) | **FIXED.** UI **VERIFIED (E)**; server gate **U**; live gate **BLOCKED** | See "AI consent" below | Branch backend functions aren't deployed (see "Platform blocker"). Owner decision on AI training (below) |
| 7 | Privacy policy, App Privacy answers and privacy manifest incomplete | **FIXED** (U) | `docs/DATA_INVENTORY.md`; `app-privacy-draft.json`; manifest grows from 8 to 15 types (`plutil` parse OK) | Xcode privacy report from the archive → Mac. Privacy URL goes live only after publish |

## Native connectivity (#1)

**Before (E):** the old configuration sent every API call (`User/me`, `trackUsage` with `fv=preview`, and so on) to the local page origin. On a device that origin is the bundled file server, not Base44.

**After (E, 2026-10-13 13:38–13:40 UTC):** synthetic account A ran register → email OTP → verify → login, all inside the emulated iOS runtime (Google button hidden):

| Call | Result |
|---|---|
| `auth/register`, `auth/verify-otp`, `auth/login` | 200 |
| `entities/User/me` | 200 |
| `functions/trackUsage` (`fv=branch:…`) | 200 |
| `entities/CreatorMembership` | 200 |
| `Base44Purchase/v2/list` | 200 |

Every call went to `https://base44.app/api/...`.

**CORS (L):** preflight from `capacitor://localhost` returns 200 with `access-control-allow-origin: *`.

**Scheme:** Capacitor's documentation says `iosScheme` "can't be set to schemes that the WKWebView already handles, such as http or https" (capacitorjs.com/docs/config). It has been removed, so the default `capacitor://` applies.

**Credentials:** none in the app. The client uses only the user's session token, and a test enforces this.

**Files:** `src/lib/nativeRuntime.js`, `src/api/base44Client.js`, `capacitor.config.ts`, `vite.config.js` (page-view logger off in native builds), `package.json` (`native:build`).

## Account deletion (#5)

- **Request (L/E):** account B requested deletion from the landing page's Account link with no membership. Request `6ace3a4e…` was created with a target of 2026-11-12.
- **Inventory (L):** all 83 plan queries ran as B with no errors.
- **Executor (U):**
  - deletes only B's rows (another tenant's rows untouched) and B's posts and messages;
  - keeps Apple/PayPal records;
  - removes the user, marks the request completed and sends one confirmation email;
  - a non-admin gets 403; a missing `confirm` gets 400; a completed request can't be re-run.

**Files:**
- New: `base44/shared/accountDeletion.ts`, `base44/functions/fulfillAccountDeletion`, `src/components/admin/AccountDeletionManager.jsx`, `docs/ACCOUNT_DELETION_RUNBOOK.md`
- Changed: `requestAccountDeletion`, `AccountDeletion.jsx`, `LandingNav.jsx`, `ChallengeHub.jsx`, `AccountDeletionRequest.jsonc` (adds `account_email`; takes effect on merge)

## AI consent (#6)

**Providers:** OpenAI, Anthropic and Google, through Base44 (docs.base44.com/Community-and-support/ai-service-providers).

**UI (E):** off → dialog naming the providers and the training notice → Allow → on → off. "Not now" leaves AI off, and both buttons stay visible on a phone screen (a bug I fixed during this pass).

**Server (U):** all 9 AI functions return 403 `ai_consent_required` without current consent and never call the model. An outdated consent version also gets 403.

**Live (L):** on the branch, `improveFunnelCopy` still returned 200 without consent, because the branch backend is still running the old function code.

**Files:**
- New: `base44/shared/aiConsent.ts`, `src/lib/aiConsent.js`, `src/components/AiConsentDialog.jsx`
- Changed: 9 function entry files, `PostWriterAgentChat.jsx`, `AccountDeletion.jsx`, `base44Client.js`

## Other findings

| Finding | Status | Evidence | Next action |
|---|---|---|---|
| Fast Form "$20/month" vs "included" | iOS: **FIXED / VERIFIED (E)** (storefront gated; "included" copy shown). Web: **BLOCKED** on your decision | No $20 product exists in any catalog, checkout or IAP | **Owner:** keep $20 (then a product must be built) or remove it from the web page |
| Affiliate account credit | **FIXED** (page gated on iOS; web text says credit can't apply to Apple/Google subscriptions) | J3 | None |
| Feedback-for-trial reward | iOS: **FIXED / VERIFIED (E)** (no reward; "not an App Store rating"). Web reward and "Leave a review, get 7 more days" emails: **BLOCKED** on your decision | J8 | **Owner:** I recommend retiring the reward or renaming it "feedback" everywhere |
| Apple receipt verification hardening | **FIXED** (U) | Adds Apple marker-OID checks and certificate validity at signing time; invalid JWS → 400. Removed the 503 gate on unused secrets | Sandbox **NOT RUN** |
| OAuth return (Outlook / Drive / OneDrive) | **FIXED** (code): opens Safari, shows guidance, refreshes on return | **NOT RUN** (D) | Device check in `docs/IOS_BUILD_AND_DEVICE_TEST.md` §4 |
| Shared links used the WebView origin | **FIXED** (U): 10 call sites now use `https://businesssystem360.com` on native | Static test | Device check |
| Camera / file-picker permission strings | **FIXED** (`NSCameraUsageDescription`, `NSMicrophoneUsageDescription`) | **NOT RUN** (D) | Device check |
| Public user pages (1.2) | **FIXED** (U): blocked-language pages not served, Report link + support email on every page, admin takedown that owners can't undo, Content reports tab | Live report **BLOCKED** (function not deployed: J6 got 404) | Deploy, then re-run J6/J7 |
| Age rating answers | **FIXED** (draft): `messagingOrChat` true; AI/UGC notes | n/a | Answer Apple's questionnaire in App Store Connect |
| Support details | **FIXED**: one constant `support@businesssystem360.com`; the "one business day" wording kept | MX records show Google Workspace mail exists. Monitoring **NOT VERIFIED** | **Owner:** confirm someone monitors the inbox. A "Tax Max support" phone line remains on the BS360 Contact page; decide whether to keep it |
| Login for web Google users | **FIXED**: iOS login explains how to set a password via reset. Password recovery **VERIFIED (L)** | SDK reset → login OK | Reset emails link to `buildout.businesssystem360.com` → **owner** should set the app's primary domain |
| Internal docs claiming PASS | **FIXED**: correction banners on 3 docs pointing here | n/a | None |
| Synthetic accounts in analytics | **FIXED**: `+bs360e2e/+bs360review` or flag excluded from admin customer and revenue views | U | None |
| Tenant isolation | **VERIFIED (L)**: A can't read, get, update, delete or create B's CRM records (0 / 404 / 403 / 404 / 403); self-promotion to admin is refused (403) | `tests/native-e2e/server-checks.mjs` | None |

## Test results (final code, 2026-10-13)

| Suite | Result |
|---|---|
| `npm run test:release` (typecheck, build, lint, 16 suites, `npm audit`) | exit 0, 209 PASS lines, 0 vulnerabilities |
| `ios-store-policy` (new) | 12/12 |
| `remediation-functions` (new, U) | 34/34 |
| `security-fixes` | 133/133 |
| Forms, landing and marketing suites | all pass |
| Emulated-iOS journeys (E) | 14/15. J6 is blocked (function not deployed). J7 passed only because I had already unpublished that test page, so it doesn't count as evidence |
| Live server checks (L) | 6/6 isolation checks pass. The 4 function checks fail because the branch backend still runs the old code |
| `test:release:evidence` | 1/4 (Apple, live security and owner approval are BLOCKED), as intended |
| a11y lint | 110 errors, all pre-existing (identical on the base commit); none introduced |

## Platform blocker: branch backend functions

Base44 still serves the **pre-change** backend code for this branch. New functions return 404, and changed functions behave as before. The only deploy API ("Redeploy a backend function") writes to **main**, which would change what live automations run, so I didn't use it.

To get live evidence for #5, #6 and the public-page fixes, you need either:
- a Base44-supported branch deploy, or
- your approval to merge to main (without publishing) and re-run `tests/native-e2e/server-checks.mjs --with-ai` and `journeys.mjs`.

## Decisions only you can make

1. **AI training:** Base44 says data on non-Enterprise plans "can be used to train AI models", including personal information submitted through your app (docs.base44.com/Community-and-support/Privacy-and-security). The policy and consent dialog currently disclose this. The alternative is moving to Enterprise and removing that sentence.
2. Fast Form $20/month (keep and build, or remove).
3. Web "review = 7 more days" reward and emails.
4. The 24-hour content-removal target in the Terms. Can you staff it?
5. Whether the Terms of Use text (newly expanded, not legal advice) needs your counsel's review.

## Synthetic data created (production data store, all labeled)

| Item | State |
|---|---|
| Users `taxmaxsoftware+bs360e2e01` (A) and `…e2e02` (B) | Passwords in the sandbox only, not in any repo |
| B: 2 CrmContacts, 1 CrmTask, 1 MemberFeedback, 1 AccountDeletionRequest (open), 2 FunnelPages | Both pages now **unpublished** |
| A | 0 AI-consent fields set; 3 AI calls made during testing |

None of this appears in customer analytics after merge. The reviewer demo account was **not** created, because purchase and device flows aren't verified yet.

## Next actions, in order

1. **Owner:** approve the merge (or arrange a branch deploy) so the backend changes go live for testing. No publish yet.
2. **Agent, after that:** re-run live server checks and journeys (AI gate, report, takedown, IAP 400), then run the B deletion with you clicking Delete.
3. **Mac owner:** `docs/IOS_BUILD_AND_DEVICE_TEST.md`: Simulator login, then StoreKit sandbox journeys and device checks; record evidence in `release-evidence/apple-organization.json`.
4. **Owner (App Store Connect):**
   - create the products and confirm the price and intro offer;
   - set the Server Notifications V2 URL;
   - after publish, enter the privacy and support URLs;
   - answer the age rating questionnaire;
   - create the review account (`+bs360review`) in App Store Connect only.
5. **Owner:** release approval (`release-evidence/founder-release.json`), then publish and submit.
