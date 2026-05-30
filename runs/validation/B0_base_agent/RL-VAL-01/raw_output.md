## rl_protocol_audit

The provided protocol is not sufficient to evaluate strong world-model planning claims. The source packet only supports a high-level comparison to established model-based RL patterns: PETS uses probabilistic dynamics ensembles with model predictive control, while PlaNet learns latent dynamics from pixels and plans in latent space. The packet does not include enough implementation detail to validate environment configuration, model objective, planning horizon, uncertainty handling, baselines, seeds, episode counts, or statistical reporting.

Main audit risks:

- Environment details are underspecified. The protocol must name the exact benchmark suite, task IDs, observation modality, action repeat, episode length, reward preprocessing, termination handling, and training-data budget.
- Model-learning objective is underspecified. For PETS-like claims, the protocol should specify probabilistic dynamics training and ensemble use. For PlaNet-like claims, it should specify latent dynamics learning from pixels and how reconstruction, reward, transition, and latent-state losses are combined.
- Planning details are underspecified. The packet supports that both papers rely on planning, but not enough to infer horizon, optimizer, number of candidate trajectories, replanning frequency, or whether planning happens in state or latent space.
- Model-error controls are insufficiently described. World-model planning claims require explicit tests for compounding prediction error, uncertainty calibration, out-of-distribution rollouts, and sensitivity to planning horizon.
- Baselines are not defined. A valid protocol needs model-free, model-based, no-planning, oracle/state-input where appropriate, random-policy, and ablation baselines.
- Seeds and evaluation are missing. The protocol must specify independent training seeds, evaluation episodes per checkpoint, fixed evaluation policy settings, confidence intervals, and whether model selection uses validation or test tasks.
- Claim boundaries are too broad. The packet supports evaluating sample-efficient model-based control under conditions like those in PETS/PlaNet, but not general claims that a world model “understands” the environment or reliably supports long-horizon planning.

## model_error_and_planning_risk_table

| Risk area | Why it matters | Required control |
|---|---:|---|
| Compounding rollout error | Planning over learned dynamics can exploit model mistakes | Report performance across multiple planning horizons and compare imagined vs real rollout error |
| Uncertainty handling | PETS-style evidence emphasizes probabilistic ensembles | Use ensembles or another explicit uncertainty method; report ensemble disagreement/calibration |
| Latent-state aliasing | PlaNet-style planning from pixels depends on learned latent dynamics | Evaluate reconstruction/prediction quality and control performance separately |
| Horizon sensitivity | Longer horizons may look better in model but fail in environment | Sweep horizon and report real-environment returns |
| Planner exploitation | Optimizer may find actions that exploit inaccurate model regions | Add uncertainty penalties, short-horizon MPC comparisons, and real rollout validation |
| Data distribution shift | Learned model may be accurate only near collected trajectories | Track model error on held-out trajectories and after policy improvement |
| Reward-model error | Planning can fail even if transitions look plausible | Report reward prediction error separately from state/latent prediction |
| Evaluation leakage | Tuning on test environments inflates claims | Separate development tasks/seeds from final reporting tasks/seeds |

## environment_and_seed_checklist

- Exact environments and versions are named.
- Observation type is stated: true state, pixels, or both.
- Action space, action bounds, action repeat, episode length, and termination conditions are fixed.
- Reward scale and any preprocessing are documented.
- Initial-state distribution is specified.
- Training budget is given in real environment steps or episodes.
- Evaluation budget is separate from training.
- Number of independent random seeds is stated before experiments.
- Seeds cover environment, model initialization, data collection, and planner randomness.
- All baselines use the same environment-step budget.
- Evaluation uses fixed checkpoints, not best-after-the-fact selection.
- Report mean, standard deviation or standard error, and confidence intervals.

## baseline_and_metric_review

Required baselines:

- Random policy baseline.
- Model-free RL baseline under the same real-environment interaction budget.
- PETS-like probabilistic ensemble plus MPC baseline for state-based continuous control.
- PlaNet-like latent dynamics planning baseline for pixel-based control.
- No-planning learned-model baseline, such as policy trained from model features but without online planning.
- Ablations for deterministic vs probabilistic model, ensemble size, planning horizon, and uncertainty penalty.
- Oracle/state-observation variant where relevant, especially if claiming pixel-based world-model planning.

Required metrics:

- Final return and learning curve versus real environment steps.
- Area under the learning curve for sample efficiency.
- Success rate where tasks have success criteria.
- Model prediction error on held-out real trajectories.
- Reward prediction error.
- Uncertainty calibration or ensemble disagreement.
- Planning compute cost per environment step.
- Sensitivity to horizon and number of planner candidates.
- Failure-case analysis for model exploitation.

## revised_protocol

1. Define claims narrowly.

Evaluate whether the proposed world model improves sample-efficient control through planning under the tested environments. Do not claim general long-horizon reasoning, environment understanding, or transfer unless those are directly tested.

2. Specify environments.

Use named continuous-control environments matching the source scope: state-based tasks for PETS-style evaluation and pixel-based DeepMind Control-style tasks for PlaNet-style evaluation. For each task, document observation modality, action repeat, episode length, reward processing, termination rules, and training-step budget.

3. Define model objectives.

For state-based experiments, train a probabilistic dynamics ensemble to predict next-state change and reward where applicable. For pixel-based experiments, train a latent dynamics model from image observations with explicit transition, observation/reconstruction, reward, and latent-state objectives. Report all losses on held-out real trajectories.

4. Define planning.

Use model predictive control with replanning at each environment step. Pre-register planning horizon, optimizer, number of candidate action sequences, action constraints, temperature or elite fraction if using sampling-based planning, and whether planning occurs in observed state space or latent space. Run a horizon sweep to test sensitivity.

5. Control model error.

Maintain a held-out validation set of real transitions. Report one-step and multi-step prediction error, reward prediction error, and uncertainty quality. Add an experiment where planning horizon increases while real-environment performance is measured, to detect compounding model error. Include an uncertainty-aware planner and a deterministic-model ablation.

6. Use fair baselines.

Compare against random, model-free, PETS-like, PlaNet-like, no-planning, deterministic-model, and reduced-data baselines as appropriate to observation modality. Keep real-environment step budgets equal across methods.

7. Set seed and evaluation rules.

Run multiple independent seeds covering environment, model initialization, data collection, and planner randomness. Evaluate every fixed number of environment steps using a fixed number of episodes per seed. Report mean performance with uncertainty intervals and avoid selecting the best checkpoint unless explicitly labeled as oracle selection.

8. Report metrics.

Primary metrics: return versus real environment steps, final return, and area under the learning curve.

Secondary metrics: model prediction error, reward prediction error, calibration or ensemble disagreement, planner compute, horizon sensitivity, and qualitative failure cases.

9. Bound conclusions.

Valid conclusion: “Under the specified tasks and budgets, the learned dynamics model supports planning that improves sample efficiency relative to the listed baselines.”

Invalid conclusion without further evidence: “The world model supports reliable long-horizon planning in general,” “the agent understands the environment,” or “planning performance will transfer outside the tested task distribution.”