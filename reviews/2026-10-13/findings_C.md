# Findings — Batch C (Modules 7, 8, 10, 11, 12, 26, 27)

**Totals:** 2 HIGH · 18 MEDIUM · 16 LOW

**Across the batch:**
- No quiz question asks for a Form 1040 line number outright. Several ask students to recall a box, code or form number from memory; these are listed under "Rote-recall replacements" below.
- None of the closing slides meets the a/b/c rule. Modules 8 and 11 have no closing slide at all.
- Due diligence is missing or weak in all 7 modules.
- All quizzes are unpublished. The quizzes for Modules 26 and 27 are ARCHIVED.
- Verified correct: the 2025 Form 1040 line references, the Schedule C expense lines, the TY2025 SALT limit, the additional standard deduction, the $400 SE threshold and 92.35% factor, and the 70¢ mileage rate for 2025.

## HIGH
1. **Module 8, slide 105** (6aa6a78168a670f9442dcde0), "It belongs in Schedule C receipts."
   - **Problem:** It says every 1099-K amount belongs on Schedule C. That is wrong, and it contradicts the module's own slide 7.
   - **Fix:** Classify each payment by the activity behind it:
     - business sales go on Schedule C;
     - personal items sold at a gain go on Form 8949 / Schedule D;
     - personal items sold at a loss, and payments that aren't income, follow IRS 1099-K guidance;
     - rents go on Schedule E;
     - hobby income is reported separately.
   - **Source:** https://www.irs.gov/businesses/understanding-your-form-1099-k
2. **Module 11, Q2** (6aae914228201c47723bdb19), "Commuting miles are ever deductible…", keyed "No."
   - **Problem:** The question is ungrammatical, and the absolute answer is wrong under Pub. 463.
   - **Fix:** Teach the exceptions: a home office that is the principal place of business, and temporary work locations.
   - **Source:** https://www.irs.gov/publications/p463

## MEDIUM
- **Module 8, slide 104:** "K-1s → Schedule E or C" is wrong. K-1 income goes to Schedule E Part II, Schedule B, Schedule D or Schedule SE, never Schedule C.
- **Module 8, year-specific changes:** add the information-return thresholds and the gambling-loss change.
  - From TY2026, gambling losses are limited to 90% (OBBBA §70114).
  - 1099-K: over $20,000 **and** over 200 transactions.
  - 1099-NEC/MISC: $600 for payments in 2025; $2,000 for payments after 2025.
- **Module 10, slide 104 (SALT):** add the TY2025 MAGI reduction (above $500,000 / $250,000 MFS, reduced by 30%, not below $10,000 / $5,000). Add TY2026: $40,400 ($20,200 MFS), threshold $505,000 ($252,500 MFS). The higher cap reverts to $10,000 in 2030.
- **Module 10, TY2026 changes not flagged:**
  - 0.5%-of-AGI floor on charitable deductions;
  - $1,000 / $2,000 charitable deduction for non-itemizers;
  - gambling losses limited to 90%;
  - casualty losses from state-declared disasters.
- **Module 11:** remove the unsourced claim that this is the "#1 IRS matching issue."
- **Module 11, missing figures:**
  - SE wage base: TY2025 $176,100; TY2026 $184,500.
  - QBI threshold: TY2025 $197,300 / $394,600.
  - Mileage: TY2026 is 72.5¢ for January–June, then 76¢ from July 1, 2026. Verify the 76¢ figure.
- **Module 12:** the workflow skips the signed Form 8879 that must be obtained before e-file (Pub. 1345). No tax year is set for the practice returns.
- **Module 26:** the Robert example (age 67) leaves out the $6,000 Schedule 1-A senior deduction for TY2025–2028. There are no TY2026 figures.
- **Module 27:** Schedule 1-A isn't flagged as temporary (2025–2028), and the caps are missing.
- **Module 7:** line numbers aren't labeled "2025 Form 1040." Due diligence is missing, and Q2–Q4 have no explanations.

## LOW (selected)
- **Module 7:** slide 105 (tax brackets) is empty.
- **Module 10:** the Q1 explanation should note the MFS rule: if one spouse itemizes, the other must too.
- **Module 11:** QBI is figured on Form 8995 but claimed on Form 1040 line 13a. Note the 0.9% Additional Medicare Tax.
- **Modules 26 and 27:** source links point to current-revision URLs. Use the irs-prior 2025 PDFs.

## Rote-recall replacements (box, code or form recall)
- **Module 7, knowledge check (W-2 box 2) and Q5 (which schedule for the CTC):** replace with withholding and ACTC scenarios.
- **Module 8, Q1 (W-2 box 1):** replace with a 401(k) deferral scenario (box 1 vs. boxes 3/5).
- **Module 8, Q4 (1099-R code 1):** replace with a scenario about Form 5329 exceptions.
- **Module 8, Q5:** the answer is obvious from the question. Replace with a scenario reconciling 1099-K, 1099-NEC and the client's books.
- **Module 11, Q4 (half of SE tax):** replace with a question on what that deduction actually reduces.
- **Module 11, Q5 (Form 8995):** replace with a QBI computation scenario.
- **Module 11, Q3:** use $380 of profit, which is below $400 after the 92.35% factor.
- **Module 27, Q4 (Schedule 1-A):** replace with a tips scenario showing the deduction reduces taxable income, not AGI.
- **Module 27, Q5:** replace with an ACTC refundability comparison.
- **Module 26:** add a computation question (MFJ, both 66, one blind → $36,300).

## Top 5 fixes
1. Module 8, slides 104–105: fix the 1099-K and K-1 errors.
2. Module 11, Q2: fix the commuting answer key.
3. All modules: add the a/b/c closing, and add closing slides to Modules 8 and 11.
4. Add year-labeled TY2026 figures (see MEDIUM above).
5. Replace the rote-recall questions and add Form 8879 to the Module 12 workflow.
