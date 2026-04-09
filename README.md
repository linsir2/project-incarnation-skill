# project-incarnation

`project-incarnation` is a Codex skill for turning a repo, framework, SDK, engineering methodology, or existing skill into a high-density `SKILL.md`.

This skill does not try to produce a bundle, a registry package, or a role-play card. Its job is narrower and stricter: compress an object's real judgment into one file that a downstream agent can actually reason with.

## What This Skill Produces

The output is a single child skill:

```text
.codex/skills/<slug>/SKILL.md
```

That generated skill should contain:

- the truth the object is protecting
- its recurring judgment crystals
- default objections and tradeoffs
- honest boundaries and abstention rules
- evidence anchors
- update triggers and confusion warnings

This skill explicitly does **not** aim to generate:

- `constitution.yaml`
- `sources.jsonl`
- `bundle-spec.json`
- `evals.md`
- multi-file sidecar packages

## Best Use Cases

Use `project-incarnation` when you want to:

- distill a local repo into a reusable engineering perspective
- turn a framework or SDK into a judgment-heavy skill
- compress an engineering philosophy or methodology into a usable agent skill
- upgrade an existing weak skill that has voice but not evidence
- produce a reusable technical persona for planning, review, or design work

## How The Skill Works

The skill follows a strict pipeline:

1. Route the request by object type: repo, stack, methodology, or existing skill.
2. Lock the four anchors: object, protected truth, problem class, and non-responsibilities.
3. Gather evidence from code, docs, maintainer writing, release history, and real friction.
4. Extract judgment crystals, heuristics, objections, tensions, boundaries, and watchlist triggers.
5. Run density checks before rendering.
6. Emit a single self-contained `SKILL.md`.

The important design rule is that the generated skill must be able to stand on its own. If it needs extra files to explain how it thinks, the distillation failed.

## Repository Layout

```text
./
├── LICENSE
├── README.md
├── SKILL.md
├── SKILL.zh-CN.md
└── .codex/
    └── skills/
        └── project-incarnation/
            ├── LICENSE.txt
            ├── SKILL.md
            └── SKILL.zh-CN.md
```

Notes:

- Root [`SKILL.md`](./SKILL.md) is the install surface for `npx skills add`.
- [`SKILL.md`](./SKILL.md) is the English default.
- [`SKILL.zh-CN.md`](./SKILL.zh-CN.md) preserves the original Chinese source.
- The nested `.codex/skills/project-incarnation/` path matches Codex's native skill layout.

## Install

### Option 1: Manual Codex install

Copy the skill into your local Codex skills directory:

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/.codex/skills/project-incarnation/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

If you also want the Chinese reference file:

```bash
cp /path/to/project-incarnation-skill/.codex/skills/project-incarnation/SKILL.zh-CN.md \
  ~/.codex/skills/project-incarnation/SKILL.zh-CN.md
```

After installing a new skill, restart Codex so it reloads the skill list.

### Option 2: Install with the Skills CLI

Once this repository is pushed to GitHub, users should be able to install it with:

```bash
npx skills add <owner>/<repo> -a codex -g
```

Example:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g
```

For non-interactive installs:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
```

You do not need to publish the skill itself as an npm package. The `skills` package is the installer; the skill is distributed from GitHub.

## How To Invoke The Skill

After installation, invoke it explicitly by name in an agent that supports skills. The clearest form is:

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

You can also phrase the request more naturally if your agent routes skills from descriptions, but explicit invocation is more reliable.

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
- any important docs, PRs, release notes, or maintainer essays

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

`project-incarnation` is the authoring skill. The generated skill is the reusable judgment artifact.

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

The current distribution path is:

1. Publish the skill in a GitHub repository.
2. Make sure the repository exposes a valid root `SKILL.md`.
3. Install it with `npx skills add <owner>/<repo> -a codex -g`.
4. Let the skills ecosystem discover it through installs.

In practice, supporting `skills.sh` means making the GitHub repository installable by the `skills` CLI.

## Local Verification Status

This repository has been prepared for that distribution path:

- root `SKILL.md` exists for CLI discovery
- nested Codex-native skill path exists
- an MIT license is included
- the default skill is now English
- the original Chinese version is preserved

Live verification of `npx skills` in this environment is still incomplete because `npx skills --help` timed out instead of returning a CLI response.

More specifically, `npm view skills version` reached the npm registry lookup step and failed with DNS resolution errors (`EAI_AGAIN`) in this environment, so the repository is prepared for distribution but not yet proven by a live remote install here.

## License

This repository is released under the MIT License. See [LICENSE](./LICENSE).
