# DEV JOURNAL - Software Engineering ADR

> Single-journal mode: this file is the live journal.
> Split-journal mode: this file becomes the stable journal entrypoint/index for active files under `docs/journal/`.

Keep this file compact and high-signal.

## RULES

- In single-journal mode, add implementation detail entries under ENTRIES.
- Focus on tricky implementation details, challenges, and uncommon solutions. Do not repeat TODO, spec, INDEX, or runbook material.
- Skip minor bug fixes, refactors, doc-only/test-only work, or low-impact config tweaks. Combine continuous work on one step/session into one entry.
- Keep one implementation session in exactly one hot journal file unless the work is truly cross-cutting.
- Do not duplicate the same journal entry across multiple journal files.
- Split-journal mode starts when any active implementation `TODO-<area>.md` exists. Stop writing live entries here, move existing live entries to `docs/journal/JOURNAL.md`, rewrite this file as a short current-state index, use `docs/journal/JOURNAL-<area>.md` for area work, use `docs/journal/JOURNAL.md` only for repo-wide or cross-cutting notes, use `docs/journal/SUMMARY.md` for condensed archive history, and keep split mode once enabled.
- Archive rules: in single-journal mode, when ENTRIES >= 20, condense the oldest 15 into "SUMMARIZED (LATEST ON TOP)", move the raw entries to `docs/archive/JOURNAL_YYYY-MM-DD.md`, and link to the archive. In split-journal mode, condense old entries from hot journals into `docs/journal/SUMMARY.md` with source journal and date range, then move raw batches to `docs/journal/archive/`.

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


