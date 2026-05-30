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
Task ID: SPR-DEV-01
Task type: single_paper_deep_reading
Topic: parameter-efficient fine-tuning
Evaluation mode: closed_source

## Research Question

What exactly does the provided LoRA-style paper claim, what evidence supports those claims, and what limitations remain?

## User Prompt

Read only the provided source packet. Produce a structured paper card, claim ledger, evidence ledger, reproducibility notes, and limitation summary.
Do not use external retrieval. If a fact is not in the packet, mark it as unknown.


## Required Output Sections

- paper_card
- claim_ledger
- evidence_ledger
- reproducibility_notes
- limitations_and_open_questions

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.

# Frozen Model Input Packet

# SPR-DEV-01 Model Input Packet

## Source

LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Core method:

- The paper proposes Low-Rank Adaptation, or LoRA.
- It freezes pretrained weights and adds trainable rank-decomposition matrices to represent updates to selected dense weight matrices.
- The method expresses an adapted weight as the frozen pretrained weight plus a low-rank update, commonly written as W0 + BA.
- Section 4.1 gives the trainable low-rank update form: W0 is frozen, A and B are trainable, and the task-specific update is represented as Delta W = BA.
- Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks, while the paper's Transformer experiments focus on selected weight matrices in attention modules.
- The paper connects this to the hypothesis that adaptation updates have low intrinsic rank.
- Relevant evidence locations: p. 1 Abstract and Figure 1; p. 2 Introduction; p. 4 Sections 4.1-4.2, including Equation 3.

Claims and evidence:

- The abstract reports reductions in trainable parameters and GPU memory in the GPT-3 175B adaptation setting.
- The abstract says LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in the paper's evaluated settings.
- Section 5 evaluates downstream task performance on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Table 1 compares inference latency of adapter-style methods and LoRA/full fine-tuning in a GPT-2 medium setup.
- Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods.
- Table 3 reports GPT-2 medium and large results on the E2E NLG Challenge.
- Table 4 reports GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons.
- The paper reports evidence concerning trainable-parameter counts, GPU-memory requirements, training throughput, inference latency, and downstream task quality in different sections and experimental settings.
- The paragraph before Section 5 reports a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the paper's stated setup.
- Section 4.1 explains that LoRA updates can be merged into W0 for deployment so that inference has no additional latency relative to the corresponding fully fine-tuned weight path.

Reproducibility and limitations:

- The paper reports public code and checkpoints for several model families.
- The method is described as orthogonal to some prior efficient adaptation approaches.
- A stated limitation is that batching inputs for different tasks can be nontrivial when different samples require different LoRA modules.
- When no-latency deployment depends on merged LoRA weights, batching inputs from different tasks that require different LoRA modules is not straightforward; the paper notes dynamic module selection remains possible when latency is not critical.
- Section 7.1 and Table 5 analyze which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks.
- Section 7.2 and Table 6 analyze the effect of rank r on WikiSQL and MultiNLI in selected GPT-3 settings.
- Footnote 6 cautions that a small rank r should not be expected to work for every task or dataset.
- Relevant evidence locations: abstract; p. 3 Table 1; pp. 3-4 Section 4.1 no-additional-inference-latency discussion; p. 4 limitations paragraph before Section 5; Section 5 experiment setup; p. 6 Table 3; p. 7 Table 4; p. 9 Section 7.1/Table 5; p. 9 Section 7.2/Table 6; p. 10 footnote 6; appendices for implementation details.

