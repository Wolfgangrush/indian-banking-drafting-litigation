# 🇮🇳 Indian Banking and Financial Litigation Drafting — Gemini CLI Port

> The same `indian-banking-drafting` pipeline you know, now invokable from Gemini CLI. **Same 6-agent pipeline. Same canonical agent specs. Same filing-grade output. Different LLM brain.**

**Version:** Gemini port 2026-05-24 · **License:** MIT · **Publisher:** wolfgang_rush

---

## What this port adds

```
indian-banking-drafting/
├── .claude-plugin/                  ← Claude plugin manifest (unchanged)
├── agents/                          ← Canonical 6-agent specs (unchanged · single source of truth)
├── skills/ (banking case-type templates)                   ← case-type templates (unchanged)
├── .gemini/                         ← NEW
│   └── commands/
│       ├── reader.toml · format.toml · drafter.toml
│       ├── verifier.toml · refiner.toml · overseer.toml
│       └── pipeline.toml             ← runs all 6 sequentially
├── GEMINI.md                        ← NEW · auto-loaded context
└── README_GEMINI.md                 ← NEW · this file
```

Each Gemini command reads its canonical spec from `agents/<name>/<name>.md` via shell injection at call time — `.md` files remain the single source of truth.

---

## Install — 4 steps

### Step 1 — Install Gemini CLI

Requires Node.js 20+ ([download](https://nodejs.org/)).

```bash
npm install -g @google/gemini-cli
gemini --version
```

### Step 2 — Set your API key

Get one from [Google AI Studio](https://aistudio.google.com/apikey).

**For client work → enable PAID billing first** (free tier sends prompts into training).

```bash
echo 'export GEMINI_API_KEY="paste-your-key-here"' >> ~/.zshrc
source ~/.zshrc
```

### Step 3 — Prepare your case folder

```
<case-folder>/
├── case-config.md           ← advocate-supplied (required)
├── laws/                            ← put required statute PDFs here
└── <documents>.pdf                  ← case documents
```

### Step 4 — Launch Gemini CLI from the plugin folder

```bash
cd "indian-banking-drafting"
gemini
```

Gemini auto-loads `GEMINI.md` + all 7 slash commands.

---

## Use — the 7 commands

| Command | Stage | Output |
|---|---|---|
| `/reader <folder>` | 1 | `case-facts.md` |
| `/format <folder>` | 2 | `format-shell.md` |
| `/drafter <folder>` | 3 | `draft-v1.docx` |
| `/verifier <folder>` | 4 | `verification-report.md` |
| `/refiner <folder>` | 5 | `draft-v2.docx` |
| `/overseer <folder>` | 6 | `opposing-notes.md` + `final-draft.docx` |
| `/pipeline <folder>` | all | runs 6 sequentially |

---

## Privacy

- ✅ **Gemini paid tier** → templates, study, public-record / consented matters
- ✅ **Local Ollama** (via parent `ailawfirm-india` CLI) → real client matters under BCI Rule 17
- ❌ **Gemini free tier** → never for client work
- ❌ **Any cloud LLM** for client data without consent + DPA → breach of BCI Rule 17 + Advocates Act §35

---

## Forum support

**Forum:** Debts Recovery Tribunal bench / Debts Recovery Appellate Tribunal / National Company Law Tribunal bench / Chief Metropolitan Magistrate / District Magistrate / civil court for SARFAESI

**Case types covered:** Original Application (OA) under RDB Act 1993 · SARFAESI Section 17 application · DRAT appeal · IBC Section 7 / 9 / 10 · Section 138 NI Act complaint · MSMED Act delayed payment · Section 14 SARFAESI possession application · Section 13(2) SARFAESI demand notice reply · Section 19 RDB Act counter-claim

---

## What this port does NOT do

- Does **NOT** modify any existing file in the plugin
- Does **NOT** replace the Claude port
- Does **NOT** invent its own agent specs (reads canonical `.md` at call time)
- Does **NOT** route around BCI Rule 17 / DPDP Act 2023

---

## ⚖️ Compliance

Same Supreme Court e-Committee alignment as the Claude port: *"AI and digital tools must be used as supportive instruments and should not be allowed to override judicial reasoning."* — Justice Rajesh Bindal, April 2026.

Every draft must be advocate-owned and human-verified before filing.

---

## ⚠️ Third-party CLI tools — user assumes all risk

The publisher does NOT recommend Gemini CLI specifically, receives no compensation from Google, and verifies no claims about Gemini's privacy posture. Use of this Gemini port is at your own risk under MIT license + Google's Gemini API terms.

---

`चलिए शुरू करें · Let's begin.` 🙏
