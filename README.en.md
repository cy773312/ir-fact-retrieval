# IR Fact Retrieval

<p align="center">
  <strong>A Codex skill for building neutral, source-aware fact briefs on concrete international relations events.</strong><br />
  Designed for conflicts, sanctions, export controls, arbitration cases, diplomatic crises, and other event-level IR questions.
</p>

<p align="center">
  <a href="./README.md">中文</a> ·
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

## What It Is

`ir-fact-retrieval` is a focused Codex skill for turning a concrete IR question into a structured factual brief.

Instead of jumping straight into theory or opinion, it helps answer:

- What happened
- When it happened
- Who the key actors are
- Which claims are confirmed
- Which are mainstream judgments
- Which are disputed
- What information is still missing

## Best Use Cases

This skill works especially well for:

- U.S.-China export controls
- the South China Sea arbitration
- sanctions disputes
- ceasefire negotiations
- alliance crises
- border incidents
- UN resolutions and treaty disputes

It is **not primarily designed for**:

- pure IR theory
- purely normative analysis
- open-ended grand strategy speculation

## What It Produces

By default, it pushes Codex toward a reusable Markdown fact brief with:

1. Event overview
2. Structural background
3. Actor analysis
4. Timeline
5. Core disputes
6. Key documents and data
7. Related issues
8. Information gaps

## Why It Helps

Concrete IR questions often create the same failure mode:

- the user asks about a specific event
- the model drifts into theory, ideology, or commentary
- the answer becomes hard to reuse as a research note

This skill is built to resist that drift.

Its default workflow is:

- define the event boundary first
- prioritize official and primary sources
- separate facts from interpretations
- surface disputes explicitly
- produce something reusable for further research or writing

## Example Prompts

```text
Use $ir-fact-retrieval to build a neutral fact base for the South China Sea arbitration.
```

```text
Please use ir-fact-retrieval to map U.S. export controls on China, focusing on semiconductors and AI chips.
```

```text
Help me reconstruct the factual background of Gaza ceasefire negotiations, with timeline, actors, and dispute points.
```

## Installation

Clone into your Codex skills directory:

```bash
git clone https://github.com/cy773312/ir-fact-retrieval.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/ir-fact-retrieval"
```

## Repository Layout

```text
ir-fact-retrieval/
├── README.md
├── README.en.md
├── SKILL.md
└── agents/
    └── openai.yaml
```

## Iterative Optimization with Darwin Skill

This repository was iteratively improved with [`darwin-skill`](https://github.com/alchaincyf/darwin-skill), using a hill-climbing workflow rather than a one-shot rewrite.

The process looked like this:

1. score the skill
2. improve one weak dimension at a time
3. re-score after each edit
4. compare `with_skill` vs `baseline`
5. keep the change only if the score improves

That process was used against realistic prompts such as:

- U.S. export controls on China
- U.S. restrictions on Hikvision
- the South China Sea arbitration

So this skill was optimized not only for readability, but also for real prompt performance.

## Design Principles

- Facts first, theory second
- Primary sources before commentary
- Disputes should be labeled, not blurred
- Context should be sufficient, not sprawling
- Output should be reusable as a fact brief

## Related Files

- Skill body: [SKILL.md](./SKILL.md)
- UI metadata: [agents/openai.yaml](./agents/openai.yaml)
- Optimizer: [darwin-skill](https://github.com/alchaincyf/darwin-skill)

## License

No license file has been added yet. If you want explicit reuse terms, consider adding `MIT` or `Apache-2.0`.
