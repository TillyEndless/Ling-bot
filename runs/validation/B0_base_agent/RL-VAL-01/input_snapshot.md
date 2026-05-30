# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `RL-VAL-01`
- Split: `validation`
- Task type: `rl_specific_analysis`
- Topic: model-based reinforcement learning
- Research question: Is the provided model-based RL protocol sufficient to evaluate world-model planning claims?

## Input Prompt

Review the provided model-based RL protocol using only the source packet.
Audit environment details, model-learning objective, planning horizon, model-error controls, baselines, seeds, evaluation episodes, metrics, and claim boundaries.
Return an RL-specific risk register and a revised protocol.


## Required Outputs

- rl_protocol_audit
- model_error_and_planning_risk_table
- environment_and_seed_checklist
- baseline_and_metric_review
- revised_protocol

# Source Packet

# RL-VAL-01 Model Input Packet
## Sources
- Deep Reinforcement Learning in a Handful of Trials using Probabilistic Dynamics Models (arXiv:1805.12114; 2018). Local file: `chua_2018_pets.pdf`. Included evidence: Abstract; probabilistic ensembles; model predictive control; experiments.
- Learning Latent Dynamics for Planning from Pixels (arXiv:1811.04551; 2018). Local file: `hafner_2018_planet.pdf`. Included evidence: Abstract; latent dynamics model; planning; DeepMind Control experiments.

## Controlled Source Notes
- PETS paper: uses probabilistic dynamics models and model predictive control for sample-efficient continuous-control reinforcement learning.
- PlaNet paper: learns latent dynamics from pixels and plans in latent space for control tasks.
- Evidence objects: abstracts, dynamics/model-learning sections, planning/control sections, experiment sections, baselines, result tables/figures, and limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

