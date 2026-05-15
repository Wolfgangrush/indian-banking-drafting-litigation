---
name: ni-act-138-reply-notice-draft
description: Draft a Reply Notice on behalf of the drawer / accused in response to a statutory notice issued under the proviso (b) to Section 138 of the Negotiable Instruments Act 1881. Encodes the defences typically available to the drawer (cheque issued not for legally enforceable debt; cheque issued as security and not in discharge of an enforceable obligation; signature disputed; alteration of the cheque; cheque presented after validity; statutory-notice defects; settlement / payment already made); the Krishna Janardhan Bhat (2008) 4 SCC 54 burden-shift framework; and the discipline that the reply must be careful not to admit the underlying debt while contesting the statutory ingredients. Auto-fires on "draft 138 reply notice", "draft reply to cheque bounce notice", "draft reply NI Act notice", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 138 NI Act Reply Notice Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_banking_drafting_base/SKILL.md` (with adaptations — a reply notice is a private legal notice, not a court pleading; the Cause-Title section is replaced by the notice header and the Affidavit + Index sections are dropped)
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: REPLY NOTICE TO THE STATUTORY NOTICE UNDER THE PROVISO (b) TO SECTION 138 OF THE NEGOTIABLE INSTRUMENTS ACT 1881
case_short_code: NI_138_REPLY
notice_type: Reply to statutory pre-litigation notice
typical_forum: N/A — issued by the drawer's advocate to the payee / payee's advocate
typical_parties: Issuing party (Drawer / Accused) + Addressee (Payee / Complainant) — and copy to Payee's advocate on the original notice
statutory_opening: "This Reply is issued on behalf of my client [Drawer's name] (hereinafter the 'Drawer') in reply to the statutory notice dated ____ issued by you / on behalf of your client (hereinafter the 'Payee') under the proviso (b) to Section 138 of the Negotiable Instruments Act 1881, received by the Drawer on ____. The contents of the said notice are denied as set out below."
defence_paragraphs_to_consider_in_each_reply:
  - "1. Cheque not issued for legally enforceable debt or liability — the cheque was issued [as security for a transaction that did not crystallise / in blank as part of an executory arrangement / under coercion or undue influence / for a debt that had already been discharged / for a transaction that is unlawful / void / opposed to public policy under Section 23 ICA 1872]."
  - "2. Cheque was issued as security and not in discharge of a present, ascertained, and legally enforceable liability — the underlying transaction was [executory / contingent / dependent on a condition that has not materialised]."
  - "3. Signature is denied — the signature appearing on the cheque is not that of the Drawer; the cheque was [forged / fraudulently obtained / signed in blank and material alterations have been made without consent]."
  - "4. Material alteration without consent — the cheque has been [altered as to date / altered as to amount / altered as to payee] after it left the Drawer's hands, rendering the instrument void under Section 87 NI Act."
  - "5. Cheque presented after expiry of validity — the cheque was presented for payment beyond three months from the date of the cheque, attracting the bar in proviso (a) to Section 138."
  - "6. Statutory-notice defects — the notice [was not served on the Drawer / was served at a non-current address / does not specify the cheque particulars / does not demand the cheque amount within 15 days / is otherwise non-compliant with proviso (b) to Section 138]."
  - "7. Payment already made / cheque amount tendered — the Drawer has [paid the cheque amount on ____ / tendered the cheque amount through bank transfer on ____ / tendered payment through demand draft on ____], evidence whereof is enclosed."
  - "8. Cheque issued under a Section 17 NI Act conditional delivery — the cheque was delivered conditionally and the condition has not been satisfied."
  - "9. No subsisting contract — the underlying contract has been [rescinded / terminated / frustrated / vitiated by misrepresentation under Section 18 ICA 1872]."
  - "10. Discharge under Section 82 NI Act / settlement reached — the parties have reached a settlement / there is a written discharge of the underlying liability under Section 82 NI Act."
careful_anti_admission_discipline:
  - "The Reply must NOT admit the underlying debt while contesting the statutory ingredients. A reply that admits the existence of the debt while disputing only the cheque-related ingredients hands the Complainant the easier route through Section 139 presumption."
  - "The Reply must NOT acknowledge receipt of an outstanding sum — Section 18 Limitation Act 1963 acknowledgement language is to be avoided."
  - "Tentative language is to be avoided — every defence is to be stated affirmatively, with 'denied' on each adverse allegation."
operational_guidance:
  - "Issued within 7-10 days of receipt of the statutory notice. A timely reply preserves the Drawer's defences and avoids the 'silent-acceptance' inference at trial."
  - "Served by registered post AD on the Payee / Payee's advocate, with proof of dispatch retained."
  - "Copy to the Drawer's banker where bank-statement-based defences are anticipated."
no_separate_filing_fee: "N/A — this is a private legal notice, not a court filing."
```

## Krishna Janardhan Bhat burden-shift discipline

Under *Krishna Janardhan Bhat v. Dattatraya G. Hegde* (2008) 4 SCC 54, the Section 139 presumption can be rebutted by the Drawer on a preponderance-of-probabilities standard. The Drawer is not required to discharge a beyond-reasonable-doubt burden. The reply notice — by laying out the defence early and with specificity — frames the foundation for the rebuttal evidence that the Drawer will lead at trial.

## What a reply notice is NOT

A reply notice is not a confession statement and not a substitute for a full defence in trial. The reply preserves defences and signals seriousness; the actual evidence on each defence is led at trial through the Drawer's witnesses and documents. The reply is also not a counter-claim — Section 138 NI Act is a criminal proceeding and the Drawer's counter-claim, if any, is to be pursued by separate civil suit (subject to limitation).

## Service discipline

The reply is dispatched by:

- Registered post AD to the Payee's address on the original notice
- Speed post / courier with acknowledgement
- Email to the email-on-record (additional, not substitution)

The proof of dispatch is retained — a duplicate of the reply, the postal receipt, and the AD card / delivery acknowledgement.
