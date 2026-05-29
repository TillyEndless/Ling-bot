# RL-DEV-01 Model Input Packet

## Corpus

1. D4RL: Datasets for Deep Data-Driven Reinforcement Learning, arXiv:2004.07219, 19-page arXiv PDF.
2. Conservative Q-Learning for Offline Reinforcement Learning, arXiv:2006.04779, 31-page arXiv PDF.

## Controlled Source Notes

D4RL:

- D4RL is a benchmark suite for offline RL datasets and tasks.
- D4RL frames algorithms as training from static, previously collected datasets in the offline RL setting.
- Benchmark policy performance is evaluated through specified simulator-based evaluation and reported with normalized-return conventions.
- The paper emphasizes dataset properties and difficulties important for offline RL, including narrow data, biased data, multitask data, suboptimal data, and non-representable behavior policies.
- It defines benchmark domains and normalized-score conventions.
- The normalized score is defined using task- or domain-specific reference anchors.
- Appendix Tables 1-3 provide task identities, normalized scores, raw returns, and seed-reporting information.
- Evidence locations: p. 1 Abstract; p. 2 Introduction; Section 3 fixed dataset and behavior-policy framing; Sections 4-5 task design factors and task instantiations; p. 7 evaluation protocol and normalized-score definition; Appendix Tables 1-3; limitations/discussion.

CQL:

- CQL addresses offline RL distributional shift by learning conservative Q-functions that reduce optimistic value estimates for learned-policy actions unsupported or weakly supported by the offline dataset.
- The CQL objective regularizes Q-values under selected action distributions relative to dataset-supported behavior and provides lower-bound guarantees under stated assumptions.
- The paper evaluates on D4RL tasks and compares against prior offline RL methods and behavioral cloning.
- Tables 1 and 2 report normalized-score comparisons on D4RL domains, including Gym, AntMaze, Adroit, and Kitchen, averaged over four seeds.
- Table 3 reports Atari offline RL experiments.
- Table 4 reports estimated policy values and true returns on selected D4RL datasets in the paper's conservative-value analysis.
- Appendix p. 29 provides D4RL hyperparameter and four-seed reporting details.
- Evidence locations: p. 1 Abstract and Introduction; p. 2 Section 2 action distribution shift; p. 3 Section 3.1 conservative off-policy evaluation and lower-bound Q objective; p. 4 Section 3.2 Equations 3-4; p. 7 Section 6 and Table 1; p. 8 Table 2; p. 9 Table 4; Appendix p. 29; conclusion/limitations.

Additional source notes:

- Source materials discuss normalized benchmark score, actual environment return, and policy value estimates as separate quantities.
