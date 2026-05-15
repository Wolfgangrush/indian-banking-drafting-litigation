---
name: ibc-section-7-application-draft
description: Draft an Application under Section 7 of the Insolvency and Bankruptcy Code 2016 by a Financial Creditor for initiation of the Corporate Insolvency Resolution Process against a Corporate Debtor before the National Company Law Tribunal. Encodes the Section 4 default-threshold rule (currently ₹1 crore), the Section 5(7) Financial-Creditor definition, the Section 5(8) Financial-Debt definition, the Section 7(3) — Section 7(5) admission framework, the proposed-IRP discipline (Section 7(3)(b) read with IBBI (CIRP for Corporate Persons) Regulations 2016), the Vashdeo R. Bhojwani (2019) / Babulal Vardharji Gurjar (2020) limitation rule from date of default with Section 18 Limitation Act acknowledgement, the moratorium under Section 14, the Innoventive Industries (2018) admission framework, and the IBBI (Application to Adjudicating Authority) Rules 2016 Form 1 filing discipline. Auto-fires on "draft Section 7 IBC", "draft IBC application financial creditor", "draft NCLT IBC", "draft CIRP application", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# IBC Section 7 Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION UNDER SECTION 7 OF THE INSOLVENCY AND BANKRUPTCY CODE 2016 FOR INITIATION OF THE CORPORATE INSOLVENCY RESOLUTION PROCESS
case_short_code: IBC_7
case_number_prefix: C.P. (IB)
pleading_type: Company Petition (Insolvency)
typical_forum: National Company Law Tribunal of competent territorial jurisdiction under Section 60(1) IBC (NCLT within whose territorial jurisdiction the registered office of the Corporate Debtor is situated)
typical_parties: Applicant Financial Creditor (Bank / NBFC / Asset Reconstruction Company / Debenture-Trustee / Allottee-Class under Section 5(8)(f) Explanation / consortium-member) + Respondent Corporate Debtor
filing_form: Form 1 of the IBBI (Application to Adjudicating Authority) Rules 2016 — supported by Part I (Particulars of Applicant), Part II (Particulars of Corporate Debtor), Part III (Particulars of Proposed Interim Resolution Professional), Part IV (Particulars of Financial Debt with documents), Part V (Particulars of Financial Debt-evidence documents)
statutory_opening: "This Application is filed under Section 7 of the Insolvency and Bankruptcy Code 2016 read with Rule 4 of the Insolvency and Bankruptcy Board of India (Application to Adjudicating Authority) Rules 2016, by the Applicant Financial Creditor against the Respondent Corporate Debtor, for initiation of the Corporate Insolvency Resolution Process on account of default by the Corporate Debtor in payment of a financial debt of ₹ ___ which is in excess of the threshold prescribed under Section 4 of the Code (currently ₹1 crore per Section 4 notification dated 24 March 2020)."
ground_clauses:
  - "Applicant is a Financial Creditor — within the meaning of Section 5(7) IBC; the debt owed by the Corporate Debtor is a Financial Debt within the meaning of Section 5(8) IBC, being a debt along with interest which is disbursed against the consideration for the time value of money and includes the heads enumerated in Section 5(8)(a) to (i)."
  - "Default has occurred — the Corporate Debtor has committed a default within the meaning of Section 3(12) IBC, by failing to make payment of the Financial Debt on the date of default being ____. The aggregate amount in default is ₹ ___, which is in excess of the threshold of ₹1 crore prescribed under Section 4 IBC (per the notification dated 24 March 2020)."
  - "Existence and quantum of debt — particulars of sanction, disbursement, accrued interest, and present default are set out in Part IV of Form 1 and supported by the documents at Part V (sanction letter at Exhibit ___, loan agreement at Exhibit ___, security documents at Exhibits ___, statement of account with Section 2A Bankers' Books Evidence Act 1891 certificate at Exhibit ___, default-intimation correspondence at Exhibit ___, NPA classification advice at Exhibit ___, recall notice at Exhibit ___)."
  - "Innoventive admission framework — under Innoventive Industries v. ICICI Bank (2018) 1 SCC 407, the NCLT is required only to satisfy itself that (a) a default has occurred, (b) the application is complete, and (c) no disciplinary proceedings are pending against the proposed IRP. The merits of any dispute about the debt are not the subject of inquiry at the admission stage."
  - "Limitation — the Application is filed within three years from the date of default per Article 137 of the Schedule to the Limitation Act 1963, as held in Vashdeo R. Bhojwani v. Abhyudaya Co-operative Bank (2019) 9 SCC 158 and Babulal Vardharji Gurjar v. Veer Gurjar Aluminium Industries (2020) 15 SCC 1. Acknowledgement of debt under Section 18 of the Limitation Act 1963 by the Corporate Debtor at Exhibit ___ extends limitation."
  - "Section 10A bar inapplicable — the default did not occur during the Section 10A suspension window (25 March 2020 — 24 March 2021); the present cause of action is post-suspension."
  - "Proposed Interim Resolution Professional — the Applicant proposes [Proposed-IRP-Name], registered with IBBI under registration No. [Registration-Placeholder], who has furnished a written communication in Form 2 of the IBBI (CIRP for Corporate Persons) Regulations 2016 consenting to act as Interim Resolution Professional (Exhibit ___). The proposed IRP has the requisite authorisation, has no disciplinary proceedings pending, and is otherwise eligible under Section 7(3)(b) IBC."
prayer_clauses:
  - "(a) Admit this Application under Section 7(5)(a) IBC and pass an order initiating the Corporate Insolvency Resolution Process in respect of the Corporate Debtor;"
  - "(b) Declare moratorium under Section 14 IBC in respect of the Corporate Debtor with effect from the date of admission;"
  - "(c) Appoint [Proposed IRP] as the Interim Resolution Professional with such directions as this Tribunal may consider appropriate, including directions for the public announcement under Section 13(1) IBC and the constitution of the Committee of Creditors under Section 21 IBC;"
  - "(d) Direct that the Corporate Debtor shall extend all assistance to the Interim Resolution Professional in accordance with Sections 17, 18, and 19 IBC."
mandatory_exhibits:
  - sanction_letter_loan_agreement_facility_documents
  - security_documents_hypothecation_mortgage_guarantee
  - statement_of_account_with_section_2a_bbea_certificate
  - default_intimation_correspondence
  - npa_classification_advice
  - recall_notice_with_proof_of_service
  - section_18_acknowledgement_of_debt_correspondence_or_balance_confirmation_where_relied_on
  - certified_master_data_of_corporate_debtor_from_mca
  - certified_charge_search_report_from_mca
  - board_resolution_authorising_the_applicant_to_file_the_application
  - written_consent_in_form_2_from_proposed_irp
  - registration_certificate_of_proposed_irp_with_ibbi
  - fee_receipt_under_schedule_to_ibbi_aaa_rules_2016
accompanying_applications:
  - "I.A. for ad-interim moratorium pending hearing (Section 14 read with Rule 11 NCLT Rules 2016 — though admission ordinarily triggers moratorium automatically)"
  - "I.A. for urgent listing"
  - "I.A. for any specific direction (e.g. directions to the Corporate Debtor to hand over books of account / records)"
filing_fee: "Fee under the Schedule to the IBBI (Application to Adjudicating Authority) Rules 2016 — ₹25,000 for a Section 7 application by a Financial Creditor (verify current schedule before filing). Paid through the NCLT's online portal / by demand draft as required by the bench."
limitation: "Three years from the date of default per Article 137 Limitation Act 1963 (Vashdeo R. Bhojwani (2019); Babulal Vardharji Gurjar (2020)). Acknowledgement under Section 18 Limitation Act extends limitation."
```

## Section 10A bar discipline

Section 10A IBC bars the filing of any Section 7 / Section 9 / Section 10 application in respect of any default arising during the period 25 March 2020 to 24 March 2021. The Drafter pleads positively that the date of default is outside the Section 10A window. Where any acknowledgement-of-debt is post the Section 10A window, the limitation runs from the acknowledgement; where the underlying default is pre-Section 10A and there is no Section 10A-window default, the bar is not attracted.

## Default-threshold discipline

The current default threshold under Section 4 IBC is ₹1 crore (per the notification dated 24 March 2020). The Drafter pleads the threshold compliance with specificity — the aggregate default amount (including interest crystallised to the date of default-determination) must equal or exceed ₹1 crore. Any subsequent re-categorisation of the default below ₹1 crore can be a ground for dismissal of the application at admission.

## Proposed IRP eligibility

The proposed IRP must:

- Be registered with the IBBI as an Insolvency Professional (Regulations 4 — 5 of the IBBI (Insolvency Professionals) Regulations 2016)
- Not have any disciplinary proceedings pending against him / her at the IBBI or the registered IPA
- Be eligible under Section 7(3)(b) read with the IBBI (Insolvency Professionals) Regulations 2016 to act as IRP in respect of the Corporate Debtor (no related-party relationship; no conflict of interest)
- Furnish written consent in Form 2 of the IBBI (CIRP for Corporate Persons) Regulations 2016

The Applicant attaches the IRP's registration certificate, the Form 2 consent, and the disciplinary-status declaration. The Drafter checks these annexures before filing.

## Moratorium under Section 14

On admission of the application, the NCLT declares moratorium under Section 14 IBC. The moratorium prohibits:

- The institution of suits or continuation of pending suits or proceedings against the Corporate Debtor including execution of any judgment / decree / order
- The transferring / encumbering / alienating / disposing of any assets of the Corporate Debtor
- Any action to foreclose, recover or enforce any security interest including action under SARFAESI
- The recovery of any property in possession of the Corporate Debtor as occupied by it
(Subject to Section 14(2A) — supply of essential goods or services to the Corporate Debtor shall not be terminated.)

The Drafter prays for the declaration of moratorium in the prayer clauses.
