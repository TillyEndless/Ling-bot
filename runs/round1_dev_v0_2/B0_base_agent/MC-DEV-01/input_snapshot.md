# Benchmark Task Input

Benchmark version: round1_dev_v0.2
Task ID: MC-DEV-01
Task type: method_comparison
Topic: LLM post-training
Evaluation mode: closed_source

## Research Question

How should DPO-style preference optimization and PPO-style RLHF be compared without overstating either method?

## User Prompt

Using only the provided source packet, compare DPO-style preference optimization and PPO-style RLHF.
Produce a comparison matrix covering objectives, assumptions, data requirements, optimization dynamics, baselines, evaluation protocols, and evidence limits.
Mark any claim not supported by the packet as unknown or speculative.


## Required Output Sections

- method_comparison_matrix
- assumptions_table
- evidence_strength_summary
- fairness_caveats
- scoped_conclusions

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.
