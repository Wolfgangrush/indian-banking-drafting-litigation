---
name: ibc-section-95-application-draft
description: Draft an Application under Section 95 of the Insolvency and Bankruptcy Code 2016 by a creditor for initiation of the Insolvency Resolution Process against a Personal Guarantor to a Corporate Debtor before the National Company Law Tribunal (where the CIRP of the Corporate Debtor is pending) — or before the Debts Recovery Tribunal where the personal guarantor is being proceeded against independently of any corporate CIRP. Encodes the Section 78 default threshold (₹1,000), the Lalit Kumar Jain v. Union of India (2021) 9 SCC 321 constitutional-validity framework, the IBBI (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019 filing discipline (Form C of the said Rules), the Section 99 Resolution Professional report stage, the Section 100 admission stage, and the Section 101 moratorium. Auto-fires on "draft Section 95 IBC", "draft personal guarantor IBC", "draft IBC personal insolvency", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# IBC Section 95 Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION UNDER SECTION 95 OF THE INSOLVENCY AND BANKRUPTCY CODE 2016 FOR INITIATION OF INSOLVENCY RESOLUTION PROCESS AGAINST A PERSONAL GUARANTOR TO A CORPORATE DEBTOR
case_short_code: IBC_95
case_number_prefix: C.P. (IB)
pleading_type: Company Petition (Insolvency — Personal Guarantor)
typical_forum: National Company Law Tribunal (where the CIRP of the Corporate Debtor is pending / has been admitted) under Section 60(2) IBC; OR Debts Recovery Tribunal in respect of personal-guarantor insolvency where the corporate-debtor route is not invoked
typical_parties: Applicant Creditor (Bank / NBFC / ARC / individual creditor of the personal guarantor) + Respondent Personal Guarantor
filing_form: Form C of the IBBI (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019 — Part I (Particulars of Applicant), Part II (Particulars of Personal Guarantor), Part III (Particulars of Proposed Resolution Professional), Part IV (Particulars of Debt with documents), Part V (Particulars of Debt-evidence documents)
statutory_opening: "This Application is filed under Section 95 of the Insolvency and Bankruptcy Code 2016 read with Rule 7 of the Insolvency and Bankruptcy Board of India (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019, by the Applicant Creditor against the Respondent Personal Guarantor, for initiation of the Insolvency Resolution Process on account of default by the Personal Guarantor in respect of a debt of ₹ ___ which is in excess of the threshold prescribed under Section 78 IBC (₹1,000)."
ground_clauses:
  - "Applicant is a creditor — within the meaning of Section 3(10) IBC; the debt owed by the Personal Guarantor is a 'debt' within the meaning of Section 3(11) read with the contract of guarantee at Exhibit ___."
  - "Respondent is a Personal Guarantor to a Corporate Debtor — within the meaning of Section 5(22) IBC, having executed a Deed of Guarantee dated ____ in favour of the Applicant in respect of the credit facilities granted to [Name of Corporate Debtor] (Exhibit ___)."
  - "Default has occurred — the Corporate Debtor has defaulted on the underlying credit facility; the Applicant has invoked the guarantee by Notice of Invocation dated ____ (Exhibit ___); the Personal Guarantor has failed to honour the invocation of guarantee."
  - "Default threshold satisfied — the aggregate default amount is ₹ ___, which is well in excess of the ₹1,000 threshold prescribed under Section 78 IBC."
  - "Lalit Kumar Jain framework — the constitutional validity of the IBC scheme applicable to personal guarantors to corporate debtors stands affirmed in Lalit Kumar Jain v. Union of India (2021) 9 SCC 321; the Adjudicating Authority's jurisdiction under Section 60(2) IBC over the Personal Guarantor where the Corporate Debtor's CIRP is pending is established by State Bank of India v. Mahendra Kumar Jajodia (2022) and the lineage of Supreme Court precedent thereafter."
  - "Limitation — the Application is filed within three years from the date of invocation of guarantee / from the date of last acknowledgement under Section 18 Limitation Act 1963 (Exhibit ___)."
  - "Proposed Resolution Professional — the Applicant proposes [Proposed-RP-Name], registered with IBBI under registration No. [Registration-Placeholder], who has furnished a written communication consenting to act as Resolution Professional (Exhibit ___)."
prayer_clauses:
  - "(a) Admit this Application under Section 100 IBC and pass an order initiating the Insolvency Resolution Process in respect of the Personal Guarantor;"
  - "(b) Direct the Insolvency and Bankruptcy Board of India to confirm the appointment of [Proposed RP] as the Resolution Professional under Section 97 IBC;"
  - "(c) Declare interim moratorium under Section 96 IBC from the date of filing of this Application and final moratorium under Section 101 IBC from the date of admission;"
  - "(d) Direct the Resolution Professional to examine the Application and submit the report under Section 99 IBC."
mandatory_exhibits:
  - underlying_loan_agreement_or_facility_documents_to_the_corporate_debtor
  - deed_of_personal_guarantee_signed_by_the_personal_guarantor
  - statement_of_account_or_default_calculation_certified_under_section_2a_bbea
  - notice_of_invocation_of_guarantee_with_proof_of_service
  - personal_guarantors_failure_to_honour_invocation_correspondence
  - section_18_acknowledgement_of_debt_or_balance_confirmation_where_relied_on
  - certified_master_data_of_corporate_debtor_from_mca
  - particulars_of_corporate_debtor_cirp_status_where_applicable
  - written_consent_of_proposed_resolution_professional
  - registration_certificate_of_proposed_resolution_professional_with_ibbi
  - fee_receipt_under_schedule_to_ibbi_aaa_for_personal_guarantors_rules_2019
  - board_resolution_authorising_the_applicant_to_file_the_application
accompanying_applications:
  - "I.A. for direction to the IBBI to confirm the Resolution Professional"
  - "I.A. for ad-interim moratorium under Section 96 IBC pending hearing"
  - "I.A. for urgent listing"
filing_fee: "Fee under the Schedule to the IBBI (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019 — paid through the NCLT's online portal / by demand draft. Verify current schedule before filing."
limitation: "Three years from the date of invocation of guarantee / from the date of last acknowledgement under Section 18 Limitation Act 1963."
```

## Section 60(2) jurisdictional anchor

Where the Corporate Debtor is already under CIRP / liquidation before the NCLT, Section 60(2) IBC vests jurisdiction over insolvency / bankruptcy proceedings against a personal guarantor in the same NCLT bench. *State Bank of India v. Mahendra Kumar Jajodia* (2022) confirms that pendency of CIRP of the Corporate Debtor is not a pre-condition for the maintainability of a Section 95 application against the Personal Guarantor — the same NCLT bench has jurisdiction over the Personal Guarantor under Section 60(2) regardless.

Where the Corporate Debtor's CIRP is not pending, the personal-guarantor insolvency proceedings lie before the DRT under Part III IBC (Sections 79 — 187), with the threshold and procedure suitably adapted.

## Section 99 Resolution Professional report stage

Once the Application is filed, the Adjudicating Authority appoints the Resolution Professional under Section 97. The Resolution Professional submits a report under Section 99 within 10 days of appointment, recommending either admission or rejection of the Application. The Adjudicating Authority decides on admission under Section 100 within 14 days of receipt of the Section 99 report.

The Drafter prepares the Applicant's potential response to any Section 99 report that recommends rejection, anticipating the personal-guarantor's typical defences (denial of execution of the guarantee / invalid invocation / discharge of the guarantor under Sections 134 — 141 ICA 1872 / time-bar).

## Sections 134 — 141 ICA defences

Personal guarantors routinely plead discharge defences:

- **Section 134** — variance in terms of the principal-debtor contract without the guarantor's consent
- **Section 135** — composition / promise to give time to the principal debtor
- **Section 139** — creditor's act / omission impairing the surety's eventual remedy
- **Section 141** — release / loss of security held by the creditor for the principal debt

The Drafter pleads positively that no such discharge events have occurred — the guarantee is a continuing guarantee under Section 129 ICA 1872, the credit facility was extended on the agreed terms, no variance was made without the guarantor's consent, no security was released or impaired, and the guarantee remains in subsisting force.
