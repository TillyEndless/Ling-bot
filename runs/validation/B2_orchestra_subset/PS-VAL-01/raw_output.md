## scoped_research_questions

1. Under limited real-environment interaction, does latent world-model planning improve policy performance compared with model-free RL baselines in control and Atari-like settings?
2. How does accumulated model error during imagined rollouts affect downstream policy quality?
3. Do discrete world models offer better robustness to long imagined rollouts than continuous latent world models in Atari-like domains?
4. What rollout horizon, planning frequency, or imagination depth best trades off sample efficiency against model-error accumulation?

Provenance separation:

- Packet facts: Dream to Control learns latent dynamics models and uses latent imagination for behavior learning in control tasks. Mastering Atari with Discrete World Models studies discrete world models for Atari and reports performance under Atari evaluation settings. The seed asks whether latent world-model planning remains useful under limited real interaction and accumulated model error.
- Synthesis: The proposal can compare world-model planning usefulness across interaction budgets, rollout horizons, and world-model representation types.
- Proposed hypotheses: The specific claims below are testable proposal hypotheses, not established packet findings.

## hypothesis_table

| Hypothesis | Type | Evidence grounding | Falsification criteria | Scope |
|---|---|---|---|---|
| H1: Latent world-model planning improves sample efficiency under low real-environment interaction budgets versus model-free RL. | Improvement | Source-derived grounding: Dream to Control uses latent imagination for behavior learning; Atari discrete world-model work evaluates world models against baselines. | Falsified if world-model planning fails to outperform matched model-free baselines at low budgets across predefined tasks and metrics. | Limited-budget control and Atari-like tasks only. |
| H2: Longer imagined rollouts initially help but eventually degrade policy learning because model error accumulates. | Causal/mechanism proposal | Source-derived seed concern: accumulated model error; source-derived world-model imagination/planning setup. | Falsified if performance is monotonic with rollout horizon or if measured model error does not correlate with policy degradation. | Imagined-rollout planning regimes in learned latent models. |
| H3: Discrete latent world models are more robust than continuous latent models on Atari-like domains under the same interaction budget. | Improvement/comparison | Source-derived: Mastering Atari studies discrete world models for Atari; Dream to Control uses latent dynamics and imagination in control tasks. | Falsified if discrete models do not outperform or show lower rollout-error sensitivity than continuous alternatives under matched protocol. | Atari-like domains; not general control unless separately tested. |
| H4: Adaptive short-horizon planning outperforms fixed long-horizon planning when the world model is imperfect. | Proposal | Agent-proposed from seed concern about accumulated model error. | Falsified if fixed long horizons match or exceed adaptive planning across seeds without higher model-error penalties. | Planning with learned world models under limited environment interaction. |

## evidence_map

| Evidence item | Provenance | Supports | Limitations |
|---|---|---|---|
| Dream to Control learns latent dynamics models and uses latent imagination for behavior learning in control tasks. | source-derived | Feasibility of latent world-model imagination for control. | Exact metrics, baselines, and implementation details are not included in the packet. |
| Mastering Atari with Discrete World Models studies discrete world models for Atari and reports evaluation against baselines. | source-derived | Feasibility of discrete world models and Atari evaluation framing. | Exact scores, tables, and protocol details are omitted. |
| Seed asks whether planning remains useful with limited real interaction and accumulated model error. | source-derived | Central research question and threat model. | Does not itself provide empirical evidence. |
| Comparing rollout horizons can expose model-error accumulation. | agent-inferred | H2 and ablation design. | Requires direct measurement of model prediction error and policy performance. |
| Comparing continuous and discrete latent models may test representation robustness. | cross-source synthesis | H3. | Packet does not establish that tasks, architectures, or budgets are directly comparable across original papers. |

## experiment_plan

| Experiment | Purpose | Required setup | Baselines | Ablations | Success condition |
|---|---|---|---|---|---|
| E1: Limited-budget control benchmark | Test H1 in control tasks. | Train world-model planning agents under fixed low, medium, and high real-interaction budgets. | Model-free RL matched for interaction budget; no-imagination latent agent if available. | Rollout horizon, model update frequency, planning frequency. | World-model planning improves return or sample efficiency at low budgets with uncertainty reported. |
| E2: Atari-like discrete world-model benchmark | Test H1 and H3 in Atari-like settings. | Evaluate discrete world-model planning under Atari protocol. | Atari model-free baseline; continuous latent world-model variant if implemented. | Discrete vs continuous latent state; imagination horizon; action-repeat/frame preprocessing if relevant. | Discrete model shows better limited-budget performance or lower sensitivity to rollout length. |
| E3: Model-error accumulation study | Test H2. | Measure latent prediction error or reconstruction/prediction quality across imagined rollout lengths. | Short-horizon planning; model-free baseline not using imagination. | Horizons such as 1, 5, 15, 30 imagined steps; teacher-forced vs free rollout prediction. | Performance degrades when measured rollout error exceeds a predefined threshold. |
| E4: Adaptive horizon planning | Test H4. | Stop or shorten imagination when model uncertainty/error proxy is high. | Fixed short horizon; fixed long horizon. | Error threshold, uncertainty proxy, horizon cap. | Adaptive horizon improves return or reduces variance over fixed long horizon. |

## rl_evaluation_protocol

- Tasks: include at least one continuous-control setting aligned with Dream to Control’s control focus and at least one Atari-like setting aligned with the discrete world-model paper.
- Metrics: report episode return, sample efficiency curves, area under learning curve, final performance at fixed interaction budgets, and model prediction/error metrics over imagined rollout length.
- Interaction budgets: define low, medium, and high real-environment step budgets before training; do not tune budgets post hoc.
- Baselines: include matched model-free RL, world-model agent without imagined rollouts, fixed short-horizon planning, fixed long-horizon planning, and where feasible continuous vs discrete world-model variants.
- Seeds and uncertainty: run multiple random seeds and report mean, variance or confidence intervals, and per-task results before aggregate scores.
- Fairness controls: match real-environment interaction, observation preprocessing, action space, reward normalization, network capacity where possible, optimizer budget, and hyperparameter search budget.
- Leakage controls: separate training/evaluation episodes; avoid using evaluation returns to tune rollout horizon or model-selection criteria.
- Aggregation: preserve per-task learning curves and only aggregate after normalizing or otherwise justifying cross-task comparability.
- Failure reporting: report negative results, unstable training, high model-error regimes, and cases where planning underperforms model-free RL.

## risk_register

| Risk | Severity | Claim affected | Consequence | Minimal mitigation |
|---|---:|---|---|---|
| Baselines are weaker or less tuned than the world-model method. | High | H1, H3 | Apparent improvement may reflect unfair comparison. | Use published strong baselines where available and equalize tuning budgets. |
| Model-error metric is poorly aligned with control performance. | High | H2, H4 | Error analysis may not explain policy degradation. | Measure both prediction error and downstream return; test correlation explicitly. |
| Continuous-control and Atari results are over-aggregated. | Medium | Generalization claims | Proposal may imply broader validity than supported. | Report domains separately and avoid unrestricted generalization. |
| Exact source tables and implementation details are missing from the packet. | Medium | Reproducibility | Proposal cannot lock exact hyperparameters or expected numeric thresholds. | Treat numeric targets as preregistered design choices to be filled from full papers or pilot runs. |
| Adaptive horizon uses evaluation feedback indirectly. | Medium | H4 | Protocol overfitting could inflate results. | Select thresholds on validation tasks or training-only model-error proxies. |
| Limited interaction budget makes results high variance. | Medium | H1 | False negatives or false positives across seeds. | Increase seeds, report confidence intervals, and include learning curves. |
| Discrete vs continuous model comparison changes too many variables. | High | H3 | Representation effect may be confounded by architecture or optimization differences. | Keep architecture, capacity, training data, and optimizer as matched as possible; ablate only representation where feasible. |