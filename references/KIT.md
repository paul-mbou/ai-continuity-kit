# AI Continuity Kit — definition

## Problem

AI coding tools do not share chat memory. Continuity must live in **git**.

## Solution (minimal)

| Layer | File(s) | Purpose | Update cadence |
|-------|---------|---------|----------------|
| Contract | `AGENTS.md` (+ `CLAUDE.md` pointer) | Non-negotiable constraints, stack, how to verify | When rules change |
| Product | `docs/PRODUCT.md` | Purpose, users, out-of-scope | When product intent shifts |
| Depth | `docs/knowledge/*` | Architecture, patterns, status | After major changes |
| Why | `docs/decisions/*` | ADRs | Per architectural decision |
| Session | `HANDOFF.md` | WIP, don’t-touch, how to validate | End of each session |
| Domain | `.agents/skills/*`, `.cursor/rules/*` | Playbooks & IDE rules | As domains grow |

## Tool compatibility

| Tool | What it reads |
|------|----------------|
| Cursor | `AGENTS.md`, `.cursor/rules/`, project skills |
| Claude Code | `CLAUDE.md` / `AGENTS.md` |
| Zed / others | Same markdown if present in repo |
| Any agent | Follow bootstrap order in `AGENTS.md` |

## Install checklist (copy-paste)

- [ ] `AGENTS.md` filled (no `{{…}}` left)
- [ ] `CLAUDE.md` points to `AGENTS.md`
- [ ] `docs/PRODUCT.md` written
- [ ] `docs/decisions/README.md` + first ADR if needed
- [ ] `HANDOFF.md` current
- [ ] `docs/knowledge/` generated or stubbed with INDEX
- [ ] Critical rules mirrored in analyzer/CI where possible
- [ ] Secrets excluded from docs

## Anti-patterns

- Putting the only truth in Cursor Memories or a single chat
- 50-page AGENTS.md (keep AGENTS short; depth → knowledge/)
- HANDOFF that duplicates architecture docs
- ADRs that describe *what* was coded instead of *why*
