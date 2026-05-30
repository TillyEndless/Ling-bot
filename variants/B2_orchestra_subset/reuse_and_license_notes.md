# B2 Reuse And License Notes

This variant selectively adapts Orchestra-derived ideas for claim-centered artifacts, provenance, rigor review, and evaluation reasoning. It deliberately excludes autonomous experiment execution, repository management, evaluation harnesses, training infrastructure, deployment, and tool loops.

## Components Used

| Upstream component | Files consulted per ledger | Adaptation decision | License status from audit |
|---|---|---|---|
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/ara-compiler` | `SKILL.md`, `references/schema.md` | Rewritten as compact claim/evidence/artifact schema | MIT observed in skill frontmatter |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/research-manager` | `SKILL.md`, `references/provenance_tags.md` | Rewritten as provenance tags and artifact discipline | MIT observed in skill frontmatter |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/rigor-reviewer` | `SKILL.md`, `references/rigor_dimensions.md` | Rewritten as type-aware rigor review workflow | MIT observed in skill frontmatter |
| `Orchestra-Research/AI-Research-SKILLs/20-ml-paper-writing/ml-paper-writing` | `SKILL.md`, citation/reviewer references | Rewritten as claim-to-evidence and reviewer criteria patterns | MIT observed in skill frontmatter |

## Explicit Runtime Exclusions

- No autonomous research loop or persistent research state.
- No scripts, APIs, retrieval tools, evaluation harnesses, training infrastructure, or code execution.
- No K-Dense-derived material.
- No benchmark-specific paper names, task identifiers, expected answers, or development answer-key content.
