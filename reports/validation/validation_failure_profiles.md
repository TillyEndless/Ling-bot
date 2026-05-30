# Validation Failure Profiles

## B0_base_agent

- Overall mean: 3.915
- Hard fails: 0

Lower-scoring dimensions:
- `factual_accuracy`: 3.75
- `evidence_traceability`: 3.25
- `citation_validity`: 3.857
- `literature_coverage`: 4
- `comparison_fairness`: 3.9
- `experimental_rigor`: 3.909
- `benchmark_validity`: 3.889
- `inference_boundary_discipline`: 4.167
- `hypothesis_quality`: 4
- `rl_specific_correctness`: 3.833
- `output_usefulness`: 4.083

Representative notes:
- `SPR-VAL-01` (3.1): Cautious and mostly safe, but too skeletal for a deep-reading task. It avoids hallucinating and marks many missing details unknown, yet misses the required substantive DreamerV3 objective, policy-learning setup, domains, metrics, baselines, and limitations.
- `SPR-VAL-02` (3.3): Cautious and RL-aware, but substantially incomplete. It captures the high-level return-conditioned sequence-modeling framing and avoids overclaiming, yet fails the deep-reading requirement by not extracting actual experimental and reproducibility details.
- `MC-VAL-01` (3.78): Strongly scoped and avoids unfair superiority claims, but materially misses the required PPO on-policy distinction, reducing RL-specific correctness and factual accuracy.

## B1_kdense_subset

- Overall mean: 4.158
- Hard fails: 0

Lower-scoring dimensions:
- `factual_accuracy`: 3.75
- `evidence_traceability`: 3.75
- `citation_validity`: 3.857
- `comparison_fairness`: 4
- `experimental_rigor`: 4.091
- `benchmark_validity`: 3.889
- `rl_specific_correctness`: 3.833
- `output_usefulness`: 4.25

Representative notes:
- `SPR-VAL-01` (3.1): A compact, disciplined answer that avoids overclaiming, but it is under-informative for the benchmark. It is useful as a missing-evidence audit, not as the requested structured deep reading of the Dreamer-style paper.
- `SPR-VAL-02` (3.3): Stronger organization than B0 and good boundary discipline, but it remains a generic cautious template. It captures the central formulation but misses the actual empirical content that the task asked to extract.
- `MC-VAL-01` (3.78): Clear and fair closed-source comparison with strong boundary discipline, but it misses the high-weight PPO on-policy fact and remains only moderately traceable.

## B2_orchestra_subset

- Overall mean: 4.257
- Hard fails: 0

Lower-scoring dimensions:
- `factual_accuracy`: 4
- `evidence_traceability`: 3.667
- `citation_validity`: 3.857
- `experimental_rigor`: 4.273
- `benchmark_validity`: 4.222
- `rl_specific_correctness`: 4

Representative notes:
- `SPR-VAL-01` (3.3): The strongest of the incomplete subset-style answers. It gives useful calibrated critique and comparison-fairness warnings, but it remains far below an expert paper card because it lacks the actual DreamerV3 objective, domains, metrics, baselines, and limitations.
- `SPR-VAL-02` (3.3): A careful but under-informative answer. It is useful as an evidence-boundary checklist, not as a deep reading of the Decision Transformer packet.
- `ERA-VAL-01` (4.0): B2 is a strong audit that captures the central benchmark-contamination skepticism and gives a solid corrected protocol. It handles baselines, metrics, uncertainty, prompt protocol, leakage, and claim scope well. It remains within the closed-source boundary.

## B3_final_for_validation

- Overall mean: 4.437
- Hard fails: 0

Lower-scoring dimensions:
- `factual_accuracy`: 4.083
- `citation_validity`: 3.875
- `rl_specific_correctness`: 4.167
- `efficiency`: 4.083

Representative notes:
- `SPR-VAL-02` (3.5): Best-calibrated of the four on inference boundaries and evidence labeling, but still not a successful deep reading because it mostly inventories missing information rather than extracting the paper’s concrete experimental content.
- `SPR-VAL-01` (3.6): Best calibrated variant. It is highly disciplined about inference boundaries and explicitly distinguishes packet evidence from critique, but it remains substantively incomplete for the requested deep read because the key DreamerV3 experimental and method facts are absent.
- `MC-VAL-01` (4.2): Very usable and disciplined artifact with explicit evidence-burden labels and strong recommendations, but it still weakens the required PPO on-policy fact enough to lose factual and RL-specific credit.

