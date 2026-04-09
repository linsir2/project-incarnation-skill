# project-incarnation

[中文 README](./README.zh-CN.md)

`project-incarnation` distills a repo, framework, SDK, methodology, or existing skill into a reusable technical persona.

It does not produce a summary or a bundle. It produces one dense `SKILL.md` that preserves how the object actually makes decisions: what it protects, what it rejects, what evidence it checks first, and where it should abstain.

## What This Skill Does

When active, `project-incarnation` is designed to:

- classify the object being distilled: project, stack, methodology, or existing skill
- gather evidence from docs, code, tests, releases, maintainer writing, and real-world friction
- extract judgment crystals, decision heuristics, default objections, boundaries, tensions, and watchlist triggers
- render a single self-contained child `SKILL.md`
- avoid bundle-style outputs and tool-specific scaffolding

## Use When

Use this skill when you want to:

- turn a codebase into a reusable engineering perspective
- turn a framework or SDK into a judgment-heavy skill
- compress a methodology into a skill that can participate in planning or review
- upgrade an existing skill that has voice but weak evidence, boundaries, or predictive power

## Output

The output is a single child skill.

Default location:

```text
<project-root>/skills/<slug>/SKILL.md
```

Fallback when there is no clear project root:

```text
./skills/<slug>/SKILL.md
```

A strong generated child skill should include:

- the truth the object is protecting
- judgment crystals
- decision heuristics
- default objections
- honest boundaries
- evidence anchors
- confusion warnings
- watchlist triggers

Tool-private directories such as `.codex/` and `.claude/` are adapter paths, not the canonical default output.

## Install

Install manually into Codex:

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

Install from GitHub with the Skills CLI:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
```

## How To Use

Invoke it explicitly:

```text
$project-incarnation <your request>
```

Examples:

```text
$project-incarnation Distill this repository into a skill that captures maintainer judgment.
```

```text
$project-incarnation Turn FastAPI into a high-density skill focused on API contract design and production boundaries.
```

```text
$project-incarnation Upgrade this existing skill with better evidence, boundaries, and update triggers.
```

## Best Inputs

You will get the best results if you provide:

- a local repository path or GitHub URL
- the framework, SDK, stack, or methodology name
- an existing `SKILL.md` when upgrading
- the version or branch that matters
- the kinds of questions the generated skill should answer
- any key docs, PRs, release notes, or maintainer writing

## Repository Contents

This repository is intentionally minimal:

- [`SKILL.md`](./SKILL.md): the skill itself
- [`README.md`](./README.md): English documentation
- [`README.zh-CN.md`](./README.zh-CN.md): Chinese documentation

## License

MIT. See [LICENSE](./LICENSE).
