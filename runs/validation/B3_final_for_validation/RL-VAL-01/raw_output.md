**rl_protocol_audit**

Source inventory: PETS (Chua et al., 2018, arXiv:1805.12114) with supplied evidence from abstract, probabilistic ensembles, model predictive control, experiments, baselines, result tables/figures, and limitations; PlaNet (Hafner et al., 2018, arXiv:1811.04551) with supplied evidence from abstract, latent dynamics model, planning, DeepMind Control experiments, baselines, result tables/figures, and limitations. Exact numeric values, full tables, appendix details, and implementation settings are explicitly absent from the packet.

| Audit item | Packet evidence | Risk | Evidence label |
|---|---|---|---|
| Environment details | PETS: continuous-control RL; PlaNet: DeepMind Control experiments from pixels | Environment versions, task list, wrappers, horizons, stochasticity, termination, and action/reward specs are not available in the packet | `LIMITED_CRITIQUE` |
| Model-learning objective | PETS uses probabilistic dynamics models; PlaNet learns latent dynamics from pixels | Packet does not provide exact losses, likelihood terms, latent objectives, training schedules, or validation criteria | `LIMITED_CRITIQUE` |
| Planning method | PETS uses model predictive control; PlaNet plans in latent space | Planning horizon, optimizer, candidate action budget, replanning frequency, and uncertainty handling are not specified in the packet | `LIMITED_CRITIQUE` |
| Model-error controls | PETS explicitly uses probabilistic ensembles | PETS has direct model-uncertainty machinery, but the packet does not establish sufficient model-error diagnostics; PlaNet model-error controls are underspecified here | `WITHIN_PACKET_SYNTHESIS` |
| Baselines | Packet states included evidence contains baselines | Baseline identities, tuning parity, data budgets, compute budgets, and evaluation protocol compatibility are absent | `LIMITED_CRITIQUE` |
| Seeds and variability | Not supplied | Cannot assess robustness across random seeds or model/planner stochasticity | `LIMITED_CRITIQUE` |
| Evaluation episodes | Not supplied | Cannot assess whether reported returns/success metrics are stable rollout estimates | `LIMITED_CRITIQUE` |
| Metrics | Not supplied beyond control-task evaluation context | Metric alignment with “world-model planning” is unclear without return definitions, aggregation, uncertainty, and model-prediction metrics | `LIMITED_CRITIQUE` |
| Claim boundary | Both sources support model-based planning claims in their reported experimental settings | Packet does not support global claims about deployment robustness, universal sample efficiency, or superiority across environments | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` |

**model_error_and_planning_risk_table**

| Risk | Why it matters for world-model planning claims | Packet grounding | Mitigation in revised protocol |
|---|---|---|---|
| Planning may exploit model errors | A planner can find high-reward imagined trajectories that fail under real rollout | PETS/PlaNet both rely on learned dynamics plus planning | Report imagined vs real rollout returns; add model-prediction error by horizon |
| Horizon sensitivity is unknown | Long horizons compound model error; short horizons may test reactive control more than planning | Planning is supplied, but horizon details are absent | Sweep planning horizons and report performance/error curves |
| Uncertainty handling is incomplete | Probabilistic ensembles help PETS, but uncertainty calibration is not established by the packet | PETS uses probabilistic ensembles | Add ensemble disagreement/calibration diagnostics and uncertainty ablations |
| Latent model validity is unclear | PlaNet plans in latent space, so latent predictive quality may not equal task-relevant control reliability | PlaNet learns latent dynamics from pixels and plans in latent space | Evaluate latent prediction, reconstruction if applicable, reward prediction, and rollout control performance |
| Baseline comparability risk | Strong claims require comparable data, compute, tuning, and evaluation | Baselines are included but not specified | Fix data budgets, environment versions, action repeat, seeds, and tuning protocol across baselines |
| Evaluation variance risk | Planning methods can vary by seed, model initialization, and environment randomness | Seeds/episodes not supplied | Require multiple seeds, fixed evaluation episodes per seed, and confidence intervals |

**environment_and_seed_checklist**

| Required item | Status from packet | Needed for sufficient protocol |
|---|---|---|
| Environment/task names | Partially supplied: continuous-control and DeepMind Control context | Exact task names and versions |
| Observation type | PlaNet: pixels; PETS not fully specified in packet | Observation shape, preprocessing, frame stacking/action repeat |
| Reward definition | Not supplied | Exact reward, return horizon, discount, termination |
| Episode horizon | Not supplied | Max episode length and termination rules |
| Environment stochasticity | Not supplied | Randomization, seeds, simulator version |
| Training seeds | Not supplied | At least multiple independent seeds; exact count must be specified |
| Evaluation episodes | Not supplied | Fixed number of evaluation episodes per seed |
| Train/eval split | Not supplied | Separate training interaction from held-out evaluation rollouts |
| Dataset/interaction budget | Source notes imply sample efficiency, but exact budgets absent | Step budgets and equal-budget comparison across methods |
| Hardware/compute | Not supplied | Compute budget or planner/model update budget for fair comparison |

**baseline_and_metric_review**

Baselines are mentioned as included evidence objects, but the packet does not provide their identities or settings. Therefore, any claim that PETS or PlaNet outperforms specific alternatives is only supportable inside the original papers’ reported setups, not from the packet alone. This is `LIMITED_CRITIQUE`.

For a sufficient world-model planning evaluation, baselines should include: a no-planning dynamics baseline if applicable, model-free RL under the same environment and interaction budget, random or simple scripted policy, behavior cloning or supervised dynamics-only control where relevant, and ablations of model uncertainty, planning horizon, and learned reward/dynamics components. These are revised-protocol requirements, not packet-established facts, so they are `SPECULATIVE_PROPOSAL`.

Metrics should include real-environment episodic return, success rate where task-appropriate, sample efficiency curves, prediction error across rollout horizon, reward-prediction error, planner compute cost, uncertainty or disagreement calibration, and variance across seeds. Benchmark score alone would not be sufficient to establish robust world-model planning. This audit judgment is `LIMITED_CRITIQUE`.

**revised_protocol**

1. Specify every environment: task name, version, observation modality, reward, action space, episode horizon, termination, wrappers, simulator settings, and random seeds.

2. Define the model objective: supervised dynamics target, latent objective if used, reward model, reconstruction or representation terms if any, optimizer, update schedule, validation split, and early-stopping or checkpoint rule.

3. Define planning exactly: MPC or latent-space planner, horizon, replanning frequency, action-sequence optimizer, number of candidates/iterations, discount, terminal value handling, and compute budget.

4. Add model-error controls: horizon-wise prediction error, reward-prediction error, imagined-vs-real rollout comparison, uncertainty calibration for probabilistic models, ensemble-disagreement analysis where used, and failure cases where planning exploits model error.

5. Run ablations: no planning, shorter/longer planning horizons, deterministic vs probabilistic model where applicable, ensemble size or uncertainty removal for PETS-style methods, latent-model component ablations for PlaNet-style methods, and equal-budget planner variants.

6. Use fair baselines: random/simple policy, strong model-free RL under the same interaction budget, model-based method without uncertainty or without latent planning as applicable, and any paper-reported baselines with identical environment and evaluation settings.

7. Report evaluation rigor: multiple training seeds, fixed evaluation episodes per seed, mean plus uncertainty interval, raw per-task returns, aggregate metrics only after showing task-level results, and all failed or unstable runs.

8. Bound claims narrowly: supported claims may concern sample-efficient planning in the specified continuous-control or pixel-control tasks under the stated protocol. Claims about general world-model reasoning, deployment robustness, or universal superiority require external evidence and should be labeled `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`.