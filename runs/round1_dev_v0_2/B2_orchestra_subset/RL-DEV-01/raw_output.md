## rl_protocol_audit

| Risk | Severity | Provenance | Evidence issue | Consequence | Minimal fix |
|---|---:|---|---|---|---|
| Offline-to-online claims may be overstated | High | source-derived + agent-inferred | D4RL evaluates learned policies in specified simulators with normalized-return conventions; CQL reports D4RL normalized scores and some true returns, but the packet does not establish real-world online deployment performance. | Simulator evaluation can support benchmark performance, not unrestricted online RL effectiveness. | State claims as “offline-trained policy performance under D4RL simulator evaluation,” unless additional online/real-world experiments are added. |
| Dataset coverage may not match proposed generalization claims | High | source-derived | D4RL explicitly includes narrow, biased, multitask, suboptimal, and non-representable behavior-policy datasets. | A single aggregate result can hide failures on specific offline-RL pathologies. | Report per-domain and per-dataset results before aggregates; stratify by dataset property. |
| Behavior policy assumptions are underspecified | High | source-derived + agent-inferred | D4RL highlights non-representable behavior policies; CQL lower-bound guarantees hold under stated assumptions, but the packet does not list those assumptions in the proposed protocol. | Claims about conservatism, support, or value lower bounds may not apply to every dataset. | For each dataset, document behavior-policy source, support assumptions, and whether the method’s assumptions plausibly hold. |
| Train/eval separation is not fully auditable from the protocol | Medium | source-derived + agent-inferred | D4RL is framed as fixed static offline datasets with simulator-based evaluation, but the supplied protocol details are not given. | Leakage or adaptive tuning against evaluation environments could inflate reported performance. | Freeze offline datasets for training, separate validation for tuning, and reserve final simulator evaluation for locked policies. |
| Metrics may be conflated | Medium | source-derived | The packet notes normalized benchmark score, actual environment return, and policy value estimates are separate quantities. CQL Table 4 compares estimated policy values and true returns. | A protocol that treats value estimates as equivalent to returns may overclaim policy quality. | Report normalized score, raw return, and estimated value separately; define each metric and its claim target. |
| Seed and uncertainty reporting may be insufficient | Medium | source-derived | CQL D4RL tables average over four seeds; D4RL appendix tables include seed-reporting information. | Means alone do not show variance or robustness. Four seeds help but do not fully characterize uncertainty. | Report mean, standard deviation or confidence intervals, all seed values, and evaluation episodes per seed. |
| Baseline fairness is not guaranteed by packet alone | Medium | source-derived + agent-inferred | CQL compares against prior offline RL methods and behavioral cloning on D4RL tasks. Hyperparameter details are noted in the appendix. | Without equal tuning budgets and implementation details, improvement claims may be hard to attribute. | Specify baseline versions, tuning budgets, compute, hyperparameter search, and whether results are reproduced or copied. |

## dataset_and_environment_checklist

| Item | Status from packet | Risk | Required protocol detail |
|---|---|---|---|
| Dataset identity | Partially supported: D4RL defines benchmark domains and task identities. | Missing exact task list can blur scope. | List every D4RL task used, grouped by domain such as Gym, AntMaze, Adroit, and Kitchen where applicable. |
| Dataset type/pathology | Supported in general: D4RL discusses narrow, biased, multitask, suboptimal, and non-representable behavior policies. | Aggregate claims may hide which pathology is being tested. | Annotate each dataset with its relevant offline-RL challenge. |
| Behavior policy | Partially supported: D4RL frames fixed datasets and behavior-policy issues. | Support assumptions may fail. | Describe data collection policy or mixture when known; mark unknown or non-representable cases. |
| Static offline training | Supported: D4RL frames training from static datasets. | Online interaction during training would invalidate offline RL claims. | Explicitly prohibit environment interaction during training and tuning except final evaluation. |
| Evaluation environment | Partially supported: simulator-based evaluation is specified by D4RL. | Environment versions and episode settings may affect returns. | Record simulator version, task version, horizon, termination rules, number of episodes, and wrappers. |
| Normalized score anchors | Supported: D4RL defines normalized scores using task/domain-specific reference anchors. | Scores may be incomparable if anchors are changed. | Use official D4RL normalized-score formula and state anchors. |
| Raw returns | Supported: D4RL appendix includes raw returns; packet distinguishes raw return from normalized score. | Normalized-only reporting can obscure practical magnitude. | Report both raw environment return and normalized score. |
| Seeds | Partially supported: CQL reports four seeds; D4RL includes seed-reporting info. | Too little variance detail if only averages are shown. | Use at least the reported four-seed convention and disclose seed values, variance, and failed runs. |

## baseline_and_metric_review

| Dimension | Audit finding | Support status | Protocol requirement |
|---|---|---|---|
| Baselines | CQL compares against prior offline RL methods and behavioral cloning on D4RL. | Supported for benchmark comparison, not automatically fair across all implementations. | Include behavioral cloning and relevant offline RL baselines; document source, implementation, tuning, and compute. |
| Metrics | D4RL normalized score and raw environment return are distinct; CQL also analyzes estimated policy values versus true returns. | Supported. | Keep normalized score, raw return, and value estimate separate. |
| Aggregation | Tables report normalized-score comparisons across domains/tasks. | Partially supported. | Provide per-task results first; aggregate only with transparent weighting and domain grouping. |
| Uncertainty | CQL averages over four seeds. | Partially supported. | Report mean plus variance/CI, seed-level results, and evaluation episode counts. |
| Offline policy evaluation | CQL includes conservative-value analysis comparing estimated values and true returns on selected D4RL datasets. | Scoped support. | Treat OPE/value estimates as diagnostic unless validated against true simulator returns. |
| Improvement claims | Require direct compatible baseline comparison. | Only supported where same D4RL task, metric, and protocol are used. | Avoid global “better offline RL” claims from selective tables or incomparable settings. |

## claim_scope_assessment

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|
| The protocol evaluates offline RL on fixed datasets. | Benchmark-validity | Fixed dataset framing and eval protocol. | D4RL frames offline RL as training from static datasets. | Supported. | D4RL-style offline RL benchmark evaluation. |
| Normalized D4RL scores measure policy performance. | Benchmark-validity | Metric definition and task anchors. | D4RL defines normalized-score conventions using reference anchors. | Supported with caveat. | Benchmark-relative performance, not absolute capability. |
| CQL improves over baselines. | Improvement | Compatible baseline comparisons. | CQL Tables 1-2 compare normalized scores against prior methods and BC over four seeds. | Supported only for reported tasks/protocols. | The specific D4RL tasks, baselines, metrics, and seed setup in CQL. |
| Conservative Q-values solve offline distribution shift generally. | Generalization/causal | Broad heterogeneous evidence plus mechanism-isolating ablations. | CQL motivates action distribution shift and uses conservative objectives with guarantees under assumptions. | Partially supported. | Method rationale and reported D4RL/Atari settings, not all offline RL. |
| Offline benchmark success implies online deployment success. | Generalization | Online or real-world deployment evidence. | Packet only establishes simulator-based evaluation. | Unsupported. | Do not claim beyond offline-trained policies evaluated in specified simulators. |
| Estimated policy values are reliable substitutes for true returns. | Benchmark-validity | Calibration evidence across tasks. | CQL Table 4 compares estimates and true returns on selected datasets. | Scoped diagnostic support only. | Selected analysis settings; not a universal replacement for evaluation returns. |

## revised_protocol

1. **Dataset specification**
   - Use fixed D4RL datasets only.
   - List every task, domain, dataset variant, and dataset property: narrow, biased, multitask, suboptimal, or non-representable behavior policy where applicable.
   - Document behavior-policy information and explicitly mark unknown or non-representable behavior-policy cases.

2. **Offline training rule**
   - Train only on the static offline dataset.
   - Do not allow simulator interaction during training.
   - Use a separate validation procedure for hyperparameter selection; lock all settings before final evaluation.

3. **Environment and evaluation setup**
   - Evaluate policies only in the specified simulator environments.
   - Record environment/task version, horizon, termination behavior, number of evaluation episodes, random seeds, and any wrappers.
   - Preserve raw environment returns before computing normalized scores.

4. **Metrics**
   - Report three quantities separately:
     - raw environment return,
     - D4RL normalized score using official task/domain anchors,
     - estimated policy value, if offline value estimation is analyzed.
   - Do not use estimated policy value as a substitute for simulator return unless explicitly validated.

5. **Baselines**
   - Include behavioral cloning and relevant prior offline RL methods.
   - For every baseline, report implementation source, hyperparameters, tuning budget, compute budget, and whether numbers are reproduced or taken from prior reports.
   - Compare methods only when task, dataset, metric, and evaluation protocol match.

6. **Seeds and uncertainty**
   - Run multiple seeds, with four seeds as the minimum convention supported by the CQL packet.
   - Report mean, standard deviation or confidence intervals, and individual seed results.
   - Include failed or unstable runs rather than silently dropping them.

7. **Reporting structure**
   - Report per-task results first.
   - Then report domain-level summaries.
   - Use aggregate scores only after explaining weighting and preserving per-task visibility.

8. **Claim boundaries**
   - Allowed: “The method performs better/worse under the specified D4RL offline benchmark protocol.”
   - Allowed: “The method addresses offline action distribution shift under the assumptions stated for the conservative objective.”
   - Not allowed without extra evidence: “The method is generally superior for offline RL,” “the learned policy will perform well online,” or “offline value estimates prove deployment performance.”