# Controlled Vocabularies

This directory provides guidance on the use of community-recognized ontologies, controlled vocabularies, and standardized identifiers for representing genomic metadata.

## Available guidance

- [`resources.md`](resources.md) — a reference table of the community metadata standards, ontologies, and identifier systems that support AI-ready genomic datasets, with a link to each resource, followed by general recommendations for choosing among them.

The resources listed there include the metadata schemas and minimum-information standards cited in the manuscript (FAIR Genomes, EDAM, MIxS), the ontologies used to anchor individual fields (NCIt, EFO, OBI, UBERON, Mondo, HPO, Sequence Ontology), ontology lookup services (OLS4, Ontobee), the GA4GH standards for variation and reference sequences (VRS, Refget), provenance standards (W3C PROV, RO-Crate), and persistent identifier systems (ORCID, DOI, BioSample, BioProject, HGNC, HGVS).

## Applying these vocabularies

The packages under [`../examples/`](../examples/) and the template in [`../templates/`](../templates/) show these vocabularies in use. Each file opens with a `prefixes` block that expands its CURIEs, terms are written as `{ label, id }` pairs, and any field whose terminology is fixed by the manuscript's Supplementary Table 1 cites that reference in a trailing comment.

## Continued development

We will add terminology mappings and cross-ontology alignments as community best practices evolve. Where multiple ontologies are appropriate, document the standard used and provide mappings where possible.
