# Validation Human Review Queue

## ERA-VAL-01

### Source Files To Inspect
- `ERA-VAL-01/canonical_sources/brown_2020_language_models_are_few_shot_learners.pdf`: Language Models are Few-Shot Learners (arXiv:2005.14165)
- `ERA-VAL-01/canonical_sources/hendrycks_2021_measuring_massive_multitask_language_understanding.pdf`: Measuring Massive Multitask Language Understanding (arXiv:2009.03300)

### Highest-Priority Must-Capture Entries
- `ERA-VAL-01-M1` (high): Identifies benchmark scores as protocol-bound evidence rather than self-validating capability proof. Evidence to verify: GPT-3 PDF p.1 Abstract; evaluation/result sections; test-set contamination analysis section/appendix; MMLU PDF p.1 Abstract and benchmark/evaluation sections.
- `ERA-VAL-01-M2` (high): Audits contamination, benchmark exposure, prompt protocol, baseline choice, uncertainty, and reproducibility controls. Evidence to verify: GPT-3 contamination analysis section/appendix; MMLU evaluation protocol and benchmark construction sections.
- `ERA-VAL-01-M3` (medium): Separates source-reported contamination analysis from additional contamination risks requiring follow-up evidence. Evidence to verify: GPT-3 and MMLU result tables/figures and limitations/discussion sections.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## ERA-VAL-02

### Source Files To Inspect
- `ERA-VAL-02/canonical_sources/ho_2020_denoising_diffusion_probabilistic_models.pdf`: Denoising Diffusion Probabilistic Models (arXiv:2006.11239)
- `ERA-VAL-02/canonical_sources/nichol_2021_improved_ddpm.pdf`: Improved Denoising Diffusion Probabilistic Models (arXiv:2102.09672)

### Highest-Priority Must-Capture Entries
- `ERA-VAL-02-M1` (high): Identifies quality/diversity/likelihood/speed claims and ties them to the metrics actually reported. Evidence to verify: DDPM PDF p.1 Abstract and experiments section; Improved DDPM PDF p.1 Abstract and evaluation sections.
- `ERA-VAL-02-M2` (high): Audits baselines, sample selection, human/subjective evaluation if present, ablations, compute, and dataset scope. Evidence to verify: Improved DDPM metric/result tables and precision/recall or sample-quality discussion; DDPM sample-quality/likelihood result sections.
- `ERA-VAL-02-M3` (medium): Separates visual sample evidence from quantitative metric evidence and stated limitations. Evidence to verify: DDPM and Improved DDPM experiment sections, ablation/result tables, sample figures, and discussion/limitations.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## LS-VAL-01

### Source Files To Inspect
- `LS-VAL-01/canonical_sources/song_2020_denoising_diffusion_implicit_models.pdf`: Denoising Diffusion Implicit Models (arXiv:2010.02502)
- `LS-VAL-01/canonical_sources/salimans_2022_progressive_distillation.pdf`: Progressive Distillation for Fast Sampling of Diffusion Models (arXiv:2202.00512)
- `LS-VAL-01/canonical_sources/lu_2022_dpm_solver.pdf`: DPM-Solver: A Fast ODE Solver for Diffusion Probabilistic Model Sampling in Around 10 Steps (arXiv:2206.00927)
- `LS-VAL-01/canonical_sources/rombach_2022_latent_diffusion_models.pdf`: High-Resolution Image Synthesis with Latent Diffusion Models (arXiv:2112.10752)
- `LS-VAL-01/canonical_sources/song_2023_consistency_models.pdf`: Consistency Models (arXiv:2303.01469)

### Highest-Priority Must-Capture Entries
- `LS-VAL-01-M1` (high): Accounts for every paper in the fixed corpus. Evidence to verify: All five canonical PDFs p.1 Abstracts and method overview sections.
- `LS-VAL-01-M2` (high): Separates solver/sampler acceleration, distillation, latent-space modeling, and consistency/few-step generation lines where supported. Evidence to verify: DDIM method/experiment sections; Progressive Distillation method/experiment sections; DPM-Solver method/experiment sections; Latent Diffusion method/experiment sections; Consistency Models method/experiment sections.
- `LS-VAL-01-M3` (medium): Links speed-quality tradeoffs to metrics, datasets, sampling steps, model settings, and scope. Evidence to verify: Result tables/figures reporting sampling steps, quality metrics, speed, or compute tradeoffs in each canonical source.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## LS-VAL-02

### Source Files To Inspect
- `LS-VAL-02/canonical_sources/wei_2022_chain_of_thought_prompting.pdf`: Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (arXiv:2201.11903)
- `LS-VAL-02/canonical_sources/kojima_2022_large_language_models_are_zero_shot_reasoners.pdf`: Large Language Models are Zero-Shot Reasoners (arXiv:2205.11916)
- `LS-VAL-02/canonical_sources/turpin_2023_unfaithful_explanations_cot.pdf`: Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting (arXiv:2305.04388)
- `LS-VAL-02/canonical_sources/lanham_2023_measuring_faithfulness_cot.pdf`: Measuring Faithfulness in Chain-of-Thought Reasoning (arXiv:2307.13702)

### Highest-Priority Must-Capture Entries
- `LS-VAL-02-M1` (high): Accounts for supportive and skeptical papers in the fixed corpus. Evidence to verify: All four canonical PDFs p.1 Abstracts and evaluation/method sections.
- `LS-VAL-02-M2` (high): Distinguishes behavioral reasoning performance, rationale generation, faithfulness evidence, intervention/perturbation evidence, and speculative internal reasoning claims. Evidence to verify: CoT and Zero-shot CoT evaluation sections; Unfaithful Explanations experiment sections; Measuring Faithfulness experiment/intervention sections.
- `LS-VAL-02-M3` (medium): Includes skeptical or alternative-explanation evidence rather than organizing around an assumed latent-reasoning thesis. Evidence to verify: Unfaithful Explanations discussion/results; Measuring Faithfulness results and limitations/discussion.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## MC-VAL-01

### Source Files To Inspect
- `MC-VAL-01/canonical_sources/schulman_2017_proximal_policy_optimization_algorithms.pdf`: Proximal Policy Optimization Algorithms (arXiv:1707.06347)
- `MC-VAL-01/canonical_sources/haarnoja_2018_soft_actor_critic.pdf`: Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor (arXiv:1801.01290)

### Highest-Priority Must-Capture Entries
- `MC-VAL-01-M1` (high): Correctly distinguishes PPO on-policy policy-gradient assumptions from SAC off-policy maximum-entropy actor-critic assumptions. Evidence to verify: PPO PDF p.1 Abstract, Section 3 clipped surrogate objective, Section 4 KL variant, Algorithm 1; SAC PDF p.1 Abstract and method/objective sections.
- `MC-VAL-01-M2` (high): Compares continuous-control evidence only within compatible environment, metric, seed, and tuning settings. Evidence to verify: PPO and SAC experiment sections, continuous-control benchmark tables/figures, and implementation/details sections where supplied.
- `MC-VAL-01-M3` (medium): Avoids universal PPO-over-SAC or SAC-over-PPO claims. Evidence to verify: PPO and SAC result tables, benchmark protocol descriptions, and discussion/limitations.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## MC-VAL-02

### Source Files To Inspect
- `MC-VAL-02/canonical_sources/he_2015_deep_residual_learning.pdf`: Deep Residual Learning for Image Recognition (arXiv:1512.03385)
- `MC-VAL-02/canonical_sources/dosovitskiy_2020_vit.pdf`: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (arXiv:2010.11929)
- `MC-VAL-02/canonical_sources/liu_2022_convnet_for_the_2020s.pdf`: A ConvNet for the 2020s (arXiv:2201.03545)

### Highest-Priority Must-Capture Entries
- `MC-VAL-02-M1` (high): Identifies architecture and inductive-bias differences without attributing all performance differences to architecture alone. Evidence to verify: ResNet PDF p.1 Abstract and architecture sections; ViT PDF p.1 Abstract and architecture/data-scale sections; ConvNeXt PDF p.1 Abstract and modernization/training-recipe sections.
- `MC-VAL-02-M2` (high): Audits data scale, pretraining, augmentation, compute, training recipe, and benchmark comparability. Evidence to verify: ViT data/pretraining/evaluation sections; ConvNeXt training recipe and ablation sections; ResNet ImageNet/CIFAR experiment sections.
- `MC-VAL-02-M3` (medium): Limits conclusions about transfer, robustness, or scaling to packet-supported settings. Evidence to verify: Result tables/figures and discussion/limitations from ResNet, ViT, and ConvNeXt canonical PDFs.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## PS-VAL-01

### Source Files To Inspect
- `PS-VAL-01/canonical_sources/hafner_2019_dream_to_control.pdf`: Dream to Control: Learning Behaviors by Latent Imagination (arXiv:1912.01603)
- `PS-VAL-01/canonical_sources/hafner_2020_mastering_atari_discrete_world_models.pdf`: Mastering Atari with Discrete World Models (arXiv:2010.02193)
- `PS-VAL-01/canonical_sources/local_seed_world_model_planning.md`: local_seed_world_model_planning.md (local_seed_brief)

### Highest-Priority Must-Capture Entries
- `PS-VAL-01-M1` (high): Grounds proposal hypotheses in world-model/planning packet facts and the local seed brief. Evidence to verify: Dream to Control PDF p.1 Abstract and latent world-model/imagination sections; DreamerV2 PDF p.1 Abstract and Atari/world-model sections; local seed brief.
- `PS-VAL-01-M2` (high): Specifies falsifiable predictions, disconfirming outcomes, model-error controls, planning baselines, RL metrics, seeds, and environment details. Evidence to verify: Dream to Control and DreamerV2 experiment sections, baseline tables/figures, and local seed brief.
- `PS-VAL-01-M3` (medium): Separates model-learning quality, planner quality, and policy performance claims. Evidence to verify: World-model method sections, planning/control sections, result tables, and discussion/limitations in the two canonical PDFs.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## PS-VAL-02

### Source Files To Inspect
- `PS-VAL-02/canonical_sources/wang_2022_interpretability_in_the_wild_ioi.pdf`: Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small (arXiv:2211.00593)
- `PS-VAL-02/canonical_sources/meng_2022_locating_and_editing_factual_associations.pdf`: Locating and Editing Factual Associations in GPT (arXiv:2202.05262)
- `PS-VAL-02/canonical_sources/local_mech_interp_claim.md`: local_mech_interp_claim.md (local_seed_brief)

### Highest-Priority Must-Capture Entries
- `PS-VAL-02-M1` (high): Separates descriptive/correlational mechanistic evidence from interventional or causal evidence. Evidence to verify: IOI PDF p.1 Abstract and circuit/intervention sections; ROME PDF p.1 Abstract and causal tracing/model editing sections; local claim brief.
- `PS-VAL-02-M2` (high): Proposes tests with causal interventions, controls, falsification criteria, and alternative explanations. Evidence to verify: IOI ablation/intervention figures/tables; ROME causal tracing and editing result sections.
- `PS-VAL-02-M3` (medium): Limits claims to supplied model family, task, layer, feature, and behavior scope. Evidence to verify: IOI and ROME limitations/discussion plus local claim brief scope.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## RL-VAL-01

### Source Files To Inspect
- `RL-VAL-01/canonical_sources/chua_2018_pets.pdf`: Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models (arXiv:1805.12114)
- `RL-VAL-01/canonical_sources/hafner_2018_planet.pdf`: Learning Latent Dynamics for Planning from Pixels (arXiv:1811.04551)

### Highest-Priority Must-Capture Entries
- `RL-VAL-01-M1` (high): Audits learned dynamics assumptions, planning horizon, model-error accumulation, baselines, seeds, evaluation episodes, and metrics. Evidence to verify: PETS PDF p.1 Abstract and probabilistic dynamics/model predictive control sections; PlaNet PDF p.1 Abstract and latent dynamics/planning sections.
- `RL-VAL-01-M2` (high): Separates planning success, world-model fidelity, sample efficiency, and policy performance. Evidence to verify: PETS and PlaNet experiment sections, baseline tables/figures, environment descriptions, and evaluation protocol sections.
- `RL-VAL-01-M3` (medium): Requires model-free and model-based baselines where packet evidence supports the comparison need. Evidence to verify: PETS/PlaNet model-learning sections, planning horizon/control sections, result tables, and limitations/discussion.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## RL-VAL-02

### Source Files To Inspect
- `RL-VAL-02/canonical_sources/christiano_2017_deep_rl_from_human_preferences.pdf`: Deep Reinforcement Learning from Human Preferences (arXiv:1706.03741)
- `RL-VAL-02/canonical_sources/bai_2022_training_helpful_harmless_assistant_rlhf.pdf`: Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback (arXiv:2204.05862)

### Highest-Priority Must-Capture Entries
- `RL-VAL-02-M1` (high): Audits preference-data collection, reward-model training/validation, policy optimization, and policy evaluation setup. Evidence to verify: Deep RL from Human Preferences PDF p.1 Abstract and preference/reward-predictor sections; Helpful/Harmless RLHF PDF p.1 Abstract and preference model/RLHF sections.
- `RL-VAL-02-M2` (high): Separates reward-model score improvements from human preference, alignment, helpfulness, or deployment claims. Evidence to verify: Preference data, reward model validation, policy optimization, and evaluation sections in both canonical PDFs.
- `RL-VAL-02-M3` (medium): Identifies proxy mismatch, reward hacking, evaluator bias, and train/eval leakage risks. Evidence to verify: Result tables/figures and limitations/discussion covering proxy mismatch, evaluator bias, reward hacking, or evaluation scope where supplied.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## SPR-VAL-01

### Source Files To Inspect
- `SPR-VAL-01/canonical_sources/hafner_2023_mastering_diverse_domains_through_world_models.pdf`: Mastering Diverse Domains through World Models (arXiv:2301.04104)

### Highest-Priority Must-Capture Entries
- `SPR-VAL-01-M1` (high): Captures the world-model objective, policy-learning setup, evaluated domains, baselines, metrics, and reported limitations. Evidence to verify: DreamerV3 PDF p.1 Abstract and method/objective sections.
- `SPR-VAL-01-M2` (high): Separates model-based learning, latent dynamics, planning or imagination, and policy optimization claims. Evidence to verify: DreamerV3 experiment sections, domain/evaluation tables, baseline comparisons, and ablation sections where supplied.
- `SPR-VAL-01-M3` (medium): Marks absent environment versions, wrappers, seeds, episodes, or implementation details as unknown. Evidence to verify: DreamerV3 reproducibility/implementation details, result tables/figures, and limitations/discussion.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.

## SPR-VAL-02

### Source Files To Inspect
- `SPR-VAL-02/canonical_sources/chen_2021_decision_transformer.pdf`: Decision Transformer: Reinforcement Learning via Sequence Modeling (arXiv:2106.01345)

### Highest-Priority Must-Capture Entries
- `SPR-VAL-02-M1` (high): Captures the formulation of reinforcement learning as sequence modeling or conditional trajectory generation. Evidence to verify: Decision Transformer PDF p.1 Abstract and method/formulation sections.
- `SPR-VAL-02-M2` (high): Identifies offline datasets/environments, baselines, metrics, evaluation protocol, and reproducibility details. Evidence to verify: Decision Transformer dataset/environment sections, baseline/metric sections, and experiment tables/figures.
- `SPR-VAL-02-M3` (medium): Does not overstate online-control, planning, imitation, or general RL implications beyond packet evidence. Evidence to verify: Decision Transformer implementation/reproducibility details and limitations/discussion.

### Critical-Error Rules To Confirm
- `E1` (major): Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
- `E2` (major): Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
- `E3` (major): Invents missing metrics, seeds, versions, baselines, or numeric results.

### Ambiguities / Packet Decisions
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.
- Packet leakage sanitization: packet-scope wording sanitized globally; no task-specific leakage edit required after audit.
