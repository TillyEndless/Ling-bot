## `method_comparison_matrix`

| Dimension | DPO-style preference optimization | PPO-style RLHF | Support status |
|---|---|---|---|
| Core objective | Directly optimizes a policy from preference data, avoiding a separate standalone reward-model-training-plus-RL stage. | Uses a multi-stage pipeline: supervised fine-tuning, reward modeling from human preference comparisons, then policy optimization with PPO. | Supported by packet. |
| Algorithmic framing | Derived from a preference model such as Bradley-Terry plus a KL-constrained reward-maximization formulation. | PPO is a policy-gradient RL method using clipped or KL-penalized surrogate objectives; in RLHF it is used as the policy optimization step after reward modeling. | Supported by packet. |
| Reward model | Does not fit an explicit standalone reward model before RL; the language model is treated as implicitly connected to reward modeling through the derivation. | Fits a reward model from human preference comparisons, then optimizes the policy against that reward model using PPO. | Supported by packet. |
| Preference data | Uses preference data directly for policy optimization. | Uses human preference comparisons to train a reward model. | Supported by packet. |
| Supervised data | Packet does not specify whether DPO requires SFT data as a general requirement. | Includes supervised fine-tuning as the first stage of the InstructGPT/RLHF pipeline. | DPO SFT requirement unknown from packet; PPO-style RLHF SFT stage supported. |
| Reference policy / KL role | Relies on a KL-constrained reward-maximization framing, implying a reference-policy constraint in the derivation. | PPO may use clipped or KL-penalized surrogate objectives; RLHF policy optimization is described as PPO-based. | Supported at high level; exact reference-policy mechanics unknown from packet. |
| Optimization dynamics | Direct preference optimization, avoiding an explicit RL loop after reward-model fitting. | Iterative policy-gradient reinforcement learning using PPO after reward-model training. | Supported at high level. Detailed stability/sample-efficiency claims unknown. |
| Baselines | Compared against PPO-style preference-learning baselines in selected sentiment and summarization settings. | InstructGPT evidence concerns its own RLHF pipeline and evaluation setup; PPO paper evidence concerns general RL benchmarks. | Supported by packet. |
| Evaluation settings | Selected sentiment and summarization settings. | Instruction-following behavior under the InstructGPT pipeline and evaluation setup. PPO alone is evaluated on benchmark RL tasks including continuous control and Atari. | Supported by packet. |
| Direct comparability | Direct comparisons exist only where DPO paper compares against PPO-style preference-learning baselines in selected tasks. | PPO-style RLHF evidence from InstructGPT is not automatically a controlled comparison against DPO. PPO paper is not direct LM-preference evidence. | Supported by required boundaries. |
| Claims about universal superiority | Not supported. | Not supported. | Must be marked unknown/speculative. |
| Claims about production suitability, cost, scalability, safety, or deployment | Unknown unless specifically reported in the packet. | Unknown unless specifically reported in the packet. | Packet-unsupported. |

## `assumptions_table`

| Assumption type | DPO-style | PPO-style RLHF | Packet-supported distinction |
|---|---|---|---|
| Preference-model assumption | Uses a preference model such as Bradley-Terry. | Uses human preference comparisons to train a reward model; specific preference-model form not specified in packet. | DPO assumption supported; PPO/RLHF details partially unknown. |
| Reward-model assumption | Avoids fitting an explicit standalone reward model before RL. | Assumes a learned reward model can guide policy optimization. | Supported. |
| Data assumption | Requires preference data. | Requires SFT data plus human preference comparisons in the described InstructGPT pipeline. | Supported. |
| RL assumption | Does not require running a separate RL optimization stage after reward-model training. | Requires PPO-style RL policy optimization in the described RLHF pipeline. | Supported. |
| KL/reference assumption | Derived from KL-constrained reward maximization. | PPO can use clipped or KL-penalized objectives. | Supported at abstract level. |
| Evaluation assumption | Evidence is task- and setup-specific: sentiment and summarization. | Evidence is setup-specific: instruction-following evaluations for InstructGPT; general RL benchmarks for PPO. | Supported. |

## `evidence_strength_summary`

| Evidence category | Strength |
|---|---|
| DPO objective and derivation | Relatively strong within packet: abstract, Sections 3-4, Figure 2, Section 6, Table 1, and appendices are identified. |
| DPO empirical comparison to PPO-style baselines | Limited: packet says comparisons are in selected sentiment and summarization settings only. |
| PPO-style RLHF pipeline description | Relatively strong within packet: InstructGPT method sections cover SFT, reward modeling, and RLHF/PPO. |
| PPO algorithm mechanics | Strong for general RL: PPO paper covers clipped or KL-penalized surrogate objectives, Algorithm 1, and benchmark evaluations. |
| PPO as evidence for language-model RLHF | Limited: PPO paper is not itself a language-model preference optimization paper. |
| Universal claims about DPO vs PPO/RLHF | Unsupported. Any such claim is speculative. |

## `fairness_caveats`

- Do not rank DPO and PPO-style RLHF universally from this packet.
- DPO comparisons to PPO-style baselines are only supported for selected sentiment and summarization settings.
- InstructGPT/RLHF evidence concerns one multi-stage instruction-following pipeline and its evaluation setup, not all PPO-style RLHF systems.
- PPO benchmark results on continuous control and Atari are not direct evidence about language-model preference optimization.
- Claims about compute cost, implementation complexity, safety, robustness, annotation efficiency, or deployment performance are unknown unless explicitly stated in the packet.
- Direct comparisons, indirect comparisons, and non-comparable evidence must remain separated.

## `scoped_conclusions`

DPO-style preference optimization is supported by the packet as a direct preference-based policy optimization method derived from a Bradley-Terry-like preference model and KL-constrained reward-maximization framing. Its key contrast with PPO-style RLHF is that it avoids fitting a separate standalone reward model followed by RL.

PPO-style RLHF, as represented by the InstructGPT paper, is supported as a multi-stage alignment pipeline: supervised fine-tuning, reward modeling from human preference comparisons, and PPO-based policy optimization.

The strongest fair conclusion is methodological rather than universal: DPO and PPO-style RLHF differ in how they use preference data and reward modeling. DPO directly optimizes from preferences; PPO-style RLHF trains a reward model and then runs RL policy optimization.

The packet does not support a universal claim that either method is better overall. Any broader claim about superiority, scalability, safety, cost, or general language-model performance should be marked unknown or speculative.