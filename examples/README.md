# Examples

Worked, end-to-end AI-ready metadata packages for common sequencing workflows.
Each renders the sample-source, sequencing-chemistry, and pipeline metadata the
manuscript describes as structured, identifier-anchored covariates (see
[`../vocabularies/resources.md`](../vocabularies/resources.md)), serialized as
both YAML and JSON.

| Assay | Directory | Description |
|-------|-----------|-------------|
| Genome sequencing | [`genome_sequencing/`](genome_sequencing/) | Two-center autism genome-sequencing composite (five packages + `cohort_context`) modelling the manuscript's use case. |
| Exome sequencing | [`exome_sequencing/`](exome_sequencing/) | Same package shape plus a `capture` block and capture-specific QC. |
| Targeted panel | [`targeted_panel/`](targeted_panel/) | Same package shape plus a `panel` block with HGNC-identified genes and a real GRCh38 target-regions BED. |

A blank, adaptable form is in [`../templates/`](../templates/); a workflow-run
provenance record is in [`../provenance/`](../provenance/); a draft JSON Schema and
a CI check are in [`../schemas/`](../schemas/) and `.github/workflows/`.

## Conventions

- Unfilled values use the angle-bracket convention (e.g. `<uuid>`,
  `<BioSample accession>`). Placeholder checksums appear in three registers by
  digest kind: `sha256:<digest>` (files/reads), `md5:<fasta-md5>` (the reference
  FASTA), and `sha256:<lock-digest>` (the reference-manifest lock).
- Field-level ontology anchoring follows the manuscript's Supplementary Table 1.
  `GIST-*-EX` package ids are GIST-local and non-resolving; `ga4gh:` is the GA4GH
  VRS namespace (computed, content-derived identifiers with no central resolver).
- The GS file's root key is `metadata_packages` (a **list** of packages); the ES
  and panel files use `metadata_package` (a single **mapping**) — a consumer must
  handle both.

> [!IMPORTANT]
> **Illustrative / synthetic.** All subject identifiers, values, checksums, container
> digests, and accessions are placeholders and site identities are generalized; no values
> derive from human subjects. Deliberate exceptions, marked inline: the GA4GH Refget seqcol
> digest and the ontology CURIEs (and, in the panel example, the HGNC gene IDs and the
> target-regions BED with its real sha256).
