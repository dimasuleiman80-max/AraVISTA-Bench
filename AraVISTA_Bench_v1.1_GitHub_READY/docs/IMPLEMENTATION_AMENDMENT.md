# AraVISTA Frozen Experiment v1.1 — Implementation and Ontology-Alignment Amendment

**Date:** 2026-09-18  
**Applies to:** AraVISTA-Bench v1.1  
**Supersedes for execution:** Frozen notebook v1.0/v1.0.1  
**Does not change:** model IDs, NLI thresholds, semantic thresholds, reranking weights, bootstrap count, random seed, action priority, query/evidence/QCES/action gold.

## 1. Why an amendment is required

The first locked run is retained as an **implementation diagnostic** rather than a headline experimental result. Post-run audit identified mechanical defects that prevented the frozen conceptual protocol from being executed as written:

1. Regexes were double-escaped (`\\d`, `\\w`, `\\u0600`), breaking Gregorian-year extraction and Arabic BM25 tokenization.
2. Transition detection used substring matching with `إلى/الى`; after Arabic normalization, `الى` could spuriously match inside unrelated words such as `حاليا`.
3. Missing `normalized_reference_time` values were converted to the literal string `nan`, preventing the 16 deliberately ambiguous control queries from triggering `CLARIFY`.
4. The implementation contained a recency-only `later_same_slot_state -> SUPERSEDES` fallback, contradicting the validated Round-3 rule that newer evidence alone is insufficient.
5. The notebook implemented pairwise relations as query-conditioned, although Relation Calibration Round 3 validated a text-only pairwise construct.

No threshold or weight is changed in response to test performance.

## 2. Validated construct alignment

Pairwise evidence relation is now defined as:

\[
R_{ij}=g(e_i,e_j)
\]

and query-conditioned evidence state remains:

\[
S_i=h(e_i,q,t_q,E_q,R).
\]

Round-3 operational direction is enforced:

- explicit transition `X -> Y` paired with a passage asserting `Y` -> `SUPPORTS`;
- explicit transition `X -> Y` paired with a passage asserting `X` -> `SUPERSEDES`;
- incompatible claims anchored to the same time -> `CONTRADICTS`;
- otherwise -> `NONE`.

The implication below remains explicitly invalid:

\[
	ext{newer}(e_i,e_j) 
ot\Rightarrow 	ext{SUPERSEDES}(e_i,e_j).
\]

## 3. Gold relation alignment

The query/evidence benchmark is unchanged. Only the manually selected relation edges are aligned to the Round-3 ontology.

- Total relation rows: **592** (unchanged)
- Rows with any source/target/label/rationale revision: **124**
- Rows whose source/target edge was rewired: **104**
- Rows whose relation label changed: **52**
- Old distribution: `{'NONE': 280, 'SUPPORTS': 124, 'SUPERSEDES': 108, 'CONTRADICTS': 80}`
- New distribution: `{'NONE': 268, 'SUPPORTS': 124, 'SUPERSEDES': 120, 'CONTRADICTS': 80}`

Specific systematic corrections:

- temporal-counterfactual, dialect, and control chains: later-state -> older-state `SUPERSEDES` edges are replaced by explicit-transition -> predecessor `SUPERSEDES` edges;
- stale traps: an explicit transition -> stale claim `SUPERSEDES` edge is added in place of a less informative NONE edge, while current-vs-stale remains `CONTRADICTS`;
- calendar dated-event -> predecessor edges become `NONE` when the source event does not explicitly encode predecessor-to-successor replacement.

## 4. Frozen quantities retained unchanged

- NLI contradiction threshold: **0.55**
- NLI entailment threshold: **0.55**
- semantic relation floor: **0.40**
- current-conflict support floor: **0.40**
- semantic weight: **1.00**
- state weight: **0.85**
- graph weight: **0.25**
- bootstrap resamples: **10,000**
- random seed: **20260917**
- dense model: `intfloat/multilingual-e5-small`
- NLI model: `MoritzLaurer/mDeBERTa-v3-base-mnli-xnli`

## 5. Reporting rule

The first run must be described only as an implementation diagnostic and must not be used as the paper's final headline result. The corrected v1.1 run is the first execution that matches the validated ontology and the preregistered conceptual protocol. Any future changes after seeing the corrected v1.1 results must be reported as post-test analysis and must not be silently folded into the frozen system.
