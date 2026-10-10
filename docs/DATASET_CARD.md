# Dataset Card

## Dataset name
AraVISTA-Bench v1.1

## Task
Controlled evaluation of temporal evidence validity, evidence relations, query-conditioned
evidence states, reranking, and selective actions in Arabic retrieval-augmented generation.

## Languages
Arabic (MSA and controlled Levantine, Egyptian, and Gulf variants). Some source metadata and
transition cues may include English.

## Unit of analysis
The benchmark includes query instances, candidate evidence passages, directed pairwise evidence
relations, query-conditioned evidence-state labels, gold actions, acceptable evidence sets, and
gold answers for answerable cases.

## Relation ontology
- SUPPORTS
- CONTRADICTS
- SUPERSEDES
- NONE

## Query-conditioned evidence-state ontology
- ACTIVE_SUPPORT
- HISTORICAL_SUPPORT
- SUPERSEDED
- CO_TEMPORAL_CONFLICT
- INSUFFICIENT

## Action ontology
- ANSWER
- ANSWER_WITH_UPDATE
- CLARIFY
- ABSTAIN_CONFLICT
- ABSTAIN_INSUFFICIENT

## Construction
The benchmark was derived from temporally ordered source chains and controlled transformations.
Gold answers, acceptable evidence sets, pairwise relation labels, and QCES labels are
construction-derived from the known source-chain structure and intended temporal configuration.

## Human calibration
- Action ontology: 25 calibration cases, two independent annotators, Cohen's kappa = 0.85.
- Final relation ontology: 40 balanced cases, two independent annotators, raw agreement = 90%,
  Cohen's kappa = 0.867, Gwet's AC1 approximately 0.867.

## Known limitations
- Controlled diagnostic benchmark rather than a sample of open-web Arabic traffic.
- Construction and initial labeling were AI-assisted.
- Full independent human reannotation of all benchmark labels was not performed.
- Historical validity near transition boundaries remains the principal failure mode.
- The relation module includes manually specified transition/replacement cues.
- Only one language family is evaluated.
- Free-form answer generation and citation faithfulness are not evaluated.

## Intended use
Research on temporal evidence reasoning, selective RAG, Arabic NLP, evidence-state modeling,
and controlled diagnostic evaluation.

## Out-of-scope use
The aggregate benchmark score should not be treated as an estimate of deployment performance.
