# project-incarnation

[中文 README](./README.zh-CN.md)

`project-incarnation` is a skill for turning a repo, framework, SDK, methodology, or existing skill into a reusable technical persona.

Its output is not a summary, a role-play card, or a bundle of side files. Its job is to produce one dense `SKILL.md` that preserves how the object actually makes decisions.

## Why This Exists

Most generated skills fail for one of two reasons:

- they rewrite documentation without extracting judgment
- they imitate tone without preserving boundaries, tradeoffs, or evidence paths

`project-incarnation` exists to avoid both.

It forces the resulting skill to carry:

- what truth the object is protecting
- what it rejects by default
- what evidence it checks first
- what tradeoffs it accepts
- when it should abstain
- what changes should trigger an update

## What You Get

The result is a single child skill, typically written to:

```text
<repo>/skills/<slug>/SKILL.md
```

A strong generated child skill should include:

- judgment crystals
- decision heuristics
- default objections
- honest boundaries
- evidence anchors
- confusion warnings
- watchlist triggers

Tool-private directories such as `.codex/` or `.claude/` are adapter paths, not the canonical default output.

## Install

Install manually into Codex:

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

Or install from GitHub with the Skills CLI:

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
$project-incarnation Upgrade this existing skill with evidence anchors, boundaries, and update triggers.
```

## Best Inputs

You will get the best result if you provide:

- a local repository path or GitHub URL
- the framework, SDK, stack, or methodology name
- an existing `SKILL.md` when upgrading
- the version or branch that matters
- the kinds of questions the generated skill should answer
- any key docs, PRs, release notes, or maintainer writing

## What Good Output Looks Like

A strong generated skill should let a downstream agent answer:

- What does this object protect?
- What does it oppose?
- What evidence does it check first?
- What tradeoffs does it accept?
- When should it abstain?
- What events force an update?

If the generated skill only sounds smart but cannot reject a bad plan, it is not finished.

## License

MIT. See [LICENSE](./LICENSE).
