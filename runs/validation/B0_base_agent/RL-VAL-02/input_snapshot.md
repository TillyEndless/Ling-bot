# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `RL-VAL-02`
- Split: `validation`
- Task type: `rl_specific_analysis`
- Topic: reward modeling and post-training RL
- Research question: Does the provided reward-modeling or post-training RL protocol support its alignment or preference-learning claims?

## Input Prompt

Review the provided reward-modeling or post-training RL protocol using only the source packet.
Audit preference data, reward model validation, policy optimization setup, evaluation metrics, baseline policies, human or automated evaluation, reward hacking risks, and claim boundaries.
Return an RL-specific risk register and a revised protocol.


## Required Outputs

- rl_protocol_audit
- reward_model_validation_review
- policy_evaluation_checklist
- reward_hacking_and_proxy_risk_register
- revised_protocol

# Source Packet

# RL-VAL-02 Model Input Packet
## Sources
- Deep Reinforcement Learning from Human Preferences (arXiv:1706.03741; 2017). Local file: `christiano_2017_deep_rl_from_human_preferences.pdf`. Included evidence: Abstract; preference data; reward predictor; policy optimization; experiments.
- Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback (arXiv:2204.05862; 2022). Local file: `bai_2022_training_helpful_harmless_assistant_rlhf.pdf`. Included evidence: Abstract; preference models; RLHF; evaluations; limitations.

## Controlled Source Notes
- Deep RL from Human Preferences: trains reward predictors from human preference comparisons and uses reinforcement learning to optimize policies under learned rewards.
- Helpful and Harmless Assistant RLHF paper: uses preference models and RLHF-style optimization/evaluation for assistant behavior.
- Evidence objects: abstracts, preference-data/reward-model sections, policy-optimization sections, evaluation protocol, result tables/figures, and limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

