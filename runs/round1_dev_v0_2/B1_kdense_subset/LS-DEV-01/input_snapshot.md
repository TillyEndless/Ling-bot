# Variant Runtime Instructions

You are running benchmark variant `B1_kdense_subset` for the `literature_analysis_and_research_rigor` module. Follow only the variant skill/reference content included below. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Variant Skill And References

## Variant File: variant/kdense_literature_research_rigor/SKILL.md

---
name: kdense-literature-research-rigor-subset
description: Instruction-only K-Dense-derived subset for fixed-source literature review, citation/evidence handling, scientific criticism, and synthesis. No tools, scripts, APIs, retrieval, or external services.
license: MIT-derived-upstream-patterns-with-attribution
---

# K-Dense Subset: Literature Analysis And Research Rigor

Use this skill when the task asks for research literature review, paper reading, citation/evidence handling, scientific criticism, or synthesis from supplied material.

This variant is instruction/reference-only. It must not retrieve, search, execute scripts, call APIs, manage a citation library, parse PDFs, or use external databases. If the user asks for facts not present in the supplied material, mark them as unavailable or unsupported.

## Operating Rules

1. Work only from the provided source packet and task prompt.
2. Build an evidence-first response: every important claim should point to a supplied source, section, page, figure, table, or quoted/excerpted location when available.
3. Separate source claims, your synthesis, and unsupported possibilities.
4. For literature reviews, account for every supplied source before synthesizing themes.
5. For criticism, assess validity, bias, methods, evidence quality, limitations, and claim scope.
6. For proposal or hypothesis tasks, turn observations into testable claims only when the packet supports the motivation; mark broader novelty or field-gap claims as needing external review.
7. Do not rank methods globally unless the packet contains directly comparable evidence.

## Workflow

1. Scope the task: identify the research question, the fixed corpus, requested output sections, and forbidden external evidence.
2. Inventory sources: make a source coverage table with role, evidence type, claims, methods, experiments, and limitations.
3. Extract evidence: record claims, evidence locations, methods, datasets, metrics, baselines, comparisons, and caveats.
4. Evaluate quality: ask whether the evidence is direct, indirect, incomplete, contradictory, or out of scope.
5. Synthesize cautiously: group sources into themes or methods, then state what the corpus supports and what remains unresolved.
6. Audit conclusions: remove unsupported generalizations, invented citations, prestige-based judgments, or claims that exceed the supplied evidence.

## Preferred Output Moves

- Use tables for source coverage, claim-evidence mapping, comparison, and limitations.
- Use short evidence labels such as source name plus page/section/table when provided.
- Include an explicit unsupported-or-unknown section whenever the task asks for synthesis or comparison.
- Preserve uncertainty instead of filling missing methods, metrics, or results from memory.

Load the references in this variant only as needed:

- `references/literature_review_structure.md`
- `references/evidence_and_citation_handling.md`
- `references/scientific_criticism.md`
- `references/synthesis_and_hypotheses.md`


## Variant File: variant/kdense_literature_research_rigor/references/evidence_and_citation_handling.md

# Evidence And Citation Handling

Adapted from K-Dense citation-management and literature-review patterns, without scripts or external services.

## Evidence Ledger

For each important claim, record:

| Claim | Source | Location supplied | Evidence type | Support status | Caveat |
|---|---|---|---|---|---|

Support status should be one of: direct, indirect, partial, contradicted, absent, or speculative.

## Citation Discipline

- Cite only sources supplied in the packet.
- If metadata is incomplete, do not invent DOI, venue, version, page, or author details.
- Prefer supplied page, section, figure, and table locations over generic source mentions.
- If the packet gives only a general source note, cite that note and mark the granularity as limited.
- Separate bibliographic identity from evidence support: a real source is not automatically evidence for a claim.

## Unsupported Evidence Policy

- Incidental background knowledge may be mentioned only if clearly outside the evidence base and not used to support a conclusion.
- Any conclusion, method ranking, novelty claim, or causal claim must be grounded in supplied evidence.
- If evidence is missing, write “not established by the packet” rather than guessing.


## Variant File: variant/kdense_literature_research_rigor/references/literature_review_structure.md

# Literature Review Structure

Adapted from K-Dense literature-review, paper-lookup, and research-lookup workflow patterns.

## Fixed-Corpus Review

For a closed packet, treat literature review as mapping and synthesis rather than discovery.

1. Corpus inventory: list every supplied source and its apparent role.
2. Screening within packet: identify central, supporting, background, boundary, and unusable sources using only packet evidence.
3. Extraction fields: research question, method, assumptions, data, experimental setup, result type, limitations, and relevance.
4. Thematic grouping: cluster sources by problem, method family, evidence type, or claim type.
5. Synthesis: state relationships among sources and qualify them by evidence strength.
6. Gaps: report gaps visible in the packet, not gaps claimed for the entire field unless external review is allowed.

## Literature Map Template

| Source | Role in packet | Research problem | Method or artifact | Evidence type | Limitations | Use in synthesis |
|---|---|---|---|---|---|---|

## Search-Derived Workflows Disabled

K-Dense search, database, and citation-chaining patterns are not active in this variant. When external retrieval is disabled, do not simulate search results or cite absent work.


## Variant File: variant/kdense_literature_research_rigor/references/scientific_criticism.md

# Scientific Criticism

Adapted from K-Dense scientific-critical-thinking and peer-review patterns.

## Critique Axes

- Internal validity: does the method or experiment test what it claims?
- Construct validity: do tasks, metrics, and proxies match the intended concept?
- External validity: what populations, settings, tasks, models, or environments are covered?
- Statistical validity: are seeds, variability, uncertainty, aggregation, and multiple comparisons handled?
- Reproducibility: are data, code, settings, prompts, models, hardware, and configs sufficiently specified?
- Bias and confounds: are there dataset artifacts, leakage, selection bias, or unfair baselines?
- Claim proportionality: are conclusions limited to the actual evidence?

## Review Pattern

1. State the claim under review.
2. Identify the direct evidence.
3. List missing controls, baselines, metrics, or reporting details.
4. Classify severity and likely effect on the claim.
5. Suggest a corrected, narrower claim or improved protocol.

Avoid prestige-based judgments and avoid treating citation count, venue, or author identity as proof of quality.


## Variant File: variant/kdense_literature_research_rigor/references/synthesis_and_hypotheses.md

# Synthesis And Hypotheses

Adapted from K-Dense hypothesis-generation and scientific brainstorming patterns, constrained by evidence.

## Synthesis Rules

- Build synthesis from extracted evidence, not from memory.
- Name the synthesis operation: grouping, contrast, causal conjecture, mechanism hypothesis, or gap identification.
- Mark whether a statement is source-stated, cross-source synthesis, or proposal speculation.
- Do not turn absence from a small fixed packet into a field-wide absence.

## Hypothesis Template

| Hypothesis | Evidence motivation | Prediction | Disconfirming observation | Required experiment | Feasibility caveat |
|---|---|---|---|---|---|

## Useful Checks

- Is the hypothesis falsifiable?
- Does it identify observables and controls?
- Does it require stronger evidence than the packet provides?
- Does it distinguish correlation, recoverability, mechanism, and causation?


## Variant File: variant/reuse_and_license_notes.md

# B1 Reuse And License Notes

This variant selectively adapts K-Dense-derived instruction patterns for literature review, citation/evidence handling, scientific criticism, peer-review framing, and hypothesis formulation.

No upstream scripts, APIs, database clients, generated templates, search providers, or executable services are included. The implementation is rewritten in compact form for fixed-source benchmark execution.

## Components Used

| Upstream component | Files consulted per ledger | Adaptation decision | License status from audit |
|---|---|---|---|
| `K-Dense-AI/scientific-agent-skills/skills/literature-review` | `SKILL.md`, citation/database references, review template | Rewritten into fixed-corpus review structure | MIT observed in skill frontmatter; root repository MIT |
| `K-Dense-AI/scientific-agent-skills/skills/citation-management` | `SKILL.md`, citation/database references | Rewritten as evidence and citation discipline only | MIT observed in skill frontmatter; root repository MIT |
| `K-Dense-AI/scientific-agent-skills/skills/scientific-critical-thinking` | `SKILL.md`, evidence, bias, validity references | Rewritten as critique axes and review pattern | MIT observed in skill frontmatter; root repository MIT |
| `K-Dense-AI/scientific-agent-skills/skills/peer-review` | `SKILL.md`, review criteria/templates | Rewritten as criticism scaffolding | MIT observed in skill frontmatter; root repository MIT |
| `K-Dense-AI/scientific-agent-skills/skills/hypothesis-generation` | `SKILL.md`, design/framework references | Rewritten as evidence-constrained hypothesis template | MIT observed in skill frontmatter; root repository MIT |

## Explicit Runtime Exclusions

- No scripts copied or enabled.
- No API keys, external services, citation databases, PDF parsers, or search tools.
- No Orchestra-derived material.
- No benchmark-specific paper names, task identifiers, expected answers, or development answer-key content.


## Variant File: variant/variant_manifest.yaml

variant_id: B1_kdense_subset
module_scope: literature_analysis_and_research_rigor
implementation_type: instruction_reference_only
runtime_tools_enabled: false
external_services_enabled: false
dynamic_retrieval_enabled: false
scripts_enabled: false
upstream_basis:
  repository: K-Dense-AI/scientific-agent-skills
  components:
    - path: skills/literature-review/SKILL.md
      consulted_files:
        - skills/literature-review/SKILL.md
        - skills/literature-review/references/citation_styles.md
        - skills/literature-review/references/database_strategies.md
        - skills/literature-review/assets/review_template.md
      use: adapted_workflow_pattern
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: skills/citation-management/SKILL.md
      consulted_files:
        - skills/citation-management/SKILL.md
        - skills/citation-management/references/citation_styles.md
        - skills/citation-management/references/database_apis.md
      use: adapted_citation_discipline_without_tools
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: skills/scientific-critical-thinking/SKILL.md
      consulted_files:
        - skills/scientific-critical-thinking/SKILL.md
        - skills/scientific-critical-thinking/references/bias_detection.md
        - skills/scientific-critical-thinking/references/evidence_evaluation.md
        - skills/scientific-critical-thinking/references/validity_frameworks.md
      use: adapted_critique_axes
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: skills/peer-review/SKILL.md
      consulted_files:
        - skills/peer-review/SKILL.md
        - skills/peer-review/references/review_criteria.md
        - skills/peer-review/references/review_templates.md
      use: adapted_review_scaffolding
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: skills/hypothesis-generation/SKILL.md
      consulted_files:
        - skills/hypothesis-generation/SKILL.md
        - skills/hypothesis-generation/references/experimental_design.md
        - skills/hypothesis-generation/references/hypothesis_frameworks.md
      use: adapted_hypothesis_template
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
runtime_exclusions:
  - no K-Dense scripts included
  - no APIs included
  - no database search included
  - no external citation validation included
  - no Orchestra-derived rules included
  - no B3-original AI/ML/RL guidance included


# Benchmark Task Input

Benchmark version: round1_dev_v0.2
Task ID: LS-DEV-01
Task type: literature_mapping
Topic: transformer efficiency
Evaluation mode: closed_source

## Research Question

Within the fixed source packet, what are the main research lines for making transformer computation more efficient, and what evidence does each paper provide?

## User Prompt

Produce a fixed-corpus literature map on transformer efficiency for AI/ML research.
Use only the provided source packet. Do not perform external retrieval.
Return a corpus coverage table, taxonomy of efficiency approaches, method-difference matrix, evidence-grounded synthesis, unsupported-synthesis warnings, and research gaps visible within the corpus.
Distinguish paper claims from your synthesis. If a method, metric, or conclusion is not supported by the packet, mark it as unsupported.


## Required Output Sections

- corpus_coverage_table
- literature_taxonomy
- method_difference_matrix
- core_paper_identification
- evidence_grounded_gap_list
- unsupported_synthesis_warnings

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.

# Frozen Model Input Packet

# LS-DEV-01 Model Input Packet

## Corpus

1. Efficient Transformers: A Survey, arXiv:2009.06732, 39-page arXiv PDF.
2. Linformer: Self-Attention with Linear Complexity, arXiv:2006.04768, 12-page arXiv PDF.
3. Longformer: The Long-Document Transformer, arXiv:2004.05150, 17-page arXiv PDF.
4. FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness, arXiv:2205.14135, 34-page arXiv PDF.
5. LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Efficient Transformers survey:

- The survey frames transformer efficiency around the standard attention mechanism's quadratic dependence on sequence length and organizes many approaches for reducing time or memory.
- The paper presents itself as a survey and taxonomy of efficient Transformer approaches.
- Relevant evidence locations: abstract; survey taxonomy sections; comparison tables; discussion/limitations.

Linformer:

- The paper proposes projecting keys and values to a lower-dimensional sequence axis to make self-attention linear in sequence length under its assumptions.
- Its Table 1 compares per-layer time complexity, listing Linformer as O(n) where standard self-attention is quadratic.
- Its empirical discussion includes validation perplexity and downstream classification evidence in the paper's reported settings.
- Relevant evidence locations: abstract; introduction; Section 3 method; Figure 2; Table 1; experiment section.

Longformer:

- The paper proposes local windowed attention plus task-motivated global attention for long documents.
- It claims linear scaling with sequence length for its attention pattern and evaluates both autoregressive language modeling and downstream long-document tasks.
- The paper focuses on long-document Transformer architecture and attention patterns.
- Relevant evidence locations: abstract; Figure 1; Table 1; Section 3; Tables 7-11; appendices on implementation details.

FlashAttention:

- The paper introduces an IO-aware exact attention algorithm that reduces memory reads/writes between GPU memory levels.
- The paper describes FlashAttention as an exact attention algorithm.
- The abstract states that FlashAttention is an IO-aware exact attention algorithm and also reports an extension to block-sparse attention.
- Section 3 describes an IO-aware attention algorithm using tiling to reduce HBM reads and writes while computing exact attention without materializing the full attention matrix.
- Reported speed and memory evidence appears in experiment tables and figures with stated model, hardware, and sequence settings.
- Relevant evidence locations: p. 1 Abstract; p. 4 Section 3; p. 7 Section 4.1 and Table 1 for BERT-large training-time comparison; p. 8 Table 2 for GPT-2 training-time comparison; theorem/complexity discussion; experiment tables and figures.

LoRA:

- The paper freezes pretrained model weights and injects trainable low-rank update matrices for adaptation.
- The paper frames LoRA around downstream adaptation with frozen pretrained weights and trainable low-rank update matrices.
- It reports large reductions in trainable parameters and memory for adaptation settings and evaluates on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Relevant evidence locations: abstract; Section 1; Section 4; Table 1; Table 2; GPT-3 experiment discussion; limitations paragraph in Section 4.

