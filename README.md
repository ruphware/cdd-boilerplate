# Chat Drive Development (CDD) Boilerplate

This is a tiny, documentation-first **template contract** for building with coding agents - KISS, but with consistently high-quality outcomes.

**Core values**
- **Resumable**: any agent can pick up from TODO + INDEX + JOURNAL
- **Auditable**: every step has checks + UAT
- **Safe-by-default**: PRD/Blueprint are the contract; INDEX is the context snapshot
- **Tool-agnostic**: works with a wide range of coding agents and editor/IDE integrations.

## What you get (and what you don't)

This template gives you:
- a repo-level operating contract for agents (`AGENTS.md`)
- a step-based execution plan (`TODO.md`) with **Automated checks** + **UAT** discipline
- a docs system designed for “high-density context” + change safety (`docs/*`)

This template does **not** give you:
- a tech stack, runtime, or app framework
- any bundled vendor-specific or tool-specific skill packs beyond the tiny local governance skill under `.agents/skills/`

## Human-in-the-loop contract

This repo is a workflow contract, not just a folder template.

**Humans must provide:**
- Product intent (what "good" means)
- Non-negotiable constraints
- Acceptance criteria
- Final sign-off via UAT

**Agents do best at:**
- Turning intent/specs into step plans
- Implementation + doc updates
- Producing exact validation commands
- Keeping changes small, consistent, and well-logged

**CDD step gate:** nothing is "done" until the human runs the step’s UAT and signs it off.

## Template contract

When you create a new repo from this template, keep these invariants true:

- **Required files:** `AGENTS.md`, `README.md`, `TODO.md`
- **Required docs:**
  - `docs/INDEX.md` (generated context snapshot)
  - `docs/JOURNAL.md` (stable journal entrypoint; live journal in small repos)
  - `docs/specs/prd.md` and `docs/specs/blueprint.md` (project contract)
  - `docs/prompts/PROMPT-INDEX.md` (how to regenerate `docs/INDEX.md`)
- **Optional scaled docs (create only when split journaling is active):**
  - `docs/journal/JOURNAL.md` (cross-cutting live journal)
  - `docs/journal/JOURNAL-<area>.md` (area journal aligned to `TODO-<area>.md`)
  - `docs/journal/SUMMARY.md` (condensed archive across split journals)
  - `docs/journal/archive/` (raw archived journal batches)
- **Optional scaled docs (create only when INDEX split is active):**
  - `docs/index/DIAGRAMS.md` (mermaid diagram bodies for INDEX)
  - `docs/index/INVENTORY-<area>.md` (file & API inventory bodies for INDEX; typical areas: `source`, `tests`, `other`)
- **Fully generated vs edited:**
  - Regenerate: `docs/INDEX.md` (and `docs/index/**` together when INDEX split is active)
  - Edit: `TODO.md`, `docs/specs/*`, `docs/JOURNAL.md`
  - When split journaling is active, also edit: `docs/journal/*`

## Why this works (KISS, but high-quality)

At any moment you can answer:
- What are we building? → PRD
- How is it structured? → Blueprint
- What’s next? → TODO
- What changed and why? → JOURNAL
- What exists right now? → INDEX

…and every step is small, testable, and gated by UAT.

## Quickstart 

### 1) Create repo from template

GitHub UI:
- Click **Use this template** → create a new repo.

GitHub CLI:
```bash
gh repo create <owner>/<new-repo> --template ruphware/cdd-boilerplate --private
# or --public

git clone git@github.com:<owner>/<new-repo>.git
cd <new-repo>
```

### 2) Replace template placeholders

```bash
grep -REIn "<PROJECT NAME>|YYYY-MM-DD|cdd-boilerplate" .
```

### 3) Fill the contract

- Run `TODO.md` Step 00 and:
  - Fill in:
    - `docs/specs/prd.md`
    - `docs/specs/blueprint.md`
  - Use `docs/specs/prd.md` and `docs/specs/blueprint.md` to create `TODO.md` steps + tasks.
  - Update this README.md.

### 4) Start building

```text
Review and implement Step 01
```

### 5) Regenerate `docs/INDEX.md`

```text
Open docs/prompts/PROMPT-INDEX.md and execute it verbatim.
Update docs/INDEX.md so Mermaid renders on GitHub and the file inventory matches the repo.
If INDEX split is active, regenerate the slim docs/INDEX.md and all docs/index/** siblings in the same pass.
```

## Agent boot prompt

```text
Read AGENTS.md and assume the role.
Ingest README.md, docs/specs/blueprint.md, docs/specs/prd.md to understand the project and read docs/JOURNAL.md to get up to speed with the current journal layout and implementation process.
If docs/JOURNAL.md points to split journals, continue with the matching docs/journal/JOURNAL-<area>.md and docs/journal/SUMMARY.md as needed.
Read docs/INDEX.md if present to get an overview of the codebase. If it points to docs/index/** siblings, open the relevant ones for the area you are touching.
```

## CDD Skills for Agents

This template ships one tiny project-local governance skill under `.agents/skills/`:

- `cdd-drift-guard`: keeps `README.md`, `TODO.md`, `docs/INDEX.md`, `docs/specs/*`, and `docs/JOURNAL.md` aligned when repo behavior or structure changes, applies the README’s scaling patterns before root docs get noisy, and routes split-journal notes to `docs/journal/JOURNAL.md`, `docs/journal/JOURNAL-<area>.md`, and `docs/journal/SUMMARY.md` when journals branch.

It still ships **no** tool-specific skill packs, so the template stays stable and portable.

If you want to install Agent Skills to work with this template, see:
- [ruphware/cdd-skills](https://github.com/ruphware/cdd-skills)


## How to scale when projects get bigger?

As complexity grows, keep docs predictable and let `docs/specs/blueprint.md`, root `TODO.md`, and root `docs/JOURNAL.md` route humans and agents to the right level of detail.

### Docs taxonomy (recommended)

- `docs/RUNBOOK.md`: exact dev/test/deploy commands + env vars
- `docs/specs/blueprint.md`: root spec + “Spec Index” linking to leaf specs
- `docs/specs/*-definition.md`: one subsystem per file (contracts, edge cases, tests)
- `docs/INDEX.md`: generated context snapshot (diagrams + file inventory); slim entrypoint once INDEX splits
- `docs/index/DIAGRAMS.md`: mermaid diagram bodies for INDEX when split
- `docs/index/INVENTORY-<area>.md`: file & API inventory bodies for INDEX when split
- `docs/JOURNAL.md`: live journal in small repos; stable journal entrypoint/index once journals split
- `docs/journal/JOURNAL.md`: cross-cutting / shared implementation notes when journals split
- `docs/journal/JOURNAL-<area>.md`: area journal aligned to `TODO-<area>.md`
- `docs/journal/SUMMARY.md`: condensed archive across split journals
- `docs/journal/archive/`: raw archived journal batches referenced from `SUMMARY.md`
- `docs/archive/`: archived TODO batches and single-journal archives before split mode
- `docs/prompts/PROMPT-INDEX.md`: canonical instructions to regenerate `docs/INDEX.md`

### Optional branching patterns (enable, don’t enforce)

- Specs: if `docs/specs/` gets large, branch into subfolders by domain (e.g. `client/`, `server/`, `ops/`) but keep `blueprint.md` as the single entrypoint.
- TODOs: keep root `TODO.md`, and optionally add `TODO-<area>.md` files as work splits. If you branch TODOs, consider adding an “Active Work Index” in root `TODO.md` and keeping each step in exactly one TODO file.
- Journals: if active implementation work branches into `TODO-<area>.md`, also branch the journal. Keep `docs/JOURNAL.md` as the stable entrypoint, rewrite it as a short current-state index after split activation, create `docs/journal/JOURNAL-<area>.md` for active workstreams, use `docs/journal/JOURNAL.md` for cross-cutting notes, and use `docs/journal/SUMMARY.md` only for condensed archive history. Once split journaling starts, keep it.
- INDEX: if `docs/INDEX.md` exceeds ~300 lines or its diagram/inventory sections grow unboundedly with the codebase, split it. Keep `docs/INDEX.md` as a slim entrypoint (executive summary, project snapshot, layout pointers, dependency map, glossary, footer) and move bodies into `docs/index/DIAGRAMS.md` and `docs/index/INVENTORY-<area>.md` (typical areas: `source`, `tests`, `other`). Each inventory row belongs in exactly one sibling. Regenerate the entrypoint and siblings together via `docs/prompts/PROMPT-INDEX.md`. Once INDEX split starts, keep it.

Example (minimal scalable layout):
```text
docs/
  RUNBOOK.md
  INDEX.md
  index/
    DIAGRAMS.md
    INVENTORY-source.md
    INVENTORY-tests.md
    INVENTORY-other.md
  JOURNAL.md
  archive/
  journal/
    JOURNAL.md
    JOURNAL-backend.md
    SUMMARY.md
    archive/
  prompts/PROMPT-INDEX.md
  specs/blueprint.md
  specs/<area>-definition.md
TODO.md
TODO-backend.md
```

Example (slim `docs/INDEX.md` skeleton once INDEX split is active):
````text
# Context for `<project>`

## Executive Summary
...

## Project Snapshot
- **Frameworks**: ...
- **Languages**: ...
- **Architecture**: ...

## Layout

Diagrams → `docs/index/DIAGRAMS.md`
- System Context
- Component Interaction
- (one bullet per H3 in DIAGRAMS.md)

Inventory
- `docs/index/INVENTORY-source.md` — primary source tree (`src/`, `lib/`, `apps/`)
- `docs/index/INVENTORY-tests.md` — tests and fixtures
- `docs/index/INVENTORY-other.md` — contracts, assets, scripts

## Dependency Map
```mermaid
...
```

## Glossary
- ...

## Last Generated
- ...
````

Each sibling under `docs/index/` opens with a one-line back-pointer so contributors landing there know the entrypoint:

```text
# INDEX body — Diagrams

> Body of [docs/INDEX.md](../INDEX.md) — architecture, flow, and component diagrams.
```

## License

Free-to-use-adjust-just-don't-blame-me-for-anything-licence. _Peace._ ✌️

____

[![CDD Project](https://img.shields.io/badge/CDD-Project-ecc569?style=flat-square&labelColor=0d1a26)](https://github.com/ruphware/cdd-boilerplate)
<sup>This repo follows the [`CDD Project`](https://github.com/ruphware/cdd-boilerplate) + [`CDD Skills`](https://github.com/ruphware/cdd-skills) workflow with the local [`AGENTS.md`](./AGENTS.md) contract.</sup>
