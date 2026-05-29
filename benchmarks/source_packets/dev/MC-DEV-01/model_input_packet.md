# MC-DEV-01 Model Input Packet

Task: compare DPO-style preference optimization and PPO-style RLHF under fixed sources.

Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.

## Corpus

1. Direct Preference Optimization: Your Language Model is Secretly a Reward Model, arXiv:2305.18290, 27-page arXiv PDF.
2. Training language models to follow instructions with human feedback, arXiv:2203.02155, 68-page arXiv PDF.
3. Proximal Policy Optimization Algorithms, arXiv:1707.06347, 12-page arXiv PDF.

## Controlled Source Notes

DPO:

- DPO is presented as a direct method for optimizing a policy from preference data without fitting an explicit standalone reward model and then running RL.
- The derivation relies on a preference model such as Bradley-Terry and a KL-constrained reward-maximization framing.
- The paper compares DPO to PPO-style preference-learning baselines in selected sentiment and summarization settings.
- Evidence locations: abstract; Sections 3-4; Figure 2; Section 6; Table 1; appendices for derivations.

InstructGPT/RLHF:

- The paper describes a multi-stage alignment pipeline: supervised fine-tuning, reward modeling from human preference comparisons, and policy optimization with PPO.
- Its evidence concerns instruction-following model behavior under that pipeline and evaluation setup.
- Evidence locations: method sections on SFT, reward modeling, and RLHF/PPO; data collection description; evaluation protocol; main result tables; limitations.

PPO:

- PPO is a general policy-gradient reinforcement-learning algorithm using clipped or KL-penalized surrogate objectives.
- The paper evaluates PPO on benchmark RL tasks including continuous control and Atari.
- It is not itself a language-model preference optimization paper.
- Evidence locations: abstract; Sections 3-5; Algorithm 1; Section 6; Tables 1-6.

## Required Comparison Boundaries

- Do not rank DPO and PPO/RLHF universally.
- Separate algorithmic objective, data assumptions, reward-model assumptions, reference-policy assumptions, and evaluation settings.
- Mark direct comparisons, indirect comparisons, and non-comparable claims separately.
- Do not treat the PPO paper's RL benchmark evidence as direct evidence about RLHF for language models.

