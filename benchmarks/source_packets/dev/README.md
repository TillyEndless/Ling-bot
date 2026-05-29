# Development Source Packets

This directory is reserved for source packets for the six development tasks.

Round 1 uses only fixed source packets. No open retrieval, external citation APIs, PDF parsers, or dynamic paper lookup should be used at runtime.

## Required Status Before Dev Runs

Each dev task must have:

- A packet directory named after the `packet_id`.
- The required paper PDFs, markdown files, or excerpt files.
- A `packet_manifest.yaml` with source provenance and checksums.
- Stable file names.
- License/access notes.
- Page, section, table, figure, or appendix references needed by gold annotations.

## Suggested Layout

```text
benchmarks/source_packets/dev/
  source_acquisition_manifest.yaml
  LS-DEV-01/
    packet_manifest.yaml
    model_input_packet.md
    canonical_sources/
  SPR-DEV-01/
    packet_manifest.yaml
    model_input_packet.md
    canonical_sources/
```

Do not add generated summaries to source packets unless a task explicitly provides a prepared excerpt as input. Gold annotations belong under `benchmarks/gold_annotations/dev/`.
