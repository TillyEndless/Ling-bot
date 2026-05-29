# ERA-DEV-01 Human Review Log

## Review Decision

- `task_id`: `ERA-DEV-01`
- `review_status`: `approved_with_minor_notes`
- `eligible_for_scoring`: `true`
- `review_basis`: Human review instructions supplied for the pinned AgentBench packet.

## Version Verification

The local canonical PDF was verified against the pinned task version before approving scoring:

- `AgentBench: Evaluating LLMs as Agents`
- Local first page reports `Published as a conference paper at ICLR 2024`.
- Local first page reports `arXiv:2308.03688v3 [cs.AI] 4 Oct 2025`.
- Local abstract reports evaluation of `29 API-based and open-sourced (OSS) LLMs`.

Because the local PDF matches the pinned 29-model ICLR 2024 / arXiv v3 version, the revised page, table, model-count, and scoring references are eligible for use after the requested annotation edits.

## Applied Corrections

- Replaced `ERA1` with the eight-environment, code/game/web-grounded benchmark framing.
- Replaced `ERA2` with the pinned-version 29-model evaluation statement and added an explicit version condition.
- Replaced `ERA3` with the heterogeneous-metrics and weighted-overall-score finding.
- Moved the former benchmark-validity audit item into `benchmark_audit_requirements`.
- Added `ERA5` for execution-outcome categories and the paper's aggregate failure-outcome interpretation.
- Replaced `ERA-E1`, `ERA-E2`, and `ERA-E3`, and added `ERA-E4` for pinned-version model-count and score interpretation errors.
- Added the graded outside-corpus policy.
- Replaced `inference_boundary_requirements` with version-aware benchmark-construction, metric, result, interpretation, and audit-risk boundaries.
- Replaced `optional_high_value_findings` with audit-oriented validity, aggregation, robustness, and outcome-analysis findings.

## Remaining Minor Notes

- Scoring should enforce the pinned 29-model version when judging model counts, roster claims, and score interpretation.
- Responses should not treat contamination, prompt leakage, prompt sensitivity, environment-isolation failures, or protocol bias as established unless directly evidenced by the fixed packet.
- Proposed follow-up audits are allowed, but they must be labeled as audit risks or future checks rather than paper-established failures.
