# Validation Source-Check Workbook

This is a source-check worksheet, not an approval record. It does not approve gold, does not change benchmark files, and does not make any task eligible for scoring.

## ERA-VAL-01

- Task type: `experimental_rigor_audit`
- Topic: LLM benchmark contamination
- Source packet ID: `validation_ERA-VAL-01_packet_v0_draft`

### Manual Source Checks Required

`ERA-VAL-01-M1`, `ERA-VAL-01-M2`, `ERA-VAL-01-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `ERA-VAL-01-M1` | Identifies benchmark scores as protocol-bound evidence rather than self-validating capability proof. | Language Models are Few-Shot Learners; Measuring Massive Multitask Language Understanding | GPT-3 PDF p.1 Abstract; evaluation/result sections; test-set contamination analysis section/appendix; MMLU PDF p.1 Abstract and benchmark/evaluation sections. | Language Models are Few-Shot Learners (arXiv:2005.14165; 2020). Local file: `brown_2020_language_models_are_few_shot_learners.pdf`. Included evidence: Abstract; evaluation/benchmark descriptions; contamination discussion; limitations. Measuring Massive Multitask Language Understanding (arXiv:2009.03300; 2021). Local file: `hendrycks_2021_measuring_massive_mu | `requires_human_source_check` |  |
| `ERA-VAL-01-M2` | Audits contamination, benchmark exposure, prompt protocol, baseline choice, uncertainty, and reproducibility controls. | Language Models are Few-Shot Learners; Measuring Massive Multitask Language Understanding | GPT-3 contamination analysis section/appendix; MMLU evaluation protocol and benchmark construction sections. | Language Models are Few-Shot Learners (arXiv:2005.14165; 2020). Local file: `brown_2020_language_models_are_few_shot_learners.pdf`. Included evidence: Abstract; evaluation/benchmark descriptions; contamination discussion; limitations. Measuring Massive Multitask Language Understanding (arXiv:2009.03300; 2021). Local file: `hendrycks_2021_measuring_massive_mu | `requires_human_source_check` |  |
| `ERA-VAL-01-M3` | Separates source-reported contamination analysis from additional contamination risks requiring follow-up evidence. | Language Models are Few-Shot Learners; Measuring Massive Multitask Language Understanding | GPT-3 and MMLU result tables/figures and limitations/discussion sections. | Language Models are Few-Shot Learners (arXiv:2005.14165; 2020). Local file: `brown_2020_language_models_are_few_shot_learners.pdf`. Included evidence: Abstract; evaluation/benchmark descriptions; contamination discussion; limitations. Measuring Massive Multitask Language Understanding (arXiv:2009.03300; 2021). Local file: `hendrycks_2021_measuring_massive_mu | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## ERA-VAL-02

- Task type: `experimental_rigor_audit`
- Topic: generative model evaluation
- Source packet ID: `validation_ERA-VAL-02_packet_v0_draft`

### Manual Source Checks Required

`ERA-VAL-02-M1`, `ERA-VAL-02-M2`, `ERA-VAL-02-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `ERA-VAL-02-M1` | Identifies quality/diversity/likelihood/speed claims and ties them to the metrics actually reported. | Denoising Diffusion Probabilistic Models; Improved Denoising Diffusion Probabilistic Models | DDPM PDF p.1 Abstract and experiments section; Improved DDPM PDF p.1 Abstract and evaluation sections. | Denoising Diffusion Probabilistic Models (arXiv:2006.11239; 2020). Local file: `ho_2020_denoising_diffusion_probabilistic_models.pdf`. Included evidence: Abstract; experiments; sample quality/likelihood discussion; limitations. Improved Denoising Diffusion Probabilistic Models (arXiv:2102.09672; 2021). Local file: `nichol_2021_improved_ddpm.pdf`. Included ev | `requires_human_source_check` |  |
| `ERA-VAL-02-M2` | Audits baselines, sample selection, human/subjective evaluation if present, ablations, compute, and dataset scope. | Denoising Diffusion Probabilistic Models; Improved Denoising Diffusion Probabilistic Models | Improved DDPM metric/result tables and precision/recall or sample-quality discussion; DDPM sample-quality/likelihood result sections. | Denoising Diffusion Probabilistic Models (arXiv:2006.11239; 2020). Local file: `ho_2020_denoising_diffusion_probabilistic_models.pdf`. Included evidence: Abstract; experiments; sample quality/likelihood discussion; limitations. Improved Denoising Diffusion Probabilistic Models (arXiv:2102.09672; 2021). Local file: `nichol_2021_improved_ddpm.pdf`. Included ev | `requires_human_source_check` |  |
| `ERA-VAL-02-M3` | Separates visual sample evidence from quantitative metric evidence and stated limitations. | Denoising Diffusion Probabilistic Models; Improved Denoising Diffusion Probabilistic Models | DDPM and Improved DDPM experiment sections, ablation/result tables, sample figures, and discussion/limitations. | Denoising Diffusion Probabilistic Models (arXiv:2006.11239; 2020). Local file: `ho_2020_denoising_diffusion_probabilistic_models.pdf`. Included evidence: Abstract; experiments; sample quality/likelihood discussion; limitations. Improved Denoising Diffusion Probabilistic Models (arXiv:2102.09672; 2021). Local file: `nichol_2021_improved_ddpm.pdf`. Included ev | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## LS-VAL-01

- Task type: `literature_mapping`
- Topic: diffusion and generative modeling efficiency
- Source packet ID: `validation_LS-VAL-01_packet_v0_draft`

### Manual Source Checks Required

`LS-VAL-01-M1`, `LS-VAL-01-M2`, `LS-VAL-01-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `LS-VAL-01-M1` | Accounts for every paper in the fixed corpus. | Denoising Diffusion Implicit Models; Progressive Distillation for Fast Sampling of Diffusion Models; DPM-Solver: A Fast ODE Solver for Diffusion Probabilistic Model Sampling in Around 10 Steps; High-Resolution Image Synthesis with Latent Diffusion Models; Consistency Models | All five canonical PDFs p.1 Abstracts and method overview sections. | Denoising Diffusion Implicit Models (arXiv:2010.02502; 2020). Local file: `song_2020_denoising_diffusion_implicit_models.pdf`. Included evidence: Abstract; sampling acceleration method; experiments; limitations. Progressive Distillation for Fast Sampling of Diffusion Models (arXiv:2202.00512; 2022). Local file: `salimans_2022_progressive_distillation.pdf`. I | `requires_human_source_check` |  |
| `LS-VAL-01-M2` | Separates solver/sampler acceleration, distillation, latent-space modeling, and consistency/few-step generation lines where supported. | Denoising Diffusion Implicit Models; Progressive Distillation for Fast Sampling of Diffusion Models; DPM-Solver: A Fast ODE Solver for Diffusion Probabilistic Model Sampling in Around 10 Steps; High-Resolution Image Synthesis with Latent Diffusion Models; Consistency Models | DDIM method/experiment sections; Progressive Distillation method/experiment sections; DPM-Solver method/experiment sections; Latent Diffusion method/experiment sections; Consistency Models method/experiment sections. | Denoising Diffusion Implicit Models (arXiv:2010.02502; 2020). Local file: `song_2020_denoising_diffusion_implicit_models.pdf`. Included evidence: Abstract; sampling acceleration method; experiments; limitations. Progressive Distillation for Fast Sampling of Diffusion Models (arXiv:2202.00512; 2022). Local file: `salimans_2022_progressive_distillation.pdf`. I | `requires_human_source_check` |  |
| `LS-VAL-01-M3` | Links speed-quality tradeoffs to metrics, datasets, sampling steps, model settings, and scope. | Denoising Diffusion Implicit Models; Progressive Distillation for Fast Sampling of Diffusion Models; DPM-Solver: A Fast ODE Solver for Diffusion Probabilistic Model Sampling in Around 10 Steps; High-Resolution Image Synthesis with Latent Diffusion Models; Consistency Models | Result tables/figures reporting sampling steps, quality metrics, speed, or compute tradeoffs in each canonical source. | Denoising Diffusion Implicit Models (arXiv:2010.02502; 2020). Local file: `song_2020_denoising_diffusion_implicit_models.pdf`. Included evidence: Abstract; sampling acceleration method; experiments; limitations. Progressive Distillation for Fast Sampling of Diffusion Models (arXiv:2202.00512; 2022). Local file: `salimans_2022_progressive_distillation.pdf`. I | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## LS-VAL-02

- Task type: `literature_mapping`
- Topic: latent reasoning in language models
- Source packet ID: `validation_LS-VAL-02_packet_v0_draft`

### Manual Source Checks Required

`LS-VAL-02-M1`, `LS-VAL-02-M2`, `LS-VAL-02-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `LS-VAL-02-M1` | Accounts for supportive and skeptical papers in the fixed corpus. | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models; Large Language Models are Zero-Shot Reasoners; Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting; Measuring Faithfulness in Chain-of-Thought Reasoning | All four canonical PDFs p.1 Abstracts and evaluation/method sections. | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (arXiv:2201.11903; 2022). Local file: `wei_2022_chain_of_thought_prompting.pdf`. Included evidence: Abstract; prompting/evaluation results; limitations. Large Language Models are Zero-Shot Reasoners (arXiv:2205.11916; 2022). Local file: `kojima_2022_large_language_models_are_zero_shot_reas | `requires_human_source_check` |  |
| `LS-VAL-02-M2` | Distinguishes behavioral reasoning performance, rationale generation, faithfulness evidence, intervention/perturbation evidence, and speculative internal reasoning claims. | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models; Large Language Models are Zero-Shot Reasoners; Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting; Measuring Faithfulness in Chain-of-Thought Reasoning | CoT and Zero-shot CoT evaluation sections; Unfaithful Explanations experiment sections; Measuring Faithfulness experiment/intervention sections. | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (arXiv:2201.11903; 2022). Local file: `wei_2022_chain_of_thought_prompting.pdf`. Included evidence: Abstract; prompting/evaluation results; limitations. Large Language Models are Zero-Shot Reasoners (arXiv:2205.11916; 2022). Local file: `kojima_2022_large_language_models_are_zero_shot_reas | `requires_human_source_check` |  |
| `LS-VAL-02-M3` | Includes skeptical or alternative-explanation evidence rather than organizing around an assumed latent-reasoning thesis. | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models; Large Language Models are Zero-Shot Reasoners; Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting; Measuring Faithfulness in Chain-of-Thought Reasoning | Unfaithful Explanations discussion/results; Measuring Faithfulness results and limitations/discussion. | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (arXiv:2201.11903; 2022). Local file: `wei_2022_chain_of_thought_prompting.pdf`. Included evidence: Abstract; prompting/evaluation results; limitations. Large Language Models are Zero-Shot Reasoners (arXiv:2205.11916; 2022). Local file: `kojima_2022_large_language_models_are_zero_shot_reas | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## MC-VAL-01

- Task type: `method_comparison`
- Topic: policy optimization
- Source packet ID: `validation_MC-VAL-01_packet_v0_draft`

### Manual Source Checks Required

`MC-VAL-01-M1`, `MC-VAL-01-M2`, `MC-VAL-01-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `MC-VAL-01-M1` | Correctly distinguishes PPO on-policy policy-gradient assumptions from SAC off-policy maximum-entropy actor-critic assumptions. | Proximal Policy Optimization Algorithms; Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor | PPO PDF p.1 Abstract, Section 3 clipped surrogate objective, Section 4 KL variant, Algorithm 1; SAC PDF p.1 Abstract and method/objective sections. | Proximal Policy Optimization Algorithms (arXiv:1707.06347; 2017). Local file: `schulman_2017_proximal_policy_optimization_algorithms.pdf`. Included evidence: Abstract; clipped objective; adaptive KL; experiments. Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor (arXiv:1801.01290; 2018). Local file: `haarnoja_2 | `requires_human_source_check` |  |
| `MC-VAL-01-M2` | Compares continuous-control evidence only within compatible environment, metric, seed, and tuning settings. | Proximal Policy Optimization Algorithms; Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor | PPO and SAC experiment sections, continuous-control benchmark tables/figures, and implementation/details sections where supplied. | Proximal Policy Optimization Algorithms (arXiv:1707.06347; 2017). Local file: `schulman_2017_proximal_policy_optimization_algorithms.pdf`. Included evidence: Abstract; clipped objective; adaptive KL; experiments. Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor (arXiv:1801.01290; 2018). Local file: `haarnoja_2 | `requires_human_source_check` |  |
| `MC-VAL-01-M3` | Avoids universal PPO-over-SAC or SAC-over-PPO claims. | Proximal Policy Optimization Algorithms; Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor | PPO and SAC result tables, benchmark protocol descriptions, and discussion/limitations. | Proximal Policy Optimization Algorithms (arXiv:1707.06347; 2017). Local file: `schulman_2017_proximal_policy_optimization_algorithms.pdf`. Included evidence: Abstract; clipped objective; adaptive KL; experiments. Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor (arXiv:1801.01290; 2018). Local file: `haarnoja_2 | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## MC-VAL-02

- Task type: `method_comparison`
- Topic: visual representation learning
- Source packet ID: `validation_MC-VAL-02_packet_v0_draft`

### Manual Source Checks Required

`MC-VAL-02-M1`, `MC-VAL-02-M2`, `MC-VAL-02-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `MC-VAL-02-M1` | Identifies architecture and inductive-bias differences without attributing all performance differences to architecture alone. | Deep Residual Learning for Image Recognition; An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale; A ConvNet for the 2020s | ResNet PDF p.1 Abstract and architecture sections; ViT PDF p.1 Abstract and architecture/data-scale sections; ConvNeXt PDF p.1 Abstract and modernization/training-recipe sections. | Deep Residual Learning for Image Recognition (arXiv:1512.03385; 2015). Local file: `he_2015_deep_residual_learning.pdf`. Included evidence: Abstract; architecture; ImageNet/CIFAR experiments. An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (arXiv:2010.11929; 2020). Local file: `dosovitskiy_2020_vit.pdf`. Included evidence: Abstract | `requires_human_source_check` |  |
| `MC-VAL-02-M2` | Audits data scale, pretraining, augmentation, compute, training recipe, and benchmark comparability. | Deep Residual Learning for Image Recognition; An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale; A ConvNet for the 2020s | ViT data/pretraining/evaluation sections; ConvNeXt training recipe and ablation sections; ResNet ImageNet/CIFAR experiment sections. | Deep Residual Learning for Image Recognition (arXiv:1512.03385; 2015). Local file: `he_2015_deep_residual_learning.pdf`. Included evidence: Abstract; architecture; ImageNet/CIFAR experiments. An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (arXiv:2010.11929; 2020). Local file: `dosovitskiy_2020_vit.pdf`. Included evidence: Abstract | `requires_human_source_check` |  |
| `MC-VAL-02-M3` | Limits conclusions about transfer, robustness, or scaling to packet-supported settings. | Deep Residual Learning for Image Recognition; An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale; A ConvNet for the 2020s | Result tables/figures and discussion/limitations from ResNet, ViT, and ConvNeXt canonical PDFs. | Deep Residual Learning for Image Recognition (arXiv:1512.03385; 2015). Local file: `he_2015_deep_residual_learning.pdf`. Included evidence: Abstract; architecture; ImageNet/CIFAR experiments. An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (arXiv:2010.11929; 2020). Local file: `dosovitskiy_2020_vit.pdf`. Included evidence: Abstract | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## PS-VAL-01

- Task type: `evidence_grounded_proposal_support`
- Topic: world-model planning
- Source packet ID: `validation_PS-VAL-01_packet_v0_draft`

### Manual Source Checks Required

`PS-VAL-01-M1`, `PS-VAL-01-M2`, `PS-VAL-01-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `PS-VAL-01-M1` | Grounds proposal hypotheses in world-model/planning packet facts and the local seed brief. | Dream to Control: Learning Behaviors by Latent Imagination; Mastering Atari with Discrete World Models; local_seed_world_model_planning.md | Dream to Control PDF p.1 Abstract and latent world-model/imagination sections; DreamerV2 PDF p.1 Abstract and Atari/world-model sections; local seed brief. | Dream to Control: Learning Behaviors by Latent Imagination (arXiv:1912.01603; 2019). Local file: `hafner_2019_dream_to_control.pdf`. Included evidence: Abstract; latent world model; imagination/planning/control; experiments. Mastering Atari with Discrete World Models (arXiv:2010.02193; 2020). Local file: `hafner_2020_mastering_atari_discrete_world_models.pdf | `requires_human_source_check` |  |
| `PS-VAL-01-M2` | Specifies falsifiable predictions, disconfirming outcomes, model-error controls, planning baselines, RL metrics, seeds, and environment details. | Dream to Control: Learning Behaviors by Latent Imagination; Mastering Atari with Discrete World Models; local_seed_world_model_planning.md | Dream to Control and DreamerV2 experiment sections, baseline tables/figures, and local seed brief. | Dream to Control: Learning Behaviors by Latent Imagination (arXiv:1912.01603; 2019). Local file: `hafner_2019_dream_to_control.pdf`. Included evidence: Abstract; latent world model; imagination/planning/control; experiments. Mastering Atari with Discrete World Models (arXiv:2010.02193; 2020). Local file: `hafner_2020_mastering_atari_discrete_world_models.pdf | `requires_human_source_check` |  |
| `PS-VAL-01-M3` | Separates model-learning quality, planner quality, and policy performance claims. | Dream to Control: Learning Behaviors by Latent Imagination; Mastering Atari with Discrete World Models; local_seed_world_model_planning.md | World-model method sections, planning/control sections, result tables, and discussion/limitations in the two canonical PDFs. | Dream to Control: Learning Behaviors by Latent Imagination (arXiv:1912.01603; 2019). Local file: `hafner_2019_dream_to_control.pdf`. Included evidence: Abstract; latent world model; imagination/planning/control; experiments. Mastering Atari with Discrete World Models (arXiv:2010.02193; 2020). Local file: `hafner_2020_mastering_atari_discrete_world_models.pdf | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## PS-VAL-02

- Task type: `evidence_grounded_proposal_support`
- Topic: mechanistic interpretability
- Source packet ID: `validation_PS-VAL-02_packet_v0_draft`

### Manual Source Checks Required

`PS-VAL-02-M1`, `PS-VAL-02-M2`, `PS-VAL-02-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `PS-VAL-02-M1` | Separates descriptive/correlational mechanistic evidence from interventional or causal evidence. | Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small; Locating and Editing Factual Associations in GPT; local_mech_interp_claim.md | IOI PDF p.1 Abstract and circuit/intervention sections; ROME PDF p.1 Abstract and causal tracing/model editing sections; local claim brief. | Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small (arXiv:2211.00593; 2022). Local file: `wang_2022_interpretability_in_the_wild_ioi.pdf`. Included evidence: Abstract; circuit analysis; interventions/ablations; limitations. Locating and Editing Factual Associations in GPT (arXiv:2202.05262; 2022). Local file: `meng_2022 | `requires_human_source_check` |  |
| `PS-VAL-02-M2` | Proposes tests with causal interventions, controls, falsification criteria, and alternative explanations. | Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small; Locating and Editing Factual Associations in GPT; local_mech_interp_claim.md | IOI ablation/intervention figures/tables; ROME causal tracing and editing result sections. | Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small (arXiv:2211.00593; 2022). Local file: `wang_2022_interpretability_in_the_wild_ioi.pdf`. Included evidence: Abstract; circuit analysis; interventions/ablations; limitations. Locating and Editing Factual Associations in GPT (arXiv:2202.05262; 2022). Local file: `meng_2022 | `requires_human_source_check` |  |
| `PS-VAL-02-M3` | Limits claims to supplied model family, task, layer, feature, and behavior scope. | Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small; Locating and Editing Factual Associations in GPT; local_mech_interp_claim.md | IOI and ROME limitations/discussion plus local claim brief scope. | Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small (arXiv:2211.00593; 2022). Local file: `wang_2022_interpretability_in_the_wild_ioi.pdf`. Included evidence: Abstract; circuit analysis; interventions/ablations; limitations. Locating and Editing Factual Associations in GPT (arXiv:2202.05262; 2022). Local file: `meng_2022 | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## RL-VAL-01

- Task type: `rl_specific_analysis`
- Topic: model-based reinforcement learning
- Source packet ID: `validation_RL-VAL-01_packet_v0_draft`

### Manual Source Checks Required

`RL-VAL-01-M1`, `RL-VAL-01-M2`, `RL-VAL-01-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `RL-VAL-01-M1` | Audits learned dynamics assumptions, planning horizon, model-error accumulation, baselines, seeds, evaluation episodes, and metrics. | Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models; Learning Latent Dynamics for Planning from Pixels | PETS PDF p.1 Abstract and probabilistic dynamics/model predictive control sections; PlaNet PDF p.1 Abstract and latent dynamics/planning sections. | Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models (arXiv:1805.12114; 2018). Local file: `chua_2018_pets.pdf`. Included evidence: Abstract; probabilistic ensembles; model predictive control; experiments. Learning Latent Dynamics for Planning from Pixels (arXiv:1811.04551; 2018). Local file: `hafner_2018_planet.pdf`. Includ | `requires_human_source_check` |  |
| `RL-VAL-01-M2` | Separates planning success, world-model fidelity, sample efficiency, and policy performance. | Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models; Learning Latent Dynamics for Planning from Pixels | PETS and PlaNet experiment sections, baseline tables/figures, environment descriptions, and evaluation protocol sections. | Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models (arXiv:1805.12114; 2018). Local file: `chua_2018_pets.pdf`. Included evidence: Abstract; probabilistic ensembles; model predictive control; experiments. Learning Latent Dynamics for Planning from Pixels (arXiv:1811.04551; 2018). Local file: `hafner_2018_planet.pdf`. Includ | `requires_human_source_check` |  |
| `RL-VAL-01-M3` | Requires model-free and model-based baselines where packet evidence supports the comparison need. | Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models; Learning Latent Dynamics for Planning from Pixels | PETS/PlaNet model-learning sections, planning horizon/control sections, result tables, and limitations/discussion. | Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models (arXiv:1805.12114; 2018). Local file: `chua_2018_pets.pdf`. Included evidence: Abstract; probabilistic ensembles; model predictive control; experiments. Learning Latent Dynamics for Planning from Pixels (arXiv:1811.04551; 2018). Local file: `hafner_2018_planet.pdf`. Includ | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## RL-VAL-02

- Task type: `rl_specific_analysis`
- Topic: reward modeling and post-training RL
- Source packet ID: `validation_RL-VAL-02_packet_v0_draft`

### Manual Source Checks Required

`RL-VAL-02-M1`, `RL-VAL-02-M2`, `RL-VAL-02-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `RL-VAL-02-M1` | Audits preference-data collection, reward-model training/validation, policy optimization, and policy evaluation setup. | Deep Reinforcement Learning from Human Preferences; Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback | Deep RL from Human Preferences PDF p.1 Abstract and preference/reward-predictor sections; Helpful/Harmless RLHF PDF p.1 Abstract and preference model/RLHF sections. | Deep Reinforcement Learning from Human Preferences (arXiv:1706.03741; 2017). Local file: `christiano_2017_deep_rl_from_human_preferences.pdf`. Included evidence: Abstract; preference data; reward predictor; policy optimization; experiments. Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback (arXiv:2204.05862; 2022). Loc | `requires_human_source_check` |  |
| `RL-VAL-02-M2` | Separates reward-model score improvements from human preference, alignment, helpfulness, or deployment claims. | Deep Reinforcement Learning from Human Preferences; Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback | Preference data, reward model validation, policy optimization, and evaluation sections in both canonical PDFs. | Deep Reinforcement Learning from Human Preferences (arXiv:1706.03741; 2017). Local file: `christiano_2017_deep_rl_from_human_preferences.pdf`. Included evidence: Abstract; preference data; reward predictor; policy optimization; experiments. Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback (arXiv:2204.05862; 2022). Loc | `requires_human_source_check` |  |
| `RL-VAL-02-M3` | Identifies proxy mismatch, reward hacking, evaluator bias, and train/eval leakage risks. | Deep Reinforcement Learning from Human Preferences; Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback | Result tables/figures and limitations/discussion covering proxy mismatch, evaluator bias, reward hacking, or evaluation scope where supplied. | Deep Reinforcement Learning from Human Preferences (arXiv:1706.03741; 2017). Local file: `christiano_2017_deep_rl_from_human_preferences.pdf`. Included evidence: Abstract; preference data; reward predictor; policy optimization; experiments. Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback (arXiv:2204.05862; 2022). Loc | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## SPR-VAL-01

- Task type: `single_paper_deep_reading`
- Topic: world models
- Source packet ID: `validation_SPR-VAL-01_packet_v0_draft`

### Manual Source Checks Required

`SPR-VAL-01-M1`, `SPR-VAL-01-M2`, `SPR-VAL-01-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `SPR-VAL-01-M1` | Captures the world-model objective, policy-learning setup, evaluated domains, baselines, metrics, and reported limitations. | Mastering Diverse Domains through World Models | DreamerV3 PDF p.1 Abstract and method/objective sections. | Mastering Diverse Domains through World Models (arXiv:2301.04104; 2023). Local file: `hafner_2023_mastering_diverse_domains_through_world_models.pdf`. Included evidence: Abstract; method/objective; domains; baselines; experiments; limitations. DreamerV3 paper: presents a world-model agent intended to work across diverse domains and reports benchmark performa | `requires_human_source_check` |  |
| `SPR-VAL-01-M2` | Separates model-based learning, latent dynamics, planning or imagination, and policy optimization claims. | Mastering Diverse Domains through World Models | DreamerV3 experiment sections, domain/evaluation tables, baseline comparisons, and ablation sections where supplied. | Mastering Diverse Domains through World Models (arXiv:2301.04104; 2023). Local file: `hafner_2023_mastering_diverse_domains_through_world_models.pdf`. Included evidence: Abstract; method/objective; domains; baselines; experiments; limitations. DreamerV3 paper: presents a world-model agent intended to work across diverse domains and reports benchmark performa | `requires_human_source_check` |  |
| `SPR-VAL-01-M3` | Marks absent environment versions, wrappers, seeds, episodes, or implementation details as unknown. | Mastering Diverse Domains through World Models | DreamerV3 reproducibility/implementation details, result tables/figures, and limitations/discussion. | Mastering Diverse Domains through World Models (arXiv:2301.04104; 2023). Local file: `hafner_2023_mastering_diverse_domains_through_world_models.pdf`. Included evidence: Abstract; method/objective; domains; baselines; experiments; limitations. DreamerV3 paper: presents a world-model agent intended to work across diverse domains and reports benchmark performa | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |

## SPR-VAL-02

- Task type: `single_paper_deep_reading`
- Topic: sequence modeling for reinforcement learning
- Source packet ID: `validation_SPR-VAL-02_packet_v0_draft`

### Manual Source Checks Required

`SPR-VAL-02-M1`, `SPR-VAL-02-M2`, `SPR-VAL-02-M3`

### Source-Check Table

| Item | Gold claim | Canonical source | Page / section / table / figure | Packet/source excerpt available | Evidence appears sufficient | Human decision |
|---|---|---|---|---|---|---|
| `SPR-VAL-02-M1` | Captures the formulation of reinforcement learning as sequence modeling or conditional trajectory generation. | Decision Transformer: Reinforcement Learning via Sequence Modeling | Decision Transformer PDF p.1 Abstract and method/formulation sections. | Decision Transformer: Reinforcement Learning via Sequence Modeling (arXiv:2106.01345; 2021). Local file: `chen_2021_decision_transformer.pdf`. Included evidence: Abstract; method formulation; datasets/environments; baselines; experiments; limitations. Decision Transformer paper: formulates offline reinforcement learning as conditional sequence modeling over  | `requires_human_source_check` |  |
| `SPR-VAL-02-M2` | Identifies offline datasets/environments, baselines, metrics, evaluation protocol, and reproducibility details. | Decision Transformer: Reinforcement Learning via Sequence Modeling | Decision Transformer dataset/environment sections, baseline/metric sections, and experiment tables/figures. | Decision Transformer: Reinforcement Learning via Sequence Modeling (arXiv:2106.01345; 2021). Local file: `chen_2021_decision_transformer.pdf`. Included evidence: Abstract; method formulation; datasets/environments; baselines; experiments; limitations. Decision Transformer paper: formulates offline reinforcement learning as conditional sequence modeling over  | `requires_human_source_check` |  |
| `SPR-VAL-02-M3` | Does not overstate online-control, planning, imitation, or general RL implications beyond packet evidence. | Decision Transformer: Reinforcement Learning via Sequence Modeling | Decision Transformer implementation/reproducibility details and limitations/discussion. | Decision Transformer: Reinforcement Learning via Sequence Modeling (arXiv:2106.01345; 2021). Local file: `chen_2021_decision_transformer.pdf`. Included evidence: Abstract; method formulation; datasets/environments; baselines; experiments; limitations. Decision Transformer paper: formulates offline reinforcement learning as conditional sequence modeling over  | `requires_human_source_check` |  |

### Review Questions

| Item | Question | Reason | Human note |
|---|---|---|---|
| `E1` | Is this critical-error rule fair for core scored claims only? Uses external sources or remembered facts as evidence for a core claim in the closed-source task. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E2` | Is this critical-error rule fair for core scored claims only? Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `E3` | Is this critical-error rule fair for core scored claims only? Invents missing metrics, seeds, versions, baselines, or numeric results. | Generic closed-source scoring rule; no concrete defect proven by workbook. |  |
| `B1` | Is this boundary rule appropriately scoped rather than too strict? Use only the packet as evidence. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B2` | Is this boundary rule appropriately scoped rather than too strict? Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
| `B3` | Is this boundary rule appropriately scoped rather than too strict? Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced. | Generic inference-boundary rule; needs reviewer calibration, not automatic revision. |  |
