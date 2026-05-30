**Source Inventory**

Packet source: *AgentBench: Evaluating LLMs as Agents*, arXiv:2308.03688, pinned ICLR 2024 / arXiv v3 PDF, first page dated “4 Oct 2025.” Evidence objects supplied: p. 1 Abstract; p. 2 Figure 2 and Introduction; p. 3 Table 1; Sections 1-4; p. 4 Section 2; pp. 4-5 Section 3; p. 6 Section 4.1 and Table 2; p. 7 Section 4.1 and Table 3; p. 8 Section 4.3 and Table 4; appendices B-I.

## rigor_audit_findings

1. **High: Overall-score aggregation may not cleanly support broad model-ranking claims.**  
   `LIMITED_CRITIQUE`  
   The packet states that Table 2 uses heterogeneous environment metrics, including success rate, F1, reward, game progress, and step success rate, while Section 4.1 resizes task scores and aggregates them with weights derived from reciprocal average model performance. This supports an AgentBench-specific aggregate, but not necessarily a stable or construct-pure measure of general “agent” ability. The weighting scheme can amplify environments where average model performance is low, so overall rankings depend strongly on the benchmark’s aggregation design.  
   Source: p. 6 Table 2; p. 7 Section 4.1 and Table 3.

2. **High: Task coverage is broad but construct validity remains only partially established.**  
   `LIMITED_CRITIQUE`  
   AgentBench includes eight interactive environments spanning operating-system, database, web-shopping, web-browsing, household, game, and knowledge-graph style tasks. Figure 2 groups them into grounding categories such as code-grounded, game-grounded, and web-grounded. This is evidence of breadth, but the packet does not establish that these eight environments fully represent general LLM-agent competence.  
   Source: p. 2 Figure 2 and Introduction; pp. 4-5 Section 3.

3. **Medium: Baseline adequacy is underspecified beyond the LLM roster.**  
   `LIMITED_CRITIQUE`  
   The paper evaluates 29 API-based and open-sourced LLMs, and Table 1 lists the model roster. The packet does not mention non-LLM baselines, scripted agents, random agents, oracle/tool-specific agents, behavior-cloning baselines, or prior agent frameworks. Without those, it is harder to separate “LLMs can act as agents” from “some LLMs outperform other LLMs under this benchmark.”  
   Source: p. 1 Abstract; p. 3 Table 1.

4. **Medium: Ablation evidence is not described in the packet.**  
   `LIMITED_CRITIQUE`  
   The packet reports model comparisons, environment-specific scores, execution outcomes, toolkit design, prompts, and appendices, but does not identify ablations over prompts, tool access, task limits, context length, invalid-action handling, environment weighting, or aggregation choices. These ablations are important because Section 2 outcome categories include Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded.  
   Source: p. 4 Section 2; p. 8 Section 4.3 and Table 4; appendices B-I noted but no ablation details supplied.

5. **Medium: Statistical reporting is unclear from the packet.**  
   `LIMITED_CRITIQUE`  
   The packet reports environment-specific performance and aggregate outcome proportions, but does not state whether repeated runs, random seeds, confidence intervals, bootstrap intervals, or variance estimates are reported. For interactive environments, stochasticity and prompt sensitivity can affect model rankings. Missing uncertainty weakens ranking claims.  
   Source: Table 2; Table 3; Table 4. Packet does not provide finer statistical detail.

6. **Medium: Contamination risk is not resolved by the supplied evidence.**  
   `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`  
   The benchmark includes web, database, OS, game, household, and knowledge-graph style environments. The packet does not state whether tasks were hidden, generated after model training cutoffs, checked for public benchmark exposure, or protected against prompt/task leakage. This is a risk, not a proven flaw.  
   Source: pp. 4-5 Section 3; appendices B-I. Missing detail in packet.

7. **Low-to-medium: Reproducibility is partially supported by toolkit and isolation details, but artifact completeness is unknown.**  
   `LIMITED_CRITIQUE`  
   The packet states that Section 4.1 describes an API-centric evaluation toolkit, task workers, Docker/worker isolation, and evaluation-prompt setup. That helps reproducibility. However, the packet does not specify whether raw prompts, exact model versions, decoding parameters, seeds, task instances, worker configs, Docker images, raw outputs, and scoring scripts are available.  
   Source: p. 6 Section 4.1; appendices B-I.

## missing_baselines_and_ablations

| Item | Why it matters | Evidence-burden label | Packet status |
|---|---:|---|---|
| Random or no-op agent baseline | Calibrates task difficulty and success-rate floor. | `LIMITED_CRITIQUE` | Not mentioned in packet. |
| Scripted/task-specific baseline | Shows whether environments require general agent behavior or can be solved by narrow policies. | `LIMITED_CRITIQUE` | Not mentioned in packet. |
| Human or expert reference where feasible | Helps interpret whether scores are low, high, or near task ceiling. | `LIMITED_CRITIQUE` | Not mentioned in packet. |
| Prior agent-framework baselines | Needed if the claim compares AgentBench-style evaluation to existing agent systems. | `LIMITED_CRITIQUE` | Not mentioned in packet. |
| Prompt ablation | Tests sensitivity to evaluation-prompt wording. | `LIMITED_CRITIQUE` | Evaluation-prompt setup is mentioned, but ablations are not. |
| Tool/action-space ablation | Separates reasoning ability from tool-interface affordances. | `LIMITED_CRITIQUE` | Not mentioned in packet. |
| Context-limit/task-limit ablation | Outcome categories include Context Limit Exceeded and Task Limit Exceeded. | `DIRECT_PACKET_EVIDENCE` for categories; `LIMITED_CRITIQUE` for ablation need | Categories stated in Section 2; ablation not supplied. |
| Aggregation-weight ablation | Tests whether overall rankings depend on reciprocal-average-performance weighting. | `LIMITED_CRITIQUE` | Weighting described; robustness ablation not supplied. |
| Per-environment removal ablation | Tests whether overall score is dominated by a small number of environments. | `LIMITED_CRITIQUE` | Not mentioned in packet. |

## metric_claim_alignment_table

| Claimed construct | Packet metric/protocol | Alignment | Evidence-burden label | Boundary |
|---|---|---:|---|---|
| Interactive LLM-agent performance | Eight interactive environments; environment-specific scores. | Moderate | `DIRECT_PACKET_EVIDENCE` | Supports benchmark-specific performance, not universal agent ability. |
| Cross-environment agent ability | Overall AgentBench score from resized, weighted task scores. | Partial | `LIMITED_CRITIQUE` | Aggregation depends on metric normalization and reciprocal average model performance weights. |
| Task success | Success rate for several environments. | Strong where success is well-defined | `DIRECT_PACKET_EVIDENCE` | Does not cover environments using F1, reward, game progress, or step success rate. |
| Knowledge or retrieval-like task ability | Knowledge-graph style environment and possibly F1 metric. | Partial | `DIRECT_PACKET_EVIDENCE` | Packet does not provide task-instance design or contamination controls. |
| Robust execution as an agent | Execution outcomes: Completed, Context Limit Exceeded, Invalid Format, Invalid Action, Task Limit Exceeded. | Moderate | `DIRECT_PACKET_EVIDENCE` | Outcome categories diagnose failures but do not alone explain causes. |
| General superiority of one model over another | Table 3 overall score and environment scores. | Limited | `LIMITED_CRITIQUE` | Supported only under AgentBench’s tasks, prompts, metrics, and aggregation procedure. |

## reproducibility_risk_list

- `DIRECT_PACKET_EVIDENCE`: The packet states that the paper includes an evaluation toolkit, task workers, Docker/worker isolation, and evaluation-prompt setup.
- `LIMITED_CRITIQUE`: Exact model versions and API snapshot dates are not specified in the packet, despite evaluation over API-based and open-sourced LLMs.
- `LIMITED_CRITIQUE`: Decoding parameters, sampling settings, retries, timeout rules, and task-limit settings are not supplied in the packet.
- `LIMITED_CRITIQUE`: Seeds, repeated runs, confidence intervals, or variance reporting are not described in the packet.
- `LIMITED_CRITIQUE`: Raw model outputs, invalid-action logs, task-instance files, scoring scripts, and aggregation scripts are not confirmed available.
- `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`: Public exposure or contamination status of the benchmark tasks cannot be determined from the packet.
- `LIMITED_CRITIQUE`: Appendices B-I contain task details according to the packet, but the provided notes do not establish whether those details are sufficient for full independent reproduction.

## corrected_protocol

1. **Define claim scope before scoring.**  
   State that the primary claim is benchmark-specific: “Model X performs better than Model Y on AgentBench v3 under the specified prompts, tools, metrics, and aggregation.” Avoid claiming general LLM-agent superiority unless additional external validation is performed.

2. **Report environment-level results as primary.**  
   Keep Table 2-style environment metrics separate. Treat the overall AgentBench score as a secondary summary, not the sole ranking.

3. **Add transparent aggregation robustness checks.**  
   Report rankings under: equal environment weighting, reciprocal-average weighting, no resizing where possible, per-category aggregation from Figure 2 groups, and leave-one-environment-out aggregation.

4. **Add missing baselines.**  
   Include random/no-op agents, scripted task-specific agents, simple tool-use agents, and human or expert references where feasible. Compare LLMs against these baselines before interpreting model-to-model differences.

5. **Add ablations.**  
   Run prompt variants, context-limit settings, task-limit settings, invalid-action handling variants, tool/action-space constraints, and per-environment removal ablations.

6. **Improve statistical reporting.**  
   Use repeated runs or repeated task samples where stochasticity exists. Report confidence intervals or bootstrap intervals for environment metrics and overall score. Include rank uncertainty.

7. **Make contamination checks explicit.**  
   Document task provenance, whether tasks were public before evaluation, whether instances overlap with common training/evaluation data, and whether web tasks were time-sensitive or frozen.

8. **Release reproducibility artifacts where possible.**  
   Provide exact prompts, task instances, scoring scripts, aggregation code, worker configs, Docker images or build files, model identifiers, API dates, decoding parameters, timeout/retry rules, and raw outputs.

9. **Separate execution reliability from task competence.**  
   Report Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded rates alongside task scores, and analyze whether score differences are driven by reasoning, formatting, context length, or action validity.

10. **Use conservative conclusions.**  
   A corrected conclusion should read: “The supplied evidence supports comparative performance of 29 LLMs on the specified AgentBench environments and aggregation procedure. Broader claims about general agent competence, deployment robustness, or field-wide model superiority require stronger baselines, uncertainty reporting, contamination analysis, and aggregation robustness checks.”