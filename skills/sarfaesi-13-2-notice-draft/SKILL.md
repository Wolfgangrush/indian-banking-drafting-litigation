---
name: sarfaesi-13-2-notice-draft
description: Draft a Demand Notice under Section 13(2) of the Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002 (SARFAESI Act). Pre-enforcement statutory notice issued by a secured creditor (Bank / NBFC notified under Section 2(1)(m) / ARC) to a borrower whose account has been classified as a Non-Performing Asset under RBI Master Direction on IRAC 2021. Encodes the 60-day payment window, the secured-debt break-up discipline, the Schedule-of-Secured-Asset discipline, and the Mardia Chemicals (2004) 4 SCC 311 + ITC Ltd. v. Blue Coast Hotels (2018) 15 SCC 99 + Authorised Officer of UCO Bank discipline on Section 13(2) ingredients. Auto-fires on "draft SARFAESI 13(2) notice", "draft demand notice", "draft Section 13(2) notice", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# SARFAESI Section 13(2) Demand Notice Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md` (with adaptations — a Section 13(2) notice is a quasi-judicial notice, not a tribunal pleading; the Cause-Title section is replaced by the notice header and the Affidavit + Index sections are dropped)
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: NOTICE UNDER SECTION 13(2) OF THE SARFAESI ACT 2002
case_short_code: SARFAESI_13_2
notice_type: Statutory demand-notice (pre-enforcement)
typical_forum: N/A (notice is issued by the secured creditor under its own authority; no court / tribunal involvement at this stage)
typical_parties: Issuing Secured Creditor (Bank / NBFC / ARC) + Borrower(s) + Guarantor(s) + Mortgagor(s) (every guarantor and every third-party security holder must be separately served)
statutory_opening: "This Notice is issued under Section 13(2) of the Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002, read with Rule 3 of the Security Interest (Enforcement) Rules 2002, by the Authorised Officer of the [Secured Creditor], in respect of the secured asset(s) described in the Schedule hereto."
mandatory_ingredients:
  - "Identification of the secured creditor + its registration / licence reference + the name and designation of the Authorised Officer"
  - "Identification of the borrower(s) + guarantor(s) + mortgagor(s) by name and address"
  - "Identification of the loan account + sanction reference + sanction date + sanction amount + present outstanding"
  - "Statement of the secured debt with break-up: principal + accrued interest + cost-of-funds penal interest + legal costs"
  - "Date of NPA classification + reference to RBI Master Direction on IRAC 2021"
  - "60-day window from the date of the notice for the borrower to discharge in full the liabilities described"
  - "Consequences of failure to discharge — the secured creditor will be entitled to exercise all or any of the rights under Section 13(4) (taking possession / management / lease / assignment / sale of the secured assets)"
  - "Description of the secured asset(s) in the Schedule, with sufficient particularity to identify each asset (immovable property — survey number / municipal number / boundaries; movable assets — make / model / description / location)"
  - "Statement of Account certified under Section 2A of the Bankers' Books Evidence Act 1891 enclosed"
  - "The borrower's right under Section 13(3A) to make representation to the secured creditor + the address for representation + the time within which the representation must be received"
  - "Mode of service contemplated — registered post AD / speed post / courier / affixture / publication / electronic mode under Rule 3(1) Security Interest (Enforcement) Rules 2002"
mandatory_exhibits_to_keep_on_file:
  - sanction_letter
  - loan_agreement
  - hypothecation_deed_or_mortgage_deed
  - guarantee_deed
  - statement_of_account_with_section_2a_bbea_certificate
  - npa_classification_advice
  - schedule_of_secured_asset_with_valuation_reference
  - board_resolution_or_general_power_of_attorney_authorising_the_authorised_officer
```

## Section 13(3A) representation discipline

A borrower may, on receipt of a Section 13(2) notice, make a representation or raise objection to the secured creditor under Section 13(3A). The secured creditor must consider the representation and communicate the reasons for non-acceptance within 15 days of receipt of the representation. Non-consideration of the representation is a ground for a Section 17 SA.

The Section 13(2) notice itself must state the borrower's right to make representation, the address for service, and the period within which the representation must be received. The Drafter never omits this paragraph — its omission is fatal under *Mardia Chemicals v. Union of India* (2004) 4 SCC 311.

## Service discipline

Service must satisfy Rule 3 Security Interest (Enforcement) Rules 2002:

- Registered post AD to the last known address of the borrower / guarantor / mortgagor
- Speed post / courier with acknowledgement
- Hand delivery with signed acknowledgement
- Affixture in case of evasion of service (with two-witness panchnama)
- Publication in two newspapers (one local-language newspaper + one English newspaper) where the borrower is not traceable
- Electronic service to email-on-record (post the 2016 amendment to Rule 3)

The Drafter prepares a service-affidavit annexure to be sworn after service is effected.

## Ingredient-omission landmines

A Section 13(2) notice that omits any of the following ingredients is challengeable in a Section 17 SA and frequently set aside:

1. Failure to identify the secured debt with break-up (principal + interest + costs separately)
2. Failure to state the 60-day window
3. Failure to enclose Section 2A BBEA certificate
4. Failure to state Section 13(3A) representation right
5. Service at a non-current address (where a current address was on the bank's records)
6. Issued by an officer not designated as Authorised Officer under Section 13(12)

The Drafter checks each ingredient before finalising the notice.
