## method_comparison_matrix

| Dimension | DPO-style preference optimization | PPO-style RLHF | Comparable? | Evidence from packet | Caveat |
|---|---|---|---|---|---|
| Objective | Directly optimize a policy from preference data, framed through a preference model and KL-constrained reward-maximization derivation. | Optimize a policy using PPO after supervised fine-tuning and reward modeling from human preference comparisons. | Partly | DPO notes: abstract, Sections 3-4, appendices. InstructGPT notes: method sections on SFT, reward modeling, RLHF/PPO. | The packet does not provide exact objective equations, so detailed mathematical comparison is limited. |
| Reward model role | Does not fit an explicit standalone reward model before RL; the language model is treated through the DPO derivation as implicitly related to reward modeling. | Fits a reward model from human preference comparisons, then uses it during PPO policy optimization. | Yes, at pipeline level | DPO notes: direct method without explicit standalone reward model and RL. InstructGPT notes: reward modeling then PPO. | “No explicit reward model” should not be overstated as “no reward assumptions”; DPO still relies on a preference model and KL framing. |
| Assumptions | Relies on a preference model such as Bradley-Terry and KL-constrained reward maximization. | Assumes reward model learned from human comparisons can guide policy optimization through PPO. | Partly | DPO notes: Sections 3-4, appendices. InstructGPT notes: reward modeling and PPO method sections. | Packet gives high-level assumptions only; robustness of assumptions is unknown. |
| Data requirements | Preference data. | SFT data, human preference comparisons for reward modeling, and PPO policy optimization setup. | Partly | DPO notes: preference data. InstructGPT notes: SFT, reward modeling, RLHF/PPO, data collection. | Packet does not specify dataset sizes, annotation formats, or whether the same preference data could be reused across methods. |
| Optimization dynamics | Direct preference-optimization objective; avoids a separate RL optimization stage according to the packet. | Multi-stage pipeline with PPO policy-gradient optimization, using clipped or KL-penalized surrogate objectives from PPO. | Partly | DPO notes: direct method. InstructGPT notes: PPO-based RLHF. PPO notes: clipped or KL-penalized surrogate objectives, Algorithm 1. | Direct comparison of stability, sample efficiency, or compute is unsupported without compatible experiments. |
| Baselines | Compared to PPO-style preference-learning baselines in selected sentiment and summarization settings. | InstructGPT evaluates instruction-following behavior under its pipeline and setup. PPO paper evaluates PPO on RL benchmarks such as continuous control and Atari. | Limited | DPO notes: Section 6, Figure 2, Table 1. InstructGPT notes: main result tables. PPO notes: Sections 3-6, Tables 1-6. | Cross-paper baseline comparison is not automatically fair because tasks, data, models, and metrics differ. |
| Evaluation protocols | Selected sentiment and summarization settings. | Instruction-following evaluation under the InstructGPT pipeline. | Limited | DPO notes: Section 6, Table 1. InstructGPT notes: evaluation protocol and main result tables. | These are not the same evaluation protocols, so broad superiority claims are unsupported. |
| Evidence limits | Supports claims about DPO under selected paper settings and its derivation assumptions. | Supports claims about PPO-style RLHF within the InstructGPT instruction-following setup and PPO’s general RL algorithm behavior on benchmark RL tasks. | Yes, but scoped | Controlled source notes for all three papers. | Packet does not establish a universal winner between DPO-style optimization and PPO-style RLHF. |

## assumptions_table

| Assumption | Method | Provenance | Support status | Evidence limit |
|---|---|---|---|---|
| Human preferences can be modeled with a preference model such as Bradley-Terry. | DPO | Source-derived | Supported by packet | The packet does not assess whether this assumption holds across domains. |
| KL-constrained reward maximization is an appropriate framing for deriving the objective. | DPO | Source-derived | Supported by packet | The packet gives the framing, not a full validation of its practical adequacy. |
| Preference data is sufficient for the direct DPO-style update under the paper’s setup. | DPO | Agent-inferred from source notes | Partly supported | Exact data requirements and failure modes are unknown. |
| A learned reward model from human preference comparisons can guide policy optimization. | PPO-style RLHF | Source-derived | Supported by packet | Reward model quality, bias, and calibration details are not provided in the packet. |
| PPO is an appropriate optimizer for the RLHF policy-optimization stage. | PPO-style RLHF | Cross-source synthesis | Partly supported | PPO is described as a general RL algorithm, and InstructGPT uses PPO, but the packet does not prove PPO is optimal for RLHF. |
| PPO’s benchmark RL results transfer directly to LLM post-training. | PPO-style RLHF | Unsupported | Unknown/speculative | PPO paper evaluates continuous control and Atari, not LLM post-training. |
| DPO is generally better than PPO-style RLHF. | DPO | Unsupported | Unknown/speculative | Packet only mentions selected sentiment and summarization comparisons. |
| PPO-style RLHF is generally better than DPO. | PPO-style RLHF | Unsupported | Unknown/speculative | Packet does not provide compatible head-to-head evidence favoring PPO-style RLHF broadly. |

## evidence_strength_summary

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|
| DPO avoids fitting an explicit standalone reward model followed by RL. | Method description | Direct method description | DPO controlled notes: abstract, Sections 3-4 | Supported | DPO as presented in the packet. |
| DPO depends on preference-model and KL-constrained reward-maximization assumptions. | Method assumption | Derivation or method statement | DPO controlled notes: Sections 3-4 and appendices | Supported | DPO derivation assumptions. |
| InstructGPT-style RLHF uses SFT, reward modeling, and PPO. | Method description | Pipeline description | InstructGPT controlled notes: method sections | Supported | InstructGPT/RLHF pipeline in the packet. |
| PPO is a general policy-gradient RL algorithm using clipped or KL-penalized surrogate objectives. | Method description | Algorithm paper evidence | PPO controlled notes: abstract, Sections 3-5, Algorithm 1 | Supported | PPO as a general RL algorithm. |
| DPO outperforms PPO-style baselines in all LLM post-training settings. | Improvement/generalization | Compatible broad comparisons across settings | Only selected sentiment and summarization settings are mentioned | Unsupported | Unknown. |
| PPO-style RLHF is more reliable because PPO has broad RL benchmark evidence. | Generalization | Evidence connecting RL benchmarks to LLM post-training | PPO evidence is continuous control and Atari; InstructGPT evidence is instruction following | Unsupported | Unknown/speculative. |
| DPO and PPO-style RLHF can be fairly compared by headline scores alone. | Benchmark-validity | Compatible metrics, data, protocols, baselines, compute | Packet does not provide such compatibility | Unsupported | Should not be concluded. |

## fairness_caveats

| Severity | Claim affected | Evidence issue | Consequence | Minimal fix |
|---|---|---|---|---|
| High | “DPO is better than PPO-style RLHF” | Packet only supports selected DPO comparisons against PPO-style baselines in sentiment and summarization. | Overstates generality beyond supplied evidence. | Restrict the claim to the exact reported settings, or require matched evaluations across tasks. |
| High | “PPO-style RLHF is better established for LLM post-training” | PPO’s own paper evaluates continuous control and Atari, while InstructGPT evaluates a specific instruction-following pipeline. | Conflates general RL algorithm evidence with LLM alignment evidence. | Separate PPO algorithm evidence from RLHF pipeline evidence. |
| High | Direct cross-paper performance comparison | Tasks, data, metrics, model sizes, compute, and protocols are not specified as compatible in the packet. | Any winner claim may be confounded. | Compare only under matched datasets, models, metrics, tuning budgets, and evaluation protocols. |
| Medium | “DPO removes reward modeling entirely” | DPO avoids an explicit standalone reward model, but relies on preference-model and reward-maximization derivation assumptions. | Misrepresents the method’s theoretical dependencies. | Say “no explicit standalone reward model stage,” not “no reward-model assumptions.” |
| Medium | Optimization stability or compute-efficiency claims | Packet does not provide comparable runtime, variance, tuning, or failure-mode details. | Efficiency or stability claims would be speculative. | Require seeds, runs, hyperparameter search, compute budgets, and variance reporting. |
| Medium | Evaluation validity | Packet mentions evaluation settings but not full metric definitions or aggregation details. | Aggregate conclusions may hide task-specific behavior. | Preserve per-task results and specify metrics and aggregation. |

## scoped_conclusions

DPO-style preference optimization and PPO-style RLHF should be compared as different post-training pipelines, not as universally ranked methods.

Supported by the packet: DPO is a direct preference-optimization approach that avoids fitting an explicit standalone reward model followed by RL, while relying on preference-model and KL-constrained reward-maximization assumptions. PPO-style RLHF, as represented by InstructGPT, is a multi-stage pipeline involving supervised fine-tuning, reward modeling from human comparisons, and PPO policy optimization. PPO itself is a general policy-gradient RL algorithm evaluated in the PPO paper on benchmark RL tasks such as continuous control and Atari.

Not supported by the packet: broad claims that DPO is generally superior to PPO-style RLHF, that PPO-style RLHF is generally superior to DPO, or that PPO benchmark results on non-language RL tasks directly establish PPO’s advantage for LLM post-training.

A fair comparison would need matched models, preference data, prompts/tasks, metrics, baselines, compute budgets, hyperparameter tuning procedures, seeds, uncertainty reporting, and per-task results. Without those controls, the strongest valid conclusion is narrower: DPO and PPO-style RLHF differ in objective formulation and training pipeline, and the packet supports only scoped evidence about their behavior in the reported settings.