---
name: ni-act-138-complaint-draft
description: Draft a Complaint under Section 138 of the Negotiable Instruments Act 1881 read with Section 142 NI Act and Section 223 of the Bharatiya Nagarik Suraksha Sanhita 2023 (corresponding to Section 200 of the Code of Criminal Procedure 1973). For dishonour of cheque issued by the drawer for discharge of a legally enforceable debt or liability where the drawer fails to make payment within 15 days of receipt of statutory notice. Encodes each statutory ingredient (cheque drawn on account maintained by drawer / for legally enforceable debt / presented within validity / returned unpaid for insufficiency / statutory notice within 30 days of return / drawer's failure to pay within 15 days / complaint within 30 days of notice expiry), the Section 142(2) territorial-jurisdiction rule (drawee-bank-branch jurisdiction), and the Section 141 company-prosecution discipline. Auto-fires on "draft Section 138 complaint", "draft cheque bounce complaint", "draft NI Act 138 complaint", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 138 NI Act Complaint Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: COMPLAINT UNDER SECTION 138 OF THE NEGOTIABLE INSTRUMENTS ACT 1881
case_short_code: NI_138
case_number_prefix: C.C.
pleading_type: Criminal Complaint
typical_forum: Court of the Judicial Magistrate First Class / Metropolitan Magistrate of competent territorial jurisdiction under Section 142(2) NI Act (where the drawee bank's branch is situated)
typical_parties: Complainant (Payee / Holder-in-due-course) + Accused (Drawer + where drawer is a company / partnership: every director / partner in charge of and responsible for the conduct of business under Section 141)
statutory_opening: "This Complaint is filed under Section 138 read with Section 142 of the Negotiable Instruments Act 1881 and Section 223 of the Bharatiya Nagarik Suraksha Sanhita 2023 (corresponding to Section 200 of the Code of Criminal Procedure 1973), against the Accused for dishonour of cheque on insufficiency of funds / for the amount exceeding the arrangement, the cheque having been issued by the Accused for the discharge of a legally enforceable debt or liability owed to the Complainant."
ingredient_paragraphs:
  - "1. Legally enforceable debt or liability — full narrative of the underlying transaction / debt / liability for which the cheque was issued, with supporting document references (Exhibit ___)."
  - "2. Cheque particulars — Cheque No. ___ dated ____ drawn on [Drawee-Bank-Placeholder], [Branch-Placeholder], for ₹ ___, in favour of the Complainant, signed by the Accused — original cheque at Exhibit ___."
  - "3. Presentation — the cheque was presented for payment / for collection through the Complainant's bank account at [Collecting-Bank-Placeholder] on ____, within the validity period of the cheque (three months from the date of the cheque)."
  - "4. Dishonour — the cheque was returned unpaid by the Drawee Bank vide Return Memo dated ____ with the reason 'funds insufficient' / 'exceeds arrangement' / 'account closed' / 'payment stopped by drawer' / [other reason actionable under Section 138] — Return Memo at Exhibit ___."
  - "5. Statutory notice — the Complainant issued a statutory notice under the proviso (b) to Section 138 NI Act on ____, demanding payment of the cheque amount within 15 days from the date of receipt of the notice — notice and proof of dispatch at Exhibit ___, acknowledgement of receipt / postal receipt with returned-cover at Exhibit ___."
  - "6. Drawer's failure to pay — the Accused has failed to make payment of the cheque amount within the 15-day period from receipt of the statutory notice — last day for payment was ____."
  - "7. Limitation — this Complaint is filed within 30 days from the expiry of the 15-day notice period, i.e. within the period prescribed by Section 142(1)(b) NI Act."
  - "8. Territorial jurisdiction — this Hon'ble Court has territorial jurisdiction under Section 142(2)(a) NI Act as the cheque was delivered for collection through the Complainant's account at [Collecting-Bank-Branch], the said branch being situated within the local jurisdiction of this Hon'ble Court."
  - "9. Section 141 (where the Accused is a company / partnership / LLP) — every Director / Partner / Designated Partner who was in charge of and was responsible to the company / firm / LLP for the conduct of business at the time the offence was committed is arrayed as Accused, along with the company / firm / LLP itself as the principal Accused."
prayer_clauses:
  - "(a) Take cognizance of the offence under Section 138 of the Negotiable Instruments Act 1881 and issue summons to the Accused under Section 227 of the Bharatiya Nagarik Suraksha Sanhita 2023 (corresponding to Section 204 of the Code of Criminal Procedure 1973);"
  - "(b) Try the Accused for the offence under Section 138 NI Act in accordance with law;"
  - "(c) On conviction, sentence the Accused to imprisonment for a term that may extend to two years and / or impose a fine that may extend to twice the cheque amount, and direct payment of the cheque amount with interest by way of compensation to the Complainant under Section 357 / Section 395 BNSS;"
  - "(d) Pass an order of interim compensation under Section 143A NI Act, equal to twenty percent of the cheque amount, payable to the Complainant within 60 days of the order;"
  - "(e) Pass an order of disposal in summary trial form under Section 143 NI Act."
mandatory_exhibits:
  - underlying_transaction_documents_or_loan_documents_evidencing_legally_enforceable_debt
  - original_cheque_at_issue
  - bank_return_memo
  - statutory_notice_with_postal_dispatch_proof_and_track_record
  - acknowledgement_of_receipt_or_returned_cover_evidencing_service
  - drawee_bank_certificate_under_section_146_NI_act
  - complainants_account_statement_evidencing_collection_through_local_branch
  - board_resolution_or_partnership_authority_in_company_partnership_complaints
accompanying_applications:
  - "Application for examination of the Complainant on solemn affirmation (under Section 223 BNSS / Section 200 CrPC)"
  - "Application for interim compensation under Section 143A NI Act"
  - "Application for summary trial under Section 143 NI Act"
court_fee: "Process fee under the local Magistrate-court schedule + court fee on the complaint under the applicable State Court-Fees Act."
limitation: "30 days from the expiry of the 15-day period given to the drawer to make payment after receipt of the statutory notice (Section 142(1)(b) NI Act). Delay condonable under the proviso to Section 142(1)(b) on sufficient cause."
```

## Section 141 (company / partnership) discipline

Where the drawer is a company / partnership / LLP, Section 141 NI Act extends liability to every person who, at the time the offence was committed, was in charge of and was responsible to the company / firm for the conduct of business. The Complainant must plead the specific role and responsibility of each Director / Partner arrayed — a generic pleading that the Director was "in charge" without further particulars is insufficient (*S.M.S. Pharmaceuticals v. Neeta Bhalla* (2005) 8 SCC 89).

## Section 139 presumption

Section 139 NI Act raises a statutory presumption in favour of the Complainant that the cheque was issued for the discharge of a legally enforceable debt or liability. The presumption is rebuttable — the Accused may rebut by leading evidence on a preponderance-of-probabilities standard (*Krishna Janardhan Bhat v. Dattatraya G. Hegde* (2008) 4 SCC 54). The Complainant is not required to lead detailed evidence on the existence of the debt at the threshold; the presumption operates until rebutted.

## Section 143A interim compensation

Post the 2018 amendment, Section 143A empowers the Magistrate to direct the drawer to pay interim compensation up to 20% of the cheque amount within 60 days of the order. The Drafter includes this prayer in every Section 138 complaint where the underlying debt is liquidated and undisputed on the face of the Complaint.

## Section 142(2) territorial-jurisdiction rule

Post the 2015 amendment to Section 142 NI Act, territorial jurisdiction lies in the court within whose local jurisdiction the bank branch where the cheque was delivered for collection (through the payee's account) is situated — OR where the cheque was presented for payment over-the-counter and the drawee bank's branch is situated. The pre-2015 *Dashrath Rupsingh Rathod* (2014) 9 SCC 129 rule (only drawee-bank-branch jurisdiction) stands legislatively displaced. The Drafter pleads the jurisdictional anchor by reference to the Complainant's collecting-bank-branch address and cites Section 142(2)(a).
