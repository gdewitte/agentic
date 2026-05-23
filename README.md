# Agentic

> Personal agent skills for day-to-day coding, planning, clarification, refactoring, and Svelte frontend work.

## Skills

| Skill | What it does |
|---|---|
| `clarify` | Turns a vague or messy ask into a clean, self-contained prompt. |
| `design-doc` | Writes a lightweight architecture design doc before implementation. |
| `spec` | Writes requirements and technical design before coding. |
| `plan` | Breaks a spec, brief, or request into agent-sized tasks. |
| `refactor` | Simplifies existing code without changing behavior. |
| `frontend-svelte` | Builds distinctive, production-grade Svelte interfaces. |

## Install

Install with the open `skills` CLI:

```bash
npx skills add gdewitte/agentic
```

Install globally for Codex:

```bash
npx skills add gdewitte/agentic -g -a codex
```

Install one skill:

```bash
npx skills add gdewitte/agentic --skill frontend-svelte
```

Install all skills to every detected agent:

```bash
npx skills add gdewitte/agentic --all
```

## Codex

For Codex's native local setup flow, use `$skill-installer` and ask it to install skills from:

```text
https://github.com/gdewitte/agentic
```

Codex should detect newly installed skills automatically. Restart Codex if a skill does not appear.

This repository is currently a skills repository, not a Codex plugin marketplace. Automatic Codex plugin marketplace installation would require adding plugin/marketplace metadata before using `codex plugin marketplace add`.

## Update

```bash
npx skills update
```

## Add A Skill

Create a directory under `skills/` with a `SKILL.md` file:

```markdown
---
name: skill-name
description: "What this skill does and when to use it."
---

# Skill instructions
```
