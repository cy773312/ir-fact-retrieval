# IR Fact Retrieval

<p align="center">
  <strong>面向国际关系具体事件的事实检索型 Codex Skill</strong><br />
  用中立、结构化、可复用的方式，把冲突、仲裁、制裁、出口管制与外交议题整理成事实底稿。
</p>

<p align="center">
  <a href="./README.en.md">English</a> ·
  <a href="./SKILL.md">SKILL.md</a> ·
  <a href="https://github.com/alchaincyf/darwin-skill">Darwin Skill</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Codex-Skill-111827?style=flat-square" alt="Codex Skill" />
  <img src="https://img.shields.io/badge/Language-Chinese%20First-0f766e?style=flat-square" alt="Chinese First" />
  <img src="https://img.shields.io/badge/Use%20Case-IR%20Fact%20Briefs-1d4ed8?style=flat-square" alt="IR Fact Briefs" />
  <a href="https://github.com/alchaincyf/darwin-skill">
    <img src="https://img.shields.io/badge/Optimized%20with-Darwin%20Skill-7c3aed?style=flat-square" alt="Optimized with Darwin Skill" />
  </a>
</p>

## 一句话介绍

`ir-fact-retrieval` 是一个专门服务于**国际关系具体事件**的事实底稿 skill。  
它不先讲理论流派，而是先帮你回答这些研究中最常见的问题：

- 到底发生了什么
- 时间线怎么展开
- 关键行为者是谁
- 哪些是已确认事实
- 哪些是主流认定
- 哪些地方存在争议
- 还缺什么信息

## 适合什么场景

这个 skill 特别适合：

- 美国对华出口管制
- 南海仲裁案
- 俄乌战争中的某一轮升级
- 加沙停火谈判
- 联合国决议与制裁机制
- 边境冲突、外交危机、联盟争议
- 需要快速建立“事实认知底盘”的 IR 研究任务

它**不主要用于**：

- 纯理论比较
- 纯规范判断
- 开放式大战略推演

## 这个 Skill 会做什么

它会把用户的问题变成一份可继续研究、可继续扩写、可直接拿去汇报的 Markdown 事实底稿，默认包含：

1. 事件概览
2. 结构性背景
3. 行为者分析
4. 关键事件时间线
5. 核心争议与分歧
6. 关键数据与文件
7. 延伸关联
8. 信息缺口

核心能力可以概括成 4 件事：

| 能力 | 作用 |
|---|---|
| 先界定边界 | 避免把多个事件、多个时间段混写 |
| 先找高可信来源 | 优先官方、条约、裁决、机构文件 |
| 区分事实与解释 | 避免把叙事当事实，把争议当结论 |
| 输出可复用底稿 | 更适合研究、汇报、写作，而不只是聊天回答 |

## 触发方式

适合被这样调用：

```text
请用 ir-fact-retrieval 帮我梳理美国对华出口管制，重点看半导体和 AI 芯片。
```

```text
What happened in the South China Sea arbitration? Build a fact brief.
```

```text
帮我梳理一下加沙停火谈判的来龙去脉，按事实、行为者、争议点来写。
```

也适合更口语化的请求：

- “帮我梳理一下来龙去脉”
- “这个冲突到底发生了什么”
- “给我一版事实底稿”
- “timeline + actors + dispute points”

## 输出风格

这个 skill 的输出目标不是“写得像评论文章”，而是“更像一份事实底稿”。

它会尽量做到：

- 中立
- 来源敏感
- 结构化
- 争议显式标注
- 方便继续扩写成报告、PPT 或研究笔记

常见的分级标签包括：

- `已确认`
- `主流认定`
- `存在争议`
- `待核实`

## 快速安装

如果你的 Codex skills 放在 `$CODEX_HOME/skills` 下：

```bash
git clone https://github.com/cy773312/ir-fact-retrieval.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/ir-fact-retrieval"
```

也可以手动复制整个目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R ir-fact-retrieval "${CODEX_HOME:-$HOME/.codex}/skills/"
```

## 仓库结构

```text
ir-fact-retrieval/
├── README.md
├── README.en.md
├── SKILL.md
└── agents/
    └── openai.yaml
```

## 为什么这个 Skill 值得单独存在

国际关系问题里，一个很常见的痛点是：

- 用户问的是一个**具体事件**
- 但模型容易直接滑向理论、立场或评论
- 结果缺少一份“能继续研究”的事实底稿

这个 skill 的设计目标，就是把回答强行拉回到事实研究路径：

- 先收窄事件边界
- 再组织高可信来源
- 再把事实、争议、行为者与时间线拆开

## 使用 Darwin Skill 做迭代优化

这个仓库不是一次性写出来的，而是借助 [`darwin-skill`](https://github.com/alchaincyf/darwin-skill) 做了多轮迭代优化。

优化方式不是“重写一遍就算完”，而是更像一个小型 hill-climbing 流程：

1. 先评分
2. 每轮只改一个弱项
3. 改后重新评估
4. 用独立子 agent 跑 `with_skill / baseline`
5. 只有分数上升才保留，否则回滚

实际测试 prompt 包括：

- 美国对华出口管制
- 美国对海康威视的限制机制
- 南海仲裁案

这意味着它不是只在纸面上“写得工整”，而是在真实任务下反复比对过：

- 是否更像事实底稿
- 是否更能区分事实与争议
- 是否比不带 skill 的 baseline 更稳定

## 设计原则

- Facts first, theory second
- Official sources before commentary
- Label disputes explicitly
- Add context, but do not sprawl
- Produce something reusable

## 相关文件

- Skill 主体：[SKILL.md](./SKILL.md)
- UI 元数据：[agents/openai.yaml](./agents/openai.yaml)
- Darwin 优化器：[darwin-skill](https://github.com/alchaincyf/darwin-skill)

## License

当前仓库尚未附带许可证文件。若你希望开放复用条款，建议补一个 `MIT` 或 `Apache-2.0`。
