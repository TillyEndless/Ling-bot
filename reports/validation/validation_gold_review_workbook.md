# Validation Gold Review Workbook

Use this workbook to approve, revise, reject, or flag uncertainty for the highest-impact validation scoring anchors. Gold annotations remain pending and ineligible until reviewed.

## ERA-VAL-01

- Task type: `experimental_rigor_audit`
- Topic: LLM benchmark contamination
- Source packet ID: `validation_ERA-VAL-01_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/ERA-VAL-01/canonical_sources/brown_2020_language_models_are_few_shot_learners.pdf`: Language Models are Few-Shot Learners (arXiv:2005.14165)
- `benchmarks/source_packets/validation/ERA-VAL-01/canonical_sources/hendrycks_2021_measuring_massive_multitask_language_understanding.pdf`: Measuring Massive Multitask Language Understanding (arXiv:2009.03300)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `ERA-VAL-01-M1` | Identifies benchmark scores as protocol-bound evidence rather than self-validating capability proof. | GPT-3 PDF p.1 Abstract; evaluation/result sections; test-set contamination analysis section/appendix; MMLU PDF p.1 Abstract and benchmark/evaluation sections. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `requires_human_source_check` |  |  |  |
| `ERA-VAL-01-M2` | Audits contamination, benchmark exposure, prompt protocol, baseline choice, uncertainty, and reproducibility controls. | GPT-3 contamination analysis section/appendix; MMLU evaluation protocol and benchmark construction sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `ERA-VAL-01-M3` | Separates source-reported contamination analysis from additional contamination risks requiring follow-up evidence. | GPT-3 and MMLU result tables/figures and limitations/discussion sections. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## ERA-VAL-02

- Task type: `experimental_rigor_audit`
- Topic: generative model evaluation
- Source packet ID: `validation_ERA-VAL-02_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/ERA-VAL-02/canonical_sources/ho_2020_denoising_diffusion_probabilistic_models.pdf`: Denoising Diffusion Probabilistic Models (arXiv:2006.11239)
- `benchmarks/source_packets/validation/ERA-VAL-02/canonical_sources/nichol_2021_improved_ddpm.pdf`: Improved Denoising Diffusion Probabilistic Models (arXiv:2102.09672)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `ERA-VAL-02-M1` | Identifies quality/diversity/likelihood/speed claims and ties them to the metrics actually reported. | DDPM PDF p.1 Abstract and experiments section; Improved DDPM PDF p.1 Abstract and evaluation sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `ERA-VAL-02-M2` | Audits baselines, sample selection, human/subjective evaluation if present, ablations, compute, and dataset scope. | Improved DDPM metric/result tables and precision/recall or sample-quality discussion; DDPM sample-quality/likelihood result sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `ERA-VAL-02-M3` | Separates visual sample evidence from quantitative metric evidence and stated limitations. | DDPM and Improved DDPM experiment sections, ablation/result tables, sample figures, and discussion/limitations. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## LS-VAL-01

- Task type: `literature_mapping`
- Topic: diffusion and generative modeling efficiency
- Source packet ID: `validation_LS-VAL-01_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/LS-VAL-01/canonical_sources/song_2020_denoising_diffusion_implicit_models.pdf`: Denoising Diffusion Implicit Models (arXiv:2010.02502)
- `benchmarks/source_packets/validation/LS-VAL-01/canonical_sources/salimans_2022_progressive_distillation.pdf`: Progressive Distillation for Fast Sampling of Diffusion Models (arXiv:2202.00512)
- `benchmarks/source_packets/validation/LS-VAL-01/canonical_sources/lu_2022_dpm_solver.pdf`: DPM-Solver: A Fast ODE Solver for Diffusion Probabilistic Model Sampling in Around 10 Steps (arXiv:2206.00927)
- `benchmarks/source_packets/validation/LS-VAL-01/canonical_sources/rombach_2022_latent_diffusion_models.pdf`: High-Resolution Image Synthesis with Latent Diffusion Models (arXiv:2112.10752)
- `benchmarks/source_packets/validation/LS-VAL-01/canonical_sources/song_2023_consistency_models.pdf`: Consistency Models (arXiv:2303.01469)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `LS-VAL-01-M1` | Accounts for every paper in the fixed corpus. | All five canonical PDFs p.1 Abstracts and method overview sections. | Controls literature coverage and prevents missing or cherry-picked sources. | `requires_human_source_check` |  |  |  |
| `LS-VAL-01-M2` | Separates solver/sampler acceleration, distillation, latent-space modeling, and consistency/few-step generation lines where supported. | DDIM method/experiment sections; Progressive Distillation method/experiment sections; DPM-Solver method/experiment sections; Latent Diffusion method/experiment sections; Consistency Models method/experiment sections. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `LS-VAL-01-M3` | Links speed-quality tradeoffs to metrics, datasets, sampling steps, model settings, and scope. | Result tables/figures reporting sampling steps, quality metrics, speed, or compute tradeoffs in each canonical source. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## LS-VAL-02

- Task type: `literature_mapping`
- Topic: latent reasoning in language models
- Source packet ID: `validation_LS-VAL-02_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/LS-VAL-02/canonical_sources/wei_2022_chain_of_thought_prompting.pdf`: Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (arXiv:2201.11903)
- `benchmarks/source_packets/validation/LS-VAL-02/canonical_sources/kojima_2022_large_language_models_are_zero_shot_reasoners.pdf`: Large Language Models are Zero-Shot Reasoners (arXiv:2205.11916)
- `benchmarks/source_packets/validation/LS-VAL-02/canonical_sources/turpin_2023_unfaithful_explanations_cot.pdf`: Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting (arXiv:2305.04388)
- `benchmarks/source_packets/validation/LS-VAL-02/canonical_sources/lanham_2023_measuring_faithfulness_cot.pdf`: Measuring Faithfulness in Chain-of-Thought Reasoning (arXiv:2307.13702)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `LS-VAL-02-M1` | Accounts for supportive and skeptical papers in the fixed corpus. | All four canonical PDFs p.1 Abstracts and evaluation/method sections. | Controls literature coverage and prevents missing or cherry-picked sources. | `requires_human_source_check` |  |  |  |
| `LS-VAL-02-M2` | Distinguishes behavioral reasoning performance, rationale generation, faithfulness evidence, intervention/perturbation evidence, and speculative internal reasoning claims. | CoT and Zero-shot CoT evaluation sections; Unfaithful Explanations experiment sections; Measuring Faithfulness experiment/intervention sections. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `LS-VAL-02-M3` | Includes skeptical or alternative-explanation evidence rather than organizing around an assumed latent-reasoning thesis. | Unfaithful Explanations discussion/results; Measuring Faithfulness results and limitations/discussion. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `possibly_insufficient` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## MC-VAL-01

- Task type: `method_comparison`
- Topic: policy optimization
- Source packet ID: `validation_MC-VAL-01_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/MC-VAL-01/canonical_sources/schulman_2017_proximal_policy_optimization_algorithms.pdf`: Proximal Policy Optimization Algorithms (arXiv:1707.06347)
- `benchmarks/source_packets/validation/MC-VAL-01/canonical_sources/haarnoja_2018_soft_actor_critic.pdf`: Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor (arXiv:1801.01290)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `MC-VAL-01-M1` | Correctly distinguishes PPO on-policy policy-gradient assumptions from SAC off-policy maximum-entropy actor-critic assumptions. | PPO PDF p.1 Abstract, Section 3 clipped surrogate objective, Section 4 KL variant, Algorithm 1; SAC PDF p.1 Abstract and method/objective sections. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `MC-VAL-01-M2` | Compares continuous-control evidence only within compatible environment, metric, seed, and tuning settings. | PPO and SAC experiment sections, continuous-control benchmark tables/figures, and implementation/details sections where supplied. | Controls method-comparison fairness and protocol awareness. | `requires_human_source_check` |  |  |  |
| `MC-VAL-01-M3` | Avoids universal PPO-over-SAC or SAC-over-PPO claims. | PPO and SAC result tables, benchmark protocol descriptions, and discussion/limitations. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## MC-VAL-02

- Task type: `method_comparison`
- Topic: visual representation learning
- Source packet ID: `validation_MC-VAL-02_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/MC-VAL-02/canonical_sources/he_2015_deep_residual_learning.pdf`: Deep Residual Learning for Image Recognition (arXiv:1512.03385)
- `benchmarks/source_packets/validation/MC-VAL-02/canonical_sources/dosovitskiy_2020_vit.pdf`: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (arXiv:2010.11929)
- `benchmarks/source_packets/validation/MC-VAL-02/canonical_sources/liu_2022_convnet_for_the_2020s.pdf`: A ConvNet for the 2020s (arXiv:2201.03545)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `MC-VAL-02-M1` | Identifies architecture and inductive-bias differences without attributing all performance differences to architecture alone. | ResNet PDF p.1 Abstract and architecture sections; ViT PDF p.1 Abstract and architecture/data-scale sections; ConvNeXt PDF p.1 Abstract and modernization/training-recipe sections. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `requires_human_source_check` |  |  |  |
| `MC-VAL-02-M2` | Audits data scale, pretraining, augmentation, compute, training recipe, and benchmark comparability. | ViT data/pretraining/evaluation sections; ConvNeXt training recipe and ablation sections; ResNet ImageNet/CIFAR experiment sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `MC-VAL-02-M3` | Limits conclusions about transfer, robustness, or scaling to packet-supported settings. | Result tables/figures and discussion/limitations from ResNet, ViT, and ConvNeXt canonical PDFs. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## PS-VAL-01

- Task type: `evidence_grounded_proposal_support`
- Topic: world-model planning
- Source packet ID: `validation_PS-VAL-01_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/PS-VAL-01/canonical_sources/hafner_2019_dream_to_control.pdf`: Dream to Control: Learning Behaviors by Latent Imagination (arXiv:1912.01603)
- `benchmarks/source_packets/validation/PS-VAL-01/canonical_sources/hafner_2020_mastering_atari_discrete_world_models.pdf`: Mastering Atari with Discrete World Models (arXiv:2010.02193)
- `benchmarks/source_packets/validation/PS-VAL-01/canonical_sources/local_seed_world_model_planning.md`: local_seed_world_model_planning.md (local_seed_brief)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `PS-VAL-01-M1` | Grounds proposal hypotheses in world-model/planning packet facts and the local seed brief. | Dream to Control PDF p.1 Abstract and latent world-model/imagination sections; DreamerV2 PDF p.1 Abstract and Atari/world-model sections; local seed brief. | Controls proposal groundedness and hypothesis quality. | `requires_human_source_check` |  |  |  |
| `PS-VAL-01-M2` | Specifies falsifiable predictions, disconfirming outcomes, model-error controls, planning baselines, RL metrics, seeds, and environment details. | Dream to Control and DreamerV2 experiment sections, baseline tables/figures, and local seed brief. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `PS-VAL-01-M3` | Separates model-learning quality, planner quality, and policy performance claims. | World-model method sections, planning/control sections, result tables, and discussion/limitations in the two canonical PDFs. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## PS-VAL-02

- Task type: `evidence_grounded_proposal_support`
- Topic: mechanistic interpretability
- Source packet ID: `validation_PS-VAL-02_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/PS-VAL-02/canonical_sources/wang_2022_interpretability_in_the_wild_ioi.pdf`: Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small (arXiv:2211.00593)
- `benchmarks/source_packets/validation/PS-VAL-02/canonical_sources/meng_2022_locating_and_editing_factual_associations.pdf`: Locating and Editing Factual Associations in GPT (arXiv:2202.05262)
- `benchmarks/source_packets/validation/PS-VAL-02/canonical_sources/local_mech_interp_claim.md`: local_mech_interp_claim.md (local_seed_brief)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `PS-VAL-02-M1` | Separates descriptive/correlational mechanistic evidence from interventional or causal evidence. | IOI PDF p.1 Abstract and circuit/intervention sections; ROME PDF p.1 Abstract and causal tracing/model editing sections; local claim brief. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `PS-VAL-02-M2` | Proposes tests with causal interventions, controls, falsification criteria, and alternative explanations. | IOI ablation/intervention figures/tables; ROME causal tracing and editing result sections. | Controls proposal groundedness and hypothesis quality. | `requires_human_source_check` |  |  |  |
| `PS-VAL-02-M3` | Limits claims to supplied model family, task, layer, feature, and behavior scope. | IOI and ROME limitations/discussion plus local claim brief scope. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `possibly_insufficient` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## RL-VAL-01

- Task type: `rl_specific_analysis`
- Topic: model-based reinforcement learning
- Source packet ID: `validation_RL-VAL-01_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/RL-VAL-01/canonical_sources/chua_2018_pets.pdf`: Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models (arXiv:1805.12114)
- `benchmarks/source_packets/validation/RL-VAL-01/canonical_sources/hafner_2018_planet.pdf`: Learning Latent Dynamics for Planning from Pixels (arXiv:1811.04551)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `RL-VAL-01-M1` | Audits learned dynamics assumptions, planning horizon, model-error accumulation, baselines, seeds, evaluation episodes, and metrics. | PETS PDF p.1 Abstract and probabilistic dynamics/model predictive control sections; PlaNet PDF p.1 Abstract and latent dynamics/planning sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `RL-VAL-01-M2` | Separates planning success, world-model fidelity, sample efficiency, and policy performance. | PETS and PlaNet experiment sections, baseline tables/figures, environment descriptions, and evaluation protocol sections. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `RL-VAL-01-M3` | Requires model-free and model-based baselines where packet evidence supports the comparison need. | PETS/PlaNet model-learning sections, planning horizon/control sections, result tables, and limitations/discussion. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## RL-VAL-02

- Task type: `rl_specific_analysis`
- Topic: reward modeling and post-training RL
- Source packet ID: `validation_RL-VAL-02_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/RL-VAL-02/canonical_sources/christiano_2017_deep_rl_from_human_preferences.pdf`: Deep Reinforcement Learning from Human Preferences (arXiv:1706.03741)
- `benchmarks/source_packets/validation/RL-VAL-02/canonical_sources/bai_2022_training_helpful_harmless_assistant_rlhf.pdf`: Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback (arXiv:2204.05862)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `RL-VAL-02-M1` | Audits preference-data collection, reward-model training/validation, policy optimization, and policy evaluation setup. | Deep RL from Human Preferences PDF p.1 Abstract and preference/reward-predictor sections; Helpful/Harmless RLHF PDF p.1 Abstract and preference model/RLHF sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `RL-VAL-02-M2` | Separates reward-model score improvements from human preference, alignment, helpfulness, or deployment claims. | Preference data, reward model validation, policy optimization, and evaluation sections in both canonical PDFs. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `RL-VAL-02-M3` | Identifies proxy mismatch, reward hacking, evaluator bias, and train/eval leakage risks. | Result tables/figures and limitations/discussion covering proxy mismatch, evaluator bias, reward hacking, or evaluation scope where supplied. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## SPR-VAL-01

- Task type: `single_paper_deep_reading`
- Topic: world models
- Source packet ID: `validation_SPR-VAL-01_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/SPR-VAL-01/canonical_sources/hafner_2023_mastering_diverse_domains_through_world_models.pdf`: Mastering Diverse Domains through World Models (arXiv:2301.04104)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `SPR-VAL-01-M1` | Captures the world-model objective, policy-learning setup, evaluated domains, baselines, metrics, and reported limitations. | DreamerV3 PDF p.1 Abstract and method/objective sections. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `SPR-VAL-01-M2` | Separates model-based learning, latent dynamics, planning or imagination, and policy optimization claims. | DreamerV3 experiment sections, domain/evaluation tables, baseline comparisons, and ablation sections where supplied. | Controls inference-boundary discipline and prevents conflating evidence types. | `requires_human_source_check` |  |  |  |
| `SPR-VAL-01-M3` | Marks absent environment versions, wrappers, seeds, episodes, or implementation details as unknown. | DreamerV3 reproducibility/implementation details, result tables/figures, and limitations/discussion. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `requires_human_source_check` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |

## SPR-VAL-02

- Task type: `single_paper_deep_reading`
- Topic: sequence modeling for reinforcement learning
- Source packet ID: `validation_SPR-VAL-02_packet_v0_draft`

### Source Files To Open
- `benchmarks/source_packets/validation/SPR-VAL-02/canonical_sources/chen_2021_decision_transformer.pdf`: Decision Transformer: Reinforcement Learning via Sequence Modeling (arXiv:2106.01345)

### Highest-Priority Gold Anchors

| Item | Gold claim | Evidence location | Why it matters | Packet adequacy | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|---|
| `SPR-VAL-02-M1` | Captures the formulation of reinforcement learning as sequence modeling or conditional trajectory generation. | Decision Transformer PDF p.1 Abstract and method/formulation sections. | Controls factual extraction and evidence traceability. | `requires_human_source_check` |  |  |  |
| `SPR-VAL-02-M2` | Identifies offline datasets/environments, baselines, metrics, evaluation protocol, and reproducibility details. | Decision Transformer dataset/environment sections, baseline/metric sections, and experiment tables/figures. | Controls experimental and benchmark rigor scoring. | `requires_human_source_check` |  |  |  |
| `SPR-VAL-02-M3` | Does not overstate online-control, planning, imitation, or general RL implications beyond packet evidence. | Decision Transformer implementation/reproducibility details and limitations/discussion. | High-weight anchor affecting factual correctness, traceability, or scope discipline. | `possibly_insufficient` |  |  |  |

### Critical-Error Rules To Verify

| Item | Error | Penalty | Grounding / fairness check | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `E1` | Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E2` | Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | `major` | potentially broad; verify penalty is applied only to core claims |  |  |  |
| `E3` | Invents missing metrics, seeds, versions, baselines, or numeric results. | `major` | appears grounded in closed-source task protocol |  |  |  |

### Inference-Boundary Checks

| Item | Requirement | Origin | Strictness flag | Human decision | Human note | Required change |
|---|---|---|---|---|---|---|
| `B1` | Use only the packet as evidence. | `task-derived` | not obviously too strict |  |  |  |
| `B2` | Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | `evaluator-derived` | not obviously too strict |  |  |  |
| `B3` | Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | `evaluator-derived` | could be too strict if applied to harmless background context |  |  |  |
