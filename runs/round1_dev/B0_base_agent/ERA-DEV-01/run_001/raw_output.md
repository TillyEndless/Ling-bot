## rigor_audit_findings

**High severity: Aggregated overall score may overstate “agent” capability.**  
The packet says AgentBench uses eight heterogeneous environments and reports an overall score aggregated across environments. Because the environments include operating-system, database, web-shopping, web-browsing, household, game, and knowledge-graph style tasks, the packet does not establish that they measure a single shared construct. A high aggregate score should therefore not be interpreted as proof of general agency.

**High severity: Metric-task alignment is under-justified.**  
Success rate is reported as the main metric for several environments, but the packet does not indicate whether success rate captures partial progress, efficiency, robustness, reasoning quality, tool-use reliability, or recovery from failed actions. For interactive agents, binary success can hide important differences between models.

**High severity: Contamination and train/eval leakage risk is not resolved by the packet.**  
The packet explicitly instructs that contamination, benchmark saturation, and train/eval leakage should be assessed as risks, not invented as facts. From the available notes, there is no clear evidence of dataset release timing controls, task secrecy, decontamination checks, or model training-data audits.

**Medium severity: Baseline coverage is unclear.**  
The paper evaluates 29 LLMs, but the packet does not identify non-agent baselines, scripted policies, retrieval-only systems, tool-disabled variants, random-action baselines, or human performance. Without these, it is hard to separate genuine interactive competence from prompt following, memorization, or environment-specific affordances.

**Medium severity: Ablation support is unclear.**  
The packet mentions model comparisons and environment-specific performance, but does not describe ablations over prompts, tool access, memory, action space, observation format, retries, or environment workers. This limits causal interpretation of what drives performance.

**Medium severity: Reproducibility details appear incomplete from the packet.**  
The packet notes an evaluation toolkit and task workers, but does not confirm full task instances, prompts, seeds, model versions, decoding parameters, API dates, environment states, scoring scripts, retry policy, or failure classification.

**Medium severity: Statistical reporting is underspecified.**  
The packet mentions success rates and aggregate scores but does not say whether confidence intervals, standard errors, bootstrap intervals, significance tests, or per-task variance are reported. This is important because interactive tasks can have high variance.

**Low severity: Claim scope needs stronger separation.**  
The packet says to distinguish benchmark construction, model performance results, and broader claims about LLM agents. Any claim that AgentBench measures “general agency” should be weakened unless supported by construct validity evidence across environments.

---

## missing_baselines_and_ablations

**Missing or unclear baselines**

| Baseline | Why needed |
|---|---|
| Random-action or no-op policy | Establishes task difficulty floor. |
| Scripted/rule-based environment-specific agents | Shows whether tasks reward simple heuristics. |
| Human baseline | Calibrates task difficulty and ceiling performance. |
| Tool-disabled LLM baseline | Separates language reasoning from interactive/tool-use ability. |
| Same LLM with single-step prompting only | Tests whether multi-turn interaction adds value. |
| Retrieval-only or search-only baseline where relevant | Especially important for web-browsing and knowledge tasks. |
| Smaller/open models under same protocol | Helps interpret scale effects and reproducibility. |
| Oracle planner or environment expert policy | Provides an approximate upper bound where feasible. |

**Missing or unclear ablations**

| Ablation | Why needed |
|---|---|
| Prompt template ablation | Measures prompt sensitivity. |
| Decoding parameter ablation | Checks stability under temperature/top-p/max-token changes. |
| Tool/API access ablation | Determines contribution of external actions. |
| Observation format ablation | Tests whether formatting, not capability, drives scores. |
| Action-space restriction ablation | Identifies whether broad action spaces cause failures. |
| Retry-budget / max-step ablation | Success may depend heavily on interaction budget. |
| Memory/context-window ablation | Tests dependence on long context or state tracking. |
| Environment-worker ablation | Checks whether infrastructure choices affect results. |
| Task-source split ablation | Helps assess leakage or memorization risk. |

---

## metric_claim_alignment_table

| Claim type | Packet-supported metric | Alignment judgment | Correction |
|---|---:|---|---|
| “Model succeeds on benchmark tasks” | Environment success rate | Reasonable if task scoring is valid | Report per-environment and per-task success with uncertainty. |
| “Model is better than another model” | Model comparison tables | Partially supported | Add paired tests or confidence intervals; avoid ranking by aggregate alone. |
| “Model is a generally capable agent” | Overall aggregate score | Weak alignment | Reframe as performance on this benchmark’s task mix only. |
| “Model handles interactive environments” | Success rate across executable/interactive settings | Partially supported | Add step efficiency, invalid action rate, recovery rate, and failure categories. |
| “Model can use tools robustly” | Not clearly specified in packet | Insufficient | Include tool-call validity, tool success, error recovery, and action trace analysis. |
| “Benchmark covers diverse agent tasks” | Eight environments across multiple task types | Supported at high level | Avoid implying coverage is exhaustive or capability-unified. |
| “Aggregate score summarizes agent ability” | Overall score | Under-justified | Report aggregate only as secondary; include weighting rationale and sensitivity analysis. |
| “Results are reproducible” | Toolkit/task workers mentioned | Incomplete | Release prompts, seeds, versions, task instances, scoring code, and environment configs. |

---

## reproducibility_risk_list

1. **Model version ambiguity:** Packet does not confirm exact model snapshots, API dates, or backend versions.
2. **Prompt ambiguity:** Prompt protocol is listed as an audit focus, but exact prompts are not provided in the packet.
3. **Decoding settings unknown:** Temperature, top-p, max tokens, stop rules, and retry policies are not specified here.
4. **Environment state drift:** Web, shopping, browsing, OS, and database-style tasks may depend on mutable states unless frozen.
5. **Task instance availability unknown:** The packet does not confirm whether all task instances and answer keys are released.
6. **Scoring implementation risk:** Success-rate computation and edge-case handling are not described in detail here.
7. **Aggregation sensitivity:** Overall score may change depending on weighting, normalization, and task count per environment.
8. **Contamination risk unresolved:** No packet evidence of decontamination or train/eval leakage checks.
9. **Failure-mode opacity:** Packet does not confirm systematic labels for invalid actions, timeouts, hallucinated actions, or environment errors.
10. **Infrastructure dependence:** Task workers and toolkit may introduce implementation-specific behavior that needs versioning and tests.

---

## corrected_protocol

1. **Define claim boundaries before evaluation.**  
   State that the benchmark measures performance on a selected set of interactive environments, not general agency.

2. **Report results primarily per environment.**  
   Use environment-level and task-level scores as the main results. Treat the overall aggregate as secondary.

3. **Justify aggregation.**  
   Specify weighting, normalization, and rationale. Add sensitivity analyses using equal environment weighting, equal task weighting, and exclusion of each environment one at a time.

4. **Use richer metrics.**  
   Report success rate plus confidence intervals, average steps, invalid action rate, timeout rate, tool-call error rate, recovery rate, and partial-credit progress where applicable.

5. **Add statistical reporting.**  
   Include per-environment sample sizes, confidence intervals, paired comparisons where the same tasks are used, and variance across task categories.

6. **Add required baselines.**  
   Include random/no-op, scripted heuristic, human, tool-disabled LLM, prompt-only LLM, and environment-specific simple baselines where feasible.

7. **Run core ablations.**  
   Ablate prompt format, tool access, observation format, max steps, retry budget, decoding settings, and memory/context availability.

8. **Control contamination risk.**  
   Document task creation dates, public availability, overlap checks where possible, and whether evaluated models may have seen task data. Mark unresolved contamination as a limitation.

9. **Freeze interactive environments.**  
   Use static snapshots or versioned local replicas for web, shopping, database, OS, and knowledge-graph tasks. Record environment hashes and configuration files.

10. **Release reproducibility artifacts.**  
   Provide exact prompts, task instances, scoring scripts, worker code, environment versions, seeds, model identifiers, API dates, decoding parameters, retry policies, and raw trajectories.

11. **Analyze failures.**  
   Categorize failures into reasoning error, invalid action, environment misunderstanding, tool/API failure, timeout, hallucinated observation/action, and scoring ambiguity.

12. **Constrain conclusions.**  
   Report model rankings as benchmark-specific. Avoid statements that a high overall score proves broad autonomous agency unless supported by additional construct-validity evidence.