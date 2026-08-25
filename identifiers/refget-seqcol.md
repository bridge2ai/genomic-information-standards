## Reference Sequence Identifiers: Refget Sequences and Sequence Collections

Reference genome ambiguity (which FASTA? which chromosome naming
convention? which patch level?) is a common source of irreproducibility
in genomic pipelines. GA4GH Refget addresses this by giving sequences
content-derived, checksum-based identifiers.

- **Refget Sequences** identifies an individual sequence by a digest
  computed over its content. Pipelines that operate on individual
  sequences rather than a full reference genome (e.g., aligning to a
  single chromosome or a custom contig) can use a Refget Sequences
  identifier directly to unambiguously record which sequence was used.

- **Refget Sequence Collections** extends this to an entire collection
  of sequences (e.g., a full reference genome assembly), producing a
  single digest that identifies the exact set of sequence names,
  lengths, and content, independent of file format or chromosome
  naming convention. The spec also defines a comparison function that,
  given two collections, reports which attributes (names, lengths,
  sequences) match, are swapped in order, or differ entirely, useful
  for diagnosing exactly how two reference genome builds differ rather
  than just confirming they're not identical.

**Why this matters for AI-ready genomic metadata:** recording a Refget
identifier alongside a dataset lets any downstream consumer verify,
without downloading the reference, whether two datasets used the
identical sequence(s), catching mismatches (e.g. GRCh38 vs. GRCh38 with
alt contigs) that free-text reference labels miss.

**References:**
- Refget Specifications (overview): https://ga4gh.github.io/refget/
- Refget Sequences protocol: https://ga4gh.github.io/refget/sequences/
- Refget Sequence Collections spec: https://ga4gh.github.io/refget/seqcols/
- Spec source / issue tracker: https://github.com/ga4gh/refget
