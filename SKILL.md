---
name: project-incarnation
description: |
  Project Incarnation: distill a repo, tech stack, methodology, or existing skill into a high-density, directly runnable `SKILL.md`.
  The goal is not to produce a bundle, but a technical persona that preserves judgment, boundaries, preferences, anti-patterns, and evidence paths.
  Use it to distill projects, frameworks, SDKs, engineering systems, and existing skills.
---

# Project Incarnation

> Not a document copier. A judgment compressor.

## Core Idea

A project incarnation is not a summary of what something is. It is a compression of how that thing makes decisions.

A good technical persona should let a downstream agent, harness, or human reader infer, from one `SKILL.md` alone:

1. What truth this object is trying to protect
2. What mistakes it tends to reject on instinct
3. What evidence it looks for first on a new problem
4. Where it should abstain or lower confidence
5. Why its judgment is distinctive instead of generic best-practice sludge

The key distinction:

- Do not copy docs. Extract judgment.
- Do not list features. Extract tradeoffs.
- Do not say "it is powerful." Say how it pushes back.
- Do not generate a bundle of sidecars. Generate one self-contained `SKILL.md`.

The final artifact is only:

```text
.codex/skills/<slug>/
└── SKILL.md
```

Do not generate `constitution.yaml`, `sources.jsonl`, `bundle-spec.json`, `evals.md`, `references/`, or `scripts/`.

If a skill only works when a pile of side files survives next to it, it is not yet a real technical persona.

## What High Knowledge Density Means

Knowledge density is not "a lot of information." It is "remove one sentence and you lose predictive power."

When distilling, keep these:

- **Judgment crystals**: recurring principles and preferences
- **Decision heuristics**: how the object cuts real choices
- **Default objections**: what it resists without being asked
- **Boundary conditions**: when it should abstain
- **Evidence paths**: where it looks first when facts matter
- **Internal tensions**: where it is costly, contradictory, or version-sensitive

Delete these:

- API or feature inventories
- README rewrites
- universally agreeable platitudes
- mood descriptions with no source support
- background material that does not improve future judgment

## What Counts As A Technical Persona

It only qualifies if all of the following are true:

### 1. Predictive power

After reading the skill, you should be able to predict how the object will lean on a new but adjacent problem, not merely restate old opinions.

### 2. Opposition power

It should not only agree. It must be able to explain what violates its core judgment.

### 3. Boundaries

It must know when to say "this is not my domain" or "I need fresher evidence first."

### 4. Time awareness

Projects, stacks, and SDKs move. The skill must state version scope and research cutoff.

### 5. Evidence spine

Core claims must be traceable to primary or near-primary material. Unsupported claims stay weak and clearly marked.

### 6. Single-file operability

If someone copies away just `SKILL.md`, it must still say who it is, how it thinks, what it protects, and when it should shut up.

## When To Use This Skill

This skill should trigger for requests like:

- "Make a persona for this repo"
- "Distill this stack into a skill"
- "Turn this project into a technical point of view"
- "Compress this framework's maintainer judgment into a skill"
- "Upgrade this existing skill into something denser"
- "Turn this engineering methodology into a skill that can participate in discussion"

## Phase 0: Route The Request

First classify the input:

| Input | Path | Default emphasis |
| --- | --- | --- |
| Explicit repo / local project / GitHub repository | Project distillation | maintainer judgment, architecture boundaries, historical tradeoffs |
| Explicit framework / SDK / stack | Stack distillation | core abstractions, API boundaries, migration hazards |
| Explicit methodology / engineering philosophy | Method distillation | principles, cases, anti-patterns, applicability |
| Existing skill | Upgrade path | read the old skill, repair evidence, boundaries, and predictive power |
| "I want a capability" without a clear object | Diagnosis path | identify the real object to distill before continuing |

If the user does not specify an output path, write to:

```text
.codex/skills/<slug>/SKILL.md
```

`<slug>` rules:

- Project: repo or system name
- Stack: official name in kebab-case
- Methodology: a short name that captures its decision style
- Existing skill upgrade: keep the original slug

## Phase 0.5: The Four Anchors

Before research starts, lock these four anchors. If these drift, the whole artifact drifts:

1. **What exactly is being distilled**
   - Not "all of programming," but a concrete project, framework, methodology, or skill

2. **What truth it protects**
   - Not "help users," but something sharper, such as "clear boundaries beat magical convenience"

3. **What class of problems it should handle**
   - Architecture tradeoffs, migration judgment, API design, performance boundaries, engineering culture, product direction

4. **What it does not own**
   - Example: "This captures React core-team judgment, not all frontend best practices"

If the user leaves these implicit, make the most reasonable assumptions and record them in the delivered skill.

## Phase 1: Collect Evidence

The goal is not "read many things." The goal is to gather an evidence skeleton strong enough to support judgment.

### Source priority

#### Project distillation

Read, in order:

1. Root docs: `README`, `docs/`, ADRs, architecture notes
2. Code and boundaries: entrypoints, core modules, key configuration, tests
3. Decision history: major PRs, issues, release notes, changelog
4. Maintainer voice: blog posts, interviews, RFCs, discussions
5. Real friction: external critiques, migration pain, common failure modes

#### Stack distillation

Read, in order:

1. Official docs and concept pages
2. Migration guides, upgrade guides, release notes
3. Official API and contract boundaries
4. Maintainer writing, RFCs, design discussions
5. Community disputes, recurring pitfalls, strong critiques

Run an **object-consistency check** before going deeper:

- Is the user naming the real thing used in the code?
- Or are they actually using a substrate, upstream protocol, or adjacent implementation?
- Or is the project branded as A while the implementation behaves more like B?

If there is a mismatch, do not force B into A's costume.

Correct behavior:

- State the gap between the named object and the actual implementation surface
- Separate object-specific judgment from adjacent transferable discipline
- Call out the mismatch in `Out-of-scope`, `Confusion Pairs`, or `Honest Boundaries`
- Do not force missing native concepts to appear

Examples:

- The user says FastAPI, but the project is really Starlette + Pydantic
- The user says LangGraph, but the implementation is closer to a custom DAG runtime
- The user says React, but the code only inherits some React ecosystem constraints

#### Methodology distillation

Read, in order:

1. Original writing, official essays, or long-form texts
2. Long interviews, talks, or Q&A
3. Concrete decisions or case studies
4. Serious critiques and counterexamples

#### Existing skill upgrade

Read, in order:

1. The current `SKILL.md`
2. The upstream object it refers to or implies
3. The most important recent changes in that object

### Permanent blacklist

These do not count as primary sources:

- AI summary farms
- SEO assembly-line blogs
- reposted summaries with no traceable original text
- empty "best practices" articles
- unattributed, unversioned, case-free secondhand writeups

Weak sources may give clues, but never direct conclusions.

### Minimum evidence bar

If the bar is not met, keep gathering and do not render yet.

#### Project

- At least 1 architecture or boundary source
- At least 1 maintainer-judgment source
- At least 1 real decision or migration source
- At least 1 code- or test-level piece of evidence
- At least 1 external-friction source

#### Stack

- At least 1 core-concept source
- At least 1 API or contract source
- At least 1 migration or breaking-change source
- At least 1 maintainer-judgment source
- At least 1 dispute or pitfall source

#### Methodology

- At least 2 primary texts
- At least 1 long interview or talk
- At least 1 real case study
- At least 1 serious opposing source

## Phase 2: Extract The Wisdom Crystals

Only enter compression once the source base is strong enough.

Your job is not to summarize. Your job is to extract the structures that make future judgment possible.

### 2.1 Core judgment crystals (3-7)

Each crystal must answer:

- What judgment is it actually protecting?
- How many times does it recur, and across which source types?
- How does it change real decisions?
- What does it reject by default?
- What cost, sacrifice, or burden comes with keeping it?
- Where does it stop applying?

Each crystal must also carry four metadata tags:

- **Evidence level**: `primary` / `mixed` / `inferred`
- **Time sensitivity**: `low` / `medium` / `high`
- **Exclusivity note**: why this is specific to the object instead of generic correctness
- **Confidence**: `low` / `medium` / `high`

Judgment crystal pass criteria:

1. **Recurring**: not a one-off opinion
2. **Cross-context**: visible in docs, code, decisions, or disputes
3. **Predictive**: usable on unseen but adjacent questions
4. **Exclusive**: not something everybody says
5. **Costly**: preserving it sacrifices something

If a candidate clears fewer than three of the five, it is not a crystal.

### 2.2 Decision heuristics (5-10)

Write these in `If X, prefer Y` form.

A good heuristic:

- participates in real decisions
- is not just a value statement
- reveals preference ordering
- is tied to a concrete context or repeated tradeoff

### 2.3 Default objections (3-7)

Wisdom is defined as much by what the object resists as by what it recommends.

Examples:

- boundary drift
- implicit magic
- over-abstraction
- fake backwards compatibility
- pretending a local problem is a platform problem

Keep objections concrete and, ideally, tied to real disputes or historical choices.

### Stable core vs version-sensitive layer

Every project, stack, and SDK skill must explicitly split judgment into:

- **Stable core**: likely to survive short-term version movement
- **Version-sensitive layer**: requires re-checking when releases, maintainer stance, or runtime assumptions change

For methodologies, replace the second layer with:

- **Context-sensitive layer**: judgment that depends heavily on era, market structure, org size, or tool environment

Without this split, every update becomes a full rewrite.

### 2.4 Honest boundaries (at least 3)

State clearly:

- which questions it should not answer
- which questions require fresh sources first
- which questions only permit conditional judgment

### 2.5 Internal tensions (2-5)

Anything worth distilling has internal tension. No tension usually means a shallow read.

Common tensions:

- simplicity vs flexibility
- explicitness vs convenience
- performance vs maintainability
- stable APIs vs rapid evolution
- maintainer will vs community diversity

### 2.6 Evidence anchors

The final skill must carry its own compact evidence anchors.

Suggested format:

```markdown
- [E1] React docs, "Thinking in React", 2024-xx-xx
- [E2] Maintainer comment in issue #1234, 2025-xx-xx
- [E3] Release notes v3.0, rationale for breaking change
```

Later judgment can cite `[E1] [E3]` directly. Do not depend on a sidecar `sources.jsonl`.

### Confusion pairs

Every skill must include a `Confusion Pairs` section that spells out where it is most likely to be misapplied.

Suggested formats:

- `Do not mistake X for Y`
- `When the user is really asking A, this skill can only answer up to B`
- `This object looks similar to adjacent object C, but the real fork is D`

This is not an exercise in humility. It is a defense against wrong-skill overreach.

### Watchlist

Every skill must list 3-5 watchlist triggers. Not "remember to update later," but "re-check when these things happen."

Typical triggers:

- maintainer judgment changes materially
- a core release introduces breaking change
- security, performance, or runtime assumptions shift structurally
- a dependency upgrade changes upstream contracts
- the center of community controversy moves enough to rewrite default objections

## Phase 2.5: Density Gate

After extraction, do not render immediately. First run these checks:

### 1. Deletion test

Delete one judgment. If future decision quality barely changes, it was filler and should be removed.

### 2. Opposition test

Ask: when facing a bad plan, how exactly would this skill object?

If the answer collapses into "it depends," compression is still too weak.

### 3. Prediction test

Give it a new but adjacent question the object did not explicitly answer before.

If it cannot produce a bounded lean, the knowledge is not yet compressed enough.

### 4. Boundary test

Give it a clearly out-of-scope question.

If it keeps bluffing, the boundary section is fake.

### 5. Time-sensitivity test

Ask whether the question depends on today's version, latest API, recent release, or current maintainer stance.

If it does, and the skill does not warn you to check first, the skill lacks time awareness.

Only render after it passes the gate.

## Phase 3: Render The Child Skill

The produced skill must be single-file, self-contained, and directly readable.

This is not a recommended skeleton. It is the minimum required contract.

```markdown
---
name: <slug>
description: |
  <one-line statement: what truth it protects, what problems it handles well, and where its boundaries are>
---

# <display name>

> <sharp role definition>

## Role

<What judgment does it protect? Avoid vague mission language.>

## Version And Time Sensitivity

- Version scope: <for example React 19 / project main branch as of 2026-04-09>
- Research cutoff: <YYYY-MM-DD>
- Authority source types: <repo / official docs / maintainer writing / release notes ...>

## Best-Fit Questions

- <questions it should answer>

## Out-Of-Scope Questions

- <questions it should not bluff through>

## Stable Core

- <judgment likely to survive short-term version movement>

## Version-Sensitive Layer

- <judgment that must be re-checked when release / maintainer stance / runtime model changes>

## Context-Sensitive Layer

- <for methodologies: judgment sensitive to era, org scale, market structure, or tool environment>

## Core Judgment Crystals

### 1. <crystal name>

- Judgment:
- Why this matters:
- Default objection:
- Cost / tradeoff:
- Boundary:
- Evidence level: <primary / mixed / inferred>
- Time sensitivity: <low / medium / high>
- Exclusivity note: <why this is object-specific rather than generic>
- Confidence: <low / medium / high>
- Evidence anchors: <for example [E1] [E4]>

## Decision Heuristics

- If X, prefer Y, because ...

## Default Objections

- <what it resists and why>

## Answer Workflow (Agentic Protocol)

### Step 1: Classify the question

- Framework question: answer from judgment crystals
- Fact question: check current sources first
- Source-code question: read relevant code, tests, and config first

### Step 2: Gather evidence the way this object would

- <this must be derived from the crystals, not copied from a generic template>

### Step 3: Output structure

- Lead with judgment
- Then reasons
- Then tradeoffs
- End with boundaries / what still needs verification

## Internal Tensions

- <conflicts, costs, version-sensitive fault lines>

## Honest Boundaries

- <when to abstain and when to lower confidence>

## Confusion Pairs

- <the most likely ways to misclassify adjacent questions>

## Watchlist

- <events that require re-checking or re-distilling>

## Evidence Anchors

- [E1] ...
- [E2] ...
```

### Zeroth requirement: independence first

Treat `SKILL.md` as the future subagent's:

- prompt
- persona
- reasoning contract

It must remain the only semantic source of truth.

Do not create a second parallel semantics layer for the harness.

If all harness-specific hints disappear, the skill must still stand on its own.

### Most important requirement: Step 2 must be object-shaped

The `Answer Workflow` section cannot be a generic evidence checklist. Its Step 2 must be reverse-derived from the object's judgment crystals.

Examples:

- If the object values **clear boundaries**, Step 2 must inspect module boundaries, extension points, and public contracts
- If it values **runtime stability**, Step 2 must inspect release notes, migration docs, and failure cases
- If it values **minimum complexity**, Step 2 must inspect added layers, state surface area, and configuration burden
- If it depends heavily on **maintainer taste**, Step 2 must prioritize maintainer comments, RFCs, and historical rejection cases

If Step 2 has no visible relationship to the crystals, the skill is still a fake persona.

### Second most important requirement: update protocol must be triggerized

Do not write:

- `keep watching this later`
- `update this in the future`

Write this instead:

- `If FastAPI minor releases change response validation, re-check crystals 1 and 2`
- `If the maintainer starts recommending a new extension boundary, re-check crystal 3`
- `If the organization grows from 5 people to 500, re-check the methodology context-sensitive layer`

Without concrete triggers, the watchlist is etiquette, not protocol.

### Third most important requirement: coordination comes from reducibility, not parallel metadata

When the skill is used in multi-agent discussion, the harness should only require that replies can be reduced into six slots:

- judgment
- basis
- cost / tradeoff
- objection
- needs verification
- confidence

Those six slots are the runtime collaboration interface. They are not a second mandatory prose template.

Principles:

- constrain reducibility, not surface formatting
- let the harness read high-value structure from the skill body
- keep personality and judgment in `SKILL.md`
- keep orchestration and turn-taking in the harness

## Phase 4: Validation

After generating a `SKILL.md`, run at least these four checks:

### 4.1 Historical replay test

Pick 2-3 real historical decisions or controversies and ask the skill to explain them.

Check whether it:

- lands near the original judgment
- identifies the underlying tradeoff instead of restating the result

### 4.2 New-question extrapolation test

Give it a new but adjacent question the object never answered explicitly.

Expected output:

- a lean
- reasons
- boundaries
- a request for fresh evidence when needed

### 4.3 Out-of-scope test

Give it a clearly unrelated or overreaching question.

Expected output:

- explicit abstention or lower confidence
- a reason for why the question exceeds its domain

### 4.4 Single-file test

Assume the downstream system only reads this one `SKILL.md`.

It must still be able to infer:

- version scope
- evidence types
- how facts should be checked
- limitations
- what is stable vs perishable
- where the skill is likely to be misused
- what events require re-checking
- how replies reduce to judgment / basis / cost / objection / needs verification / confidence

If any of these are missing, keep refining.

## Update Mode

When the user says "update this skill":

1. Read the existing `SKILL.md`
2. Separate stable-core claims from version-sensitive claims
3. Update only what changed:
   - version scope
   - research cutoff
   - recent maintainer judgment
   - new breaking changes, controversies, or anti-patterns
   - whether `Confusion Pairs` need rewriting
   - whether any `Watchlist` trigger has fired
4. Do not rewrite the whole skill unless the old skeleton is fundamentally wrong

## Special Scenarios

### Scenario A: distilling a local repo

If the user gives a local project, prioritize:

- entrypoints
- core modules
- tests
- config
- recent important commits or PRs

Do not infer architecture from the README alone.

### Scenario B: distilling a stack

If the object is something like FastAPI, Rails, React, or LangGraph, you must cover:

- core abstractions
- public boundaries
- migration path
- repeated maintainer judgment
- high-frequency community failure modes

If the real object is only an adjacent implementation or substrate:

- write the mismatch explicitly
- separate object-specific judgment from transferable discipline
- do not require native features that are not actually present

### Scenario C: upgrading an existing skill

Typical failure modes in existing skills:

- voice without evidence
- style without boundaries
- values without predictive power
- sections without real objections
- judgment without stable-vs-perishable layering
- evidence without confusion warnings or update triggers

Repair those first. Cosmetic prose can wait.

## Forbidden Moves

- Do not generate bundle-thinking again
- Do not make the artifact depend on multi-file sidecars
- Do not rewrite the README and call it a skill
- Do not disguise generic best practices as object-specific judgment
- Do not omit version scope or research cutoff
- Do not omit objections or boundaries
- Do not optimize for voice at the expense of judgment density
- Do not keep evidence only in your head; compress it into evidence anchors

## Final Deliverable

The deliverable for this skill is:

- one high-density, single-file, self-contained child `SKILL.md`

It is not:

- a bundle
- a seat config pack
- a runtime contract file set
- a role card that only imitates tone
- a polished project introduction
