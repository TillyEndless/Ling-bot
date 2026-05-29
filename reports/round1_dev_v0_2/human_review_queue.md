# Human Review Queue For Round 1 Dev v0.2 Draft Packets

Review scope: changed packet contents only. Gold annotations remain unchanged and approved unless you explicitly request a gold revision.

## `LS-DEV-01`

Changed packet:

- `benchmarks/source_packets/dev_v0_2/LS-DEV-01/model_input_packet.md`

Newly added evidence to verify:

- FlashAttention p. 1 Abstract: exact IO-aware attention and block-sparse extension are both present.
- FlashAttention p. 4 Section 3: core algorithm computes exact attention using IO-aware tiling and fewer HBM reads/writes.
- FlashAttention p. 7 Section 4.1/Table 1 and p. 8 Table 2: BERT-large and GPT-2 comparisons are setup-specific.

Gold status:

- Gold unchanged.
- Minimum human check: confirm the packet wording does not overstate the block-sparse extension or turn it into a hint beyond source-facing evidence.

## `SPR-DEV-01`

Changed packet:

- `benchmarks/source_packets/dev_v0_2/SPR-DEV-01/model_input_packet.md`

Newly added evidence to verify:

- LoRA p. 4 Section 4.1 Equation 3: frozen `W0`, trainable `A` and `B`, and `Delta W = BA`.
- LoRA p. 4 Section 4.2: general dense-layer applicability and selected Transformer-module experimental focus.
- LoRA p. 3 Table 1 and pp. 3-4: inference-latency comparison and merge-for-deployment mechanism.
- LoRA p. 4 paragraph before Section 5: GPT-3 training-speed comparison.
- LoRA p. 6 Table 3 and p. 7 Table 4: GPT-2 and GPT-3 empirical scope.
- LoRA p. 9 Tables 5-6 and p. 10 footnote 6: matrix-choice/rank analyses and caveat that small rank is not universal.

Gold status:

- Gold unchanged.
- Minimum human check: confirm the packet gives enough table/section context without embedding the scoring expectation that Tables 5-6 are mandatory.

## `ERA-DEV-01`

Changed packet:

- `benchmarks/source_packets/dev_v0_2/ERA-DEV-01/model_input_packet.md`

Newly added evidence to verify:

- AgentBench p. 1: ICLR 2024 / arXiv v3 marker and 29 API/OSS LLM count.
- AgentBench p. 2 Figure 2: eight environments and code/game/web grounding categories.
- AgentBench p. 3 Table 1: model roster for pinned version.
- AgentBench p. 6 Table 2: heterogeneous metrics and inverse-weight statistics.
- AgentBench p. 7 Section 4.1 and Table 3: overall-score resizing/reciprocal-average weighting and resulting scores.
- AgentBench p. 8 Table 4 and Section 4.3: execution-outcome categories and Task Limit Exceeded interpretation.
- AgentBench p. 6 Section 4.1: evaluation toolkit, task workers, Docker/worker isolation, and prompt setup.

Gold status:

- Gold unchanged.
- Minimum human check: confirm version marker and 29-model wording match the pinned PDF and that failure-category wording separates observed outcomes from unverified causal explanations.

## `RL-DEV-01`

Changed packet:

- `benchmarks/source_packets/dev_v0_2/RL-DEV-01/model_input_packet.md`

Newly added evidence to verify:

- D4RL p. 1 Abstract and p. 2 Introduction: fixed offline datasets and benchmark evaluation framing.
- D4RL Section 3: fixed dataset, behavior-policy, and distribution-shift framing.
- D4RL p. 7: simulator-based evaluation and normalized-score definition.
- D4RL Appendix Tables 1-3: task identities, normalized scores, raw returns, and seed-reporting anchors.
- CQL pp. 1-4: action-distribution shift, conservative Q-functions, lower-bound objective, and policy-learning objectives.
- CQL Tables 1-2: D4RL performance comparisons and four-seed aggregation.
- CQL Table 3: Atari offline RL boundary.
- CQL Table 4: conservative-value/lower-bound analysis, not ordinary benchmark ranking.
- CQL Appendix p. 29: D4RL hyperparameter and four-seed reporting details.

Gold status:

- Gold unchanged.
- Minimum human check: confirm CQL Table 3/Table 4 roles and the wording around conservative Q-values are faithful and not oversimplified.

## Tasks Not Requiring Review For v0.2 Packet Changes

- `MC-DEV-01`: no v0.2 packet change proposed.
- `PS-DEV-01`: no v0.2 packet change proposed.

## Next Gate

After human review approves these draft packets, the next action is to freeze `round1_dev_v0.2` with a new manifest and report. Do not rerun B0 or implement variants before that freeze.
