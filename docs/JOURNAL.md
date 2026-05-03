# DEV JOURNAL - Software Engineering ADR

> Live journal in single-journal mode.
> Once active implementation work branches into `TODO-<area>.md`, enable split-journal mode: convert this file into the stable journal entrypoint/index and move live entries into `docs/journal/`.

When editing this file you act as an elite information architect. You don't like empty words, you enjoy keeping records compact, in high information density. This is a high entropy document.

## RULES

- Add an implementation detail entry under ENTRIES while this file is the live journal.
- Focus on tricky implementation details, challenges, uncommon solutions.
- Don't duplicate basic info: We have TODO.md for tasks, `docs/specs/*` for specifications, `docs/INDEX.md` keeps the project tree, README.md is for runbook.
- If split-journal mode is enabled, stop writing live entries here. Use `docs/journal/JOURNAL-<area>.md` for work tied to `TODO-<area>.md`, use `docs/journal/JOURNAL.md` only for repo-wide or cross-cutting notes, and read `docs/journal/SUMMARY.md` when older condensed context matters.
- `TODO-next.md` is backlog and does not require `JOURNAL-next.md`.
- Keep one implementation session in exactly one hot journal file unless the work is truly cross-cutting.
- Do not duplicate the same journal entry across multiple journal files.
- Skip entries if only minor bug fixes or refactoring, documentation or test-only changes or random configuration tweaks without architectural impact. In case of continuous implementation of a step / session combine multiple entries into one.
- In single-journal mode, when ENTRIES >= 20, condense the oldest 15 into a single well distilled summary under "SUMMARIZED (LATEST ON TOP)" with a descriptive title and the batch’s last-entry date; move the 15 originals to `docs/archive/JOURNAL_YYYY-MM-DD.md` and link to it; repeat until ≤20 remain.
- Once split-journal mode is enabled, keep the split topology. Do not auto-collapse back to a single hot journal. Each hot journal should condense old entries into `docs/journal/SUMMARY.md` with the source journal and date range, then move raw archived batches under `docs/journal/archive/`.

## TRANSITION TO SPLIT MODE

- Keep this file as the live journal until any active implementation `TODO-<area>.md` exists.
- On split activation, move existing live entries from this file into `docs/journal/JOURNAL.md` by default, then create matching `docs/journal/JOURNAL-<area>.md` files for active workstreams.
- Rewrite this file as a short journal entrypoint/index after split activation.

**Format:**

Only use what's needed.

```
[YYYY-MM-DD HH:MM UTC]
Context: (task or area, include relevant background information, constraints, and forces at play)
Decisions: (key choices & why, clearly state the decision and the approach)
Findings: (surprises, pitfalls, dead ends)
Risks: (what might break, monitoring hooks)
Important: (add especially important remarks here; can be omitted if there aren't any)
```

## ENTRIES (LATEST ON TOP)

## SUMMARIZED (LATEST ON TOP)
