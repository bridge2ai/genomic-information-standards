# Targeted Panel Sequencing

This directory contains an example AI-ready metadata package for a targeted gene
panel: [`panel_example.metadata.yaml`](panel_example.metadata.yaml) (JSON twin:
`panel_example.metadata.json`).

It illustrates assay-specific metadata, targeted regions, sequencing platform
information, variant representation, and supporting quality control metrics, using
the same package structure as the [WGS example](../whole_genome_sequencing/): it
adds a `panel` block (panel name/version, gene count, a sample of well-established
ASD genes with real HGNC ids, and a real GRCh38 target-regions BED —
[`targets/ndd_panel_v2.1.bed`](targets/ndd_panel_v2.1.bed), covering the spans of
the ten example genes with a real sha256) and reports very deep on-target QC (mean
target coverage, % target bases at 100x, on-target rate). It intentionally omits
`genetic_ancestry`: a sub-megabase panel target cannot support 1000 Genomes PCA
projection.

> [!IMPORTANT]
> **Illustrative / synthetic.** All subject identifiers, values, checksums, container
> digests, and accessions are placeholders and site identities are generalized; no values
> derive from human subjects. Deliberate exceptions, marked inline: the GA4GH Refget seqcol
> digest and the ontology CURIEs (and, in the panel example, the HGNC gene IDs and the
> target-regions BED with its real sha256).
