# project-incarnation

[中文说明](./README.zh-CN.md)

`project-incarnation` is a skill for distilling a repo, framework, SDK, methodology, or existing skill into a high-density `SKILL.md`.

It is an authoring skill. Its job is to compress an object's real judgment into one reusable child skill, not to generate bundles or sidecar metadata.

## What It Produces

The output is a single child skill, typically written to:

```text
<repo>/skills/<slug>/SKILL.md
```

A good generated skill should contain:

- the truth the object is protecting
- recurring judgment crystals
- default objections and tradeoffs
- boundaries and abstention rules
- evidence anchors
- update triggers and confusion warnings

Tool-private directories such as `.codex/` or `.claude/` are adapter paths, not the canonical default output.

## Install

Manual Codex install:

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
$project-incarnation Upgrade this existing skill with evidence anchors, boundaries, and update triggers.
```

## Best Inputs

This skill works best when you provide:

- a local repository path or GitHub URL
- a framework, SDK, stack, or methodology name
- an existing `SKILL.md` if you want an upgrade
- the version or branch you care about
- the question types the generated child skill should answer
- any key docs, PRs, release notes, or maintainer writing

## What Good Output Looks Like

A strong generated skill should let a downstream agent answer:

- What does this object protect?
- What does it oppose?
- What evidence does it check first?
- What tradeoffs does it accept?
- When should it abstain?
- What events force an update?

If the generated skill only sounds smart but cannot reject a bad plan, it is not done.

## License

MIT. See [LICENSE](./LICENSE).
