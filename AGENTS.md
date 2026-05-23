# Working in Agentic

Agentic is a personal collection of reusable agent skills. It packages clear, focused workflows for clarifying vague asks, writing design docs and specs, planning work, refactoring safely, and building polished Svelte frontends.

If you are an AI agent working in this repo, follow this guidance.

## The Flow

Use `clarify` when a request is vague, multi-part, voice-dictated, or needs to become a reusable prompt before execution.

Use `design-doc -> spec -> plan` for changes with ambiguous architecture, tradeoffs, or cross-cutting concerns. Use `spec -> plan` for changes that touch contracts, behavior, invariants, or multiple files. Skip stages only when explicitly told to or when the change is trivial and decision-complete.

Use `refactor` when existing code or skill text needs cleanup without behavior changes. Use `frontend-svelte` when the task is specifically about Svelte or SvelteKit interface work.

Exploration is allowed without creating docs or issue tracker entries. Do not manufacture fake specs, plans, or issues for spikes.

## Skills

- `clarify`: turn a vague or messy ask into a clean, self-contained prompt.
- `design-doc`: write a lightweight architecture design doc before implementation when the design is ambiguous.
- `spec`: write the technical design before coding.
- `plan`: break a spec, brief, or request into agent-sized tasks.
- `refactor`: simplify changed code without changing behavior.
- `frontend-svelte`: design and build distinctive, production-grade Svelte interfaces.

## Guidance

- Keep each skill directory self-contained under `skills/<skill-name>/`.
- The skill entrypoint is always `skills/<skill-name>/SKILL.md`.
- Preserve YAML front matter, including `name`, `description`, and `author`.
- Prefer small, readable skill instructions over broad frameworks or duplicated policy.
- If a skill depends on supporting files, keep them inside that skill directory.
- If a task, spec, plan, or prompt is wrong, stop and update it. Do not push through.
- Density over length.

## Out of Scope

Agentic is not an issue tracker, release process, or full software delivery framework. It is a curated skill library for agent workflows. That's the entire job.
