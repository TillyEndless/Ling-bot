## rigor_audit_findings

1. **High: Overall AgentBench score may not cleanly support broad “agent capability” claims.**  
   Source notes say Table 2 mixes environment-specific metrics: success rate, F1, reward, game progress, and step success rate. Section 4.1 then resizes and aggregates task scores using weights derived from reciprocal average model performance. This creates a risk that the overall score reflects metric normalization and weighting choices as much as agent ability. The packet does not state that this aggregation is validated against an external construct of “agent capability.”

2. **High: Task heterogeneity weakens single-rank conclusions.**  
   AgentBench covers eight environments including operating-system, database, web-shopping, web-browsing, household, game, and knowledge-graph style tasks. Figure 2 groups them into grounding categories such as code-grounded, game-grounded, and web-grounded. These are meaningfully different constructs. A model ranking that aggregates them should be interpreted as benchmark-specific performance, not global agent superiority.

3. **Medium: Baseline adequacy is unclear from the packet.**  
   Table 1 lists 29 API-based and open-sourced LLMs, and Tables 2-3 report model comparisons. However, the packet does not state whether non-agent baselines, tool-disabled baselines, random/action-template baselines, task-specialized agents, or human/reference performance are included. Missing baseline detail limits the ability to attribute performance to agentic interaction rather than model scale, prompt compliance, tool familiarity, or task-specific affordances.

4. **Medium: Ablation evidence is not established in the supplied notes.**  
   The packet mentions an API-centric evaluation toolkit, task workers, Docker/worker isolation, and evaluation prompts, but does not report ablations over prompt format, tool access, context limits, task limits, environment categories, aggregation weights, or retry/error handling. Without these, it is hard to know which design choices drive the reported performance.

5. **Medium: Statistical reporting is under-specified.**  
   The packet reports success rates and other environment metrics, plus aggregate execution outcomes in Table 4, but does not mention seeds, repeated runs, confidence intervals, variance, bootstrap intervals, or per-task uncertainty. For interactive agent benchmarks, stochasticity can enter through model sampling, environment behavior, task selection, and parsing/execution failures.

6. **Medium: Contamination and public benchmark exposure risk are not resolved by the packet.**  
   The benchmark uses tasks such as web-shopping, web-browsing, database, operating-system, household, game, and knowledge-graph environments. The packet does not state whether tasks are newly generated, held out, private, versioned, or screened for training-data exposure. This is a risk, not proof of leakage.

7. **Low-to-medium: Reproducibility details are partially supported but incomplete.**  
   Section 4.1 describes the evaluation toolkit, task workers, Docker/worker isolation, and evaluation-prompt setup. That supports some reproducibility. The packet does not specify whether raw outputs, exact prompts, model versions, API parameters, task instances, scoring scripts, environment versions, or configs are available.

## missing_baselines_and_ablations

| Category | Missing or unclear item | Why it matters | Source grounding |
|---|---|---|---|
| Baseline | Non-agent prompting baseline | Tests whether interaction/tool use improves over direct answering | Packet only states 29 LLMs in Table 1 |
| Baseline | Random or scripted action baseline | Calibrates environment difficulty and metric floor | Not stated in packet |
| Baseline | Tool-disabled or environment-disabled LLM baseline | Separates language ability from agent-environment control | Not stated in packet |
| Baseline | Human or expert reference performance | Helps interpret success rates and ceiling effects | Not stated in packet |
| Baseline | Task-specialized agent systems | Tests whether general LLM agents are competitive with specialized methods | Not stated in packet |
| Ablation | Prompt-template sensitivity | Section 4.1 mentions evaluation-prompt setup, but no prompt ablation is described in the packet | p. 6 Section 4.1 |
| Ablation | Aggregation-weight sensitivity | Overall score depends on resizing and reciprocal-average-performance weights | p. 7 Section 4.1, Table 3 |
| Ablation | Metric normalization choices | Mixed metrics are combined into one score | p. 6 Table 2; p. 7 Table 3 |
| Ablation | Context limit and task limit effects | Section 2 defines Context Limit Exceeded and Task Limit Exceeded outcomes | p. 4 Section 2; p. 8 Table 4 |
| Ablation | Error-category impact | Invalid Format and Invalid Action may affect model ranking | p. 4 Section 2; p. 8 Table 4 |
| Ablation | Environment-family leave-one-out | Tests whether the overall score is dominated by one task category | Figure 2; Tables 2-3 |

## metric_claim_alignment_table

| Claimed conclusion type | Metric evidence in packet | Alignment | Boundary |
|---|---|---|---|
| “LLMs can be evaluated as agents in interactive environments” | Eight interactive/executable environments; evaluation toolkit and task workers | Stronger alignment | Supported as a benchmark-construction claim |
| “Model A is better than Model B on AgentBench” | Table 2 environment metrics and Table 3 overall AgentBench score | Partial alignment | Supported only under this benchmark’s tasks, prompts, metrics, and aggregation |
| “Model A is generally a better agent” | Aggregated overall score across heterogeneous tasks | Weak-to-partial alignment | Not supported globally; task and metric heterogeneity limit scope |
| “Overall AgentBench score measures general agent ability” | Resized task scores aggregated using reciprocal average model performance weights | Risky alignment | Needs validation or sensitivity analysis; packet does not provide it |
| “Models fail in identifiable execution modes” | Section 2 outcome categories and Table 4 aggregate proportions | Moderate alignment | Supports aggregate outcome-pattern claims, not necessarily causal explanations |
| “Performance is robust” | Environment-specific scores and aggregate scores | Weak alignment | Packet does not mention repeated runs, uncertainty, or sensitivity tests |
| “Results are reproducible” | Toolkit, task workers, Docker/worker isolation, prompt setup | Partial alignment | Exact artifacts, raw outputs, versions, seeds, and configs are not specified in packet |

## reproducibility_risk_list

- Exact model versions and API settings are not specified in the supplied packet.
- Sampling parameters, decoding settings, retries, and timeout behavior are not described in the packet.
- Prompt templates are mentioned but not confirmed as fully available.
- Task instance lists, splits, or generation procedures are not detailed in the packet.
- Environment versions and dependency versions are not specified in the packet.
- Scoring scripts and normalization code for the overall score are not confirmed as available.
- Raw model trajectories, invalid actions, invalid formats, and failure logs are not confirmed as released.
- Seeds, repeated-run counts, confidence intervals, and variance estimates are not reported in the packet.
- Contamination controls for public or training-exposed tasks are not described in the packet.
- Aggregation-weight sensitivity and alternative ranking robustness are not reported in the packet.

## corrected_protocol

1. **Define claim scope before scoring.**  
   State that the benchmark measures performance on the specified AgentBench environments, not general agent intelligence or deployment robustness.

2. **Report environment-level results as primary.**  
   Treat Table 2-style environment metrics as the main evidence. Use the overall score only as a secondary summary, with clear warning that it aggregates heterogeneous metrics.

3. **Add baseline families.**  
   Include direct-prompt non-agent baselines, tool-disabled baselines, random/scripted action baselines, human or expert reference where feasible, and task-specialized systems where relevant.

4. **Add required ablations.**  
   Run prompt-template ablations, aggregation-weight sensitivity, metric-normalization sensitivity, environment-family leave-one-out, context-limit/task-limit sensitivity, and error-handling ablations for Invalid Format, Invalid Action, and Task Limit Exceeded.

5. **Improve statistical reporting.**  
   Run repeated trials where model or environment stochasticity exists. Report confidence intervals or variance for environment-level metrics, overall score, and execution-outcome categories.

6. **Separate capability from execution reliability.**  
   Report task success metrics separately from execution outcomes such as Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded. Do not collapse these into a single interpretation without analysis.

7. **Control contamination risk.**  
   Document task provenance, whether task instances are public or private, benchmark release timing, held-out splits if any, and any screening for train/test exposure.

8. **Publish reproducibility artifacts.**  
   Provide exact prompts, task instances, scoring scripts, aggregation code, model identifiers, API parameters, environment versions, Docker files, configs, raw trajectories, and failure logs.

9. **Use robust ranking checks.**  
   Report whether model rankings change under alternative weighting schemes, per-environment ranks, macro-averaging, unweighted aggregation, and exclusion of each environment family.

10. **State corrected conclusion.**  
   A defensible conclusion would be: the benchmark provides comparative evidence about evaluated LLMs under the specified AgentBench environments, metrics, prompts, and aggregation procedure. It does not by itself establish universal agent superiority, deployment robustness, or a validated single measure of general agent capability.