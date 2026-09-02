# BAM Validation and Inspection

This document records the validation results and inspection commands used for the regional BAM exemplar:

`HG002.GRCh38.2x250.chr20_10000000-10100000.bam`

The file was derived from the NIST Genome in a Bottle HG002 Illumina 2 x 250 bp alignment against GRCh38. The selected interval was `chr20:10000000-10100000`.

## Summary

| Metric | Result |
|---|---:|
| Structural validation with `samtools quickcheck` | Passed; no errors reported |
| Reference containing selected records | `chr20` |
| chr20 reference length | 64,444,167 bp |
| Mapped records reported for chr20 by `samtools idxstats` | 28,595 |
| Unmapped records associated with chr20 by `samtools idxstats` | 206 |
| Bases covered on chr20 | 100,492 |
| Percentage of chr20 covered | 0.155937% |
| Mean depth across chr20 | 0.109747 |
| Mean base quality | 37.1 |
| Mean mapping quality | 70 |

The coverage statistics above were calculated across the complete chr20 reference sequence because `samtools coverage` was run without an explicit region. The low chromosome-wide coverage percentage and mean depth are therefore expected for a BAM containing reads selected from a 100-kb interval. These values must not be interpreted as genome-wide or chromosome-wide performance metrics for the complete upstream sequencing dataset.

The mapped and unmapped columns produced by `samtools idxstats` describe records associated with each reference sequence in the BAM index. They are not equivalent to the more detailed alignment categories reported by `samtools flagstat`.

## File Variables

The following variables can be used to reproduce the commands in this document:

```bash
UPSTREAM_BAM="HG002.GRCh38.2x250.bam"
REGIONAL_BAM="HG002.GRCh38.2x250.chr20_10000000-10100000.bam"
REGION="chr20:10000000-10100000"
```

## Software Version

Record the exact software version used for validation:

```bash
samtools --version
```

To save the result:

```bash
samtools --version > samtools-version.txt
```

## File and Index Integrity

Confirm that the BAM and BAI files are present and nonempty:

```bash
ls -lh "$REGIONAL_BAM" "${REGIONAL_BAM}.bai"

test -s "$REGIONAL_BAM" &&
  echo "PASS: BAM is nonempty"

test -s "${REGIONAL_BAM}.bai" &&
  echo "PASS: BAI is nonempty"
```

Perform a rapid structural check of the BAM and its terminating blocks:

```bash
samtools quickcheck -v "$REGIONAL_BAM"
```

`samtools quickcheck -v` produces no output when the checked file passes. Any reported filename or error should be investigated before the BAM is included in the repository.

Calculate SHA-256 checksums for the upstream and derived files:

```bash
shasum -a 256 \
  "$UPSTREAM_BAM" \
  "${UPSTREAM_BAM}.bai" \
  "$REGIONAL_BAM" \
  "${REGIONAL_BAM}.bai" \
  > sha256sums.txt
```

## Header Inspection

Extract the complete header from the upstream BAM:

```bash
samtools view -H "$UPSTREAM_BAM" > HG002.GRCh38.2x250.header.sam
```

Inspect the read-group records, which may contain sample, library, sequencing-platform, and platform-unit information:

```bash
grep '^@RG' HG002.GRCh38.2x250.header.sam
```

Inspect the processing-program records, which may contain software names, versions, command lines, and relationships between processing steps:

```bash
grep '^@PG' HG002.GRCh38.2x250.header.sam
```

Inspect the first three reference-sequence records:

```bash
grep '^@SQ' HG002.GRCh38.2x250.header.sam | head -3
```

Confirm that the regional BAM retained the upstream metadata-bearing header records:

```bash
samtools view -H "$REGIONAL_BAM" | grep '^@RG'
samtools view -H "$REGIONAL_BAM" | grep '^@PG'
samtools view -H "$REGIONAL_BAM" | grep '^@SQ' | head -3
```

## Alignment Inspection

Display the first five alignment records in SAM format:

```bash
samtools view "$REGIONAL_BAM" | head -5
```

Display selected fields in a more compact form:

```bash
samtools view "$REGIONAL_BAM" |
  awk 'BEGIN { OFS="\t"; print "QNAME","FLAG","RNAME","POS","MAPQ","CIGAR" }
       NR <= 5 { print $1,$2,$3,$4,$5,$6 }'
```

Inspect alignments retrieved through the regional index:

```bash
samtools view "$REGIONAL_BAM" "$REGION" | head -5
```

Count records returned for the selected interval:

```bash
samtools view -c "$REGIONAL_BAM" "$REGION"
```

## Alignment Counts

Generate detailed alignment-category counts:

```bash
samtools flagstat "$REGIONAL_BAM"
```

Save the output:

```bash
samtools flagstat "$REGIONAL_BAM" > regional-flagstat.txt
```

Generate counts by reference sequence:

```bash
samtools idxstats "$REGIONAL_BAM"
```

Save the output:

```bash
samtools idxstats "$REGIONAL_BAM" > regional-idxstats.tsv
```

For this exemplar, `samtools idxstats` reported 28,595 mapped records and 206 unmapped records associated with chr20. Other reference sequences had zero records.

## Coverage Inspection

Summarize the regional BAM against every reference sequence represented in its header:

```bash
samtools coverage "$REGIONAL_BAM"
```

Save the output:

```bash
samtools coverage "$REGIONAL_BAM" > chromosome-wide-coverage.tsv
```

This command produced the chromosome-wide statistics shown in the validation summary. Because the denominator is the complete length of chr20, these results characterize the distribution of the regional subset across chr20 rather than coverage within the selected interval alone.

Calculate coverage specifically within the extraction interval:

```bash
samtools coverage \
  --region "$REGION" \
  "$REGIONAL_BAM"
```

Save the interval-specific result:

```bash
samtools coverage \
  --region "$REGION" \
  "$REGIONAL_BAM" \
  > selected-interval-coverage.tsv
```

The interval-specific output should be used when describing coverage within the 100-kb exemplar region.

## Optional Additional Statistics

Generate more detailed alignment statistics:

```bash
samtools stats "$REGIONAL_BAM" > regional-samtools-stats.txt
```

Extract the principal summary-number records:

```bash
grep '^SN' regional-samtools-stats.txt > regional-summary-numbers.tsv
```

Useful summary fields can include total sequences, mapped reads, error rate, average read length, insert size, and properly paired reads. These values should be interpreted as properties of the regional subset and not as genome-wide quality metrics for the complete HG002 sequencing experiment.
