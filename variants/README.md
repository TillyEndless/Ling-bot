# Benchmark Variants

This directory describes the controlled variants to compare. It should not contain copied upstream repositories or final skill implementations at this stage.

## Variants

| Variant | Status | Description |
|---|---|---|
| `B0_base_agent` | Defined | Same model, same task input, same tool permissions, no research skill. |
| `B1_kdense_subset` | Defined | Targeted K-Dense subset for literature review, citation management, peer review, critical thinking, statistics, and writing. |
| `B2_orchestra_subset` | Defined | Targeted Orchestra subset for research state, ARA-style artifacts, rigor review, ideation, ML writing, and selected evaluation guidance. |
| `B3_your_v1_original` | Not implemented yet | The first independently designed `ai-ml-rl-research` skill, implemented only after this benchmark package is frozen. |
| `B4_your_v1_integrated` | Out of scope for this stage | The later integrated version created only after `B0`-`B3` results identify useful upstream components. |

## Controls

All variants must use:

- The same model and reasoning settings.
- The same task YAML.
- The same source packets.
- The same tool permissions.
- Fresh contexts or equivalent context resets.
- The same output storage layout.

Upstream repositories remain read-only baselines pinned in `upstream/manifest.yaml`.

## Prohibited in This Stage

- Do not implement `B3_your_v1_original` here.
- Do not create `B4_your_v1_integrated`.
- Do not copy upstream skill contents into this directory.
- Do not execute unreviewed upstream scripts.
- Do not use validation gold annotations while developing any skill.

