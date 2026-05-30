# Validation Review Decision Prefill

This is a prefill recommendation only. It does not approve benchmark gold, does not change any gold annotation file, and does not make any task eligible for scoring.

## Per-Task Prefill

```yaml
- task_id: ERA-VAL-01
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [ERA-VAL-01-M1, ERA-VAL-01-M2, ERA-VAL-01-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: ERA-VAL-02
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [ERA-VAL-02-M1, ERA-VAL-02-M2, ERA-VAL-02-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: LS-VAL-01
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [LS-VAL-01-M1, LS-VAL-01-M2, LS-VAL-01-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: LS-VAL-02
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: LS-VAL-02-M3
      required_change: Verify source support or revise packet/gold anchor if evidence is insufficient.
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [LS-VAL-02-M1, LS-VAL-02-M2]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: MC-VAL-01
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [MC-VAL-01-M1, MC-VAL-01-M2, MC-VAL-01-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: MC-VAL-02
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [MC-VAL-02-M1, MC-VAL-02-M2, MC-VAL-02-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: PS-VAL-01
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [PS-VAL-01-M1, PS-VAL-01-M2, PS-VAL-01-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: PS-VAL-02
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: PS-VAL-02-M3
      required_change: Verify source support or revise packet/gold anchor if evidence is insufficient.
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [PS-VAL-02-M1, PS-VAL-02-M2]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: RL-VAL-01
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [RL-VAL-01-M1, RL-VAL-01-M2, RL-VAL-01-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: RL-VAL-02
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [RL-VAL-02-M1, RL-VAL-02-M2, RL-VAL-02-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: SPR-VAL-01
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [SPR-VAL-01-M1, SPR-VAL-01-M2, SPR-VAL-01-M3]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

- task_id: SPR-VAL-02
  recommended_human_review_status: human_source_check_required
  eligible_for_scoring_after_human_confirmation: true
  approved_items_candidate: []
  revisions_required_candidate:
    - item_id: SPR-VAL-02-M3
      required_change: Verify source support or revise packet/gold anchor if evidence is insufficient.
    - item_id: E1
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: E2
      required_change: Confirm penalty applies only to core claims and is not too broad.
    - item_id: B1
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B2
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
    - item_id: B3
      required_change: Confirm boundary rule allows harmless background context and does not over-penalize scoped caveats.
  manual_source_check_required: [SPR-VAL-02-M1, SPR-VAL-02-M2]
  rationale: High-priority anchors are plausible but require manual source inspection for exact page/section/table/figure support.

validation_gold_review_overall:
  approved_candidate_tasks: []
  human_source_check_required_tasks: [ERA-VAL-01, ERA-VAL-02, LS-VAL-01, LS-VAL-02, MC-VAL-01, MC-VAL-02, PS-VAL-01, PS-VAL-02,
  RL-VAL-01, RL-VAL-02, SPR-VAL-01, SPR-VAL-02]
  revisions_required_candidate_tasks: []
  ready_for_validation_freeze: false
```

## Summary

### Tasks Likely Approvable Quickly

- None before source-location verification.

### Tasks Needing Human Source Checks

- `ERA-VAL-01`
- `ERA-VAL-02`
- `LS-VAL-01`
- `LS-VAL-02`
- `MC-VAL-01`
- `MC-VAL-02`
- `PS-VAL-01`
- `PS-VAL-02`
- `RL-VAL-01`
- `RL-VAL-02`
- `SPR-VAL-01`
- `SPR-VAL-02`

### Tasks Likely Needing Gold Revision

- None clearly indicated by the workbook alone; source checks may still reveal revision needs.

### Freeze Status

Validation freeze is blocked until human source checks are completed and real gold files are explicitly approved in a later step.