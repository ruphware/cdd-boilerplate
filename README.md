# agentic-boilerplate

A GitHub **template repository** for agentic / Chat‑Driven‑Development (CDD) workflows.

## What you get

This template standardizes the minimum set of files that make a repo easy to operate with coding agents:

- `AGENTS.md` — the **agent prompt** for this repo (instructions for coding agents; humans can read it, but it’s written for agents)
- `TODO.md` — step-based plan; **each step should include automated checks + UAT**
- `docs/specs/*` — PRD/Blueprint/definition specs (the contract)
- `docs/INDEX.md` — periodically generated high-density repo context (architecture + inventory + diagrams)
- `docs/prompts/*` — prompts used for repo maintenance (includes INDEX refresh prompt)
- `docs/JOURNAL.md` — high-signal dev journal / ADR log with strict archive rules

## Quickstart (new project)

### GitHub UI
- Click **Use this template** → create a new repo.

### GitHub CLI
```bash
gh repo create <owner>/<new-repo> --template ruphware/agentic-boilerplate --private
# or --public
```

## RENAME CHECKLIST (DO THIS FIRST)

Right after templating:

1) **Update identity strings**
- `README.md` title + description
- `docs/specs/prd.md` and `docs/specs/blueprint.md`: replace `<PROJECT NAME>` and `YYYY-MM-DD`

2) **Search for template placeholders**
```bash
rg -n "<PROJECT NAME>|YYYY-MM-DD|agentic-boilerplate" .
```

3) **Regenerate repo context**
- Update `docs/INDEX.md` to match the real codebase using `docs/prompts/PROMPT-INDEX.md`.

## Agent workflow (boot prompt)

When starting a coding agent in a repo created from this template, use this boot sequence:

- Ingest `AGENTS.md` and assume the role.
- Read `README.md`, `docs/INDEX.md`, `docs/specs/blueprint.md` to understand the project.
- See the top of `docs/JOURNAL.md` for implementation process and details.

## INDEX refresh workflow

When regenerating `docs/INDEX.md`:

- Ingest `docs/prompts/PROMPT-INDEX.md` and execute it **verbatim**.
- Use the correct tools to count LOC and fulfill all requirements.
- Update diagrams and keep Mermaid syntax GitHub-compatible.

## License

MIT (see `LICENSE`).
