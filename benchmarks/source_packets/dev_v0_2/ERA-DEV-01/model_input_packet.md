# ERA-DEV-01 Model Input Packet

## Source

AgentBench: Evaluating LLMs as Agents, arXiv:2308.03688, 58-page arXiv PDF.

Pinned source identity:

- The local canonical source is the ICLR 2024 / arXiv v3 PDF whose first page reports "arXiv:2308.03688v3 [cs.AI] 4 Oct 2025."
- The abstract in this pinned version reports evaluation over 29 API-based and open-sourced LLMs.

## Controlled Source Notes

Benchmark setup:

- The paper introduces AgentBench as a benchmark for evaluating LLMs as agents in interactive environments.
- It describes eight environments across multiple task types and evaluates 29 LLMs.
- Figure 2 groups the eight environments into grounding categories, including code-grounded, game-grounded, and web-grounded task types.
- Table 1 lists the evaluated model roster for the pinned 29-model version.
- The paper reports success rate as the main metric for several environments and defines an overall score aggregated across environments.
- Evidence locations: p. 1 Abstract; p. 2 Figure 2 and Introduction; p. 3 Table 1; Sections 1-4; Table 2; Table 3; appendices B-I.

Evaluation details:

- The benchmark includes executable or interactive settings such as operating-system, database, web-shopping, web-browsing, household, game, and knowledge-graph style environments.
- The paper discusses an evaluation toolkit and task workers to manage diverse environments.
- Reported results include model comparisons and environment-specific performance.
- Table 2 reports environment-specific metrics. Several environments use success rate, while others use F1, reward, game progress, or step success rate.
- Section 4.1 describes the overall-score calculation: task scores are resized and aggregated using task weights derived from reciprocal average model performance.
- Table 3 reports environment-specific scores and the overall AgentBench score after the paper's aggregation procedure.
- Section 2 defines execution-outcome categories including Completed, Context Limit Exceeded, Invalid Format, Invalid Action, and Task Limit Exceeded.
- Table 4 reports aggregate proportions for these execution outcomes, and Section 4.3 discusses the reported outcome patterns.
- Section 4.1 describes the API-centric evaluation toolkit, task workers, Docker/worker isolation, and evaluation-prompt setup.
- Evidence locations: pp. 4-5 Section 3 environment descriptions; p. 4 Section 2 execution-outcome categories; p. 6 Section 4.1 and Table 2; p. 7 Section 4.1 Overall Score Calculation and Table 3; p. 8 Section 4.3 and Table 4; appendix task details.
