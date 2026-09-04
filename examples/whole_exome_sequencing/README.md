# Whole Exome Sequencing (WES)

This directory contains an example AI-ready metadata package for a whole exome
sequencing experiment: [`wes_example.metadata.yaml`](wes_example.metadata.yaml)
(JSON twin: `wes_example.metadata.json`).

It uses the same package structure as the
[WGS example](../whole_genome_sequencing/) — subject, sample, sequencing, reference
(Refget seqcol), processing/workflow, sequence-file, variant (VRS), QC, ancestry,
phenotype (Phenopacket), and provenance (W3C PROV) — adapted to a capture-based
exome assay: it adds a `capture` block (target kit + target-regions BED) and
reports capture-specific QC (mean target coverage, % target bases at 20x,
on-target rate).

> [!IMPORTANT]
> **Illustrative / synthetic.** All subject identifiers, values, checksums, container
> digests, and accessions are placeholders and site identities are generalized; no values
> derive from human subjects. Deliberate exceptions, marked inline: the GA4GH Refget seqcol
> digest and the ontology CURIEs (and, in the panel example, the HGNC gene IDs and the
> target-regions BED with its real sha256).
