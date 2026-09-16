# Controlled Vocabularies and Community Standards

This directory provides guidance on community-recognized metadata standards, ontologies, and identifier systems that support the creation of AI-ready genomic datasets. For additional information on each resource, please use the corresponding provided links.

| Resource | Description | Resource Link |
|---|---|---|
| FAIR Genomes | Metadata schema for genomic sequencing studies. | [FAIR Genomes](https://fairgenomes.org/) |
| EDAM | Ontology for bioinformatics data types, operations, formats, and topics. | [EDAM Ontology](https://edamontology.org/) |
| MIxS (Genomic Standards Consortium) | Minimum information standards for sequencing experiments. | [MIxS Documentation](https://genomicsstandardsconsortium.github.io/mixs/) |
| Sequence Ontology (SO) | Controlled vocabulary for genomic sequence features and variants. | [Sequence Ontology](http://www.sequenceontology.org/) |
| Experimental Factor Ontology (EFO) | Standardized terminology for experimental variables and study metadata. | [Experimental Factor Ontology](https://www.ebi.ac.uk/efo/) |
| National Cancer Institute Thesaurus (NCIt) | Biomedical ontology covering diseases, drugs, anatomy, and experimental concepts. | [NCI Thesaurus Browser](https://ncithesaurus.nci.nih.gov/ncitbrowser/) |
| Ontology Lookup Service (OLS4) | Search interface for biomedical ontologies. | [EMBL-EBI OLS4](https://www.ebi.ac.uk/ols4/) |
| Ontobee | Linked ontology browser and term lookup service. | [Ontobee](https://ontobee.org/) |
| GA4GH Variation Representation Specification (VRS) | Standard for computational representation of genomic variation. | [GA4GH VRS](https://vrs.ga4gh.org/) |
| Refget Sequences | GA4GH standard for content-derived checksum identifiers for individual reference sequences, enabling reproducible reference lookup independent of filename or format. | [Refget Sequences](https://ga4gh.github.io/refget/sequences/) |
| Refget Sequence Collections | Extends Refget Sequences to whole collections, such as reference genome assemblies, producing a digest that identifies an exact collection of sequence names, lengths, and content. | [Refget Sequence Collections](https://ga4gh.github.io/refget/seqcols/) |
| W3C PROV | Standard for representing computational provenance. | [W3C PROV Overview](https://www.w3.org/TR/prov-overview/) |
| RO-Crate | Standard for packaging research objects and their associated metadata. | [RO-Crate](https://www.researchobject.org/ro-crate/) |
| ORCID | Persistent identifiers for researchers and contributors. | [ORCID](https://orcid.org/) |
| DOI | Persistent identifiers for datasets, publications, and other research objects. | [DOI Foundation](https://www.doi.org/) |
| BioSample | Persistent identifiers and metadata records for biological samples. | [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/) |
| BioProject | Persistent identifiers and organizational records for sequencing projects and studies. | [NCBI BioProject](https://www.ncbi.nlm.nih.gov/bioproject/) |
| HGVS | Standard nomenclature for describing genetic sequence variants. | [HGVS Nomenclature](https://hgvs-nomenclature.org/) |
| HGNC | Standardized human gene nomenclature and stable gene identifiers. | [HGNC](https://www.genenames.org/) |
| Human Phenotype Ontology (HPO) | Controlled vocabulary for human phenotypic abnormalities. | [Human Phenotype Ontology](https://hpo.jax.org/) |
| Mondo Disease Ontology | Unified disease ontology integrating multiple disease vocabularies. | [Mondo Disease Ontology](https://mondo.monarchinitiative.org/) |
| UBERON | Cross-species anatomy ontology. | [UBERON](https://obophenotype.github.io/uberon/) |
| Ontology for Biomedical Investigations (OBI) | Ontology describing biomedical investigations, assays, protocols, and biospecimens. | [OBI](https://obi-ontology.org/) |
| ChEBI | Ontology and database of chemical entities of biological interest. | [ChEBI](https://www.ebi.ac.uk/chebi/) |
| RxNorm | Standardized names and identifiers for clinical drugs and medications. | [RxNorm](https://www.nlm.nih.gov/research/umls/rxnorm/) |
| ChEMBL | Curated database of bioactive molecules, drug targets, mechanisms, and bioactivity information. | [ChEMBL](https://www.ebi.ac.uk/chembl/) |

## General Recommendations

- Use established community standards whenever possible.
- Prefer persistent identifiers over free-text values.
- Use controlled vocabularies to improve interoperability and reproducibility.
- When multiple ontologies are appropriate, document the standard used and provide mappings where possible.