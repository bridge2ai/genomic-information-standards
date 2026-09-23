# Bridge2AI Genomic Information Standards (GIST) Implementation Resources

This repository serves as the companion implementation resource for the manuscript:

> **Bridge2AI Recommendations for AI-Ready Genomic Data**

This repository supports practical adoption of the manuscript's recommendations with worked metadata packages, reusable templates, schemas, validation tooling, provenance records, and links to community standards.

## What is available

The following resources are available in this repository:

- **Worked metadata packages** for three sequencing workflows: genome, exome, and targeted panel sequencing (represented in both YAML and JSON)
- **A blank metadata template** covering sample, sequencing, reference, processing, variant, QC, ancestry, phenotype, and provenance metadata
- **A JSON Schema** for the metadata packages, along with the GA4GH Refget Sequence Collections v1.0.0 schemas
- **A GitHub Actions workflow** that validates the example packages against the schema, checks each YAML and JSON pair for equivalence, and cross-checks per-package arithmetic
- **A workflow-run provenance record** following the W3C PROV activity/entity model, chained to one of the example packages
- **Example data files** in each recommended storage format: BAM, CRAM, VCF, GFF3, and FASTA (drawn from GIAB, IGSR, and GENCODE, with checksums, tool versions, and validation output)
- **Vocabulary and identifier guidance**, including a table of community standards and guidance on Refget sequence and sequence collection identifiers

## Start here

- Read [`examples/`](examples/) to see completed packages
- Copy [`templates/genomic_metadata_package_template.yaml`](templates/genomic_metadata_package_template.yaml) and fill in the bracketed placeholders to build your own
- Validate it against [`schemas/genomic_metadata_package_v0.1.0.json`](schemas/genomic_metadata_package_v0.1.0.json), the same schema checked in CI ([`.github/workflows/validate-metadata.yml`](.github/workflows/validate-metadata.yml))

## Repository Organization

| Directory | Description |
|-----------|-------------|
| **examples/** | Metadata packages for genome, exome, and targeted panel sequencing, plus example data files in each recommended storage format under `examples/example_files/`. |
| **templates/** | Reusable metadata templates in YAML and JSON. |
| **schemas/** | Machine-readable metadata schemas: the GIST metadata package schema and the GA4GH Refget Sequence Collections schemas. |
| **vocabularies/** | Recommended ontologies, controlled vocabularies, and terminology guidance. |
| **identifiers/** | Guidance for persistent identifiers and standardized identifier systems. |
| **provenance/** | An example workflow-run provenance record for capturing computational provenance. |

## Scope

The resources in this repository are intended to complement the recommendations presented in the manuscript and are not intended to prescribe a single implementation. Instead, they provide practical examples and guidance that may be adapted to different sequencing assays, computational workflows, institutional environments, and evolving community standards.

The example metadata packages and the provenance record are synthetic. No values derive from human subjects; subject identifiers, accessions, checksums, container digests, and dates are placeholders. Values that are real (the GA4GH Refget sequence collection digest, ontology CURIEs, HGNC gene identifiers, and the panel target regions BED) are marked inline. The files under `examples/example_files/` are public reference data, either unmodified or subset to a region, and documented with their upstream sources.

## Continued development

The Bridge2AI Genomic Information Standards Team maintains this repository as a living community resource. We will extend these materials as community best practices evolve, including broader coverage of the recommended metadata fields in the worked examples.

## Citation

If you use these implementation resources, please cite the accompanying manuscript.

> Cannon, Matthew, Wesley Goar, In-Hee Lee, James Stevenson, Amy Heiser, Nathan Sheffield, James Eddy, Monica Munoz-Torres, Sek Won Kong, and Alex H. Wagner. 2025. “Bridge2AI Recommendations for AI-Ready Genomic Data.” arXiv [q-Bio.OT]. arXiv. https://doi.org/10.48550/arXiv.2512.11519.
