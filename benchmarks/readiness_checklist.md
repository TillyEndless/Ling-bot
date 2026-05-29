# Benchmark Readiness Checklist

Use this checklist before any Round 1 development run.

## Round 1 Design

- [x] All Round 1 tasks are `closed_source`.
- [x] Literature tasks are fixed-corpus literature mapping tasks, not open retrieval tasks.
- [x] Retrieval-enabled testing is deferred to `benchmarks/future_rounds/retrieval_enabled_evaluation.md`.
- [x] The split policy has been adopted.
- [x] The private-test protocol has been adopted.
- [x] The 12 non-dev tasks have been reclassified as validation tasks.
- [ ] No `B1`, `B2`, `B3`, or `B4` variant implementation has begun before the benchmark freeze.

## Development Assets

- [x] Six dev task YAML files are present.
- [x] Each dev task has a concrete source packet ID.
- [x] Each dev task specifies required papers, sections, tables, appendices, or metadata.
- [x] `benchmarks/source_packets/dev/source_acquisition_manifest.yaml` is complete.
- [x] All six dev source packets are acquired.
- [x] All six dev source packet manifests include provenance.
- [x] All six dev source packet manifests include checksums.
- [x] All six dev source packet license/access notes are recorded.
- [x] All six dev gold annotations are grounded in candidate source locations.
- [ ] All six dev gold annotations are human-reviewed.
- [ ] All six dev gold annotations are marked `eligible_for_scoring: true`.

## Variant Controls

- [ ] `B0_base_agent` run instructions are defined.
- [ ] `B1_kdense_subset` skill subset is frozen before execution.
- [ ] `B2_orchestra_subset` skill subset is frozen before execution.
- [ ] `B3_your_v1_original` is implemented only after benchmark assets are frozen.
- [ ] No `B4_your_v1_integrated` implementation exists yet.
- [x] Upstream repos are pinned in `upstream/manifest.yaml`.
- [x] Upstream repos are treated as read-only.

## Execution Controls

- [ ] Same model and reasoning settings are selected for all variants.
- [ ] Same tool permissions are selected for all variants.
- [ ] Fixed source packets are identical across variants.
- [ ] Unreviewed upstream scripts are disabled.
- [x] External APIs and citation databases are disabled.
- [x] Open retrieval is disabled.
- [x] Autonomous experiment execution is disabled.
- [ ] Fresh contexts or equivalent resets are used between runs.

## Leakage Controls

- [ ] Validation source packets are outside the development workspace or access-controlled.
- [ ] Validation gold annotations are outside the development workspace or access-controlled.
- [ ] Validation scorecards are not used to tune prompts or references.
- [ ] Source packets are identical across variants.
- [ ] Run metadata records loaded skills and source materials.
- [ ] Variant commits or file hashes are frozen before validation execution.

## Scoring Controls

- [ ] Scoring rubric is frozen.
- [ ] Scorecard format is frozen.
- [ ] Hard-fail rules are agreed before runs.
- [ ] At least one reviewer is assigned.
- [ ] Repeated-run policy is set for validation tasks.

## Current Blocking Status

Do not run `B0_base_agent` yet. The remaining blocker is human review of all six agent-drafted dev gold annotations and setting each to `eligible_for_scoring: true`.
