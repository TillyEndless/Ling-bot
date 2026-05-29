# Round 1 Dev v0.2 Packet Revision Plan

This plan preserves `round1_dev_v0.1` as a benchmark-debugging run and creates draft v0.2 packets only for tasks where approved central gold anchors were not sufficiently represented in the B0-facing packet.

## Tasks Requiring Packet Expansion

### `LS-DEV-01`

Add raw source-facing evidence for:

- FlashAttention p. 1 Abstract: exact IO-aware attention and block-sparse extension are both mentioned.
- FlashAttention p. 4 Section 3: core algorithm computes exact attention while reducing HBM reads/writes.
- FlashAttention p. 7 Section 4.1/Table 1 and p. 8 Table 2: BERT-large and GPT-2 comparisons are setup-specific.

No gold changes proposed.

### `SPR-DEV-01`

Add raw source-facing evidence for:

- LoRA p. 4 Section 4.1 Equation 3: `W0` frozen, trainable `A` and `B`, update `Delta W = BA`.
- LoRA p. 4 Section 4.2: general dense-layer applicability and experimental focus on selected Transformer weights.
- LoRA p. 3 Table 1 and pp. 3-4 no-additional-inference-latency discussion.
- LoRA p. 4 pre-Section-5 training-speed claim.
- LoRA p. 6 Table 3 and p. 7 Table 4: GPT-2 and GPT-3 task settings.
- LoRA p. 9 Tables 5-6 and p. 10 footnote 6: matrix-choice/rank analyses are setting-specific and small rank is not universal.

No gold changes proposed.

### `ERA-DEV-01`

Add raw source-facing evidence for:

- AgentBench p. 1 first-page version marker and abstract: ICLR 2024 / arXiv v3, 8 environments, 29 API/OSS LLMs.
- AgentBench p. 2 Figure 2: eight environments and grounding categories.
- AgentBench p. 3 Table 1: evaluated model roster.
- AgentBench p. 6 Table 2: heterogeneous metrics and inverse-weight statistics.
- AgentBench p. 7 Section 4.1: overall-score resizing and reciprocal-average weighting.
- AgentBench p. 8 Table 4/Section 4.3: execution-outcome categories and aggregate outcome interpretation.
- AgentBench p. 6 Section 4.1: evaluation toolkit, task workers, Docker/worker isolation, and prompt setup at the level needed for audit.

No gold changes proposed.

### `RL-DEV-01`

Add raw source-facing evidence for:

- D4RL p. 1 Abstract and p. 2 Introduction: static offline datasets and benchmark evaluation protocol.
- D4RL p. 7: simulator-based evaluation protocol and normalized-score definition.
- D4RL Appendix Tables 1-3: task identities, normalized scores, raw returns, and seed reporting anchors.
- CQL pp. 1-4: action-distribution shift, conservative Q-functions, lower-bound objective, and CQL policy-learning objectives.
- CQL pp. 7-9 Tables 1, 2, 3, and 4: D4RL performance tables, Atari boundary, and lower-bound analysis.
- CQL Appendix p. 29: D4RL hyperparameters and four-seed reporting.

No gold changes proposed.

## Tasks Requiring No Change

### `MC-DEV-01`

The approved central anchors are already supported by the v0.1 packet:

- DPO direct preference optimization and implicit-reward framing.
- Bradley-Terry/KL assumptions.
- InstructGPT SFT/RM/PPO pipeline.
- PPO as algorithmic foundation rather than direct RLHF evidence.
- Setup-specific DPO/PPO comparisons and no universal ranking.

### `PS-DEV-01`

The approved central anchors are already supported by the v0.1 packet:

- BERT Rediscovers edge probing and causal-use warning.
- BERTology as survey/methodological context.
- Structural Probe's linear geometric hypothesis and baselines.
- Proposal-quality requirements for falsification, controls, and alternative explanations.
- Local seed idea as user-provided motivation only, not authoritative evidence.

## Gold Revision Plan

No gold revisions are proposed for v0.2. The accepted gold annotations remain valid. The v0.2 work is packet expansion only.

If human review rejects any added evidence as too leading, the fallback is to revise the packet wording, not to change gold eligibility automatically.
