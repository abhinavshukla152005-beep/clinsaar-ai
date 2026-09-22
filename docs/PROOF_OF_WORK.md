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
| Clinician control | Open Doctor Cockpit; verify intake | State changes to “Doctor Reviewed” and source timeline updates | ✅ verified |
| Interoperability prototype | Open ABDM/FHIR; download JSON | Future-ready FHIR sample bundle downloads; page states no live ABDM connection | ✅ verified |

## Synthetic test data

`test-data/synthetic-prescription-ocr.json` contains fictional prescription and lab-report fixtures. The dataset explicitly includes a low-confidence handwriting case so a future OCR integration can be evaluated for cautious failure rather than optimistic guessing.

## What is deliberately simulated

- Speech capture/transcription is a local interaction demonstration.
- OCR results are synthetic fixture outputs; this repository does not claim live OCR.
- Analytics are simulated operational metrics.
- ABDM/FHIR is a data-model/export demonstration; no live ABDM API exists in this project.

These boundaries are displayed in the app and documentation to prevent misleading clinical claims.
