# Capability Map for a General AI/ML/RL Research Skill

This map separates core general research capabilities from optional topic or tool packs. The target skill should support AI/ML/RL broadly and should not be built around any one research direction.

## Coverage Matrix

| Capability Category | Upstream Coverage | Useful Sources | Coverage Quality | Missing / Required for New Skill |
|---|---|---|---|---|
| Research scoping and question formulation | Partial | K-Dense `hypothesis-generation`, `scientific-brainstorming`; Orchestra `autoresearch`, `brainstorming-research-ideas`, `creative-thinking-for-research` | Good ideation, weak grounding. | Research question template with scope, unit of analysis, claim type, feasible evidence, benchmark availability, and stop criteria. |
| Literature discovery and citation tracing | Partial-strong | K-Dense `literature-review`, `paper-lookup`, `research-lookup`, `exa-search`, `bgpt-paper-search`, `citation-management`, `pyzotero`; Orchestra `autoresearch`, `ml-paper-writing` citation workflow | Strong tool inventory; weak coverage auditing. | Query ledger, source diversity audit, backward/forward citation protocol, AI venue/arXiv version resolution, inclusion/exclusion rationale. |
| Structured paper reading and summarization | Weak-partial | K-Dense `literature-review`; Orchestra ARA `compiler` | ARA is rich but heavy; K-Dense extraction is review-oriented. | Lightweight AI paper card: problem, assumptions, method, datasets, baselines, metrics, evidence, limitations, reproducibility, open questions. |
| Comparative synthesis and taxonomy construction | Partial | K-Dense `literature-review`, `scientific-critical-thinking`; Orchestra ARA schema and rigor reviewer | Provides general synthesis but not AI method-comparison discipline. | Comparison matrix for methods, assumptions, compute/data requirements, benchmark settings, failure modes, and evidence strength. |
| Research ideation and hypothesis generation | Strong but insufficiently guarded | K-Dense `hypothesis-generation`; Orchestra `brainstorming-research-ideas`, `creative-thinking-for-research`, `autoresearch` | Good creative frameworks. | Evidence-grounded promotion path: idea -> conjecture -> testable hypothesis -> protocol. Mark speculation explicitly. |
| AI/ML experiment design | Partial | Orchestra `autoresearch`, `ml-training-recipes`, evaluation harness skills; K-Dense `statistical-analysis`, `scikit-learn`, `pytorch-lightning` | Good engineering recipes, weak design rubric. | Protocol template with claim type, baseline, dataset split, metric, seed plan, compute budget, ablations, expected failure, and analysis plan. |
| Benchmark, baseline, metric, and ablation analysis | Partial | Orchestra `lm-evaluation-harness`, `bigcode-evaluation-harness`, `nemo-evaluator`, `ml-training-recipes`; K-Dense `statistical-analysis`, `scientific-critical-thinking` | Can run benchmarks; does not reliably critique benchmark suitability. | Baseline adequacy rubric, metric-claim alignment, contamination/leakage checks, ablation matrix, uncertainty reporting. |
| Reinforcement learning research workflows | Partial | K-Dense `stable-baselines3`, `pufferlib`; Orchestra `trl-fine-tuning`, `grpo-rl-training`, `openrlhf`, `verl`, `simpo`, `torchforge`, `slime`, `miles` | Good framework coverage, fragmented between classic RL and LLM RL. | RL research checklist covering MDP/POMDP framing, environment versioning, seeds, eval episodes, reward design, offline data quality, return distributions, exploration budget. |
| Implementation, reproduction, and code-level analysis | Partial-strong | Orchestra model/training/distributed/MLOps skills; K-Dense package skills and document parsers | Strong package help, weak research-level reproducibility grading. | Reproduction readiness rubric: code, configs, env, data, checkpoints, hardware, expected runtime, known nondeterminism, exact evaluation command. |
| Mechanistic interpretability or representation analysis | Strong tool coverage | Orchestra `transformer-lens`, `saelens`, `pyvene`, `nnsight`; K-Dense `shap`, `umap-learn`, `torch-geometric` | Strong for LLM mech-interp tools; weaker for broader representation analysis. | Causal intervention controls, feature validation rubric, negative controls, scope limits for interpretability claims. |
| Evidence management and citation audit | Partial-strong | K-Dense `citation-management`; Orchestra ARA `research-manager`, `rigor-reviewer`, `ml-paper-writing` | Best upstream area when combined. | Unified evidence ledger connecting claims to citations, paper passages, tables, figures, experiment runs, and support status. |
| Scientific writing, reviewing, and presentation generation | Strong but needs filtering | K-Dense `scientific-writing`, `peer-review`, `scholar-evaluation`, `scientific-slides`; Orchestra `ml-paper-writing`, `systems-paper-writing`, `presenting-conference-talks`, `academic-plotting` | Strong templates and writing advice. | Reliability-first writing workflow: no unsupported claims, no decorative visuals, venue-specific claims/evidence checklist, reviewer-risk table. |

## Core Capability Modules Needed

1. Research Intake and Scope
   - Convert vague topic to research question candidates.
   - Classify contribution type: algorithm, benchmark, dataset, theory, system, interpretability, survey, replication, negative result.
   - Define boundaries: modality, setting, assumptions, excluded topics.

2. Literature Discovery and Coverage
   - Maintain query log and source log.
   - Track seed papers, forward citations, backward citations, related work clusters, and canonical baselines.
   - Explicitly mark coverage limits.

3. Paper Reading
   - Produce one structured paper card per important paper.
   - Extract claims and evidence separately.
   - Track reproducibility facts: code, data, hardware, seeds, configs, checkpoints, licenses.

4. Synthesis and Taxonomy
   - Build method comparison tables.
   - Identify assumption conflicts, benchmark families, metric families, and evidence gaps.
   - Distinguish consensus, disagreement, and unexplored regions.

5. Hypothesis and Research Gap Management
   - Convert gaps into hypotheses only when falsifiable.
   - Keep speculative ideas in a separate queue.
   - Link each hypothesis to motivating papers and required evidence.

6. Experiment and Reproduction Planning
   - Produce protocols before execution.
   - Define baseline set, ablation set, evaluation set, and statistical plan.
   - Include minimal viable reproduction and full reproduction variants.

7. Evidence and Claim Audit
   - Maintain claim ledger with support status.
   - Audit overclaiming, weak citations, contradicted evidence, missing controls, and unsupported novelty claims.

8. Writing and Review Support
   - Draft papers, proposals, reviews, and talks from the evidence ledger.
   - Preserve uncertainty and limitations.
   - Create reviewer-risk and rebuttal-prep notes.

## Optional Topic/Tool Packs

These should not define the core architecture:

- LLM post-training/RLHF pack: TRL, GRPO, OpenRLHF, verl, reward modeling, preference data.
- Classical RL pack: Stable-Baselines3, PufferLib, Gymnasium, offline RL protocols.
- Mechanistic interpretability pack: TransformerLens, SAELens, pyvene, nnsight.
- LLM evaluation pack: lm-eval-harness, BigCode, NeMo Evaluator, contamination audit.
- Systems/distributed training pack: FSDP, DeepSpeed, Megatron, Ray, hardware profiling.
- RAG/agent pack: retrieval evaluation, agent benchmarks, observability.
- Representation learning pack: embeddings, probing, disentanglement, invariance, transfer.
- Robotics/world models pack: simulation protocols, sim-to-real, policy evaluation, datasets.

## Upstream Elements to Avoid in Core

- Mandatory generated figures or graphical abstracts.
- Provider-specific search as the only path.
- Tool-specific instructions before a research question is scoped.
- Autonomous “never stop” execution posture.
- Biomedical evidence hierarchies applied unmodified to AI/ML.
- Large artifact schemas as the only paper-reading mode.
- Quantitative scores without calibrated evidence and uncertainty.
