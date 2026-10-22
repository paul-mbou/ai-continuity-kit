# AGENTS.md — {{PROJECT_NAME}}

> Portable contract for **any** coding agent (Cursor, Claude Code, Zed, Copilot, …).
> Read this first. Then `HANDOFF.md`, then `docs/PRODUCT.md`, then `docs/knowledge/INDEX.md`.

## Product (one sentence)

{{ONE_SENTENCE_PRODUCT}}

## Stack

| Layer | Choice |
|-------|--------|
| Language / framework | {{STACK}} |
| State / routing / backend | {{STATE_ROUTING_BACKEND}} |
| UI / design system | {{UI_SYSTEM}} |

## Hard rules (do not violate)

1. {{HARD_RULE_1}}
2. {{HARD_RULE_2}}
3. {{HARD_RULE_3}}
4. Prefer existing patterns in the codebase over inventing new ones.
5. Never commit secrets (`.env`, keys, tokens).

## Layout map

```text
{{LAYOUT_MAP}}
```

## How to verify before claiming done

```bash
{{VERIFY_COMMANDS}}
```

## Where deeper truth lives

| Need | Path |
|------|------|
| Product intent | `docs/PRODUCT.md` |
| Architecture & conventions | `docs/knowledge/` (start at `INDEX.md`) |
| Why we chose X | `docs/decisions/` |
| Current WIP / don’t-touch | `HANDOFF.md` |
| Domain playbooks | `.agents/skills/`, `.cursor/rules/` |

## Bootstrap order (mandatory)

1. This file  
2. `HANDOFF.md`  
3. `docs/PRODUCT.md`  
4. `docs/knowledge/INDEX.md` → only the sections relevant to the task  
5. Matching skill/rule for the domain (UI, payments, DB, …)

## Out of scope for agents

{{OUT_OF_SCOPE}}
