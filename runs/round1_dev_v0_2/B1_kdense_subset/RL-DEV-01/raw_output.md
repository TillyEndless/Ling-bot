## rl_protocol_audit

| Risk | Packet evidence | Why it matters for offline RL | Severity | Protocol requirement |
|---|---|---:|---:|---|
| Dataset coverage may not span the claimed behavior regimes | D4RL emphasizes narrow, biased, multitask, suboptimal, and non-representable behavior-policy datasets; Sections 3-5 | Offline RL results are highly dataset-dependent. A method that works on one data regime may fail under another. | High | Report results separately by dataset regime: narrow, biased, multitask, suboptimal, and non-representable behavior-policy settings where available. |
| Behavior policy assumptions are underspecified | D4RL frames fixed datasets and behavior-policy issues in Section 3; CQL targets learned-policy actions unsupported by the dataset, p. 2 and Section 3 | Claims about conservatism, policy improvement, or robustness require knowing what support the logged data provides. | High | State whether the behavior policy is known, unknown, mixture, non-representable, narrow, or suboptimal for each dataset. |
| Train/eval separation is not sufficient unless simulator evaluation is isolated | D4RL uses static datasets for training and simulator-based policy evaluation, p. 7 | Offline training must not use environment interaction; evaluation can use simulator rollouts only after training. | High | Freeze datasets before training; prohibit online data collection, tuning by online return, or environment interaction during training. |
| Normalized score can obscure raw environment performance | D4RL defines normalized scores with task/domain-specific anchors, p. 7; Appendix Tables 1-3 include raw returns and normalized scores | Normalized scores are useful for benchmarking but are not identical to raw return or policy value. | Medium | Report normalized score, raw return, and evaluation episode count. Do not base all claims on normalized score alone. |
| Offline value estimates may be confused with true returns | CQL Table 4 separates estimated policy values and true returns; source notes distinguish normalized score, actual return, and value estimates | Offline policy evaluation claims require special care because estimated values may be biased under distribution shift. | High | Clearly separate learned Q/value estimates, simulator returns, and normalized benchmark scores. |
| Baseline set may be too narrow | CQL compares against prior offline RL methods and behavioral cloning on D4RL, Tables 1-2 | Offline RL methods must beat simple imitation baselines to support policy-improvement claims. | High | Include behavioral cloning and relevant offline RL baselines used in the packet; report per-task comparisons. |
| Seed and uncertainty reporting may be insufficient if only means are reported | CQL Tables 1-2 average over four seeds; Appendix p. 29 gives four-seed details. D4RL Appendix Tables 1-3 include seed-reporting information | Four seeds give some robustness information, but uncertainty must be visible. | Medium | Use at least four seeds to match CQL packet evidence; report mean plus variability, not only averages. |
| Offline-to-online claims may exceed evidence | D4RL and CQL evaluate offline training with simulator-based benchmark evaluation; CQL’s guarantees are under stated assumptions | Strong deployment or online improvement claims are not established by the packet. | High | Limit claims to offline RL benchmark performance under D4RL-style evaluation unless online interaction experiments are added and separated. |

## dataset_and_environment_checklist

| Item | Required audit question | Packet basis | Status needed in revised protocol |
|---|---|---|---|
| Dataset identity | Which exact D4RL task/dataset is used? | D4RL Appendix Tables 1-3 list task identities | Must list every dataset by name. |
| Dataset regime | Is the data narrow, biased, multitask, suboptimal, or from a non-representable behavior policy? | D4RL Sections 4-5 | Must classify each dataset. |
| Static offline data | Is training restricted to fixed logged data? | D4RL Section 3 | Must explicitly freeze the training dataset. |
| Behavior policy | Is the behavior policy known, mixture-based, suboptimal, or not representable? | D4RL Section 3; CQL p. 2 | Must document assumptions per dataset. |
| Environment | What simulator/domain produces evaluation returns? | D4RL benchmark domains and p. 7 evaluation protocol | Must name environment/domain and evaluation setup. |
| Evaluation separation | Are simulator rollouts used only after training? | D4RL offline framing and simulator-based evaluation | Must prohibit evaluation leakage into training/tuning. |
| Normalization | Which reference anchors define normalized score? | D4RL p. 7 | Must state normalized-score formula/anchors as supplied by D4RL. |
| Raw returns | Are actual environment returns reported? | D4RL Appendix Tables 1-3; source notes | Must report raw return alongside normalized score. |

## baseline_and_metric_review

| Category | Minimum acceptable protocol | Evidence basis |
|---|---|---|
| Behavioral cloning baseline | Include BC as a baseline, because it tests whether RL improves over imitation. | CQL compares against behavioral cloning, Tables 1-2. |
| Offline RL baselines | Include prior offline RL methods used in the packet’s D4RL comparisons. | CQL Tables 1-2 compare against prior offline RL methods. |
| Per-domain reporting | Report results separately for Gym, AntMaze, Adroit, Kitchen, and Atari only if those are included. | CQL Tables 1-3 report these domains. |
| Normalized score | Use D4RL normalized-score conventions. | D4RL p. 7. |
| Raw environment return | Report raw simulator return in addition to normalized score. | D4RL Appendix Tables 1-3 and source notes. |
| Offline value estimate | If reporting Q/value estimates, label them separately from true returns. | CQL Table 4. |
| Seeds | Use at least four seeds and state seed count. | CQL Tables 1-2 and Appendix p. 29. |
| Uncertainty | Report variability across seeds. | Seed averaging alone is only partial support; uncertainty is needed for claim strength. |

## claim_scope_assessment

| Proposed claim type | Supported by packet if protocol does this | Not established by packet |
|---|---|---|
| “The method improves D4RL benchmark performance” | Supported if it reports D4RL normalized scores and raw returns, with baselines and seed variability. | Not supported if based only on one dataset, one seed, or value estimates. |
| “The method handles offline distribution shift” | Partially supported if evaluated across dataset regimes with unsupported-action risk, following CQL-style motivation. | Not established as a general property without behavior-support analysis and multiple dataset regimes. |
| “The method is conservative / avoids overestimation” | Supported only if value estimates are compared with true returns or equivalent conservative-value analysis. | Not established from normalized return alone. |
| “The method is robust across offline RL settings” | Supported only across the included D4RL domains and dataset types. | Not established field-wide from the packet. |
| “The method will work online or in deployment” | Not supported by the supplied packet unless a separate online protocol is added. | Offline-to-online generalization is not established by D4RL/CQL evidence alone. |
| “The method is state of the art” | Not established by the packet. | Requires external comparison beyond the closed packet. |

## revised_protocol

1. **Dataset declaration**
   List every D4RL dataset and task used. For each one, record domain, dataset regime, behavior-policy assumption, whether the policy is known or unknown, and whether the dataset is narrow, biased, multitask, suboptimal, or potentially non-representable.

2. **Offline training constraint**
   Train only on the fixed static dataset. No simulator interaction, online data collection, evaluation-return tuning, or environment-based early stopping is allowed during training.

3. **Train/eval separation**
   Use simulator rollouts only for final evaluation. Hyperparameters must be selected without using online evaluation returns unless a separate validation protocol is explicitly defined and reported.

4. **Baselines**
   Include behavioral cloning and prior offline RL baselines comparable to those used in CQL’s D4RL evaluation. Report all baselines under the same dataset, environment, seed, and metric protocol.

5. **Metrics**
   For every task, report:
   - D4RL normalized score using the benchmark convention.
   - Raw environment return.
   - Seed mean and variability.
   - Number of evaluation episodes, if available.
   - Offline value estimates only in a separate column, never as substitutes for true returns.

6. **Seeds and uncertainty**
   Run at least four seeds to match the CQL reporting pattern. Report mean plus variability across seeds. Avoid claims based only on best seed or single-run results.

7. **Distribution-shift analysis**
   For each dataset, state why learned-policy actions may be unsupported or weakly supported by the data. If claiming conservatism, include an analysis separating estimated policy value from true simulator return, following the distinction shown by CQL Table 4.

8. **Per-domain reporting**
   Do not collapse all results into one aggregate score without also showing per-task and per-domain results. Report Gym, AntMaze, Adroit, Kitchen, or Atari separately when those domains are included.

9. **Claim boundaries**
   Limit conclusions to offline RL benchmark evidence on the evaluated D4RL tasks. Claims about online deployment, general robustness, or global superiority are not established by the packet and should be marked as requiring additional experiments.