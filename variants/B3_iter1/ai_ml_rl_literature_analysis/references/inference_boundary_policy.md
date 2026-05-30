# Inference Boundary Policy

## Claim Classes

- Source fact: directly stated in supplied material; usually `DIRECT_PACKET_EVIDENCE`.
- Extracted observation: result or detail read from supplied evidence; usually `DIRECT_PACKET_EVIDENCE`.
- Cross-source synthesis: relation among supplied sources; usually `WITHIN_PACKET_SYNTHESIS`.
- Method background: general method context supplied by the packet; usually `METHOD_BACKGROUND`.
- Grounded critique: audit concern based on packet evidence but not directly stated by the source; usually `LIMITED_CRITIQUE`.
- Proposed hypothesis: new testable idea grounded in supplied evidence; usually `SPECULATIVE_PROPOSAL`.
- Speculation: plausible but not established by supplied material; usually `SPECULATIVE_PROPOSAL` or `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`.
- Unsupported claim: not justified by the packet; use `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`.

## Boundary Rules

- Mark unsupported synthesis explicitly.
- Use evidence-burden labels to distinguish direct evidence, synthesis, grounded critique, proposal, and unsupported claims. Prioritize labels for claims that affect conclusions, rankings, critique severity, or proposed hypotheses.
- Do not infer a field-wide literature gap from a small packet.
- Do not infer causality from correlation, probing, association, or representation recoverability alone.
- Do not infer mechanism from performance unless intervention or ablation evidence supports it.
- Do not infer deployment robustness from benchmark performance alone.
- Do not infer global superiority from setup-specific comparisons.
- Do not fill absent numbers, versions, metrics, seeds, or tables from memory.

## Proposal Rules

A useful proposal must state:

- a falsifiable hypothesis;
- observable outcomes that would support it;
- observations that would count against it;
- controls and baselines;
- feasibility and reproducibility requirements;
- the evidence still needed before making stronger claims.
