# project-incarnation

`project-incarnation` is a Codex skill for distilling a repo, framework, methodology, or existing skill into a high-density `SKILL.md`.

## Repository Layout

```text
./
├── SKILL.md
├── LICENSE
├── README.md
└── .codex/skills/project-incarnation/SKILL.md
```

The root [`SKILL.md`](./SKILL.md) is for `npx skills add <owner>/<repo>` compatibility.

```text
.codex/skills/project-incarnation/SKILL.md
```

The nested copy keeps the original Codex skill path so it can also be dropped into an existing Codex home with minimal changes.

## Install

### Codex manual install

Copy the skill into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp SKILL.md ~/.codex/skills/project-incarnation/SKILL.md
```

### Install with the Skills CLI

Once the repository is on GitHub, users can install it with:

```bash
npx skills add <owner>/<repo> -a codex -g
```

Examples:

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g
npx skills add https://github.com/linsir2/project-incarnation-skill -a codex -g
```

`skills` is the CLI package name, but the skill itself is distributed from GitHub. You do not need to publish this repo to npm.

## skills.sh

There is no separate manual submission flow documented for skills.sh. The current documented path is:

1. Host the skill in a GitHub repository.
2. Make sure the repo contains a valid `SKILL.md`.
3. Have users install it with `npx skills add <owner>/<repo>`.
4. The skills.sh leaderboard picks it up automatically from anonymous install telemetry.

In other words, "support skills.sh" really means "make the GitHub repo installable by `npx skills add`."

## Publish To GitHub

Create an empty GitHub repository, then run:

```bash
cd /path/to/project-incarnation-skill
git remote add origin <your-github-repo-url>
git push -u origin main
```

If you use SSH:

```bash
git remote add origin git@github.com:<owner>/<repo>.git
git push -u origin main
```

If you use HTTPS:

```bash
git remote add origin https://github.com/<owner>/<repo>.git
git push -u origin main
```

After that, your install command becomes:

```bash
npx skills add <owner>/<repo> -a codex -g
```

## License

This repository is released under the MIT License. If you want your real name or organization name in the copyright line, edit [`LICENSE`](./LICENSE).
