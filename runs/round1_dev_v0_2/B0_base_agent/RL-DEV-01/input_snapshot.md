# Benchmark Task Input

Benchmark version: round1_dev_v0.2
Task ID: RL-DEV-01
Task type: rl_specific_analysis
Topic: offline reinforcement learning
Evaluation mode: closed_source

## Research Question

Is the provided offline RL evaluation protocol sufficient to support the proposed claims?

## User Prompt

Review the provided offline RL protocol using only the source packet.
Audit dataset coverage, behavior policy assumptions, train/eval separation, environment details, metrics, baselines, seeds, uncertainty reporting, and offline-to-online claim boundaries.
Return an RL-specific risk register and a revised protocol.


## Required Output Sections

- rl_protocol_audit
- dataset_and_environment_checklist
- baseline_and_metric_review
- claim_scope_assessment
- revised_protocol

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.
