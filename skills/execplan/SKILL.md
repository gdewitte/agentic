---
name: execplan
description: Create or update living execution plans (ExecPlans) for complex or cross-cutting implementation work after a spec is approved, or when a repo explicitly requires ExecPlans. Use when asked to create an ExecPlan from an approved spec, keep implementation progress/decision logs current, or produce a self-contained execution guide. Do not use as a substitute for the spec skill.
---

# ExecPlan

Use ExecPlans for complex or cross-cutting implementation work. Keep plans self-contained so a novice can execute from the plan alone.

## Boundaries

- Use `spec` first when requirements, design decisions, invariants, or contracts need human review.
- Use `execplan` after the spec is approved, or when the target repo explicitly requires an ExecPlan.
- Use `plan` for portable task lists that can be copied into an issue tracker or delegated independently. Use an ExecPlan only when the plan must remain living implementation state.
- Do not rename or replace the source spec with the ExecPlan. Record the spec path and approval state, then turn it into concrete implementation steps.

## Workflow

1. Confirm the repo wants an ExecPlan. If the request needs unresolved design decisions, write or revise a `spec` first instead of hiding those decisions in the ExecPlan.
2. If starting from a spec, read the approved spec and record its path in the ExecPlan. Keep the spec as the durable review artifact.
3. Read the repo's plan policy (often `docs/PLANS.md`). If none exists, use the template in `references/execplan-template.md`.
4. Follow the repo's plan location. If none is defined, place new plans in `docs/plans/active/` with a clear, dated filename.
5. Write in plain language. Define terms. Avoid pointers to external docs unless the repo policy requires them.
6. For UI or brand-affecting work, require a design thesis, token plan, and a `docs/` brand guideline update. Invoke `frontend-skill` to shape these sections.
7. Anchor each milestone with observable outcomes and explicit proof steps.
8. Maintain the living sections: Progress, Surprises & Discoveries, Decision Log, Outcomes & Retrospective.
9. Update the plan as decisions are made or scope changes.

## Quality bar

- Self-contained and reproducible.
- Source spec and approval state are visible when a spec exists.
- Explicit file paths, commands, and expected outputs.
- Acceptance criteria are behavior, not just code changes, and include how to prove it worked.
- New design decisions are called out instead of being smuggled in as execution steps.

## Template

Use `references/execplan-template.md` as the base skeleton.
