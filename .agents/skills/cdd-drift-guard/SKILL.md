---
name: cdd-drift-guard
description: Use when a task changes code, commands, structure, docs, or workflow in this repo and the change could stale README.md, TODO.md, docs/INDEX.md, docs/specs/*, or docs/JOURNAL.md. Keeps CDD docs aligned with implementation and applies the README scaling patterns before root docs become noisy.
---

# CDD Drift Guard

Use this skill for repo changes that affect behavior, file layout, entrypoints, operating workflow, architecture, or CDD doc topology.

## Goal

Keep the CDD docs current without turning every task into a docs rewrite, and keep root docs stable as the project grows.

## Update only what drifted

- `README.md`: project description, runbook entrypoints, setup/dev/test/build commands, and repo-level promises
- `TODO.md`: active steps, sequencing, automated checks, and UAT
- `docs/specs/blueprint.md`: architecture, invariants, interfaces, data structures, and runbook deltas
- `docs/specs/prd.md`: user-visible scope, use cases, user stories, requirements, vision
- `docs/INDEX.md`: regenerate or update when structure, entrypoints, or diagrams are stale
- `docs/JOURNAL.md`: add one compact entry for non-trivial implementation decisions

## Scaling rules

- Keep `README.md` current, it should always reflect the current status of the codebase.
- Keep `docs/specs/blueprint.md` as the stable root. When one area needs repeated detail, add a spec index there and branch into `docs/specs/<area>-definition.md`. If specs grow large, group them into domain subfolders such as `client/`, `server/`, or `ops/`, but keep `blueprint.md` as the single entrypoint.
- Keep root `TODO.md` as the entrypoint. When work gets noisy, user might split `TODO-<area>.md` and/or `TODO-next.md`. Each step must be in exactly one TODO file.
- Introduce `docs/RUNBOOK.md` when exact setup, dev, test, deploy commands, or env vars start to crowd `README.md`. Keep `README.md` as the top-level runbook entrypoint.
- Treat `docs/INDEX.md` as a generated context snapshot. Regenerate it when architecture, entrypoints, diagrams, or file inventory drift.
- Keep `docs/JOURNAL.md` high-signal only
- Archive `docs/JOURNAL.md` and `TODO.md` as it's defined on top of the files. Old material should go under `docs/archive/` instead of letting the hot file grow without bound.

## Operating heuristics

- Prefer the smallest doc edit that removes ambiguity.
- Do not rewrite stable docs just to mirror low-signal code churn.
- If a task is too small to justify doc edits, say so explicitly.
- If the repo is still in template or bootstrap state, keep updates proportional, do not invent project-specific detail, and avoid journal entries for template housekeeping unless the template contract itself materially changed.
- End with exact validation commands for any doc updates made.
