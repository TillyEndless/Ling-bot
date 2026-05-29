# Controlled Run Protocol

This protocol governs Round 1 comparison of instruction/reference-based research skill variants. Round 1 uses fixed source packets only.

No open retrieval, dynamic external APIs, citation databases, PDF-parser integrations, autonomous experiment execution, or unreviewed upstream scripts are allowed at runtime.

## Round 1 Variants

Run the first comparison on:

- `B0_base_agent`
- `B1_kdense_subset`
- `B2_orchestra_subset`
- `B3_your_v1_original`

Do not implement or run `B4_your_v1_integrated` until after `B0`-`B3` results are analyzed.

## Round 1 Evaluation Mode

All Round 1 tasks are `closed_source`.

The agent receives:

- The task YAML.
- The fixed source packet for that task.
- The common scoring rubric only if the run design allows rubric-visible evaluation.

The agent does not receive:

- Dev or validation gold annotations.
- Validation source packets during development.
- External retrieval.
- Citation lookup services.
- Any tool output not supplied in the frozen packet.

## Environment Controls

For each task and variant:

- Use the same model.
- Use the same reasoning settings.
- Use the same agent environment.
- Use the same task YAML.
- Use the same source packet files and checksums.
- Use the same tool permissions.
- Use fresh contexts or equivalent context resets.
- Disable unreviewed upstream scripts.
- Disable external APIs and citation databases.
- Disable autonomous experiment execution.

## Source Packet Controls

Every Round 1 run requires a source packet with:

- Packet ID.
- Packet manifest.
- File checksums.
- Source provenance.
- Version metadata.
- License/access notes.
- Stable filenames.

If the source packet is missing or unchecksummed, the task is not executable.

## Literature Mapping Controls

Literature tasks in Round 1 are fixed-corpus literature mapping tasks, not open-ended retrieval tasks.

Coverage means:

- Accounting for every supplied corpus item.
- Correctly identifying core, supporting, background, or out-of-scope papers within the packet.
- Correctly distinguishing research lines represented in the packet.
- Mapping method differences, evidence types, and limits from packet evidence.
- Flagging synthesis that would require evidence outside the packet.

Coverage does not mean:

- Discovering additional papers.
- Rewarding broader bibliographies.
- Using remembered canonical papers not present in the packet.

## Repeated Runs

Use repeated runs where stochastic variation matters.

Recommended minimum:

- Dev split: one run per variant for debugging, with repeats for unstable tasks.
- Validation split: three runs per variant-task pair for formal comparison if resources permit.

All repeated runs must use fresh contexts and the same source packets.

## Output Storage

Store outputs under:

```text
runs/
  raw_outputs/
    <variant>/<task_id>/<run_id>.md
  run_metadata/
    <variant>/<task_id>/<run_id>.yaml
  scorecards/
    <variant>/<task_id>/<run_id>.yaml
```

The `runs/.gitkeep` placeholder exists now; run outputs should be generated later.

## Run Metadata

Each run metadata file should include:

```yaml
run_id:
variant:
task_id:
split:
model:
reasoning_settings:
date:
operator:
variant_commit_or_hash:
skills_loaded:
task_yaml:
source_packets:
  - packet_id:
    packet_manifest:
    packet_checksum:
tool_permissions:
retrieval_allowed: false
scripts_allowed: false
external_apis_allowed: false
citation_databases_allowed: false
autonomous_experiment_execution_allowed: false
token_usage:
wall_clock_seconds:
tool_calls:
output_file:
known_failures:
```

## Split Protection

Follow `benchmarks/split_policy.md` and `benchmarks/private_test_protocol.md`.

Minimum rules:

- Validation source packets and gold annotations must not be accessible during skill development.
- Do not tune `B3_your_v1_original` against validation tasks, packets, gold annotations, or scorecards.
- Before validation execution, freeze variant commits or file hashes.
- Do not modify validation task shells after formal runs begin unless the benchmark version is incremented and all variants are rerun.
- Keep source packets identical across variants.
- Private-test artifacts must not be created or stored in this development workspace.

## Scoring Process

1. Confirm task source packet availability and checksums.
2. Confirm gold annotation status is source-grounded and human-reviewed.
3. Run the variant under this protocol.
4. Save raw output and metadata.
5. Score using `benchmarks/rubrics/scoring_rubric.md`.
6. Apply hard-fail flags before interpretive summaries.
7. Compare variants per dimension and task family, not only by average score.

## Deferred Retrieval Evaluation

Open retrieval belongs to a future evaluation round, described in `benchmarks/future_rounds/retrieval_enabled_evaluation.md`.
