# Post-review supplementary diagnostics

This directory contains reviewer-requested analyses added during revision of the AraVISTA manuscript. These are supplementary diagnostics and comparator analyses; they do **not** replace or modify the original v1.1 frozen predictions, thresholds, benchmark labels, or frozen reranking configuration.

## Included files

- `action_class_metrics_drp_vs_aravista.csv` and the two action confusion matrices — class-wise selective-action comparison of DRP and AraVISTA.
- `temporal_date_heuristic_summary.csv` — date-only temporal comparator with the paired bootstrap interval reported in the revised manuscript.
- `reranking_weight_sensitivity.csv` and `state_graph_grid_sensitivity.csv` — post-review sensitivity diagnostics around the frozen reranking weights. The frozen configuration remains semantic=1.00, state=0.85, graph=0.25.
- `transition_cue_dropout_sensitivity.csv` — transition-cue dropout diagnostic for the pairwise relation reasoner.
- `benchmark_label_audit_summary.csv` and `benchmark_label_audit_qces_class_metrics.csv` — aggregate results from the blind benchmark-label audit.
- `source_diversity_audit_summary.csv` and `provenance_composition_summary.csv` — counts reproducibly derived from the frozen repository data and source registry.

The original annotation/adjudication workbooks are retained separately by the authors; this public directory releases the aggregate audit results reported in the manuscript.

## Interpretation

These files were produced after reviewer feedback to test comparator fairness, label quality, source diversity, and sensitivity. They were not used to tune the frozen thresholds or to alter the original v1.1 predictions after inspection of held-out results.
