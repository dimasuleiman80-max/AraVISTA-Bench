# Data Dictionary

## data/queries.csv
Original columns retained from `benchmark_240_v1.1.csv`:
- `query_id`: stable query identifier.
- `scenario_id`: evidence-pack/scenario identifier.
- `family`: benchmark challenge family.
- `benchmark_split`: `HELDOUT_NEW_CHAIN` or `CALENDAR_CHALLENGE`.
- `chain_id`: temporal source-chain identifier.
- `query_text`: Arabic query text.
- `reference_surface`: temporal wording in the query.
- `normalized_reference_time`: resolved reference time.
- `dialect`: controlled Arabic variety where applicable.
- `calendar_surface`: calendar realization where applicable.
- `gold_answer`: construction-derived answer for answerable cases.
- `gold_action`: target selective action.
- `gold_evidence_ids`: semicolon-separated acceptable evidence IDs.
- `pair_group_id`: matched temporal/calendar/dialect group identifier.
- `expected_relation`: scenario-level expected relation where applicable.
- `calendar_gold_type`: calendar-equivalence metadata.
- `notes`: construction notes.
- `benchmark_version`: benchmark version.

## data/evidence.csv
Original columns retained from `evidence_packs_v1.1.csv`:
- `evidence_id`, `scenario_id`, `chain_id`
- `evidence_text`: source-grounded paraphrase or controlled benchmark text.
- `candidate_answer`
- `source_url`, `source_date`
- `provenance_type`
- `forced_rank`, `forced_similarity`, `visible_control_flag`

## data/qces_labels.csv
- `query_id`, `evidence_id`, `qces_state`, `is_gold_evidence`, `rationale`

## data/pairwise_relations.csv
- `relation_id`, `scenario_id`
- `source_evidence_id`, `target_evidence_id`
- `gold_relation`, `gold_rationale`

## data/splits.csv
Frozen query/scenario/family/split/chain manifest.

## Prediction files
The released prediction files are the direct outputs of the implementation-aligned frozen v1.1 run.
