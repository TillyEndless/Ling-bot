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
