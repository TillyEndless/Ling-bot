# RL-DEV-01 Model Input Packet

Task: RL-specific audit of an offline RL protocol.

Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.

## Corpus

1. D4RL: Datasets for Deep Data-Driven Reinforcement Learning, arXiv:2004.07219, 19-page arXiv PDF.
2. Conservative Q-Learning for Offline Reinforcement Learning, arXiv:2006.04779, 31-page arXiv PDF.

## Controlled Source Notes

D4RL:

- D4RL is a benchmark suite for offline RL datasets and tasks.
- The paper emphasizes dataset properties and difficulties important for offline RL, including narrow data, biased data, multitask data, suboptimal data, and non-representable behavior policies.
- It defines benchmark domains and normalized-score conventions.
- Evidence locations: abstract; Sections 1-4; dataset/task tables; score normalization discussion; limitations/discussion.

CQL:

- CQL addresses offline RL distributional shift by learning conservative Q-functions that lower-bound or penalize overestimated values for out-of-distribution actions.
- The paper evaluates on D4RL tasks and compares against prior offline RL methods and behavioral cloning.
- It reports normalized scores on gym, AntMaze, Adroit, kitchen, and Atari-style datasets in its experiment section.
- Evidence locations: abstract; Section 2 offline RL setup; Section 3 CQL method; Section 6; Tables 1-4; conclusion/limitations.

RL audit focus:

- Identify dataset source, behavior-policy assumptions, environment/version details, train/eval separation, baselines, metrics, seeds/runs, and uncertainty reporting.
- Check whether offline performance supports online performance, deployment, or generalization claims.
- Distinguish normalized benchmark score, actual environment return, and policy value estimates.

## Required Boundaries

- Do not treat offline RL as ordinary supervised learning.
- Do not infer online performance from offline benchmark results unless the packet directly supports it.
- Mark absent environment version, wrapper, seed, or evaluation-episode details as missing.

