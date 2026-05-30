## rl_protocol_audit

The supplied packet supports only a scoped audit of the protocol family, not a full validation of any specific implementation. The sources describe protocols that train reward or preference models from human comparisons, then optimize policies against learned rewards using RLHF-style policy optimization. That supports the broad claim that the protocol is a preference-learning/post-training RL approach, but not a strong claim that it robustly aligns behavior in general.

| Audit area | Status from packet | Risk | Boundary |
|---|---:|---|---|
| Preference data | Human preference comparisons are used in both source notes. | Preference quality, annotator instructions, sampling, disagreement handling, and coverage are not specified. | Supports “learns from comparisons,” not “captures human values broadly.” |
| Reward/preference model | Reward predictors/preference models are trained from comparisons. | Validation details, held-out splits, calibration, uncertainty, adversarial tests, and distribution-shift checks are missing. | Supports “model trained to predict preferences,” not “validated alignment reward.” |
| Policy optimization | Policies are optimized under learned rewards/RLHF. | Optimizer, KL/control constraints, reward normalization, stopping rules, and overoptimization checks are unspecified. | Supports “RL optimized against learned reward,” not “safe optimization.” |
| Evaluation metrics | Sources include evaluations and result tables/figures, but packet lacks exact metrics. | Metric alignment and aggregation cannot be audited. | Any improvement claim must be limited to the reported protocols in the original papers. |
| Baselines | Baseline policies are implied by experiments but not detailed in the packet. | Fairness, strength, tuning, and compute comparability unknown. | No broad superiority claim is justified from packet alone. |
| Human/automated eval | Human preferences and evaluations are included at a high level. | Eval population, prompt/task sampling, blind review, inter-rater reliability, and automated judge validity are unspecified. | Supports existence of evaluation, not robustness. |
| Reward hacking | Learned rewards create proxy-optimization risk. | Packet does not establish systematic reward hacking detection or mitigation. | Alignment claims require explicit overoptimization and failure-mode audits. |

## reward_model_validation_review

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|
| Reward models learn from human preferences. | Preference-learning claim | Preference comparison data and reward model training procedure. | Source notes say both protocols use human preference comparisons/preference models. | Supported at high level. | The protocols train models from preference comparisons. |
| Reward models are valid proxies for alignment. | Benchmark/proxy-validity claim | Held-out validation, calibration, adversarial checks, distribution-shift analysis, and failure-mode evidence. | Not included in packet. | Undersupported. | At most, they are learned preference predictors under the reported data distribution. |
| RLHF improves helpfulness/harmlessness or task behavior. | Improvement claim | Compatible baseline comparison under shared metrics/protocols. | Packet says evaluations and result tables/figures exist, but omits details. | Not auditable from packet. | Only source-specific experimental settings, if original reported comparisons support it. |
| Optimizing learned reward improves alignment. | Causal/alignment claim | Intervention evidence plus controls and mechanism-isolating ablations. | Protocol optimizes policies under learned rewards, but validation details are missing. | Partially supported as optimization of a proxy, not alignment. | “Optimizes behavior toward learned preference model.” |

Required validation elements missing from the packet:

| Validation item | Why it matters |
|---|---|
| Preference split design | Prevents leakage between reward model training and validation. |
| Annotator guidance and demographics | Defines whose preferences are learned. |
| Agreement/disagreement reporting | Distinguishes stable preference signal from noisy labels. |
| Held-out reward model accuracy/calibration | Tests whether the model predicts unseen preferences. |
| Reward model uncertainty | Helps identify low-confidence optimization regions. |
| Adversarial or out-of-distribution prompts/tasks | Tests whether the reward proxy fails outside training support. |
| Overoptimization curves | Detects when policy reward rises while human preference falls. |

## policy_evaluation_checklist

Use this before accepting alignment or preference-learning claims:

| Check | Required evidence |
|---|---|
| Preference data provenance | Source of prompts/tasks, sampling method, annotator instructions, comparison format, label aggregation. |
| Reward model split | Train/validation/test split with leakage controls. |
| Reward model metrics | Accuracy or ranking loss, calibration, uncertainty, subgroup/task breakdowns. |
| Baseline policies | SFT/pre-RL policy, non-RL baseline, prior method baseline, and reward-model-only comparison where relevant. |
| Policy optimizer | RL algorithm, KL penalty or constraint, reward normalization, batch sizes, update counts, stopping criteria. |
| Compute/tuning parity | Comparable search budget across baselines. |
| Human evaluation | Blind randomized comparisons, evaluator count, disagreement, confidence intervals. |
| Automated evaluation | Justification that automated metrics or judges measure the target construct. |
| Per-task reporting | Results before aggregation, especially for helpfulness versus harmlessness tradeoffs. |
| Safety and refusal behavior | Separate metrics for harmlessness, helpfulness, evasiveness, and false refusal. |
| Reward hacking tests | Examples where reward model prefers bad outputs, adversarial prompts, and high-reward low-quality generations. |
| Reproducibility | Code/configs, model versions, prompts, seeds, reward model checkpoints, data documentation. |

## reward_hacking_and_proxy_risk_register

| Severity | Risk | Evidence issue | Consequence | Minimal fix |
|---|---|---|---|---|
| High | Reward overoptimization | Packet does not include overoptimization curves or human eval versus reward score comparison. | Policy may exploit reward model while degrading true preference quality. | Track human preference as a function of RL steps/reward score; stop when human preference plateaus or reverses. |
| High | Preference-model distribution shift | Reward model trained on one comparison distribution may score optimized policy outputs outside that distribution. | High reward may not mean aligned behavior. | Evaluate reward model on outputs from intermediate and final RL policies, including adversarial samples. |
| High | Ambiguous alignment construct | “Helpful/harmless/aligned” are broader than pairwise preference prediction. | Claims may overstate what the reward model measures. | Define target constructs and map each metric to a bounded claim. |
| Medium | Annotator bias or inconsistency | Packet lacks annotator protocol and agreement statistics. | Learned reward may encode unstable or narrow preferences. | Report annotator instructions, aggregation, disagreement, and subgroup/task analyses. |
| Medium | Baseline weakness | Packet lacks baseline identity, tuning, and compute details. | Improvement claims may reflect weak comparisons. | Compare against strong SFT and non-RL baselines under equal evaluation protocols. |
| Medium | Metric aggregation hides tradeoffs | Packet lacks per-task/per-category results. | Helpful gains may mask harmlessness failures, or vice versa. | Report helpfulness and harmlessness separately with per-category breakdowns. |
| Medium | Automated evaluation mismatch | Packet notes evaluations but not metric validity. | Automated scores may not reflect human preference. | Validate automated metrics against blind human comparisons. |
| Low | Reproducibility gaps | Exact numeric values, appendices, and implementation settings are omitted. | Independent verification is difficult from packet alone. | Provide configs, seeds, data schemas, checkpoints, and evaluation prompts. |

## revised_protocol

1. Define claim boundaries before training:
   - Primary claim: the policy is optimized to match a specified preference model trained from a documented comparison dataset.
   - Secondary claim: human evaluators prefer the optimized policy over named baselines under a fixed evaluation protocol.
   - Do not claim broad alignment unless tested across heterogeneous tasks, evaluators, adversarial settings, and distribution shifts.

2. Build and document preference data:
   - Specify prompt/task sampling, annotator pool, instructions, comparison UI, label aggregation, and disagreement handling.
   - Maintain separate reward-model train, validation, and test splits.
   - Include samples from baseline, SFT, intermediate RL, and final RL policies to reduce distribution shift.

3. Validate the reward model before policy optimization:
   - Report held-out preference prediction, calibration, uncertainty, and per-category performance.
   - Test adversarial and out-of-distribution examples.
   - Identify examples where the reward model assigns high scores to clearly poor, evasive, unsafe, or nonsensical outputs.

4. Constrain and monitor RL optimization:
   - Use a documented RL algorithm with KL control against the reference policy.
   - Report reward normalization, update counts, hyperparameters, compute budget, and stopping rules.
   - Track reward score, KL distance, diversity, human preference, and safety metrics across training.

5. Evaluate policies with strong baselines:
   - Compare final policy against pre-RL/SFT policy and other relevant baselines.
   - Use blinded randomized human comparisons with confidence intervals.
   - Report helpfulness and harmlessness separately, plus aggregate results only after per-category reporting.

6. Audit reward hacking:
   - Plot learned reward versus human preference over RL steps.
   - Manually inspect high-reward outputs.
   - Run adversarial prompts and policy-generated edge cases through human review.
   - Treat divergence between reward score and human judgment as a stopping or redesign trigger.

7. Release reproducibility artifacts where possible:
   - Include data documentation, prompt sets, reward model architecture/configuration, policy optimization settings, seeds, evaluation rubrics, and analysis scripts.

Revised supported claim: “Under the specified comparison-data, reward-model, RL-optimization, and evaluation protocol, the post-trained policy is preferred by evaluators over named baselines on the tested task distribution.”

Unsupported from the packet alone: “The protocol solves alignment,” “the reward model captures human values generally,” or “RLHF improvements generalize outside the evaluated settings.”