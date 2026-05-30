You are scoring an internal fixed-source validation benchmark after generation is complete.

Use only the task specification, frozen validation gold annotation, scoring rubric, and generated outputs below. Do not use external facts. Do not reward style over correctness. Score each variant independently but compare across variants for calibration.

Return JSON matching the provided schema only. For each of the four variants, provide scores from 1-5 or null when a dimension is not applicable to this task. Include concise findings and scoring_notes. No markdown.

# Task ID
RL-VAL-01

# Task Specification
task_id: RL-VAL-01
split: validation
task_type: rl_specific_analysis
topic: model-based reinforcement learning
research_question: "Is the provided model-based RL protocol sufficient to evaluate world-model planning claims?"
input_prompt: |
  Review the provided model-based RL protocol using only the source packet.
  Audit environment details, model-learning objective, planning horizon, model-error controls, baselines, seeds, evaluation episodes, metrics, and claim boundaries.
  Return an RL-specific risk register and a revised protocol.
evaluation_mode: closed_source
source_material_required: true
provided_materials:
  - material_id: packet_rl_ho_model_based_protocol
    type: protocol_packet
    status: source_material_required
    description: "A frozen model-based RL or world-model planning protocol/proposal excerpt."
required_outputs:
  - rl_protocol_audit
  - model_error_and_planning_risk_table
  - environment_and_seed_checklist
  - baseline_and_metric_review
  - revised_protocol
critical_facts_to_capture:
  - "Planning setup, learned model assumptions, and environment details in the packet."
  - "Baselines, ablations, seeds, and evaluation episode counts."
  - "Controls for compounding model error or planning-specific confounds."
  - "Scope of claims about sample efficiency, generalization, or planning quality."
common_failure_modes:
  - "Ignoring model-error accumulation."
  - "Failing to require model-free and model-based baselines where appropriate."
  - "Omitting environment version or wrapper details."
  - "Treating planning success as proof of learned world-model fidelity."
scoring_dimensions:
  - factual_accuracy
  - evidence_traceability
  - experimental_rigor
  - benchmark_validity
  - rl_specific_correctness
  - inference_boundary_discipline
  - output_usefulness
  - efficiency
notes_on_domain_specificity: "Validation RL task emphasizing model-based RL and world-model evaluation."



# Frozen Gold Annotation
task_id: RL-VAL-01
source_packet_id: validation_RL-VAL-01_packet_v0_draft
drafted_by_agent: true
human_review_status: pending
eligible_for_scoring: false
must_capture:
- id: RL-VAL-01-M1
  finding: Audits learned dynamics assumptions, planning horizon, model-error accumulation, baselines, seeds, evaluation episodes,
    and metrics.
  evidence_locations_to_verify:
  - PETS PDF p.1 Abstract and probabilistic dynamics/model predictive control sections; PlaNet PDF p.1 Abstract and latent
    dynamics/planning sections.
  scoring_weight: high
- id: RL-VAL-01-M2
  finding: Separates planning success, world-model fidelity, sample efficiency, and policy performance.
  evidence_locations_to_verify:
  - PETS and PlaNet experiment sections, baseline tables/figures, environment descriptions, and evaluation protocol sections.
  scoring_weight: high
- id: RL-VAL-01-M3
  finding: Requires model-free and model-based baselines where packet evidence supports the comparison need.
  evidence_locations_to_verify:
  - PETS/PlaNet model-learning sections, planning horizon/control sections, result tables, and limitations/discussion.
  scoring_weight: medium
acceptable_equivalent_formulations:
- Equivalent wording is acceptable if it remains grounded in the supplied validation packet and preserves claim scope.
critical_errors:
- id: E1
  error: Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
  penalty: major
- id: E2
  error: Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
  penalty: major
- id: E3
  error: Invents missing metrics, seeds, versions, baselines, or numeric results.
  penalty: major
inference_boundary_requirements:
- Use only the packet as evidence.
- Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses.
- Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced.
optional_high_value_findings:
- Identifies missing reproducibility details without treating absence from the packet as proof of source failure.
- Separates direct evidence from synthesis and proposed follow-up checks.
- Reports source/page/table grounding where the packet or canonical source supplies it.
ambiguities_requiring_human_review:
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.


# Agent Review Authorization Layer
This authorizes internal scoring but is not itself a gold answer. Apply the global E/B rule: external facts or broad claims should be penalized only when used as evidence for a core scored claim; harmless background context clearly marked as non-evidence should not trigger a major penalty.

# Scoring Rubric
# Scoring Rubric

Score each dimension from 1 to 5. Keep dimensions separate; do not collapse them into one total score unless a later report explicitly defines a weighted decision rule.

## Scale

| Score | Meaning |
|---:|---|
| 5 | Excellent. Expert-useful, accurate, traceable, and complete for the task scope. |
| 4 | Strong. Minor omissions or calibration issues, but scientifically reliable. |
| 3 | Adequate. Useful with expert cleanup; some missing detail or weak organization. |
| 2 | Weak. Substantial omissions, unsupported reasoning, or poor task fit. |
| 1 | Unreliable. Misleading, unsupported, materially incorrect, or unsafe for research use. |

## Dimensions

### Factual Accuracy

Measures whether the output correctly states methods, assumptions, datasets, metrics, experimental findings, and limitations.

Strong outputs separate source claims from the agent's interpretation. Weak outputs misstate paper facts, confuse versions, invent details, or generalize beyond the source.

### Evidence Traceability

Measures whether substantive claims link to provided sources, source locations, evidence IDs, or retrieval results.

Strong outputs make it clear what each source supports and what it does not support. Weak outputs provide unsupported claims or citations that are only topically related.

### Citation Validity

Measures whether cited works exist, are identified correctly, and support the stated claim.

For closed-source tasks, citations must come from the source packet. For retrieval tasks, citations must follow fixed retrieval rules and include enough metadata to verify.

### Literature Coverage

Applies primarily to retrieval and literature-survey tasks. Measures whether the output includes canonical work, recent relevant work, and important contrasting lines of research.

Strong outputs document search strategy, coverage limits, and omissions. Weak outputs miss obvious core work or overfit to one source.

### Comparison Fairness

Measures whether methods are compared under compatible assumptions, datasets, metrics, compute, tuning effort, and evaluation protocols.

Strong outputs identify non-comparable settings and normalize conclusions. Weak outputs declare winners without accounting for task setup or baseline strength.

### Experimental Rigor

Measures handling of baselines, ablations, metrics, seeds, statistical uncertainty, compute, data splits, hyperparameter search, and reproduction risk.

Strong outputs distinguish confirmatory from exploratory evidence. Weak outputs ignore missing baselines, single-seed claims, metric mismatch, or leakage.

### Benchmark Validity

Measures whether benchmarks, datasets, tasks, metrics, and protocols are suitable for the claim being made.

Strong outputs identify contamination, leakage, saturation, protocol mismatch, metric gaming, and train/eval mismatch. Weak outputs treat a benchmark score as automatically meaningful.

### Inference-Boundary Discipline

Measures whether the output distinguishes source-supported conclusions, cross-paper synthesis, hypotheses, and speculation.

Strong outputs calibrate scope and uncertainty. Weak outputs launder speculation into conclusions or overstate causal/generalization claims.

### Hypothesis Quality

Applies primarily to proposal-support tasks. Measures whether hypotheses are grounded in evidence, falsifiable, scoped, feasible, and paired with disconfirming observations.

Strong outputs specify predictions, failure criteria, required evidence, and alternative explanations. Weak outputs generate attractive but untestable ideas.

### RL-Specific Correctness

Applies to RL tasks. Measures correctness about environment versions, wrappers, policies, reward functions, offline data, evaluation episodes, stochasticity, train/eval mismatch, and return distributions.

Strong outputs catch RL-specific failure modes. Weak outputs treat RL results like ordinary supervised-learning benchmarks.

### Output Usefulness

Measures whether the artifact supports a real research decision: reading, reviewing, planning, reproduction, proposal writing, or experimental design.

Strong outputs are structured, actionable, and concise enough to use. Weak outputs are polished but generic.

### Efficiency

Measures token cost, latency, tool calls, retrieval volume, and useful-information density.

High-quality but extremely inefficient outputs should be flagged. Efficient outputs must still satisfy reliability requirements.

## Hard-Fail Conditions

A task may receive an overall hard-fail flag if any of these occur:

- A hallucinated citation is presented as real.
- A critical claim is marked supported without direct evidence.
- A comparative conclusion is made without adequate baseline or setting normalization.
- An RL result is summarized from best seed/checkpoint only without disclosure.
- A causal interpretability claim is supported only by correlational evidence.
- A reproduction or experiment plan omits required data, environment, or evaluation protocol.
- Held-out gold annotation content appears in the output or prompt context.

## Scorecard Format

```yaml
run_id:
variant:
task_id:
reviewer:
scores:
  factual_accuracy:
  evidence_traceability:
  citation_validity:
  literature_coverage:
  comparison_fairness:
  experimental_rigor:
  benchmark_validity:
  inference_boundary_discipline:
  hypothesis_quality:
  rl_specific_correctness:
  output_usefulness:
  efficiency:
hard_fail:
  triggered: false
  reasons: []
findings:
  - severity: major|minor
    dimension:
    description:
    evidence:
summary:
```


# Generated Outputs
## OUTPUT: B0_base_agent

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
## OUTPUT: B1_kdense_subset

I can’t complete the requested audit against the actual protocol because the packet does not include the protocol text to review. It only provides two source notes: PETS uses probabilistic dynamics models with MPC, and PlaNet learns latent dynamics from pixels and plans in latent space. Exact settings, tables, appendix details, and implementation parameters are explicitly unavailable.

## rl_protocol_audit

| Audit area | Packet-supported expectation | Status for provided protocol | Risk |
|---|---|---:|---|
| Environment details | PETS: continuous-control RL; PlaNet: DeepMind Control from pixels | Protocol details absent | Not established by packet |
| Model-learning objective | PETS: probabilistic dynamics models; PlaNet: latent dynamics from pixels | Objective absent | Cannot assess whether learning objective matches claim |
| Planning horizon | Both source notes involve planning/control | Horizon absent | Cannot assess whether planning claim is meaningfully tested |
| Model-error controls | PETS emphasizes probabilistic ensembles; PlaNet uses learned latent dynamics | Controls absent | High risk of attributing model artifacts to planning |
| Baselines | Packet says experiment sections/baselines exist, but details unavailable | Baselines absent | Cannot judge comparative strength |
| Seeds | No seed information in packet | Absent | Statistical validity not established |
| Evaluation episodes | No episode-count information in packet | Absent | Reliability not established |
| Metrics | No metric details in packet | Absent | Claim scope unsupported |
| Claim boundaries | PETS and PlaNet support only general world-model planning relevance | Protocol claim absent | Any strong claim would exceed packet evidence |

## model_error_and_planning_risk_table

| Risk | Source motivation | Why it matters | Severity | Required control |
|---|---|---|---:|---|
| Model exploitation during planning | PETS uses probabilistic dynamics models with MPC; PlaNet plans using learned latent dynamics | Planning may exploit prediction errors rather than learn robust control | High | Report model-error diagnostics and evaluate rollouts under held-out dynamics data |
| Unspecified uncertainty handling | PETS specifically uses probabilistic ensembles | Deterministic or under-specified models may hide compounding error | High | State uncertainty method, ensemble size if any, and how uncertainty affects planning |
| Planning horizon not specified | Both packet sources involve planning/control | Long horizons amplify model error; short horizons may not test world-model planning claims | High | Predefine horizon sweep or justify fixed horizon |
| Pixel-to-latent mismatch | PlaNet learns latent dynamics from pixels | Latent planning may optimize representations that do not preserve task-relevant state | Medium | Include reconstruction/prediction or latent consistency checks tied to control |
| Weak baseline comparison | Packet notes baselines exist but gives no details | Planning claims require comparison against non-planning or model-free alternatives | High | Include model-free, no-planning, random-shooting/MPC, and ablation baselines where appropriate |
| Insufficient reporting of variance | Seeds unavailable | Sample-efficient RL can be unstable across seeds | High | Report multiple seeds with dispersion, not only best run |

## environment_and_seed_checklist

| Item | Required for sufficient protocol | Packet status |
|---|---|---|
| Environment names | List all tasks and versions | Not provided |
| Observation modality | State whether state-based, pixel-based, or both | Only source notes distinguish PETS continuous control and PlaNet pixels |
| Action space | Specify continuous/discrete and bounds | Not provided |
| Episode horizon | Specify max episode length | Not provided |
| Training budget | State environment steps/trials | Not provided |
| Evaluation budget | State number of episodes per checkpoint | Not provided |
| Seeds | Use multiple random seeds and disclose them | Not provided |
| Initialization | Specify model, policy, planner, and environment initialization | Not provided |
| Train/eval separation | Separate model-learning data from evaluation episodes | Not provided |

## baseline_and_metric_review

| Area | Minimum needed | Packet-supported critique |
|---|---|---|
| Baselines | Compare against relevant model-free, no-model, no-planning, and prior model-based methods | Packet confirms baselines exist in source papers but does not provide which ones |
| Metrics | Return, sample efficiency, model prediction error, planning success, variance | Metrics are not specified in the packet |
| Aggregation | Mean/median plus uncertainty across seeds | Not established |
| Claim boundary | Claims should be limited to tested environments and budgets | Any broader claim is unsupported |
| Ablations | Remove planning, vary horizon, vary model uncertainty, vary data budget | Needed to isolate world-model planning effects |

## revised_protocol

1. Define environments explicitly: task names, versions, observation modality, action space, episode length, reward definition, and train/evaluation split.

2. Specify the world model: input/output variables, deterministic vs probabilistic dynamics, latent vs observation-space prediction, loss function, training schedule, data collection procedure, and uncertainty mechanism.

3. Define planning: planner type, planning horizon, number of candidate trajectories or optimization iterations, replanning frequency, objective, terminal value use if any, and action constraints.

4. Add model-error controls: held-out one-step and multi-step prediction error, error by horizon, uncertainty calibration if probabilistic, and comparison between imagined rollouts and real environment outcomes.

5. Include baselines: model-free baseline, random policy, no-planning world-model ablation, shorter/longer planning-horizon ablations, and a model-based baseline comparable to MPC-style planning where applicable.

6. Use rigorous evaluation: multiple seeds, fixed evaluation episodes per seed, no exploration noise during evaluation unless justified, report mean and uncertainty, and include learning curves over environment interaction budget.

7. Bound claims narrowly: state that results support world-model planning only for the listed environments, budgets, observation modalities, model class, and planner settings. Broader claims about model-based RL or general planning ability are not established by this packet.
## OUTPUT: B2_orchestra_subset

## rl_protocol_audit

The source packet is not sufficient to fully evaluate broad world-model planning claims. It supports only a scoped audit: PETS uses probabilistic dynamics models plus model predictive control for sample-efficient continuous-control RL, and PlaNet learns latent dynamics from pixels and plans in latent space for control tasks. Those are source-derived claims, but the packet omits most protocol details needed to judge validity.

| Claim / protocol element | Provenance | Evidence in packet | Support status | Audit consequence |
|---|---|---|---|---|
| PETS evaluates probabilistic dynamics models with MPC | source-derived | Controlled source notes | Supported at high level | Enough to identify model-based planning setup, not enough to validate implementation fairness |
| PlaNet evaluates latent dynamics planning from pixels | source-derived | Controlled source notes | Supported at high level | Enough to identify pixel-based world-model planning, not enough to audit representation/model training details |
| Protocol can support sample-efficiency claims | agent-inferred | PETS note mentions sample-efficient continuous control | Partially supported | Needs exact trial counts, environment steps, baselines, and uncertainty |
| Protocol can support world-model planning superiority claims | unsupported | No compatible direct comparison across methods in packet | Not supported | Requires controlled baselines, ablations, model-error diagnostics, and planning-vs-model-learning separation |
| Protocol generalizes across RL domains | unsupported | Only continuous-control and DeepMind Control are noted | Not supported | Needs heterogeneous tasks, domains, seeds, and failure cases |

Major missing details: environment names and versions, observation/action spaces, reward definitions, episode length, dataset collection policy, model-learning loss, ensemble size, uncertainty handling, planning horizon, MPC optimizer, replanning frequency, seeds, number of evaluation episodes, metric definitions, aggregation method, compute/tuning budgets, and ablations.

## model_error_and_planning_risk_table

| Risk | Severity | Evidence issue | Consequence | Minimal fix |
|---|---:|---|---|---|
| Model-error compounding is not directly audited | High | Packet says models are used for planning, but gives no rollout-error or calibration diagnostics | Planning gains may reflect short-horizon luck, simulator simplicity, or hidden tuning | Report one-step and multi-step prediction error, uncertainty calibration, and performance by planning horizon |
| Planning horizon is unspecified | High | MPC/latent planning are named, but horizon and replanning settings are omitted | Cannot tell whether claims concern long-horizon world modeling or short-horizon control | Pre-register horizon values, optimizer budget, replanning frequency, and horizon ablations |
| Model learning objective is underspecified | High | “Probabilistic dynamics” and “latent dynamics” are described only broadly | Cannot separate representation quality, likelihood fit, reward prediction, and control utility | State losses, targets, latent variables, reward/value terms, training schedule, and validation criteria |
| Model/planner contribution is not isolated | High | No ablation details included | Strong planning claims may actually depend on ensemble uncertainty, action optimizer, data collection, or representation | Add ablations: no planning, random-shooting/CEM variants, deterministic model, oracle/state model where appropriate |
| Pixel versus state inputs may make comparisons incompatible | Medium | PETS appears continuous-control dynamics; PlaNet plans from pixels | Cross-paper conclusions may conflate observation modality with method quality | Compare only within matched observation settings, or label cross-method comparison as non-equivalent |
| Evaluation variance is unknown | Medium | Seeds and repeated runs not included | Sample-efficiency and final-return rankings may be unstable | Use multiple seeds, confidence intervals, per-task results, and learning-curve variability |
| Baseline strength is unclear | Medium | Baselines are listed as evidence objects but not specified in packet | Reported gains may depend on weak or unfairly tuned baselines | Specify baseline algorithms, tuning budgets, input modality, compute, and data access |

## environment_and_seed_checklist

| Item | Required for audit | Status from packet |
|---|---|---|
| Environment/task names | Needed to assess task coverage and comparability | Missing |
| Simulator/version | Needed for reproducibility | Missing |
| Observation modality | Critical because PETS and PlaNet may differ on state vs pixel inputs | Partially present |
| Action space and reward definition | Needed to interpret control difficulty and metrics | Missing |
| Episode length/termination | Needed for return comparability | Missing |
| Training interaction budget | Needed for sample-efficiency claims | Missing |
| Evaluation episodes per checkpoint | Needed for variance control | Missing |
| Random seeds | Needed for uncertainty and reproducibility | Missing |
| Train/eval split or task sampling | Needed to avoid overfitting claims | Missing |
| Failure cases/negative tasks | Needed for claim boundaries | Missing |

## baseline_and_metric_review

The packet does not provide enough detail to judge whether baselines and metrics are fair. A valid comparison would need compatible observation modality, data budget, environment steps, compute budget, hyperparameter search, and evaluation protocol.

Metrics should include at minimum average episodic return, sample-efficiency curves versus real environment steps, final performance at fixed budgets, per-task results before aggregation, and uncertainty across seeds. For world-model planning specifically, the protocol should also report model prediction error, uncertainty calibration, planning-horizon sensitivity, and real-environment performance after executing planned actions.

The claim boundary should be tightened: the packet can support “these papers study model-based RL systems that learn dynamics models and use planning for continuous-control or pixel-control tasks.” It does not support a general claim that world-model planning is superior, robust, or broadly general without further protocol evidence.

## revised_protocol

1. Define environments exactly: task names, versions, observation modality, action space, reward, episode length, termination, and train/evaluation budgets.

2. Specify the learned world model: inputs, targets, probabilistic or latent variables, loss function, reward prediction, validation split, training frequency, ensemble or uncertainty method, and stopping criteria.

3. Specify planning: MPC or latent-space planner, horizon, action optimizer, number of candidate sequences/iterations, replanning frequency, terminal value use, and compute budget.

4. Add model-error controls: one-step and multi-step prediction error, calibration curves for probabilistic models, latent reconstruction or prediction diagnostics where applicable, and correlation between model error and control return.

5. Add planning ablations: no-planning policy baseline, deterministic model, shorter/longer horizons, planner budget sweep, uncertainty disabled, reward-model ablation, and model-free baseline under matched environment-step budgets.

6. Use fair baselines: same observation modality, same real-environment interaction budget, comparable tuning budget, reported hyperparameters, and identical evaluation episodes where possible.

7. Use robust evaluation: at least multiple random seeds, fixed evaluation intervals, enough episodes per checkpoint to estimate variance, confidence intervals or standard errors, and per-task results before aggregate summaries.

8. Bound claims explicitly: state whether conclusions apply to sample efficiency, final return, pixel-based control, continuous-control state tasks, short-horizon MPC, latent planning, or uncertainty-aware planning. Do not generalize beyond the evaluated tasks and protocols.
## OUTPUT: B3_final_for_validation

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
