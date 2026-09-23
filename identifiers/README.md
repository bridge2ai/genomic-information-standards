# Identifiers

This directory contains guidance for the use of persistent identifiers throughout genomic metadata.

## Available guidance

- [`refget-seqcol.md`](refget-seqcol.md) — how GA4GH Refget Sequences and Refget Sequence Collections give reference sequences content-derived, checksum-based identifiers, why that resolves the reference-genome ambiguity that free-text assembly labels leave open, and how the sequence-collection comparison function can diagnose exactly how two references differ. The corresponding JSON Schemas are mirrored in [`../schemas/seqcol/`](../schemas/seqcol/).

## Identifier systems used elsewhere in this repository

The packages under [`../examples/`](../examples/) and the template in [`../templates/`](../templates/) also carry de-identified subject and sample identifiers, BioSample and BioProject accessions, a GA4GH VRS identifier for each represented variant, ORCID identifiers for contributors, HGNC gene identifiers, and a content checksum for every registered file. The file-level records under [`../examples/example_files/`](../examples/example_files/) carry DOIs for their upstream source datasets. [`../vocabularies/resources.md`](../vocabularies/resources.md) links to each of these systems.

## Continued development

We will add guidance for these other identifier systems, comparable to the Refget document above, as community best practices evolve.
