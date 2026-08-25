# Controlled Vocabularies and Community Standards

This directory provides guidance on community-recognized metadata standards, ontologies, and identifier systems that support the creation of AI-ready genomic datasets.

| Resource | Description |
|----------|-------------|
| FAIR Genomes | Metadata schema for genomic sequencing studies. |
| EDAM | Ontology for bioinformatics data types, operations, formats, and topics. |
| MIxS (Genomic Standards Consortium) | Minimum information standards for sequencing experiments. |
| Sequence Ontology (SO) | Controlled vocabulary for genomic sequence features and variants. |
| Experimental Factor Ontology (EFO) | Standardized terminology for experimental variables and study metadata. |
| National Cancer Institute Thesaurus (NCIt) | Biomedical ontology covering diseases, drugs, anatomy, and experimental concepts. |
| Ontology Lookup Service (OLS4) | Search interface for biomedical ontologies. |
| Ontobee | Linked ontology browser and term lookup service. |
| GA4GH Variation Representation Specification (VRS) | Standard for computational representation of genomic variation. |
| Refget Sequences | GA4GH standard for content-derived checksum identifiers for individual reference sequences, enabling reproducible reference lookup independent of filename or format. https://ga4gh.github.io/refget/sequences/ |
| Refget Sequence Collections | Extends Refget Sequences to whole collections (e.g., a reference genome assembly), producing a single digest identifying an exact set of sequence names, lengths, and content. JSON Schema definitions available. https://ga4gh.github.io/refget/seqcols/ |
| W3C PROV | Standard for representing computational provenance. |
| RO-Crate | Standard for packaging research objects and associated metadata. |
| ORCID | Persistent identifiers for researchers. |
| DOI | Persistent identifiers for datasets and publications. |
| BioSample | Persistent identifiers for biological samples. |
| BioProject | Persistent identifiers for sequencing projects and studies. |
| HGVS | Standard nomenclature for describing genetic variants. |
| HGNC | Standardized human gene nomenclature. |
| Human Phenotype Ontology (HPO) | Controlled vocabulary for human phenotypic abnormalities. |
| MONDO Disease Ontology | Unified disease ontology integrating multiple disease vocabularies. |
| UBERON | Cross-species anatomy ontology. |
| Ontology for Biomedical Investigations (OBI) | Ontology describing biomedical investigations, assays, and biospecimens. |
| ChEBI | Ontology of chemical entities of biological interest. |
| RxNorm | Standardized identifiers for clinical drugs and medications. |
| ChEMBL | Database of bioactive molecules and drug-related information. |

## General Recommendations

- Use established community standards whenever possible.
- Prefer persistent identifiers over free-text values.
- Use controlled vocabularies to improve interoperability and reproducibility.
- When multiple ontologies are appropriate, document the standard used and provide mappings where possible.