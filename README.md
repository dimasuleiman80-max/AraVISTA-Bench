# AraVISTA-Bench v1.1 — Public Release Draft

**Paper:** *AraVISTA: Evidence-State Reasoning for Selective Arabic Retrieval-Augmented Generation*

**Authors:** Dima Suleiman, Ruba Obiedat, Yazan Al-Zain

## Status

This package is a **public-release draft**. It already contains the verified aggregate numerical
results and the frozen configuration reported in the manuscript, plus schemas and documentation
for the full benchmark release.

It is **not yet the complete public dataset** because the query-level benchmark instances,
evidence-level records, pairwise labels, QCES labels, frozen predictions, and evaluation scripts
still need to be inserted from the final experiment files.

## Recommended public release

Use **Zenodo** for the archival dataset release and DOI. A GitHub repository can be used in
parallel for code and issue tracking, while Zenodo should contain a versioned archival snapshot.

## Dataset scope reported in the manuscript

- 240 Arabic queries
- 592 evidence passages
- 960 construction-derived QCES labels
- 592 construction-derived pairwise relation labels
- Corpus reference time: 2026-08-30
- Primary evaluation split: `HELDOUT_NEW_CHAIN` (200 queries)
- Separate challenge split: `CALENDAR_CHALLENGE` (40 queries)

## Benchmark families

- 48 temporal-counterfactual queries
- 40 calendar-equivalence queries
- 64 dialectal temporal-equivalence queries
- 32 stale-evidence traps
- 24 controlled co-temporal conflict instances
- 32 control / clarification / insufficient-evidence instances

## Important provenance note

The manuscript states that the benchmark was constructed from temporally ordered source chains
assembled from publicly accessible official institutional webpages and dated official records.

**Publicly accessible does not automatically mean public-domain or freely redistributable.**
Before publication of this repository, verify the redistribution rights for any verbatim source
passages. If the rights are unclear, release the benchmark annotations, IDs, metadata, source URLs,
source dates, hashes, and controlled transformations, while linking to the original source instead
of redistributing full third-party text.

## AI-assisted construction disclosure

Benchmark construction and initial labeling were AI-assisted under predefined source-chain
structures, temporal scenarios, and ontology definitions. The resulting materials and labels were
reviewed and refined by the authors. Human calibration was conducted separately for the action
and pairwise-relation ontologies. Dialectal variants were reviewed by a native Arabic speaker for
propositional and temporal equivalence.

## Files already included

`results/summary/` contains the verified aggregate numerical results reported in the manuscript.

`config/` contains the frozen configuration in machine-readable form.

`docs/` contains release documentation and schema descriptions.

`data/` currently contains schema-only CSV templates. Replace them with the final query-level
records before public release.

## Suggested citation

See `CITATION.cff`.

## License

The authors' original annotations, labels, metadata, schemas, and documentation can be released
under **CC BY 4.0**, subject to author approval.

Third-party source content is **not** automatically covered by that license. See
`docs/LICENSE_AND_REUSE_NOTES.md`.
