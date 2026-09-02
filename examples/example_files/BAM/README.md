# BAM Exemplar: HG002 Illumina Alignment

This example is derived from the NIST Genome in a Bottle (GIAB) Illumina sequencing data for the human reference sample HG002/NA24385. The upstream BAM contains paired-end Illumina reads aligned to GRCh38 using Novoalign.

To provide a compact example suitable for inspection and reuse, alignments overlapping `chr20:10000000-10100000` were extracted into a regional BAM file with a corresponding BAI index. The complete upstream BAM and its original index are also retained in this example.

The complete upstream BAM is not committed to this repository because it exceeds GitHub's file-size limit. It remains available through the authoritative NCBI-hosted Genome in a Bottle collection. This repository instead contains a compact regional BAM, its corresponding BAI index, and validation materials derived from the upstream alignment.

## Obtaining the Complete Upstream Alignment

The complete HG002 alignment and corresponding BAI index are hosted by NCBI Genome in a Bottle and are not duplicated in this repository.

```bash
SOURCE_BAM_URL="https://ftp-trace.ncbi.nlm.nih.gov/ReferenceSamples/giab/data/AshkenazimTrio/HG002_NA24385_son/NIST_Illumina_2x250bps/novoalign_bams/HG002.GRCh38.2x250.bam"

curl \
  --location \
  --fail \
  --retry 5 \
  --retry-delay 3 \
  --continue-at - \
  --output "HG002.GRCh38.2x250.bam" \
  "$SOURCE_BAM_URL"

curl \
  --location \
  --fail \
  --retry 5 \
  --retry-delay 3 \
  --continue-at - \
  --output "HG002.GRCh38.2x250.bam.bai" \
  "${SOURCE_BAM_URL}.bai"

## Provenance Table

| Field | Value |
|---|---|
| Dataset | NIST Genome in a Bottle HG002 Illumina 2 × 250 bp sequencing |
| Sample | HG002 / NA24385 |
| Organism | *Homo sapiens* |
| Sequencing technology | Illumina |
| Sequencing layout | Paired-end, 2 × 250 bp |
| Reference assembly | GRCh38 |
| Alignment software | Novoalign |
| Upstream distributor | NIST Genome in a Bottle / NCBI |
| Upstream BAM | `HG002.GRCh38.2x250.bam` - externally hosted; not committed |
| Upstream index | `HG002.GRCh38.2x250.bam.bai` |
| Regional exemplar | `HG002.GRCh38.2x250.chr20_10000000-10100000.bam` |
| Regional index | `HG002.GRCh38.2x250.chr20_10000000-10100000.bam.bai` |
| Exemplar interval | `chr20:10000000-10100000` |
| Retrieval date | September 1, 2026 |
| Integrity | SHA-256 values recorded with the validation outputs |
| Validation software | Record the samtools version used for validation |
| Modifications | Regional BAM and BAI derived from the unmodified upstream alignment |

## Upstream Source

The complete alignment was obtained from the NCBI-hosted Genome in a Bottle collection:

`https://ftp-trace.ncbi.nlm.nih.gov/ReferenceSamples/giab/data/AshkenazimTrio/HG002_NA24385_son/NIST_Illumina_2x250bps/novoalign_bams/HG002.GRCh38.2x250.bam`

The source path identifies the sample, sequencing assay, read configuration, reference assembly, and alignment workflow associated with the file.

## Repository Contents

| File | Description |
|---|---|
| `HG002.GRCh38.2x250.bam` | Complete upstream HG002 alignment against GRCh38 |
| `HG002.GRCh38.2x250.bam.bai` | BAI index corresponding to the complete upstream BAM |
| `HG002.GRCh38.2x250.chr20_10000000-10100000.bam` | Regional alignment exemplar containing records selected from the chr20 interval |
| `HG002.GRCh38.2x250.chr20_10000000-10100000.bam.bai` | BAI index corresponding to the regional exemplar |

The complete upstream BAM and BAI remain available through NCBI and can be obtained using the commands provided above.

## Application to the GIST Recommendations

The example implements several recommendations from *Bridge2AI Recommendations for AI-Ready Genomic Data*:

- **Stable sample identification:** The BAM represents Genome in a Bottle sample HG002, also identified as NA24385. These stable identifiers connect the alignment to an established human reference material and its associated public metadata.

- **Sequencing-assay documentation:** The source dataset records the use of paired-end Illumina sequencing with a read configuration of 2 × 250 bp. Relevant read-group records embedded in the BAM header should be retained when creating regional or otherwise derived examples.

- **Reference-genome documentation:** The BAM header records the reference-sequence names and lengths used for alignment. These records allow genomic coordinates to be interpreted against the intended GRCh38 reference assembly.

- **Processing provenance:** Program records in the BAM header can identify the alignment and processing software used to generate the file. The upstream directory and filename additionally document that the reads were aligned to GRCh38 using Novoalign.

- **Standardized alignment representation:** Reads are represented using the community-standard BAM format, which stores alignment coordinates, mapping qualities, CIGAR strings, flags, mate relationships, read-group assignments, and optional alignment annotations.

- **Defined analysis scope:** The regional filename and documentation identify `chr20:10000000-10100000` as the selection interval. This distinguishes the compact exemplar from the complete whole-genome alignment.

- **Machine-readable indexing:** The BAI files enable programmatic retrieval of alignments by genomic interval without sequentially reading the complete BAM.

- **File provenance and integrity:** The provenance table records the upstream distributor, source URL, sample, sequencing assay, reference assembly, source file, derivation interval, retrieval date, and local SHA-256 checksums.

- **Quality-control documentation:** Reproducible `samtools` outputs document file readability, reference-sequence composition, alignment counts, indexed retrieval, mapped and unmapped records, regional coverage, depth, base quality, and mapping quality.

- **Transparent derivation:** The regional BAM is explicitly identified as a subset derived from the complete upstream BAM. The source file, selected interval, generating software, commands, and validation outputs should be retained so the transformation can be independently reproduced.

## Regional Subset

The compact example was generated by selecting records overlapping:

```text
chr20:10000000-10100000