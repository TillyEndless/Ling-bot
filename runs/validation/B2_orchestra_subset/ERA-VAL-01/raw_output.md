## rigor_audit_findings

| Severity | Claim affected | Evidence issue | Consequence | Minimal fix |
|---|---|---|---|---|
| High | “The evaluation supports broad model capability.” | The packet only states that GPT-3 was evaluated across many NLP tasks and that MMLU measures knowledge and reasoning across many subjects. Exact task coverage, scores, splits, prompts, and result tables are not included. | Broad capability claims are under-supported because the supplied evidence lacks enough detail to verify representativeness, per-task behavior, or failure modes. | Report per-task results, task categories, prompt formats, scoring rules, and aggregate construction. |
| High | “Benchmark performance reflects uncontaminated capability.” | GPT-3 includes contamination analysis discussion, but the packet does not provide the overlap rates, affected benchmarks, filtering method, or sensitivity results. MMLU construction/evaluation notes are present only at a high level. | Contamination cannot be ruled out. Scores may overestimate capability if test items or close variants appeared in pretraining or prompt-development data. | Add dataset provenance checks, train-test overlap analysis, near-duplicate detection, and contaminated-vs-clean subset reporting. |
| High | “Performance gains imply better reasoning or knowledge.” | Improvement claims require direct compatible baselines. The packet says both papers report model results, but omits baseline identities, tuning fairness, compute, prompt budgets, and exact metrics. | Model superiority or reasoning improvement claims are not established from the supplied packet. | Compare against clearly specified baselines under identical prompts, scoring, data access, and evaluation budgets. |
| Medium | “Aggregate benchmark scores are meaningful.” | The packet does not include aggregation formulas, per-subject MMLU results, weighting, variance, or calibration details. | Aggregate scores may hide benchmark saturation, subject imbalance, or uneven performance. | Preserve per-task and per-subject results; define macro/micro aggregation; report uncertainty. |
| Medium | “Prompt protocol is stable.” | GPT-3 reports zero-shot, one-shot, and few-shot settings; MMLU reports defined evaluation settings. The packet does not include prompt templates, demonstration selection, ordering, or prompt search details. | Prompt sensitivity and protocol overfitting remain unresolved risks. | Pre-register prompt templates, demonstration selection rules, number of trials, and prompt tuning constraints. |
| Medium | “Reported results are statistically reliable.” | The packet does not include repeated runs, seeds, confidence intervals, bootstrap estimates, or variance across prompts/items. | Differences may be noise, especially for small subject subsets or prompt-sensitive tasks. | Report confidence intervals, paired tests where applicable, seed counts, and prompt-sampling variance. |
| Low | “Benchmark limitations are acknowledged.” | Both source notes mention limitations, but the packet does not include their exact scope. | The audit cannot determine whether the original claims were properly calibrated. | Quote or summarize limitation sections and align final claims to them. |

## contamination_and_leakage_risk_table

| Risk | Evidence from packet | Severity | Why it matters | Required check |
|---|---|---:|---|---|
| Pretraining test-set contamination | GPT-3 paper includes contamination analysis discussion. Exact details omitted. | High | Large web-scale corpora may contain benchmark test examples or near-duplicates. | Exact-match and near-duplicate overlap against train corpus; report affected items and clean-subset scores. |
| Benchmark saturation | GPT-3 evaluated on many existing NLP benchmarks; MMLU introduced a broad multitask benchmark. Exact score distributions omitted. | Medium | Saturated tasks can exaggerate apparent generality or fail to distinguish models. | Include human, random, prior SOTA, and strong contemporary baselines; inspect ceiling effects per task. |
| Prompt leakage or prompt tuning leakage | Zero-/one-/few-shot settings noted, but prompt construction details omitted. | Medium | Development on test examples or repeated prompt iteration can leak evaluation signal. | Separate dev set for prompt selection; freeze prompts before test evaluation; log all prompt trials. |
| Evaluation-set leakage through examples | Few-shot evaluation uses demonstrations; demonstration sourcing not specified in packet. | Medium | Demonstrations may overlap with test distribution or include answer patterns that bias results. | Document demonstration pool, exclusion rules, and retrieval/selection procedure. |
| MMLU item exposure | MMLU benchmark construction and limitations noted, but contamination checks are not described in packet. | High | Public benchmark items can later enter training or prompt-selection workflows. | Use hidden or refreshed test sets; track release date relative to model training data cutoff. |
| Metric leakage or answer-format artifacts | Metrics and scoring details omitted. | Medium | Multiple-choice format or answer tokenization can create shortcuts unrelated to claimed reasoning. | Validate scoring rules, answer normalization, and artifact-only baselines. |

## baseline_and_metric_review

| Dimension | Supplied evidence | Rigor assessment | Needed for stronger support |
|---|---|---|---|
| Baselines | Packet says benchmark result tables exist, but identities and setup are omitted. | Insufficient for improvement claims. | Name all baselines, model sizes, training data assumptions, prompt settings, and tuning budgets. |
| Metrics | Packet references benchmark evaluations and result tables but omits metric definitions. | Insufficient to judge alignment with capability claims. | Define accuracy/F1/exact match/etc.; explain aggregation and task weighting. |
| Prompt protocol | GPT-3 includes zero-shot, one-shot, few-shot settings; MMLU has defined evaluation settings. | Partially supported, but not auditable from packet. | Provide exact templates, examples, ordering, sampling, and prompt-search policy. |
| Statistical reporting | No uncertainty details included in packet. | Weak support for fine-grained comparisons. | Report confidence intervals, standard errors, paired bootstrap or randomization tests, and variance across prompts. |
| Per-task reporting | Source notes mention many tasks and result tables, but not values. | Aggregate claims cannot be checked. | Include per-task and per-subject scores before any aggregate conclusion. |
| Human or expert reference | MMLU is described as measuring knowledge and reasoning across subjects, but reference levels are not included. | Cannot calibrate absolute capability. | Include human/expert, random, majority, and simple retrieval or artifact baselines where relevant. |

## claim_scope_assessment

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|
| GPT-3 was evaluated in zero-shot, one-shot, and few-shot settings across many NLP tasks. | Descriptive | Source description of evaluation setup. | Controlled notes state this directly. | Supported at high level. | The packet supports only the existence of these evaluation modes, not exact performance strength. |
| GPT-3 results demonstrate broad few-shot language capability. | Generalization / improvement | Heterogeneous tasks, compatible baselines, metrics, and contamination controls. | Many-task evaluation and contamination discussion are noted, but details are omitted. | Partially supported, scope-limited. | May claim evaluated performance across included benchmarks, with unresolved contamination and protocol caveats. |
| MMLU measures multitask language understanding across knowledge and reasoning subjects. | Benchmark-validity | Task/metric/protocol analysis and limitations. | MMLU benchmark design and protocol are noted. | Partially supported. | May describe MMLU as intended to measure broad multitask knowledge/reasoning, not as definitive proof of general intelligence. |
| Scores on these benchmarks prove uncontaminated model capability. | Benchmark-validity / causal | Strong contamination exclusion, leakage controls, and clean-subset analysis. | Packet lacks exact contamination rates and leakage controls. | Not supported. | Only claim performance under the reported benchmark protocols, with contamination risk unresolved. |
| Higher benchmark scores imply better reasoning. | Causal / improvement | Controlled comparisons plus ablations or mechanism-isolating evidence. | No mechanism evidence or ablations included in packet. | Not supported. | At most, higher scores indicate better performance on the evaluated tasks under the specified protocol. |

## corrected_protocol

1. **Define the claim before evaluation.** State whether the target claim is benchmark performance, few-shot adaptation, factual knowledge, reasoning, or broad generalization. Avoid claiming reasoning ability from benchmark accuracy alone.

2. **Use contamination controls.** Record model training data cutoff, benchmark release dates, dataset provenance, exact-match overlap, near-duplicate overlap, and paraphrase-level similarity. Report results on full, flagged, and clean subsets.

3. **Freeze the prompt protocol.** Pre-register prompt templates, demonstration counts, example selection rules, ordering, answer format, decoding settings, and allowed prompt-development data. Do not tune prompts on the test set.

4. **Select compatible baselines.** Include random, majority or simple heuristic baselines, prior published systems, same-family smaller models, and strong contemporary models where available. Match evaluation data access, prompt budget, decoding, and scoring.

5. **Report metrics transparently.** Provide metric definitions, answer normalization, aggregation formula, task weights, and per-task/per-subject results. Do not rely only on a headline aggregate.

6. **Quantify uncertainty.** Run repeated prompt samples or seeds where applicable. Report confidence intervals and paired significance tests for model comparisons.

7. **Audit leakage paths.** Separate training, development, prompt-selection, and test data. Log all prompt trials and exclude test examples from demonstrations or prompt engineering.

8. **Check benchmark saturation.** Compare against human/expert references, prior SOTA, and ceiling effects. If many tasks are saturated, use harder held-out or newly constructed evaluations.

9. **Preserve failure analysis.** Report low-performing tasks, contaminated subsets, prompt-sensitive cases, and answer-format artifacts.

10. **Calibrate final claims.** The defensible claim should be: “The model achieved the reported results under the specified benchmark and prompting protocol, subject to unresolved or quantified contamination, leakage, and prompt-sensitivity risks.”