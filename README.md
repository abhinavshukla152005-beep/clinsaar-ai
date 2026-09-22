# ClinSaar AI

> **From Patient Voice to Clinical Clarity.** An accessibility-first OPD intake workflow for India. It helps a clinician receive a structured, traceable history; it does **not** diagnose, prescribe, or recommend treatment.

![ClinSaar architecture](architecture.svg)

## The problem

High-volume OPDs spend valuable minutes translating a patient’s spoken story, paper documents and language preferences into a history a clinician can review. ClinSaar designs an intake layer for that operational gap: Hindi/English patient interaction, source-labelled structuring, document-extraction evidence, a doctor queue, and explicit clinician verification.

## What works in this prototype

- Patient kiosk with Hindi and English, large touch targets and a local voice-flow demonstration.
- Minimal profile policy: name, age and preferred language only. The demo excludes sex/gender and warns against real data entry.
- Structured intake with traceability and “AI-generated — Requires clinician verification” gates.
- A safe, synthetic prescription/OCR evidence step with confidence and warning language.
- Functional patient handoff into a doctor queue; clinician verification updates the record state.
- Five synthetic records, including an AYUSH-aware example.
- FHIR-ready bundle preview/download, explicitly labelled as **not a live ABDM integration**.
- Simulated operational analytics with transparent labelling.

## Run it

Open `index.html` in any modern browser. No build step, account, API key, or internet connection is required.

## Demo flow

1. Open **Patient Kiosk**, choose Hindi or English, and complete the voice-guided intake demonstration.
2. Generate the structured history and analyze the synthetic prescription sample.
3. Confirm the intake; it appears immediately in **Doctor Cockpit** as *Needs Verification*.
4. Inspect source traceability, clinical summary, document extraction confidence, and verify it as the doctor.
5. Use **ABDM / FHIR** to download the clearly-labelled future-ready FHIR bundle.

## Architecture

The architecture diagram in [`architecture.svg`](architecture.svg) shows the intended production boundary: patient input, an intake orchestrator, optional AI adapters, an evidence layer, explicit doctor verification, and a future consented FHIR integration layer. See [`test-data/synthetic-prescription-ocr.json`](test-data/synthetic-prescription-ocr.json) for synthetic OCR evaluation fixtures.

## Production path (intentionally not overclaimed)

1. Add consented server-side ASR/translation and OCR adapters; never place API keys in the client.
2. Retain original-document references and confidence values alongside extracted fields.
3. Add role-based authorization, audit events, encryption and minimum-necessary retention before handling real patient data.
4. Validate in a consented pilot using intake time, clinician correction rate, completion by language and staff feedback—not unverified health outcomes.
5. Implement ABDM only after approved access, consent workflows and a compliant backend exist.

## Safety and evidence

- Uses only synthetic demo patients; the kiosk explicitly warns against entering real data.
- Does not collect sex/gender and does not make diagnoses, prescribe, or recommend treatment.
- Marks all AI/OCR output as needing clinician verification.
- Labels metrics as simulated and ABDM/FHIR as a prototype—not a live integration.
