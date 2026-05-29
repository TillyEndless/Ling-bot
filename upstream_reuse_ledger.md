# Upstream Reuse Ledger for General AI/ML/RL Research Skill

## Scope and Method

This ledger verifies reuse opportunities against the actual upstream skill files in:

- `K-Dense-AI/scientific-agent-skills`
- `Orchestra-Research/AI-Research-SKILLs`

The goal is not to collect many upstream skills. The goal is to identify which upstream patterns should shape a first-version general AI/ML/RL research skill, where they should live in the proposed architecture, and what must be rewritten for reliability, evidence traceability, and practical AI/ML/RL research use.

Reuse decisions here mean selective adaptation of ideas, schemas, prompts, checklists, or tool-interface patterns with attribution and license preservation. They do not imply bulk-copying upstream repositories into the new skill.

## High-Level Finding

The previous architecture recommendation remains correct: v1 should be a single orchestrating AI/ML/RL research skill with modular reference files and optional tool/topic packs.

The upstream analysis strengthens that recommendation because the reusable value is unevenly distributed:

- K-Dense provides broad research workflows and citation utilities, but many skills are generic, biomedical-leaning, or brittle when treated as complete AI/ML/RL research workflows.
- Orchestra provides stronger state-management, artifact, writing, rigor-review, and ML evaluation patterns, but several skills are either too autonomous, too framework-specific, or too topic-specific for the v1 core.
- The best reusable material is cross-cutting: evidence ledgers, citation verification discipline, claim-to-evidence mapping, structured literature review phases, research artifact state, and ML/RL-specific rigor checks.

No revision to `skill_architecture_proposal.md` is required. The reuse analysis supports the hybrid architecture already proposed: one orchestrating core with modular references and optional packs.

## License Summary

| Repository | Repository license | Skill-level license observations | Reuse implication |
|---|---:|---|---|
| `K-Dense-AI/scientific-agent-skills` | MIT, copyright K-Dense Inc. | Most inspected skills declare MIT in frontmatter. `paper-lookup` did not declare a per-skill license in the inspected frontmatter; treat it under the repository-level MIT license unless upstream adds a specific license. `exa-search` and `bgpt-paper-search` declare MIT and identify external authors in frontmatter. | Preserve attribution per skill/component. Do not assume all scripts have separate notices beyond the repository/skill metadata. |
| `Orchestra-Research/AI-Research-SKILLs` | MIT, copyright Claude AI Research Skills Contributors | All inspected relevant skills declare `license: MIT` in frontmatter. | Preserve attribution per skill/component and cite the specific path when adapting. |

## Inspected File Inventory

### K-Dense-AI/scientific-agent-skills

- `skills/literature-review/SKILL.md`
- `skills/literature-review/references/citation_styles.md`
- `skills/literature-review/references/database_strategies.md`
- `skills/literature-review/assets/review_template.md`
- `skills/literature-review/scripts/generate_pdf.py`
- `skills/literature-review/scripts/search_databases.py`
- `skills/literature-review/scripts/verify_citations.py`
- `skills/paper-lookup/SKILL.md`
- `skills/paper-lookup/references/academic_databases.md`
- `skills/paper-lookup/references/citation_networks.md`
- `skills/paper-lookup/references/paper_evaluation.md`
- `skills/research-lookup/SKILL.md`
- `skills/research-lookup/references/research_databases.md`
- `skills/research-lookup/references/research_evaluation.md`
- `skills/research-lookup/references/search_strategies.md`
- `skills/exa-search/SKILL.md`
- `skills/bgpt-paper-search/SKILL.md`
- `skills/citation-management/SKILL.md`
- `skills/citation-management/references/citation_styles.md`
- `skills/citation-management/references/database_apis.md`
- `skills/citation-management/scripts/doi_to_bibtex.py`
- `skills/citation-management/scripts/extract_metadata.py`
- `skills/citation-management/scripts/format_bibtex.py`
- `skills/citation-management/scripts/search_google_scholar.py`
- `skills/citation-management/scripts/search_pubmed.py`
- `skills/citation-management/scripts/validate_citations.py`
- `skills/pyzotero/SKILL.md`
- `skills/pyzotero/examples/example_usage.py`
- `skills/hypothesis-generation/SKILL.md`
- `skills/hypothesis-generation/references/experimental_design.md`
- `skills/hypothesis-generation/references/hypothesis_frameworks.md`
- `skills/scientific-brainstorming/SKILL.md`
- `skills/scientific-brainstorming/references/brainstorming_techniques.md`
- `skills/scientific-brainstorming/references/creativity_frameworks.md`
- `skills/scientific-critical-thinking/SKILL.md`
- `skills/scientific-critical-thinking/references/bias_detection.md`
- `skills/scientific-critical-thinking/references/evidence_evaluation.md`
- `skills/scientific-critical-thinking/references/validity_frameworks.md`
- `skills/peer-review/SKILL.md`
- `skills/peer-review/references/review_criteria.md`
- `skills/peer-review/references/review_templates.md`
- `skills/scholar-evaluation/SKILL.md`
- `skills/scholar-evaluation/references/evaluation_metrics.md`
- `skills/scholar-evaluation/references/scholar_profiles.md`
- `skills/scholar-evaluation/scripts/calculate_scores.py`
- `skills/statistical-analysis/SKILL.md`
- `skills/statistical-analysis/references/statistical_tests.md`
- `skills/statistical-analysis/scripts/assumption_checks.py`
- `skills/scientific-writing/SKILL.md`
- `skills/scientific-writing/references/journal_formats.md`
- `skills/scientific-writing/references/writing_guidelines.md`
- `skills/scientific-slides/SKILL.md`
- `skills/scientific-slides/references/conference_templates.md`
- `skills/scientific-slides/references/design_principles.md`

### Orchestra-Research/AI-Research-SKILLs

- `0-autoresearch-skill/SKILL.md`
- `0-autoresearch-skill/templates/research-state.yaml`
- `20-ml-paper-writing/ml-paper-writing/SKILL.md`
- `20-ml-paper-writing/ml-paper-writing/references/writing-best-practices.md`
- `20-ml-paper-writing/ml-paper-writing/references/citation-management.md`
- `20-ml-paper-writing/ml-paper-writing/references/reviewer-criteria.md`
- `20-ml-paper-writing/ml-paper-writing/references/figures-and-tables.md`
- `20-ml-paper-writing/systems-paper-writing/SKILL.md`
- `20-ml-paper-writing/systems-paper-writing/references/systems-paper-patterns.md`
- `20-ml-paper-writing/academic-plotting/SKILL.md`
- `20-ml-paper-writing/academic-plotting/references/matplotlib-styles.md`
- `20-ml-paper-writing/academic-plotting/references/figure-types.md`
- `20-ml-paper-writing/presenting-conference-talks/SKILL.md`
- `20-ml-paper-writing/presenting-conference-talks/references/talk-structure.md`
- `20-ml-paper-writing/presenting-conference-talks/references/slide-design.md`
- `21-research-ideation/brainstorming-research-ideas/SKILL.md`
- `21-research-ideation/brainstorming-research-ideas/references/ideation-frameworks.md`
- `21-research-ideation/creative-thinking-for-research/SKILL.md`
- `21-research-ideation/creative-thinking-for-research/references/creativity-techniques.md`
- `22-agent-native-research-artifact/ara-compiler/SKILL.md`
- `22-agent-native-research-artifact/ara-compiler/references/schema.md`
- `22-agent-native-research-artifact/research-manager/SKILL.md`
- `22-agent-native-research-artifact/research-manager/references/provenance_tags.md`
- `22-agent-native-research-artifact/rigor-reviewer/SKILL.md`
- `22-agent-native-research-artifact/rigor-reviewer/references/rigor_dimensions.md`
- `10-optimization/ml-training-recipes/SKILL.md`
- `10-optimization/ml-training-recipes/references/architecture-recipes.md`
- `10-optimization/ml-training-recipes/references/optimizer-recipes.md`
- `10-optimization/ml-training-recipes/references/domain-recipes.md`
- `10-optimization/ml-training-recipes/references/scaling-recipes.md`
- `10-optimization/ml-training-recipes/references/experiment-loop.md`
- `11-evaluation/lm-evaluation-harness/SKILL.md`
- `11-evaluation/lm-evaluation-harness/references/api-evaluation.md`
- `11-evaluation/lm-evaluation-harness/references/benchmark-guide.md`
- `11-evaluation/lm-evaluation-harness/references/custom-tasks.md`
- `11-evaluation/lm-evaluation-harness/references/distributed-eval.md`
- `11-evaluation/bigcode-evaluation-harness/SKILL.md`
- `11-evaluation/bigcode-evaluation-harness/references/benchmarks.md`
- `11-evaluation/bigcode-evaluation-harness/references/custom-tasks.md`
- `11-evaluation/bigcode-evaluation-harness/references/common-issues.md`
- `11-evaluation/nemo-evaluator/SKILL.md`
- `11-evaluation/nemo-evaluator/references/configuration.md`
- `11-evaluation/nemo-evaluator/references/adapters.md`
- `11-evaluation/nemo-evaluator/references/custom-benchmarks.md`
- `11-evaluation/nemo-evaluator/references/execution-backends.md`
- `04-mechanistic-interpretability/transformer-lens/SKILL.md`
- `04-mechanistic-interpretability/transformer-lens/references/hook-points.md`
- `04-mechanistic-interpretability/transformer-lens/references/activation-patching.md`
- `04-mechanistic-interpretability/transformer-lens/references/circuit-analysis.md`
- `04-mechanistic-interpretability/saelens/SKILL.md`
- `04-mechanistic-interpretability/saelens/references/sae-training.md`
- `04-mechanistic-interpretability/saelens/references/feature-analysis.md`
- `04-mechanistic-interpretability/saelens/references/model-analysis.md`
- `04-mechanistic-interpretability/pyvene/SKILL.md`
- `04-mechanistic-interpretability/pyvene/references/intervention-types.md`
- `04-mechanistic-interpretability/pyvene/references/activation-patching.md`
- `04-mechanistic-interpretability/pyvene/references/iit.md`
- `04-mechanistic-interpretability/nnsight/SKILL.md`
- `04-mechanistic-interpretability/nnsight/references/intervention-basics.md`
- `04-mechanistic-interpretability/nnsight/references/remote-models.md`
- `04-mechanistic-interpretability/nnsight/references/activation-analysis.md`

## Reuse Ledger

| Upstream skill or component | Actual capability from inspected files | Type and dependencies | Reuse decision | v1 architecture destination | Preserve | Rewrite, defer, or reject | License status |
|---|---|---|---|---|---|---|---|
| `K-Dense-AI/scientific-agent-skills/skills/literature-review` | Structured review workflow: planning, scoping, search strategy, multi-database search, screening, extraction, quality assessment, thematic synthesis, citation chaining, DOI verification, and review-template generation. | Mostly instruction/checklist-based. Optional scripts for search formatting, DOI verification, PDF generation, and schematic/visual generation. Assumes `parallel-cli`, database searches, DOI/CrossRef access, and sometimes web search. | Rewrite into v1 core skill. | Core `literature_workflow.md`, `paper_card_schema.md`, `evidence_ledger.md`, and optional future citation-verification tool. | Review phases, explicit search logs, inclusion/exclusion criteria, dedup/screening, extraction fields, backward/forward citation chaining, DOI verification pattern. | Remove prestige-biased prioritization by venue/impact factor/author reputation. Replace biomedical quality scales with AI/ML/RL-specific evidence criteria. Do not require generated figures. Search scripts are not robust enough to be core. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/paper-lookup` | Paper search and evaluation orientation: academic databases, citation networks, paper evaluation, relevance/quality checks. | Instruction/checklist-based. No inspected scripts. May depend on external academic databases and search engines. | Rewrite into v1 core skill. | `literature_discovery.md` and `paper_triage.md`. | Separation of paper lookup, citation network expansion, and paper evaluation. | Too generic and not enough AI/ML/RL-specific checks for benchmark validity, reproducibility, code availability, or dataset leakage. | No per-skill license observed in frontmatter; covered by root MIT unless upstream states otherwise. |
| `K-Dense-AI/scientific-agent-skills/skills/research-lookup` | General research search strategy, source/database guidance, and research evaluation. | Instruction/checklist-based. External database/search dependent. | Rewrite into v1 core skill. | `research_scoping.md` and `literature_discovery.md`. | Query expansion, source diversity, evaluation of research sources. | Too broad for AI/ML/RL without explicit treatment of arXiv/preprints, benchmark papers, code repos, leaderboards, and replication artifacts. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/exa-search` | Search wrapper guidance for Exa-style web/research search. | Dependent on Exa/API tooling. | Preserve as optional tool pack pattern. | Optional `tool_packs/search_exa.md`. | Tool abstraction idea: search as a replaceable provider behind the literature workflow. | Not a core requirement. Avoid hard dependency on one commercial provider. Needs provenance logging and query/result capture before use in v1. | Skill frontmatter declares MIT and external author metadata. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/bgpt-paper-search` | Paper search guidance tied to BGPT paper-search capability. | Dependent on external BGPT service/tooling. | Preserve as optional tool pack pattern. | Optional `tool_packs/paper_search_provider.md`. | Provider-specific paper search can plug into the common search-log schema. | Reject as core because it couples the skill to a specific service. Use only as an example of a provider adapter. | Skill frontmatter declares MIT and external author metadata. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/citation-management` | Metadata extraction, BibTeX generation/formatting, DOI/PMID/arXiv/URL handling, citation validation, deduplication, and source API guidance. | Instruction plus scripts. Scripts call DOI/CrossRef, PubMed E-utilities, arXiv/DataCite patterns, Google Scholar via `scholarly`, and BibTeX formatting/validation routines. External API/tool dependent. | Defer to a future deterministic tool; reuse workflow in v1 core. | Core `citation_audit.md`; future `tools/citation_verifier`. | Never treat citations as memory-only; extract identifiers; validate required fields; deduplicate; use DOI/CrossRef where possible. | Google Scholar scraping/proxy behavior is brittle and potentially fragile. Biomedical/PubMed emphasis is not central to AI/ML/RL. Regex BibTeX parsing is useful only as a prototype. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/pyzotero` | Zotero library operations through Pyzotero example usage. | Dependent on Zotero API/Pyzotero and user credentials. | Preserve as optional tool pack. | Optional `tool_packs/zotero.md`. | Zotero as an import/export backend for paper collections and citation libraries. | Not required for v1. Needs careful credential handling and clear read/write boundaries before integration. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/hypothesis-generation` | Hypothesis formulation and experimental-design references. | Instruction/checklist-based. No required scripts. | Rewrite into v1 core skill. | `hypothesis_and_gap_analysis.md`. | Convert gaps into testable hypotheses; connect hypotheses to variables, mechanisms, predictions, and experiments. | Must add AI/ML/RL-specific hypothesis forms: algorithmic claim, scaling claim, representation claim, data/benchmark claim, RL environment/generalization claim. Needs falsification criteria and evidence burden. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/scientific-brainstorming` | General scientific ideation techniques and creativity frameworks. | Instruction/checklist-based. | Rewrite selectively into v1 core. | `ideation_prompts.md`. | Divergent/convergent ideation, analogy, constraint manipulation, and structured brainstorming. | Too generic unless constrained by literature evidence, feasibility, and falsifiability. Must prevent idea generation that invents unsupported gaps. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/scientific-critical-thinking` | Critique framework for methodology, bias, validity, statistical analysis, evidence quality, logical fallacies, research design, and claim evaluation. | Instruction/checklist-based. | Reuse with substantial rewrite into v1 core. | `rigor_review.md`, `claim_audit.md`, `experimental_design_review.md`. | Internal/external/construct/statistical validity; bias detection; claim proportionality; statistical red flags; transparency and reproducibility checks. | Biomedical evidence hierarchy and general science framing are insufficient for AI/ML/RL. Add benchmark leakage, compute/reporting, seed variance, ablation logic, baseline fairness, environment stochasticity, dataset shift, and implementation confounds. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/peer-review` | Scientific peer review criteria and review templates. | Instruction/template-based. | Rewrite into v1 core and writing module. | `peer_review.md` and `writing_review.md`. | Structured review categories: significance, novelty, clarity, methods, evidence, limitations, recommendation framing. | Must be adapted to AI conference/journal expectations and avoid generic review prose. Needs explicit checks for overclaiming, artifact availability, benchmark validity, and reproducibility. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/scholar-evaluation` | Scholar/profile evaluation and scoring, including script-based weighted scoring. | Instruction plus scoring script. External metric/source dependent. | Reject for v1 core. | None, except possibly a cautionary anti-pattern in `source_quality.md`. | Some source evaluation awareness. | Scholar scoring is not a general research capability and risks authority bias. Weighted scoring creates false precision and should not drive literature relevance. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/statistical-analysis` | Statistical test selection and assumption checking; script for normality/variance/independence style checks. | Instruction plus Python script. | Rewrite small parts into v1 rigor module; defer scripts. | `experimental_design_review.md` and optional future `stats_checklist.md`. | Effect sizes, assumptions, multiple comparisons, missing data, statistical reporting awareness. | Classic statistical-test workflow is incomplete for AI/ML/RL. Need multi-seed reporting, confidence intervals, bootstrap/permutation where appropriate, hyperparameter search accounting, RL variance, and benchmark suite aggregation. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/scientific-writing` | General scientific manuscript structure and journal-format guidance. | Instruction/reference-based. | Rewrite into v1 writing module. | `scientific_writing.md`. | IMRaD-style structure, clarity, contribution framing, limitations, and citation integration. | Too generic. Needs AI/ML/RL paper sections: method, algorithm/pseudocode, datasets, compute, implementation details, ablations, baselines, ethical/limitations, reproducibility checklist. | Skill frontmatter declares MIT. Root repo MIT. |
| `K-Dense-AI/scientific-agent-skills/skills/scientific-slides` | Scientific presentation structure, conference templates, design principles. | Instruction/reference-based. | Rewrite into optional output module. | Optional `outputs/presentation_support.md`. | Presentation adaptation of research artifacts into talks/slides. | Not core to research reasoning. Needs to remain downstream of verified claims and evidence. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/0-autoresearch-skill` | Autonomous research orchestration: bootstrap literature, define hypotheses, run experiments, track state, loop over results, and route to domain skills. Template tracks project, literature, hypotheses, experiments, outer loop, and workspace. | Instruction plus state template. Strongly autonomous. Assumes tools for search, code execution, experiments, and domain skills. | Preserve state-management and workflow discipline only; reject autonomous execution behavior for v1. | `research_state.md`, `workflow_orchestrator.md`, and `project_log_schema.md`. | Literature/hypothesis/experiment state, proxy metric/baseline tracking, explicit sanity checks, negative result tracking, confirmatory vs exploratory labels, outer-loop reflection. | Remove "never stop" and autonomous experiment execution. V1 should support planning and analysis, not unbounded agentic research runs. Must add user checkpoints and evidence thresholds. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/20-ml-paper-writing/ml-paper-writing` | ML paper writing guidance, citation discipline, reviewer criteria, figure/table guidance. Strong emphasis on not hallucinating citations and verifying claims against papers. | Instruction/reference-based. Lists dependencies on `semanticscholar`, `arxiv`, `habanero`, `requests` for citation workflows. | Reuse with adaptation into v1 core writing and citation audit. | `citation_audit.md`, `scientific_writing.md`, `peer_review.md`. | "Never cite from memory"; verify citations through multiple sources; mark placeholders when not verified; connect claims to cited evidence; reviewer criteria and figure/table quality checks. | Must generalize beyond ML paper writing into reading, reviewing, proposals, and presentations. Dependencies should remain optional until deterministic tools are built. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/20-ml-paper-writing/systems-paper-writing` | Systems-style paper writing patterns: motivation, architecture, evaluation, artifact discussion. | Instruction/reference-based. | Preserve as optional writing reference. | Optional `topic_packs/systems_ml_writing.md`. | Useful for AI systems, agents, infrastructure, and evaluation-heavy papers. | Too specific for v1 core. Do not make systems framing the default for all AI/ML/RL research. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/20-ml-paper-writing/academic-plotting` | Academic plotting guidance and Python plotting dependencies. | Instruction plus plotting-library dependencies. | Defer to future tool/output pack. | Optional future `outputs/figures_and_tables.md`. | Figure quality, plot type selection, and publication presentation standards. | Not core to research-analysis skill. Should be used only after evidence/data are real and traceable. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/20-ml-paper-writing/presenting-conference-talks` | Conference talk and slide structure with optional `python-pptx`. | Instruction plus optional presentation-generation dependency. | Defer to optional output pack. | Optional `outputs/presentation_support.md`. | Talk structure and slide translation of research contributions. | Not core. Must avoid generating presentation claims unsupported by the evidence ledger. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/21-research-ideation/brainstorming-research-ideas` | Research ideation frameworks: problem-first/solution-first, abstraction ladder, contradictions, cross-pollination, boundary cases, simplicity tests, stakeholder rotation, composition/decomposition, and explanation tests. | Instruction/reference-based. | Rewrite selectively into v1 core. | `ideation_prompts.md` and `hypothesis_and_gap_analysis.md`. | Diverse ideation lenses and convergent filtering. | Needs evidence gates: every idea should map to literature gaps, assumptions, falsification criteria, required experiments, and feasibility. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/21-research-ideation/creative-thinking-for-research` | Creative research thinking: combinatorial creativity, reformulation, analogy, constraint manipulation, inversion, abstraction, adjacent possible, productive tension. | Instruction/reference-based. | Rewrite selectively into v1 core. | `ideation_prompts.md`. | Useful ideation operators for moving beyond incremental literature summaries. | Too unconstrained alone. Must be paired with claim/evidence ledgers and feasibility checks to avoid speculative drift. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/ara-compiler` | Agent-native research artifact schema: problem, claims, concepts, experiments, solution, related work, evidence, trace, and manuscript-oriented outputs. Claim entries include status, falsification criteria, proof/evidence basis, dependencies, and tags. | Template/schema-based. | Reuse schema ideas with simplification into v1 core. | `research_artifact_schema.md`, `claim_ledger.md`, `evidence_ledger.md`, `experiment_plan_schema.md`. | Claim-centered artifact structure, dependency tracking, falsification criteria, evidence basis, experiment linkage, and traceability. | Full ARA structure is too heavy for v1. Simplify to paper cards, claim ledger, evidence ledger, comparison matrix, and experiment plan. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/research-manager` | Research artifact management and provenance tags: `user`, `ai-suggested`, `ai-executed`, `user-revised`; conservative provenance handling. | Instruction plus reference schema. | Reuse with minimal adaptation. | `provenance_policy.md` and `research_state.md`. | Conservative provenance rules, no silent upgrading of AI-suggested material, history preservation, explicit user revision tagging. | Add citation/evidence provenance types, e.g. source-derived, inferred, speculative, unverified, externally verified. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/rigor-reviewer` | Rigor review over evidence relevance, falsifiability, scope calibration, argument coherence, exploration integrity, and methodological rigor. Includes type-aware entailment: causal claims require ablations, generalization claims require heterogeneous tests, improvement claims require baselines, descriptive claims require sampling, scoping claims require bounds. | Instruction/checklist-based. | Reuse with substantial adaptation into v1 core. | `rigor_review.md`, `claim_audit.md`, `experimental_design_review.md`. | The six dimensions, type-aware evidence burdens, claim-to-evidence checking, baseline/ablation/statistical-reporting/metric-alignment/reproducibility checks. | Needs AI/ML/RL-specific expansion: compute budgets, dataset contamination, hyperparameter fairness, RL stochasticity, environment versions, seed variance, benchmark saturation, and code/config availability. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/10-optimization/ml-training-recipes` | Practical ML training recipes across architectures, optimizers, domains, scaling, and experiment loop. | Instruction/reference-based. Tied to PyTorch-style ML training; dependency declares `torch>=2.0.0`. | Preserve as optional experiment-design/tool pack. | Optional `topic_packs/ml_training_experiments.md`. | Useful implementation and reproduction planning patterns: training loop, optimizer choices, scaling concerns, debugging and experiment iteration. | Too implementation-centric for v1 core. Does not replace benchmark design, literature synthesis, or evidence audit. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/11-evaluation/lm-evaluation-harness` | Guidance for running EleutherAI `lm-eval`, standard benchmarks, custom tasks, API evaluation, distributed evaluation, and training comparison. | Tool/framework-dependent: `lm-eval`, `transformers`, `vllm`. | Preserve as optional tool pack. | Optional `tool_packs/lm_eval_harness.md`. | Concrete evaluation execution patterns for language-model research. | Not general AI/ML/RL core. V1 should focus on choosing valid benchmarks, baselines, contamination checks, and interpreting results before tool execution. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/11-evaluation/bigcode-evaluation-harness` | Code-generation benchmark execution: HumanEval, MBPP, MultiPL-E, pass@k, Docker isolation, custom tasks, common issues. | Tool/framework-dependent: BigCode harness, Transformers, Accelerate, Datasets, Docker. | Preserve as optional tool pack. | Optional `tool_packs/code_model_eval.md`. | Benchmark-specific reproducibility and execution details for code model evaluation. | Too narrow for core. Needs contamination, prompt protocol, sandbox/security, and statistical uncertainty checks before use. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/11-evaluation/nemo-evaluator` | Containerized model evaluation orchestration with adapters, configs, custom benchmarks, and execution backends. | Tool/framework-dependent: NeMo evaluator, Docker, backends. | Preserve as optional tool pack. | Optional `tool_packs/nemo_evaluator.md`. | Config-driven evaluation orchestration pattern. | Too tool-specific for core. Use only after v1 defines benchmark validity and evidence reporting requirements. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/04-mechanistic-interpretability/transformer-lens` | TransformerLens workflows: hook points, activation caching, activation patching, circuit analysis. | Framework-dependent: TransformerLens, PyTorch ecosystem. | Preserve as optional topic/tool pack. | Optional `topic_packs/mechanistic_interpretability.md`. | Clear workflow for activation-level analysis and circuit hypotheses. | Not general AI/ML/RL core. Needs safeguards against overinterpreting circuits and feature attributions. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/04-mechanistic-interpretability/saelens` | SAE Lens workflows: SAE training, feature analysis, model analysis, superposition/feature discovery. | Framework-dependent: SAELens and model-analysis stack. | Preserve as optional topic/tool pack. | Optional `topic_packs/mechanistic_interpretability.md`. | Useful for representation-analysis extension tasks. | Avoid making SAE methodology a default representation-analysis method. Add controls, baselines, feature validation, and causal tests. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/04-mechanistic-interpretability/pyvene` | Causal intervention workflows: intervention types, activation patching, interchange intervention training. | Framework-dependent: Pyvene and model internals. | Preserve as optional topic/tool pack. | Optional `topic_packs/mechanistic_interpretability.md`. | Strong fit for causal representation claims and intervention-based testing. | Too specialized for core. Needs explicit connection from intervention results to supported claims. | Skill frontmatter declares MIT. Root repo MIT. |
| `Orchestra-Research/AI-Research-SKILLs/04-mechanistic-interpretability/nnsight` | NNsight workflows: local/remote model internals, interventions, activation analysis, NDIF-style remote execution. | Framework/API-dependent; may involve remote model services. | Preserve as optional topic/tool pack with safeguards. | Optional `topic_packs/mechanistic_interpretability.md`. | Useful for tracing and intervening in model internals when infrastructure is available. | Remote execution/privacy and provider dependency concerns. Not core. Needs clear data-handling and reproducibility rules. | Skill frontmatter declares MIT. Root repo MIT. |

## Capability-Level Reuse Decisions

### Core v1 Material to Adapt

The following upstream material should directly shape the v1 core skill, rewritten and integrated rather than copied:

- Literature review workflow from K-Dense `literature-review`.
- Paper lookup and research lookup patterns from K-Dense `paper-lookup` and `research-lookup`.
- Citation verification discipline from K-Dense `citation-management` and Orchestra `ml-paper-writing`.
- Claim/evidence/falsification schema from Orchestra `ara-compiler`.
- Provenance discipline from Orchestra `research-manager`.
- Rigor-review dimensions and type-aware evidence burdens from Orchestra `rigor-reviewer`.
- Scientific criticism patterns from K-Dense `scientific-critical-thinking`.
- Peer review and writing structure from K-Dense `peer-review`, K-Dense `scientific-writing`, and Orchestra `ml-paper-writing`.
- Ideation operators from K-Dense `hypothesis-generation`, K-Dense `scientific-brainstorming`, Orchestra `brainstorming-research-ideas`, and Orchestra `creative-thinking-for-research`.

### Optional Tool Packs

These should not be v1 dependencies, but the v1 architecture should leave clean extension points for them:

- Exa search provider.
- BGPT paper search provider.
- Zotero/Pyzotero library integration.
- LM evaluation harness.
- BigCode evaluation harness.
- NeMo evaluator.
- Academic plotting and presentation generation.

### Optional Topic Packs

These should remain outside the v1 core:

- Mechanistic interpretability and representation analysis pack, combining TransformerLens, SAELens, Pyvene, and NNsight concepts.
- ML training/reproduction pack based on Orchestra `ml-training-recipes`.
- Systems ML writing pack based on Orchestra `systems-paper-writing`.

### Rejected or Non-Core Material

- K-Dense `scholar-evaluation` scoring should not be reused in v1. It risks authority bias and false precision.
- Autonomous execution behavior from Orchestra `0-autoresearch-skill` should not be reused. Only its state-management and discipline patterns are appropriate.
- Provider-specific search behavior should not be embedded into the core workflow.
- Any upstream instruction that prioritizes papers based on author prestige, venue prestige, impact factor, or citation count should be treated as a weak prior at most, never as a quality criterion.

## Required Rewrites for General AI/ML/RL Research

The upstream repositories leave several gaps that v1 must address explicitly:

- AI/ML/RL benchmark validity: contamination, benchmark saturation, train/test leakage, leaderboard overfitting, benchmark-suite representativeness, and prompt/evaluation protocol drift.
- Experimental rigor: multi-seed reporting, uncertainty intervals, hyperparameter search fairness, compute budget comparability, baseline strength, ablation necessity, environment versions, and RL stochasticity.
- Reproducibility: code availability, config completeness, data preprocessing, random seeds, hardware/software stack, training/evaluation scripts, model checkpoints, and negative result logging.
- Claim discipline: every claim should be classified by type and mapped to evidence requirements before conclusions are drafted.
- Evidence traceability: paper cards, quote/claim links, citation status, provenance tags, and explicit unsupported/speculative labels.
- Generality: the core should support supervised learning, representation learning, LLMs, RL, robotics, agents, systems, and theory-adjacent work without hard-coding one topic.
- Safety against overclaiming: no invented citations, no unsupported causal claims, no method comparison without baseline and setting normalization, and no broad conclusions from narrow tasks.

## Architecture Impact

The reuse analysis does not change the proposed v1 architecture. It makes the intended module boundaries more concrete:

- `SKILL.md`: orchestrates research modes and routes to reference modules.
- `references/research_scoping.md`: question formulation, scope, assumptions, and initial search plan.
- `references/literature_discovery.md`: provider-agnostic search, query logs, citation chaining, and screening.
- `references/paper_card_schema.md`: structured paper reading for AI/ML/RL.
- `references/evidence_ledger.md`: evidence items, source provenance, and citation verification status.
- `references/claim_ledger.md`: claim types, evidence burden, scope, falsification criteria, and support status.
- `references/comparison_matrix.md`: method/assumption/dataset/benchmark/metric comparison.
- `references/hypothesis_and_gap_analysis.md`: gaps, hypotheses, predictions, feasibility, and falsification.
- `references/experimental_design_review.md`: baselines, ablations, benchmarks, metrics, seeds, compute, RL-specific considerations, and reproduction plans.
- `references/rigor_review.md`: adapted rigor dimensions and overclaiming audit.
- `references/scientific_writing.md`: paper/proposal/review/presentation support grounded in the evidence and claim ledgers.
- `references/provenance_policy.md`: attribution, provenance tags, verified/unverified status, and user-confirmation rules.
- Optional `tool_packs/`: search providers, citation verifiers, Zotero, evaluation harnesses.
- Optional `topic_packs/`: mechanistic interpretability, ML training recipes, systems ML writing, RL-specific reproduction protocols.

The core should remain provider-agnostic and instruction/schema-oriented in v1, with deterministic tools deferred until the schemas and evaluation criteria are stable.
