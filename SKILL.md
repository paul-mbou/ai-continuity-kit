---
name: ai-continuity-kit
description: >-
  Install and maintain a portable AI continuity kit so any coding agent (Cursor,
  Claude Code, Zed, Copilot, Aider, etc.) can onboard a project deeply without
  breaking constraints. Use when starting a new repo, migrating between AI tools,
  setting up AGENTS.md / HANDOFF / ADRs, or when the user asks for multi-IDE AI
  continuity, handoff docs, or project memory for agents.
---

# AI Continuity Kit

Make the **repo** the shared brain. Chats and IDE memories are ephemeral; this kit is not.

## When to use

- New project setup (“prepare this repo for any AI”)
- Switching tools (Cursor → Claude Code / Zed / …)
- User asks for AGENTS.md, HANDOFF, ADR, or continuity docs
- Before a long multi-session feature so the next agent can continue safely

## Target layout (every repo)

```text
AGENTS.md                 # Single entry contract (all tools)
CLAUDE.md                 # Pointer → AGENTS.md (Claude Code)
HANDOFF.md                # Ephemeral session state (update end of day)
docs/
  PRODUCT.md              # What the product is / is not
  decisions/              # ADRs (why we chose X)
    README.md
    0000-template.md
    NNNN-short-title.md
  knowledge/              # Deep onboarding (via knowledge-memory-gen)
    INDEX.md
    …
.cursor/rules/            # Optional Cursor-specific hard rules (link to AGENTS)
.agents/skills/           # Project skills (domain playbooks)
```

## Workflow

### 1. Install (new or empty kit)

1. Copy files from this skill’s `templates/` into the project root (do not overwrite filled docs without asking).
2. Fill placeholders (`{{PROJECT_NAME}}`, stack, hard rules).
3. Write a real `docs/PRODUCT.md` (5–15 lines is enough to start).
4. Leave `docs/knowledge/` stubs; tell the user to run **knowledge-memory-gen** for depth, or generate it now if asked.
5. Create `HANDOFF.md` with current WIP or “clean slate”.

### 2. Maintain (every significant session)

| Event | Action |
|-------|--------|
| End of coding session | Update `HANDOFF.md` |
| Architectural choice | Add ADR under `docs/decisions/` |
| New hard constraint | Add to `AGENTS.md` **and** enforce in lint/CI if possible |
| Big feature / refactor | Refresh `docs/knowledge/` via knowledge-memory-gen |
| Tool switch tomorrow | Point next agent: read `AGENTS.md` → `HANDOFF.md` → `docs/PRODUCT.md` → `docs/knowledge/INDEX.md` |

### 3. Agent bootstrap order (always)

When taking over a project, read in this order:

1. `AGENTS.md`
2. `HANDOFF.md`
3. `docs/PRODUCT.md`
4. `docs/knowledge/INDEX.md` (then only the paths it recommends)
5. Relevant ADRs if touching architecture
6. Project skills under `.agents/skills/` or `.cursor/skills/` for the domain at hand

Do **not** invent product rules that contradict these files.

## Hard principles

1. **One contract** — `AGENTS.md` is the portable source of truth; tool-specific files only point to it.
2. **Executable > prose** — prefer lint/CI/tests for rules that must never break.
3. **Decisions are dated** — ADRs; never “we discussed in chat”.
4. **HANDOFF is short** — max ~1 screen; deep context lives in `docs/knowledge/`.
5. **No secrets** in these files (keys, tokens, `.env` values).

## Related skills

- `knowledge-memory-gen` — fills `docs/knowledge/` from the real codebase
- Project design-system / domain skills — domain hard rules

## Templates

See [templates/](templates/) and the overview in [references/KIT.md](references/KIT.md).
