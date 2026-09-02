This example is dervied from the NIST Genome in a Bottle HG002 Challenging Medically Relevant Genes benchmark set and contains curated small variants represented in VCF format together with the corresponding benchmark-region BED file.

**Provenance Table**
| Field                 | Value                                                             |
| --------------------- | ----------------------------------------------------------------- |
| Dataset               | HG002 GRCh38 CMRG small-variant benchmark                         |
| Sample                | HG002 / NA24385                                                   |
| Organism              | *Homo sapiens*                                                    |
| Reference assembly    | GRCh38                                                            |
| Benchmark release     | CMRG v1.00                                                        |
| Persistent identifier | [NIST DOI 10.18434/mds2-2475](https://doi.org/10.18434/mds2-2475) |
| Upstream distributor  | NIST Genome in a Bottle / NCBI                                    |
| Variant file          | `HG002_GRCh38_CMRG_smallvar_v1.00.vcf.gz`                         |
| Index                 | `HG002_GRCh38_CMRG_smallvar_v1.00.vcf.gz.tbi`                     |
| Benchmark regions     | `HG002_GRCh38_CMRG_smallvar_v1.00.bed`                            |
| Retrieval date        | 9/1/2026                                                          |
| Integrity             | SHA-256 values in `validation/sha256sums.txt`                     |
| Validation software   | Recorded in `validation/bcftools-version.txt`                     |
| Modifications         | None to upstream files; derived artifacts documented separately   |


The example implements several recommendations:
- **Stable sample identification**: The VCF identifies the Genome in a Bottle HG002/NA24385 reference sample
- **Reference-genome documentation**: The VCF header records the reference assembly and contig definitions used to represent the variants. It also retains these header records so that genomic coordinates can be interpreted against the intended GRCh38 reference.
- **Standardized variant representation**: Variants are distributed in the community-standard VCF format with chromosome, position, ref allele, alt allele, filter, INFO, and genotype fields.
- **Defined analysis scope**: The accompanying BED file identifies the genomic regions over which the CMRG benchmark is intended to be interpreted.
- **File provenance and integrity**: The provenance table records the upstream NIST dataset, release version, persistent identifiers, download location, retrieval date, and local SHA-256 checksums.
- **Quality-control documentation**: Reproducible *bcftools* validation outputs document file readability, record counts, contig composition, variant classes, filter results, and sample-level statistics
