# TODO

> Project: agentic-boilerplate — templates for agentic / CDD development.

## Goals

- Provide copy-paste templates that make a repo immediately **agent-ready**.
- Keep templates language-agnostic by default.
- Provide optional language overlays under `templates/<lang>/`.

## Tasks

### 1) Baseline template set
- [x] Create root `AGENTS.md` (CDD rules)
- [x] Create root `README.md`
- [x] Create `docs/` layout

### 2) Documentation templates
- [x] Add `docs/prompts/PROMPT-INDEX.md` (how to generate `docs/INDEX.md`)
- [x] Add `docs/INDEX.md` starter
- [x] Add `docs/JOURNAL.md` starter
- [x] Add `docs/specs/prd.md` and `docs/specs/blueprint.md` templates

### 3) Make it usable in other repos
- [ ] Add a short "How to adopt" section + checklist to README
- [ ] Add a `templates/base/` directory mirroring the recommended baseline
- [ ] Add `templates/typescript/` and `templates/python/` overlays (optional)

### 4) Governance
- [ ] Decide license (MIT vs private)
- [ ] Decide whether to include CI templates (GitHub Actions)
- [ ] Decide whether to include a standard `.gitignore` / `.editorconfig`

## Notes

- Keep content opinionated but not overly specific (no OrgPlot/DataGobbler-specific terms).
- Templates should be compatible with the existing Myelin pattern:
  - `AGENTS.md`
  - `TODO.md`
  - `docs/INDEX.md`
  - `docs/prompts/PROMPT-INDEX.md`
  - `docs/specs/*`
  - `docs/JOURNAL.md`
