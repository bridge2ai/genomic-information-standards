# Schemas

This directory contains the machine-readable schemas used to validate metadata prepared according to the recommendations in the manuscript.

## Available schemas

- [`genomic_metadata_package_v0.1.0.json`](genomic_metadata_package_v0.1.0.json) — a draft 2020-12 JSON Schema for the example metadata packages under [`../examples/`](../examples/). It constrains the core, stable fields (package identity, study assay CURIE, sample specimen/analyte terms, the Refget seqcol digest, and the variant call-set counts) and is exercised by the `validate-metadata` GitHub Action, which also checks YAML/JSON twin equality and per-package arithmetic. The template is intentionally not valid against it (its `<placeholder>` values are strings where integers are required).
- [`seqcol/`](seqcol/) — the GA4GH Refget Sequence Collections v1.0.0 schemas (minimal, extended, and reference-based), mirrored from the [ga4gh/refget](https://github.com/ga4gh/refget) specification repository. These describe the sequence-collection digests that the metadata packages use to identify a reference assembly; see [`../identifiers/refget-seqcol.md`](../identifiers/refget-seqcol.md).

## Validating your own metadata

The checks applied in continuous integration are defined in [`../.github/workflows/validate-metadata.yml`](../.github/workflows/validate-metadata.yml) and run on every pull request and push. To validate a package locally:

```bash
pip install pyyaml jsonschema
python3 -c "
import json, sys, yaml
from jsonschema import Draft202012Validator
schema = json.load(open('schemas/genomic_metadata_package_v0.1.0.json'))
data = yaml.safe_load(open(sys.argv[1]))
errors = sorted(Draft202012Validator(schema).iter_errors(data), key=lambda e: list(e.path))
[print(list(e.path), e.message) for e in errors] or print('valid')
" examples/whole_exome_sequencing/wes_example.metadata.yaml
```

## Scope and continued development

The package schema is a draft at version 0.1.0. It constrains a core subset of the recommended metadata rather than the full field set, and packages may carry additional fields. We will extend its coverage as the worked examples and community best practices develop, and may add other representations, such as LinkML, where they improve interoperability.
