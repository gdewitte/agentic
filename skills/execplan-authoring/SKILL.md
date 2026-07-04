---
name: execplan-authoring
description: Create or update execution plans (ExecPlans) for complex changes. Use when asked to draft a plan, specification, or design-to-implementation guide, or when a repo requires ExecPlans for nontrivial work.
---

# ExecPlan Authoring

Use ExecPlans for complex or cross-cutting work. Keep plans self-contained so a novice can implement from the plan alone.

## Workflow

1. Read the repo's plan policy (often `docs/PLANS.md`). If none exists, use the template in `references/execplan-template.md`.
2. Place new plans in `docs/plans/active/` with a clear, dated filename.
3. Write in plain language. Define terms. Avoid pointers to external docs.
4. For UI or brand-affecting work, require a design thesis, token plan, and a `docs/` brand guideline update. Invoke `frontend-skill` to shape these sections.
5. Anchor each milestone with observable outcomes and explicit proof steps.
6. Maintain the living sections: Progress, Surprises & Discoveries, Decision Log, Outcomes & Retrospective.
7. Update the plan as decisions are made or scope changes.

## Quality bar

- Self-contained and reproducible.
- Explicit file paths, commands, and expected outputs.
- Acceptance criteria are behavior, not just code changes, and include how to prove it worked.

## Template

Use `references/execplan-template.md` as the base skeleton.
