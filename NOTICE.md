# NOTICE — Provenance and Privilege Statement

This document is part of the public release of the `indian-banking-drafting` plugin (v0.1.0-alpha and onwards). It declares the provenance of the plugin's content, in order to address any question about advocate-client privilege, client confidentiality, professional ethics, personal-data protection, and commercial confidentiality that may be raised by any reader, complainant, regulator, or Bar Council disciplinary authority.

The plugin is **case-config-aware**: the universal structural skeleton of any Indian banking pleading is uniform, and the parties' chosen forum (DRT bench, DRAT, NCLT bench, Chief Metropolitan Magistrate, District Magistrate, or civil court of pecuniary jurisdiction), claim quantum, security position, NPA classification, and demand-notice trajectory are supplied by the user via a `case-config.md` file in the case folder.

This NOTICE is published in plain language so that any reader — practising advocate, judge, Bar Council officer, regulator, member of the public, fellow developer — can understand the position without ambiguity.

---

## 1. What this plugin contains

This plugin contains the following categories of content, and **only** the following categories of content:

(a) **Universal banking-pleading skeleton** — the structural shape of any Indian banking / financial-recovery / insolvency pleading (Cause Title with correct forum nomenclature, Parties block, Statutory Opening invoking the operative section, Prelude, Facts, Grounds, Prayer, Verification, Affidavit-in-support, Index, List of Documents, accompanying applications).

(b) **Formatting conventions** — text-formatting conventions for pleadings before the Debts Recovery Tribunals, the Debts Recovery Appellate Tribunal, the National Company Law Tribunal, the Chief Metropolitan Magistrate, the District Magistrate, and civil courts exercising banking-recovery jurisdiction.

(c) **Statutory references** — citations to public statutes (Recovery of Debts and Bankruptcy Act 1993, Securitisation and Reconstruction of Financial Assets and Enforcement of Security Interest Act 2002, Negotiable Instruments Act 1881, Insolvency and Bankruptcy Code 2016, Banking Regulation Act 1949, Reserve Bank of India Act 1934, Code of Civil Procedure 1908, Bharatiya Nagarik Suraksha Sanhita 2023, Bharatiya Sakshya Adhiniyam 2023, Limitation Act 1963, Indian Contract Act 1872, Transfer of Property Act 1882, Registration Act 1908, Indian Stamp Act 1899 + applicable State Stamp Acts, Companies Act 2013, Limited Liability Partnership Act 2008, Foreign Exchange Management Act 1999, Prevention of Money-Laundering Act 2002, applicable State Court-Fees Acts).

(d) **Procedural rule references** — citations to public rules (Debts Recovery Tribunal (Procedure) Rules 1993, Debts Recovery Appellate Tribunal (Procedure) Rules 1994, Security Interest (Enforcement) Rules 2002, IBBI (Application to Adjudicating Authority) Rules 2016, IBBI (Application to Adjudicating Authority for Insolvency Resolution Process for Personal Guarantors to Corporate Debtors) Rules 2019, IBBI (Insolvency Resolution Process for Corporate Persons) Regulations 2016, NCLT Rules 2016, RBI Master Direction on Income Recognition, Asset Classification and Provisioning pertaining to Advances 2021, RBI Master Direction on Frauds 2016, RBI Master Circulars on Wilful Defaulters, and the various Practice Directions of the DRT / DRAT / NCLT benches).

(e) **Generic placeholders** — every variable in every template is a placeholder (`[Applicant Bank]`, `[Defendant Borrower]`, `[Defendant Guarantor]`, `[Loan Account No.]`, `[Sanction Date]`, `[Disbursement Date]`, `[NPA Classification Date]`, `[Outstanding Amount]`, `[Schedule of Mortgaged Property]`, `[Cheque No.]`, `[Cheque Date]`, `[Cheque Amount]`, `[Drawee Bank]`, `[Return Memo Date]`, `[Statutory Notice Date]`, `[Date of Default]`). No placeholder is filled with any specific account, borrower, guarantor, loan amount, security description, cheque particulars, or any other identifying information.

(f) **Anti-hallucination and privacy-firewall workflow** — six agents (Reader, Format, Drafter, Verifier, Refiner, Overseer) that operate on a case folder supplied by the user. The plugin itself contains no case folder. The Reader substitutes every party name, key person, account number, and financial figure with placeholders before downstream AI processing.

---

## 2. What this plugin does NOT contain

This plugin does **not** contain any of the following, and has never contained any of the following at any point in any committed version:

(a) **No specific client matter or banking case.** No client of the author, and no specific lending transaction or recovery proceeding handled by the author or any client, appears in the plugin — by name, by account number, by sanction reference, by NPA tag, by loan amount, by security description, by party name, by registration number (CIN / LLPIN / GSTIN / PAN), or by any other identifying signature.

(b) **No client communications.** No oral or written communication made to the author by or on behalf of any client (whether a bank, an NBFC, a corporate debtor, a personal guarantor, or any other party) appears in the plugin in any form.

(c) **No client documents.** No document or instrument with which the author has become acquainted in the course of professional employment as an advocate appears in the plugin, in original, in redacted, in summary, in extract, or in pattern. This includes — but is not limited to — sanction letters, loan agreements, hypothecation deeds, mortgage deeds, deeds of guarantee, demand notices, return memos, statutory notices, balance-confirmation letters, recall notices, classification advices, valuation reports, and security audits of any specific account.

(d) **No personal data of any data principal.** The plugin processes no personal data, collects no personal data, stores no personal data.

(e) **No specific board resolution, no specific power-of-attorney, no specific authorisation letter** of any specific bank or NBFC handled by the author or any other advocate.

(f) **No client list, no panel-counsel list of any bank, no chamber list, no associate list, no opposing-counsel list, no Presiding Officer-specific intelligence, no Member-specific intelligence.**

(g) **No tracking, no telemetry, no analytics, no opt-in error reporting, no login, no account, no cloud sync.** The plugin runs entirely on the user's machine. The author receives no information about who installs the plugin, who uses it, on what cases, with what consideration, with what outcomes.

---

## 3. The legal distinction

Indian law has long recognised a clear distinction between two categories:

(i) **Specific client communications and documents** — protected under Section 132 of the Bharatiya Sakshya Adhiniyam 2023 (formerly Section 126 of the Indian Evidence Act 1872) and under Rule 17 of the Bar Council of India Standards of Professional Conduct and Etiquette. This category is privileged and confidential.

(ii) **General professional knowledge of banking law, debt-recovery procedure, and pleading craft** — an advocate's accumulated knowledge of how a Section 19 RDDBFI Original Application is structured, how a SARFAESI Section 13(2) demand notice must read to survive challenge in a Section 17 Securitisation Application, what *Mardia Chemicals v. Union of India* (2004) 4 SCC 311 holds about the constitutional validity of SARFAESI, what *Innoventive Industries v. ICICI Bank* (2018) 1 SCC 407 holds about the operation of moratorium under Section 14 IBC, what *Dashrath Rupsingh Rathod v. State of Maharashtra* (2014) 9 SCC 129 / the Section 142(2) amendment holds about Section 138 NI Act territorial jurisdiction, what the RBI Master Direction on Income Recognition, Asset Classification and Provisioning 2021 prescribes for NPA classification, how a DRAT pre-deposit application under Section 21 RDDBFI is structured. This category is the advocate's own professional knowledge. It is not the property of any specific client. It is not privileged.

This plugin operates **entirely within category (ii)**.

Every Indian advocate accumulates this knowledge through years of practice, through study of Tannan's *Banking Law and Practice in India*, Mulla on the Code of Civil Procedure, the SARFAESI and DRT Act commentaries, Mookerjee on Negotiable Instruments, the IBC commentaries (Sumant Batra, Subodh Kumar Jain, the IBBI handbooks), the RBI Master Directions, and the case-law of the Supreme Court and the High Courts on banking recovery, securitisation, insolvency, and cheque-dishonour jurisprudence. The plugin codifies that accumulated procedural knowledge into machine-readable form. It does not codify any client's confidential information.

The plugin is, in this respect, identical in legal character to a published banking-law textbook, a continuing legal education handout, or a senior advocate's drafting-style lecture. The medium is software. The content is procedural knowledge.

---

## 4. The author's professional position

The author is **Rushikesh R. Mahajan**, Advocate, enrolled with the Bar Council of Maharashtra and Goa, practising before the Bombay High Court, Nagpur Bench. The plugin is published under the open-source brand **Wolfgang Rush**, which is the author's publishing handle for legal-technology infrastructure; the real-identity accountability declared in this section attaches to the author personally and is not displaced by the use of a publishing handle.

The author retains full enrolment, full responsibility, and full liability under the Advocates Act 1961, the Bar Council of India Rules, and the Standards of Professional Conduct and Etiquette.

The plugin is published as a personal contribution to the open-source legal-technology ecosystem. It is published without any commercial channel, without any solicitation of professional work, without any advertisement of professional services, and without any acceptance of work through this repository.

This NOTICE is filed of record in this open-source repository so that any person who reads, reviews, audits, or assesses this plugin has full transparency about its provenance and its scope from the moment of release.

---

## 5. Verification of clean provenance

The repository owner shall maintain, on a private offline record, a build log demonstrating that every line of every file in the plugin was either:

(a) authored from scratch as procedural skeleton, OR
(b) derived from public statute, public rule, public judgment, or public banking-law textbook, OR
(c) derived from the author's own original procedural knowledge as a practitioner.

No line of any file was, at any stage, copied from, paraphrased from, summarised from, or pattern-matched against any specific client matter, banking case, client communication, or client document.

This NOTICE is the author's signed declaration of that position.

---

## 6. Reporting concerns

If any reader, regulator, fellow advocate, or member of the public believes any specific content in this plugin is derived from a specific client matter or specific confidential communication, the reader is requested to:

(a) identify the file and line at issue in the plugin,
(b) identify the specific client matter or communication believed to be the source,
(c) explain the basis of the belief,

and raise the concern via a GitHub Issue on this repository.

Concerns raised with these particulars will be investigated and the file or line will be removed or rewritten if the concern is well-founded. Concerns raised without these particulars cannot be acted upon.

---

## 7. Standing instruction to forks and derivatives

Any fork, derivative, downstream redistribution, or commercial integration of this plugin or its content shall preserve this NOTICE in unmodified form, and shall extend the same provenance discipline to any content added in the fork or derivative.

This NOTICE travels with the code under the same MIT licence that governs the source.

---

*Signed and dated by way of public commit history on the repository. The author stands by every line of this notice.*
