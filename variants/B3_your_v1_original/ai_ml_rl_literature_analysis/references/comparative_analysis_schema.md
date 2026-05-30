# Comparative Analysis Schema

## Method Comparison Matrix

| Dimension | Method or source A | Method or source B | Comparable as stated? | Evidence | Boundary |
|---|---|---|---|---|---|

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

## Output Checks

- Have all methods/sources been represented fairly?
- Are assumptions visible?
- Are incompatible protocols called out?
- Are claims limited to supported settings?
