# Benchmark Task Input

Benchmark version: round1_dev_v0.2
Task ID: ERA-DEV-01
Task type: experimental_rigor_audit
Topic: agent evaluation
Evaluation mode: closed_source

## Research Question

Does the provided AgentBench-style agent-evaluation evidence support its claimed conclusion?

## User Prompt

Audit the provided experiment plan or paper excerpt for experimental rigor.
Focus on baselines, ablations, task selection, metrics, contamination risk, statistical reporting, reproducibility details, and claim scope.
Return severity-ranked findings and a corrected evaluation protocol.


## Required Output Sections

- rigor_audit_findings
- missing_baselines_and_ablations
- metric_claim_alignment_table
- reproducibility_risk_list
- corrected_protocol

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.
