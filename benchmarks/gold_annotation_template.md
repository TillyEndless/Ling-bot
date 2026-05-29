# Gold Annotation Template

Gold annotations are used for scoring. They must not be exposed to any variant during task execution, especially validation tasks.

Create one gold file per task after the required source packet is collected.

```yaml
task_id:
split:
annotator:
annotation_date:
source_packets:
  - packet_id:
    packet_version:
    files:
      - path:
        checksum:

canonical_facts:
  - fact_id:
    statement:
    source_location:
    importance: critical|major|minor

required_citations:
  - citation_id:
    expected_source:
    supports:
    source_location:

acceptable_outputs:
  required_sections:
    - name:
      criteria:
  optional_sections:
    - name:
      criteria:

common_errors:
  - error_id:
    description:
    severity: hard_fail|major|minor

scoring_guidance:
  factual_accuracy:
  evidence_traceability:
  citation_validity:
  literature_coverage:
  comparison_fairness:
  experimental_rigor:
  inference_boundary_discipline:
  rl_specific_correctness:
  output_usefulness:
  efficiency:

hard_fail_triggers:
  - trigger:
    evidence_required_to_apply:

notes:
```

For retrieval tasks, include canonical and acceptable paper sets without requiring one exact bibliography when the field is legitimately broad. For closed-source tasks, every critical fact must be grounded in the packet.

