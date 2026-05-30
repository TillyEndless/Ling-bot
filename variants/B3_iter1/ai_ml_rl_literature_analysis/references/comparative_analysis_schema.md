# Comparative Analysis Schema

## Method Comparison Matrix

| Dimension | Method or source A | Method or source B | Comparable as stated? | Evidence-burden label | Evidence | Boundary |
|---|---|---|---|---|---|---|

Recommended dimensions:

- objective;
- input data and supervision;
- optimization procedure;
- model or policy class;
- assumptions;
- baselines;
- datasets, environments, or tasks;
- metrics;
- compute or hardware when available;
- ablations;
- limitations and failure modes.

## Fairness Rules

- Compare within the same experimental setup when possible.
- If comparisons cross papers, state differences in data, model size, metrics, training budget, implementation, and evaluation protocol.
- A method can be better in a reported setup without being universally better.
- A result from one domain does not automatically transfer to another domain.
- If a source is an algorithmic foundation rather than a direct comparison, use it for mechanism/objective explanation, not direct empirical ranking.
- Label setup-specific comparisons as direct evidence only for the reported setup.
- Label cross-paper relations as synthesis unless the packet contains a direct shared evaluation.
- In matrices, one evidence-burden label per row is usually enough; avoid duplicating the same label again in adjacent prose unless the claim changes.

## Output Checks

- Have all methods/sources been represented fairly?
- Are assumptions visible?
- Are incompatible protocols called out?
- Are claims limited to supported settings?
- Are unsupported ranking or transfer claims explicitly marked as needing external review?
