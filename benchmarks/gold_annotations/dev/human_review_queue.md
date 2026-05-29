# 开发集“黄金标准”标注的人工审核队列

所有的开发集“黄金标准”（Gold）标注均由代理（Agent）自动生成草稿，必须经过人工审核后方可进行评分。在审核完成之前，每个文件的状态将保持为 `eligible_for_scoring: false`（暂不具备评分资格）。

## LS-DEV-01

需打开的源文件：

- `benchmarks/source_packets/dev/LS-DEV-01/canonical_sources/efficient_transformers_survey_arxiv_2009.06732.pdf`
- `benchmarks/source_packets/dev/LS-DEV-01/canonical_sources/linformer_arxiv_2006.04768.pdf`
- `benchmarks/source_packets/dev/LS-DEV-01/canonical_sources/longformer_arxiv_2004.05150.pdf`
- `benchmarks/source_packets/dev/LS-DEV-01/canonical_sources/flashattention_arxiv_2205.14135.pdf`
- `benchmarks/source_packets/dev/LS-DEV-01/canonical_sources/lora_arxiv_2106.09685.pdf`

审核重点：

- 验证每个“方法族”（method-family）标签是否准确无误。
- 验证关于 Efficient Transformers 和 FlashAttention 的页面及表格引用是否正确。
- 确认 LoRA 应当被归类为“适应性效率”（adaptation efficiency），而非“注意力效率”（attention efficiency）。
- 确认在“固定语料库映射”（fixed-corpus mapping）任务中，引用语料库以外的论文应如何进行扣分处罚。

## SPR-DEV-01

需打开的源文件：

- `benchmarks/source_packets/dev/SPR-DEV-01/canonical_sources/lora_arxiv_2106.09685.pdf`

审核重点：

- 验证关于“低秩适应”（low-rank adaptation）机制的措辞是否准确。
- 验证关于方法描述、实验部分、表1、表2、消融实验（ablations）以及局限性段落的具体位置标注是否精确。
- 确认该“黄金标准”是否应当要求包含针对 GPT-3 特定的内存/吞吐量详细数据。
- 确认针对后续 LoRA 生态系统相关事实的“严重错误”（critical-error）判定阈值。 ## MC-DEV-01

需查阅的源文件：

- `benchmarks/source_packets/dev/MC-DEV-01/canonical_sources/dpo_arxiv_2305.18290.pdf`
- `benchmarks/source_packets/dev/MC-DEV-01/canonical_sources/instructgpt_arxiv_2203.02155.pdf`
- `benchmarks/source_packets/dev/MC-DEV-01/canonical_sources/ppo_arxiv_1707.06347.pdf`

审查重点：

- 核实 DPO 目标函数以及 Bradley-Terry/KL 框架的对应位置。
- 核实 InstructGPT/RLHF 流程（pipeline）的引用及其所在页码。
- 确认相关措辞，明确指出 PPO 仅作为一种算法基础，而非直接的 RLHF 证据。
- 确认应如何对“将 DPO 与 PPO 进行普适性排名比较”这一做法进行扣分（惩罚）。

## ERA-DEV-01

需查阅的源文件：

- `benchmarks/source_packets/dev/ERA-DEV-01/canonical_sources/agentbench_arxiv_2308.03688.pdf`

审查重点：

- 核实关于该八个环境基准测试的描述。
- 核实关于对 29 个模型进行评估的陈述及所采用的聚合方法。
- 核实关于成功率和综合得分的引用。
- 确认是否应将“数据污染/提示词泄露”（contamination/prompt leakage）视为一种潜在风险进行评分，而非将其作为既定事实处理。

## RL-DEV-01

需查阅的源文件：

- `benchmarks/source_packets/dev/RL-DEV-01/canonical_sources/d4rl_arxiv_2004.07219.pdf`
- `benchmarks/source_packets/dev/RL-DEV-01/canonical_sources/cql_arxiv_2006.04779.pdf`

审查重点：

- 核实 D4RL 数据集中的病态现象术语及标准化得分的详细信息。
- 核实关于 CQL 中“分布偏移/过高估计/保守 Q 函数”等概念的表述框架。
- 核实 CQL 结果表格的引用。 - 确认推断在线性能所需的 RL 协议字段及相关惩罚机制。

## PS-DEV-01

需打开的源文件：

- `benchmarks/source_packets/dev/PS-DEV-01/canonical_sources/bert_rediscovers_arxiv_1905.05950.pdf`
- `benchmarks/source_packets/dev/PS-DEV-01/canonical_sources/bertology_arxiv_2002.12327.pdf`
- `benchmarks/source_packets/dev/PS-DEV-01/canonical_sources/structural_probe_acl_N19-1419.pdf`
- `benchmarks/source_packets/dev/PS-DEV-01/canonical_sources/local_seed_idea_representation_probing.md`

审查重点：

- 核实《BERT Rediscovers》一文中关于局限性的表述。
- 核实《BERTology》一文中关于综述/探究（probing）部分的参考文献。
- 核实《Structural Probe》一文中关于方法论及局限性的具体位置。
- 确认针对“相关性探究与因果性断言”这一议题，其相关“关键错误”措辞是否准确。