# Direct Relation Policy (DRP) comparator

DRP was added during peer review as a stronger selective-action comparator. It addresses the limitation of comparing AraVISTA's five-way selective policy only against the structural default-`ANSWER` baseline.

## Inputs

DRP uses the same frozen Dense-E5 semantic scores, benchmark-supplied canonical temporal reference, and frozen query-independent relation predictions. It does not use QCES states, QCES confidence, graph signals, or state-aware reranking.

## Ordered policy

1. Missing or ambiguous temporal reference -> `CLARIFY`.
2. Future temporal reference -> `ABSTAIN_INSUFFICIENT`.
3. A predicted `CONTRADICTS` edge whose endpoints both have semantic score >= 0.40 -> `ABSTAIN_CONFLICT`.
4. Maximum semantic score < 0.20 -> `ABSTAIN_INSUFFICIENT`.
5. For a current query, a predicted `SUPERSEDES` edge whose source passage has semantic score >= 0.40 -> `ANSWER_WITH_UPDATE`.
6. Otherwise -> `ANSWER`.

The 0.20 and 0.40 thresholds are inherited from the frozen AraVISTA configuration; no new threshold was tuned for DRP.

## Reported results

- Full 240-query benchmark: DRP action accuracy 92.50%, Macro-F1 92.35%; AraVISTA action accuracy 95.42%, Macro-F1 94.83%.
- 200-query held-out core: DRP 91.00% versus AraVISTA 96.00%; paired difference +5.00 percentage points, 95% CI +1.55 to +9.27.

The correct interpretation is that most of the original 24%-to-96% gap reflects introducing a selective policy at all; QCES provides a smaller additional gain over DRP.
