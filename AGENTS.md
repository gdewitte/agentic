# Working in Agentic

Agentic is a personal collection of reusable agent skills. It packages clear, focused workflows for clarifying vague asks, writing design docs and specs, authoring execution plans, planning work, refactoring safely, and building polished frontend experiences.

If you are an AI agent working in this repo, follow this guidance.

## The Flow

Use `clarify` when a request is vague, multi-part, voice-dictated, or needs to become a reusable prompt before execution.

Use `design-doc -> spec -> plan` for changes with ambiguous architecture, tradeoffs, or cross-cutting concerns. Use `spec -> plan` for changes that touch contracts, behavior, invariants, or multiple files. Skip stages only when explicitly told to or when the change is trivial and decision-complete.

Use `execplan-authoring` when a repo requires a living ExecPlan or a complex implementation plan needs to be self-contained and verifiable.

Use `refactor` when existing code or skill text needs cleanup without behavior changes. Use `commit-message` when drafting or reviewing commit messages.

Use `frontend-skill` for visually strong landing pages, websites, apps, prototypes, demos, and game UIs. Use `uncodixfy` as a restraint pass for frontend work, especially dashboards and tools.

Use `explain-visually` when a repo, spec, PR, architecture, or concept should become a clear HTML visual explanation.

Exploration is allowed without creating docs or issue tracker entries. Do not manufacture fake specs, plans, or issues for spikes.

## Skills

- `clarify`: turn a vague or messy ask into a clean, self-contained prompt.
- `commit-message`: draft concise commit messages with a conventional header and optional structured body.
- `design-doc`: write a lightweight architecture design doc before implementation when the design is ambiguous.
- `execplan-authoring`: create or update self-contained ExecPlans for complex changes.
- `explain-visually`: create a visual HTML explanation of a repo, spec, PR, architecture, or concept.
- `spec`: write the technical design before coding.
- `plan`: break a spec, brief, or request into agent-sized tasks.
- `refactor`: simplify changed code without changing behavior.
- `frontend-skill`: guide visually strong frontend pages, apps, prototypes, demos, and games.
- `uncodixfy`: remove generic AI UI patterns from frontend work.

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
