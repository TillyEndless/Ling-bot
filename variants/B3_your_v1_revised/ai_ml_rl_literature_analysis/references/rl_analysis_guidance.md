# RL Analysis Guidance

Use this reference for reinforcement learning and sequential-decision tasks.

## Core Distinctions

- Data collection policy versus learned policy.
- Offline training from fixed data versus online interaction.
- Simulator evaluation versus real-world deployment.
- Reward function, return metric, success metric, and normalized benchmark score.
- Behavior-policy support and learned-policy distribution shift.
- Environment version, wrappers, stochasticity, horizon, termination, and evaluation episodes.
- Policy value estimates versus actual rollout returns.

## Offline RL Checklist

| Item | What to extract |
|---|---|
| Dataset identity | Task, domain, version, collection regime, size if supplied. |
| Behavior policy | Known, unknown, mixture, expert, suboptimal, scripted, human, or generated. |
| Training mode | Fixed dataset only, online rollouts, model-based augmentation, or unclear. |
| Evaluation mode | Simulator rollout, logged-policy evaluation, off-policy estimate, real deployment, or unclear. |
| Metrics | Raw return, normalized score, success, regret, value estimate, or other. |
| Baselines | Behavior cloning, offline RL methods, online RL, random, expert, or task-specific baselines. |
| Variability | Seeds, runs, episodes, confidence intervals, or missing uncertainty. |
| Claim boundary | Benchmark performance, algorithmic property, deployment robustness, or generalization. |

## RL Failure Modes

- Treating trajectories as independent supervised examples while ignoring policy evaluation.
- Ignoring action-distribution shift or support mismatch.
- Equating normalized benchmark scores with universal absolute performance.
- Using offline value estimates as if they were verified returns.
- Generalizing simulator results to deployment without evidence.
