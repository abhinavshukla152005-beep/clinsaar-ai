# Development log

## 2026-09-22 — Prototype baseline

- Defined ClinSaar AI as a **clinical documentation/intake assistant**, not a diagnostic or treatment system.
- Built the patient-kiosk → doctor-cockpit flow with five fully fictional demo records.
- Added bilingual Hindi/English interaction, large touch targets and minimal profile capture.
- Added a traceability pattern: patient statement, document extraction and clinician verification are separate states.
- Added optional AYUSH context for one synthetic record without presenting it as a diagnosis.
- Added transparent safety labels for AI draft, OCR confidence, simulated analytics and future ABDM/FHIR architecture.

## 2026-09-22 — Submission evidence hardening

- Published the app with GitHub Pages from `main`.
- Added an architecture diagram showing the intended production boundaries.
- Added synthetic OCR fixtures, including a low-confidence case, for a future extractor evaluation.
- Added a repeatable validation checklist and time-boxed judge walkthrough.

## 2026-09-22 — Workflow clarity hardening

- Retained the patient-entered synthetic concern through review, doctor queue and record-specific FHIR export instead of substituting a fixed narrative.
- Added an explicit AI Assistance Layer and trust panel that distinguishes deterministic demo simulations from consented production ASR/LLM/OCR adapters.
- Added provenance labels for patient-provided, demo-structured, document-extracted and clinician-verified information.
- Reworked the synthetic OCR step to show an evidence → extraction → confidence/warning → verification story without claiming live OCR.
- Updated the architecture, demo script, Q&A and proof-of-work wording to remove unsupported operational statistics and align every claim with implementation.

## Next engineering milestones

1. Replace the local voice demo with a consented, server-side ASR adapter.
2. Run OCR only in a secure server-side environment; store source reference and confidence for every extraction.
3. Add audited clinician edits and role-based authorization before any real-record pilot.
4. Conduct a consented usability pilot; track completion time, clinician correction rate and language accessibility—not clinical outcomes.
