# FASTA Example: GRCh38 Regional Reference Sequence

This example is derived from the GRCh38 primary-assembly genome FASTA distributed with GENCODE Human Release 49. To provide a compact reference-sequence example suitable for inclusion in this repository, the interval `chr20:10000000-10100000` was extracted using `samtools faidx`.

The complete upstream genome FASTA is not committed because of its size. This repository instead includes the extracted sequence, its FASTA index, a sequence dictionary, validation results, provenance information, and commands for obtaining the authoritative upstream resource.

# Metrics

The regional FASTA was inspected using `samtools faidx` and standard sequence-summary commands. The validation confirms that the derived sequence has the expected length, can be retrieved through its FASTA index, and is accompanied by the files needed to document its identity and support downstream reuse.

| Validation metric | Result |
|---|---:|
| Source reference | GENCODE Human Release 49 GRCh38 primary assembly |
| Source sequence | `chr20` |
| Source chr20 length | 64,444,167 bp |
| Extracted interval | `chr20:10000000-10100000` |
| Coordinate convention | 1-based, end-inclusive |
| Expected sequence length | 100,001 bp |
| Observed sequence length | 100,001 bp |
| GC bases | Record from `validation/sequence-summary.tsv` |
| Ambiguous (`N`) bases | Record from `validation/sequence-summary.tsv` |
| GC percentage excluding `N` bases | Record from `validation/sequence-summary.tsv` |
| FASTA index generation | Passed |
| Indexed sequence retrieval | Passed |
| Sequence dictionary generation | Passed |
| File-integrity checksums | Recorded in `validation/sha256sums.txt` |
| Validation software | Recorded in `validation/samtools-version.txt` |

The observed sequence length matches the expected length of 100,001 bp. This result reflects the 1-based, end-inclusive coordinate convention used by `samtools faidx`.

The GC-content and ambiguous-base measurements describe only the extracted regional sequence and should not be interpreted as chromosome-wide or genome-wide reference statistics. Similarly, successful indexed retrieval confirms that the regional FASTA and its `.fai` file are internally compatible, but it does not independently establish the identity of the complete upstream genome assembly.

The regional FASTA, `.fai` index, and sequence dictionary are derived artifacts. Their upstream source, extraction interval, generating software, and checksums are documented to preserve the relationship between the compact exemplar and the complete GENCODE reference.



# Application to the GIST Recommendations

This example implements several recommendations:
- **Reference-genome identification**: The example identifies the reference as the GRCh38 primary assembly distributed with GENCODE Human Release 49.
- **Reference source and version documentation**: The provenance record identifies GENCODE as the distributor, Human Release 49 as the source release, and GRCh38 as the primary genome assembly. Additionally, the complete upstream download URL and retrieval date provide a traceable pointer to the source material.
- **Reference file integrity**: SHA-256 checksums are provided for regional FASTA, FASTA index, and sequence dictionary.
- **Sequence-level identity**: The example demonstrates that an assembly name alone is not sufficient to establish reference identity.
- **Reference bundle components**: The FASTA is accompanied by a *.fai* index and sequence dictionary.
- **Machine-readable indexing**: The *.fai* file records the sequence name, sequence length, file offset, bases per line, and bytes per line.
- **Defined analysis scope**: The filename, FASTA header, provenance table, and validation materials identify the example.
- **Quality-control documentation**: Reproducible validation outputs record sequence length, GC content, ambiguous-base count, index contents, sequence-retrieval success, software version, and checksums.
