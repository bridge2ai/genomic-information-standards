# Exome Sequencing (ES)

This directory contains an example AI-ready metadata package for an exome
sequencing experiment: [`es_example.metadata.yaml`](es_example.metadata.yaml)
(JSON twin: `es_example.metadata.json`).

It uses the same package structure as the
[GS example](../genome_sequencing/) — subject, sample, sequencing, reference
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
