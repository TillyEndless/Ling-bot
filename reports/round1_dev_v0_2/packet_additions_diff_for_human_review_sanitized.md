# Sanitized Packet Additions Diff For Human Review

Comparison: `benchmarks/source_packets/dev/<task_id>/model_input_packet.md` versus sanitized `benchmarks/source_packets/dev_v0_2/<task_id>/model_input_packet.md`.

No files were frozen and B0 was not rerun.

## Sanitization Summary

The sanitization pass removed or neutralized directive/scoring-hint wording from the draft v0.2 model input packets. The remaining additions are intended to be source-facing paper facts, table/figure descriptions, version metadata, or source-location metadata.

## LS-DEV-01

### LS-A1

New passage:

> The abstract states that FlashAttention is an IO-aware exact attention algorithm and also reports an extension to block-sparse attention.

Source: `FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness`, p. 1 Abstract.

Supports approved anchor: `LS4`.

Leakage assessment: Low risk after sanitization. The previous directive phrasing was removed.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### LS-A2

New passage:

> Section 3 describes an IO-aware attention algorithm using tiling to reduce HBM reads and writes while computing exact attention without materializing the full attention matrix.

Source: `FlashAttention`, p. 4 Section 3.

Supports approved anchor: `LS4`.

Leakage assessment: Low risk. Source-facing method description.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### LS-A3

New passage:

> Relevant evidence locations: p. 1 Abstract; p. 4 Section 3; p. 7 Section 4.1 and Table 1 for BERT-large training-time comparison; p. 8 Table 2 for GPT-2 training-time comparison; theorem/complexity discussion; experiment tables and figures.

Source: `FlashAttention`, listed locations.

Supports approved anchor: `LS4`.

Leakage assessment: Low risk. Source-location metadata.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## SPR-DEV-01

Preserved additions `SPR-A1`, `SPR-A2`, `SPR-A3`, `SPR-A4`, `SPR-A6`, `SPR-A7`, `SPR-A8`, and `SPR-A9` from the previous review report.

### SPR-A5

New sanitized passage:

> The paper reports evidence concerning trainable-parameter counts, GPU-memory requirements, training throughput, inference latency, and downstream task quality in different sections and experimental settings.

Source: `LoRA: Low-Rank Adaptation of Large Language Models`, p. 1 Abstract; p. 2 Introduction; p. 3 Table 1; pp. 3-4 Section 4.1; p. 4 pre-Section-5 paragraph; p. 7 Table 4.

Supports approved anchor: `SPR4`.

Leakage assessment: Low risk after sanitization. The prior directive sentence was removed.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## ERA-DEV-01

Preserved additions `ERA-A1`, `ERA-A2`, and `ERA-A3`.

### ERA-A4

New sanitized passages:

> Table 2 reports environment-specific metrics. Several environments use success rate, while others use F1, reward, game progress, or step success rate.

> Section 4.1 describes the overall-score calculation: task scores are resized and aggregated using task weights derived from reciprocal average model performance.

> Table 3 reports environment-specific scores and the overall AgentBench score after the paper's aggregation procedure.

Source: `AgentBench: Evaluating LLMs as Agents`, p. 6 Table 2; p. 7 Section 4.1; p. 7 Table 3.

Supports approved anchor: `ERA3`.

Leakage assessment: Low risk after sanitization. The removed phrase compared the procedure to an unweighted average.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### ERA-A5

New sanitized passages:

> Section 2 defines execution-outcome categories including Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded.

> Table 4 reports aggregate proportions for these execution outcomes, and Section 4.3 discusses the reported outcome patterns.

Source: `AgentBench`, p. 4 Section 2; p. 8 Table 4 and Section 4.3.

Supports approved anchor: `ERA5`.

Leakage assessment: Low risk after sanitization. The earlier "predominant failure outcome" interpretation was removed from the packet.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### ERA-A6

New sanitized passage:

> Section 4.1 describes the API-centric evaluation toolkit, task workers, Docker/worker isolation, and evaluation-prompt setup.

Source: `AgentBench`, p. 6 Section 4.1.

Supports approved anchor: `ERA-AUDIT`.

Leakage assessment: Low risk after sanitization. The evaluator-framed phrase was removed.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### ERA-A7

Retained passage:

> Evidence locations: pp. 4-5 Section 3 environment descriptions; p. 4 Section 2 execution-outcome categories; p. 6 Section 4.1 and Table 2; p. 7 Section 4.1 Overall Score Calculation and Table 3; p. 8 Section 4.3 and Table 4; appendix task details.

Deleted from packet:

- `Distinguish observed execution outcomes from unverified causal explanations of those outcomes.`
- `Respect the pinned paper version when stating model counts, included models, or reported score interpretation.`

Source: `AgentBench`, listed locations.

Supports approved anchors: `ERA-AUDIT`, `ERA-E3`, `ERA-E4`, `ERA-IB`.

Leakage assessment: Low risk after sanitization. Only evidence-location metadata remains.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## RL-DEV-01

Preserved additions `RL-A1`, `RL-A3`, `RL-A4`, and `RL-A6`, subject to neutralized phrasing in the packet.

### RL-A2

New sanitized passages:

> The normalized score is defined using task- or domain-specific reference anchors.

> Appendix Tables 1-3 provide task identities, normalized scores, raw returns, and seed-reporting information.

Source: `D4RL: Datasets for Deep Data-Driven Reinforcement Learning`, p. 7 normalized-score definition; Appendix Tables 1-3.

Supports approved anchors: `RL1`, `RL-PROTOCOL`, `RL-IB4`.

Leakage assessment: Low risk after sanitization. The interpretation warning was removed.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### RL-A5

New sanitized passages:

> Tables 1 and 2 report normalized-score comparisons on D4RL domains, including Gym, AntMaze, Adroit, and Kitchen, averaged over four seeds.

> Table 3 reports Atari offline RL experiments.

> Table 4 reports estimated policy values and true returns on selected D4RL datasets in the paper's conservative-value analysis.

> Appendix p. 29 provides D4RL hyperparameter and four-seed reporting details.

Source: `Conservative Q-Learning for Offline Reinforcement Learning`, p. 7 Section 6/Table 1; p. 8 Table 2; p. 9 Tables 3-4; Appendix p. 29.

Supports approved anchor: `RL4`.

Leakage assessment: Low risk after sanitization. The prior table-use directives were removed.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### RL-A7

Deleted entirely from packet:

- `Separate offline training on fixed datasets from simulator-based policy evaluation.`
- `Separate algorithmic motivation and theoretical lower-bound analysis from empirical benchmark performance claims.`

Reason: This was inference-boundary guidance, not raw source evidence. Related evidence locations remain covered elsewhere in the packet.

## Unchanged Tasks

- `MC-DEV-01` remains carried forward unchanged from v0.1. No draft v0.2 packet exists for it.
- `PS-DEV-01` remains carried forward unchanged from v0.1. No draft v0.2 packet exists for it.

## Phrase Scan

The four sanitized v0.2 model input packets were scanned for:

- `Treat that as`
- `Do not collapse`
- `Respect`
- `should not be used`
- `do not interpret`
- `Distinguish`
- `correct interpretation`
- `must identify`
- `critical error`
- `gold`
- `scoring`

Result: no matches in the four sanitized model input packets.
