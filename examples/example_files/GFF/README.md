# GFF3 Example: GENCODE BRCA1 Regional Annotation

This example is derived from the comprehensive primary-assembly GFF3 annotation distributed with GENCODE Human Release 49. To provide a compact and interpretable annotation example suitable for inclusion in this repository, features overlapping the BRCA1 locus at `chr17:43040000-43175000` were extracted from the GRCh38 annotation.

The complete upstream GFF3 is not committed because of its size. This repository instead includes the regional annotation in uncompressed and BGZF-compressed forms, a Tabix index, validation results, provenance information, and commands for obtaining the authoritative upstream resource.

The selected region demonstrates the hierarchical representation of a protein-coding gene and its associated transcripts, exons, coding sequences, and untranslated regions. It also illustrates the use of stable GENCODE, Ensembl, and HGNC identifiers in a machine-readable genomic annotation.

The complete annotation was obtained from GENCODE Human Release 49:

`https://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_49/gencode.v49.primary_assembly.annotation.gff3.gz`

## Provenance Table

| Field | Value |
|---|---|
| Dataset | GENCODE comprehensive gene annotation |
| Organism | *Homo sapiens* |
| GENCODE release | Human Release 49 |
| Genome assembly | GRCh38 |
| Assembly patch release associated with GENCODE 49 | GRCh38.p14 |
| Annotation scope | Primary assembly |
| Annotation format | GFF3 |
| Annotation target | BRCA1 locus |
| Gene symbol | BRCA1 |
| Ensembl gene identifier | `ENSG00000012048` |
| HGNC identifier | `HGNC:1100` |
| Source interval | `chr17:43040000-43175000` |
| Coordinate convention | 1-based, end-inclusive |
| Upstream distributor | GENCODE / EMBL-EBI |
| Upstream file | `gencode.v49.primary_assembly.annotation.gff3.gz` |
| Regional exemplar | `GENCODE.v49.GRCh38.BRCA1.gff3` |
| Compressed exemplar | `GENCODE.v49.GRCh38.BRCA1.gff3.gz` |
| Regional index | `GENCODE.v49.GRCh38.BRCA1.gff3.gz.tbi` |
| Retrieval date | September 3, 2026 |
| Integrity | SHA-256 values recorded in `validation/sha256sums.txt` |
| Validation software | Recorded in `validation/software-versions.txt` |
| Modifications | Overlapping features were extracted and coordinate-sorted; feature fields and attributes were not otherwise modified |


## Metrics

The regional annotation was evaluated for file presence, compression integrity, GFF3 structure, coordinate validity, sorting, identifier content, and indexed retrieval.

| Validation metric | Result |
|---|---|
| GFF version | GFF3 |
| Reference sequence | `chr17` |
| Extraction interval | `chr17:43040000-43175000` |
| Coordinate convention | 1-based, end-inclusive |
| Target gene | BRCA1 |
| Ensembl gene identifier | `ENSG00000012048` |
| HGNC identifier | `HGNC:1100` |
| Regional files present and nonempty | Validated in `validation/file-presence.txt` |
| Regional annotation record count | Recorded in `validation/indexed-record-count.tsv` |
| Feature types and counts | Recorded in `validation/feature-counts.tsv` |
| Stable identifiers and parent relationships | Summarized in `validation/attribute-summary.tsv` |
| BRCA1 gene record | Recorded in `validation/BRCA1-gene-record.tsv` |
| Nine-column GFF3 structure | Validated in `validation/column-validation.txt` |
| Coordinate and strand values | Validated in `validation/coordinate-validation.txt` |
| Coordinate sorting | Validated in `validation/sort-validation.txt` |
| BGZF compression | Validated in `validation/compression-check.txt` |
| Indexed reference sequence | Recorded in `validation/indexed-contigs.txt` |
| Indexed regional retrieval | Validated in `validation/index-validation.txt` |
| File-integrity checksums | Recorded in `validation/sha256sums.txt` |
| Validation software | Recorded in `validation/software-versions.txt` |

These results apply only to the regional BRCA1 annotation and should not be interpreted as summary statistics for the complete GENCODE Human Release 49 annotation.