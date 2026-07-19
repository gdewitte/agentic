# Agentic

Personal agent skills for clarifying ambiguous work, writing specs and plans, implementing safely, refactoring, testing, reviewing, frontend polish, visual explanations, and repository harnesses.

This README lists the user-facing skill interface.

## Skills

| Skill | Use | Works with |
|---|---|---|
| `clarify` | Turns a vague or messy ask into a clean, self-contained prompt. | None |
| `commit-message` | Drafts concise commit messages with a conventional header and optional structured body. | None |
| `design-doc` | Writes a lightweight architecture design doc before implementation. | None |
| `explain-visually` | Creates a visual HTML explanation of a repo, spec, PR, architecture, or concept. | `frontend-skill`, `uncodixfy` |
| `frontend-skill` | Guides visually strong landing pages, websites, apps, prototypes, demos, and game UIs. | None |
| `grill-me` | Runs a grilling session through an invocable wrapper. | `grilling` |
| `harness` | Audits and improves a repo's agent instructions, commands, state, environment, and feedback loops. | None |
| `implement` | Executes approved or decision-complete work, choosing the right implementation mode and verification path. | `tdd`; `frontend-skill`, `uncodixfy` when frontend |
| `plan` | Breaks a spec, brief, or request into agent-sized tasks or a self-contained implementation plan. | None |
| `refactor` | Simplifies existing code without changing behavior. | None |
| `spec` | Writes requirements and technical design before coding. | None |
| `uncodixfy` | Removes generic AI UI patterns from frontend work. | None |

## References

- [Matt Pocock skills](https://github.com/mattpocock/skills)
- [Owain Lewis](https://github.com/owainlewis/)
- [Uncodixfy](https://github.com/cyxzdev/Uncodixfy)

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
