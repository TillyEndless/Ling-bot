# Scoring Rubric

Score each dimension from 1 to 5. Keep dimensions separate; do not collapse them into one total score unless a later report explicitly defines a weighted decision rule.

## Scale

| Score | Meaning |
|---:|---|
| 5 | Excellent. Expert-useful, accurate, traceable, and complete for the task scope. |
| 4 | Strong. Minor omissions or calibration issues, but scientifically reliable. |
| 3 | Adequate. Useful with expert cleanup; some missing detail or weak organization. |
| 2 | Weak. Substantial omissions, unsupported reasoning, or poor task fit. |
| 1 | Unreliable. Misleading, unsupported, materially incorrect, or unsafe for research use. |

## Dimensions

### Factual Accuracy

Measures whether the output correctly states methods, assumptions, datasets, metrics, experimental findings, and limitations.

Strong outputs separate source claims from the agent's interpretation. Weak outputs misstate paper facts, confuse versions, invent details, or generalize beyond the source.

### Evidence Traceability

Measures whether substantive claims link to provided sources, source locations, evidence IDs, or retrieval results.

Strong outputs make it clear what each source supports and what it does not support. Weak outputs provide unsupported claims or citations that are only topically related.

### Citation Validity

Measures whether cited works exist, are identified correctly, and support the stated claim.

For closed-source tasks, citations must come from the source packet. For retrieval tasks, citations must follow fixed retrieval rules and include enough metadata to verify.

### Literature Coverage

Applies primarily to retrieval and literature-survey tasks. Measures whether the output includes canonical work, recent relevant work, and important contrasting lines of research.

Strong outputs document search strategy, coverage limits, and omissions. Weak outputs miss obvious core work or overfit to one source.

### Comparison Fairness

Measures whether methods are compared under compatible assumptions, datasets, metrics, compute, tuning effort, and evaluation protocols.

Strong outputs identify non-comparable settings and normalize conclusions. Weak outputs declare winners without accounting for task setup or baseline strength.

### Experimental Rigor

Measures handling of baselines, ablations, metrics, seeds, statistical uncertainty, compute, data splits, hyperparameter search, and reproduction risk.

Strong outputs distinguish confirmatory from exploratory evidence. Weak outputs ignore missing baselines, single-seed claims, metric mismatch, or leakage.

### Benchmark Validity

Measures whether benchmarks, datasets, tasks, metrics, and protocols are suitable for the claim being made.

Strong outputs identify contamination, leakage, saturation, protocol mismatch, metric gaming, and train/eval mismatch. Weak outputs treat a benchmark score as automatically meaningful.

### Inference-Boundary Discipline

Measures whether the output distinguishes source-supported conclusions, cross-paper synthesis, hypotheses, and speculation.

Strong outputs calibrate scope and uncertainty. Weak outputs launder speculation into conclusions or overstate causal/generalization claims.

### Hypothesis Quality

Applies primarily to proposal-support tasks. Measures whether hypotheses are grounded in evidence, falsifiable, scoped, feasible, and paired with disconfirming observations.

Strong outputs specify predictions, failure criteria, required evidence, and alternative explanations. Weak outputs generate attractive but untestable ideas.

### RL-Specific Correctness

Applies to RL tasks. Measures correctness about environment versions, wrappers, policies, reward functions, offline data, evaluation episodes, stochasticity, train/eval mismatch, and return distributions.

Strong outputs catch RL-specific failure modes. Weak outputs treat RL results like ordinary supervised-learning benchmarks.

### Output Usefulness

Measures whether the artifact supports a real research decision: reading, reviewing, planning, reproduction, proposal writing, or experimental design.

Strong outputs are structured, actionable, and concise enough to use. Weak outputs are polished but generic.

### Efficiency

Measures token cost, latency, tool calls, retrieval volume, and useful-information density.

High-quality but extremely inefficient outputs should be flagged. Efficient outputs must still satisfy reliability requirements.

## Hard-Fail Conditions

A task may receive an overall hard-fail flag if any of these occur:

- A hallucinated citation is presented as real.
- A critical claim is marked supported without direct evidence.
- A comparative conclusion is made without adequate baseline or setting normalization.
- An RL result is summarized from best seed/checkpoint only without disclosure.
- A causal interpretability claim is supported only by correlational evidence.
- A reproduction or experiment plan omits required data, environment, or evaluation protocol.
- Held-out gold annotation content appears in the output or prompt context.

## Scorecard Format

```yaml
run_id:
variant:
task_id:
reviewer:
scores:
  factual_accuracy:
  evidence_traceability:
  citation_validity:
  literature_coverage:
  comparison_fairness:
  experimental_rigor:
  benchmark_validity:
  inference_boundary_discipline:
  hypothesis_quality:
  rl_specific_correctness:
  output_usefulness:
  efficiency:
hard_fail:
  triggered: false
  reasons: []
findings:
  - severity: major|minor
    dimension:
    description:
    evidence:
summary:
```
