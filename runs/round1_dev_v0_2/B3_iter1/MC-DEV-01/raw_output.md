## method_comparison_matrix

| Dimension | DPO-style preference optimization | PPO-style RLHF | Comparable as stated? | Evidence-burden label | Evidence | Boundary |
|---|---|---|---|---|---|---|
| Objective | Optimizes a language-model policy directly from preference data, using a derivation tied to a Bradley-Terry-style preference model and KL-constrained reward maximization. | In RLHF pipeline, optimizes a policy using PPO after supervised fine-tuning and reward-model training from human preference comparisons. PPO itself optimizes clipped or KL-penalized policy-gradient surrogate objectives. | Partly. Both can be framed around preference-aligned policy optimization, but PPO is a general RL optimizer while DPO is a direct preference-optimization method. | DIRECT_PACKET_EVIDENCE | DPO abstract, Sections 3-4, appendices; InstructGPT method sections; PPO abstract, Sections 3-5, Algorithm 1. | Packet does not provide a unified mathematical comparison beyond the controlled notes. |
| Assumptions | Relies on a preference model such as Bradley-Terry and a KL-constrained reward-maximization framing. Avoids fitting an explicit standalone reward model followed by RL. | Assumes a staged pipeline: SFT, reward modeling from human comparisons, then PPO policy optimization. PPO assumes policy-gradient RL setup with surrogate objectives. | Partly. DPO and PPO-style RLHF share preference-data motivation in LLM alignment, but differ in whether reward modeling and RL are explicit stages. | DIRECT_PACKET_EVIDENCE | DPO Sections 3-4; InstructGPT method sections; PPO Sections 3-5. | Unknown whether all assumptions are equally satisfied in the same datasets or model scales; packet does not specify enough. |
| Data requirements | Preference data are required. Source packet does not specify the full data recipe beyond selected sentiment and summarization settings. | Requires SFT data, human preference comparisons for reward modeling, and policy optimization data or prompts under the RLHF setup. | Yes at high level, but not enough for quantitative data-efficiency claims. | DIRECT_PACKET_EVIDENCE | DPO Section 6, Table 1; InstructGPT data collection description. | Any claim that DPO needs less data, cheaper labels, or less compute is unsupported unless directly shown in packet details, which are not provided here. |
| Optimization dynamics | Direct optimization from preferences; no explicit standalone reward model followed by RL. | Multi-stage optimization; PPO updates policy using clipped or KL-penalized surrogate objectives in the RLHF stage. | Partly. The procedural contrast is supported; stability, convergence, or optimization-efficiency rankings are not established by the packet. | DIRECT_PACKET_EVIDENCE / LIMITED_CRITIQUE | DPO abstract, Sections 3-4; InstructGPT RLHF/PPO method sections; PPO Algorithm 1. | Claims about which is more stable, simpler in practice, or easier to tune are unknown from the packet unless specific results are supplied. |
| Baselines | DPO compares against PPO-style preference-learning baselines in selected sentiment and summarization settings. | InstructGPT evaluates instruction-following behavior under its pipeline; PPO paper compares PPO on benchmark RL tasks including continuous control and Atari. | Limited. DPO has direct selected comparisons to PPO-style baselines; InstructGPT and PPO papers are not direct DPO comparisons. | DIRECT_PACKET_EVIDENCE / WITHIN_PACKET_SYNTHESIS | DPO Section 6, Figure 2, Table 1; InstructGPT main result tables; PPO Section 6, Tables 1-6. | Cross-paper ranking is not justified because tasks, models, and evaluation protocols differ. |
| Evaluation protocols | Selected sentiment and summarization settings. | InstructGPT: instruction-following evaluation under its data collection and evaluation protocol. PPO: benchmark RL tasks, including continuous control and Atari. | Mostly no across all three papers. Only DPO’s own selected comparisons are directly comparable as stated. | WITHIN_PACKET_SYNTHESIS | DPO Section 6/Table 1; InstructGPT evaluation protocol/main tables; PPO Section 6/Tables 1-6. | LLM post-training evidence and general RL benchmark evidence should not be merged into one superiority claim. |
| Evidence limits | Supports that DPO is presented and evaluated as a direct preference-optimization alternative to PPO-style preference-learning baselines in selected settings. | Supports that PPO-style RLHF was used in a multi-stage instruction-following alignment pipeline; PPO also has separate RL benchmark evidence. | Comparable only within matched LLM preference-learning setups. | LIMITED_CRITIQUE | Controlled source notes across all three papers. | Global claims such as “DPO is better than PPO-style RLHF” or “PPO-style RLHF is more reliable than DPO” are unsupported by this packet. |

## assumptions_table

| Assumption | DPO-style preference optimization | PPO-style RLHF | Evidence-burden label | Status |
|---|---|---|---|---|
| Preference comparisons can guide post-training | Yes, via direct optimization from preference data. | Yes, via reward modeling from human preference comparisons. | DIRECT_PACKET_EVIDENCE | Supported at high level. |
| Explicit reward model is required | No, DPO is presented as avoiding a standalone reward model followed by RL. | Yes in the InstructGPT pipeline: reward modeling precedes PPO policy optimization. | DIRECT_PACKET_EVIDENCE | Supported. |
| KL control matters | Yes, derivation uses KL-constrained reward maximization. | PPO may use clipped or KL-penalized surrogate objectives; RLHF pipeline uses PPO. | DIRECT_PACKET_EVIDENCE | Supported, but implementation details are not fully supplied. |
| Same tasks and metrics are used across methods | DPO uses selected sentiment and summarization settings. | InstructGPT uses instruction-following evaluation; PPO uses continuous control and Atari benchmarks. | WITHIN_PACKET_SYNTHESIS | Not supported globally. |
| One method is universally superior | Not established. | Not established. | UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW | Unsupported by packet. |
| Data, compute, and tuning budgets are directly comparable | Packet does not provide enough detail. | Packet does not provide enough detail. | LIMITED_CRITIQUE | Unknown. |

## evidence_strength_summary

The strongest packet-supported contrast is procedural: DPO directly optimizes from preference data without fitting a standalone reward model and then running RL, while PPO-style RLHF in InstructGPT uses a staged pipeline of SFT, reward modeling, and PPO policy optimization. This is `DIRECT_PACKET_EVIDENCE` from the DPO controlled notes and InstructGPT method notes.

The strongest empirical comparison is narrower: the DPO paper compares DPO against PPO-style preference-learning baselines in selected sentiment and summarization settings. That supports setup-specific comparison only, not general superiority. This is `DIRECT_PACKET_EVIDENCE` for the existence of those comparisons and `LIMITED_CRITIQUE` for restricting the conclusion scope.

The PPO paper supplies background evidence that PPO is a general policy-gradient RL algorithm evaluated on continuous control and Atari. It supports understanding PPO’s optimizer class, but not direct evidence about LLM post-training versus DPO. Using PPO benchmark results to rank RLHF against DPO would be `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`.

## fairness_caveats

- Do not compare DPO’s selected sentiment/summarization results against InstructGPT’s instruction-following results as if they were the same benchmark.
- Do not treat PPO’s continuous-control and Atari performance as evidence for or against PPO-style RLHF in language-model alignment.
- Do not infer global method superiority from DPO’s selected comparisons to PPO-style baselines.
- Do not claim DPO is simpler, cheaper, more stable, or easier to reproduce unless the packet provides direct evidence for those properties.
- Do not claim PPO-style RLHF is more robust or more scalable merely because it appears in a multi-stage instruction-following pipeline.
- Missing details about seeds, uncertainty, compute, tuning budgets, model sizes, and exact evaluation procedures limit cross-method conclusions.

## scoped_conclusions

DPO-style preference optimization and PPO-style RLHF should be compared first as different optimization pipelines for using preference information: DPO removes the explicit reward-model-plus-RL stage, while PPO-style RLHF keeps reward modeling and then applies PPO policy optimization.

The packet supports narrow, setup-specific empirical comparison where DPO is evaluated against PPO-style preference-learning baselines in selected sentiment and summarization settings. It does not support a broad claim that DPO is generally better than PPO-style RLHF, or that PPO-style RLHF is generally stronger than DPO.

A fair comparison would require matched models, preference datasets, prompts/tasks, metrics, KL constraints, tuning budgets, compute reporting, repeated runs or uncertainty estimates, and shared evaluation protocols. Those requirements are audit criteria from the packet, not established facts about the included experiments.