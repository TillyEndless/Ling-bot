## rigor_audit_findings

**High severity: Overall score can overstate broad “agent” capability.**  
The overall AgentBench score is aggregated after resizing task scores and weighting tasks by reciprocal average model performance. That makes difficult environments disproportionately influential and turns the headline score into a benchmark-specific construct, not a direct measure of general agent ability. The evidence supports “performance under this aggregation,” but not a broad claim that one model is generally the best agent.

**High severity: Baseline coverage is unclear for non-LLM and tool-specific agent strategies.**  
The packet reports 29 API-based and open-sourced LLMs, but does not indicate strong non-LLM, scripted, retrieval-based, tool-specific, or human baselines. Without these, it is hard to know whether failures reflect LLM agent weakness, environment difficulty, prompt/interface design, or solvability.

**High severity: Task selection may not justify generalization across agent settings.**  
The benchmark covers eight environments, including OS, database, web-shopping, web-browsing, household, game, and knowledge-graph tasks. This is broad, but the packet does not establish that task distributions are representative of real agent use cases or balanced across difficulty, interaction length, tool affordances, and domain familiarity.

**Medium severity: Metric heterogeneity weakens direct comparison.**  
Table 2 uses success rate for several environments, but also F1, reward, game progress, and step success rate. These metrics measure different things. Aggregating them into one score risks mixing final-task completion, partial progress, semantic accuracy, and procedural compliance.

**Medium severity: Contamination risk is not adequately resolved from the packet.**  
The source notes do not describe train/test leakage checks, task release timing controls, web task freshness, prompt exposure controls, or whether model providers may have seen benchmark tasks. This matters because AgentBench-style tasks can be memorized or optimized against once public.

**Medium severity: Statistical reporting appears incomplete.**  
The packet mentions model comparisons and environment-specific performance, but not confidence intervals, repeated runs, variance across seeds/prompts, significance tests, or uncertainty around overall rankings. Single-point scores are weak evidence for close model ordering.

**Medium severity: Execution failures are reported but not fully tied to metric interpretation.**  
Section 2 defines Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded, and Table 4 reports aggregate proportions. That is useful, but aggregate outcome proportions do not by themselves explain whether a model’s score reflects reasoning ability, interface brittleness, prompt-following, context length, or action-space mismatch.

**Low severity: Reproducibility details are promising but incomplete from the packet.**  
The evaluation toolkit, task workers, Docker/worker isolation, and prompt setup improve reproducibility. Still, the packet does not confirm exact prompts, task instances, model versions, decoding parameters, API dates, retry policy, environment seeds, scoring scripts, or raw traces.

## missing_baselines_and_ablations

**Missing baselines:**

- Human expert or human average performance per environment.
- Random-action and majority/default-action baselines.
- Simple scripted agents for structured environments such as OS, database, and knowledge-graph tasks.
- Retrieval-augmented baselines where external knowledge or document lookup is relevant.
- Tool-specific non-agent baselines, especially SQL solvers for database tasks and web automation scripts for web tasks.
- Smaller local models with identical prompting and tool interfaces, separated from API model comparisons.
- “No-interaction” or single-turn LLM baselines to isolate the value of iterative agent interaction.
- Oracle-format baselines to separate reasoning failure from invalid action or invalid format failure.

**Missing ablations:**

- Prompt-template ablation across all environments.
- Tool-description and action-schema ablation.
- Context-window ablation, especially given Context Limit Exceeded as an outcome category.
- Maximum-step-budget ablation.
- Temperature/decoding ablation.
- Environment-order or task-order ablation.
- Aggregation-weight ablation comparing reciprocal-performance weighting against equal weighting and per-category weighting.
- Metric-normalization ablation showing whether rankings change under alternative score resizing.
- Task-category removal ablation, e.g. removing web-grounded or game-grounded tasks to test ranking stability.
- Failure-mode ablation separating invalid format/action penalties from genuine task failure.

## metric_claim_alignment_table

| Claim type | Evidence described in packet | Alignment judgment |
|---|---:|---|
| “AgentBench evaluates LLMs as agents in interactive environments.” | Eight executable or interactive environments; task workers; outcome categories. | Supported. |
| “The benchmark covers diverse agent tasks.” | OS, database, web-shopping, web-browsing, household, game, and knowledge-graph style environments. | Partly supported; diversity is shown, representativeness is not established. |
| “Model A is better than Model B on AgentBench.” | Table 3 environment scores and aggregate AgentBench score. | Supported only under the paper’s scoring and weighting scheme. |
| “Model A is a generally better agent.” | Aggregate score across heterogeneous environments. | Overclaimed unless backed by uncertainty, sensitivity analyses, and stronger task-selection justification. |
| “Success rate measures agent performance.” | Several environments use success rate. | Supported for binary completion tasks only. |
| “Overall score summarizes performance across environments.” | Scores are resized and aggregated using reciprocal average-performance weights. | Mechanically supported, but construct validity is uncertain. |
| “Failures are interpretable.” | Execution outcome categories and aggregate proportions in Table 4. | Partly supported; aggregate failure categories need per-model and per-environment analysis. |
| “Results are reproducible.” | Toolkit, task workers, Docker/worker isolation, evaluation-prompt setup. | Partly supported; exact versions, seeds, prompts, raw traces, and scoring scripts are still needed. |

## reproducibility_risk_list

- Exact model versions and API snapshot dates may be missing or unstable.
- API-based models can change behavior over time.
- Decoding parameters may not be fully specified.
- Prompt templates and system messages may not be fully recoverable.
- Environment seeds and task-instance sampling may not be fixed.
- Docker/worker isolation is described, but full container images and dependency versions are not confirmed in the packet.
- Web-shopping and web-browsing environments may depend on changing external or simulated web content.
- Raw action traces may be unavailable, limiting auditability.
- Scoring scripts and normalization rules may be insufficiently transparent.
- Overall score depends on benchmark-specific resizing and reciprocal-performance task weights.
- Contamination checks are not described.
- Statistical uncertainty is not reported in the packet.

## corrected_protocol

1. **Define claim scope before evaluation.**  
   State that the benchmark measures performance on the selected AgentBench environments under specified prompts, tool interfaces, metrics, and aggregation rules. Avoid claiming general agent superiority unless sensitivity and external-validity checks support it.

2. **Freeze all evaluation artifacts.**  
   Release task instances, prompts, action schemas, scoring scripts, Docker images, dependency versions, model identifiers, API dates, decoding parameters, retry policy, step limits, and context limits.

3. **Add baseline tiers.**  
   Include random, scripted, non-agent single-turn LLM, tool-specific solver, retrieval-assisted, and human baselines where applicable.

4. **Run required ablations.**  
   Test prompt variants, action schemas, step limits, context limits, decoding settings, task-category removals, equal weighting versus reciprocal-performance weighting, and alternative metric normalizations.

5. **Report per-environment results first.**  
   Treat the overall score as secondary. For each environment, report the native metric, number of tasks, confidence intervals, and failure-mode breakdown.

6. **Quantify uncertainty.**  
   Use repeated runs or bootstrap confidence intervals. Report whether model rankings are statistically distinguishable, especially for close scores.

7. **Separate capability from interface failure.**  
   Report Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded by model and environment, not only in aggregate.

8. **Control contamination risk.**  
   Document task creation dates, release dates, public availability, overlap checks, and whether tasks were hidden from evaluated systems before testing.

9. **Validate aggregation.**  
   Publish the exact overall-score formula and show ranking sensitivity under equal weights, category-balanced weights, and no aggregate score.

10. **Constrain conclusions.**  
   The corrected conclusion should be: “The evaluated models differ substantially on the specified AgentBench environments, with rankings depending on metric normalization and task weighting.” Broader claims about general agent ability require additional evidence.