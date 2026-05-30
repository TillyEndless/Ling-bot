**method_comparison_matrix**

| Dimension | DPO-style preference optimization | PPO-style RLHF | Comparable as stated? | Evidence-burden label | Evidence | Boundary |
|---|---|---|---|---|---|---|
| Objective | Directly optimize a language-model policy from preference data, avoiding a separate standalone reward model plus RL stage. | Optimize a policy using PPO after supervised fine-tuning and reward-model training from human preference comparisons. | Partly. Both target preference-aligned policies, but pipeline structure differs. | `DIRECT_PACKET_EVIDENCE` | DPO: abstract, Sections 3-4. InstructGPT: method sections on SFT, reward modeling, RLHF/PPO. | Packet does not establish universal objective superiority. |
| Preference model / reward framing | Derivation uses a preference model such as Bradley-Terry and a KL-constrained reward-maximization framing. | Uses an explicit learned reward model from human comparisons, then PPO for policy optimization. | Yes, at high level. | `DIRECT_PACKET_EVIDENCE` | DPO: Sections 3-4, appendices. InstructGPT: reward modeling and RLHF/PPO method sections. | Exact mathematical equivalence or mismatch beyond supplied notes is unknown. |
| Data requirements | Requires preference data. Packet does not state all dataset details. | Requires SFT data, human preference comparisons for reward modeling, and policy optimization setup. | Partly. PPO-style RLHF pipeline has more explicitly staged data needs in the packet. | `DIRECT_PACKET_EVIDENCE` | InstructGPT: data collection description. DPO: Sections 3-4, Section 6. | Dataset scale, labeling cost, and data quality comparisons are unknown unless directly reported in the packet. |
| Optimization dynamics | Direct preference optimization; no explicit standalone reward-model fitting followed by RL. | PPO policy-gradient optimization using clipped or KL-penalized surrogate objectives in the general PPO paper; applied in RLHF pipeline in InstructGPT. | Partly. DPO and PPO optimize different objectives/procedures. | `WITHIN_PACKET_SYNTHESIS` | DPO: abstract, Sections 3-4. PPO: abstract, Sections 3-5, Algorithm 1. InstructGPT: RLHF/PPO method sections. | Packet does not support claims about stability, sample efficiency, or ease of tuning in general. |
| Baselines | Compared to PPO-style preference-learning baselines in selected sentiment and summarization settings. | InstructGPT evaluates instruction-following behavior under its multi-stage RLHF pipeline. PPO paper compares PPO on RL benchmarks. | Limited. DPO has direct comparisons to PPO-style preference-learning baselines in selected settings; PPO paper itself is not an LLM post-training comparison. | `DIRECT_PACKET_EVIDENCE` / `WITHIN_PACKET_SYNTHESIS` | DPO: Figure 2, Section 6, Table 1. InstructGPT: main result tables. PPO: Tables 1-6. | Cross-paper ranking is not justified without shared setup. |
| Evaluation protocols | Selected sentiment and summarization settings. | Instruction-following evaluation under InstructGPT’s data collection and evaluation protocol. General PPO evaluated on continuous control and Atari. | Mostly no across all sources. Evaluation targets differ. | `LIMITED_CRITIQUE` | DPO: Section 6, Table 1. InstructGPT: evaluation protocol, main result tables. PPO: Section 6, Tables 1-6. | Do not infer DPO is better for instruction following, or PPO-style RLHF is better for summarization, unless directly tested in the packet. |
| Evidence limits | Evidence is selected sentiment and summarization comparisons against PPO-style preference-learning baselines. | Evidence concerns instruction-following behavior under the InstructGPT pipeline; PPO algorithm evidence is from benchmark RL tasks, not LLM alignment. | Yes, limits are central to fair comparison. | `WITHIN_PACKET_SYNTHESIS` | Controlled source notes across all three papers. | Deployment robustness, general alignment quality, safety, and field-wide superiority require external review. |

**assumptions_table**

| Assumption | DPO-style preference optimization | PPO-style RLHF | Evidence-burden label | Supported scope |
|---|---|---|---|---|
| Human or preference comparisons can guide policy improvement | Yes, preference data is central. | Yes, human preference comparisons train the reward model. | `DIRECT_PACKET_EVIDENCE` | Supported for the described methods. |
| A preference model such as Bradley-Terry is appropriate | Explicitly part of DPO derivation. | Not stated in packet for InstructGPT/PPO-style RLHF. | `DIRECT_PACKET_EVIDENCE` for DPO; `unknown` for PPO-style RLHF | Do not assume shared preference-model form unless stated. |
| KL-constrained reward maximization is the framing | Explicit in DPO derivation. | PPO can use clipped or KL-penalized surrogate objectives; RLHF pipeline uses PPO. | `WITHIN_PACKET_SYNTHESIS` | Related but not identical as stated. |
| A separate reward model is required | No, DPO is presented as avoiding explicit standalone reward-model fitting followed by RL. | Yes, InstructGPT includes reward modeling before PPO. | `DIRECT_PACKET_EVIDENCE` | Supported for the described pipelines. |
| Online RL-style policy optimization is required | No explicit RL stage as described. | Yes, PPO-style policy optimization is part of the RLHF pipeline. | `DIRECT_PACKET_EVIDENCE` | Supported at method-description level. |
| One method is globally superior | Not supported. | Not supported. | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | Packet only supports setup-specific claims. |

**evidence_strength_summary**

DPO has direct packet evidence for its method definition, derivation assumptions, and selected empirical comparisons against PPO-style preference-learning baselines in sentiment and summarization settings. Evidence burden: `DIRECT_PACKET_EVIDENCE`.

InstructGPT/RLHF has direct packet evidence for a staged SFT plus reward modeling plus PPO pipeline and for instruction-following evaluations under that setup. Evidence burden: `DIRECT_PACKET_EVIDENCE`.

The PPO paper provides method background for PPO as a general RL algorithm using clipped or KL-penalized surrogate objectives, with benchmark evidence on continuous control and Atari. For LLM post-training, this is `METHOD_BACKGROUND`, not direct evidence that PPO-style RLHF outperforms DPO.

Any broad claim that DPO is simpler, cheaper, more stable, or generally better than PPO-style RLHF is not established by the packet unless tied narrowly to the DPO paper’s reported settings. Any broad claim that PPO-style RLHF is more capable, safer, or more general is also not established by the packet.

**fairness_caveats**

The strongest fair comparison is not “DPO vs PPO globally,” but “DPO’s direct preference objective vs PPO-style preference-learning baselines in the DPO paper’s selected sentiment and summarization settings.”

InstructGPT’s PPO-style RLHF evidence concerns an instruction-following pipeline, not necessarily the same tasks, data, models, metrics, or baselines used in the DPO comparisons.

The PPO algorithm paper is an algorithmic foundation source. Its continuous-control and Atari results should not be treated as direct evidence about LLM post-training quality.

Missing or unspecified details in the packet include exact model sizes, data scale, reward-model architecture, tuning budgets, seeds, uncertainty, compute, and all metric definitions. These omissions weaken cross-method ranking claims but do not prove flaws in the original studies.

**scoped_conclusions**

DPO-style preference optimization is supported by the packet as a direct preference-learning method derived from a KL-constrained reward-maximization view and a preference model such as Bradley-Terry, avoiding an explicit standalone reward-model-plus-RL pipeline.

PPO-style RLHF is supported by the packet as a multi-stage alignment pipeline: supervised fine-tuning, reward modeling from human preferences, and PPO-based policy optimization.

A careful comparison should say that DPO offers a direct alternative to PPO-style preference optimization in the settings where it is evaluated, while PPO-style RLHF has separate evidence as part of the InstructGPT instruction-following pipeline. The packet does not support a universal ranking between the two.