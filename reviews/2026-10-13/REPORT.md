# Lesson Review: Tax Max Affiliate Hub

**Date:** 2026-10-13
**Scope:** all 52 TrainingModules, 380 TrainingSlides, 50 Quizzes and 351 QuizQuestions in the Base44 app *Tax Max Affiliate Hub*. Marketing-only modules 41 and 42 were not reviewed for tax content.
**Method:** each module was checked against the 10-section lesson standard, the tax-year labelling rule, the no-line-number-quiz rule and the closing-remarks rule. Facts were checked against current IRS sources: IRC, regulations, form instructions, publications, Rev. Proc. 2024-40, Rev. Proc. 2025-32, and IRS.gov pages.
**Read-only:** nothing in Base44 was changed.

Detailed findings for each batch are in `findings_A.md` through `findings_F.md`.

| Batch | Topics | HIGH | MEDIUM | LOW |
|---|---|---|---|---|
| A | Credentials, ethics, due diligence, retention, preparer penalties | 3 | 15 | 8 |
| B | Filing status, dependents, filing requirements, credits | 2 | 19 | 20 |
| C | Form 1040, income documents, deductions, Schedule C, software | 2 | 18 | 16 |
| D | Sections 7–11 + **published Final Exam** | 0 | 12 | 9 |
| E | OBBB deductions (seniors/tips/overtime), adoption & less-common credits, 2026 brackets, IRA | 0 | 19 | 13 |
| F | Extensions, notices, injured/innocent spouse, payment plans, QC, data security, ERO, drafts | 2 | ~24 | ~12 |
| **Total** | | **9** | **~107** | **~78** |

Most dollar figures checked were **correct for the year they name**, including the 2025 EITC/CTC amounts, the 2025 and 2026 standard deductions, the 2026 brackets, §6695 amounts by filing year, IRA limits and installment-agreement fees. The problems are mostly wrong rules, missing tax-year labels, missing TY2026 changes, and structure.

---

## 1. HIGH: wrong rules students could rely on (fix first)

Each item below was confirmed against the exported lesson text.

| # | Module | Location | What it says | Correct rule | Source |
|---|---|---|---|---|---|
| 1 | 6, Dependents | Quiz Q4 `6a9724476ebc0245b90284b1` (answer key), slides 6–7, description | Tiebreaker: "The parent, then higher AGI, then **closeness of relationship**" | There is no "closeness of relationship" rule. A parent beats a non-parent. Between two parents, the child goes to the parent the child lived with longer; AGI decides only when time is equal. If no parent can claim the child, highest AGI wins. A non-parent can claim only with AGI above every eligible parent's. | Pub 501 |
| 2 | 6, Dependents | Slide 7 scenario `…cd9b` | Asks who claims the child (lived 9 months with client), gives no answer, and points students to AGI | The custodial parent claims the child. The noncustodial parent can claim the child as a dependent and take the CTC/ACTC/ODC **only with a signed Form 8332**. HOH, EITC and the dependent care credit never transfer. Divorce decrees executed after 2008 cannot substitute for Form 8332. | Pub 501 |
| 3 | 8, Income Docs | Slide 105 `6aa6a78168a670f9442dcde0` | 1099-K: "It belongs in Schedule C receipts" | Classify each payment by the activity that produced it. Personal items sold at a loss, payments that are not income, rental income and hobby income do not go on Schedule C. | IRS "Understanding your Form 1099-K" |
| 4 | 11, Schedule C | Quiz Q2 `6aae914228201c47723bdb19` | "Commuting miles are ever deductible…", keyed **No** | Commuting is not deductible, but the Pub 463 exceptions apply: a home office that is the principal place of business, and temporary work locations. The module's own slides teach this. | Pub 463 |
| 5 | 14, IRS Letters | Quiz Q4 `6aae9186fa9e0e4fcb60cb27` and description | "Form 2848 lets a preparer represent a client" | A preparer with only a PTIN has **no** representation rights. An AFSP Record holder may represent only on returns they prepared **and signed**, before examination, customer service and the Taxpayer Advocate Service, never before Appeals or Collection. Teach Form 8821 for receiving information. | IRS credentials page; Form 2848 instructions |
| 6 | 15, Audit & QC | Description, objective, Quiz Q4 | "use Form 2848 to represent the client" | Same as #5. | Same as #5 |
| 7 | 3, Ethics | Description, slide 2, objective | "§10.20/10.21 — return client records" | Returning client records is **§10.28**. §10.20 covers responding to IRS requests; §10.21 covers advising the client of errors. | Circular 230 |
| 8 | 3, Ethics | Description, slide 4 | "§10.34 … **realistic possibility** standard" | That standard was removed in the 2011 revisions. Current §10.34(a) uses reasonable basis and unreasonable position (§6694(a)(2)). | Circular 230; The Tax Adviser, Jan 2012 |
| 9 | 4, Due Diligence | Quiz Q3 `6aae9068b458eadc5b5b35bd` | Keyed "**Per return** for a due-diligence failure" | The §6695(g) penalty is **per failure**, and one return can have up to 4 failures: $650 each for returns filed in 2026, up to $2,600 per return. The lesson's own text says "each failure". | Form 8867 instructions; Rev. Proc. 2024-40 |

---

## 2. Problems across many modules

### 2.1 Closing-remarks rule: fails everywhere
**No module's closing or key-takeaways slide includes all three required items.** Most say only "Next: read the Full Lesson Notes … then take the final exam." Several modules have no closing slide at all (0, 2, 3, 4, 6, 8, 11, 16.1).

Suggested standard closing text for every lesson:

> **Does anyone have any questions?**
> If you need more help, open the **portal → Lessons**, scroll down, and describe the lesson or topic you need help with.
> Use the **demo environment** to practice what we covered today.

### 2.2 TY2026 changes not flagged (law changes by tax year)

| Topic | TY2025 | TY2026 (or the change) | Modules affected |
|---|---|---|---|
| AOTC/LLC identification | SSN, ITIN or ATIN | **SSN valid for work** required for the taxpayer (or the spouse on MFJ) and a dependent student | 4, 7.4, 9, 32, 40 |
| CTC taxpayer SSN | **New in TY2025:** the taxpayer (one spouse on MFJ) must have a valid SSN | Continues | 6, 24, 7.4 |
| Child & dependent care credit | 20–35% of $3,000/$6,000; $5,000 dependent care FSA exclusion | Up to **50%**, with a new phase-down; **$7,500** dependent care FSA exclusion | 9, 25, 40 |
| Premium tax credit | 400% FPL limit suspended; repayment caps apply | 400% FPL limit **returns**; **no repayment cap** | 9 |
| SALT cap | $40,000 ($20,000 MFS), reduced above $500k MAGI, $10k floor | $40,400; threshold $505,000 | 10, 26, 40 |
| Standard deduction | $15,750 / $31,500 / $23,625 | $16,100 / $32,200 / $24,150 | 5, 26, 40 |
| EITC maximum (3+ children) | $8,046 | $8,231 | 9, 23, 7.4 |
| Educator expense | $300 | $350 | 25.5 |
| Adoption credit | $17,280; $5,000 refundable | $17,670; $5,120 refundable | 25.5, 27 |
| Gambling losses | Up to winnings | Limited to **90%** | 8, 10 |
| Charitable | — | 0.5%-of-AGI floor for itemizers; $1,000/$2,000 deduction for non-itemizers | 10, 7.3 |
| Mileage | 70¢ | 72.5¢ (verify the mid-year change reported for July 2026) | 11, 40 |
| SE wage base | $176,100 | $184,500 | 11, 40 |
| §6695(g) penalty | $635 (filed 2025) / **$650 (filed 2026)** | $665 (filed 2027) | 4, 32, 7.4 |
| 1099-NEC/MISC threshold | $600 | $2,000 (payments after 2025) | 8, 11 |
| Tips/overtime reporting | Transition relief (overtime: one-third method) | W-2 box 12 codes **TP** / **TT** | 29, 30 |
| Schedule 1-A deductions | — | Temporary, **2025–2028 only**; not labelled as temporary | 10, 26, 27, 36/40 |

### 2.3 Due diligence is missing or thin in most modules
Nearly every non-due-diligence module leaves out how preparers are expected to verify and document a claim. Even the due-diligence modules have errors:
- Modules 32 and 34 list **4 records**; the Form 8867 instructions list **5**.
- Module 32 says the retention period starts at one date "or" another; it actually runs 3 years from the **latest** of the listed dates.

### 2.4 Quiz quality
- **Published quizzes:** only 2 of 50 are published, the **Final Exam** (7.4) and the **Oct. 6 recap** (13.5). The rest are unpublished or archived, so most lessons have no live quiz.
- **Final Exam:**
  - All 50 answer keys are correct.
  - The correct answer is **option B in 42 of 50 questions**, and the longest option in 43 of 50. Unless the portal shuffles options, students can score about 84% by picking B.
  - About 25 questions have joke distractors.
- **Module 40's exam** copies the Final Exam word for word and does not test the deck.
- **Line-number memorization:** no question asks for a Form 1040 line number outright. However, these are the same kind of rote recall:
  - box/code/form/section recall (Module 7 knowledge check and Q5; Module 8 Q1 and Q4; Module 11 Q4 and Q5; Module 15 Q5; Module 27 Q4 and Q5; Module 33 publication number; Module 34 "6695(d)");
  - two line-location learning objectives (Modules 23 and 24).

  Each findings file proposes a scenario-based replacement.
- **Explanations:** blank in Modules 2, 3, 4, 11, 12, 13, 14, 14.1, 14.2, 15 and 16.1. Elsewhere they mostly repeat the answer.

### 2.5 Missing lesson sections (10-section standard)
No module meets all 10. The most commonly missing sections are:
- common preparer mistakes
- due-diligence requirements
- practice scenario with a model answer
- answer explanations

**Module 16.1 (IRA Contributions)** is *Approved* but has **no slides**.

---

## 3. Priority fix list

1. **Fix the 9 HIGH items** in section 1, especially the Module 6 tiebreaker answer key and the Form 2848 representation statements.
2. **Rebalance the published Final Exam:** shuffle answer positions, replace joke distractors, and add explanations that cite the IRS rule.
3. **Add the standard closing** (questions, portal → Lessons, demo environment) to every lesson.
4. **Add TY2026 callouts** from the table in 2.2, starting with AOTC SSN, the child and dependent care credit, the PTC, SALT and the Schedule 1-A sunset.
5. **Due-diligence modules (4, 32, 34):** use 5 records, the "latest of" date rule, penalty amounts by filing year, firm liability, and include the AOTC.
6. **Module 3 Circular 230 fixes:** §10.28, current §10.34, §10.50 sanctions, §10.23 wording, and who Circular 230 binds.
7. **Fill in the blank quiz explanations**, and replace recall questions with the scenario questions proposed in the findings files.
8. **Build out or unpublish** Module 16.1 (no slides). Retire Module 40's duplicate exam.
9. **Smaller corrections:**
   - Module 8: K-1 income never goes on Schedule C.
   - Module 12: add Form 8879 to the workflow.
   - Module 13: remove the stale "Keep Draft" note.
   - Module 29: the tips cap is $25,000 **per return**.
   - Modules 28–30: add phase-out rates.

---

## 4. Items reviewers could not fully confirm on irs.gov (verify before publishing)
- TY2026 CTC/ACTC amounts ($2,200/$1,700) and the TY2026 qualifying-relative gross-income limit ($5,300). Secondary sources cite Rev. Proc. 2025-32.
- The mid-2026 mileage change to 76¢.
- TY2026 educator-expense itemizing rules.
- AFSP 10/2-hour CE split.
- Exact §10.34(a) and §10.50(a) wording.
