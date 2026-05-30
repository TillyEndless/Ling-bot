# Method And Claim Audit

Adapted from Orchestra claim-centered artifact patterns and ML writing/reviewer criteria.

## Method Comparison Schema

| Dimension | Method A | Method B | Comparable? | Evidence | Caveat |
|---|---|---|---|---|---|

Recommended dimensions: objective, data, assumptions, model class, optimization, baselines, metrics, compute, evaluation protocol, limitations, and claim scope.

## Claim Ledger Schema

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|

## Boundary Rules

- A within-paper comparison supports that paper's setup, not all possible settings.
- A benchmark score supports performance under the benchmark protocol, not unrestricted capability.
- A probe or correlational analysis supports recoverability or association unless stronger causal evidence is supplied.
- A reproduction plan must list artifacts, code/config/data needs, seeds, metrics, and environment details.
