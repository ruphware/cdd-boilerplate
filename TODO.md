# TODO

> Active execution plan (steps). Gate completion on Automated checks + UAT.

Reference: `docs/specs/prd.md` and `docs/specs/blueprint.md`.
Archive: move completed steps to `docs/archive/TODO_YYYY-MM-DD.md` when noisy.

---

## Step 00 — project setup

Goal:
- Establish the project contract (PRD + Blueprint) and a project-specific README.

Constraints:
- Keep `README.md` as the runbook entrypoint for setup, development, test, and build usage.
- Keep `docs/specs/prd.md`, `docs/specs/blueprint.md`, and `README.md` aligned on the same project scope, terminology, and current repo reality.
- Preserve any imported source material or existing repo-specific context while replacing boilerplate placeholders.

Tasks:
- [ ] `docs/specs/prd.md`: replace boilerplate placeholders and record the real project goals, scope, acceptance criteria, and open questions.
- [ ] `docs/specs/blueprint.md`: replace boilerplate placeholders and record the real architecture, invariants, contracts, and runbook details.
- [ ] `README.md`: rewrite the runbook to match the PRD and Blueprint and reflect the actual repo entrypoints, setup flow, and current development workflow.

Implementation notes:
- Resolve placeholders before adding new product or architecture detail so the contract reads as repo-specific from the start.
- Translate product intent into concrete repo contracts, commands, file paths, and operating assumptions; do not leave essential setup detail only in chat.
- If the repo already contains source material or legacy docs, preserve that context and reconcile terminology rather than overwriting it blindly.

Automated checks:
- test -f docs/specs/prd.md && test -f docs/specs/blueprint.md && test -f README.md
- ! grep -REIn "<PROJECT NAME>|YYYY-MM-DD" docs/specs/*.md README.md

UAT:
- [ ] Confirm no placeholders remain in `docs/specs/prd.md`, `docs/specs/blueprint.md`, or `README.md`.
- [ ] Confirm `README.md` reflects the same scope, terminology, and runbook flow as the PRD and Blueprint.
- [ ] Confirm a new contributor can locate setup, development, and test entrypoints from `README.md` without relying on chat context.

---

## Step template (copy/paste)

```md
## Step <NN> — <title>

Goal:
- <one-sentence outcome>

Constraints:
- <technical, sequencing, migration, rollback, or evidence constraint that must shape implementation>
- <must-preserve invariant, compatibility rule, or operating assumption>

Tasks:
- [ ] <boundary>: <exact change> so <artifact or behavior>; preserve <invariant or evidence requirement>
- [ ] <boundary>: <exact change> so <artifact or behavior>; keep <compatibility, migration, or rollback constraint>

Implementation notes:
- <file or symbol hints, interface or schema changes, ordering constraints, migration notes, rollback notes, or proof requirements>

Automated checks:
- <exact command>
- <exact command>

UAT:
- [ ] <manual or role-based verification>
- [ ] <end-to-end behavior or acceptance proof>
```
