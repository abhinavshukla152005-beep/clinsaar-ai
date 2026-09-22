# Proof of work — ClinSaar AI

This document lets a judge reproduce the demo without trusting a slide deck.

## Deployment evidence

| Evidence | Public location | What it proves |
| --- | --- | --- |
| Live application | https://abhinavshukla152005-beep.github.io/clinsaar-ai/ | The prototype is publicly deployable and runs without a local setup. |
| Source repository | https://github.com/abhinavshukla152005-beep/clinsaar-ai | The implementation, architecture and test fixtures are inspectable. |
| Deployment settings | Repository → Settings → Pages | The live site is built from the repository's `main` branch. |

## Repeatable functional validation

| Test | Steps | Expected result | Status |
| --- | --- | --- | --- |
| Accessible language selection | Open Patient Kiosk; choose Hindi or English | Large touch cards; selected language appears in the flow | ✅ verified |
| Voice-to-history demonstration | Advance to guided intake; tap microphone | A bilingual synthetic statement appears locally; no audio leaves the browser | ✅ verified |
| Safety gate | Review the intake | Patient-provided text is retained; the structure is labelled as a demo template requiring clinician verification | ✅ verified |
| OCR evidence boundary | Run the demo OCR extraction | Synthetic original evidence, extracted text, demonstrative confidence and warning are visible | ✅ verified |
| Patient-to-doctor handoff | Confirm the synthetic intake | Record is added to doctor queue as “Needs Verification” | ✅ verified |
| Local queue filters | In Doctor Cockpit, select All, Pending, or Verified | Existing synthetic records visibly filter without network calls | ✅ verified |
| Inline clinician edit | Open a record; select Edit local draft; save or cancel | Patient-reported history fields can be locally edited; verification remains a separate action | ✅ verified |
| Clinician control | Open Doctor Cockpit; verify intake | State changes to “Doctor Reviewed” and source timeline updates | ✅ verified |
| Interoperability prototype | Open ABDM/FHIR; download JSON | Basic FHIR R4 (4.0.1) structural checks pass before the selected demo bundle downloads; page states no live ABDM connection | ✅ verified |
| Demo reset | Select Reset demo from navigation or cockpit | All browser-local demo records and flow state return to the synthetic initial state | ✅ verified |

## Synthetic test data

`test-data/synthetic-prescription-ocr.json` contains fictional prescription and lab-report fixtures. The dataset explicitly includes a low-confidence handwriting case so a future OCR integration can be evaluated for cautious failure rather than optimistic guessing.

## What is deliberately simulated

- Speech capture/transcription is a local interaction demonstration.
- OCR results are synthetic fixture outputs; this repository does not claim live OCR.
- Analytics are simulated operational metrics.
- ABDM/FHIR is a data-model/export demonstration; no live ABDM API exists in this project.

## FHIR validation boundary

The page performs a local FHIR R4 (4.0.1) **basic structural check**, not formal profile validation. It checks the bundle type, five demonstration resource types, and Patient references in Encounter and Observation. It does not validate an implementation guide, terminology bindings, clinical correctness, an ABDM profile, or a remote FHIR server response.

These boundaries are displayed in the app and documentation to prevent misleading clinical claims.
