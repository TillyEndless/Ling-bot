## scoped_research_questions

**Packet Facts**

Dream to Control studies learned latent dynamics models and uses latent imagination for behavior learning in control tasks. Mastering Atari with Discrete World Models studies discrete world models for Atari and reports performance under Atari evaluation settings with baselines. The seed brief asks whether latent world-model planning remains useful under limited real-environment interaction and accumulated model error.

**Synthesis**

The feasible proposal should not ask whether world models work in general. The packet already supports that world-model behavior learning has been demonstrated in control and Atari settings. The sharper question is when latent imagination helps or hurts as real interaction is constrained and model rollout error grows.

**Scoped Research Questions**

1. Under fixed low real-environment interaction budgets, does behavior learning through latent imagination improve policy performance over comparable non-imagination or model-free baselines?
2. How does imagined rollout horizon affect return, stability, and model-error sensitivity?
3. Are discrete latent world models more robust than continuous latent world models in Atari-like visual domains when imagination horizons increase?
4. Can simple model-error controls, such as shorter imagination horizons or uncertainty/error-based rollout truncation, preserve the benefits of planning while reducing failure from accumulated model error?

## hypothesis_table

| ID | Proposed Hypothesis | Evidence Grounding | Falsification Criteria |
|---|---|---|---|
| H1 | Latent imagination improves sample efficiency under limited real interaction compared with policy learning without imagination. | Dream to Control uses latent dynamics and latent imagination for behavior learning in control tasks. The seed asks about limited real-environment interaction. | At matched environment-step budgets, imagination agents fail to outperform no-imagination variants on most tasks, or gains vanish across repeated seeds. |
| H2 | Longer imagined rollout horizons help only up to a point; excessive horizon length degrades performance because model error accumulates. | The seed explicitly raises accumulated model error. Dream to Control relies on imagined latent trajectories, making horizon length a direct mechanism. | Performance monotonically improves with longer horizons, or model-error metrics do not increase with horizon length. |
| H3 | Discrete world models are a strong candidate for Atari-like settings under limited interaction. | Mastering Atari with Discrete World Models studies discrete world models for Atari and reports Atari evaluation and baselines. | Discrete world-model variants do not match or exceed continuous/standard latent variants under the same Atari evaluation settings and interaction budgets. |
| H4 | Error-aware planning, such as truncating imagined rollouts when predicted uncertainty/error is high, improves reliability over fixed long rollouts. | Seed concern is accumulated model error; both cited works rely on learned world models, making rollout quality a central dependency. | Error-aware truncation does not improve return, variance, or catastrophic failure rate relative to fixed-horizon imagination. |

## evidence_map

| Claim Type | Packet Fact | How It Supports Proposal | Limitation |
|---|---|---|---|
| Packet fact | Dream to Control learns latent dynamics models. | Justifies using learned latent world models as the main method family. | Packet does not provide exact architecture or numeric results. |
| Packet fact | Dream to Control uses latent imagination for behavior learning in control tasks. | Grounds RQs about imagined rollouts, planning horizon, and sample efficiency. | Does not by itself prove robustness under severe model error. |
| Packet fact | Mastering Atari with Discrete World Models studies discrete world models for Atari. | Grounds Atari-like visual RL experiments and discrete latent ablations. | Packet omits exact table values and implementation settings. |
| Packet fact | Mastering Atari reports performance under Atari evaluation settings with baselines. | Supports including Atari evaluation protocol and baseline comparisons. | Exact baseline list must be selected conservatively from the packet description. |
| Packet fact | Seed brief asks whether latent world-model planning remains useful under limited real interaction and accumulated model error. | Defines the central empirical uncertainty. | The seed is a research prompt, not evidence that the effect exists. |
| Synthesis | Planning benefit should be measured at fixed real-environment budgets. | Directly tests whether imagination substitutes for real interaction. | Requires careful compute and update matching to avoid unfair comparisons. |
| Synthesis | Model-error accumulation should be tested by varying rollout horizon. | Horizon is the cleanest intervention on accumulated latent prediction error. | Error metrics may not perfectly correlate with control performance. |

## experiment_plan

**Experiment 1: Limited-Interaction Control Benchmark**

Purpose: Test whether latent imagination improves sample efficiency in control tasks.

Design:
- Train a Dream-to-Control-style latent world-model agent.
- Compare against a no-imagination ablation using the same encoder/world model where possible but learning behavior only from real collected transitions.
- Run multiple real-environment budgets: very low, low, medium.
- Report final return, learning curves, and area under the learning curve.

Baselines:
- No-imagination latent agent.
- Model-free RL baseline under the same environment-step budget.
- Random policy or simple non-learning policy as a sanity baseline.

Ablations:
- Imagined rollout horizon: short, medium, long.
- World-model update frequency.
- Planning/control objective with and without imagined trajectories.
- Same policy capacity with imagination disabled.

**Experiment 2: Horizon and Model-Error Accumulation**

Purpose: Directly test the seed concern that accumulated model error may erase planning benefits.

Design:
- Train world models on limited real data.
- Evaluate prediction error over imagined rollout depth.
- Train policies using different imagination horizons.
- Correlate model rollout error with downstream return.

Metrics:
- Return at fixed environment steps.
- Prediction error by rollout depth.
- Policy variance across seeds.
- Failure rate or severe return collapse.

Falsification:
- If long horizons produce no additional model error and consistently improve returns, H2 is falsified.

**Experiment 3: Atari-Like Discrete World Model Evaluation**

Purpose: Test whether discrete world models are more suitable for visual Atari settings.

Design:
- Implement or adapt a discrete latent world-model agent consistent with the Atari source.
- Evaluate under Atari-style settings from the packet.
- Compare against non-discrete latent world model and non-world-model baselines.

Baselines:
- Atari model-free baseline.
- Continuous latent world-model variant.
- No-imagination discrete world-model variant.

Ablations:
- Discrete vs continuous latent representation.
- Imagined horizon length.
- Real-data budget.
- Planning with fixed horizon vs error-aware truncation.

**Experiment 4: Error-Aware Planning**

Purpose: Test whether model-error controls preserve planning gains.

Design:
- Add rollout truncation based on learned or held-out model prediction error.
- Compare to fixed short, medium, and long horizons.
- Evaluate both control and Atari-like tasks.

Expected useful outcome:
- Even if full world-model planning fails under long horizons, the study can identify regimes where short-horizon or error-aware imagination remains useful.

## rl_evaluation_protocol

Use matched real-environment interaction budgets across all agents. The main independent variable is access to latent imagination, not additional real samples.

Evaluation requirements:
- Report learning curves over real environment steps.
- Use identical environment-step budgets for all methods.
- Use multiple random seeds and report variability.
- Evaluate final policies without exploration noise where appropriate.
- Track both task return and model-prediction error.
- Separate training-time imagined steps from real environment steps in all reporting.
- Include compute/update counts so imagination methods are not silently given much larger optimization budgets.
- For Atari-like tasks, use the Atari evaluation setting referenced by the packet source and compare to baselines under that same setting.
- Include low-budget regimes because the seed specifically concerns limited real interaction.
- Include horizon sweeps because accumulated model error is the key failure mode.

Primary metrics:
- Final episodic return.
- Sample efficiency: return at fixed real-step budgets.
- Area under learning curve.
- Variance across seeds.
- Model rollout error as a function of imagined depth.

Decision rule:
- The idea is supported if imagination-based agents outperform matched baselines in low-interaction regimes and if horizon/error-aware ablations show a controllable tradeoff between planning benefit and model-error accumulation.
- The idea is weakened if gains disappear under fair step/update matching or if imagined rollouts systematically reduce return as model error grows.

## risk_register

| Risk | Why It Matters | Mitigation |
|---|---|---|
| Model-based agents get more compute than baselines. | Apparent sample efficiency may reflect extra optimization, not better use of data. | Report real steps, imagined steps, gradient updates, and wall-clock or compute proxies separately. |
| Accumulated model error causes misleading imagined rewards/states. | This is the seed’s central concern. | Sweep imagination horizon and add error-aware rollout truncation. |
| Exact source implementation details are missing from packet. | Full reproduction may be underspecified. | Treat the proposal as a small comparative study; clearly document implementation choices. |
| Atari and control tasks may favor different latent representations. | Results may not generalize across domains. | Analyze control and Atari-like settings separately before making cross-domain claims. |
| Baseline selection may be unfair. | Weak baselines could overstate world-model planning value. | Include no-imagination, model-free, random/sanity, discrete/continuous variants where applicable. |
| Prediction error may not correlate with policy performance. | Model metrics alone may not explain RL outcomes. | Report both model-error curves and downstream return. |
| Low interaction budgets may be too low for stable world-model learning. | All methods could fail, making conclusions uninformative. | Use several budgets, including a minimally viable medium budget. |
| High variance across RL seeds may obscure effects. | False positives or negatives are likely in RL. | Use repeated seeds and report confidence intervals or variability summaries. |