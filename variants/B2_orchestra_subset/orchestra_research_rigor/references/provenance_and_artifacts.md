# Provenance And Research Artifacts

Adapted from Orchestra agent-native research artifact and research-manager patterns.

## Provenance Tags

Use these tags internally and expose them when helpful:

- source-derived: directly stated by supplied material.
- source-located: source-derived and tied to page, section, figure, or table.
- cross-source synthesis: a relation among supplied sources.
- agent-inferred: inferred from supplied evidence and marked as such.
- agent-proposed: a hypothesis, critique, or protocol improvement.
- unsupported: not established by supplied material.

## Artifact Schema

| Artifact | Purpose |
|---|---|
| Claim ledger | Tracks claims, claim types, source support, and scope. |
| Evidence ledger | Tracks source locations and directness of support. |
| Assumption list | Separates method assumptions from evaluation assumptions. |
| Risk register | Records threats to validity and reproducibility. |
| Missing-information list | Identifies details needed before stronger conclusions. |

Never silently convert an agent-proposed idea into a source-derived fact.
