# Evaluation Framework Proposal

This framework is for later benchmarking of the proposed AI/ML/RL research skill. It evaluates research usefulness, reliability, and rigor, not just polished prose.

The controlled variant design is specified in `benchmark_variant_plan.md`. This file defines what to score; the variant plan defines what to compare and how to keep the comparison fair.

## Experimental Variants

The first benchmark should compare five controlled variants:

| Variant | Contents | Purpose |
|---|---|---|
| `B0_base_agent` | No research skill; same model, tools, and task prompt. | Measures whether skills provide real marginal value. |
| `B1_kdense_subset` | Relevant K-Dense literature, citation, peer review, critical thinking, statistics, and writing skills only. | Tests broad scientific research support. |
| `B2_orchestra_subset` | Relevant Orchestra state-management, ARA, rigor-review, ideation, ML writing, and evaluation skills only. | Tests AI research engineering and artifact discipline. |
| `B3_your_v1_original` | Independently designed `ai-ml-rl-research` skill based on the audit, before direct upstream adaptation. | Tests the proposed architecture itself. |
| `B4_your_v1_integrated` | `B3` plus selectively rewritten upstream components justified by the reuse ledger. | Tests the final integrated version. |

After `B4`, run ablations for evidence policy, rigor audit, RL guidance, upstream components, and writing/review support. Do not collapse the results into a single winner; compare per capability and per task family.

## Evaluation Dimensions

| Dimension | What to Measure | Strong Performance | Failure Modes |
|---|---|---|---|
| Literature coverage | Round 1: correct coverage of the fixed corpus. Future retrieval rounds: breadth and relevance of discovered papers. | Round 1 accounts for all supplied papers and maps research lines accurately; future rounds find canonical, recent, and directly relevant work. | Omits supplied corpus papers; imports outside papers in Round 1; misses seminal baselines in retrieval rounds. |
| Factual accuracy | Correctness of paper facts, methods, metrics, and claims. | Accurately distinguishes what papers did, found, and claimed. | Misstates results, invents details, confuses arXiv/conference versions. |
| Evidence traceability | Link from claim to source evidence. | Every substantive claim has source/evidence IDs and support status. | Claims appear without evidence; citations support only adjacent topics. |
| Paper-reading quality | Structured extraction from individual papers. | Captures problem, assumptions, method, datasets, baselines, metrics, evidence, limitations, reproducibility. | Produces generic summaries that miss experimental setup or limitations. |
| Comparative synthesis | Quality of method/taxonomy comparison. | Compares assumptions, mechanisms, datasets, metrics, compute, baselines, failure modes, and evidence strength. | Lists papers chronologically without synthesis. |
| Research question refinement | Ability to improve vague topics. | Converts broad interest into scoped, testable, useful questions with alternatives. | Narrows around a random trend or overcommits too early. |
| Hypothesis quality | Falsifiability and grounding. | Hypotheses have motivating evidence, predictions, and failure criteria. | Generates plausible-sounding but untestable ideas. |
| Experimental rigor | Design of reproduction/baseline/ablation/evaluation protocols. | Includes baselines, ablations, metrics, seeds, statistical plan, compute, and failure modes. | Omits baseline fairness, uses single seed, or aligns metric poorly to claim. |
| Benchmark validity | Suitability of datasets, benchmarks, and metrics. | Checks contamination, leakage, saturation, metric gaming, and benchmark-claim alignment. | Treats leaderboard benchmark as automatically valid. |
| Reproducibility awareness | Ability to identify missing reproduction details. | Tracks code/data/configs/seeds/hardware/checkpoints/runtime/license. | Says “reproducible” because code exists. |
| RL-specific rigor | RL environment and evaluation discipline. | Records env versions, wrappers, seeds, eval episodes, return distributions, reward design, offline data quality. | Reports best seed/checkpoint or ignores stochasticity. |
| Interpretability rigor | Causal and representation-analysis discipline. | Requires controls, interventions, validation, and scope limits. | Treats saliency/SAE/activation observations as causal explanations. |
| Citation audit | Bibliography and citation correctness. | Verifies citations programmatically and checks claim support. | Hallucinates citations or uses papers for claims they do not support. |
| Overclaiming control | Calibration of conclusions. | Separates supported conclusions, weak evidence, speculation, and open questions. | Converts preliminary evidence into broad claims. |
| Practical usefulness | Helpfulness to real AI/ML/RL researchers. | Produces artifacts researchers can use: matrices, protocols, review risks, reproduction plans. | Produces polished but non-actionable narrative. |

## Candidate Evaluation Task Types

1. Vague Topic to Research Questions
   - Input: “I want to study latent reasoning in LLMs” or “world models for robotics.”
   - Expected output: scoped questions, assumptions, literature seed plan, risks.
   - Domain topics are evaluation tasks only; they must not define the core skill.

2. Fixed-Corpus Literature Mapping
   - Input: a research area and 2-3 seed papers.
   - Expected output: corpus coverage table, method taxonomy, core/supporting paper labels, evidence-grounded gaps.
   - Open literature discovery is deferred to a future retrieval-enabled evaluation round.

3. Structured Paper Reading
   - Input: one AI/ML/RL paper PDF or markdown.
   - Expected output: paper card with claims/evidence/baselines/metrics/limitations/reproducibility.

4. Method Comparison Matrix
   - Input: 5-8 papers on a subtopic.
   - Expected output: taxonomy and comparison table across method, assumption, dataset, benchmark, evidence, limitations.

5. Research Gap and Hypothesis Generation
   - Input: literature matrix.
   - Expected output: gaps, competing hypotheses, falsification criteria, required evidence.

6. Reproduction Plan
   - Input: a paper with code link and reported results.
   - Expected output: minimal and full reproduction plans, expected blockers, environment/config/data requirements.

7. Baseline and Ablation Audit
   - Input: a proposed experimental section.
   - Expected output: missing baselines, weak ablations, metric mismatch, compute fairness concerns.

8. RL Protocol Review
   - Input: a reinforcement learning experiment plan.
   - Expected output: environment/version/seed/eval/reward/offline-data audit and corrected protocol.

9. Interpretability Claim Audit
   - Input: a mechanistic interpretability claim and evidence summary.
   - Expected output: causal-support assessment, missing controls, alternative explanations.

10. Paper Draft Claim Audit
   - Input: introduction/discussion draft with citations.
   - Expected output: unsupported claims, overclaiming, citation mismatches, limitation edits.

11. Peer Review Simulation
   - Input: anonymized paper draft or proposal.
   - Expected output: severity-ranked review with evidence-grounded major/minor comments.

12. Proposal Design
   - Input: research idea and constraints.
   - Expected output: aims, hypotheses, milestones, risks, evaluation plan, expected evidence.

## Scoring Rubric

Use 1-5 scores per dimension with severity-ranked findings.

- 5: Excellent, directly useful to an expert researcher, no material reliability issues.
- 4: Strong, minor gaps or missing details but scientifically sound.
- 3: Adequate, useful but incomplete; requires expert cleanup.
- 2: Weak, substantial omissions or questionable reasoning.
- 1: Unreliable, misleading, unsupported, or actively harmful to research quality.

Hard-fail conditions:

- Hallucinated citation presented as real.
- Major claim with no evidence.
- Comparative conclusion with no adequate baseline.
- RL result summarized from best seed only without disclosure.
- Causal interpretability claim supported only by correlational evidence.
- Reproduction plan missing data or evaluation protocol.
- Literature review omits obvious seminal work when the task includes enough clues to find it.

## Benchmark Construction Principles

- Use multiple AI/ML/RL domains so the skill does not overfit one topic.
- Include both recent and classic literature tasks.
- Include adversarial cases: misleading abstracts, weak baselines, benchmark contamination, arXiv/conference version mismatch, unsupported discussion claims.
- Evaluate artifacts, not just answers: paper cards, ledgers, matrices, protocols, audits.
- Include human expert review for final scoring where possible.
- Track time/cost/tool dependence separately from quality.

## Suggested Evaluation Domains

These are task domains, not core architecture assumptions:

- Reinforcement learning algorithms and offline RL.
- LLM post-training and RLHF/GRPO.
- Mechanistic interpretability and sparse autoencoders.
- Representation learning and probing.
- LLM agents and tool-use evaluation.
- RAG evaluation and retrieval benchmarks.
- World models and model-based RL.
- Robotics policy learning and sim-to-real.
- Scaling laws and efficient training.
- Multimodal model evaluation.

## Minimum Passing Bar for v1

The first version should pass if it can consistently:

- Produce structured paper cards with accurate evidence separation.
- Build useful literature and method comparison matrices.
- Identify missing baselines, weak metrics, and overclaiming.
- Produce reproduction and experiment protocols that an ML researcher could execute.
- Mark uncertainty and speculation instead of laundering it into conclusions.
- Preserve citation and evidence traceability across writing outputs.
