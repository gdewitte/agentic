# Working in Agentic

Agentic is a personal collection of reusable agent skills. It packages clear, focused workflows for clarifying vague asks, mapping large uncertain efforts, prototyping design questions, writing design docs and specs, planning work, implementing approved changes, stress-testing ideas, refactoring safely, and building polished frontend experiences.

If you are an AI agent working in this repo, follow this guidance.

## The Flow

Use `clarify` when a request is vague, multi-part, voice-dictated, or needs to become a reusable prompt before execution.

Use `setup-matt-pocock-skills` once per repo before Wayfinder or the related engineering skills. It records the issue tracker and domain-document conventions those skills consume.

Use `grilling` when the user wants a plan, decision, or idea stress-tested through a one-question-at-a-time interview. Use `grill-me` as the invocable wrapper for starting that session.

Use `domain-modeling` when terminology, ubiquitous language, `CONTEXT.md`, or an architectural decision needs to be sharpened and recorded.

Use `research` when a question needs primary-source reading delegated to a background agent and captured as a cited Markdown artifact.

Use `wayfinder` before specification when a loose idea is too large or uncertain to resolve in one session. It maps the effort as decision tickets and clears the route to one coherent spec; completing the map does not authorize implementation.

Use `prototype` to build throwaway code that answers one design question. Choose the logic branch for state models and behavior, or the UI branch for visual direction, then capture the decision and keep the prototype itself out of main.

Use `design-doc -> spec -> approve -> implement -> review` for changes with ambiguous architecture, tradeoffs, or cross-cutting concerns. Use `spec -> approve -> implement -> review` for changes that touch contracts, behavior, invariants, or multiple files. Skip stages only when explicitly told to or when the change is trivial and decision-complete.

Use `plan` when approved work needs portable task splitting for humans, issue trackers, independent agents, multi-session handoff, or a self-contained implementation runbook.

Use `implement` after requirements are approved or decision-complete. It is the execution router: choose direct implementation, TDD, repro-first debugging, characterization/refactor, contract-first work, frontend polish, or plan-backed execution based on the task. If the source leaves product, API, or design decisions unresolved, stop and route back to `spec` or `design-doc`.

Use `tdd` inside implementation for meaningful behavior changes, test-first feature work, red-green loops, or integration tests. TDD is one implementation mode, not the only implementation mode.

Use `refactor` when existing code or skill text needs cleanup without behavior changes. Use `commit-message` when drafting or reviewing commit messages.

Use `harness` when a repo needs a better agent operating system: concise instructions, repo-local source-of-truth docs, setup/run/test commands, durable state, smoke/e2e proof, observability, or clean handoff.

Use `frontend-skill` for visually strong landing pages, websites, apps, prototypes, demos, and game UIs. Use `uncodixfy` as a restraint pass for frontend work, especially dashboards and tools.

Use `explain-visually` when a repo, spec, PR, architecture, or concept should become a clear HTML visual explanation.

Exploration is allowed without creating docs or issue tracker entries. Do not manufacture fake specs, plans, or issues for spikes.

## Skills

- `clarify`: turn a vague or messy ask into a clean, self-contained prompt.
- `commit-message`: draft concise commit messages with a conventional header and optional structured body.
- `design-doc`: write a lightweight architecture design doc before implementation when the design is ambiguous.
- `domain-modeling`: sharpen domain terminology, maintain `CONTEXT.md`, and record consequential ADRs.
- `explain-visually`: create a visual HTML explanation of a repo, spec, PR, architecture, or concept.
- `grilling`: stress-test a plan, decision, or idea one question at a time.
- `grill-me`: start a grilling session through an invocable wrapper.
- `harness`: audit and improve a repo's agent instructions, commands, state, environment, and feedback loops.
- `implement`: execute approved or decision-complete work and verify the result.
- `spec`: write the technical design before coding.
- `plan`: break a spec, brief, or request into agent-sized tasks or a self-contained implementation plan.
- `prototype`: build a throwaway logic or UI prototype to answer one design question.
- `refactor`: simplify changed code without changing behavior.
- `research`: delegate primary-source research and capture cited findings in the repo.
- `setup-matt-pocock-skills`: configure a repo's issue tracker and domain-document conventions for the engineering skills.
- `tdd`: build behavior through a red-green test-first loop.
- `frontend-skill`: guide visually strong frontend pages, apps, prototypes, demos, and games.
- `uncodixfy`: remove generic AI UI patterns from frontend work.
- `wayfinder`: map a large uncertain effort as decision tickets until the route to a spec or other destination is clear.

## Guidance

- Keep each skill directory self-contained under `skills/<skill-name>/`.
- The skill entrypoint is always `skills/<skill-name>/SKILL.md`.
- Preserve YAML front matter, including `name` and `description`.
- Prefer small, readable skill instructions over broad frameworks or duplicated policy.
- If a skill depends on supporting files, keep them inside that skill directory.
- If a task, spec, plan, or prompt is wrong, stop and update it. Do not push through.
- Density over length.

## Out of Scope

Agentic is not an issue tracker, release process, or full software delivery framework. It is a curated skill library for agent workflows. That's the entire job.
