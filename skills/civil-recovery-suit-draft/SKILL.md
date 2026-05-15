---
name: civil-recovery-suit-draft
description: Draft a Plaint for recovery of money — either an ordinary Order 7 CPC plaint for recovery of money / mortgage suit, OR an Order 37 CPC Summary Suit for a liquidated demand based on a written contract / bill of exchange / promissory note / cheque (excluding Section 138 NI Act criminal proceedings). For Banks / NBFCs / individual lenders whose claim falls BELOW the DRT pecuniary threshold (currently ₹20 lakh) or where the lender is not a 'Bank' / 'Financial Institution' notified under the RDDBFI Act 1993. Encodes the Order 7 mandatory averments, the Order 37 summary procedure (10-day leave to defend / unconditional defence on triable issues), the Order 34 mortgage-suit framework, and the limitation discipline. Auto-fires on "draft recovery suit", "draft summary suit", "draft Order 37 suit", "draft money suit", "draft mortgage suit", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Civil Recovery Suit Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: PLAINT FOR RECOVERY OF MONEY UNDER ORDER 7 OF THE CODE OF CIVIL PROCEDURE 1908 / SUMMARY SUIT UNDER ORDER 37 OF THE CODE OF CIVIL PROCEDURE 1908
case_short_code: CIVIL_RECOVERY
case_number_prefix: R.C.S. / Spl.C.S. / Comm.S. (per local civil-court nomenclature)
pleading_type: Plaint (ordinary) / Plaint (Order 37 Summary)
typical_forum: Civil Court of competent pecuniary jurisdiction (per applicable State pecuniary-jurisdiction notification) within whose territorial jurisdiction the cause of action arose or the Defendant resides
typical_parties: Plaintiff Lender (Bank / NBFC / individual / company) + Defendant Borrower + Defendant Guarantor + Defendant Mortgagor (where the security holder is distinct)
statutory_opening_ordinary: "This Plaint is filed under Order 7 of the Code of Civil Procedure 1908 read with Section 26 CPC, for recovery of a sum of ₹ ___ together with interest from the Defendants, and where applicable for a decree of foreclosure / sale of the mortgaged property under Order 34 CPC."
statutory_opening_summary: "This Plaint is filed under Order 37 of the Code of Civil Procedure 1908 for a liquidated demand of ₹ ___ together with interest at the contractual rate of ___% per annum, the claim being founded on a written contract / promissory note / bill of exchange / cheque / hundi / written guarantee dated ____, which entitles the Plaintiff to recover the said amount as a liquidated demand under Order 37."
ground_clauses_for_ordinary_plaint:
  - "Authority — the Plaintiff is competent to maintain the present suit (where Plaintiff is a Bank / NBFC, the Banking Regulation Act 1949 / RBI registration; where Plaintiff is a private lender, the underlying contract / promissory note is enforceable)."
  - "Jurisdictional anchor — the Court has territorial jurisdiction under Sections 16 — 20 CPC and pecuniary jurisdiction under the applicable State pecuniary-jurisdiction notification."
  - "Cause of action crystallised — first default on ____; recall notice / demand notice issued on ____ and served; payment window of ___ days has expired without payment."
  - "Where Plaintiff is a Bank / NBFC, the claim is BELOW the DRT pecuniary threshold of ₹20 lakh — Section 18 RDDBFI bar does not apply (Bank can also waive the DRT remedy where the claim is above the threshold; but the cleaner route is to file before DRT for above-₹20-lakh claims)."
  - "Limitation — Article 19 / Article 21 / Article 22 / Article 55 of the Schedule to the Limitation Act 1963 — 3 years from default / from accrual of cause of action; acknowledgement under Section 18 Limitation Act extends limitation."
  - "Where the suit is a mortgage suit under Order 34 CPC — particulars of the mortgage, of the mortgaged property, of the mortgage-money, of the security interest registered with the Sub-Registrar and with CERSAI."
ground_clauses_for_summary_suit_under_order_37:
  - "The suit is on a written contract / promissory note / bill of exchange / cheque / written guarantee — the writing in question is annexed as Exhibit ___, with all particulars."
  - "The claim is for a liquidated demand — ₹ ___ as principal + ₹ ___ as agreed interest, the principal and interest both being ascertained or ascertainable from the face of the writing."
  - "Order 37 jurisdiction — the Plaint specifically states that it is a suit under Order 37 and that the Plaintiff seeks an Order 37 summons (Form 4 of Appendix B CPC) requiring the Defendant to obtain leave to defend within 10 days of service."
  - "Limitation — Article 35 of the Schedule to the Limitation Act 1963 (promissory note) / Article 36 (bill of exchange) / 3 years from date of execution of the promissory note / bill of exchange."
prayer_clauses_for_ordinary_plaint:
  - "(a) Pass a decree against the Defendants jointly and severally for the sum of ₹ ___ together with contractual interest at the rate of ___% per annum from ____ till date of realisation;"
  - "(b) Where applicable: pass a preliminary decree under Order 34 Rule 4 CPC and direct sale of the mortgaged property and the apportionment of the sale proceeds towards the Plaintiff's claim;"
  - "(c) Costs of the suit;"
  - "(d) Such further and other reliefs as this Hon'ble Court may deem fit and proper."
prayer_clauses_for_summary_suit:
  - "(a) Issue an Order 37 summons (Form 4 of Appendix B CPC) to the Defendants requiring the Defendants to enter appearance within 10 days of service and to apply for leave to defend, failing which the suit shall be decreed in favour of the Plaintiff;"
  - "(b) On the Defendants' failure to enter appearance / failure to obtain leave to defend / unconditional decree if leave to defend is not granted — pass a decree against the Defendants for ₹ ___ together with contractual interest at the rate of ___% per annum from ____ till date of realisation;"
  - "(c) Costs of the suit;"
  - "(d) Such further and other reliefs as this Hon'ble Court may deem fit and proper."
mandatory_exhibits:
  - sanction_letter_or_loan_agreement_or_promissory_note_or_bill_of_exchange_or_written_guarantee
  - mortgage_deed_or_hypothecation_deed_where_secured
  - statement_of_account_with_section_2a_bbea_certificate_where_plaintiff_is_a_bank
  - demand_notice_or_recall_notice_with_proof_of_service
  - reply_received_from_defendant_if_any
  - board_resolution_authorising_the_litigation_or_authorised_signatory_power_of_attorney
accompanying_applications:
  - "Application for ad-interim injunction restraining the Defendants from alienating, transferring, or encumbering the Schedule of Property (under Order 39 Rules 1 and 2 CPC)"
  - "Application for attachment before judgment (under Order 38 Rule 5 CPC)"
  - "Application for appointment of Receiver (under Order 40 CPC)"
  - "Application for ad-valorem court-fee abatement / installment payment (where applicable)"
court_fee: "Ad valorem under the applicable State Court-Fees Act on the principal claim + interest accrued to date of filing. Summary suit attracts the same ad valorem fee as an ordinary plaint."
limitation: "3 years from date of default / from date of accrual of cause of action / from date of acknowledgement under Section 18 Limitation Act 1963 — Articles 19 / 21 / 22 / 35 / 36 / 55 as applicable to the cause of action."
```

## Order 37 leave-to-defend discipline

Under Order 37 Rule 3 CPC, the Defendant must enter appearance within 10 days of service of the summons and must thereafter apply for leave to defend within 10 days of appearance. The Court grants leave —

- **Unconditional** — where the Defendant raises a triable issue going to the root of the case
- **Conditional (on deposit of part / whole of the claim)** — where the defence is plausible but not so persuasive as to warrant unconditional leave
- **Refused** — where the defence is sham / illusory / dilatory

*Mechanlec Engineers & Manufacturers v. Basic Equipment Corporation* (1976) 4 SCC 687 and *IDBI Trusteeship v. Hubtown Limited* (2017) 1 SCC 568 set out the threshold for leave to defend.

The Drafter prepares the Plaintiff's counter-affidavit to the leave-to-defend application as part of the same case folder.

## Order 34 mortgage-suit framework note

Where the suit is for foreclosure (Order 34 Rule 1) or for sale of mortgaged property (Order 34 Rule 4):

- Preliminary decree determining the mortgage-money, the date of redemption / sale, and the costs
- Final decree on expiry of the redemption period, directing sale and apportionment of proceeds
- Subsequent execution proceedings under Order 21 CPC

Where the Plaintiff is a Bank / NBFC and the claim is ≥ ₹20 lakh, the cleaner remedy is a DRT OA under Section 19 RDDBFI Act 1993 — see the `drt-original-application-draft` skill in this plugin.

## Bar of Section 34 SARFAESI

Where the Plaintiff is a secured creditor under the SARFAESI Act 2002 and the underlying matter falls within the SARFAESI scheme, Section 34 SARFAESI bars the jurisdiction of the Civil Court. *Mardia Chemicals v. Union of India* (2004) 4 SCC 311 read with *Jagdish Singh v. Heeralal* (2014) 1 SCC 479 set out the scope of the Section 34 bar. The Drafter checks the Section 34 bar before filing.
