# project-incarnation

`project-incarnation` is a Codex skill for distilling a repo, framework, methodology, or existing skill into a high-density `SKILL.md`.

## Repository Layout

```text
.codex/skills/project-incarnation/SKILL.md
```

The published copy keeps the original Codex skill path so it can be dropped into an existing Codex home with minimal changes.

## Install

Copy this repository's skill directory into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R .codex/skills/project-incarnation ~/.codex/skills/
```

## Publish To GitHub

Create an empty GitHub repository, then run:

```bash
cd /path/to/project-incarnation-skill
git remote add origin <your-github-repo-url>
git push -u origin main
```
