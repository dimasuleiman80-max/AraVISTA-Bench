# AraVISTA-Bench v1.1

**Evidence-State Reasoning for Selective Arabic Retrieval-Augmented Generation**

AraVISTA-Bench v1.1 is a controlled Arabic benchmark for evaluating temporal evidence
validity, directed relations among retrieved passages, query-conditioned evidence states,
state-aware reranking, and selective system actions in retrieval-augmented generation.

## Authors

- Dima Suleiman — The University of Jordan
- Ruba Obiedat — The University of Jordan
- Yazan Al-Zain — The University of Jordan

## Benchmark size

- 240 Arabic queries
- 592 evidence passages
- 960 construction-derived QCES labels
- 592 construction-derived directed pairwise relation labels
- Corpus reference time: 2026-08-30
- 200-query `HELDOUT_NEW_CHAIN` split
- 40-query `CALENDAR_CHALLENGE` split

## Challenge families

- 48 temporal-counterfactual queries
- 40 calendar-equivalence queries
- 64 dialectal temporal-equivalence queries
- 32 stale-evidence traps
- 24 controlled co-temporal conflict instances
- 32 control / clarification / insufficient-evidence instances

## Ontologies

### Pairwise evidence relations
`SUPPORTS`, `CONTRADICTS`, `SUPERSEDES`, `NONE`

### Query-conditioned evidence states (QCES)
`ACTIVE_SUPPORT`, `HISTORICAL_SUPPORT`, `SUPERSEDED`,
`CO_TEMPORAL_CONFLICT`, `INSUFFICIENT`

### Selective actions
`ANSWER`, `ANSWER_WITH_UPDATE`, `CLARIFY`,
`ABSTAIN_CONFLICT`, `ABSTAIN_INSUFFICIENT`

## Repository contents

- `data/queries.csv` — complete 240-query benchmark master file.
- `data/evidence.csv` — 592 evidence passages with source metadata and candidate answers.
- `data/qces_labels.csv` — 960 construction-derived query/evidence state labels.
- `data/pairwise_relations.csv` — 592 construction-derived directed relation labels.
- `data/splits.csv` — frozen evaluation split/chain manifest.
- `data/model_input_queries.csv` and `data/model_input_evidence.csv` — model-facing inputs.
- `data/predictions_dense_e5.csv` and `data/predictions_bm25.csv` — frozen end-to-end outputs.
- `data/pairwise_predictions.csv` — frozen pairwise relation-model outputs.
- `data/qces_predictions_dense_e5.csv` and `data/qces_predictions_bm25.csv` — frozen QCES outputs.
- `code/` — implementation-aligned frozen notebook.
- `config/` — frozen run manifest and software/model versions.
- `results/` — aggregate results, bootstrap intervals, ablations, and class-wise metrics.
- `provenance/` — source URL registry.
- `docs/` — dataset card, data dictionary, implementation notes, and validation report.

## Data provenance

The benchmark was derived from temporally ordered source chains assembled from publicly
accessible official institutional webpages and dated official records. The evidence text
released here is explicitly identified in the benchmark as source-grounded paraphrase,
controlled stale paraphrase, controlled synthetic conflict, or controlled context. The
original linked webpages remain third-party materials and are not relicensed by this repository.

## AI-assisted construction disclosure

ChatGPT (OpenAI) was used as an assistive tool during controlled benchmark development,
including linguistic realization, reformulation, and initial assignment of construction-derived
labels under predefined source-chain structures, temporal scenarios, and ontology definitions.
The resulting materials and labels were reviewed and refined by the authors. Human calibration
was conducted separately for the action and pairwise-relation ontologies, and dialectal variants
were reviewed by a native Arabic speaker for propositional and temporal equivalence.

## Human calibration reported in the paper

- Action ontology: 25 calibration cases, two independent annotators, Cohen's kappa = 0.85.
- Final four-way relation calibration: 40 balanced cases (10/class), two independent annotators,
  raw agreement = 90%, Cohen's kappa = 0.867, Gwet's AC1 approximately 0.867.

## Frozen evaluation

The release contains the implementation-aligned v1.1 frozen run. The run manifest records
the exact model IDs, model commits, thresholds, reranking weights, software versions,
10,000 bootstrap resamples, and random seed.

No held-out test-time threshold or weight tuning was performed after the frozen run was examined.

## Reproduction

Open:

`code/AraVISTA_Frozen_Pairwise_Relation_Reasoner_v1.1_IMPLEMENTATION_ALIGNED.ipynb`

The notebook references the v1.1 input files included in `data/`. Model downloads require
network access to the model repositories.

## Validation

See `docs/VALIDATION_REPORT.md`. The public package contains exactly:

- 240 unique queries
- 592 unique evidence passages
- 960 QCES gold labels
- 592 pairwise relation gold labels
- 200 held-out-new-chain queries
- 40 calendar-challenge queries

All released QCES and relation IDs were checked against the released query/evidence files.

## License and third-party materials

The original AraVISTA benchmark annotations, controlled/paraphrased benchmark text,
metadata created by the authors, documentation, and result files in this repository are
released under **CC BY 4.0**, subject to the notice in `LICENSE`.

Linked source webpages are third-party materials and remain subject to their original
rights and terms.

## Citation

Zenodo DOI: **10.5281/zenodo.23277316**

Persistent link: https://doi.org/10.5281/zenodo.23277316

See `CITATION.cff` for citation metadata. The DOI is reserved and becomes registered
when the Zenodo record is published.
