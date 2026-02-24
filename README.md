# agentic-boilerplate

A reusable, opinionated template set for **agentic / CDD-style software development**.

This repo exists to make new projects immediately “agent-ready” by standardizing:
- `AGENTS.md` — how coding agents should operate in this repo
- `TODO.md` — execution plan / backlog
- `docs/INDEX.md` — high-density architecture/context snapshot
- `docs/prompts/PROMPT-INDEX.md` — how to regenerate `docs/INDEX.md`
- `docs/specs/*` — PRD/Blueprint/specs as the canonical contract
- `docs/JOURNAL.md` — decision log

## Quickstart (for a new project)

1. Copy these files into the root of your new repo:
   - `AGENTS.md`
   - `TODO.md`
   - `docs/` (everything)

2. Edit `README.md` and `docs/specs/` to reflect the project.

3. Generate/update `docs/INDEX.md` using `docs/prompts/PROMPT-INDEX.md`.

## Structure

- `AGENTS.md` — CDD rules for agents and humans
- `TODO.md` — task list; should reference specs and runbook
- `docs/INDEX.md` — architecture overview + inventory + diagrams
- `docs/prompts/` — prompts used to generate/refresh documentation
- `docs/specs/` — PRD + blueprint + definition specs
- `docs/JOURNAL.md` — implementation log / ADRs

## Notes

- This repo contains **templates** (not a framework). It should stay language-agnostic.
- If you want language-specific additions, add them under `templates/<lang>/...`.
