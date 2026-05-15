---
name: drt-original-application-draft
description: Draft an Original Application before the Debts Recovery Tribunal under Section 19 of the Recovery of Debts and Bankruptcy Act 1993 (formerly the RDDBFI Act 1993). For a Bank / Financial Institution / Asset Reconstruction Company recovering a debt of ≥ ₹20 lakh (current threshold under Section 1(4); verify against latest notification) from a borrower / corporate debtor / guarantor / mortgagor. Encodes the Section 19 jurisdictional scheme, the Rule 4 / Rule 5 DRT (Procedure) Rules 1993 filing discipline, the Section 22 evidence + procedure framework, and the Section 25 — 28 recovery framework (recovery officer + certificate of recovery + attachment + sale). Covers secured-creditor and unsecured-creditor pleadings. Auto-fires on "draft DRT OA", "draft DRT original application", "draft DRT recovery petition", "draft Section 19 RDDBFI", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# DRT Original Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: ORIGINAL APPLICATION UNDER SECTION 19 OF THE RECOVERY OF DEBTS AND BANKRUPTCY ACT 1993
case_short_code: DRT_OA
case_number_prefix: O.A.
pleading_type: Original Application
typical_forum: Debts Recovery Tribunal (territorial jurisdiction per Section 19(1) — cause of action / defendant residence / branch where the loan account is maintained)
typical_parties: Applicant Bank / Financial Institution / ARC + Defendant Borrower + Defendant Guarantor(s) + Defendant Mortgagor(s) (where security holder is distinct)
statutory_opening: "This Original Application is filed under Section 19 of the Recovery of Debts and Bankruptcy Act 1993 read with Rule 4 and Rule 5 of the Debts Recovery Tribunal (Procedure) Rules 1993, for recovery of a debt of ₹ ___ together with interest at the contractual rate from the Defendants, and for confirmation of the security interest created in favour of the Applicant Bank over the Schedule of Property at Exhibit ___."
ground_clauses:
  - "Authority — the Applicant Bank is a 'Bank' within the meaning of Section 2(d) of the RDDBFI Act 1993 / the Applicant Financial Institution is a notified Financial Institution under Section 2(h) / the Applicant Asset Reconstruction Company is a securitisation or reconstruction company registered with the RBI under Section 3 of the SARFAESI Act 2002."
  - "Jurisdictional anchor — the Tribunal has territorial jurisdiction under Section 19(1) read with Section 17 RDDBFI as (a) the cause of action wholly or in part arose within the local limits, OR (b) the Defendants reside / carry on business within the local limits, OR (c) the branch where the loan account is maintained is situated within the local limits."
  - "Pecuniary jurisdiction — the debt claimed is ≥ ₹20 lakh, satisfying Section 1(4) RDDBFI Act 1993."
  - "Cause of action crystallised — first default on ____; NPA classification on ____ in accordance with RBI Master Direction on Income Recognition, Asset Classification and Provisioning 2021; recall notice / demand notice issued on ____ and served on the Defendants; payment window of ___ days has expired without payment / restructuring."
  - "Security interest valid and subsisting — Deed of Hypothecation / Mortgage Deed / Deed of Guarantee duly executed; CHG-1 filed with the RoC; CERSAI registration completed; security interest is registered under the SARFAESI Act 2002."
  - "Limitation — the present Application is filed within three years from the date of default / from the date of last acknowledgement of debt under Section 18 of the Limitation Act 1963 (Exhibit ___)."
prayer_clauses:
  - "(a) Issue a Certificate of Recovery under Section 19(20) / Section 19(22) of the RDDBFI Act 1993 in favour of the Applicant Bank against the Defendants jointly and severally for the sum of ₹ ___ together with contractual interest at the rate of ___% per annum from ____ till date of realisation, together with costs of these proceedings;"
  - "(b) Confirm the security interest of the Applicant Bank over the Schedule of Property at Exhibit ___ and direct that the said property may be sold and the sale proceeds applied towards satisfaction of the Certificate of Recovery;"
  - "(c) Direct that the Recovery Officer may proceed under Sections 25 to 28 of the RDDBFI Act 1993 read with the Second and Third Schedules to the Income-tax Act 1961 for execution of the Certificate of Recovery;"
  - "(d) Grant ad-interim ex-parte injunction restraining the Defendants from alienating, transferring, encumbering, or in any manner dealing with the Schedule of Property and / or any other assets of the Defendants pending disposal of this Application;"
mandatory_exhibits:
  - sanction_letter
  - loan_agreement
  - hypothecation_deed_or_mortgage_deed_or_guarantee_deed
  - charge_form_chg_1
  - cersai_registration_certificate
  - statement_of_account_with_section_2a_bbea_certificate
  - first_default_intimation
  - recall_or_demand_notice_with_proof_of_service
  - npa_classification_advice
  - board_resolution_authorising_the_litigation
  - power_of_attorney_in_favour_of_the_authorised_signatory_where_applicable
accompanying_applications:
  - "I.A. for ad-interim ex-parte injunction (under Section 19(12) RDDBFI Act 1993 read with Order 39 CPC)"
  - "I.A. for attachment before judgment (under Section 19(13) RDDBFI Act 1993 read with Order 38 CPC)"
  - "I.A. for appointment of Receiver (under Order 40 CPC)"
  - "I.A. for urgent listing (where the threat of asset dissipation is imminent)"
court_fee: "Slab fee under Rule 7 of the DRT (Procedure) Rules 1993 — tiered against claim quantum. The Drafter computes the slab fee from `case-config.md` and reflects it in the OA memo."
```

## Section 22 procedure note

Section 22 RDDBFI Act 1993 ousts the strict application of the Code of Civil Procedure 1908 and the Indian Evidence Act 1872 — the Tribunal is guided by principles of natural justice and has the power to regulate its own procedure under Section 22(2). The Drafter relies on this for shorter form pleadings (no ad valorem schedule; no formal exhibits in original at filing; reliance on certified copies and Section 2A Bankers' Books Evidence Act 1891 certificates).

## Section 25 — 28 recovery framework note

On issue of the Certificate of Recovery, execution proceeds before the Recovery Officer applying the Second and Third Schedules to the Income-tax Act 1961 (Tax Recovery Officer powers — attachment, sale, arrest, detention). The DRT order does not become a "decree" of a civil court; execution remains within the RDDBFI scheme.

## Cross-references to SARFAESI

The Bank may pursue SARFAESI enforcement and DRT recovery in parallel — see *Transcore v. Union of India* (2008) 1 SCC 125. The Drafter incorporates a brief paragraph confirming that no SARFAESI measure under Section 13(4) operates as an estoppel against the present DRT OA.
