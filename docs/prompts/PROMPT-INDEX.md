ROLE: You are a diligent assistant that prepares **Chat-Driven-Development (CDD)-ready documentation** for a given repository.

GOAL: Generate or update a perfectly formatted `docs/INDEX.md` file by following a two-phase process of analysis and generation, with strict quality assurance. The INDEX should be a comprehensive, high-level overview of the project's architecture, components, and user flows.

──────────────────────────────────────────────
Phase 1: Analysis & Code Comprehension
──────────────────────────────────────────────

1) Overview
- Read `README.md`, `TODO.md` to understand the project and its progress.
- Read `docs/specs/blueprint.md` and connected specs.
- If `docs/INDEX.md` already exists: treat this as an **update** task.

2) Identify core language & frameworks
- Determine primary languages and frameworks.
- Scan dependency files: `package.json`, `requirements.txt`, etc.

3) Map the codebase
- Enumerate directories.
- Identify main source directories (e.g. `src`, `apps`, `packages`).

4) Read source files
- Focus entrypoints, config, and core business logic.
- Build a file inventory table with LOC.
- Tag files >760 LOC as `refactor-candidate`.
- Do this separately for app source vs tests.

5) Extract architectural components
- Entrypoints/processes
- Core services/logic
- Data models
- API layers
- Client-side logic
- Integrations

──────────────────────────────────────────────
Phase 2: Diagram & Content Generation
──────────────────────────────────────────────

Generate 2–4 mermaid diagrams as appropriate:
- System Context (C4 L1)
- User Flow / Sequence Diagram
- Component Interaction (C4 L3)
- Dependency Map

Mermaid rules (GitHub-safe):
- Node IDs must be alphanumeric/hyphen only.
- Use consistent arrows (prefer `-->`).
- No complex shapes.
- Use `<br/>` for line breaks.

──────────────────────────────────────────────
Quality Assurance (self-grade)
──────────────────────────────────────────────

Grade yourself 0–12. If <11.5, repeat analysis+generation.

Checklist:
1. Executive summary + project snapshot present (+1)
2. File inventory with LOC (+2)
3. Refactor candidates flagged (+1)
4. Markdown structure correct (+1)
5. System context diagram (+1)
6. User flow diagram (+1)
7. Component interaction diagram (+1)
8. Dependency map (+1)
9. Mermaid syntax correct (+1)
10. Glossary + Last Generated present (+1)
11. High information density (+1)

──────────────────────────────────────────────
TEMPLATE
──────────────────────────────────────────────

# Context for `{{PROJECT_NAME}}`

## Executive Summary
...

## Project Snapshot
- **Frameworks**: ...
- **Languages**: ...
- **Key Libraries**: ...
- **Architecture**: ...

## Diagrams

### System Context
```mermaid
...
```

## File & API Inventory

| Path | Role | LOC | Key Tags, Symbols, Names |
| :--- | :--- | --: | :----------------------- |
| ... | ... | ... | ... |

## Dependency Map
```mermaid
...
```

## Glossary
- ...

## Last Generated
- **Lines of Code (App/Tests)**: ...
- **Last Commit Msg**: ...
- **Timestamp**: ...
- **LLM Model**: ...
- **Grade**: ...
