---
name: _banking_drafting_base
description: Universal Indian banking pleading skeleton. Shared base for all 10 case-type drafting skills. Holds the standard structure (Cause Title -> Parties block -> Statutory Opening -> Prelude -> Facts -> Grounds -> Prayer -> Verification -> Affidavit-in-support -> Index -> List of Documents -> accompanying applications). NOT invoked directly — extended by every case-type skill in this plugin.
allowed-tools: Read
---

# `_banking_drafting_base` — universal Indian banking pleading skeleton

This base skill defines the **structural shape** of any banking / financial-recovery / insolvency pleading drafted by the plugin. Case-type skills extend this base with case-type-specific statutory openings, fact-sequences, grounds, prayer clauses, and accompanying applications.

## Universal skeleton

```
1. CAUSE TITLE
   {{forum.name}} {{forum.bench}}
   {{case_type.case_number_prefix}} No. ____ of {{year}}

   {{party_block_template}}
   {{applicant_or_complainant_party}} ... {{applicant_role}}
                                  Versus
   {{respondent_or_accused_party}} ... {{respondent_role}}

2. STATUTORY OPENING
   {{case_type.statutory_opening}}

3. PRELUDE
   (Short paragraph identifying the Applicant's status — Bank / NBFC /
   ARC / Holder-in-Due-Course / Operational-Creditor — with the
   authorisation reference (Board Resolution / Power-of-Attorney) and
   the registration / licence / branch particulars.)

4. FACTS (numbered narrative paragraphs)
   4.1 Sanction — date of sanction, sanction reference, sanction amount,
       tenor, interest, security stipulated, account opening
       (refer Exhibit / Annexure A).
   4.2 Disbursement — date(s) of disbursement, instruments of
       disbursement, accounts credited (refer Exhibit / Annexure B).
   4.3 Security creation — particulars of hypothecation / mortgage /
       guarantee / pledge, registration of charge, valuation report,
       CERSAI registration (refer Exhibits / Annexures C, D, E).
   4.4 Operation of the account — pre-default operation, drawings,
       repayments, periodic confirmations (refer Statement of Account
       certified under Section 2A Bankers' Books Evidence Act 1891 at
       Exhibit / Annexure F).
   4.5 First default — date of first default, instrument of default
       (returned cheque / unpaid EMI / failed RTGS), Bank's first
       intimation (refer Exhibit / Annexure G).
   4.6 Recall / demand notice — date of issue, date of service, mode
       of service, address served at, payment window allowed
       (refer Exhibit / Annexure H).
   4.7 NPA classification — date of NPA classification, classification
       advice, RBI MD IRAC 2021 compliance, intimation to the borrower
       (refer Exhibit / Annexure I).
   4.8 Post-NPA conduct — wilful-default tag (if any), CIBIL reporting,
       fraud declaration (if any), borrower's correspondence with the
       Bank, any restructuring proposal received and rejected
       (refer Exhibit / Annexure J).
   4.9 Cause of action for the present pleading — the specific event
       that has crystallised the present cause of action (e.g. expiry
       of the 60-day Section 13(2) window without payment; dishonour
       of cheque post-statutory notice; refusal of the Resolution
       Plan; etc.).
   4.10 Limitation — applicable Article of the Limitation Act 1963,
        date of accrual, date of filing, days within limitation (with
        Section 18 acknowledgement-of-debt reference where applicable).
   4.11 Jurisdiction — territorial jurisdiction of the Tribunal / Court,
        with statutory anchor (Section 19 RDDBFI / Section 142(2)
        NI Act / Section 60(1) IBC / etc.).
   4.12 Court fee / filing fee — amount + applicable rule (Rule 7 DRT
        Procedure Rules 1993 / Schedule I NCLT Rules 2016 / applicable
        State Court-Fees Act).

5. GROUNDS (numbered)
   5.1 {{case_type.ground_1}}
   5.2 {{case_type.ground_2}}
   5.3 {{case_type.ground_3}}
   ...
   (Grounds anchor each prayer clause; every ground cites the
    operative provision and the document supporting the ground.)

6. PRAYER
   {{case_type.prayer_clauses}}

   And for such further and other reliefs as this Hon'ble Tribunal /
   Court may deem fit and proper.

7. VERIFICATION
   I, [Name of Authorised Signatory], being the duly authorised
   signatory of the Applicant / Complainant / Petitioner, do hereby
   verify that the contents of paragraphs ___ to ___ of the
   {{case_type.pleading_type}} are true to my personal knowledge and
   the contents of paragraphs ___ to ___ are true on the basis of
   information received and believed to be true. No part of this
   verification is false and nothing material has been concealed
   therefrom.

   Verified at [Place] on this __ day of [Month, Year].

                                       [Authorised Signatory]
                                       [Designation]
                                       [Applicant Bank / Party]

8. AFFIDAVIT-IN-SUPPORT
   I, [Name of Authorised Signatory], aged ___ years, occupation
   [Designation], having office at [Address], do hereby solemnly
   affirm on oath and state as under:
   1. That I am the duly authorised signatory of the Applicant /
      Complainant / Petitioner herein under Board Resolution dated
      ____ (Exhibit / Annexure ___), and am acquainted with the
      facts and circumstances of the case from the records maintained
      by the Applicant in the ordinary course of business.
   2. That I have read and understood the contents of the
      {{case_type.pleading_type}} comprising paragraphs 1 to ___ and
      the same are true and correct.
   3. That the documents annexed are true copies / certified true
      copies / true print-outs of the originals available with the
      Applicant.

   Affirmed at [Place] on this __ day of [Month, Year].

                                       [Authorised Signatory]
                                       [Designation]

   Solemnly affirmed before me on solemn affirmation under the
   Bharatiya Sakshya Adhiniyam 2023.

                                       [Notary Public / Oath
                                        Commissioner / Tribunal
                                        Officer]

9. INDEX
   (Running paragraph-anchored index — paragraph numbers, content
   summary, exhibit references.)

10. LIST OF DOCUMENTS / EXHIBITS / ANNEXURES
    Exhibit / Annexure A — Sanction letter dated ____
    Exhibit / Annexure B — Loan Agreement dated ____
    Exhibit / Annexure C — Deed of Hypothecation dated ____
    Exhibit / Annexure D — Mortgage Deed dated ____ (registered
                          before the Sub-Registrar at ____)
    Exhibit / Annexure E — Deed of Guarantee dated ____
    Exhibit / Annexure F — Statement of Account dated ____ with
                          Section 2A Bankers' Books Evidence Act
                          1891 certificate
    Exhibit / Annexure G — First default intimation dated ____
    Exhibit / Annexure H — Recall / demand notice dated ____ with
                          proof of service
    Exhibit / Annexure I — NPA classification advice dated ____
    Exhibit / Annexure J — Post-NPA correspondence
    Exhibit / Annexure K — Board Resolution authorising the
                          litigation dated ____
    Exhibit / Annexure L — Power-of-Attorney in favour of the
                          authorised signatory (where applicable)
    ... (further case-type-specific exhibits)

11. ACCOMPANYING APPLICATIONS
    {{case_type.accompanying_applications}}
    (Common examples: application for ad-interim ex-parte
    injunction / application for waiver of pre-deposit / application
    for condonation of delay / application for exemption from
    filing certified copies / application for urgent listing /
    application for substituted service.)
```

## Statute references the plugin handles

- Recovery of Debts and Bankruptcy Act 1993 (formerly RDDBFI)
- Debts Recovery Tribunal (Procedure) Rules 1993
- Debts Recovery Appellate Tribunal (Procedure) Rules 1994
- Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002 (SARFAESI)
- Security Interest (Enforcement) Rules 2002
- Negotiable Instruments Act 1881 (Sections 138 to 147)
- Insolvency and Bankruptcy Code 2016 (Parts I to V)
- IBBI (Application to Adjudicating Authority) Rules 2016
- IBBI (Insolvency Resolution Process for Corporate Persons) Regulations 2016
- IBBI (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019
- NCLT Rules 2016
- Banking Regulation Act 1949
- Reserve Bank of India Act 1934
- RBI Master Direction on Income Recognition, Asset Classification and Provisioning pertaining to Advances 2021
- RBI Master Direction on Frauds 2016
- RBI Master Circular on Wilful Defaulters
- Code of Civil Procedure 1908 (Order 7 / Order 37 / Order 21)
- Bharatiya Nagarik Suraksha Sanhita 2023
- Bharatiya Sakshya Adhiniyam 2023
- Bankers' Books Evidence Act 1891 (Sections 2 / 2A)
- Limitation Act 1963 (Schedule I)
- Indian Contract Act 1872 (Sections 124 — 147 on indemnity, guarantee, surety)
- Transfer of Property Act 1882 (Sections 58 — 104 on mortgage)
- Registration Act 1908 (Section 17 for registered mortgage)
- Indian Stamp Act 1899 + applicable State Stamp Acts (Articles 6 / 40 for security documents)
- Companies Act 2013 (Section 77 / 86 for charge registration)
- SEBI (Issue and Listing of Debt Securities) Regulations 2008 (where corporate debentures form the security)
- FEMA 1999 + RBI ECB Master Directions (where the lending or borrowing is cross-border)
