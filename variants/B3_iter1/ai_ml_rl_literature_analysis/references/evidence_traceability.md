# Evidence Traceability

## Claim-Evidence Ledger

Use a ledger whenever the task has more than one substantive claim.

| Claim | Claim type | Evidence-burden label | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|---|

Claim types include method definition, assumption, empirical result, benchmark result, comparison, limitation, mechanism claim, causal claim, reproducibility claim, and proposal hypothesis.

## Evidence-Burden Labels

Use these labels to make provenance and uncertainty visible:

- `DIRECT_PACKET_EVIDENCE`: directly stated in the provided source packet.
- `WITHIN_PACKET_SYNTHESIS`: synthesized from multiple packet-provided sources.
- `METHOD_BACKGROUND`: general method context from the provided materials.
- `LIMITED_CRITIQUE`: critique grounded in packet evidence but not directly stated by the source.
- `SPECULATIVE_PROPOSAL`: proposed hypothesis or future work, explicitly not established fact.
- `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`: claim requiring literature search or external evidence beyond the packet.

Prefer the narrowest label that fits. A claim may be useful even when it is not direct evidence, but its burden must be visible. Use labels for substantive claims, ledger rows, and major proposal hypotheses; do not add repetitive labels to every sentence when a nearby table or bullet already carries the burden.

## Source Location Granularity

Use the most precise available location:

1. page plus section/table/figure/appendix;
2. section/table/figure/appendix without page;
3. source note or excerpt name;
4. source-level citation only when no finer location is supplied.

If the packet supplies exact locations, use them. If it does not, state that the packet does not provide finer grounding.

## Evidence Directness

- Direct: the source explicitly states the claim.
- Indirect: the claim follows from supplied details but is not directly stated.
- Partial: evidence supports only part of the claim.
- Comparative: evidence supports a relation between methods under a specific setup.
- Absent: the packet does not establish the claim.

## Citation Hygiene

Do not invent missing metadata. Do not cite absent papers. Do not use external memory as evidence. A citation is valid only if the supplied source supports the statement being made.
