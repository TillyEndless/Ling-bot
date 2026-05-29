# Skill Architecture Proposal

## Recommendation

Build the first version as one orchestrating skill with modular reference files and optional tool/topic adapters.

Do not start with many independent skills. The target behavior is one coherent research workflow: scope a question, discover literature, read papers, synthesize evidence, form hypotheses, design experiments, audit claims, and support writing. Splitting too early would recreate the upstream problem: many useful fragments but no shared evidence model.

The first version should therefore be a hybrid:

- One core skill: `ai-ml-rl-research`
- Modular references loaded on demand
- Optional tool adapters for search/citations/parsing/tracking
- Optional topic packs for RL, mech interp, LLM evaluation, systems, robotics, etc.

## Design Rationale

The core skill should be tool-neutral and reliability-first. It should define the research process, artifact schemas, evidence standards, and decision gates. Tools should be adapters, not architecture.

Upstream patterns to preserve:

- From Orchestra `autoresearch`: staged state, inner/outer loop, protocol-before-results, confirmatory vs exploratory distinction.
- From Orchestra ARA: provenance tags, claim/evidence separation, falsification criteria, semantic rigor review.
- From Orchestra `ml-paper-writing`: citation hallucination prevention and placeholder discipline.
- From K-Dense `literature-review`: search planning, inclusion/exclusion, screening, extraction, citation chaining.
- From K-Dense `citation-management`: programmatic metadata retrieval and validation.
- From K-Dense `scientific-critical-thinking` and `peer-review`: overclaiming, bias, limitations, reproducibility critique.
- From K-Dense `statistical-analysis`: effect sizes, CIs, assumptions, power where applicable.

Upstream patterns to rewrite:

- Replace mandatory visuals with “figures only when they clarify evidence.”
- Replace biomedical frameworks with AI/ML/RL-specific evidence rubrics.
- Replace framework-first execution with question-first planning.
- Replace autonomous “never stop” with explicit escalation and uncertainty gates.
- Replace single-score evaluation with severity-ranked findings and support status.

## Proposed Directory Structure

```text
ai-ml-rl-research/
  SKILL.md
  references/
    research_intake.md
    literature_discovery.md
    paper_reading_card.md
    synthesis_taxonomy.md
    hypothesis_management.md
    experiment_protocols.md
    benchmark_baseline_ablation.md
    rl_research_workflows.md
    reproducibility_audit.md
    evidence_claim_ledger.md
    citation_audit.md
    writing_review_presentations.md
    quality_gates.md
  references/topic-packs/
    llm_evaluation.md
    llm_post_training_rlhf.md
    classical_rl.md
    mechanistic_interpretability.md
    representation_learning.md
    systems_and_scaling.md
    agents_and_rag.md
    robotics_world_models.md
  references/tool-adapters/
    semantic_scholar_arxiv_crossref.md
    zotero.md
    exa_parallel_web.md
    pdf_markdown_extraction.md
    experiment_tracking.md
  templates/
    research_state.yaml
    paper_card.md
    literature_matrix.md
    evidence_ledger.md
    claim_ledger.md
    experiment_protocol.md
    reproduction_plan.md
    review_report.md
```

No scripts are required for v1. Scripts can be added later only where deterministic behavior is needed, such as citation metadata retrieval, BibTeX validation, PDF extraction, or evidence-ledger validation.

## Core `SKILL.md` Responsibilities

`SKILL.md` should stay compact and define:

- When to use the skill.
- The default workflow.
- Which reference file to read for each task.
- The mandatory reliability rules.
- The artifact discipline: paper cards, evidence ledger, claim ledger, protocol, reproduction plan.
- The escalation rules: when to ask the user, when to mark uncertainty, when not to proceed.

## Default Workflow

1. Intake and Scope
   - Clarify the research objective, contribution type, scope, constraints, and desired output.
   - If vague, produce 2-4 candidate research questions with tradeoffs.

2. Literature Discovery
   - Start with seed queries and seed papers.
   - Use multiple source types when possible.
   - Maintain a search log and coverage notes.

3. Paper Reading
   - Create structured paper cards for core papers.
   - Separate author claims from actual evidence.
   - Extract assumptions, datasets, benchmarks, metrics, baselines, ablations, limitations, and reproducibility facts.

4. Comparative Synthesis
   - Build method/taxonomy matrices.
   - Identify consensus, disagreement, and gaps.
   - Track which claims are well-supported versus speculative.

5. Hypothesis Formation
   - Convert gaps to falsifiable hypotheses.
   - Record motivating evidence and disconfirming evidence.
   - Define testable predictions and failure criteria.

6. Experiment/Reproduction Planning
   - Produce protocol before any implementation.
   - Specify baselines, ablations, datasets, metrics, seeds, compute, and analysis plan.
   - For RL, require environment/version/seed/eval episode/reward checks.

7. Evidence and Claim Audit
   - Maintain evidence ledger and claim ledger.
   - Audit overclaiming, weak citations, missing baselines, leakage, and reproducibility gaps.

8. Writing and Review
   - Draft only from the evidence ledger.
   - Mark placeholders and unsupported claims.
   - Produce reviewer-risk table and limitation language.

## Minimal Artifact Schemas

### Paper Card

Fields:

- Citation and version: title, authors, year, venue/arXiv, DOI, URL, code/data links.
- Research question.
- Contribution type.
- Main claims.
- Method summary.
- Assumptions and scope.
- Datasets/environments.
- Baselines.
- Metrics.
- Key evidence.
- Ablations.
- Limitations.
- Reproducibility facts.
- Open questions.
- Relevance to current project.
- Confidence and notes.

### Evidence Ledger

Fields:

- Evidence ID.
- Source ID.
- Evidence type: paper passage, table, figure, benchmark result, code inspection, experiment run.
- Exact location: page/section/table/figure/commit/run.
- What it directly supports.
- What it does not support.
- Extraction confidence.
- Verification status.

### Claim Ledger

Fields:

- Claim ID.
- Statement.
- Claim type: empirical, causal, comparative, theoretical, methodological, reproducibility, novelty.
- Support status: supported, weakly supported, contradicted, speculative, unknown.
- Evidence IDs.
- Falsification criteria.
- Scope boundaries.
- Overclaiming risk.
- Required next evidence.

### Experiment Protocol

Fields:

- Hypothesis.
- Prediction.
- Confirmatory or exploratory.
- Dataset/environment and split/version.
- Baselines.
- Ablations.
- Metrics and statistical plan.
- Seeds/runs.
- Compute budget.
- Failure criteria.
- Reproducibility requirements.
- Analysis plan before seeing results.

## Quality Gates

The skill should refuse to upgrade a claim to “supported” unless:

- The evidence is directly relevant to the claim type.
- The benchmark/metric matches the claim.
- Baselines are adequate for comparative claims.
- Ablations isolate the claimed mechanism when needed.
- Reproducibility facts are sufficient to understand the result.
- Limitations and scope boundaries are recorded.

For citations:

- Never invent citations or BibTeX.
- Prefer programmatic metadata retrieval.
- Mark unverified citations as placeholders.
- Verify that the cited paper actually supports the cited claim.

For AI/ML/RL experiments:

- Report variance or uncertainty for stochastic results.
- Track seeds and number of runs.
- Record data splits and preprocessing.
- Check for leakage and benchmark contamination.
- Separate exploratory discoveries from confirmatory tests.

For RL specifically:

- Record environment name, version, wrappers, observation/action spaces, reward function, time limits, seeds, evaluation episodes, deterministic/stochastic policy setting, and return distribution.
- Check reward hacking and train/eval mismatch.
- Avoid reporting only best seed or best checkpoint.

## Why Not Many Skills Yet?

Many independent skills would make routing and state sharing harder. The core research process needs one shared memory model and one evidence discipline. Topic packs can later become separate skills if they grow large, but v1 should prove that the central workflow works across topics.

## Later Expansion Path

After v1 is evaluated, split only modules that meet at least one criterion:

- They require substantial tool-specific instructions.
- They are used independently of the research workflow.
- They exceed a practical reference-file size.
- They need dedicated scripts or validation tools.

Likely future splits:

- `ai-ml-rl-literature-review`
- `ai-ml-rl-experiment-design`
- `rl-research-protocols`
- `mechanistic-interpretability-research`
- `ml-paper-claim-audit`

But these should be extracted from working practice, not guessed upfront.
