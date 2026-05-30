# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `PS-VAL-01`
- Split: `validation`
- Task type: `evidence_grounded_proposal_support`
- Topic: world-model planning
- Research question: Can the provided world-model planning idea be converted into a feasible, evidence-grounded research proposal?

## Input Prompt

Using only the provided source packet, turn the seed idea into a small research proposal.
Produce scoped research questions, evidence-grounded hypotheses, falsification criteria, required experiments, baselines, ablations, RL-specific evaluation details, and a risk register.
Separate packet facts, synthesis, and proposed hypotheses.


## Required Outputs

- scoped_research_questions
- hypothesis_table
- evidence_map
- experiment_plan
- rl_evaluation_protocol
- risk_register

# Source Packet

# PS-VAL-01 Model Input Packet
## Sources
- Dream to Control: Learning Behaviors by Latent Imagination (arXiv:1912.01603; 2019). Local file: `hafner_2019_dream_to_control.pdf`. Included evidence: Abstract; latent world model; imagination/planning/control; experiments.
- Mastering Atari with Discrete World Models (arXiv:2010.02193; 2020). Local file: `hafner_2020_mastering_atari_discrete_world_models.pdf`. Included evidence: Abstract; discrete world model; Atari evaluation; baselines.
- local_seed_world_model_planning.md (local_seed_brief; 2026). Local file: `local_seed_world_model_planning.md`. Included evidence: User/evaluator-provided seed idea or claim brief for proposal construction.

## Controlled Source Notes
- Dream to Control: learns latent dynamics models and uses latent imagination for behavior learning in control tasks.
- Mastering Atari with Discrete World Models: studies discrete world models for Atari and reports performance under Atari evaluation settings.
- Local seed brief: asks whether latent world-model planning remains useful under limited real-environment interaction and accumulated model error.
- Evidence objects: abstracts, method sections, experiment sections, baseline/result tables, and discussion/limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

