# Gold-To-Packet Coverage Audit For Round 1 Dev v0.2

This audit compares the approved dev gold annotations against the exact `round1_dev_v0.1` `model_input_packet.md` files supplied to `B0_base_agent`. It does not treat B0 omissions as packet defects by themselves. A packet change is recommended only when the gold-relevant source evidence is absent or materially incomplete in the model input.

## Summary

| Task | v0.1 Coverage Judgment | v0.2 Action |
|---|---|---|
| `LS-DEV-01` | Mostly supported; FlashAttention block-sparse extension absent. | Expand packet minimally. |
| `SPR-DEV-01` | Core LoRA method supported; matrix/rank analyses and several efficiency details absent or too thin. | Expand packet. |
| `MC-DEV-01` | Central anchors supported at task-appropriate granularity. | No packet change. |
| `ERA-DEV-01` | Generic audit support present; pinned version, heterogeneous metrics, weighting, and failure categories too thin. | Expand packet. |
| `RL-DEV-01` | Generic offline-RL audit support present; normalized-score, simulator-evaluation, CQL table-role, and seed details too thin. | Expand packet. |
| `PS-DEV-01` | Central proposal and probing-boundary anchors supported. | No packet change. |

## Task Findings

### LS-DEV-01

`LS1`, `LS2`, `LS3`, `LS5`, the fixed-corpus policy, comparison-fairness rule, and inference-boundary rules are sufficiently supported in the v0.1 packet. `LS4` is only partially supported: the packet says FlashAttention is exact IO-aware attention and not approximate/sparse attention, but it omits the paper's block-sparse approximate extension. The fair v0.2 fix is to add source-facing evidence that separates the exact core algorithm from the block-sparse extension.

### SPR-DEV-01

The v0.1 packet supports LoRA's core frozen-weight/low-rank-update method, broad evaluated model families, and high-level efficiency dimensions. It does not sufficiently expose Section 4.2's general dense-layer applicability, the matrix-selection and rank analyses in Tables 5-6, the explicit caveat that small rank is not universal, GPT-2/GPT-3 table scope, or the training-throughput/no-latency mechanics. These are central approved anchors, so the packet should be expanded rather than the gold downgraded.

### MC-DEV-01

The packet contains enough evidence to support the approved DPO/RLHF/PPO anchors: DPO direct preference optimization and implicit reward framing, Bradley-Terry/KL assumptions, InstructGPT's SFT/RM/PPO pipeline, PPO as a general RL algorithm, and setup-specific DPO/PPO comparisons. The task requires method-comparison reasoning, but the evidence is present. No packet change is recommended.

### ERA-DEV-01

The v0.1 packet supports broad AgentBench audit reasoning but is too compressed for the approved gold. It mentions eight environments and 29 models but does not expose the pinned ICLR 2024 / arXiv v3 version marker, the three grounding categories, the heterogeneous metrics, the reciprocal-average weighting procedure, or execution-outcome categories and their aggregate interpretation. These are central to a fair benchmark-validity audit, so v0.2 should add source-facing evidence.

### RL-DEV-01

The v0.1 packet supports generic offline-RL rigor: fixed datasets, behavior-policy assumptions, distribution shift, no online-performance overclaiming, and metric separation. It is too thin for the approved table/protocol anchors: D4RL's offline-training versus simulator-evaluation convention, normalized-score definition, CQL action-distribution/lower-bound framing, CQL Tables 1-4 roles, four-seed reporting, and the distinction between Atari experiments and D4RL performance evidence. These are central, so v0.2 should expand packet evidence.

### PS-DEV-01

The packet supports the proposal task. It includes BERT Rediscovers edge probing and causal-use warning, BERTology as methodological survey context, Structural Probe's linear geometric hypothesis and baselines, the local seed idea as motivation, and requirements for falsification, controls, and alternative explanations. No packet change is recommended. The local seed remains context-only, not authoritative literature evidence.

## Gold Revision Judgment

No approved gold item needs revision at this stage. The defects are packet-evidence coverage issues for `LS-DEV-01`, `SPR-DEV-01`, `ERA-DEV-01`, and `RL-DEV-01`, not gold-design defects. `MC-DEV-01` and `PS-DEV-01` require no change.

The machine-readable audit is in `reports/round1_dev_v0_2/gold_to_packet_coverage_audit.yaml`.
