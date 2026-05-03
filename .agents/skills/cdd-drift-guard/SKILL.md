---
name: cdd-drift-guard
description: Use when a task changes code, commands, structure, docs, or workflow in this repo and may leave README.md, TODO.md, TODO-<area>.md, docs/INDEX.md, docs/specs/*, docs/JOURNAL.md, or docs/journal/* out of date. Keep CDD docs aligned with implementation and route journaling correctly in single or split mode.
---

# CDD Drift Guard

Use for changes that affect behavior, layout, entrypoints, workflow, architecture, or CDD doc structure.

## Update only what drifted

- `README.md` — project description, top-level entrypoints, setup/dev/test/build commands, repo guarantees
- `TODO.md` — root execution entrypoint, active work index, sequencing, automated checks, UAT
- `TODO-<area>.md` — area-specific execution steps when work is split
- `docs/specs/blueprint.md` — architecture, invariants, interfaces, data structures, operational changes
- `docs/specs/prd.md` — user-visible scope, use cases, user stories, requirements, vision
- `docs/INDEX.md` — regenerate from `docs/prompts/PROMPT-INDEX.md` when structure, entrypoints, diagrams, or file inventory drift
- `docs/JOURNAL.md` — stable journal entrypoint; live journal in single-journal mode
- `docs/journal/JOURNAL.md` — cross-cutting journal when work is split
- `docs/journal/JOURNAL-<area>.md` — area journal aligned to `TODO-<area>.md`
- `docs/journal/SUMMARY.md` — condensed archive across split journals

## Scaling rules

- Keep `README.md` current. It should describe current reality first; future direction can stay brief.
- Keep `docs/specs/blueprint.md` as the root spec. Add a spec index there before branching into `docs/specs/<area>-definition.md` or domain subfolders such as `client/`, `server/`, or `ops/`.
- Keep root `TODO.md` as the entrypoint. Split into `TODO-<area>.md` and/or `TODO-next.md` only when needed. Each step belongs in exactly one TODO file.
- When any active implementation `TODO-<area>.md` exists, enable split-journal mode. Keep `docs/JOURNAL.md` as the stable journal entrypoint, create `docs/journal/`, move the live journal to `docs/journal/JOURNAL.md`, and create matching `docs/journal/JOURNAL-<area>.md` files for active workstreams. `TODO-next.md` is backlog and does not require `JOURNAL-next.md`.
- Once split-journal mode starts, keep it. Do not auto-collapse back to a single hot journal.
- Use `docs/journal/JOURNAL.md` only for repo-wide or cross-cutting notes. Area-specific notes belong in exactly one matching `docs/journal/JOURNAL-<area>.md`.
- Introduce `docs/RUNBOOK.md` when exact commands or env vars crowd `README.md`; `README.md` stays the top-level runbook entrypoint.
- Treat `docs/INDEX.md` as a generated context snapshot. Regenerate it when architecture, entrypoints, diagrams, or file inventory drift.
- If journals are not split, keep `docs/JOURNAL.md` high-signal and follow its single-file archive rule under `docs/archive/`.
- If journals are split, archive hot journals through `docs/journal/SUMMARY.md` and move raw archived batches under `docs/journal/archive/`.

## Operating rules

- Prefer the smallest doc edit that removes ambiguity.
- Do not rewrite stable docs to mirror low-signal code churn.
- One implementation session belongs in exactly one hot journal file unless the work is truly cross-cutting.
- Do not duplicate the same journal entry across multiple journal files.
- If no doc change is justified, say so explicitly.
- In template/bootstrap state, keep updates proportional, do not invent project-specific detail, and do not precreate split journal files before split mode is active.
- End by stating: changed docs, checked-but-unchanged docs, and exact validation commands.
