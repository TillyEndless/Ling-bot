# Packet Additions Diff For Human Review

Comparison: `benchmarks/source_packets/dev/<task_id>/model_input_packet.md` versus `benchmarks/source_packets/dev_v0_2/<task_id>/model_input_packet.md`.

No files were frozen and B0 was not rerun.

## LS-DEV-01

### Addition LS-A1

New passage:

> The abstract also states that the paper includes an extension to block-sparse attention. Treat that as an additional approximate/sparse extension, not as the definition of the core FlashAttention algorithm.

Source: `FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness`, p. 1 Abstract.

Supports approved anchor: `LS4`, FlashAttention exact core versus block-sparse extension.

Leakage assessment: Moderate risk. The first sentence is source evidence. The second sentence is an interpretive boundary and closely matches the approved gold distinction; it may be better rewritten as neutral source wording before freeze.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition LS-A2

New passage:

> Section 3 presents the core exact-attention algorithm as IO-aware tiling that avoids materializing the full attention matrix and reduces HBM reads/writes while computing exact attention.

Source: `FlashAttention`, p. 4 Section 3.

Supports approved anchor: `LS4`, exact attention with fewer HBM reads/writes.

Leakage assessment: Low to moderate risk. It is source-grounded, but the phrase "core exact-attention algorithm" is an interpretation aligned with the gold. Likely acceptable if the source language supports it directly.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition LS-A3

New passage:

> Relevant evidence locations: p. 1 Abstract; p. 4 Section 3; p. 7 Section 4.1 and Table 1 for BERT-large training-time comparison; p. 8 Table 2 for GPT-2 training-time comparison; theorem/complexity discussion; experiment tables and figures.

Source: `FlashAttention`, p. 1 Abstract; p. 4 Section 3; p. 7 Section 4.1/Table 1; p. 8 Table 2.

Supports approved anchor: `LS4`, setup-specific FlashAttention evidence.

Leakage assessment: Low risk. This is source-location metadata, not a conclusion.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## SPR-DEV-01

### Addition SPR-A1

New passage:

> Section 4.1 gives the trainable low-rank update form: W0 is frozen, A and B are trainable, and the task-specific update is represented as Delta W = BA.

Source: `LoRA: Low-Rank Adaptation of Large Language Models`, p. 4 Section 4.1, Equation 3.

Supports approved anchor: `SPR1`, LoRA method definition.

Leakage assessment: Low risk. This is direct method evidence.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A2

New passage:

> Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks, while the paper's Transformer experiments focus on selected weight matrices in attention modules.

Source: `LoRA`, p. 4 Section 4.2.

Supports approved anchor: `SPR1`, general dense-layer applicability versus selected Transformer experiment focus.

Leakage assessment: Low to moderate risk. It is source-grounded but already frames the contrast the scorer expects. Acceptable if Section 4.2 explicitly supports both clauses.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A3

New passage:

> Relevant evidence locations: p. 1 Abstract and Figure 1; p. 2 Introduction; p. 4 Sections 4.1-4.2, including Equation 3.

Source: `LoRA`, p. 1 Abstract/Figure 1; p. 2 Introduction; p. 4 Sections 4.1-4.2/Equation 3.

Supports approved anchors: `SPR1`, `SPR2`.

Leakage assessment: Low risk. Source-location metadata only.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A4

New passages:

> Table 3 reports GPT-2 medium and large results on the E2E NLG Challenge.

> Table 4 reports GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons.

Source: `LoRA`, p. 6 Table 3; p. 7 Table 4.

Supports approved anchor: `SPR3`, evaluated model/task scope; `SPR4`, GPT-3 trainable-parameter comparison.

Leakage assessment: Low risk. These are table descriptions.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A5

New passage:

> The paper separately discusses trainable-parameter reduction, GPU-memory reduction, training throughput, inference latency, and model quality. Do not collapse these into one generic efficiency claim.

Source: `LoRA`, p. 1 Abstract; p. 2 Introduction; p. 3 Table 1; pp. 3-4 Section 4.1; p. 4 pre-Section-5 paragraph; p. 7 Table 4.

Supports approved anchor: `SPR4`, separated efficiency dimensions.

Leakage assessment: High risk. The first sentence summarizes source evidence, but the second sentence is an explicit scoring boundary. Consider revising to a neutral list of distinct source-reported dimensions only.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A6

New passages:

> The paragraph before Section 5 reports a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the paper's stated setup.

> Section 4.1 explains that LoRA updates can be merged into W0 for deployment so that inference has no additional latency relative to the corresponding fully fine-tuned weight path.

Source: `LoRA`, p. 4 paragraph before Section 5; pp. 3-4 Section 4.1.

Supports approved anchor: `SPR4`, training throughput and inference-latency claims.

Leakage assessment: Low risk. These are source-facing evidence summaries.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A7

New passage:

> When no-latency deployment depends on merged LoRA weights, batching inputs from different tasks that require different LoRA modules is not straightforward; the paper notes dynamic module selection remains possible when latency is not critical.

Source: `LoRA`, p. 4 paragraph immediately before Section 5.

Supports approved anchor: `SPR5`, deployment limitation.

Leakage assessment: Low risk. This is a source-facing limitation summary.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A8

New passages:

> Section 7.1 and Table 5 analyze which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks.

> Section 7.2 and Table 6 analyze the effect of rank r on WikiSQL and MultiNLI in selected GPT-3 settings.

> Footnote 6 cautions that a small rank r should not be expected to work for every task or dataset.

Source: `LoRA`, p. 9 Section 7.1/Table 5; p. 9 Section 7.2/Table 6; p. 10 footnote 6.

Supports approved anchors: `SPR2`, `SPR6`, bounded low-rank claim and matrix/rank analyses.

Leakage assessment: Low to moderate risk. The passages are source-facing, but "selected GPT-3 settings" nudges the intended scope boundary. Likely acceptable because it is an evidence-scope statement rather than a scoring label.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition SPR-A9

New passage:

> Relevant evidence locations: abstract; p. 3 Table 1; pp. 3-4 Section 4.1 no-additional-inference-latency discussion; p. 4 limitations paragraph before Section 5; Section 5 experiment setup; p. 6 Table 3; p. 7 Table 4; p. 9 Section 7.1/Table 5; p. 9 Section 7.2/Table 6; p. 10 footnote 6; appendices for implementation details.

Source: `LoRA`, listed locations.

Supports approved anchors: `SPR3`, `SPR4`, `SPR5`, `SPR6`.

Leakage assessment: Low risk. Source-location metadata only.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## ERA-DEV-01

### Addition ERA-A1

New passages:

> The local canonical source is the ICLR 2024 / arXiv v3 PDF whose first page reports "arXiv:2308.03688v3 [cs.AI] 4 Oct 2025."

> The abstract in this pinned version reports evaluation over 29 API-based and open-sourced LLMs.

Source: `AgentBench: Evaluating LLMs as Agents`, p. 1 first page and Abstract.

Supports approved anchor: `ERA2`, pinned version and 29-model condition; `ERA-E4`.

Leakage assessment: Low risk. Version and count metadata are needed for source identity.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition ERA-A2

New passages:

> Figure 2 groups the eight environments into grounding categories, including code-grounded, game-grounded, and web-grounded task types.

> Table 1 lists the evaluated model roster for the pinned 29-model version.

Source: `AgentBench`, p. 2 Figure 2; p. 3 Table 1.

Supports approved anchors: `ERA1`, `ERA2`.

Leakage assessment: Low risk. These are figure/table descriptions.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition ERA-A3

New passage:

> Evidence locations: p. 1 Abstract; p. 2 Figure 2 and Introduction; p. 3 Table 1; Sections 1-4; Table 2; Table 3; appendices B-I.

Source: `AgentBench`, listed locations.

Supports approved anchors: `ERA1`, `ERA2`.

Leakage assessment: Low risk. Source-location metadata only.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition ERA-A4

New passages:

> Table 2 reports environment-specific metrics. Several environments use success rate, while others use F1, reward, game progress, or step success rate.

> Section 4.1 describes the overall-score calculation: task scores are resized and aggregated using task weights derived from reciprocal average model performance, not a simple unweighted success-rate average.

> Table 3 reports environment-specific scores and the overall AgentBench score after the paper's aggregation procedure.

Source: `AgentBench`, p. 6 Table 2; p. 7 Section 4.1 Overall Score Calculation; p. 7 Table 3.

Supports approved anchor: `ERA3`, heterogeneous metrics and weighted aggregation.

Leakage assessment: Moderate risk. The content is source-facing, but "not a simple unweighted success-rate average" directly mirrors the expected audit conclusion. Could be rewritten as neutral aggregation procedure details.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition ERA-A5

New passages:

> Section 2 defines execution-outcome categories including Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded.

> Table 4 and Section 4.3 report aggregate execution outcomes and identify Task Limit Exceeded as the predominant aggregate failure outcome, while some environments show substantial format- or action-validity failures.

Source: `AgentBench`, p. 4 Section 2; p. 8 Table 4 and Section 4.3.

Supports approved anchor: `ERA5`, observed execution-outcome categories.

Leakage assessment: Low to moderate risk. It is source-facing and table-based, but "predominant" is an interpreted summary that should be checked against Table 4.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition ERA-A6

New passage:

> Section 4.1 also describes the API-centric evaluation toolkit, task workers, Docker/worker isolation, and evaluation-prompt setup at the level needed for audit.

Source: `AgentBench`, p. 6 Section 4.1.

Supports approved anchor: `ERA-AUDIT`, benchmark audit requirements.

Leakage assessment: Moderate risk. "At the level needed for audit" is evaluator-framed rather than source-framed. Recommend revising to list only the source elements.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition ERA-A7

New passages:

> Evidence locations: pp. 4-5 Section 3 environment descriptions; p. 4 Section 2 execution-outcome categories; p. 6 Section 4.1 and Table 2; p. 7 Section 4.1 Overall Score Calculation and Table 3; p. 8 Section 4.3 and Table 4; appendix task details.

> Distinguish observed execution outcomes from unverified causal explanations of those outcomes.

> Respect the pinned paper version when stating model counts, included models, or reported score interpretation.

Source: `AgentBench`, listed locations; p. 1 version/count evidence; p. 8 outcome evidence.

Supports approved anchors: `ERA-AUDIT`, `ERA-E3`, `ERA-E4`, `ERA-IB`.

Leakage assessment: High risk for the last two sentences. They are inference-boundary/scoring guidance rather than raw source evidence. Consider moving them out of the packet or rewriting as source-facing cautions if they are directly supported by text.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## RL-DEV-01

### Addition RL-A1

New passages:

> D4RL frames algorithms as training from static, previously collected datasets in the offline RL setting.

> Benchmark policy performance is evaluated through specified simulator-based evaluation and reported with normalized-return conventions.

Source: `D4RL: Datasets for Deep Data-Driven Reinforcement Learning`, p. 1 Abstract; p. 2 Introduction; p. 7 evaluation protocol.

Supports approved anchor: `RL1`, offline training versus simulator-based evaluation.

Leakage assessment: Low risk. Source-facing task/protocol description.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition RL-A2

New passages:

> The normalized score is benchmark-specific and uses domain/task reference anchors; do not interpret it as a universal absolute performance scale.

> Appendix Tables 1-3 provide task identities, normalized scores, raw returns, and seed-reporting anchors.

Source: `D4RL`, p. 7 normalized-score definition; Appendix Tables 1-3.

Supports approved anchors: `RL1`, `RL-PROTOCOL`, `RL-IB4`.

Leakage assessment: High risk for "do not interpret it..." because it is scoring/inference-boundary guidance. The first clause and second passage are source-facing; the warning should likely be rewritten neutrally or moved out of packet.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition RL-A3

New passage:

> Evidence locations: p. 1 Abstract; p. 2 Introduction; Section 3 fixed dataset and behavior-policy framing; Sections 4-5 task design factors and task instantiations; p. 7 evaluation protocol and normalized-score definition; Appendix Tables 1-3; limitations/discussion.

Source: `D4RL`, listed locations.

Supports approved anchors: `RL1`, `RL2`, `RL-PROTOCOL`.

Leakage assessment: Low risk. Source-location metadata only.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition RL-A4

New passages:

> CQL addresses offline RL distributional shift by learning conservative Q-functions that reduce optimistic value estimates for learned-policy actions unsupported or weakly supported by the offline dataset.

> The CQL objective regularizes Q-values under selected action distributions relative to dataset-supported behavior and provides lower-bound guarantees under stated assumptions.

Source: `Conservative Q-Learning for Offline Reinforcement Learning`, p. 1 Abstract/Introduction; p. 2 Section 2; p. 3 Section 3.1; p. 4 Section 3.2 Equations 3-4.

Supports approved anchor: `RL3`, corrected conservative-Q formulation.

Leakage assessment: Low to moderate risk. This is a source-facing method summary, but it closely encodes the approved formulation. Human should confirm wording is faithful and not over-specific.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition RL-A5

New passages:

> Tables 1 and 2 report setup-specific normalized-score comparisons on D4RL domains, including Gym, AntMaze, Adroit, and Kitchen, averaged over four seeds.

> Table 3 concerns Atari offline RL experiments and should not be used as D4RL performance evidence.

> Table 4 concerns conservative-value/lower-bound analysis on selected D4RL datasets rather than an ordinary benchmark ranking table.

> Appendix p. 29 provides D4RL hyperparameter and four-seed reporting details.

Source: `CQL`, p. 7 Section 6/Table 1; p. 8 Table 2; p. 9 Tables 3-4; Appendix p. 29.

Supports approved anchor: `RL4`, CQL table roles and seed reporting.

Leakage assessment: High risk for "should not be used..." and "rather than an ordinary benchmark ranking table" because these are explicit scoring boundaries. The table-role evidence is needed, but wording should probably be made more source-descriptive.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition RL-A6

New passage:

> Evidence locations: p. 1 Abstract and Introduction; p. 2 Section 2 action distribution shift; p. 3 Section 3.1 conservative off-policy evaluation and lower-bound Q objective; p. 4 Section 3.2 Equations 3-4; p. 7 Section 6 and Table 1; p. 8 Table 2; p. 9 Table 4; Appendix p. 29; conclusion/limitations.

Source: `CQL`, listed locations.

Supports approved anchors: `RL3`, `RL4`.

Leakage assessment: Low risk. Source-location metadata only.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

### Addition RL-A7

New passages:

> Separate offline training on fixed datasets from simulator-based policy evaluation.

> Separate algorithmic motivation and theoretical lower-bound analysis from empirical benchmark performance claims.

Source: D4RL p. 7 evaluation protocol; CQL pp. 3-4 lower-bound objective; CQL pp. 7-9 empirical tables.

Supports approved anchors: `RL-PROTOCOL`, `RL-IB1`, `RL-IB5`.

Leakage assessment: High risk. These are inference-boundary instructions rather than raw source evidence. Recommend revising into neutral source descriptions or removing from packet.

Review:

- [ ] Approve addition as source-grounded and non-leaking.
- [ ] Request revision because source location is unclear.
- [ ] Request revision because it leaks the expected conclusion.

## Unchanged Tasks

`MC-DEV-01`: unchanged from v0.1. No `benchmarks/source_packets/dev_v0_2/MC-DEV-01/model_input_packet.md` draft exists, and no v0.2 packet expansion was proposed.

`PS-DEV-01`: unchanged from v0.1. No `benchmarks/source_packets/dev_v0_2/PS-DEV-01/model_input_packet.md` draft exists, and no v0.2 packet expansion was proposed.

## Overall Review Note

Several additions are clean source-location or table-description additions. The main leakage risks are additions phrased as directives: "Treat that as...", "Do not collapse...", "not a simple...", "Distinguish...", "Respect...", "do not interpret...", and "should not be used...". These may be defensible as benchmark packet boundaries, but if the goal is purely raw source evidence, they should be revised before v0.2 freeze.
