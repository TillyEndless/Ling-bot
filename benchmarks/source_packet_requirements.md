# Source Packet Requirements

Source packets provide the material used by `closed_source` tasks. They must be collected and frozen before a task is executed formally.

Round 1 uses fixed source packets only. Open retrieval is not part of Round 1.

## Packet Rules

Each packet must include:

- A stable packet ID matching task `provided_materials`.
- Source files in PDF, markdown, text, or structured excerpt form.
- Bibliographic metadata where applicable.
- Source provenance: URL, DOI, arXiv ID, commit SHA, or dataset/version identifier.
- Retrieval date.
- License or usage notes when known.
- Page, section, table, figure, or line references needed for gold annotations.
- A `packet_manifest.yaml` listing all files and checksums.

Do not summarize or rewrite source material inside the packet unless the task explicitly provides an excerpt. Gold annotations must be stored separately under `benchmarks/gold_annotations/`.

## Future Retrieval Task Inputs

Retrieval tasks are deferred to a future tool-enabled round. When they are introduced, they will require:

- A fixed retrieval protocol.
- Allowed source types.
- Search budget.
- Date cutoff if relevant.
- A canonical-paper checklist for scoring, stored only in gold annotations.

## Round 1 Closed-Source Task Inputs

Closed-source tasks must not be run until the required source packets are present. If the packet is missing, the task is marked `source_material_required`.

## Suggested Packet Layout

```text
benchmarks/source_packets/
  <packet_id>/
    packet_manifest.yaml
    sources/
      ...
    notes/
      collection_notes.md
```

## Current Packet Status

No source packets have been collected in this stage. All closed-source tasks are therefore definitions only until their packets are added.
