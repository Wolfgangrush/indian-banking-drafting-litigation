---
name: _drafting_common
description: Shared reference for all 10 banking / financial-recovery / insolvency drafting skills. Holds the anti-pollution rules, the banking privacy firewall protocol (party names + account numbers + cheque particulars + outstanding figures substituted with placeholders before downstream AI processing; real-value re-substitution local-only in the Refiner step), the AI-style-marker blacklist, citation discipline, statutory currency rules (RDDBFI / SARFAESI / NI Act / IBC / Banking Regulation Act / RBI Master Directions / BNSS / BSA / CPC / Bankers' Books Evidence Act), the Section 138 NI Act jurisdictional rule per the Section 142(2) amendment, the IBC default threshold rules, the SARFAESI Section 13(2) ingredient discipline, the DRAT pre-deposit discipline, the Limitation Act 1963 Article map, and the Bankers' Books Evidence Act 1891 Section 2A discipline. NOT invoked directly — referenced from every case-type skill in this plugin.
allowed-tools: Read
---

# `_drafting_common` — shared banking drafting infrastructure

## Privacy firewall

Banking pleadings routinely contain highly sensitive material — KYC data of borrowers, loan account numbers, sanction references, NPA classifications, security descriptions, valuation reports, cheque numbers, drawee-bank names, authorised-signatory identities, board-resolution references, statement-of-account figures. The plugin's privacy discipline:

1. **Reader** substitutes every party name, every account number, every sanction reference, every cheque number, every drawee-bank name, every outstanding figure, and every authorised-signatory name with structural placeholders before downstream processing.
2. The placeholder → real-value mapping is stored in the header of `case-facts.md` on the user's local machine **only**.
3. **Format / Drafter / Verifier / Overseer** operate **only** on placeholder-substituted content. The underlying AI runtime never holds raw account numbers or raw financial figures.
4. **Refiner** re-substitutes real values into the final `.docx`, strictly on the user's machine.
5. `.gitignore` excludes `case-facts.md` and `case-config.md` so they cannot be committed accidentally.

## AI-style-marker blacklist

Stripped by the Refiner before output:

- Em-dash (`—`) used as sentence-internal pause (replaced with semicolon or comma-bounded clause)
- Sentence-final *thereby* / *hereby* / *whereby* without an attached verb
- *Moreover*, *furthermore*, *additionally*, *in addition* as sentence-openers — replaced with *"The Applicant submits that"* / *"The Applicant further submits that"*
- *Navigate*, *delve*, *foster*, *robust*, *seamless* (metaphorical uses)
- *It is important to note that*, *it should be noted that*, *worthy of note* — replaced with direct prose
- Bullet-list-style structure in operative paragraphs (operative paragraphs are numbered, not bulleted)

## Citation discipline

The Drafter does **not** generate case names + citations from training memory. Every case citation in any explanatory note or recital must trace to a user-supplied source. Untraceable citations become `[CITATION NEEDED]` placeholders.

Headline cases the Verifier scans for fabrication:

- *Mardia Chemicals Ltd. v. Union of India* (2004) 4 SCC 311 — constitutional validity of SARFAESI; Section 17 remedy framework
- *Transcore v. Union of India* (2008) 1 SCC 125 — bank can pursue parallel SARFAESI and DRT remedies
- *United Bank of India v. Satyawati Tondon* (2010) 8 SCC 110 — discipline against writ-petition forum-shopping when SARFAESI alternative exists
- *Innoventive Industries Ltd. v. ICICI Bank* (2018) 1 SCC 407 — IBC moratorium scheme + Section 14 operation
- *Swiss Ribbons Pvt. Ltd. v. Union of India* (2019) 4 SCC 17 — IBC constitutional validity
- *Vidya Drolia v. Durga Trading Corporation* (2021) 2 SCC 1 — arbitrability bar (SARFAESI / DRT / IBC non-arbitrable)
- *Lalit Kumar Jain v. Union of India* (2021) 9 SCC 321 — IBC Part III for personal guarantors to corporate debtors
- *Dashrath Rupsingh Rathod v. State of Maharashtra* (2014) 9 SCC 129 — Section 138 territorial jurisdiction (subsequently displaced by the Section 142(2) NI Act amendment 2015 — drawee-bank-branch jurisdiction)
- *Krishna Janardhan Bhat v. Dattatraya G. Hegde* (2008) 4 SCC 54 — Section 139 NI Act presumption + burden shift
- *Vashdeo R. Bhojwani v. Abhyudaya Co-operative Bank* (2019) 9 SCC 158 — limitation under IBC §7
- *Babulal Vardharji Gurjar v. Veer Gurjar Aluminium Industries* (2020) 15 SCC 1 — limitation under IBC §7 from date of default
- *Authorised Officer, UCO Bank v. M/s. Skylink* line — Section 17 SA standing

## Statutory currency rules

Every pleading filed today should cite the operative statute. Common substitution checks:

- **Section 200 CrPC 1973 → Section 223 BNSS 2023** in any Magistrate complaint (including Section 138 NI Act complaints) filed post-BNSS commencement.
- **Section 482 CrPC 1973 → Section 528 BNSS 2023** for inherent-power petitions.
- **Section 65B Indian Evidence Act 1872 → Section 63 Bharatiya Sakshya Adhiniyam 2023** for admissibility of electronic records / Statement of Account printouts.
- **Section 126 IEA 1872 → Section 132 BSA 2023** for advocate-client privilege.
- **Companies Act 1956 → Companies Act 2013** for any corporate-debtor pleading post-2013.

Dual-citation is acceptable in any transitional pleading.

## Section 138 NI Act jurisdictional rule

Post the Section 142(2) NI Act amendment (Act 26 of 2015), territorial jurisdiction for a Section 138 complaint lies in the court within whose local jurisdiction —

- the cheque is delivered for collection through an account, the branch of the drawee bank where the cheque is dishonoured is located, OR
- the cheque is presented for payment, the branch of the drawee bank is located.

The pre-2015 *Dashrath Rupsingh* rule (only where the drawee-bank branch is situated) stands legislatively displaced. The Drafter pleads the jurisdictional anchor using the drawee-bank-branch location and cites Section 142(2) NI Act.

## IBC default thresholds

- **Section 7 IBC (Financial Creditor against Corporate Debtor)** — default of ₹1 crore minimum (per the Section 4 notification dated 24 March 2020; verify against latest notification before drafting).
- **Section 9 IBC (Operational Creditor against Corporate Debtor)** — same ₹1 crore minimum.
- **Section 95 IBC (against Personal Guarantor)** — ₹1,000 minimum (Section 78 IBC; this lower threshold for natural persons).

The Verifier checks the default figure in `case-facts.md` against the applicable threshold before allowing the draft to go forward.

## SARFAESI Section 13(2) notice ingredients

For any pleading challenging or relying on a Section 13(2) notice, these ingredients must be pleaded:

- Identification of the secured asset
- Statement of the secured debt with break-up (principal + interest + costs)
- 60-day window for payment
- Statement of intent to invoke Section 13(4) on non-payment
- Service on the correct address
- Statement of Account certified under Section 2A Bankers' Books Evidence Act 1891 accompanying the notice
- Acknowledgement of receipt or proof of service

## DRAT pre-deposit discipline

Section 21 RDDBFI Act 1993 requires the appellant in a DRAT appeal to deposit 50% of the amount of debt due as determined by the DRT. The DRAT may, for reasons recorded in writing, reduce the deposit to 25% but cannot waive it entirely. The Drafter computes the pre-deposit from `case-facts.md` and either (a) reflects deposit in the appeal memo, or (b) files a separate application for reduction of pre-deposit with grounds for the relief sought.

## Limitation Act 1963 — Article map

| Case-type | Article | Period |
|---|---|---|
| DRT OA / civil recovery suit on a loan | 19 / 21 / 22 | 3 years from default |
| Civil suit on a written contract | 55 | 3 years from breach |
| Suit on a foreign judgment | 101 | 3 years from date of judgment |
| Mortgage suit for foreclosure | 63 | 12 years from due date |
| Mortgage suit for sale | 62 | 12 years from due date |
| DRAT appeal | special — Section 20(3) RDDBFI Act 1993 | 45 days from receipt of DRT order |
| Section 138 complaint | special — Section 142 NI Act + Section 5 Limitation Act for condonation | 30 days from expiry of 15-day notice period |
| IBC Section 7 application | Article 137 + acknowledgement under Section 18 | 3 years from default |
| Securitisation Application under Section 17 SARFAESI | special — Section 17(1) read with Rule 11 of Security Interest (Enforcement) Rules 2002 | 45 days from date of measure |
| Suit on a Promissory Note | 35 | 3 years from date of promissory note |

The Drafter pleads the limitation paragraph for every case-type using the applicable Article + date-of-accrual + date-of-filing + days-within-limitation.

## Bankers' Books Evidence Act 1891 — Section 2A discipline

Any Statement of Account filed by a Bank as part of its pleading must carry a Section 2A BBEA certificate. The certificate states:

- The Statement is a printout / true copy from the bank's books
- The bank's books are kept in the ordinary course of business
- The entries are recorded in the ordinary course of business
- The bank's books were in the custody of the bank
- The printout has been produced from the bank's computerised system
- The print-out is correct

Signed by the manager / authorised officer of the bank, with branch seal. The Verifier flags any Statement of Account without a Section 2A certificate.


---

## v0.2.1 RENDER DISCIPLINE (load-bearing — Drafter must follow)

**Pandoc + reference.docx + post-pandoc fix script.** The Drafter writes Markdown using the heading discipline below. Pandoc converts the Markdown to `.docx` using the SHIPPED reference.docx at `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/reference.docx` — pre-customised with locked Word styles matching the filing-grade Bombay HC convention (extracted from an actual filed Second Appeal pleading):

- **Body (Normal)** — TNR 14pt, 1.5 line spacing, justified, 0.5cm first-line indent
- **Heading 1** — TNR 14pt **bold + centered** (NOT underlined) — for the Court / Forum / Tribunal header line and the case-number line
- **Heading 2** — TNR 14pt **bold + UNDERLINED + centered + letter-spacing** — for spaced section headers (`F A C T S`, `G R O U N D S`, `P R A Y E R`, `I N D E X`, `S Y N O P S I S`, `L I S T   O F   A N N E X U R E S`, `V E R I F I C A T I O N`)
- **Heading 3** — TNR 14pt **bold + UNDERLINED + centered** — for unspaced section headers (`SUBSTANTIAL QUESTIONS OF LAW`, `ACTS & RULES`, `CITATIONS`) and statutory opening (`WRIT PETITION UNDER ARTICLE 226 …`)
- **Heading 4** — TNR 14pt **bold + UNDERLINED + left-aligned** — for left-anchored bold-underlined headings (`MOST RESPECTFULLY SHEWETH:`)
- **Tables** — `tblLayout = fixed`; first row bold centered; cell margins locked

### Markdown heading mapping

| Markdown | Rendered as | Used for |
|---|---|---|
| `# Heading 1` | Bold centered (no underline) | Court header line; case-number line; cover-page anchors |
| `## Heading 2` | Bold centered UNDERLINED with letter-spacing | Spaced section headers (`## F A C T S`, `## G R O U N D S`, `## P R A Y E R`, `## I N D E X`, `## S Y N O P S I S`, `## L I S T   O F   A N N E X U R E S`, `## V E R I F I C A T I O N`) |
| `### Heading 3` | Bold centered UNDERLINED | Unspaced section headers + statutory opening |
| `#### Heading 4` | Bold left UNDERLINED | `#### MOST RESPECTFULLY SHEWETH:` |
| Body paragraph | TNR 14pt justified 1.5 spacing 0.5cm first-line indent | Everything else |
| `**Bold inline**` | Bold | Property descriptors / annexure markers / key terms inline within Facts narrative |

### Bold-number paragraph convention

Facts and Grounds paragraphs use **BOLD NUMBERS**: `**1.**`, `**2.**`, `**3.**` followed by a tab + body. Renders as the gold-standard pleading layout.

### Two-step pandoc command (Step 2 is NON-NEGOTIABLE)

```bash
# Step 1 — pandoc → .docx with locked Word styles
pandoc draft-v1.md -o draft-v1.docx \
  --reference-doc="${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/reference.docx" \
  --from=markdown+pipe_tables+raw_tex

# Step 2 — force table column widths
python3 "${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/fix_docx_tables.py" draft-v1.docx
```

Step 2 forces column widths on every table — 5-col (Sr.No / Annx / Particulars / Date / Pgs) = 8/8/60/14/10; 4-col = 10/10/65/15; 3-col = 10/75/15; 2-col Dates–Events = 18/82. Locks first-row bold + centered + vertically-centered cells. **Skipping the fix script reproduces the v0.2.0 Index-table defect (Sr.No / Annx columns stacking vertically).**

Do NOT auto-generate a fresh reference.docx in the case folder. Use the shipped one or a `<case-folder>/reference.docx` override.

### Cover-page discipline

INDEX, SYNOPSIS, LIST OF ANNEXURES each begin on a new page (`\newpage` in Markdown) and carry ONLY: forum header (`#`) + case-number line (`#`) + short cause-title (Petitioner short name `///VERSUS///` Respondent short name) + section header (`##`) + table + Counsel block. DO NOT repeat the full party address block on cover pages.

### Pipeline-optionality (advocate-cost discipline)

The full 6-agent pipeline (Reader → Format → Drafter → Verifier → Refiner → Overseer) is **NOT** mandatory. Only the first three stages are required to produce a filing-grade draft. Stages 4–6 are OPTIONAL QC layers the advocate explicitly invokes. Default exit point is here, after Drafter (~280K tokens). Full pipeline ~600K tokens — disproportionate for routine pleadings.

When `draft-v1.docx` is written, the Drafter's job is complete. The advocate decides whether to invoke the QC stages.


---

## v0.2.2 OUTPUT-PAIRING DISCIPLINE (load-bearing — every agent must follow)

**Every `.md` output artifact MUST be paired with a `.docx`.** Advocates do not natively read Markdown — they read Word. Every pipeline output (case-facts.md from Reader, format-shell.md from Format, draft-v1.md from Drafter, verification-report.md from Verifier, draft-v2.md from Refiner, opposing-notes.md from Overseer) must have a corresponding `.docx` rendered with the same locked Word styles.

**This plugin produces pleadings** — the shipped reference.docx is the pleading variant (TNR 14pt 1.5 spacing, Heading 2 bold + UNDERLINED + centered with letter-spacing for the spaced `F A C T S` effect).

### How to produce the paired `.docx`

Every agent runs the shipped helper script as its final post-`.md`-write step:

```bash
bash "${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/pair_md_to_docx.sh" <output.md>
```

The helper:
1. Resolves the reference.docx in `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/reference.docx`
2. Runs pandoc with `--reference-doc` and `--from=markdown+pipe_tables+raw_tex` to produce the `.docx`
3. Runs the shipped `fix_docx_tables.py` to force column widths on every table

For overriding (e.g., a per-case-folder reference.docx), pass the reference.docx as the second argument:

```bash
bash "${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/pair_md_to_docx.sh" \
    <output.md> <case-folder>/reference.docx
```

### Per-agent output-pairing map

| Agent | `.md` output | Paired `.docx` |
|---|---|---|
| Reader | `case-facts.md` | `case-facts.docx` |
| Format | `format-shell.md` | `format-shell.docx` |
| Drafter | `draft-v1.md` | `draft-v1.docx` |
| Verifier | `verification-report.md` | `verification-report.docx` |
| Refiner | `draft-v2.md` | `draft-v2.docx` |
| Overseer | `opposing-notes.md` + `final-draft.md` | `opposing-notes.docx` + `final-draft.docx` |

Every agent calls `pair_md_to_docx.sh` once for each `.md` it writes. Skipping this step leaves the advocate with `.md` files that cannot be opened natively in Word.
