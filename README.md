# Skill Optimizer

> 一个专门优化你技能的技能。10 道工程闸门、24 个交互点、4 个调研来源，最后交出一份能直接交付的 SKILL.md。

The skill that optimizes your skills. 10 engineering gates, 24 interaction points, 4 research sources. One SKILL.md, ready to ship.

基于 Anthropic Agent Skills 规范编写，兼容 Claude Code / Claude.ai / Claude API 以及其他支持 SKILL.md 的宿主。

---

## 三条特色

1. **软评测，成本低** —— 三评委读评 + 逻辑查验定位问题，一次优化通常只要 3–5 次模型调用，能天天跑。官方 skill-creator 和社区 darwin-skill 都要真跑任务，一轮十几次起步。
2. **改进方向有出处** —— 四源调研（GitHub 高分作品 / 最新论文 / 研究新闻 / 社区论坛），再把结论做受控发散，落成具体改动。这一步别人没有。
3. **每处改动可追溯** —— 改动 ↔ 规格 ↔ 问题编号三向对齐，配四项全量清单（改动 / 优化 / 建议 / 变化），谁都能复盘。

## 它怎么工作

```
阶段 0 开场 → 阶段 1 意见采集 → 阶段 2 六层检测 → 阶段 3 多评委审核
→ 阶段 4 四源调研 → 阶段 5 发散借鉴 → 阶段 6 规格确认 + 全自动重写 → 交付
```

- **内核是确定性的**：10 条硬规则（K1–K10）管闸门、备份、追溯、留痕，模型只负责创造，写文件必须穿过闸门。
- **每一步都评分**：逻辑 / 体验 / 工程三个评委独立打分，附原文证据，分歧 ≥2 分重评。
- **调研自动跑**：四源并行，精简 / 标准 / 深度三档。
- **改完全程可查**：所有改动逐条挂规格编号和问题编号。

## 四种用法

| 用法 | 用户说什么 | 结果 |
| --- | --- | --- |
| 体检 | 「看看这技能有没有毛病」 | 只检测不改文件，出问题排序表 |
| 质量优化 | 「优化这个 skill」 | 六层检测 + 评审 + 调研 + 重写 + 报告 |
| 个性化改造 | 「这 skill 用着不顺手，按我的习惯改」 | 只动触发词/默认值/profile，核心流程不动 |
| 自进化 | 「优化你自己」 | 元技能给自己做一次优化 |

## 交付物

| 产物 | 内容 |
| --- | --- |
| 优化后的 SKILL.md | 逻辑问题清零，或书面说明不修理由 |
| `skill-optimizer-records/<名称>-<日期>/` | 9 份过程文件：意见、检测、评审、调研、创意、规格、循环、交互、报告 |
| report.md | 四项全量清单 + 自动决策清单 + 触发正负例 |
| 备份 | `<原名>-backup-<日期>`，永不修改，可随时回滚 |

## 安装

**Claude.ai**：把 `skill-optimizer/` 文件夹压成 zip（顶层必须是这个文件夹）→ `Settings → Capabilities → Skills → Upload skill`。

**Claude Code**：

```bash
git clone https://github.com/Daneil-z/skill-optimizer.git
cp -r skill-optimizer/skill-optimizer ~/.claude/skills/skill-optimizer
```

装好后新开会话，或执行 `/skills reload`。

## 怎么用

- 体检：`看看这几个 skill 有没有毛病`
- 质量优化：`帮我优化这个 skill，.claude/skills/weekly-report/SKILL.md，触发不太对`
- 个性化：`这 skill 用着不顺手，按我的习惯改，别问我太多`
- 自进化：`优化你自己`

## 目录结构

```
skill-optimizer/
├── SKILL.md                  # 内核规则 + 六阶段流程
└── references/               # 按需加载
    ├── interactions.md       # 24 点交互矩阵
    ├── rubric.md             # 六维评分规与锚点
    └── research.md           # 方法学依据（2026-11 快照）
```

## 设计取舍

- **不自发复测**：改完不自己开验证循环，避免自评自证；改为给出触发正负例，由你自行验证。
- **不删能力**：拿不准的一律保留并标注，删除要先得到你同意。
- **诚实标注**：没跨模型校准、没上真机，报告里都会明说，不拿"更规范"冒充"更好用"。

## 许可证

MIT。可自由使用、修改、二次分发；引用请保留本仓库来源。
