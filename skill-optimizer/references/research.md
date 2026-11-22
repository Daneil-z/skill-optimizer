# 方法学依据（2026-11 调研快照）

本 Skill 各阶段设计的理论来源。引用时注明出处；结论可能随研究进展过时，重大优化前可重跑阶段 3 刷新。

## 优化循环

- **OPRO**（Google DeepMind, ICLR 2024）：LLM 当优化器——当前版本+得分 → 生成新版本 → 评估 → 选最优，循环至收敛。对应阶段 5 的自动重写。
- **PromptWizard**（Microsoft Research）：feedback-driven critique + synthesis，平衡探索与利用，同时优化指令与示例。对应「评审→定向修改」。
- **DSPy**（Stanford, github.com/stanfordnlp/dspy）：提示词是可优化参数而非手写文本——「提示词工程→软件工程」的工程学依据。
- **Self-Refine / Reflexion / Voyager**（均 NeurIPS 2023, arXiv:2303.17651 / 2303.11366 / 2305.16291）：自我精炼、语言反思笔记、可复用技能库三条自进化路线；本 Skill 作用于「Skill 文件」这一技能库载体。

## 评审偏差与对策（阶段 2、4 的设计依据）

- **MT-Bench**（arXiv:2306.05685）：LLM 裁判三大偏差——位置、长度（verbosity）、自偏好（self-enhancement）；强裁判与人类一致性约 80%。对策：锚定评分规、强制原文证据、多轮独立评分、警惕「更长=更好」。
- **LLMs Cannot Self-Correct Reasoning Yet**（ICLR 2024）：无外部反馈时纯自我反思会把对的改成错的（GPT-4 GSM8K 95.5%→89.0%）。对策：客观硬检查层兜底 + 用户主观量化作为外部反馈，不做无验证的自动复测循环。
- **CRITIC**（arXiv:2305.11738）：给反思接外部验证器（测试、搜索、计算器）。对应确定性 lint 与金标锚点。
- **自偏好量化研究**（arXiv:2604.22891 等）：Generator 与 Judge 同源时分数高估是结构性的，多轮平均消不掉。对策：交叉裁判（可选）、评分理由留档。

## 生态背景（阶段 3 检索线索）

- Agent Skills 2025-10 由 Anthropic 发布，2025-12-18 成为开放标准（agentskills.io），2026-10-22 移交 Linux Foundation。
- 社区 skill 超 5 万个；安全普查显示约 87.8% 从未被审计（skillselion.com, 2026-08）——质量与安全体检是生态空白。
- 高 star 参照系：anthropics/skills、linshenkx/prompt-optimizer（前后对比交互）、obra/superpowers、DaizeDong/self-evolve（中文自进化调研）。