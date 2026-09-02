# CRAM Exemplar: NA12878 Oxford Nanopore Alignment

This example is derived from the International Genome Sample Resource (IGSR) Oxford Nanopore sequencing data for the human reference sample NA12878. The original CRAM contains long-read alignments to GRCh38. To provide a compact example suitable for inclusion in this repository, alignments overlapping `chr20:10000000-10100000` were extracted into a regional CRAM file with a corresponding CRAI index.

The complete upstream CRAM is not included because of its size. The repository instead provides the upstream CRAM header, its original CRAI index, IGSR sample metadata and data-reuse information, and a derived regional CRAM that retains representative alignment, read-group, reference, and processing-provenance records.

## Provenance Table

| Field | Value |
|---|---|
| Dataset | 1000 Genomes Oxford Nanopore Vienna data collection |
| Sample | NA12878 |
| Biosample | SAME123392 |
| Organism | *Homo sapiens* |
| Population | Utah residents with Northern and Western European ancestry (CEPH) |
| Sequencing platform | Oxford Nanopore Technologies |
| Reference assembly | GRCh38 |
| Upstream distributor | International Genome Sample Resource / 1000 Genomes |
| Upstream CRAM | `NA12878.hg38.cram` |
| Upstream index | `NA12878.hg38.cram.crai` |
| Upstream header | `NA12878.hg38.header.sam` |
| Regional example | `NA12878.ONT.hg38.chr20_10000000-10100000.cram` |
| Regional index | `NA12878.ONT.hg38.chr20_10000000-10100000.cram.crai` |
| Exemplar interval | `chr20:10000000-10100000` |
| Sample metadata | `igsr_NA12878_metadata.tsv` |
| Data-use information | `data reuse policy.txt` |
| Retrieval date | September 1, 2026 |
| Integrity | SHA-256 values recorded with the validation outputs |
| Validation software | `samtools` 1.24 |
| Modifications | The regional CRAM and CRAI are derived from the upstream CRAM; the header is an extracted metadata artifact |

## Repository Contents

| File | Description |
|---|---|
| `NA12878.hg38.header.sam` | Header extracted from the complete upstream CRAM, including reference-sequence, read-group, and processing-program records |
| `NA12878.hg38.cram.crai` | Index distributed with the complete upstream CRAM |
| `NA12878.ONT.hg38.chr20_10000000-10100000.cram` | Compact regional alignment exemplar derived from the upstream CRAM |
| `NA12878.ONT.hg38.chr20_10000000-10100000.cram.crai` | CRAI index generated for the regional exemplar |
| `igsr_NA12878_metadata.tsv` | Sample and data-collection metadata obtained from IGSR |
| `data reuse policy.txt` | Data-reuse information associated with the IGSR collection |

The upstream CRAI applies to the complete `NA12878.hg38.cram` file and is not the index for the regional exemplar. The regional CRAM must be used with its corresponding regional CRAI.

## Application to the GIST Recommendations

The example implements several recommendations:

- **Stable sample identification:** The CRAM read-group records identify the sample as NA12878, while the accompanying IGSR metadata connects the sample to Biosample `SAME123392` and the relevant 1000 Genomes data collection.

- **Sequencing-assay documentation:** The `@RG` records identify Oxford Nanopore Technologies as the sequencing platform through `PL:ONT`. They also record the sample, library, platform unit, and distinct read-group identifiers associated with the sequencing runs.

- **Reference-genome documentation:** The CRAM header records GRCh38 reference-sequence names, lengths, and MD5 sequence checksums in its `@SQ` records. These identifiers make the expected reference sequences explicit and support reference verification when decoding the CRAM.

- **Processing provenance:** The `@PG` records identify the software, versions, and command-line parameters used during alignment, sorting, CRAM generation, and merging. The header documents the use of minimap2 `2.26-r1175` and samtools `1.16.1` in the upstream workflow.

- **Workflow relationships:** The `PP` fields in the `@PG` records connect successive processing steps, preserving relationships between alignment, sorting, and merging operations.

- **Standardized alignment representation:** Reads are represented using the community-standard CRAM format, which retains alignment coordinates, mapping qualities, CIGAR strings, flags, read-group assignments, and other alignment-level annotations in a compressed representation.

- **Defined analysis scope:** The filename and documentation identify the regional exemplar as containing alignments overlapping `chr20:10000000-10100000`. This distinguishes the compact repository example from the complete upstream whole-genome alignment.

- **Machine-readable indexing:** The corresponding CRAI permits indexed retrieval of alignments by genomic interval without sequentially reading the complete regional CRAM.

- **File provenance and integrity:** The provenance table records the upstream distributor, sample identifier, reference assembly, source file, derived interval, retrieval date, software versions, and local checksums.

- **Quality-control documentation:** Reproducible `samtools` outputs document file readability, alignment counts, mapping status, reference-sequence composition, regional coverage, mean depth, and mapping-quality summaries.

- **Data-use documentation:** The accompanying reuse-policy file records the terms associated with reuse of the upstream public dataset.

- **Transparent derivation:** The regional CRAM is explicitly identified as a derived subset rather than an independently generated alignment. Its source dataset, interval, index, software version, and validation results are documented so that users can understand and reproduce the transformation.

## Header Provenance

The upstream header contains two read groups for NA12878:

- Sample: `NA12878`
- Library: `NA12878`
- Platform: `ONT`
- Platform unit: `PAI05620`
- Read-group identifiers:
  - `NA12878_PAI05620_046aeac5`
  - `NA12878_PAI05620_899aff71`

The processing records document:

1. Alignment of Oxford Nanopore reads to GRCh38 using minimap2 `2.26-r1175`.
2. Coordinate sorting and CRAM encoding using samtools `1.16.1`.
3. Merging of the two read-group-specific CRAM files into `NA12878.hg38.cram`.

These header records provide an example of embedding processing provenance directly within an alignment file. However, they do not replace a complete external workflow record containing container identifiers, workflow definitions, execution environment, reference-accession information, and independently preserved input checksums.

## Validation Summary

The regional exemplar passed `samtools quickcheck` and contains:

| Metric | Result |
|---|---:|
| Total alignment records | 156 |
| Primary alignments | 136 |
| Secondary alignments | 1 |
| Supplementary alignments | 19 |
| Mapped records | 156 (100%) |
| Duplicate records | 0 |
| Records reported for chr20 by `idxstats` | 156 |
| Reads overlapping the validation interval | 155 |
| Covered bases in the interval | 99,993 |
| Interval coverage | 99.992% |
| Mean depth | 12.834 |
| Mean mapping quality | 59.5 |

The difference between the 156 records reported by `idxstats` and the 155 reads reported for the selected interval reflects differences in how the commands summarize indexed alignment records and interval overlap. These values should therefore be interpreted according to the behavior of the individual `samtools` commands rather than treated as contradictory counts.

## Scope and Limitations

This package is intended as a compact implementation example, not as a replacement for the complete NA12878 alignment dataset. It contains reads from only one genomic interval and therefore must not be used to estimate genome-wide sequencing quality, coverage, or variant-detection performance.

CRAM decoding may require access to the exact reference sequences identified by the `M5` checksums in the `@SQ` records. The original header contains a producer-local `UR` path, such as `/scratch/rausch/remap2/hg38.fa`; this path is not expected to resolve for external users. Consumers should obtain the matching GRCh38 reference sequences and verify their sequence digests rather than relying on the original filesystem path.