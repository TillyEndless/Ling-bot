# Variant Implementation Audit

## Scope

Implemented three instruction/reference-only variants for `literature_analysis_and_research_rigor`:

- `B1_kdense_subset`: K-Dense-derived literature review, evidence/citation handling, scientific criticism, and hypothesis scaffolding.
- `B2_orchestra_subset`: Orchestra-derived claim/provenance artifacts, rigor review, method audit, and evaluation reasoning.
- `B3_your_v1_original`: original AI/ML/RL-focused literature analysis and research-rigor skill.

## Runtime Exclusions

All variants explicitly exclude dynamic retrieval, external APIs, citation services, PDF parsers, executable scripts, experiment execution, training infrastructure, repository management, persistent research state, and Research OS orchestration.

## Static Contamination Scan

Scan targets included dev task IDs, frozen benchmark paper names/acronyms, benchmark-version strings, answer-key references, and rubric/hard-fail language.

No contamination hits remain after sanitization.

## Fairness Confirmation

- Variant directories do not contain frozen task IDs or benchmark-specific paper names.
- Variant directories do not contain answer-key files, scoring rubrics, B0 outputs, benchmark audit reports, validation tasks, private-test materials, or upstream repositories.
- Each variant is intended to run from a clean execution package containing only that variant, frozen prompts, frozen source packets, and empty output directories.

## File Hashes

See `variant_hash_manifest.yaml` for SHA-256 hashes of every variant file.
