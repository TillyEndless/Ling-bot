# Validation Freeze Report

- Benchmark version: `validation_v0.1_agent_reviewed_internal`
- Split: `validation`
- Frozen tasks: 12
- Approval policy: `agent_review_sufficient_for_internal_validation`
- Reviewer: `codex_independent_reviewer`
- Gold status: agent-reviewed, not human-approved
- Fixed-source / equal-input condition: true
- No-dynamic-tools condition: true
- Generation inputs exclude validation gold, scoring rubric, and agent-review reports.
- `B4_your_v1_integrated` exists: false
- `B3_final_for_validation` is frozen for validation and must not be revised after validation results.

## Frozen Task Hashes

- `ERA-VAL-01`: task `6c3fbe31dc27`, packet `3971f83b133c`, gold `52c249debe70`, review `approved`
- `ERA-VAL-02`: task `da714a9cb13a`, packet `f22de88e98ce`, gold `f88e32c11eef`, review `approved`
- `LS-VAL-01`: task `76c93ed550ee`, packet `c983aaa0ff74`, gold `18a86db0d37b`, review `approved`
- `LS-VAL-02`: task `0a463f3a253b`, packet `e7da488e2a8a`, gold `f47ef597e518`, review `approved`
- `MC-VAL-01`: task `b489e63aa556`, packet `2a8127477cbe`, gold `5a0b66a9829b`, review `approved`
- `MC-VAL-02`: task `945b70633d5d`, packet `00dfb387438a`, gold `af976f0d0b63`, review `approved`
- `PS-VAL-01`: task `eb6eb27255be`, packet `639a3ded022f`, gold `d83b7b2180b3`, review `approved`
- `PS-VAL-02`: task `acd26e34e3e8`, packet `8f34e5e11bfa`, gold `381c37cad11f`, review `approved`
- `RL-VAL-01`: task `529c8dc5a3ef`, packet `f6feb751d0a1`, gold `0c503ea06515`, review `approved`
- `RL-VAL-02`: task `fe8a37d17f60`, packet `b34c16746a3b`, gold `9a0227f29875`, review `approved`
- `SPR-VAL-01`: task `dae4da6dff17`, packet `2ab84f36591a`, gold `8b309d8cb0b3`, review `approved`
- `SPR-VAL-02`: task `92156e8f42d0`, packet `d988cff44933`, gold `81765edce186`, review `approved`

## Variant Records

- `B0_base_agent`: No skill files; no variant manifest by design.
- `B1_kdense_subset`: manifest `variants/B1_kdense_subset/variant_manifest.yaml` (`33a7ba399a2b`), hash manifest `reports/round1_dev_v0_2/variant_hash_manifest.yaml` (`ed089053ce6a`)
- `B2_orchestra_subset`: manifest `variants/B2_orchestra_subset/variant_manifest.yaml` (`0e0cf9e85549`), hash manifest `reports/round1_dev_v0_2/variant_hash_manifest.yaml` (`ed089053ce6a`)
- `B3_final_for_validation`: manifest `variants/B3_final_for_validation/final_variant_manifest.yaml` (`a74af6878ec3`), hash manifest `reports/validation/B3_final_hash_manifest.yaml` (`b6d475e1e2fd`)

## Compatibility Rule

Validation results must only be compared against runs using this frozen validation manifest. Any later change to task YAMLs, packets, gold, rubric, run protocol, agent-review decision layer, or variant files requires a new validation benchmark version and rerun of all variants.
