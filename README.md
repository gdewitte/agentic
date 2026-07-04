# Agentic

> Personal agent skills for day-to-day coding, planning, clarification, refactoring, execution plans, and frontend work.

## Skills

| Skill | What it does | Deps |
|---|---|---|
| `clarify` | Turns a vague or messy ask into a clean, self-contained prompt. | None |
| `commit-message` | Drafts concise commit messages with a conventional header and optional structured body. | None |
| `design-doc` | Writes a lightweight architecture design doc before implementation. | None |
| `execplan-authoring` | Creates or updates self-contained ExecPlans for complex changes. | `frontend-skill` |
| `explain-visually` | Creates a visual HTML explanation of a repo, spec, PR, architecture, or concept. | `frontend-skill`, `uncodixfy` |
| `spec` | Writes requirements and technical design before coding. | None |
| `plan` | Breaks a spec, brief, or request into agent-sized tasks. | None |
| `refactor` | Simplifies existing code without changing behavior. | None |
| `frontend-skill` | Guides visually strong landing pages, websites, apps, prototypes, demos, and game UIs. | None |
| `uncodixfy` | Removes generic AI UI patterns from frontend work. | None |

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
npx skills add gdewitte/agentic --skill frontend-skill
```

Install all skills to every detected agent:

```bash
npx skills add gdewitte/agentic --all
```

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
