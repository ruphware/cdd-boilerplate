---
name: cdd-drift-guard
description: Use when a task changes code, commands, structure, docs, or workflow in this repo and may leave README.md, TODO.md, docs/INDEX.md, docs/specs/*, or docs/JOURNAL.md out of date. Keep CDD docs aligned with implementation and apply the README scaling rules before root docs get noisy.
---

# CDD Drift Guard

Use for changes that affect behavior, layout, entrypoints, workflow, architecture, or CDD doc structure.

## Update only what drifted

- `README.md` — project description, top-level entrypoints, setup/dev/test/build commands, repo guarantees
- `TODO.md` — active steps, sequencing, automated checks, UAT
- `docs/specs/blueprint.md` — architecture, invariants, interfaces, data structures, operational changes
- `docs/specs/prd.md` — user-visible scope, use cases, user stories, requirements, vision
- `docs/INDEX.md` — regenerate from `docs/prompts/PROMPT-INDEX.md` when structure, entrypoints, diagrams, or file inventory drift
- `docs/JOURNAL.md` — add one compact entry for non-trivial implementation decisions

## Scaling rules

- Keep `README.md` current. It should describe current reality first; future direction can stay brief.
- Keep `docs/specs/blueprint.md` as the root spec. Add a spec index there before branching into `docs/specs/<area>-definition.md` or domain subfolders such as `client/`, `server/`, or `ops/`.
- Keep root `TODO.md` as the entrypoint. Split into `TODO-<area>.md` and/or `TODO-next.md` only when needed. Each step belongs in exactly one TODO file.
- Introduce `docs/RUNBOOK.md` when exact commands or env vars crowd `README.md`; `README.md` stays the top-level runbook entrypoint.
- Keep `docs/JOURNAL.md` high-signal. Follow the archive rule declared in each file and move archived material under `docs/archive/`.

## Operating rules

- Prefer the smallest doc edit that removes ambiguity.
- Do not rewrite stable docs to mirror low-signal code churn.
- If no doc change is justified, say so explicitly.
- In template/bootstrap state, keep updates proportional and do not invent project-specific detail.
- End by stating: changed docs, checked-but-unchanged docs, and exact validation commands.
