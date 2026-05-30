# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `MC-VAL-01`
- Split: `validation`
- Task type: `method_comparison`
- Topic: policy optimization
- Research question: How should PPO and SAC be compared for continuous-control research without making unfair general claims?

## Input Prompt

Using only the provided source packet, compare PPO and SAC for continuous-control research.
Produce a method comparison matrix, assumptions table, benchmark/evaluation caveats, and scoped recommendations for when each method is appropriate.
Mark unsupported claims as unknown.


## Required Outputs

- method_comparison_matrix
- assumptions_table
- benchmark_protocol_review
- evidence_strength_summary
- scoped_recommendations

# Source Packet

# MC-VAL-01 Model Input Packet
## Sources
- Proximal Policy Optimization Algorithms (arXiv:1707.06347; 2017). Local file: `schulman_2017_proximal_policy_optimization_algorithms.pdf`. Included evidence: Abstract; clipped objective; adaptive KL; experiments.
- Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor (arXiv:1801.01290; 2018). Local file: `haarnoja_2018_soft_actor_critic.pdf`. Included evidence: Abstract; maximum entropy objective; off-policy setup; continuous-control experiments.

## Controlled Source Notes
- PPO paper: presents a policy-gradient method based on clipped surrogate objectives and discusses KL-penalty variants with continuous-control and Atari experiments.
- SAC paper: presents an off-policy maximum-entropy actor-critic method for continuous control with stochastic policies and benchmark experiments.
- Evidence objects: abstracts, objective/method sections, algorithms/equations, experiment sections, benchmark tables/figures, and limitations/discussion.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

