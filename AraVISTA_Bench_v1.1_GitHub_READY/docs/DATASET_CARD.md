# Dataset Card — AraVISTA-Bench v1.1

## Purpose
Controlled diagnostic evaluation of temporal evidence validity and selective behavior in Arabic RAG.

## Language
Arabic, including controlled Modern Standard Arabic, Levantine, Egyptian, and Gulf variants.

## Construction
Instances were built from temporally ordered official-source chains and controlled benchmark
transformations. Gold answers, acceptable evidence sets, pairwise relations, and QCES labels are
construction-derived from known source-chain structure and the intended temporal scenario.

## Important caveat
This is a controlled diagnostic benchmark, not a representative sample of open-web Arabic RAG
traffic or an estimate of deployment performance.

## Known limitations
- AI-assisted construction and initial labeling.
- No independent manual annotation of every query-evidence instance.
- Historical validity near transition boundaries remains difficult.
- Transition/replacement reasoning partly uses manually specified cues.
- Limited retrieval/model scale.
- No free-form generation or citation-faithfulness evaluation in the frozen experiment.

## Ethical/privacy status
The released benchmark does not contain private participant records. Source grounding is through
publicly accessible official institutional webpages and dated official records. Human calibrators
are not identified in the public data files.
