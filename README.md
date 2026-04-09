# project-incarnation

[中文说明](./README.zh-CN.md)

`project-incarnation` is a skill for turning a repo, framework, SDK, engineering methodology, or existing skill into a high-density `SKILL.md`.

Its job is narrow and strict: compress an object's real judgment into one self-contained file that a downstream agent can reason with.

## Quickstart

Install into Codex manually:

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

Or install from GitHub with the Skills CLI:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
```

Invoke it explicitly:

```text
$project-incarnation Distill this repository into a reusable skill that captures maintainer judgment.
```

## What This Skill Produces

The output is a single child skill:

```text
.codex/skills/<slug>/SKILL.md
```

That generated skill should contain:

- the truth the object is protecting
- recurring judgment crystals
- default objections and tradeoffs
- boundaries and abstention rules
- evidence anchors
- update triggers and confusion warnings

This skill does **not** try to generate bundles or sidecar packages such as:

- `constitution.yaml`
- `sources.jsonl`
- `bundle-spec.json`
- `evals.md`

## Best Use Cases

Use `project-incarnation` when you want to:

- distill a local repo into a reusable engineering perspective
- turn a framework or SDK into a judgment-heavy skill
- compress an engineering philosophy or methodology into a usable agent skill
- upgrade an existing weak skill that has voice but not evidence
- produce a reusable technical persona for planning, review, migration, or design work

## How The Skill Works

The skill follows a strict pipeline:

1. Route the request by object type: repo, stack, methodology, or existing skill.
2. Lock the four anchors: object, protected truth, problem class, and non-responsibilities.
3. Gather evidence from code, docs, maintainer writing, release history, and real friction.
4. Extract judgment crystals, heuristics, objections, tensions, boundaries, and watchlist triggers.
5. Run density checks before rendering.
6. Emit a single self-contained `SKILL.md`.

If the generated skill needs extra files to explain how it thinks, the distillation failed.

## Repository Layout

```text
./
├── LICENSE
├── README.md
├── README.zh-CN.md
└── SKILL.md
```

The repository is intentionally flat. The public distribution surface is one English `SKILL.md`, plus bilingual documentation.

## Translation Audit

The current English `SKILL.md` was reviewed against the original Chinese draft before the repository was flattened.

That review verified preservation of the same:

- scope
- phase order
- evidence requirements
- rendering contract
- validation checklist
- update protocol
- forbidden moves

The English file is meant to be a semantic translation, not a simplified rewrite.

## Install

### Option 1: Manual Codex install

Copy the root skill file into your local Codex skills directory:

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

After installing a new skill, restart Codex so it reloads the skill list.

### Option 2: Install with the Skills CLI

Install directly from GitHub:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g
```

For non-interactive installs:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
```

To list the available skills in the repository without installing:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -l
```

You do not need to publish the skill itself as an npm package. The `skills` package is the installer; the skill is distributed from GitHub.

## How To Invoke The Skill

After installation, invoke it explicitly by name:

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
$project-incarnation Upgrade this existing skill into a denser version with evidence anchors, boundaries, and update triggers.
```

## What Inputs Produce The Best Results

The skill works best when you provide one or more of the following:

- a local repository path
- a GitHub repository URL
- a framework, SDK, or stack name
- an existing `SKILL.md`
- a short description of the decision domain you care about

For better outputs, include:

- the object's version or branch
- what kind of questions the future skill should answer
- what it should explicitly avoid answering
- important docs, PRs, release notes, or maintainer essays

## What Good Output Looks Like

A strong generated skill should let a downstream agent answer:

- What does this object protect?
- What does it oppose?
- What evidence does it check first?
- What tradeoffs does it accept?
- When should it abstain?
- What events force an update?

If the generated skill only sounds smart but cannot reject a bad plan, it is not done.

## Using The Generated Skill

The child skill produced by `project-incarnation` is meant for downstream use in:

- architecture review
- planning and design discussion
- tradeoff analysis
- migration advice
- code review with object-specific judgment

The expected pattern is:

1. Use `project-incarnation` once to distill the object.
2. Install the generated child skill.
3. Invoke the child skill directly for future work.

`project-incarnation` is the authoring skill. The generated child skill is the reusable judgment artifact.

## Updating A Generated Skill

When updating a skill previously generated by `project-incarnation`, the intended process is:

1. Read the current `SKILL.md`.
2. Keep stable-core judgment unless evidence changed.
3. Refresh version-sensitive claims, maintainer stance, release impacts, and controversy shifts.
4. Update confusion warnings and watchlist triggers only if reality changed.
5. Avoid rewriting the whole skill unless the original structure was wrong.

## Publish This Repository To GitHub

Create an empty GitHub repository, then run:

```bash
cd /path/to/project-incarnation-skill
git remote add origin git@github.com:<owner>/<repo>.git
git push -u origin main
```

If you prefer HTTPS:

```bash
git remote add origin https://github.com/<owner>/<repo>.git
git push -u origin main
```

## skills.sh And `npx skills`

The intended distribution path is:

1. Publish the skill in a GitHub repository.
2. Expose a valid root `SKILL.md`.
3. Install it with `npx skills add <owner>/<repo> -a codex -g`.
4. Let the skills ecosystem discover it through installs.

In practice, supporting `skills.sh` means making the GitHub repository installable by the `skills` CLI.

## Local Verification Status

This repository has been verified to the following extent:

- `git push -u origin main` succeeded to `https://github.com/linsir2/project-incarnation-skill.git`
- `npm view skills version` resolved successfully and returned `1.4.9`
- `npx -y skills --help` executed successfully
- `npx -y skills add linsir2/project-incarnation-skill -a codex -g -l` successfully discovered 1 skill: `project-incarnation`

The only thing still not verified in this environment is a full install into local agent directories, because that would mutate the current machine's skill setup.

## License

This repository is released under the MIT License. See [LICENSE](./LICENSE).
