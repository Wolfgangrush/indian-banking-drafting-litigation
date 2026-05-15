---
name: sarfaesi-17-securitisation-application-draft
description: Draft a Securitisation Application (S.A.) under Section 17 of the SARFAESI Act 2002 before the Debts Recovery Tribunal, on behalf of a borrower / guarantor / mortgagor / aggrieved person challenging a measure taken by the secured creditor under Section 13(4) SARFAESI. Encodes the Section 17(1) standing rule, the 45-day limitation under Section 17(1) read with Rule 11 Security Interest (Enforcement) Rules 2002, the limited scope of DRT inquiry under Section 17(3) (whether the Section 13 / Rule 8 / Rule 9 procedure was followed; the quantum of debt is generally NOT re-adjudicated), and the Mardia Chemicals (2004) + Authorised Officer of UCO Bank (2009) discipline. Auto-fires on "draft SARFAESI SA", "draft Section 17 SA", "draft Securitisation Application", "challenge SARFAESI possession", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# SARFAESI Section 17 Securitisation Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: SECURITISATION APPLICATION UNDER SECTION 17 OF THE SARFAESI ACT 2002
case_short_code: SARFAESI_SA
case_number_prefix: S.A.
pleading_type: Securitisation Application
typical_forum: Debts Recovery Tribunal (territorial jurisdiction per Section 17(1) — DRT within whose local jurisdiction the secured asset is situated or the cause of action arose)
typical_parties: Applicant Borrower / Guarantor / Mortgagor / Aggrieved Person + Respondent Secured Creditor (Bank / NBFC / ARC) + Respondent Authorised Officer (Section 13(12)) + Respondent Buyer (in cases where sale has been confirmed)
statutory_opening: "This Securitisation Application is filed under Section 17 of the Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002, read with Rule 11 of the Security Interest (Enforcement) Rules 2002, against the measure taken by the Respondent Secured Creditor under Section 13(4) of the said Act, in respect of the Schedule of Secured Asset at Exhibit ___."
ground_clauses:
  - "Section 13(2) notice defects — the Notice dated ____ omitted the following statutory ingredients required under Section 13(2) read with the Mardia Chemicals (2004) 4 SCC 311 framework: [specify ingredient(s) omitted]."
  - "Section 13(3A) representation not considered — the Applicant's representation dated ____ was not considered by the Respondent and no reasons of non-acceptance were communicated within the 15-day window."
  - "Defective service — the Section 13(2) notice was served at an address that was not the Applicant's address on the records of the Respondent."
  - "Section 13(4) measure premature — the measure of taking possession on ____ was taken before the expiry of the 60-day window from the date of service of the Section 13(2) notice."
  - "Rule 8 procedural defects — the Possession Notice dated ____ did not comply with Rule 8(1) / Rule 8(2) (publication in two newspapers including local-language) / Rule 8(6) (notice to borrower); the Inventory Panchnama did not comply with Rule 8(3); valuation under Rule 8(5) was not obtained from a registered valuer / was vitiated by undervaluation."
  - "Rule 9 sale defects — the Sale Notice dated ____ did not comply with Rule 9(1) (30-day window); the reserve price did not reflect the registered valuer's report; the sale confirmation was vitiated by collusive bidding."
  - "NPA classification flawed — the classification of the account as NPA on ____ was contrary to the RBI Master Direction on IRAC 2021 (premature / on irregular grounds)."
  - "Quantum disputed (where Section 17(3) permits limited inquiry) — the secured debt has been overstated by the Respondent by inclusion of unilaterally applied penal interest / unilaterally re-calculated cost-of-funds rate."
prayer_clauses:
  - "(a) Set aside the Section 13(4) measure of taking possession of the Schedule of Secured Asset by the Respondent Secured Creditor on ____;"
  - "(b) Set aside the Sale Notice dated ____ / Sale Confirmation dated ____;"
  - "(c) Direct the Respondent Secured Creditor to restore possession of the Schedule of Secured Asset to the Applicant;"
  - "(d) Restrain the Respondent Secured Creditor from confirming any sale / from issuing any sale certificate / from delivering possession to any auction-purchaser pending disposal of this Application;"
  - "(e) Direct the Respondent Authorised Officer to consider the Applicant's Section 13(3A) representation in accordance with law and to communicate the reasons of non-acceptance, if any, within the 15-day window;"
mandatory_exhibits:
  - section_13_2_notice_received
  - section_13_3a_representation_filed_with_proof_of_service
  - non_consideration_communication_or_absence_thereof
  - possession_notice_under_rule_8
  - valuation_report_relied_on_by_secured_creditor
  - sale_notice_under_rule_9
  - applicants_response_correspondence
  - loan_account_statement_relied_on_by_applicant
  - npa_classification_advice_with_irac_2021_comparison
accompanying_applications:
  - "I.A. for stay of further measures / stay of sale confirmation / status-quo on possession (under Section 17(2) read with Section 17(3) SARFAESI)"
  - "I.A. for urgent listing where sale confirmation is imminent"
  - "I.A. for condonation of delay where the 45-day limitation under Section 17(1) read with Rule 11 has expired (with Section 5 Limitation Act invocation)"
court_fee: "Fee under Rule 13 of the Security Interest (Enforcement) Rules 2002 — slab fee linked to the secured-debt quantum disputed."
limitation: "45 days from the date of the measure under Section 13(4) — per Section 17(1) read with Rule 11 of the Security Interest (Enforcement) Rules 2002. Delay condonable under Section 5 of the Limitation Act 1963 on sufficient cause shown."
```

## Standing rule (Section 17(1))

Standing is wide: borrower, guarantor, mortgagor, lessee under a registered lease, tenant in occupation, and any other "person aggrieved" by the Section 13(4) measure has standing. The Drafter pleads the Applicant's qualifying status with specificity.

## Limited scope of inquiry (Section 17(3))

The DRT's inquiry under Section 17(3) is limited to whether the secured creditor's measure under Section 13(4) is in accordance with the SARFAESI Act 2002 and the Security Interest (Enforcement) Rules 2002. The DRT will NOT, in a Section 17 SA, re-adjudicate the quantum of the secured debt or determine the merits of the underlying loan-transaction dispute — those remedies lie in a counter-claim before the DRT in the secured creditor's parallel OA, or in a civil suit (subject to Section 34 SARFAESI bar).

The Drafter pleads the procedural defects with specificity and does NOT over-plead a quantum-dispute case in a Section 17 SA — that approach attracts a *Mardia Chemicals* preliminary-objection.

## Mandatory remedy-channel disclosure

Where the Applicant has also instituted a writ petition before the High Court raising the same grounds, that must be disclosed. *United Bank of India v. Satyawati Tondon* (2010) 8 SCC 110 disapproves of writ-petition forum-shopping when the SARFAESI alternative remedy is available.
