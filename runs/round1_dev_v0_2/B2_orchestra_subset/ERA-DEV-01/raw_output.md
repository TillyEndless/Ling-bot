## rigor_audit_findings

| Severity | Claim affected | Evidence issue | Consequence | Minimal fix |
|---|---|---|---|---|
| High | Overall AgentBench score supports broad “LLMs as agents” ranking | The overall score aggregates heterogeneous environments with resized scores and task weights derived from reciprocal average model performance. This is source-derived from Section 4.1/Table 3, but the packet does not establish that the weighting scheme is construct-valid. | Overall rankings may reflect the aggregation design as much as agent capability. Strong claims should be scoped to the paper’s protocol. | Report per-environment results as primary; justify weights; add sensitivity analyses with equal weights, unweighted ranks, and alternative normalizations. |
| High | Model comparisons show agent ability differences | The packet lists 29 LLMs and environment-specific results, but does not provide evidence that tuning budgets, prompting, API settings, model access conditions, or run counts were comparable across models. | Apparent differences may be affected by protocol or inference-setting differences rather than model capability alone. | Standardize and report prompts, decoding settings, model versions, retries, context limits, tool permissions, and API dates for every model. |
| High | Benchmark validly measures agent performance across interactive environments | The eight environments are diverse, but task selection representativeness is not established in the packet. | The benchmark supports performance on selected tasks, not unrestricted agent competence. | Define the target construct, sampling frame, task inclusion criteria, and per-environment coverage rationale. |
| Medium | Success rate and overall score summarize performance adequately | Table 2 uses different environment metrics: success rate, F1, reward, game progress, and step success rate. Aggregating unlike metrics requires strong normalization assumptions. | Cross-environment comparisons may be hard to interpret. | Preserve raw metric tables, report normalized scores separately, and explain what each metric contributes to the agent construct. |
| Medium | Reported results are statistically reliable | The packet does not mention repeated runs, seeds, confidence intervals, variance, or uncertainty reporting. | Small or prompt-sensitive differences may be overinterpreted. | Run multiple trials where stochasticity exists; report confidence intervals, bootstrap intervals, or variance by task and environment. |
| Medium | Outcome categories explain model failures | Section 2 defines execution outcomes and Table 4 reports aggregate proportions, but the packet only supports aggregate outcome analysis. | Aggregate failure modes may hide environment-specific or model-specific pathologies. | Report outcome categories per model and per environment, linked to task difficulty and context/action constraints. |
| Medium | Contamination risk is controlled | The packet does not state whether benchmark tasks overlap with model training data, public examples, prior benchmarks, or web-accessible task content. | Reported performance could partially reflect memorization or benchmark exposure. | Add contamination analysis, task provenance, release dates, canary checks, and held-out/private task variants. |
| Low | Evaluation toolkit supports reproducibility | The paper discusses toolkit, workers, Docker/worker isolation, and evaluation prompts, but the packet does not confirm availability of exact code, configs, task data, seeds, or environment versions. | Reproduction may be possible in principle but not established by the supplied evidence. | Release exact artifacts or provide a reproduction manifest covering code, data, prompts, configs, environment images, and model invocation logs. |

## missing_baselines_and_ablations

| Missing item | Why it matters | Corrective addition |
|---|---|---|
| Non-agent or simple prompting baseline | Separates agent-environment interaction gains from ordinary LLM task answering. | Add direct-answer, no-tool, and minimal-prompt baselines where applicable. |
| Tool-use / environment-access ablation | Tests whether performance depends on interactive affordances. | Compare full agent setup against restricted tool/action variants. |
| Prompt ablation | The packet mentions evaluation-prompt setup but not prompt sensitivity. | Evaluate standard prompt, reduced prompt, and alternative wording variants. |
| Context-limit ablation | Context Limit Exceeded is an execution category, so context length may affect results. | Test matched context windows or report normalized subsets by context budget. |
| Step/action-budget ablation | Task Limit Exceeded and Invalid Action are defined outcomes. | Vary max steps/actions and show robustness of model rankings. |
| Aggregation ablation | Overall score depends on reciprocal average-performance weights. | Compare reciprocal weighting to equal weighting, per-task rank aggregation, and no aggregate. |
| Environment-family baseline | Figure 2 groups environments by grounding category. | Report separate code-grounded, game-grounded, web-grounded, and other category summaries before a global score. |
| Repeated-run baseline | No uncertainty details are supplied. | Repeat stochastic evaluations and report variance across runs. |

## metric_claim_alignment_table

| Metric / evidence | Claimed construct it can support | Alignment | Limitation | Correct claim scope |
|---|---|---|---|---|
| Environment-specific success rate | Task completion in environments using success criteria | Good for discrete completion tasks | Not comparable by itself to F1, reward, progress, or step success | “Model achieved X success rate on this environment under this protocol.” |
| F1 | Accuracy on structured prediction or retrieval-style subtask | Good when precision/recall tradeoff is central | Does not directly measure long-horizon agent control | “Model performed well on the F1-scored environment.” |
| Reward | Environment-defined optimization performance | Potentially appropriate for game or simulation tasks | Reward scale may not be comparable across environments | “Model achieved higher reward in this environment.” |
| Game progress | Partial completion in game-grounded tasks | Useful when full completion is rare | May reward partial progress differently from success | “Model advanced further under this game protocol.” |
| Step success rate | Local action correctness | Useful for action-level reliability | May not imply end-to-end task success | “Model produced more valid/effective steps.” |
| Overall AgentBench score | Aggregate benchmark performance | Weak-to-moderate without weighting validation | Combines heterogeneous metrics using derived weights | “Model ranks higher under AgentBench’s specified aggregation procedure.” |
| Execution outcome proportions | Failure-mode characterization | Useful diagnostic evidence | Aggregate proportions can hide per-task/model variation | “Under the evaluated tasks, failures fell into these reported outcome categories.” |

## reproducibility_risk_list

| Risk | Provenance | Why it matters |
|---|---|---|
| Exact model versions and API dates may be underspecified in the packet | Missing detail | API models can change, affecting reproducibility. |
| Prompt templates and environment prompts may not be fully recoverable from the packet | Missing detail | Prompt sensitivity can alter rankings. |
| Seeds, repeated runs, and uncertainty reporting are not described in the packet | Missing detail | Results may be unstable without variance estimates. |
| Docker/worker isolation is discussed, but exact images/configs are not confirmed | Source-derived plus missing detail | Environment drift can change task behavior. |
| Task data provenance and contamination controls are not established | Missing detail | Public or training-overlapped tasks could inflate scores. |
| Aggregation weights are protocol-dependent | Source-derived | Reproducing the same score requires exact weighting, resizing, and task inclusion rules. |
| Per-environment failure breakdowns are not established in the packet | Missing detail | Aggregate execution outcomes may obscure reproducibility failures. |

## corrected_protocol

1. Define the benchmark construct explicitly: “performance of LLMs as agents in the selected AgentBench interactive environments,” not general agent capability.

2. Freeze all evaluation artifacts: task sets, environment versions, Docker images, worker code, prompts, action schemas, model invocation parameters, context limits, step limits, and scoring scripts.

3. Evaluate each model under matched settings: same prompt family, decoding parameters where controllable, retry policy, context budget, step/action budget, and access date for API models.

4. Add required baselines: direct-answer/no-agent baseline, minimal-prompt baseline, restricted-tool baseline, and simple heuristic or random-action baselines where environment-appropriate.

5. Add ablations: prompt wording, context limit, step budget, tool availability, and aggregation method.

6. Report metrics in layers: raw per-task results, per-environment metrics, grounding-category summaries, and only then the overall AgentBench score.

7. Treat the overall score as secondary. Include sensitivity analyses using equal weighting, reciprocal average-performance weighting, and rank-based aggregation.

8. Report uncertainty: multiple runs for stochastic systems, confidence intervals or bootstrap intervals, and significance or practical-difference thresholds for model comparisons.

9. Audit contamination: document task provenance, public availability, overlap checks, benchmark release timing, and any held-out/private task variants.

10. Calibrate the conclusion: the evidence can support comparative performance of 29 LLMs on the selected AgentBench environments under the paper’s protocol. It does not, from the supplied packet alone, establish broad general agent competence or aggregation-independent superiority.