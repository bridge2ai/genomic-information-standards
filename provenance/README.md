# Provenance

This directory holds an example workflow-run provenance record,
[`wgs_align_call_run.provenance.yaml`](wgs_align_call_run.provenance.yaml)
(JSON twin: `wgs_align_call_run.provenance.json`).

It records a WGS alignment + variant-calling run structured after the **W3C PROV**
activity/entity model: each activity lists the input entities it `used` and the
output entities it `generated`, every entity carrying its identity and content
checksum as separate fields and every tool a container digest; the reference set
is identified by a **GA4GH Refget Sequence Collections** digest. The steps chain
fastq → cram → gVCF, and the final generated entity is the `variant_callset` of the
B1-0001 example package, so the provenance chain closes onto
[`../examples/whole_genome_sequencing/`](../examples/whole_genome_sequencing/). Each
real sample carries its own record of the same shape (the example packages point at
this one only for B1-0001, and at a placeholder otherwise). It is a plain YAML/JSON
record, not a serialized PROV-O graph and not an RO-Crate.

> [!IMPORTANT]
> **Illustrative / synthetic.** All subject identifiers, values, checksums, container
> digests, and accessions are placeholders and site identities are generalized; no values
> derive from human subjects. Deliberate exceptions, marked inline: the GA4GH Refget seqcol
> digest and the ontology CURIEs (and, in the panel example, the HGNC gene IDs and the
> target-regions BED with its real sha256).
