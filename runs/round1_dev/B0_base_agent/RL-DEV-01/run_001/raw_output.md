## `rl_protocol_audit`

| Area | Risk | Severity | Packet Support | Required Fix |
|---|---:|---:|---|---|
| Dataset coverage | Protocol does not specify which D4RL domains, tasks, dataset variants, or dataset sizes are used. | High | D4RL includes many benchmark domains and dataset types, including narrow, biased, multitask, suboptimal, and non-representable behavior-policy data. | List every dataset by exact task name, domain, version, and split. Explain why each dataset type is included. |
| Behavior policy assumptions | Behavior policy is not described and may be incorrectly assumed to be stationary, optimal, known, or representable. | High | D4RL explicitly emphasizes non-representable behavior policies, biased data, narrow data, and suboptimal data. | State whether the behavior policy is known, unknown, mixed, suboptimal, multitask, or non-representable. Avoid assumptions not supported by the dataset metadata. |
| Offline distribution shift | Protocol does not clearly address out-of-distribution action risk. | High | CQL is motivated by offline RL distributional shift and conservative value estimation for OOD actions. | Include explicit OOD-action mitigation, such as CQL-style conservative Q-learning or another justified offline RL method. |
| Train/eval separation | Missing details on training data, validation/model-selection data, and final evaluation episodes. | High | Offline RL requires care because policy learning occurs from fixed datasets while evaluation may be in benchmark environments. | Define training dataset, any validation procedure, hyperparameter selection protocol, and final evaluation procedure separately. |
| Environment details | Environment versions, wrappers, reward preprocessing, termination handling, and evaluation setup are absent. | High | Packet requires absent environment version, wrapper, seed, or evaluation-episode details to be marked missing. | Report exact environment/task IDs, D4RL version if known, wrappers, reward conventions, horizon, timeout handling, and evaluation episodes. |
| Metrics | Protocol may conflate normalized D4RL score, raw environment return, and learned value estimates. | High | Packet explicitly requires distinguishing normalized benchmark score, actual environment return, and policy value estimates. | Report all three separately when available; never use Q-value estimates as policy performance. |
| Baselines | Baselines are unspecified or may omit behavioral cloning and offline RL comparators. | Medium-High | CQL compares against prior offline RL methods and behavioral cloning on D4RL. | Include behavioral cloning and relevant offline RL baselines; report same metrics and evaluation conditions for all. |
| Seeds/runs | Random seeds and number of runs are missing. | High | Packet requires seed details to be audited and absent seed details marked missing. | Pre-register number of seeds, seed values or generation method, and aggregation procedure. |
| Uncertainty reporting | No confidence intervals, standard deviations, or run-to-run variability specified. | High | Packet requires uncertainty reporting audit. | Report mean plus standard deviation or confidence interval across seeds. Include per-seed results in appendix/table. |
| Offline-to-online claims | Any deployment, online improvement, or real-world generalization claim is unsupported unless directly evaluated. | High | Required boundary: do not infer online performance from offline benchmark results unless packet directly supports it. | Limit claims to offline benchmark performance under specified D4RL tasks and evaluation environments. |
| Dataset limitations | Protocol may overgeneralize from D4RL benchmark results. | Medium | D4RL discussion includes limitations and dataset-specific difficulties. | Add limitations section covering narrow, biased, suboptimal, multitask, and non-representable behavior-policy data. |

---

## `dataset_and_environment_checklist`

| Item | Status From Packet | Required Protocol Entry |
|---|---|---|
| Dataset source | D4RL benchmark suite | Exact D4RL task names and dataset variants |
| Dataset version | Missing | Version or frozen dataset hash/checksum |
| Domain coverage | D4RL includes gym, AntMaze, Adroit, kitchen, Atari-style datasets per CQL notes | Specify which are included/excluded and why |
| Dataset type | D4RL includes narrow, biased, multitask, suboptimal, and non-representable behavior-policy data | Label each selected dataset by data regime |
| Behavior policy identity | Unknown unless supplied by dataset metadata | Do not assume known/optimal/stationary behavior policy |
| Behavior policy quality | May be suboptimal or mixed | Report available dataset descriptors only |
| Train split | Missing | Define fixed offline training data |
| Validation/model selection split | Missing | Define validation policy or state no validation split |
| Test/eval environment | Missing | Exact environment IDs and versions |
| Wrappers/preprocessing | Missing | List observation, action, reward, timeout, and termination wrappers |
| Evaluation episodes | Missing | Number of episodes per seed and deterministic/stochastic policy mode |
| Random seeds | Missing | Training seeds, environment seeds, evaluation seeds |
| Dataset leakage controls | Missing | Ensure no evaluation trajectories are added to training data |
| Online interaction during training | Missing | State explicitly: none during offline training |
| Reward/score normalization | D4RL defines normalized-score conventions | Report normalized D4RL score formula/source and raw returns |

---

## `baseline_and_metric_review`

**Baselines to include**

| Baseline | Reason |
|---|---|
| Behavioral cloning | CQL uses behavioral cloning as a comparison; it is a key offline RL reference point. |
| CQL | Packet identifies CQL as an offline RL method designed to address distributional shift through conservative Q-functions. |
| Prior offline RL methods | CQL compares against prior offline RL methods; exact methods are not named in the packet, so names are unknown from this source. |
| Dataset behavior policy score | Useful if available, but packet does not provide exact values. Mark unknown unless measured or supplied. |
| Random policy | Not directly supported by packet as required baseline; optional/speculative unless protocol already includes it. |

**Metric requirements**

| Metric | Use | Risk If Omitted |
|---|---|---|
| Raw environment return | Actual episodic performance in the evaluation environment | Normalized score alone may hide task-specific scale. |
| D4RL normalized score | Benchmark comparability | Must not be confused with raw return. |
| Learned policy value estimate/Q estimate | Diagnostic only | Must not be treated as actual policy performance. |
| Mean across seeds | Aggregate result | Single-run results are unstable and underreported. |
| Std dev / confidence interval | Uncertainty | No basis for comparing methods reliably. |
| Per-task score table | Coverage | Aggregate-only reporting can hide failures. |
| Per-seed table | Reproducibility | Prevents selective reporting. |

---

## `claim_scope_assessment`

| Claim Type | Supported? | Assessment |
|---|---:|---|
| “Method performs well on specified D4RL offline RL benchmark tasks.” | Potentially supported | Only if exact datasets, environments, seeds, baselines, and metrics are reported. |
| “Method outperforms CQL.” | Not currently supported | Requires same D4RL tasks, same metrics, comparable baselines, seeds, and uncertainty. |
| “Method solves offline RL distribution shift.” | Not supported | CQL addresses distributional shift, but benchmark performance alone does not prove the problem is solved. |
| “Offline score predicts online performance.” | Not supported | Packet explicitly forbids inferring online performance from offline benchmark results unless directly supported. |
| “Ready for deployment.” | Not supported | No deployment environment, safety constraints, online validation, or real-world testing are provided. |
| “Generalizes beyond D4RL.” | Not supported | D4RL benchmark results do not establish broad generalization without additional evidence. |
| “Works under unknown/non-representable behavior policies.” | Partially testable | D4RL includes such difficulties, but the protocol must identify which datasets actually test them. |
| “Improves actual returns.” | Potentially supported | Requires raw environment return evaluation, not only normalized scores or Q estimates. |

---

## `revised_protocol`

1. **Objective**

Evaluate offline RL algorithms on fixed D4RL benchmark datasets, with explicit separation between offline training, model selection, and final environment evaluation. Claims are limited to benchmark performance on the specified datasets.

2. **Datasets**

Use a predeclared set of D4RL tasks. For each task, report:

- Exact dataset/task name.
- Domain.
- Dataset version or checksum.
- Dataset regime: narrow, biased, multitask, suboptimal, mixed, or non-representable behavior policy where known.
- Number of trajectories/transitions if available.
- Whether the behavior policy is known or unknown.
- Any unsupported behavior-policy details marked as unknown.

No online environment interaction is allowed during training.

3. **Environment Specification**

For every evaluation task, report:

- Exact environment ID and version.
- D4RL version.
- Observation/action preprocessing.
- Reward preprocessing.
- Timeout and terminal-state handling.
- Episode horizon.
- Evaluation policy mode: deterministic or stochastic.
- Number of evaluation episodes per seed.
- Environment seeds.

If any of these are absent, mark them missing rather than assuming defaults.

4. **Methods**

Evaluate the proposed method against:

- Behavioral cloning.
- CQL.
- Other offline RL baselines if implemented under the same protocol.

All methods must use the same datasets, same environment setup, same evaluation budget, and same reporting format.

5. **Training and Model Selection**

For each method:

- Train only on the fixed offline dataset.
- Predefine hyperparameter search space.
- Specify validation/model-selection procedure.
- Do not select checkpoints based on final test performance unless explicitly reported as such.
- Report compute budget and number of gradient steps or epochs.

6. **Seeds and Uncertainty**

Run each method on multiple random seeds. The exact number is missing from the packet, so the protocol must define it before experiments.

Report:

- Seed list or seed-generation rule.
- Mean performance.
- Standard deviation or confidence interval.
- Per-seed results.
- Any failed or unstable runs.

7. **Metrics**

For each task and method, report separately:

- Raw episodic return.
- D4RL normalized score.
- Learned value estimate or Q estimate, if used, only as a diagnostic.
- Runtime or sample-processing budget if relevant.

Do not substitute value estimates for environment evaluation returns.

8. **Analysis**

Include per-domain and per-dataset analysis covering:

- Performance on narrow data.
- Performance on biased data.
- Performance on suboptimal data.
- Performance on multitask data.
- Sensitivity to behavior-policy mismatch.
- Evidence of OOD-action overestimation or conservative correction where measured.

9. **Claim Boundaries**

Allowed claims:

- “The method achieves X normalized score and Y raw return on the specified D4RL task under this protocol.”
- “The method outperforms listed baselines under the same offline benchmark setup,” if supported by uncertainty-aware comparisons.

Disallowed or unsupported claims unless separately tested:

- Online performance improvement.
- Real-world deployment readiness.
- Generalization beyond tested D4RL tasks.
- Robustness to all behavior-policy types.
- Solving offline RL distribution shift generally.

10. **Reporting Package**

The final report should include:

- Dataset and environment table.
- Baseline table.
- Metric table with raw returns and normalized scores.
- Seed and uncertainty table.
- Hyperparameter table.
- Explicit missing-information table.
- Claim-scope statement separating benchmark findings from speculative extrapolation.