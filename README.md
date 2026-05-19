# indian-banking-drafting

> **Open-source Claude-compatible plugin for drafting Indian banking, debt-recovery, securitisation, cheque-dishonour, and insolvency pleadings.**
>
> Six-agent drafting pipeline · ten case-type skills · case-config-aware · RDDBFI Act 1993 + SARFAESI Act 2002 + Negotiable Instruments Act 1881 + Insolvency and Bankruptcy Code 2016 + Banking Regulation Act 1949 + RBI Master Directions + Bharatiya Nagarik Suraksha Sanhita 2023 + Bharatiya Sakshya Adhiniyam 2023 discipline encoded.
>
> Released under MIT. Open infrastructure for the legal community. No commercial engagement offered through this repository — see Disclaimer below.

> ⚠️ **AI can make mistakes. Always verify the output.**
>
> This software generates assistive drafts and suggestions only. Every legal claim, citation, statute reference, procedural step, deadline calculation, and ground of relief must be independently verified by a qualified human practitioner before filing, advising a client, or relying on the output. The publisher accepts no liability for outputs used without verification.

> 🛡️ **Privacy primitive — Reader agent invokes the gateway:** This drafting plugin's **Reader agent** (the first agent in the 6-agent pipeline) calls [pseudonymisation-gateway](https://github.com/Wolfgangrush/pseudonymisation-gateway) (MIT · Wolfgang Rush) on the user's case folder BEFORE any cloud-LLM call. Real client names · government IDs · case numbers · phone numbers · currency amounts are replaced with placeholders (`[PERSON_1]` · `[AADHAAR_1]` · `[CASE_NO_1]` · etc.) in a session-scoped in-memory token map that never touches disk. Downstream agents (Format · Drafter · Verifier · Refiner) work entirely on the sanitized text. The **Overseer agent** (the final agent) calls `desanitize()` to restore real values in the final pleading before it reaches the file system. Cloud LLM vendors never see your client's real PII.


---

## Table of contents

1. [What this plugin does](#what-this-plugin-does)
2. [Case-type skills (full inventory with statutory authority)](#case-type-skills-full-inventory-with-statutory-authority)
3. [The 6-agent drafting pipeline (what each agent does)](#the-6-agent-drafting-pipeline)
4. [Installation](#installation) — Claude Desktop application
5. [Your first pleading — step-by-step walkthrough](#your-first-pleading--step-by-step-walkthrough)
6. [The `case-config.md` file](#the-case-configmd-file)
7. [Built-in compliance disciplines](#built-in-compliance-disciplines)
8. [Privacy firewall — extra discipline for banking content](#privacy-firewall--extra-discipline-for-banking-content)
9. [Why MIT License](#why-mit-license)
10. [Sibling plugins](#sibling-plugins)
11. [Why this exists](#why-this-exists)
12. [Roadmap](#roadmap)
13. [Contributing](#contributing)
14. [Contact](#contact)
15. [Author and brand](#author-and-brand)
16. [Provenance and privilege statement](#provenance-and-privilege-statement)
17. [Disclaimer and Bar Council of India Rule 36 compliance](#disclaimer-and-bar-council-of-india-rule-36-compliance)
18. [License](#license)

---

## What this plugin does

This plugin lets an Indian advocate, sitting inside the Claude Desktop application, point at a case folder on disk and obtain a complete banking / debt-recovery / securitisation / cheque-dishonour / insolvency pleading in `.docx` form — Cause Title, Parties, Statutory Opening, Prelude, Facts, Grounds, Prayer, Verification, Affidavit-in-support, Index, List of Documents, and the accompanying applications (ad-interim ex-parte injunction, attachment before judgment, waiver of pre-deposit, condonation of delay, urgent listing, substituted service, Advocate-Commissioner under Section 14(1A) SARFAESI, ad-interim moratorium under Section 96 IBC, interim compensation under Section 143A NI Act) — formatted in the forum's idiom and the case-type-specific structure, sourced from a `case-config.md` file the user places in the case folder.

The pipeline is six agents running in sequence:

1. **Reader** — extracts banking case-facts (parties, sanction, disbursement, security, account history, default trigger, NPA classification, demand-notice trajectory, cheque particulars, statutory-notice service) from the case folder with a per-document audit log, and applies the **banking-specific privacy firewall** (every party name, every account number, every sanction reference, every cheque number, every drawee-bank name, every authorised-signatory name, and every outstanding figure substituted with structural placeholders before downstream AI processing; the placeholder → real-value mapping is stored locally on the user's machine only).
2. **Format** — loads the case-type skill template, reads the user's `case-config.md`, and pre-substitutes forum name / presiding-officer designation / case-number prefix / court-fee / statutory opening / limitation anchor into a `format-shell.md` ready for the Drafter.
3. **Drafter** — writes the actual pleading. Cause Title in the correct forum nomenclature, Parties block, Statutory Opening invoking the operative section, Prelude, Facts as numbered narrative paragraphs with inline exhibit markers, Grounds with statutory anchors and document anchors, Prayer with case-type-specific reliefs, Verification, Affidavit-in-support, Index, List of Documents, and accompanying applications.
4. **Verifier** — anti-hallucination firewall **plus** statutory-currency check (CrPC 1973 → BNSS 2023 transitions; IEA 1872 → BSA 2023 transitions; Companies Act 1956 → 2013 transitions) **plus** NPA-classification cross-check against RBI Master Direction on IRAC 2021 **plus** limitation computation **plus** SARFAESI Section 13(2) ingredient discipline **plus** Section 138 NI Act ingredient discipline **plus** IBC default-threshold check **plus** Bankers' Books Evidence Act Section 2A certificate discipline **plus** Section 21 RDDBFI pre-deposit computation discipline.
5. **Refiner** — applies Verifier flags, polishes language to formal Indian tribunal / court register, enforces internal numbering and exhibit-cross-reference consistency, strips AI-style markers, and re-substitutes real party names, real account numbers, real cheque particulars, and real financial figures into the final `.docx` (strictly on the user's local machine — the underlying AI never holds real values).
6. **Overseer** — reads the polished draft with an opposing-counsel lens (borrower's counsel for a Bank pleading; Bank's counsel for a borrower's SA / IBC dispute; defence counsel for a Section 138 complaint; financial-creditor's counsel for an IBC dispute filed by the corporate debtor). Flags attackable Section 13(2) defects, weak NPA narrative, missing Section 138 ingredient pleading, broken IBC default-threshold pleading, broken limitation, weak prayer, internal contradictions, Vidya Drolia arbitrability ousters, Innoventive moratorium gaps, Sections 134 — 141 ICA personal-guarantor discharge defences, Board-Resolution defects, Section 2A BBEA defects.

The output is what an advocate would put before the Tribunal or the Court for filing — **not a template. Not a checklist. A pleading** — ready for the advocate's review, professional verification, signature, court fee, and filing.

---

## Case-type skills (full inventory with statutory authority)

The plugin ships with ten case-type skills, each covering a distinct banking / financial-recovery / insolvency case-type:

### 1. `drt-original-application-draft`

**Statutory authority:** Recovery of Debts and Bankruptcy Act 1993 (formerly RDDBFI Act) — Section 19 jurisdictional scheme + Sections 22 — 24 procedure + Sections 25 — 28 recovery; DRT (Procedure) Rules 1993. **Use case:** Bank / Financial Institution / Asset Reconstruction Company recovering a debt of ≥ ₹20 lakh (current threshold under Section 1(4); verify against latest notification) from a borrower / corporate debtor / guarantor / mortgagor. **Output:** complete Original Application with Cause Title in DRT nomenclature, Section 19 statutory opening, full Facts paragraphs anchored to sanction / disbursement / NPA / demand-notice exhibits, Grounds, Prayer with Certificate of Recovery + security confirmation + ad-interim injunction, accompanying IAs.

### 2. `sarfaesi-13-2-notice-draft`

**Statutory authority:** Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002 — Section 13(2) read with Rule 3 of the Security Interest (Enforcement) Rules 2002; *Mardia Chemicals v. Union of India* (2004) 4 SCC 311; *Authorised Officer of UCO Bank* line. **Use case:** secured creditor's pre-enforcement demand notice for an NPA-classified account. **Output:** complete 13(2) notice with statement of secured debt, 60-day window, Section 13(3A) representation right, Schedule of Secured Asset, Section 2A BBEA certificate enclosure, service-mode discipline. **Ingredient-omission landmines** flagged — failure to identify break-up of secured debt, failure to state 60-day window, failure to enclose Section 2A certificate, failure to state Section 13(3A) representation right.

### 3. `sarfaesi-17-securitisation-application-draft`

**Statutory authority:** SARFAESI Act 2002 — Section 17 read with Rule 11 of the Security Interest (Enforcement) Rules 2002; *Mardia Chemicals* (2004) framework; Section 17(3) limited-inquiry scope. **Use case:** borrower / guarantor / mortgagor / aggrieved person challenging a measure under Section 13(4) — possession / sale / management — before the DRT within 45 days. **Output:** complete Securitisation Application with Section 13(2) ingredient defects pleaded with particularity, Section 13(3A) representation non-consideration, Rule 8 / Rule 9 procedural defects, prayer for setting aside the measure + restoration of possession. **Mandatory remedy-channel disclosure** — *United Bank of India v. Satyawati Tondon* (2010) 8 SCC 110 framework on writ-petition forum-shopping.

### 4. `sarfaesi-14-cmm-dm-application-draft`

**Statutory authority:** SARFAESI Act 2002 — Section 14 read with Section 14(1A) Advocate-Commissioner mechanism; the post-2016-amendment 30-day disposal discipline (third proviso to Section 14(1)); *Standard Chartered Bank v. V. Noble Kumar* (2013) 9 SCC 620 — affidavit-of-9-points discipline. **Use case:** secured creditor seeking CMM / DM assistance in taking physical possession of a secured asset where Section 13(4) possession-taking is obstructed. **Output:** complete Section 14 application with the Noble Kumar 9-point affidavit, prayer for Advocate-Commissioner appointment, prayer for police assistance, 30-day disposal prayer.

### 5. `ni-act-138-complaint-draft`

**Statutory authority:** Negotiable Instruments Act 1881 — Sections 138 to 147; Section 142(2) post-2015-amendment territorial jurisdiction; *Krishna Janardhan Bhat v. Dattatraya G. Hegde* (2008) 4 SCC 54 on Section 139 presumption; *S.M.S. Pharmaceuticals v. Neeta Bhalla* (2005) 8 SCC 89 on Section 141 (company / partnership) discipline; Section 143A interim compensation (post-2018-amendment); Section 143 summary-trial discipline. **Use case:** cheque dishonour for insufficiency / exceeds arrangement / account closed / payment stopped / similar Section 138-actionable reason; payee complaint against drawer. **Output:** complete Section 138 complaint with each statutory ingredient pleaded, BNSS 2023 statutory frame (Section 223 BNSS), Section 142(2) jurisdictional anchor, Section 141 directors / partners arraying where applicable, prayer for cognizance + summons + Section 143A interim compensation + Section 143 summary trial.

### 6. `ni-act-138-reply-notice-draft`

**Statutory authority:** Negotiable Instruments Act 1881 — proviso (b) to Section 138; Section 139 burden-shift on rebuttal; *Krishna Janardhan Bhat* (2008) framework. **Use case:** drawer / accused responding to the payee's statutory pre-litigation notice, preserving defences before Section 138 complaint is filed. **Output:** complete reply notice with each potential defence (cheque not for legally enforceable debt / cheque as security only / signature denied / material alteration / cheque presented post-validity / statutory-notice defects / payment already made / discharge under Section 82 NI Act) pleaded affirmatively without admission of underlying debt. **Anti-admission discipline** — careful not to admit underlying debt while contesting statutory ingredients.

### 7. `civil-recovery-suit-draft`

**Statutory authority:** Code of Civil Procedure 1908 — Order 7 (ordinary plaint for recovery of money) / Order 37 (summary suit on a written contract / promissory note / bill of exchange / cheque) / Order 34 (mortgage suit); applicable State Court-Fees Act; *Mechanlec Engineers v. Basic Equipment Corporation* (1976) 4 SCC 687 + *IDBI Trusteeship v. Hubtown* (2017) 1 SCC 568 on leave-to-defend threshold; Section 34 SARFAESI civil-court-bar; *Mardia Chemicals* (2004) + *Jagdish Singh v. Heeralal* (2014) 1 SCC 479. **Use case:** lender (Bank / NBFC / individual / company) below DRT pecuniary threshold of ₹20 lakh — OR non-Bank lender — recovering on a written contract / promissory note / cheque / written guarantee. **Output:** complete plaint with statutory opening adapted for Order 7 / Order 37 variant, full Facts paragraphs, mortgage-suit framework (Order 34) where applicable, prayer with decree + Order 37 summons request, accompanying IAs (Order 38 attachment before judgment / Order 39 injunction / Order 40 Receiver).

### 8. `ibc-section-7-application-draft`

**Statutory authority:** Insolvency and Bankruptcy Code 2016 — Section 7 (Financial Creditor application) + Section 4 default threshold + Section 5(7) / 5(8) Financial-Creditor / Financial-Debt definitions + Section 14 moratorium + Section 60(1) territorial jurisdiction + Section 10A suspension window; IBBI (Application to Adjudicating Authority) Rules 2016 (Form 1 filing discipline); *Innoventive Industries v. ICICI Bank* (2018) 1 SCC 407 (admission framework); *Vashdeo R. Bhojwani v. Abhyudaya Co-operative Bank* (2019) 9 SCC 158 + *Babulal Vardharji Gurjar v. Veer Gurjar* (2020) 15 SCC 1 (limitation under Article 137 from date of default). **Use case:** Financial Creditor initiating Corporate Insolvency Resolution Process against a Corporate Debtor before NCLT for default of ≥ ₹1 crore. **Output:** complete Section 7 application with Form 1 structure, Part IV financial-debt particulars, Part V documentary evidence, proposed IRP particulars in Form 2, prayer for admission + moratorium + IRP appointment.

### 9. `ibc-section-95-application-draft`

**Statutory authority:** Insolvency and Bankruptcy Code 2016 — Section 95 (Personal Guarantor application) + Section 60(2) NCLT jurisdiction + Section 78 default threshold (₹1,000) + Section 96 interim moratorium + Section 99 RP report stage + Section 100 admission stage + Section 101 final moratorium; IBBI (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019; *Lalit Kumar Jain v. Union of India* (2021) 9 SCC 321 (constitutional validity affirmed); *State Bank of India v. Mahendra Kumar Jajodia* (2022). **Use case:** creditor initiating Insolvency Resolution Process against a personal guarantor to a corporate debtor before NCLT (where corporate-debtor CIRP is pending) or before DRT (Part III IBC route). **Output:** complete Section 95 application with Form C structure, Deed of Guarantee + invocation notice exhibits, proposed RP particulars, prayer for admission + moratorium + RP appointment. **Sections 134 — 141 ICA discharge defences** pre-empted in the pleading.

### 10. `drat-appeal-draft`

**Statutory authority:** Recovery of Debts and Bankruptcy Act 1993 — Section 20 (appeal to DRAT) + Section 21 (pre-deposit discipline) + 45-day limitation under Section 20(3); DRAT (Procedure) Rules 1994; *Narayan Chandra Ghosh v. UCO Bank* (2011) 4 SCC 548 (pre-deposit non-waivable but reducible to 25%); Section 18 SARFAESI Act 2002 for appeal from a Section 17 SA order. **Use case:** Bank or borrower aggrieved by a DRT order — appeal to the DRAT bench corresponding to the DRT. **Output:** complete Memorandum of Appeal with Grounds (erroneous appreciation / misapplication of law / procedural irregularity / quantum miscalculation / limitation / jurisdiction / Section 17(3) scope), Prayer, accompanying IAs (waiver / reduction of pre-deposit / stay of recovery / condonation of delay / urgent listing).

### Shared infrastructure skills

- **`_drafting_common`** — anti-pollution rules, banking-specific privacy firewall, AI-style-marker blacklist, citation discipline, **statutory currency rules** (CrPC → BNSS / IEA → BSA / Companies Act 1956 → 2013 transitions), **Section 138 NI Act jurisdictional rule** (post-Section 142(2)-amendment drawee-bank-branch jurisdiction), **IBC default-threshold rules**, **SARFAESI Section 13(2) ingredient discipline**, **DRAT pre-deposit discipline**, **Limitation Act 1963 Article map**, **Bankers' Books Evidence Act 1891 Section 2A discipline**, **Vidya Drolia non-arbitrability framework**.
- **`_banking_drafting_base`** — universal Indian banking pleading skeleton (Cause Title, Parties block, Statutory Opening, Prelude, Facts, Grounds, Prayer, Verification, Affidavit-in-support, Index, List of Documents, accompanying applications).

---

## The 6-agent drafting pipeline

| Agent | What it reads | What it writes | Key banking-domain specialisation |
|---|---|---|---|
| **`reader`** | Every file in the case folder + the case-type skill's expected exhibits list | `case-facts.md` with per-document audit log + privacy-firewalled placeholder mapping in the header | Privacy firewall — substitutes party names + account numbers + sanction references + cheque particulars + outstanding figures before downstream AI processing; mapping stored locally only |
| **`format`** | `case-facts.md` + `case-config.md` + case-type SKILL.md + `_banking_drafting_base` | `format-shell.md` with forum / case-number-prefix / court-fee / statutory-opening / limitation-anchor pre-substituted | Resolves DRT vs DRAT vs NCLT vs CMM / DM vs civil-court nomenclature for the Cause Title |
| **`drafter`** | `case-facts.md` + `format-shell.md` + case-type SKILL.md + `_banking_drafting_base` + law PDFs | `draft-v1.md` + `draft-v1.docx` | Writes Cause Title + Parties + Statutory Opening + Prelude + Facts (with inline exhibit markers) + Grounds + Prayer + Verification + Affidavit + Index + List of Documents + accompanying applications |
| **`verifier`** | `draft-v1.md` + `case-facts.md` + `case-config.md` + law PDFs | `verification-report.md` | Anti-hallucination + statutory-currency (CrPC → BNSS / IEA → BSA) + NPA-classification cross-check against RBI MD IRAC 2021 + limitation Article map + SARFAESI Section 13(2) ingredient discipline + Section 138 NI Act ingredient discipline + IBC default-threshold check + Bankers' Books Evidence Act Section 2A certificate discipline + Section 21 RDDBFI pre-deposit computation |
| **`refiner`** | `draft-v1.md` + `verification-report.md` + `case-config.md` + `case-facts.md` | `draft-v2.md` + `draft-v2.docx` | Polish to Indian tribunal / court formal register + internal numbering / cross-reference / exhibit-marker consistency + privacy-firewall reversal (real values re-substituted from local mapping into final `.docx`) |
| **`overseer`** | `draft-v2.md` + `case-facts.md` + `case-config.md` | `opposing-notes.md` + `final-draft.docx` | Opposing-counsel critique — Section 13(2) defects, NPA narrative weakness, Board Resolution / Section 2A BBEA defects, Section 17 SA standing, Vidya Drolia arbitrability bar, Section 138 defence preview, IBC moratorium gaps, Sections 134 — 141 ICA personal-guarantor discharge defences |

---

## Installation

This is a Claude-compatible plugin in the Anthropic plugin format, designed to run inside the **Claude Desktop application** (available at <https://claude.ai/download>). The plugin folder location depends on your OS:

| OS | Plugin folder path |
|---|---|
| **macOS** | `~/Library/Application Support/Claude/plugins/` |
| **Windows** | `%APPDATA%\Claude\plugins\` (typically `C:\Users\<you>\AppData\Roaming\Claude\plugins\`) |
| **Linux** | `~/.config/Claude/plugins/` |

Clone the plugin into that folder:

```bash
# macOS / Linux
mkdir -p ~/Library/Application\ Support/Claude/plugins   # adjust per OS table
cd ~/Library/Application\ Support/Claude/plugins
git clone https://github.com/Wolfgangrush/indian-banking-drafting-litigation.git indian-banking-drafting

# Windows (PowerShell)
mkdir -Force $env:APPDATA\Claude\plugins
cd $env:APPDATA\Claude\plugins
git clone https://github.com/Wolfgangrush/indian-banking-drafting-litigation.git indian-banking-drafting
```

Restart the Claude Desktop application. The plugin is auto-discovered on the next session start.

### Anthropic Plugin Marketplace (when available)

When the plugin lands on the Anthropic Plugin Marketplace, you will be able to install it from inside the application's plugin browser without `git`. Until then, the manual clone steps above are canonical.

### Verifying the install

In a Claude session, type:

- *"draft DRT OA"* — triggers `drt-original-application-draft`
- *"draft SARFAESI 13(2) notice"* — triggers `sarfaesi-13-2-notice-draft`
- *"draft SARFAESI SA"* — triggers `sarfaesi-17-securitisation-application-draft`
- *"draft Section 14 SARFAESI"* — triggers `sarfaesi-14-cmm-dm-application-draft`
- *"draft Section 138 complaint"* — triggers `ni-act-138-complaint-draft`
- *"draft reply to 138 notice"* — triggers `ni-act-138-reply-notice-draft`
- *"draft recovery suit"* / *"draft summary suit"* — triggers `civil-recovery-suit-draft`
- *"draft Section 7 IBC"* — triggers `ibc-section-7-application-draft`
- *"draft Section 95 IBC"* — triggers `ibc-section-95-application-draft`
- *"draft DRAT appeal"* — triggers `drat-appeal-draft`

---

## Your first pleading — step-by-step walkthrough

Suppose you wish to draft a **DRT Original Application** under Section 19 of the RDDBFI Act 1993, for a Bank seeking recovery of a corporate debt of ₹3.5 crore secured by hypothecation and corporate guarantee.

### Step 1 — create a case folder

```
~/Desktop/cases/
└── drt-oa-2026-NPA-MATTER/
    ├── case-config.md         ← declares forum + claim quantum + security position + NPA date
    ├── inputs/
    │   ├── sanction-letter.pdf
    │   ├── loan-agreement.pdf
    │   ├── deed-of-hypothecation.pdf
    │   ├── corporate-guarantee.pdf
    │   ├── statement-of-account.pdf
    │   ├── section-2a-bbea-certificate.pdf
    │   ├── npa-classification-advice.pdf
    │   ├── recall-notice.pdf
    │   ├── proof-of-service.pdf
    │   └── board-resolution-authorising-filing.pdf
    └── laws/
        ├── rddbfi-act-1993.pdf
        ├── drt-procedure-rules-1993.pdf
        ├── bankers-books-evidence-act-1891.pdf
        └── limitation-act-1963.pdf
```

### Step 2 — write `case-config.md`

```yaml
forum: "Debts Recovery Tribunal, Mumbai-I"
case_type: "drt-original-application"
case_number_year: 2026
claim_quantum_rupees: 35000000          # ₹3.5 crore
security_position: "hypothecation_plus_corporate_guarantee"
npa_classification_date: "[NPA-Date-Placeholder]"
demand_notice_date: "[Demand-Notice-Date-Placeholder]"
demand_notice_window_days: 60
default_date: "[Default-Date-Placeholder]"
applicable_state_court_fees_act: "Bombay Court-Fees Act 1959"
limitation_article: "Article 19"
limitation_anchor_date: "[Date-of-Default-Placeholder]"
limitation_filing_date: "[Date-of-Filing-Placeholder]"
authorised_signatory_role: "Chief Manager"
board_resolution_date: "[BR-Date-Placeholder]"
parties:
  - role: "Applicant"
    party_type: "Public Sector Bank"
    party_name: "[Bank-Name-Placeholder]"
  - role: "Defendant No. 1"
    party_type: "Borrower (Pvt Ltd Company)"
    party_name: "[Borrower-Name-Placeholder]"
  - role: "Defendant No. 2"
    party_type: "Corporate Guarantor"
    party_name: "[Guarantor-Name-Placeholder]"
  - role: "Defendant No. 3"
    party_type: "Personal Guarantor"
    party_name: "[Personal-Guarantor-Name-Placeholder]"
```

### Step 3 — invoke the plugin

Open Claude Desktop, navigate to the case folder, and type:

> *draft DRT OA*

The pipeline runs:

1. **Reader** reads every PDF in `inputs/`, builds `case-facts.md` with privacy-firewalled placeholder mapping, validates that all required statutes are in `laws/`.
2. **Format** loads the `drt-original-application-draft` skill, reads `case-config.md`, builds `format-shell.md`.
3. **Drafter** writes `draft-v1.md` and `draft-v1.docx`.
4. **Verifier** reads `draft-v1.md` against `case-facts.md`, writes `verification-report.md`.
5. **Refiner** applies the verification flags, polishes the prose, re-substitutes real values, writes `draft-v2.docx`.
6. **Overseer** reads `draft-v2.docx` with a borrower's-counsel lens, writes `opposing-notes.md` and `final-draft.docx`.

The advocate now reviews `final-draft.docx` against `opposing-notes.md`, makes professional adjustments, applies court fee, signs the verification, swears the affidavit, and files.

---

## The `case-config.md` file

This file declares all forum-level / case-type-level / matter-level constants that the plugin substitutes into the format shell. Keep it on the user's local machine — `.gitignore` excludes it from any git repo.

Minimum fields:

- `forum` — exact name of the tribunal / court (e.g. *"Debts Recovery Tribunal, Mumbai-I"* / *"National Company Law Tribunal, Mumbai Bench"* / *"Court of the Chief Metropolitan Magistrate, Esplanade, Mumbai"* / *"Court of the Civil Judge Senior Division at ___"*)
- `case_type` — one of the ten supported case types
- `case_number_year` — current year for case-number placeholder
- `claim_quantum_rupees` — the principal claim figure (or the cheque amount / debt threshold)
- `security_position` — *"unsecured"* / *"hypothecation"* / *"equitable_mortgage"* / *"registered_mortgage"* / *"corporate_guarantee"* / *"personal_guarantee"* / *"pledge_of_shares"* / etc.
- `npa_classification_date` — RBI MD IRAC 2021 NPA classification date (Bank-side pleadings)
- `demand_notice_date` + `demand_notice_window_days`
- `default_date` — date of first default
- `applicable_state_court_fees_act` — for civil-court pleadings
- `limitation_article` + `limitation_anchor_date` + `limitation_filing_date`
- `authorised_signatory_role` + `board_resolution_date`
- `parties` — list of party-role + party-type + party-name-placeholder

Case-type-specific fields (for the relevant skill) layer on top of the minimum schema — see each case-type SKILL.md.

---

## Built-in compliance disciplines

The Verifier enforces several disciplines mandatory in Indian banking practice — see `skills/_drafting_common/SKILL.md` for the full discipline framework. Headline disciplines:

- **RBI Master Direction on IRAC 2021** — NPA classification date and basis cross-checked against the 90-day overdue rule (term loan) / 90-day out-of-order rule (cash credit / OD)
- **SARFAESI Section 13(2) ingredient discipline** — 60-day window, secured-debt break-up, Section 13(3A) representation right, Section 2A BBEA certificate enclosure, mode of service per Rule 3 Security Interest (Enforcement) Rules 2002
- **Section 138 NI Act ingredient discipline** — legally-enforceable-debt averment, cheque-validity period, return-memo timing, statutory-notice timing, 30-day complaint-window discipline, Section 142(2) jurisdiction
- **IBC default-threshold discipline** — Section 7 (₹1 crore current threshold), Section 95 (₹1,000 personal-guarantor threshold), Section 10A suspension-window check
- **DRAT pre-deposit discipline** — Section 21 RDDBFI 50% pre-deposit (reducible to 25%, not waivable) per *Narayan Chandra Ghosh*
- **Limitation Act 1963 discipline** — applicable Article per case-type, Section 18 acknowledgement of debt, Section 5 delay-condonation grounds
- **Bankers' Books Evidence Act 1891 Section 2A** — Statement-of-Account certification by the manager / authorised officer
- **Statutory-currency discipline** — CrPC 1973 references converted to BNSS 2023 (Section 200 → 223; Section 482 → 528); IEA 1872 references converted to BSA 2023 (Section 65B → 63; Section 126 → 132); Companies Act 1956 references converted to Companies Act 2013
- **Vidya Drolia non-arbitrability discipline** — SARFAESI / DRT / IBC matters non-arbitrable; Section 8 A&C objections by borrowers / corporate debtors anticipated and pre-empted
- **Innoventive Industries IBC admission discipline** — at admission stage only default + completeness + IRP eligibility are examined; merits not re-adjudicated

---

## Privacy firewall — extra discipline for banking content

Banking pleadings contain some of the most sensitive material an advocate handles — KYC of borrowers, loan account numbers, sanction references, NPA classifications, security descriptions, valuation reports, cheque numbers, drawee-bank names, authorised-signatory identities, board-resolution references. The plugin's privacy discipline is therefore stricter than the generic discipline of sibling plugins:

1. **Reader** substitutes every party name (Bank, Borrower, Guarantor, Mortgagor, Authorised Signatory), every account number, every sanction reference, every cheque number, every drawee-bank name, every outstanding figure, and every authorised-signatory name with structural placeholders before downstream processing.
2. The placeholder → real-value mapping is stored in the header of `case-facts.md` on the user's local machine **only**.
3. **Format / Drafter / Verifier / Overseer** operate **only** on placeholder-substituted content. The underlying AI runtime never holds raw account numbers or raw financial figures.
4. **Refiner** re-substitutes real values into the final `.docx`, strictly on the user's machine.
5. `.gitignore` excludes `case-facts.md` and `case-config.md` so they cannot be committed accidentally.

The user can verify the firewall by inspecting `case-facts.md` after the Reader runs — every party name appears as `[Party-A]` / `[Party-B]`, every account number as `[Loan-Account-Placeholder]`, every cheque number as `[Cheque-No.-Placeholder]`. The mapping is in the header of the same file.

---

## Why MIT License

The MIT licence is the most permissive widely-recognised open-source licence. Anyone may use, modify, distribute, sublicense, or sell the plugin or any derivative. The licence is short, well-understood, and compatible with every other open-source licence the legal community is likely to encounter. No proprietary gating, no field-of-use restriction, no contributor licence agreement (CLA) gymnastics. The accompanying `NOTICE.md` does not modify the licence — it documents the provenance and the privilege position so that any future audit can verify the plugin's clean origin.

---

## Sibling plugins

This plugin is one in the **Wolfgang Rush** family of Indian legal-drafting plugins. All thirteen siblings ship under the same six-agent pipeline (Reader → Format → Drafter → Verifier → Refiner → Overseer) and the family-of-plugins doctrine — each plugin narrowly scoped to one practice area / forum:

| Plugin | GitHub repo | Scope |
|---|---|---|
| `supreme-court-drafting` | [supreme-court-drafting-litigation](https://github.com/Wolfgangrush/supreme-court-drafting-litigation) | SLPs · Writ Art 32 · Transfer · Review · Curative — Supreme Court of India |
| `indian-hc-drafting` | [indian-hc-drafting-litigation](https://github.com/Wolfgangrush/indian-hc-drafting-litigation) | Pleadings across all 25 Indian High Courts (bench-config-aware) |
| `district-court-drafting` | [district-court-drafting-litigation](https://github.com/Wolfgangrush/district-court-drafting-litigation) | Plaints · WS · CPC applications · BNSS complaints across 25+ States (state-config) |
| `indian-family-drafting` | [indian-family-drafting-litigation](https://github.com/Wolfgangrush/indian-family-drafting-litigation) | HMA · SMA · IDA · matrimonial · custody · DV Act · maintenance · adoption |
| `indian-contracts-drafting` | [indian-contracts-drafting-litigation](https://github.com/Wolfgangrush/indian-contracts-drafting-litigation) | MSA · NDA · employment · lease · sale · GPA · SHA · will · loan · arbitration |
| `indian-banking-drafting` (this) | [indian-banking-drafting-litigation](https://github.com/Wolfgangrush/indian-banking-drafting-litigation) | DRT · SARFAESI · NI Act 138 · IBC §7 / §95 · DRAT |
| `indian-labour-drafting` | [indian-labour-drafting-litigation](https://github.com/Wolfgangrush/indian-labour-drafting-litigation) | ID Act · POSH · PG · EPF · ESI · MW · IESO + State exemplars |
| `indian-property-drafting` | [indian-property-drafting-litigation](https://github.com/Wolfgangrush/indian-property-drafting-litigation) | Gift · Exchange · Release · Trust · Wakf · Easement · Partition · Settlement · Mortgage · TIR |
| `indian-company-drafting` | [indian-company-drafting](https://github.com/Wolfgangrush/indian-company-drafting) | NCLT (241/242 · 245 · 230-232 · 66 · 252 · 213) · NCLAT (421 + 61) · IBC §9 / §10 |
| `indian-tax-drafting` | [indian-tax-drafting](https://github.com/Wolfgangrush/indian-tax-drafting) | Form 35 CIT(A) · Form 36 ITAT · Form 10A · Sec 148A · 263/264 · 271/270A · 144C · 201 · 260A |
| `indian-consumer-drafting` | [indian-consumer-drafting](https://github.com/Wolfgangrush/indian-consumer-drafting) | District / State / NCDRC + medical-negligence + product liability |
| `indian-mact-drafting` | [indian-mact-drafting](https://github.com/Wolfgangrush/indian-mact-drafting) | MV Act 1988 (2019 amended) · Sarla Verma + Pranay Sethi · state-config |
| `indian-ip-drafting` | [indian-ip-drafting](https://github.com/Wolfgangrush/indian-ip-drafting) | Copyright · Trade Marks · Patents · Designs + HC IP Divisions (post-IPAB-abolition) + Anton Piller / John Doe |

Each plugin can be installed independently, each plugin's Rule 36 firewall is narrow and reviewable, each plugin's bench / forum discipline is depth-validated within its scope, and the user installs only what they need.

---

## Why this exists

Indian banking practice currently has no open-source pleading-drafting infrastructure. Practising advocates piece together pleadings from their own past drafts, from senior advocates' templates, from the various textbook precedent collections (Tannan, Mookerjee, Mulla, Sumant Batra), and from such precedent volumes as the publishers issue from time to time. The result is uneven quality, uneven compliance with the latest statutory-currency rules (BNSS 2023 / BSA 2023 / Companies Act 2013), uneven discipline on the procedural traps (Section 13(2) ingredients, Section 138 ingredients, IBC thresholds, Section 21 pre-deposit), and routine omissions that opposing counsel exploit.

A plugin that codifies the procedural skeletons + the statutory-currency rules + the Verifier-side discipline + the privacy firewall is the first piece of infrastructure that the Indian banking practice has had — the second piece is community contribution from advocates who file regularly in specific DRT / NCLT / Magistrate-court benches and who deepen the bench-specific Practice Directions discipline.

Foreign legal-AI tools cannot fill this gap. The procedural conventions are jurisdiction-specific; the statutory framework is BNSS / BSA / IBC / SARFAESI / RDDBFI which no foreign training data has indexed at depth; the formatting requirements at the Registry counter of a DRT / NCLT / Magistrate court are matters of bench practice that no foreign tool has encountered.

This plugin opens that door.

---

## Roadmap

- [x] **v0.1.0-alpha (current)** — universal banking pleading skeleton + 10 case-type skills + 6-agent pipeline + privacy firewall + Verifier disciplines + 0 bench-specific exemplars
- [ ] **v0.1.x** — bug fixes, quality-gate iteration, language-register polish, formatting refinements driven by user feedback
- [ ] **v0.x onward** — bench-specific Practice Direction calibration deepening per DRT / DRAT / NCLT bench, additional case-type skills (Section 9 IBC operational-creditor / DRT recovery-officer-stage / Section 13(8) auction-purchaser challenges / Section 138 NI Act compounding application), and procedural-rule updates as they arrive
- [ ] **v1.0.0** — stable release after community-validated formatting and field-testing

Per-bench deep validation will arrive in the order advocates contribute. The plugin's case-config architecture means any advocate filing regularly before a given DRT / NCLT / Magistrate court can deepen the calibration for that bench by opening an issue or pull request with their bench's idiom — no central roadmap is needed to enable that. The roadmap above is therefore intentionally open-ended.

---

## Contributing

Advocates with regular banking / debt-recovery / cheque-dishonour / insolvency practice are invited to contribute bench-config calibration for the specific tribunal / court they practise before. Open a GitHub issue with:

- Your practice bench (e.g., *"DRT Delhi-III"* / *"NCLT Mumbai Bench Court IV"* / *"Esplanade Magistrate Court, Mumbai"*)
- Your bench's Cause Title format
- Your bench's case-number convention
- Your bench's filing-counter conventions (annexure markers / index format / verification format)
- Recent Practice Directions issued by the bench affecting pleading format

Pull requests are welcome with a one-paragraph explanation of the change and a reference to the bench rule or Practice Direction that justifies it.

This plugin is open source under MIT.

---

## Contact

Author and maintainer: **Rushikesh R. Mahajan**, Advocate, enrolled with the Bar Council of Maharashtra and Goa.

GitHub: <https://github.com/Wolfgangrush>

Issues raised with reproducible context are handled on a best-effort basis; this is an open-source contribution maintained outside the author's professional engagements and does not constitute a vehicle for legal services.

---

## Author and brand

The author is **Rushikesh R. Mahajan**, Advocate, practising before the Bombay High Court, Nagpur Bench. The plugin is published under the open-source brand **Wolfgang Rush**, which is the author's publishing handle for legal-technology infrastructure. Personal accountability under the Advocates Act 1961 attaches to the author regardless of the use of a publishing handle.

---

## Provenance and privilege statement

See `NOTICE.md` for the full provenance + privilege + privacy + Rule 36 compliance statement. The short version:

- The plugin contains only universal procedural skeletons, formatting conventions, statutory references, and generic placeholders
- The plugin contains no specific client matter, no client communications, no client documents, no personal data of any data principal, and no tracking / telemetry / analytics
- The plugin is, in legal character, identical to a published banking-law textbook — procedural knowledge in machine-readable form
- The author retains full enrolment, full responsibility, and full liability under the Advocates Act 1961 and the Bar Council of India Rules

---

## Compliance posture — Supreme Court e-Committee AI framework

This plugin is **assistive drafting infrastructure**, not autonomous decision-making software. Its operational posture is aligned with the Supreme Court of India e-Committee's stated position on AI in legal work.

> *"AI and digital tools must be used as supportive instruments and should not be allowed to override judicial reasoning."*
>
> — **Justice Rajesh Bindal**, Judge, Supreme Court of India
> [*Judicial Process Re-engineering and Digital Transformation*](https://www.sci.gov.in/press-release-dated-april-12-2026/) conference, 11–12 April 2026
> Organised by the Supreme Court e-Committee in collaboration with the Department of Justice, Government of India.
> ([Coverage — Law Trend](https://lawtrend.in/ai-must-not-replace-judicial-reasoning-warns-supreme-court-justice-rajesh-bindal/))

The same posture underpins the Supreme Court's own AI infrastructure for the judiciary:

- **[SUPACE](https://www.drishtiias.com/daily-news-analysis/ai-portal-supace)** — *Supreme Court Portal for Assistance in Court Efficiency.* AI-enabled assistive tool launched on 6 April 2021 by then-CJI S.A. Bobde. Provides legal research, fact extraction, document review, and drafting assistance to judges and legal researchers. **By design, SUPACE is not a decision-making system** — it processes facts and surfaces them to the human user. The Supreme Court has recommended adoption across all Indian High Courts.

- **[SUVAS](https://www.drishtijudiciary.com/current-affairs/supreme-court-vidhik-anuvaad-software-suvas)** — *Supreme Court Vidhik Anuvaad Software.* AI-powered translation tool launched in November 2019 by then-CJI S.A. Bobde. Translates judicial documents, orders, and judgments between English and ten Indian regional languages.

### What this plugin does — and does not — do under that framework

**Does:**

- Generate structural skeletons of pleadings, drawing on public statutes, schedule forms, and court rules.
- Run a six-agent assistive pipeline (Reader → Formatter → Drafter → Verifier → Refiner → Overseer) over the user's case facts.
- Surface citations, procedural anchors, and bench-specific conventions for advocate review.

**Does NOT:**

- Generate final filings autonomously.
- Substitute for advocate professional judgment.
- Replace human verification.
- Operate without an enrolled advocate retaining full professional responsibility.

**Every draft produced through this plugin must be advocate-owned and human-verified before filing.** The enrolled advocate using this plugin retains full professional responsibility under the Advocates Act 1961 and the Bar Council of India Rules, including verification of facts, accuracy of citations, correctness of legal grounds, propriety of the prayer, and signature on every pleading filed.

This is the same standard the Supreme Court itself applies to its own AI infrastructure (SUPACE / SUVAS): **AI as supportive instrument, never as decision-maker.**

---

## Disclaimer and Bar Council of India Rule 36 compliance

This repository is published as a personal open-source contribution to the legal-technology ecosystem. It is **not** an advertisement of professional services, **not** a solicitation of work, **not** an undertaking to act as counsel in any matter, and **not** a vehicle through which the author accepts professional engagement.

Bar Council of India Rule 36 of the Standards of Professional Conduct and Etiquette prohibits an advocate from soliciting work or advertising professional services through any medium. This repository complies with Rule 36 in both letter and spirit:

- No commercial offering is made through this repository
- No representation of professional results is made
- No invitation to engage the author professionally is made
- The README contains no contact details inviting professional retainer

The plugin is published in the same legal character as any practitioner's open-source library, public continuing-legal-education contribution, or published textbook chapter — the medium is software, the content is procedural knowledge, the practitioner retains full Bar discipline and accountability.

---

## License

MIT — see `LICENSE`.
