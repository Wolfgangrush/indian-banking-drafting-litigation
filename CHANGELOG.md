# Changelog

All notable changes to the `indian-banking-drafting` plugin are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/) and this project adheres to [Semantic Versioning](https://semver.org/).

---

## [0.1.0-alpha] — 2026-05-16 (initial release)

### Added

- **Plugin scaffolding** — `.claude-plugin/plugin.json` manifest · MIT `LICENSE` · `NOTICE.md` provenance and privilege statement · `.gitignore` · this `CHANGELOG.md` · comprehensive `README.md`.
- **Six-agent drafting pipeline** — Reader → Format → Drafter → Verifier → Refiner → Overseer. Each agent is a markdown file under `agents/<name>/<name>.md` with YAML frontmatter declaring `name`, `description`, and `allowed-tools`.
- **Shared infrastructure skills:**
  - `_drafting_common` — anti-pollution rules, encoding standards, language conventions, AI-style-marker blacklist, banking-specific privacy firewall, citation discipline, and statutory currency rules (RDDBFI Act 1993, SARFAESI Act 2002, Negotiable Instruments Act 1881 — with the *Dashrath Rupsingh Rathod* / *Bhaskar Industries* line on §138 jurisdiction — Insolvency and Bankruptcy Code 2016, Banking Regulation Act 1949, RBI Master Direction on Income Recognition Asset Classification 2021, Bharatiya Nagarik Suraksha Sanhita 2023, Bharatiya Sakshya Adhiniyam 2023, Limitation Act 1963, CPC 1908 — Order 7 and Order 37 summary procedure, applicable State Court-Fees Act, and applicable State Stamp Act).
  - `_banking_drafting_base` — universal Indian banking pleading skeleton (Cause Title with correct forum nomenclature · Parties block · Statutory Opening invoking the operative section · Prelude · Facts · Grounds · Prayer · Verification · Affidavit-in-support · Index · List of Documents · accompanying applications).
- **Ten case-type skill scaffolds:**
  - `drt-original-application-draft` — Original Application under Section 19 of the RDDBFI Act 1993 (claim of ≥ ₹20 lakh; secured / unsecured)
  - `sarfaesi-13-2-notice-draft` — demand notice under Section 13(2) of the SARFAESI Act 2002 (60-day pre-enforcement notice for NPA accounts; secured creditor)
  - `sarfaesi-17-securitisation-application-draft` — Securitisation Application under Section 17 of the SARFAESI Act 2002 (borrower's challenge in DRT against possession / sale)
  - `sarfaesi-14-cmm-dm-application-draft` — application before the Chief Metropolitan Magistrate / District Magistrate under Section 14 of the SARFAESI Act 2002 (possession assistance)
  - `ni-act-138-complaint-draft` — complaint under Section 138 of the Negotiable Instruments Act 1881 read with Section 142 and the BNSS / CrPC framework
  - `ni-act-138-reply-notice-draft` — reply notice from the drawer / accused to the statutory notice under Section 138 proviso (b)
  - `civil-recovery-suit-draft` — Order 7 CPC plaint for recovery of money / Order 37 CPC summary suit for liquidated demand (typically below DRT pecuniary threshold)
  - `ibc-section-7-application-draft` — Financial Creditor application for initiation of Corporate Insolvency Resolution Process before the NCLT under Section 7 of the IBC 2016
  - `ibc-section-95-application-draft` — application for initiation of Insolvency Resolution Process against a Personal Guarantor to a Corporate Debtor before the NCLT (or against an individual / firm before DRT) under Section 95 of the IBC 2016
  - `drat-appeal-draft` — appeal under Section 20 of the RDDBFI Act 1993 before the Debts Recovery Appellate Tribunal (and the pre-deposit obligation under Section 21)
- **Forum-aware design** — the user supplies `case-config.md` declaring the chosen forum (DRT bench / DRAT bench / NCLT bench / CMM or DM jurisdiction / civil court of pecuniary jurisdiction), claim quantum, security position, NPA classification date, demand-notice trajectory, default trigger, the security-document inventory, and the limitation-clock anchor.

### Notes on this release

This is a **v0.1.0-alpha scaffold release**. The structural skeletons, agent pipeline, base skills, and 10 case-type skill frames are in place. Deep per-skill encoding (full pleading exemplars for each case type, NPA-classification-tabular discipline per RBI MD IRAC 2021, full *Vidya Drolia* / *Mardia Chemicals* / *Innoventive Industries* line of Supreme Court precedent encoded in the Verifier, and bench-specific Practice Directions for DRT Mumbai / Delhi / Chennai / Kolkata / Bangalore / Ahmedabad / Lucknow / Pune / Allahabad / Jaipur and the equivalent NCLT benches) will land in v0.1.0 and onward.

### Released under

MIT License. Authored by Rushikesh R. Mahajan, Advocate, publishing under the Wolfgang Rush open-source brand for legal-tech infrastructure.
