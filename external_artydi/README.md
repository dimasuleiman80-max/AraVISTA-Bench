# External ArTyDi-QA validation

This folder contains the public external-validation package added after review of the AraVISTA study.

The package includes:
- the frozen 200-case human reference labels linked by public ArTyDi-QA example ID;
- inter-annotator agreement summary;
- the restricted external-evaluation protocol;
- a public reproduction notebook;
- predictions, aggregate metrics, paired McNemar tests, and the run manifest.

The original ArTyDi-QA question/context text is not republished here. Reproduction uses the official ArTyDi-QA release.

Key results:
- Final human reference: 128 ANSWERABLE, 67 UNANSWERABLE, 5 UNCERTAIN.
- Binary human/source agreement on 195 comparable cases: 92.82%, Cohen's kappa = 0.836.
- E5-only: 85.64% accuracy, Macro-F1 = 0.833.
- AraVISTA-Restricted: 81.54% accuracy, Macro-F1 = 0.799.
- E5-only vs AraVISTA-Restricted: Holm-adjusted McNemar p = 0.115.

This is a single-passage external transfer check, not an evaluation of the full multi-passage QCES/supersession/conflict pipeline.
