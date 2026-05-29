# Round 1 Dev Gold Acceptance Report

Benchmark version proposed for freeze: `round1_dev_v0.1`

## Acceptance Summary

### LS-DEV-01

- `human_review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `source_packet_id`: `packet_ls_dev_transformer_efficiency`
- `packet_manifest`: `benchmarks/source_packets/dev/LS-DEV-01/packet_manifest.yaml`
- `model_input_sha256`: `c13078138079e23f025595895c33bd2b5bf482babe6a6cbbde7c871beb05cd77`
- Accepted human-review changes: FlashAttention exact-core/block-sparse-extension distinction; LoRA boundary-paper treatment; graded outside-corpus policy.

### SPR-DEV-01

- `human_review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `source_packet_id`: `packet_spr_dev_lora`
- `packet_manifest`: `benchmarks/source_packets/dev/SPR-DEV-01/packet_manifest.yaml`
- `model_input_sha256`: `88c35c6bab01d76400e18045edf4ced0c215804570ff0df865e0b7d75f774732`
- Accepted human-review changes: LoRA arXiv v2 check; separated efficiency dimensions; bounded low-intrinsic-rank claim; matrix/rank ablation entry; graded outside-corpus policy.

### MC-DEV-01

- `human_review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `source_packet_id`: `packet_mc_dev_dpo_ppo_rlhf`
- `packet_manifest`: `benchmarks/source_packets/dev/MC-DEV-01/packet_manifest.yaml`
- `model_input_sha256`: `811f34eb8d3f3f51dfabb99c16bb65c6ade364c2b0fd626eb6b346a76460f5be`
- Accepted human-review changes: DPO implicit-reward nuance; direct setup-specific DPO/PPO comparisons; no universal DPO-over-RLHF claim; graded outside-corpus policy.

### ERA-DEV-01

- `human_review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `source_packet_id`: `packet_era_dev_agent_eval`
- `packet_manifest`: `benchmarks/source_packets/dev/ERA-DEV-01/packet_manifest.yaml`
- `model_input_sha256`: `864038d23703d73d6d0b834b4670fc44c2a06edb3633df3e2b4d777e3994addb`
- Accepted human-review changes: Pinned AgentBench ICLR 2024 / arXiv v3 29-model check; heterogeneous metrics and weighted aggregation; observed-failure-category item; version-sensitivity rule.

### RL-DEV-01

- `human_review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `source_packet_id`: `packet_rl_dev_offline_rl_protocol`
- `packet_manifest`: `benchmarks/source_packets/dev/RL-DEV-01/packet_manifest.yaml`
- `model_input_sha256`: `042acef2f135d640c4fc62f0fd0add4dc8452bf50dd6f37fb6857306a4994d12`
- Accepted human-review changes: D4RL arXiv v4 and CQL arXiv v3 checks; offline-training versus simulator-evaluation distinction; corrected CQL table roles; protocol-audit section; graded outside-corpus policy.

### PS-DEV-01

- `human_review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `source_packet_id`: `packet_ps_dev_representation_probing`
- `packet_manifest`: `benchmarks/source_packets/dev/PS-DEV-01/packet_manifest.yaml`
- `model_input_sha256`: `4cd8323980d2bdf31ddceeaddad3f8dc007fb7c048564ac59d6e780471cfa45c`
- Accepted human-review changes: Probing-versus-causal-use distinction; proposal-quality section; BERTology and Structural Probe attribution; local seed as context-only user motivation; graded outside-corpus policy.

## Version Checks

- `SPR-DEV-01`: LoRA local PDF first page reports `arXiv:2106.09685v2 [cs.CL] 16 Oct 2021` and `Version 2`.
- `RL-DEV-01`: D4RL local PDF first page reports `arXiv:2004.07219v4 [cs.LG] 6 Feb 2021`.
- `RL-DEV-01`: CQL local PDF first page reports `arXiv:2006.04779v3 [cs.LG] 19 Aug 2020`.
- `ERA-DEV-01`: AgentBench local PDF first page reports ICLR 2024, `arXiv:2308.03688v3 [cs.AI] 4 Oct 2025`, and 29 API-based/OSS LLMs.

## Decision

All six development gold annotations pass acceptance for Round 1 dev calibration and may be frozen as `round1_dev_v0.1`.

No skill variants were implemented during this acceptance step.
