# ClinSaar AI — 3-minute judge demo

## Opening (20 seconds)

“In a crowded OPD, a doctor may see more than 80 patients in a day. The bottleneck is not only consultation; it is turning a patient’s story—often in their preferred language—into a reliable history. ClinSaar AI is an accessibility-first intake layer that gives clinicians a traceable, reviewable starting point, without pretending to diagnose.”

## Show the patient experience (60 seconds)

1. Open **Patient Kiosk**.
2. Select **Hindi**. Call out the large tap targets, minimal reading and local voice demonstration.
3. Complete the minimal profile: name, age, language. Emphasize that the prototype deliberately excludes sex/gender and discourages real data entry.
4. Tap the microphone. Show the Hindi transcript becoming a structured, source-labelled intake.
5. Open the simulated prescription analysis. Point out the OCR confidence and the warning: extracted text is evidence, not medical truth.
6. Confirm the intake.

## Show the clinician experience (60 seconds)

1. Open **Doctor Cockpit**; show the new record at the top of the queue as **Needs Verification**.
2. Explain the three evidence layers: patient statement, document extraction, and clinician verification.
3. Show the source timeline and the intentionally non-diagnostic AI draft.
4. Verify the synthetic record. The status changes to **Doctor Reviewed**.
5. Select the AYUSH-focused synthetic patient to demonstrate the optional assessment fields.

## Close with scale (40 seconds)

1. Open **ABDM / FHIR**. Say: “We are not claiming a live ABDM integration. We have designed the mapping so a future consented workflow can emit Patient, Encounter, Observation, DocumentReference and Composition resources.”
2. Download the FHIR bundle.
3. Open **Analytics** and explain these are simulated pilot metrics, with real measurement targets: intake duration, correction rate, completion by language and clinician satisfaction.

## Differentiators

- **Not a chatbot:** it is a complete patient-to-physician workflow with a queue and verification state.
- **Safety by design:** no diagnosis, no prescription, no real data, explicit uncertainty and clinician control.
- **Inclusion is product architecture:** bilingual interaction, voice-first UX, low-literacy design and optional AYUSH context.
- **Interoperability without overclaiming:** FHIR mapping is visible and clearly labelled future-ready.

## One-line answer for tough questions

“ClinSaar does not decide care; it makes the patient’s own story legible, traceable and faster for a clinician to verify.”
