# IR Fact Retrieval

> A focused Codex skill for building neutral, source-aware fact bases on international relations events, disputes, sanctions, export controls, wars, arbitration cases, and diplomatic crises.

[![Skill](https://img.shields.io/badge/Codex-Skill-111827?style=flat-square)](./SKILL.md)
[![Language](https://img.shields.io/badge/Language-Chinese%20first-0f766e?style=flat-square)](./SKILL.md)
[![Optimized with Darwin Skill](https://img.shields.io/badge/Optimized%20with-Darwin%20Skill-7c3aed?style=flat-square)](https://github.com/alchaincyf/darwin-skill)

## Why This Exists

When users ask about a concrete international relations issue, they often do **not** want a theory lecture first.
They want a clean factual base:

- What happened
- When it happened
- Who the key actors are
- Which parts are confirmed
- Which parts are disputed
- Which documents and data matter

`ir-fact-retrieval` is designed for exactly that job.

It turns vague or politically loaded IR questions into a structured factual brief, while keeping facts, interpretations, and disputes clearly separated.

## What This Skill Does

This skill helps Codex:

- identify the exact event boundary before answering
- retrieve and prioritize official and primary sources
- distinguish confirmed facts from mainstream judgments and disputed claims
- add only necessary structural background
- separate actor positions from objective event history
- produce a reusable Markdown fact brief

It is especially useful for topics like:

- U.S.-China export controls
- South China Sea arbitration
- Gaza ceasefire talks
- sanctions regimes
- Taiwan Strait incidents
- alliance disputes
- border crises
- UN resolutions and treaty disputes

## Output Style

By default, the skill pushes Codex toward a structured report with:

1. Event overview
2. Structural background
3. Actor analysis
4. Timeline
5. Core disputes
6. Key documents and data
7. Related issues
8. Information gaps

It is built to be:

- neutral
- source-aware
- multilingual
- usable for research notes, briefs, and speaking prep

## Trigger Patterns

This skill is meant to trigger when the user clearly refers to a **specific IR event or issue**, for example:

- “俄乌战争现在进展到哪一步”
- “美国对海康威视的出口管制是什么”
- “What happened in the South China Sea arbitration?”
- “帮我梳理一下加沙停火谈判的事实基础”
- “timeline + actors + dispute points for the Taiwan Strait crisis”

It is **not** primarily for:

- pure IR theory
- normative policy advice
- open-ended grand strategy speculation

## Example Invocation

```text
Use $ir-fact-retrieval to build a neutral fact base for the South China Sea arbitration.
```

Or more naturally:

```text
请用 ir-fact-retrieval 帮我梳理美国对华出口管制，重点看半导体和 AI 芯片。
```

## Repository Layout

```text
ir-fact-retrieval/
├── README.md
├── SKILL.md
└── agents/
    └── openai.yaml
```

## Installation

If you use Codex skills from `$CODEX_HOME/skills`, place this folder there:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R ir-fact-retrieval "${CODEX_HOME:-$HOME/.codex}/skills/"
```

Or clone directly into your skills directory:

```bash
git clone https://github.com/cy773312/ir-fact-retrieval.git "${CODEX_HOME:-$HOME/.codex}/skills/ir-fact-retrieval"
```

## Design Principles

This skill is built around a few strong constraints:

- Facts first, theory second
- Official sources before commentary
- Disputes must be labeled, not blurred
- Context should be sufficient, not sprawling
- Output should be reusable as a factual brief

## Iterative Optimization with Darwin Skill

This repository was iteratively improved using [`darwin-skill`](https://github.com/alchaincyf/darwin-skill), an autonomous skill-optimization workflow inspired by Karpathy-style autoresearch.

The optimization process followed a hill-climbing pattern:

1. score the skill on a structured rubric
2. modify only one weak dimension at a time
3. re-evaluate after each change
4. keep changes only if the score improves
5. use independent sub-agents for real prompt-based comparison

That matters because this skill is not just “written nicely” on paper; it was stress-tested against realistic prompts such as:

- U.S. export controls on China
- U.S. restrictions on Hikvision
- the South China Sea arbitration

The goal of those iterations was not to make the file longer, but to make the skill:

- more stable under real use
- better at scoping factual questions
- better at separating fact from dispute
- more consistent in producing reusable research briefs

## Notes

- The skill body lives in [SKILL.md](./SKILL.md).
- UI-facing metadata lives in [agents/openai.yaml](./agents/openai.yaml).
- The repository is intentionally small and focused.

## License

No license file has been added yet. Add one if you want to make reuse terms explicit.
