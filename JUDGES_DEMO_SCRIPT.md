# ClinSaar AI — 2–3 minute judge demo

## 0:00–0:20 · Problem and promise

“In an OPD, a patient’s story may arrive in a preferred language, through speech, taps and paper documents. ClinSaar is an intake workflow that turns that story into a traceable draft for a clinician to verify. It does not diagnose, prescribe or replace the clinician.”

On **Overview**, point to the connected workflow and the **AI Assistance Layer** panel.

“The panel is deliberately honest: this no-build prototype uses deterministic local demonstrations. In production, consented ASR, translation, structured-history and OCR services would attach here—never in the browser with an exposed API key.”

## 0:20–0:50 · Patient kiosk

1. Open **Patient Kiosk** and select **Hindi** or **English**.
2. Point out the large touch controls, five-step progress indicator and synthetic-data notice.
3. Enter a clearly fictional name, age and short concern, then complete symptoms, duration, medications and allergies as **patient-reported** fields. Explain: “The exact statement is retained rather than replaced with a canned diagnosis.”
4. Tap the microphone to show the local voice demonstration. Say: “This is a local synthetic response; no audio leaves the browser.”

## 0:50–1:15 · AI-assisted structure and evidence boundary

1. Open the review step. Show **Patient-reported concern**, **Demo template — no live AI extraction**, and **Requires clinician verification**.
2. Continue to the document step and click **Run demo OCR extraction**.
3. Narrate: “The OCR result shows original synthetic evidence, fixture text and demonstrative confidence. It is not presented as production-grade OCR or medical truth.”

## 1:15–1:45 · Patient confirmation to doctor queue

1. Confirm the synthetic intake.
2. In **Doctor Cockpit**, show the new record at the top as **Needs Verification**.
3. Explain the handoff ribbon and evidence-provenance panel: “This separates patient provided, AI structured, document extracted and clinician verified information. That is the core differentiation: AI helps documentation; clinicians control clinical decisions.”

## 1:45–2:10 · Clinician review and verification

1. Use **Pending** then **Verified** to show the local queue filter. Return to All, then use **Edit local draft** to show the inline, browser-only correction path.
2. Click **Verify intake**, read the safety confirmation, then confirm.
3. Point to the changed state: **Doctor Reviewed** and the new verification-timeline event.

## 2:10–2:30 · FHIR-ready export and close

1. Open **ABDM / FHIR** and show the selected record’s bundle.
2. Say: “This is a FHIR-ready prototype export containing Patient, Encounter, Observation, DocumentReference and Composition. A local FHIR R4 structural check runs before download; it is not formal profile validation, live ABDM integration, health-ID lookup or patient-data exchange.”
3. Close: “ClinSaar does not decide care. It reduces information-collection burden so clinicians can spend more time on clinical care.”

## Judge-facing differentiators

- It is a patient-to-clinician workflow, not a general medical chatbot.
- Demo boundaries are visible: synthetic data, local voice/OCR examples, no live AI or ABDM claim.
- Patient confirmation, evidence provenance and clinician verification are first-class product states.
- It is reliable for a judge demo: static, offline-capable and free of API keys, accounts and external dependencies.
- **Reset demo** clears only browser-local synthetic state and restores the initial walkthrough without touching project files.
