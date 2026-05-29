# ERA-DEV-01 Model Input Packet

Task: experimental rigor audit of AgentBench-style agent evaluation.

Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.

## Source

AgentBench: Evaluating LLMs as Agents, arXiv:2308.03688, 58-page arXiv PDF.

## Controlled Source Notes

Benchmark setup:

- The paper introduces AgentBench as a benchmark for evaluating LLMs as agents in interactive environments.
- It describes eight environments across multiple task types and evaluates 29 LLMs.
- The paper reports success rate as the main metric for several environments and defines an overall score aggregated across environments.
- Evidence locations: abstract; Figure 2; Sections 1-4; Table 1; Table 2; Table 3; appendices B-I.

Evaluation details:

- The benchmark includes executable or interactive settings such as operating-system, database, web-shopping, web-browsing, household, game, and knowledge-graph style environments.
- The paper discusses an evaluation toolkit and task workers to manage diverse environments.
- Reported results include model comparisons and environment-specific performance.
- Evidence locations: Section 3 environment descriptions; Section 4 evaluation setup; Table 3; Table 4; appendix task details.

Audit focus:

- Check whether the benchmark tasks and metrics support the claimed agent capabilities.
- Check whether aggregation across heterogeneous environments is justified.
- Check whether prompt protocol, model access, environment isolation, failure modes, and reproducibility details are sufficient.
- Treat contamination, benchmark saturation, and train/eval leakage as risks to assess from the packet, not facts to invent.

## Required Boundaries

- Do not treat a high overall score as proof of general agency.
- Do not assume all environments measure the same capability.
- Distinguish benchmark construction, model performance results, and broader claims about LLM agents.

