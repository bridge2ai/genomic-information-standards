# Genome Sequencing (GS)

This directory contains an example set of AI-ready metadata packages for a genome
sequencing experiment:
[`autism_gs_composite.metadata.yaml`](autism_gs_composite.metadata.yaml)
(JSON twin: `autism_gs_composite.metadata.json`).

It accompanies the manuscript's autism genome-sequencing use case, in which two sequencing
centers (**B1** and **B2**) differ in the **proportion** of saliva-derived samples,
in **sequencing-chemistry mix** (B1 all 2-channel; B2 a mix of 2- and 4-channel),
and in **alignment/variant-calling pipeline** (BWA-MEM/GATK vs DRAGMAP/DRAGEN) —
partial confounding, not a clean 1:1 mapping.

The file holds **five sample packages** that spread specimen across both centers
and chemistry across B2 (4-channel shown on blood, so chemistry is not aliased
with specimen), plus a **`cohort_context`** block recording the center-level
specimen/chemistry proportions that make the differences statistically
identifiable. Each package renders subject/clinical, sample, sequencing, reference
(GA4GH Refget Sequence Collections), processing/workflow, sequence-file, variant
(GA4GH VRS; a worked allele is shown in B1-0001), QC, ancestry, phenotype (GA4GH
Phenopacket), and provenance (W3C PROV) metadata, and ends with a flattened
`analysis_covariates` block a model consumes directly. Ontology anchoring follows
the manuscript's Supplementary Table 1.

The companion workflow-provenance record is
[`../../provenance/gs_align_call_run.provenance.yaml`](../../provenance/gs_align_call_run.provenance.yaml)
(the illustrative run for B1-0001);
a blank, adaptable form is
[`../../templates/genomic_metadata_package_template.yaml`](../../templates/genomic_metadata_package_template.yaml).

> [!IMPORTANT]
> **Illustrative / synthetic.** All subject identifiers, values, checksums, container
> digests, and accessions are placeholders and site identities are generalized; no values
> derive from human subjects. Deliberate exceptions, marked inline: the GA4GH Refget seqcol
> digest and the ontology CURIEs (and, in the panel example, the HGNC gene IDs and the
> target-regions BED with its real sha256).
