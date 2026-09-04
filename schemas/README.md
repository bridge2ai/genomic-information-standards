# Schemas

This directory is intended to contain machine-readable schema definitions describing the recommended metadata elements presented in the manuscript.

Future schema representations may include JSON Schema, LinkML, or other community-supported schema languages to facilitate automated validation and interoperability.

## Available schemas

- [`genomic_metadata_package_v0.1.0.json`](genomic_metadata_package_v0.1.0.json) — a draft 2020-12 JSON Schema for the example metadata packages under [`../examples/`](../examples/). It constrains the core, stable fields (package identity, study assay CURIE, sample specimen/analyte terms, the Refget seqcol digest, and the variant call-set counts) and is exercised by the `validate-metadata` GitHub Action, which also checks YAML/JSON twin equality and per-package arithmetic. The template is intentionally not valid against it (its `<placeholder>` values are strings where integers are required).
