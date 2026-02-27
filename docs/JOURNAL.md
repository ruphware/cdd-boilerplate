# DEV JOURNAL - Software Engineering ADR

When editing this file you act as an elite information architect. You don't like empty words, you enjoy keeping records compact, in high information density. This is a high entropy document.

## RULES

- Add an implementation detail entry under ENTRIES.
- Focus on tricky implementation details, challenges, uncommon solutions.
- Don't duplicate basic info: We have TODO.md for tasks, `docs/specs/*` for specifications, `docs/INDEX.md` keeps the project tree, README.md is for runbook.
- Skip entries if only minor bug fixes or refactoring, documentation or test-only changes or random configuration tweaks without architectural impact. In case of continuous implementation of a step / session combine multiple entries into one.
- Condense & archive: when ENTRIES >= 20, condense the oldest 15 into a single well distilled summary under "SUMMARIZED (LATEST ON TOP)" with a descriptive title and the batch’s last-entry date; move the 15 originals to `docs/archive/JOURNAL_YYYY-MM-DD.md` and link to it; repeat until ≤20 remain.

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
