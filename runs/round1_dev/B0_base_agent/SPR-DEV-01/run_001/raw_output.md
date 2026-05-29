## paper_card

```yaml
paper_card:
  title: "LoRA: Low-Rank Adaptation of Large Language Models"
  arxiv_id: "2106.09685"
  source_type: "26-page arXiv PDF"
  method_name: "Low-Rank Adaptation (LoRA)"
  core_idea: >
    Freeze pretrained model weights and add trainable rank-decomposition matrices
    to selected dense weight matrices, representing the adapted weight as the
    frozen pretrained weight plus a low-rank update, commonly W0 + BA.
  motivation_or_hypothesis: >
    The method is connected to the hypothesis that adaptation updates have low
    intrinsic rank.
  evaluated_model_families:
    - RoBERTa
    - DeBERTa
    - GPT-2
    - GPT-3
  key_evidence_locations:
    method:
      - abstract
      - Section 1
      - Section 4
      - Figure 1
    experiments:
      - Section 5
      - Table 1
      - Table 2
    reproducibility:
      - Section 5 experiment setup
      - appendices for implementation details
  source_packet_scope: >
    This card uses only the frozen model input packet. Details not present in
    the packet are marked unknown.
```

## claim_ledger

```yaml
claim_ledger:
  - id: C1
    claim: >
      LoRA adapts large language models by freezing pretrained weights and adding
      trainable low-rank update matrices to selected dense weight matrices.
    status: supported_by_packet
    evidence_ids: [E1, E2]
    distinction: method

  - id: C2
    claim: >
      The adapted weight is represented as the frozen pretrained weight plus a
      low-rank update, commonly written W0 + BA.
    status: supported_by_packet
    evidence_ids: [E1]
    distinction: method

  - id: C3
    claim: >
      LoRA is motivated by or connected to the hypothesis that adaptation updates
      have low intrinsic rank.
    status: supported_by_packet
    evidence_ids: [E3]
    distinction: motivation

  - id: C4
    claim: >
      In the GPT-3 175B adaptation setting, the abstract reports reductions in
      trainable parameters and GPU memory.
    status: supported_by_packet
    evidence_ids: [E4]
    distinction: trainable_parameter_reduction_and_gpu_memory_reduction

  - id: C5
    claim: >
      The abstract reports that LoRA performs on par with or better than full
      fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in the paper's evaluated
      settings.
    status: supported_by_packet
    evidence_ids: [E5]
    distinction: task_quality
    caution: >
      This does not support a universal claim that LoRA is always better than
      full fine-tuning.

  - id: C6
    claim: >
      Section 5 evaluates downstream task performance on RoBERTa, DeBERTa,
      GPT-2, and GPT-3.
    status: supported_by_packet
    evidence_ids: [E6]
    distinction: task_quality

  - id: C7
    claim: >
      Table 1 compares inference latency of adapter-style methods and LoRA/full
      fine-tuning in a GPT-2 medium setup.
    status: supported_by_packet
    evidence_ids: [E7]
    distinction: inference_latency

  - id: C8
    claim: >
      Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods.
    status: supported_by_packet
    evidence_ids: [E8]
    distinction: task_quality

  - id: C9
    claim: >
      The paper reports public code and checkpoints for several model families.
    status: supported_by_packet
    evidence_ids: [E9]
    distinction: reproducibility

  - id: C10
    claim: >
      LoRA is orthogonal to some prior efficient adaptation approaches.
    status: supported_by_packet
    evidence_ids: [E10]
    distinction: method_relation
    caution: >
      The packet says this does not prove compatibility in every later setting.

  - id: C11
    claim: >
      A stated limitation is that batching inputs for different tasks can be
      nontrivial when different samples require different LoRA modules.
    status: supported_by_packet
    evidence_ids: [E11]
    distinction: limitation

  - id: C12
    claim: >
      Exact ranks, hyperparameters, datasets, metric values, code URLs, and
      checkpoint locations are available from the packet.
    status: unsupported_by_packet
    evidence_ids: []
    distinction: missing_detail
    note: unknown
```

## evidence_ledger

```yaml
evidence_ledger:
  - id: E1
    source_location: "Controlled Source Notes: Core method"
    packet_content: >
      The paper proposes LoRA, freezes pretrained weights, adds trainable
      rank-decomposition matrices, and expresses adapted weights as W0 + BA.
    supports_claims: [C1, C2]

  - id: E2
    source_location: "Relevant evidence locations: abstract; Section 1; Section 4; Figure 1"
    packet_content: >
      The packet identifies these locations as evidence for the core method.
    supports_claims: [C1]

  - id: E3
    source_location: "Controlled Source Notes: Core method"
    packet_content: >
      The paper connects LoRA to the hypothesis that adaptation updates have low
      intrinsic rank.
    supports_claims: [C3]

  - id: E4
    source_location: "Controlled Source Notes: Claims and evidence"
    packet_content: >
      The abstract reports reductions in trainable parameters and GPU memory in
      the GPT-3 175B adaptation setting.
    supports_claims: [C4]

  - id: E5
    source_location: "Controlled Source Notes: Claims and evidence"
    packet_content: >
      The abstract says LoRA performs on par or better than full fine-tuning on
      RoBERTa, DeBERTa, GPT-2, and GPT-3 in the evaluated settings.
    supports_claims: [C5]

  - id: E6
    source_location: "Controlled Source Notes: Claims and evidence"
    packet_content: >
      Section 5 evaluates downstream task performance on RoBERTa, DeBERTa,
      GPT-2, and GPT-3.
    supports_claims: [C6]

  - id: E7
    source_location: "Controlled Source Notes: Claims and evidence"
    packet_content: >
      Table 1 compares inference latency of adapter-style methods and LoRA/full
      fine-tuning in a GPT-2 medium setup.
    supports_claims: [C7]

  - id: E8
    source_location: "Controlled Source Notes: Claims and evidence"
    packet_content: >
      Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods.
    supports_claims: [C8]

  - id: E9
    source_location: "Controlled Source Notes: Reproducibility and limitations"
    packet_content: >
      The paper reports public code and checkpoints for several model families.
    supports_claims: [C9]

  - id: E10
    source_location: "Controlled Source Notes: Reproducibility and limitations"
    packet_content: >
      The method is described as orthogonal to some prior efficient adaptation
      approaches, but this does not prove compatibility in every later setting.
    supports_claims: [C10]

  - id: E11
    source_location: "Controlled Source Notes: Reproducibility and limitations"
    packet_content: >
      A stated limitation is that batching inputs for different tasks can be
      nontrivial when different samples require different LoRA modules.
    supports_claims: [C11]
```

## reproducibility_notes

```yaml
reproducibility_notes:
  source_restriction: >
    Only the frozen packet was used. No external retrieval, citation database,
    API, script, or prior outside knowledge was used as evidence.
  code_and_checkpoints: >
    The packet says the paper reports public code and checkpoints for several
    model families.
  implementation_details: >
    The packet points to appendices for implementation details, but does not
    provide the details themselves.
  experiment_setup: >
    The packet identifies Section 5 as containing the experiment setup.
  evaluated_models:
    - RoBERTa
    - DeBERTa
    - GPT-2
    - GPT-3
  reported_comparison_types:
    trainable_parameters: >
      Reductions reported in the abstract for GPT-3 175B adaptation.
    gpu_memory: >
      Reductions reported in the abstract for GPT-3 175B adaptation.
    inference_latency: >
      Table 1 compares adapter-style methods and LoRA/full fine-tuning in a
      GPT-2 medium setup.
    task_quality: >
      Section 5 evaluates downstream tasks; Table 2 reports GLUE results for
      RoBERTa/DeBERTa adaptation methods.
  missing_from_packet:
    - exact trainable-parameter reduction values
    - exact GPU memory reduction values
    - exact inference latency numbers
    - exact GLUE scores
    - exact task list
    - rank values used in experiments
    - optimizer settings
    - learning rates
    - batch sizes
    - training compute
    - random seeds
    - code URL
    - checkpoint URLs
```

## limitations_and_open_questions

```yaml
limitations_and_open_questions:
  limitations_supported_by_packet:
    - >
      Batching inputs for different tasks can be nontrivial when different
      samples require different LoRA modules.
    - >
      The packet supports claims about evaluated settings only; it does not
      support claiming LoRA is universally better than full fine-tuning.
    - >
      Orthogonality to some prior efficient adaptation approaches does not prove
      compatibility in every later setting.

  open_questions_due_to_missing_packet_detail:
    - What exact parameter and memory reductions were reported?
    - What exact latency results were shown in Table 1?
    - What exact GLUE scores were reported in Table 2?
    - Which dense weight matrices were selected in each experiment?
    - What ranks were used?
    - What training hyperparameters were used?
    - Which public code and checkpoint locations were reported?
    - How robust were results across seeds or task variants?

  unsupported_or_unknown:
    universal_superiority_over_full_fine_tuning: unknown
    exact_numeric_results: unknown
    later_real_world_adoption_or_compatibility: unknown
    implementation_hyperparameters: unknown
```