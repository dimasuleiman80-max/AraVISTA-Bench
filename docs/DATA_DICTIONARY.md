# Data Dictionary

## `data/queries.csv`
- `query_id`: stable unique query identifier.
- `family`: benchmark challenge family.
- `group_id`: temporal twin, calendar pair, or dialect-intent group identifier when applicable.
- `split`: `HELDOUT_NEW_CHAIN` or `CALENDAR_CHALLENGE`.
- `query_ar`: Arabic query text.
- `dialect`: MSA / Levantine / Egyptian / Gulf / NA.
- `temporal_reference`: resolved query time.
- `temporal_query_type`: current / historical / ambiguous / future / other.
- `gold_action`: one of the five AraVISTA actions.
- `gold_answer`: construction-derived answer for answerable cases.
- `acceptable_evidence_ids`: semicolon-separated acceptable evidence IDs.

## `data/evidence.csv`
- `evidence_id`: stable unique evidence identifier.
- `chain_id`: temporal source-chain identifier.
- `source_org`: source organization.
- `source_title`: webpage/document title.
- `source_url`: original public URL.
- `source_date`: dated record/publication/update date.
- `evidence_text_or_release_note`: full text only if redistribution is permitted; otherwise a release note.
- `text_redistribution_status`: e.g., `included`, `metadata_only`, `permission_required`.
- `content_sha256`: optional checksum for reproducibility.

## `data/qces_labels.csv`
One row per query-evidence instance.

## `data/pairwise_relations.csv`
One row per distinct directed gold evidence pair.

## `data/splits.csv`
Leakage-control and split assignment information.

## Prediction files
One row per query-candidate evidence item from the frozen run.
