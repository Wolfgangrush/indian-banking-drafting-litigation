---
name: drat-appeal-draft
description: Draft an Appeal before the Debts Recovery Appellate Tribunal under Section 20 of the Recovery of Debts and Bankruptcy Act 1993, against any order of the Debts Recovery Tribunal — including the final OA order, an order on a Section 17 SA under SARFAESI, an order under Section 19(12) ad-interim injunction, an order under Section 19(13) attachment, an order under Section 25 — 28 recovery proceedings, or any order in any other application by which the appellant is aggrieved. Encodes the Section 21 pre-deposit discipline (50% reducible to 25%; not waivable), the 45-day limitation under Section 20(3), the grounds of appeal discipline, the Section 21 waiver-of-pre-deposit application discipline, and the standard of interference. Auto-fires on "draft DRAT appeal", "draft DRT appeal", "appeal DRT order", "draft Section 20 appeal", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# DRAT Appeal Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPEAL UNDER SECTION 20 OF THE RECOVERY OF DEBTS AND BANKRUPTCY ACT 1993 BEFORE THE DEBTS RECOVERY APPELLATE TRIBUNAL
case_short_code: DRAT
case_number_prefix: M.A. / R.A. (per the bench's numbering convention)
pleading_type: Memorandum of Appeal
typical_forum: Debts Recovery Appellate Tribunal (Mumbai / Delhi / Chennai / Kolkata / Allahabad — the bench corresponding to the DRT whose order is appealed against)
typical_parties: Appellant (the party aggrieved by the DRT order — could be the Bank or the Borrower depending on the order under appeal) + Respondent(s) (the counter-parties before the DRT)
statutory_opening: "This Appeal is filed under Section 20 of the Recovery of Debts and Bankruptcy Act 1993 read with Rule 5 of the Debts Recovery Appellate Tribunal (Procedure) Rules 1994, against the Order dated ____ passed by the Debts Recovery Tribunal at ____ in O.A. / S.A. No. ____ of ____ (Exhibit P-1), being aggrieved by the said Order which is contrary to law and the record of the case."
ground_clauses:
  - "Erroneous appreciation of evidence — the DRT failed to appreciate that [specific evidentiary defect with paragraph references in the impugned order]."
  - "Erroneous application of law — the DRT misapplied [specific statutory provision] in holding that [specific legal proposition], contrary to the binding authority of [Supreme Court / High Court precedent]."
  - "Procedural irregularity — the DRT proceeded ex-parte / refused adjournment / refused to consider documentary evidence on record / refused cross-examination, in breach of natural justice / Section 22 RDDBFI Act 1993 / DRT (Procedure) Rules 1993."
  - "Quantum miscalculation — the DRT erroneously included / excluded [specific head of debt] in / from the Certificate of Recovery; the correct figure ought to have been ₹ ___."
  - "Limitation — [where the underlying debt is barred by limitation — Articles 19 / 21 / 22 / 55 of the Schedule to the Limitation Act 1963 — the DRT failed to consider the limitation bar / failed to consider Section 18 Limitation Act acknowledgement / both]."
  - "Jurisdictional defect — the DRT lacked jurisdiction on grounds of [territorial / pecuniary / subject-matter] — [for a Bank appeal: the territorial-jurisdictional rule was misapplied / for a borrower appeal: the pecuniary threshold was below ₹20 lakh and the OA itself was non-maintainable]."
  - "Section 17 SA scope — the DRT exceeded its limited jurisdiction under Section 17(3) SARFAESI Act 2002 by re-adjudicating the quantum of the secured debt / by interfering with the secured creditor's measure on non-procedural grounds."
prayer_clauses:
  - "(a) Allow this Appeal;"
  - "(b) Set aside the impugned Order dated ____ passed by the Debts Recovery Tribunal at ____ in O.A. / S.A. No. ____ of ____;"
  - "(c) Pass such consequential orders as this Hon'ble Appellate Tribunal may deem fit and proper, including [substituted relief specific to the case-type — e.g. remand to the DRT for fresh consideration on specific issues; or substituted decree on the merits];"
  - "(d) Costs."
mandatory_exhibits:
  - certified_copy_of_the_impugned_order_of_the_drt
  - certified_copies_of_all_orders_passed_by_the_drt_in_the_oa_or_sa
  - copy_of_the_pleadings_before_the_drt_oa_or_sa_with_all_exhibits
  - copy_of_the_statement_of_account_with_section_2a_bbea_certificate
  - documents_relied_on_by_the_appellant_before_the_drt
  - section_18_acknowledgement_of_debt_correspondence_where_relevant
  - any_orders_passed_in_iAs_during_the_pendency_of_the_oa_or_sa
accompanying_applications:
  - "I.A. for waiver / reduction of pre-deposit under the proviso to Section 21 RDDBFI Act 1993 — typically pleaded with grounds (undue hardship / merits of the appeal favouring the appellant / disproportionate impact)"
  - "I.A. for stay of recovery proceedings / stay of execution of the Certificate of Recovery (where applicable)"
  - "I.A. for condonation of delay (where the 45-day limitation has been exceeded — with Section 5 Limitation Act grounds)"
  - "I.A. for urgent listing"
limitation: "45 days from the date of receipt of the impugned DRT Order — per Section 20(3) RDDBFI Act 1993. Delay condonable under the proviso to Section 20(3) on sufficient cause shown."
court_fee: "Appeal fee under Rule 8 of the DRAT (Procedure) Rules 1994 — slab fee linked to the debt amount in dispute."
```

## Section 21 pre-deposit discipline

Section 21 RDDBFI Act 1993 requires the appellant before the DRAT to deposit fifty percent of the debt amount as determined by the DRT, with the DRAT, as a condition precedent to entertaining the appeal. The DRAT may, for reasons recorded in writing, reduce the deposit to twenty-five percent — but cannot waive it entirely. *Narayan Chandra Ghosh v. UCO Bank* (2011) 4 SCC 548 confirms the non-waivable nature.

The Drafter prepares the appeal in one of two postures:

- **Pre-deposit complied** — deposit receipt (or BG / TDR) for 50% (or for the reduced 25% if a prior order so directed) is annexed to the appeal memo
- **Pre-deposit reduction sought** — a separate I.A. is filed seeking reduction to 25% with detailed grounds (undue hardship / merits of the appeal favouring the appellant on the face of the record / disproportionate impact)

The I.A. for reduction must be filed contemporaneously with the appeal — failure to file pre-deposit / failure to obtain reduction will lead to dismissal under Section 21 at the threshold.

## Standard of interference

The DRAT exercises appellate jurisdiction on questions of fact and law. However, the standard of interference is typically:

- On questions of law — full reconsideration
- On questions of fact — limited reconsideration; deference to the DRT's appreciation unless perverse / contrary to record / based on inadmissible evidence
- On exercise of discretion (injunctions / attachments) — interference only where the discretion has been exercised arbitrarily or contrary to settled principles

The Drafter pleads each ground specifying whether it is a question of law / question of fact / question of discretion, and frames the relief accordingly.

## Section 17 SA appellate discipline

Where the appeal is from a DRT order in a Section 17 SARFAESI SA, the appellate jurisdiction is exercised under Section 18 SARFAESI Act 2002 read with Section 20 RDDBFI Act 1993. The pre-deposit under Section 18 SARFAESI is the same 50% (reducible to 25%) regime. The grounds of appeal must respect the limited scope of Section 17(3) DRT jurisdiction — challenges to quantum re-adjudication by the DRT are valid grounds; defences on the merits of the secured creditor's claim that should have been led in a parallel OA cannot be re-introduced in the appeal.

## Cross-objections

Cross-objections by the Respondent before the DRAT are governed by Rule 9 of the DRAT (Procedure) Rules 1994 — to be filed within 30 days of receipt of the appeal-memo. The Drafter prepares cross-objections in a separate document when acting for the Respondent who is also aggrieved on specific points in the impugned order.
