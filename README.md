# ClinSaar AI

> **From Patient Voice to Clinical Clarity.** An accessibility-first OPD intake workflow for India. It helps a clinician receive a structured, traceable history; it does **not** diagnose, prescribe, or recommend treatment.

![ClinSaar architecture](architecture.svg)

## 🔗 Live proof

- **Live prototype:** https://abhinavshukla152005-beep.github.io/clinsaar-ai/
- **Judge walkthrough:** [`JUDGES_DEMO_SCRIPT.md`](JUDGES_DEMO_SCRIPT.md)
- **Judge Q&A:** [`JUDGE_QA.md`](JUDGE_QA.md)
- **Verification evidence:** [`docs/PROOF_OF_WORK.md`](docs/PROOF_OF_WORK.md)
- **Engineering decisions:** [`docs/DEVELOPMENT_LOG.md`](docs/DEVELOPMENT_LOG.md)

## 30-second project overview

ClinSaar AI addresses a practical OPD bottleneck: clinicians need a clear history, but patients arrive with spoken narratives, mixed language preferences and paper documents. The prototype turns a safe, minimal patient intake into a **traceable draft for clinician review**. It deliberately keeps the clinician in control:

`Patient kiosk → structured history → document evidence → patient confirmation → doctor queue → clinician verification → FHIR-ready export`

> The project is intentionally **not** a diagnostic chatbot. It never proposes a diagnosis, treatment or prescription.

## The problem

High-volume OPDs spend valuable minutes translating a patient’s spoken story, paper documents and language preferences into a history a clinician can review. ClinSaar designs an intake layer for that operational gap: Hindi/English patient interaction, source-labelled structuring, document-extraction evidence, a doctor queue, and explicit clinician verification.

## What works in this prototype

- Patient kiosk with Hindi and English, large touch targets and a local voice-flow demonstration.
- Minimal profile policy: name, age and preferred language only. The demo excludes sex/gender and warns against real data entry.
- Patient-entered statement retained through the queue, with traceability and clinician-verification gates.
- A safe, synthetic prescription/OCR evidence step with confidence and warning language.
- Functional patient handoff into a doctor queue; clinician verification updates the record state.
- Five synthetic records, including an AYUSH-aware example.
- FHIR-ready bundle preview/download, explicitly labelled as **not a live ABDM integration**.
- Simulated operational analytics with transparent labelling.

## Judge demo in three clicks

1. Go to the [live prototype](https://abhinavshukla152005-beep.github.io/clinsaar-ai/) and choose **Patient Kiosk**.
2. Choose **Hindi**, follow the voice-guided demo and confirm the synthetic intake.
3. Open **Doctor Cockpit** to inspect its source timeline and click **Verify intake**. Then open **ABDM / FHIR** to download the future-ready sample bundle.

This demonstrates a genuine role-to-role state transition rather than separate static screens.

## Run it

Open `index.html` in any modern browser. No build step, account, API key, or internet connection is required.

## Demo flow

1. Open **Patient Kiosk**, choose Hindi or English, and complete the voice-guided intake demonstration.
2. Generate the structured history and analyze the synthetic prescription sample.
3. Confirm the intake; it appears immediately in **Doctor Cockpit** as *Needs Verification*.
4. Inspect source traceability, clinical summary, document extraction confidence, and verify it as the doctor.
5. Use **ABDM / FHIR** to download the clearly-labelled future-ready FHIR bundle.

## AI role: clear but not overclaimed

The **AI Assistance Layer** in the UI shows where multilingual understanding, speech-to-structured-history transformation, summarization, normalization and OCR extraction would run in production. In this repository those examples are deterministic, local **demo simulations**—there is no live LLM, ASR, translation service or OCR API.

| Functional prototype now | Simulated/demo | Future production implementation |
| --- | --- | --- |
| Bilingual kiosk, confirmation, queue, local edits, verification state and record-specific FHIR export | Voice response, structured-history template, OCR output/confidence and analytics | Consented server-side ASR/translation/LLM/OCR, authenticated roles, audit log, encrypted data handling and approved ABDM connectivity |

Every AI-assisted or document-extracted item is a draft requiring clinician verification. ClinSaar never diagnoses, prescribes or recommends treatment.

## FHIR-ready export validation

Each generated bundle is checked locally before download against a deliberately narrow **FHIR R4 (4.0.1) structural validation**: it must be a `Bundle` of type `collection`, include `Patient`, `Encounter`, `Observation`, `DocumentReference`, and `Composition`, and keep the demo Encounter/Observation references tied to the Patient. This check runs offline in the browser and is designed to catch broken demo output.

It is **not** formal FHIR profile conformance, an implementation-guide validation, server validation, certification, or ABDM integration. A production integration would validate against the selected deployment profile and an approved interoperability endpoint.

## Architecture

The architecture diagram in [`architecture.svg`](architecture.svg) shows the intended production boundary: patient input, an intake orchestrator, optional AI adapters, an evidence layer, explicit doctor verification, and a future consented FHIR integration layer. See [`test-data/synthetic-prescription-ocr.json`](test-data/synthetic-prescription-ocr.json) for synthetic OCR evaluation fixtures.

## Production path (intentionally not overclaimed)

1. Add consented server-side ASR/translation and OCR adapters; never place API keys in the client.
2. Retain original-document references and confidence values alongside extracted fields.
3. Add role-based authorization, audit events, encryption and minimum-necessary retention before handling real patient data.
4. Validate in a consented pilot using intake time, clinician correction rate, completion by language and staff feedback—not unverified health outcomes.
5. Implement ABDM only after approved access, consent workflows and a compliant backend exist.

## Repository map

| Path | Why it exists |
| --- | --- |
| `index.html` | Complete deployable interactive prototype; no account or API key needed. |
| `architecture.svg` | System boundary, evidence layer and future FHIR path. |
| `test-data/` | Synthetic OCR test fixtures that can be used to evaluate a future extractor. |
| `docs/PROOF_OF_WORK.md` | Repeatable functional test plan and evidence checklist. |
| `docs/DEVELOPMENT_LOG.md` | Transparent product and safety decisions made during this build. |
| `JUDGES_DEMO_SCRIPT.md` | Time-boxed narration for a 3-minute final demonstration. |
| `JUDGE_QA.md` | Concise, evidence-based answers to likely judge questions. |

## Safety and evidence

- Uses only synthetic demo patients; the kiosk explicitly warns against entering real data.
- Does not collect sex/gender and does not make diagnoses, prescribe, or recommend treatment.
- Marks all AI/OCR output as needing clinician verification.
- Labels metrics as simulated and ABDM/FHIR as a prototype—not a live integration.
