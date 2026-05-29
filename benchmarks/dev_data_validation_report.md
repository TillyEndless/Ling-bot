# Dev Data Validation Report

Date: 2026-05-29

## Summary

Consistency validation passed for the current Round 1 development data package.

- Six dev source-packet directories exist.
- Each dev source packet has `canonical_sources/`, `model_input_packet.md`, and `packet_manifest.yaml`.
- Every canonical source and model-input packet has a SHA-256 checksum in the task-level manifest.
- All task YAMLs use `evaluation_mode: closed_source`.
- The 12 non-dev comparison tasks are under `benchmarks/tasks/validation/` with `split: validation`.
- No implemented skill variant files exist under `variants/` beyond `variants/README.md`.
- All dev gold annotations are grounded drafts, marked `drafted_by_agent: true`, `human_review_status: pending`, and `eligible_for_scoring: false`.

## Acquired Dev Sources

### LS-DEV-01

Packet: `benchmarks/source_packets/dev/LS-DEV-01`

- `efficient_transformers_survey_arxiv_2009.06732.pdf`
- `linformer_arxiv_2006.04768.pdf`
- `longformer_arxiv_2004.05150.pdf`
- `flashattention_arxiv_2205.14135.pdf`
- `lora_arxiv_2106.09685.pdf`

### SPR-DEV-01

Packet: `benchmarks/source_packets/dev/SPR-DEV-01`

- `lora_arxiv_2106.09685.pdf`

### MC-DEV-01

Packet: `benchmarks/source_packets/dev/MC-DEV-01`

- `dpo_arxiv_2305.18290.pdf`
- `instructgpt_arxiv_2203.02155.pdf`
- `ppo_arxiv_1707.06347.pdf`

### ERA-DEV-01

Packet: `benchmarks/source_packets/dev/ERA-DEV-01`

- `agentbench_arxiv_2308.03688.pdf`

### RL-DEV-01

Packet: `benchmarks/source_packets/dev/RL-DEV-01`

- `d4rl_arxiv_2004.07219.pdf`
- `cql_arxiv_2006.04779.pdf`

### PS-DEV-01

Packet: `benchmarks/source_packets/dev/PS-DEV-01`

- `bert_rediscovers_arxiv_1905.05950.pdf`
- `bertology_arxiv_2002.12327.pdf`
- `structural_probe_acl_N19-1419.pdf`
- `local_seed_idea_representation_probing.md`

## Checksum Location

Task-level checksums are recorded in:

- `benchmarks/source_packets/dev/LS-DEV-01/packet_manifest.yaml`
- `benchmarks/source_packets/dev/SPR-DEV-01/packet_manifest.yaml`
- `benchmarks/source_packets/dev/MC-DEV-01/packet_manifest.yaml`
- `benchmarks/source_packets/dev/ERA-DEV-01/packet_manifest.yaml`
- `benchmarks/source_packets/dev/RL-DEV-01/packet_manifest.yaml`
- `benchmarks/source_packets/dev/PS-DEV-01/packet_manifest.yaml`

The acquisition manifest points to these task-level manifests for populated checksum values.

## Unresolved Ambiguities

- Exact page references in agent-drafted gold files require human verification against the PDFs.
- Some DOI or official-publication identifiers remain `unknown_pending_verification` in the acquisition manifest where the arXiv or ACL public source was used as the canonical source for this round.
- License/access notes record public access locations, but paper-level license terms were not fully audited beyond public availability.
- The controlled `model_input_packet.md` files are curated from source inspection and should be reviewed for whether they include enough material for fair B0-B3 comparison without becoming answer keys.
- Validation source packets and gold annotations are not materialized in this workspace and should be handled under `split_policy.md`.

## Readiness Blockers

Do not run `B0_base_agent` yet.

Remaining blocker:

- Human review must verify all six dev gold annotation files, resolve evidence-location uncertainty, and set each file to `eligible_for_scoring: true`.

After that blocker is cleared, the development split can be used for B0-B3 debugging and rubric calibration under `benchmarks/run_protocol.md`.
