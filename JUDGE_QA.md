# ClinSaar AI — judge Q&A

## 1. Why not ChatGPT?

ClinSaar is not a general conversation interface. It is a role-based OPD intake workflow: patient input, source-labelled draft, patient confirmation, doctor queue, clinician verification and a FHIR-ready export. A general model could be one future adapter, but it does not provide that workflow or safety boundary by itself.

## 2. Where is the AI?

In this offline prototype, the visible voice response, OCR result and structure are synthetic demonstrations. The production architecture reserves server-side adapters for speech recognition, translation, OCR and clinical-information extraction. The UI labels this distinction rather than implying a live model.

## 3. Is this real AI or simulated?

The current prototype is simulated and deterministic: no external model, API key or live OCR service runs. It demonstrates the workflow and the verification boundary; it is not presented as a deployed AI service.

## 4. What happens if AI makes a mistake?

Output is a draft with source and confidence context, never a clinical decision. The clinician reviews and can edit the synthetic draft before recording verification. A production system would retain source references and audited edits.

## 5. Does ClinSaar diagnose patients?

No. It does not diagnose, triage or recommend treatment. It collects and presents intake information for a clinician.

## 6. Does it prescribe medicines?

No. Medication text may be shown as patient-reported or synthetic OCR evidence, but the prototype never creates a prescription or recommendation.

## 7. Is ABDM actually integrated?

No. The downloadable file is a local FHIR-ready sample bundle. There is no ABDM endpoint, health-ID lookup, consent workflow or patient-data exchange.

## 8. Why would a doctor use this?

It gives the doctor a consistent review surface: chief concern, reported medications/allergies, evidence label, source timeline and an explicit verification state. The aim is to reduce repetitive information collection, not replace consultation.

## 9. How is this different from an EHR?

An EHR is the longitudinal system of record. ClinSaar is an intake layer that prepares a traceable draft before consultation; a future FHIR boundary is intended to make downstream exchange possible.

## 10. How is patient privacy protected?

This demo uses synthetic records and asks users not to enter real clinical data. It has no backend or accounts. Before real deployment, it would need consent, authenticated roles, encryption, audit events, minimum-necessary retention and a compliant server-side architecture.

## 11. How does it work with poor internet?

The demonstrated flow works locally from a static page and has no network-dependent AI call. Live speech/OCR would require a carefully designed offline or queued server-side deployment; that is not implemented here.

## 12. How can this scale?

The static prototype separates the kiosk, evidence boundary, verification state and FHIR mapping. A production version would move these into consented backend services with role-based access and asynchronous adapters.

## 13. How would hospitals deploy it?

Start with a consented, synthetic or sandboxed pilot at intake. Validate completion, correction rate, language usability and clinician feedback before connecting any real record system or health-data service.

## 14. What if the patient gives incorrect information?

The record remains patient-reported until a clinician verifies it. The source timeline makes the provenance clear; the clinician can locally edit the synthetic demo draft.

## 15. How do you handle multiple Indian languages?

The current UI demonstrates Hindi and English only. Other regional languages are explicitly marked as a pilot-phase capability, not as implemented support.

## 16. What is the technical architecture?

The repository is a dependency-free static web prototype. Its production design shows a patient kiosk, intake orchestrator, optional server-side AI adapters, evidence labelling, clinician verification and a future FHIR boundary.

## 17. What is the biggest limitation?

The important limitation is that the AI/OCR/voice demonstrations are simulated. The next technical work is not adding risky automation; it is building consented, evaluated adapters and auditable clinician workflows.

## 18. What would you build next?

Consented server-side ASR/translation and OCR adapters, immutable source references, authenticated roles, audited clinician edits, and a usability pilot with appropriate governance.

## 19. How would you validate it in a real hospital?

With approval and consent, measure intake completion time, clinician correction rate, completion by language/access need, staff feedback and workflow fit. Do not claim clinical outcomes without a suitable study.

## 20. What makes this innovative?

It treats inclusion, evidence and clinician verification as one workflow: the patient’s multilingual story becomes a reviewable, traceable draft rather than an autonomous medical answer.

## 21. How is patient consent handled?

This prototype accepts no real patient data and has no consent backend. The UI warns users to use synthetic data only. Production consent would be a required, auditable workflow before any capture, processing or exchange of health information.

## 22. What is implemented today?

Today: the bilingual static kiosk, local voice demonstration, patient confirmation, synthetic evidence display, doctor queue, local edit/verification state, source timeline and selected-record FHIR-ready export. The page works without accounts, API keys or a backend.

## 23. What happens when the doctor rejects AI output?

The clinician can edit the local synthetic draft and leave it unverified; verification is a separate explicit action. In production, a rejected or corrected draft would require an authenticated, auditable edit event with preserved source references.
