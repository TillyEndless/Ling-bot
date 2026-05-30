## Source Inventory

Sources in packet: `Dream to Control: Learning Behaviors by Latent Imagination` (2019), `Mastering Atari with Discrete World Models` (2020), and `local_seed_world_model_planning.md` (2026). Evidence objects named by the packet: abstracts, latent/discrete world-model method sections, imagination/planning/control material, experiment sections, baseline/result tables, Atari evaluation, discussion/limitations, and seed brief. Exact numeric results, full tables, appendix details, and implementation settings are not included.

## scoped_research_questions

1. Under limited real-environment interaction, when does latent world-model planning or imagination improve policy learning compared with direct model-free or behavior-cloning-style baselines?
   - Label: `SPECULATIVE_PROPOSAL`
   - Grounding: packet states Dream to Control uses latent dynamics and latent imagination for behavior learning; seed asks about limited real interaction and model error.

2. How does accumulated model error affect downstream planning quality as imagination horizon increases?
   - Label: `SPECULATIVE_PROPOSAL`
   - Grounding: seed brief explicitly raises accumulated model error; packet notes world-model imagination/planning/control evidence.

3. Are discrete latent world models more robust than continuous/standard latent models under long-horizon imagined rollouts in Atari-style environments?
   - Label: `SPECULATIVE_PROPOSAL`
   - Boundary: the packet supports that a discrete world-model Atari study exists, but does not provide enough detail to claim discrete models are generally more robust.

4. Which diagnostics best predict when imagined rollouts help versus harm control performance?
   - Label: `SPECULATIVE_PROPOSAL`
   - Candidate diagnostics: model prediction loss, latent rollout consistency, imagined-horizon sensitivity, real rollout return gap.

## hypothesis_table

| Hypothesis | Evidence basis | Support label | Falsification criteria |
|---|---|---:|---|
| H1: Latent imagination improves sample efficiency when real-environment interaction is limited, but only up to a task-dependent planning horizon. | Dream to Control learns behavior via latent imagination; seed asks about limited real interaction and accumulated model error. | `SPECULATIVE_PROPOSAL` | No improvement over non-imagination baselines at any interaction budget, or performance monotonically improves with horizon without degradation. |
| H2: Longer imagined rollouts eventually reduce policy quality because model error compounds. | Seed brief directly raises accumulated model error. | `SPECULATIVE_PROPOSAL` | Long-horizon planning shows no increase in prediction error and no return degradation relative to short-horizon planning. |
| H3: Discrete world models may show different error/return tradeoffs from latent continuous world models in Atari-style settings. | Mastering Atari studies discrete world models for Atari; Dream to Control uses latent imagination for control. | `WITHIN_PACKET_SYNTHESIS` / `SPECULATIVE_PROPOSAL` | Under matched budgets and evaluation, discrete and non-discrete variants have indistinguishable error curves and return curves. |
| H4: Model-error diagnostics can predict whether planning helps before full policy evaluation. | Seed concern links model error to planning usefulness. | `SPECULATIVE_PROPOSAL` | Diagnostics fail to correlate with later real-environment return or cannot distinguish helpful from harmful planning settings. |

## evidence_map

| Claim | Claim type | Evidence-burden label | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|---|
| Dream to Control learns latent dynamics models and uses latent imagination for behavior learning. | Method definition | `DIRECT_PACKET_EVIDENCE` | Controlled Source Notes; abstract/method evidence objects | Direct | Source-level description only | Exact architecture, losses, horizons, metrics |
| Mastering Atari studies discrete world models for Atari and reports performance under Atari evaluation settings. | Method/benchmark result | `DIRECT_PACKET_EVIDENCE` | Controlled Source Notes; abstract/evaluation/baseline tables | Direct | Source-level description only | Exact scores, games, evaluation protocol |
| The seed proposal concerns limited real-environment interaction and accumulated model error. | Proposal motivation | `DIRECT_PACKET_EVIDENCE` | local_seed brief note | Direct | Seed scope | Specific tasks and budgets |
| Comparing continuous latent imagination and discrete Atari world models requires matched setups. | Comparison boundary | `LIMITED_CRITIQUE` | Packet states different source domains and missing details | Indirect | Proposal design constraint | Model sizes, budgets, metrics, exact tasks |
| Claims of general superiority are not supported by the packet. | Inference boundary | `LIMITED_CRITIQUE` | Packet scope notes missing numeric tables and settings | Indirect | This proposal only | External literature and full papers needed |

## experiment_plan

Primary experiment: vary real-environment interaction budget and imagination horizon, then measure real-environment return and model-error diagnostics.

Independent variables:
- Real interaction budget: low, medium, high.
- Planning/imagination horizon: none, short, medium, long.
- World-model type: latent model inspired by Dream to Control; discrete latent model inspired by Mastering Atari where applicable.

Baselines:
- No-world-model policy learning baseline.
- World model trained but no imagined planning.
- Short-horizon imagination baseline.
- Behavior-cloning or supervised policy baseline if logged data is available.
- Random or task-default baseline where appropriate.

Ablations:
- Remove latent imagination while keeping model learning.
- Vary imagination horizon.
- Vary model update frequency.
- Discrete versus non-discrete latent state representation, if implementable under matched compute.
- Train policy on imagined rollouts only versus mixed real and imagined rollouts.

Metrics:
- Real-environment episodic return or task success.
- Sample efficiency at fixed interaction budgets.
- Model prediction loss or latent rollout error.
- Return gap between imagined evaluation and real rollout evaluation.
- Sensitivity of performance to horizon length.

Required reporting:
- Environment versions, wrappers, action spaces, horizons, reward definitions.
- Number of seeds/runs and uncertainty intervals.
- Hyperparameters, model size, training budget, and compute.
- Full baseline settings and raw evaluation outputs.

## rl_evaluation_protocol

Training/evaluation distinction:
- Train world models from fixed or incrementally collected real-environment trajectories.
- Train policies using imagined rollouts according to specified horizons.
- Evaluate only with real-environment or simulator rollouts, not imagined returns alone.

RL details to specify:
- Dataset collection policy: random, exploratory policy, prior agent, or online learner.
- Whether training is offline-only, online, or hybrid.
- Reward function and episode termination rules.
- Environment version and stochasticity.
- Evaluation episodes per seed.
- Seeds/runs and confidence intervals.
- Distribution shift between behavior data and learned policy actions.
- Whether model rollout states remain within behavior-policy support.

Claim boundaries:
- Benchmark performance does not establish deployment robustness.
- Model-error diagnostics do not prove mechanism unless intervention/ablation confirms they causally affect planning performance.
- Atari-style results and continuous-control results should not be merged into a universal ranking unless protocols are matched.

## risk_register

| Risk | Label | Why it matters | Mitigation |
|---|---|---|---|
| Model error compounds during imagined rollouts. | `DIRECT_PACKET_EVIDENCE` for seed concern; `SPECULATIVE_PROPOSAL` for mitigation | Could make planning harmful at longer horizons. | Horizon sweep; compare imagined-return estimates with real rollout returns. |
| Cross-domain comparison between control tasks and Atari is unfair. | `LIMITED_CRITIQUE` | Packet sources involve different evaluation settings. | Keep domain-specific conclusions separate; run matched environments where possible. |
| Missing exact source details limit reproduction. | `DIRECT_PACKET_EVIDENCE` | Packet states numeric values, full tables, appendix details, and implementation settings are not included. | Treat proposal as design-level; require full configs before empirical claims. |
| Baselines may be underpowered or unfairly tuned. | `LIMITED_CRITIQUE` | Without full baseline details, performance claims are weak. | Pre-register baseline tuning budgets and shared compute limits. |
| Diagnostics may correlate with return without explaining causal mechanism. | `LIMITED_CRITIQUE` | Could overclaim model-error mechanism. | Include intervention ablations that deliberately vary model quality or horizon. |
| Limited-budget findings may not generalize to high-budget or deployment settings. | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | Packet does not establish external validity. | Report scope narrowly and require external validation before broad claims. |