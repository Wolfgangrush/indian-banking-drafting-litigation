---
name: sarfaesi-14-cmm-dm-application-draft
description: Draft an Application under Section 14 of the SARFAESI Act 2002 before the Chief Metropolitan Magistrate (in metropolitan areas) or the District Magistrate (elsewhere) for assistance in taking physical possession of a secured asset where the secured creditor's possession-taking under Section 13(4) is obstructed. Encodes the post-2016 amendment 30-day disposal discipline, the Section 14(1A) Advocate-Commissioner mechanism, the Authorised Officer's affidavit-of-9-points requirement laid down in Standard Chartered Bank v. V. Noble Kumar (2013) 9 SCC 620, and the territorial-jurisdiction rule. Auto-fires on "draft Section 14 SARFAESI", "draft CMM application possession", "draft DM application possession", "SARFAESI 14 possession assistance", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# SARFAESI Section 14 (CMM / DM) Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION UNDER SECTION 14 OF THE SARFAESI ACT 2002 FOR ASSISTANCE IN TAKING PHYSICAL POSSESSION OF THE SECURED ASSET
case_short_code: SARFAESI_14
case_number_prefix: M.A.
pleading_type: Misc. Application
typical_forum: Chief Metropolitan Magistrate (in metropolitan areas) / District Magistrate (elsewhere) within whose local jurisdiction the secured asset is situated
typical_parties: Applicant Authorised Officer of the Secured Creditor + Respondent Borrower(s) + Respondent Occupant(s) (in-possession tenants / sub-lessees / trespassers) — formal arraying of occupants is required where third-party possession is anticipated
statutory_opening: "This Application is filed under Section 14 of the Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002, by the Authorised Officer of the Secured Creditor, for assistance from this Hon'ble Court in taking physical possession of the secured asset described in the Schedule hereto, which the Applicant is entitled to take possession of under Section 13(4) of the said Act, but has been unable to do so on account of [obstruction / refusal to vacate by the borrower / occupant / third-party]."
mandatory_affidavit_ingredients_per_Standard_Chartered_v_Noble_Kumar:
  - "1. That the Applicant is a secured creditor within the meaning of Section 2(zd) of the SARFAESI Act 2002."
  - "2. That the debt and the security interest in respect of which the present application is filed are particularised in the Schedule."
  - "3. That the security interest has been validly created and is registered with CERSAI under Section 23 of the SARFAESI Act 2002."
  - "4. That the borrower has been classified as a Non-Performing Asset in accordance with the RBI Master Direction on IRAC 2021."
  - "5. That a Section 13(2) demand notice has been issued and the 60-day window has expired without payment."
  - "6. That a Section 13(4) possession notice has been issued in compliance with Rule 8 of the Security Interest (Enforcement) Rules 2002."
  - "7. That no proceedings under any other law are pending which operate as a stay against the present possession-taking (and in particular no SARFAESI Section 17 SA is admitted and operating as a stay; no IBC Section 14 moratorium is operating against the borrower-corporate-debtor)."
  - "8. That the borrower has not made any representation under Section 13(3A), OR has made a representation which has been considered and rejected with reasons communicated within 15 days."
  - "9. That the time of 60 days for re-payment has expired and the Applicant is entitled in law to take physical possession of the secured asset."
prayer_clauses:
  - "(a) Pass an order under Section 14 of the SARFAESI Act 2002 directing assistance in taking physical possession of the Schedule of Secured Asset and handing over the same to the Applicant;"
  - "(b) Authorise an Advocate-Commissioner under Section 14(1A) for the purpose of taking possession on behalf of the Applicant Secured Creditor;"
  - "(c) Direct the local police authorities to render such assistance as may be necessary to take possession peacefully and lawfully;"
  - "(d) Dispose of this Application within 30 days as mandated by the third proviso to Section 14(1)."
mandatory_exhibits:
  - sanction_letter_and_loan_documents
  - hypothecation_deed_or_mortgage_deed
  - cersai_registration_certificate
  - section_13_2_notice_with_proof_of_service
  - section_13_3a_representation_and_response_or_certificate_of_non_receipt
  - section_13_4_possession_notice_with_publication_proof
  - npa_classification_advice
  - statement_of_account_with_section_2a_bbea_certificate
  - panchnama_of_attempted_possession_or_obstruction
  - schedule_of_secured_asset_with_valuation
  - board_resolution_or_general_power_of_attorney_authorising_the_authorised_officer
accompanying_applications:
  - "I.A. for ad-interim directions to the local Police Inspector / Station House Officer to remain present at the time of taking possession"
  - "I.A. for urgent listing where the borrower is dissipating the secured asset"
court_fee: "Local Magistrate-court schedule — typically a nominal application fee + service-process fee + inventory and panchnama fee for the Advocate-Commissioner."
```

## 30-day disposal discipline

The third proviso to Section 14(1) (inserted by the 2016 amendment) requires the CMM / DM to dispose of the application within 30 days from the date of filing — extendable up to 60 days for reasons recorded in writing. The Drafter pleads the 30-day disposal expectation in the prayer.

## Limited scope of inquiry at CMM / DM stage

The CMM / DM exercises a ministerial / procedural function under Section 14. The CMM / DM does NOT examine the merits of the Section 13(2) notice / the Section 13(4) measure / the NPA classification — those merits are within DRT's Section 17 jurisdiction. The CMM / DM's role is limited to verifying the affidavit-of-9-points and passing an order of assistance. *Standard Chartered Bank v. V. Noble Kumar* (2013) 9 SCC 620 is the controlling authority.

## Advocate-Commissioner mechanism

Section 14(1A) (inserted by the 2016 amendment) authorises the CMM / DM to appoint an Advocate-Commissioner to take possession on behalf of the secured creditor. The Drafter routinely prays for an Advocate-Commissioner where the secured creditor anticipates obstruction or where the secured asset is high-value and requires neutral panchnama.
