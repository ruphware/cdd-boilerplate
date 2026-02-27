# Chat‑Driven Development (CDD)

This repo (`ruphware/cdd-boilerplate`) is the **CDD template contract**: the docs system + operating rules you want in every agentic repo.

The **actual Codex skills** live in a separate distribution repo:
- `ruphware/cdd-skills`

The skills are **explicit-only**: they will never trigger automatically; you must invoke them as `$cdd-ship-step` / `$cdd-refresh-index`.

---

## Repos and responsibilities

### Repo 1: `ruphware/cdd-boilerplate` (GitHub template)
Contains:
- `AGENTS.md` (repo operating contract)
- `TODO.md` (step plan discipline)
- `docs/` system (`INDEX.md`, `JOURNAL.md`, specs, prompts)
- `cdd-skill.md` (this doc: how to install skills + how to use CDD)

### Repo 2: `ruphware/cdd-skills` (distribution)
Contains:
- `.agents/skills/cdd-ship-step/...`
- `.agents/skills/cdd-refresh-index/...`
- `scripts/install.sh` (installs skills into `~/.agents/skills/`)

---

## Install the skills (Codex)

### Option A (recommended): global install
This makes the skills available in **any repo**.

```bash
git clone git@github.com:ruphware/cdd-skills.git ~/Workspace/cdd-skills
cd ~/Workspace/cdd-skills
./scripts/install.sh
```

By default this copies the skill folders into:
- `~/.agents/skills/`

### Option B: custom install targets
`install.sh` supports multiple targets:

```bash
./scripts/install.sh --target ~/.agents/skills --target ~/.claude/skills
```

(Only `~/.agents/skills` is guaranteed/verified for Codex. Other agent paths may vary by tool/version.)

---

## Using CDD (day-to-day)

### 1) Use the template contract
When starting a new project, create it from the GitHub template `ruphware/cdd-boilerplate`.

Operate the repo using:
- `AGENTS.md` (how the agent should behave)
- `TODO.md` (steps; every step includes Automated checks + UAT)
- `docs/prompts/PROMPT-INDEX.md` (how to regenerate `docs/INDEX.md`)

### 2) Invoke skills explicitly
Interactive Codex:
- Run `/skills` or type `$`, then choose:
  - `$cdd-ship-step`
  - `$cdd-refresh-index`

Non-interactive:
```bash
codex exec --full-auto '$cdd-ship-step Implement TODO Step NN. Keep changes minimal. Include Automated checks + UAT.'
codex exec --full-auto '$cdd-refresh-index Refresh docs/INDEX.md using docs/prompts/PROMPT-INDEX.md. Only change docs/INDEX.md.'
```

---

## Safety / publishing

It is safe to push both repos to GitHub:
- `cdd-boilerplate` contains only templates + docs
- `cdd-skills` contains only skill definitions + install script

No secrets should ever be stored in either repo.
