---
name: implement
description: "Execute approved or decision-complete work from a spec, plan, issue, or direct request. Use when the user asks to implement, build, fix, or execute after requirements are settled. When starting from a plan, execute one approved plan slice at a time. Acts as an execution router: choose direct implementation, TDD, repro-first debugging, characterization/refactor, contract-first work, frontend polish, or plan-backed execution as appropriate; stop and route back to spec, design-doc, or plan when decisions or execution state are not settled."
---

# Implement

Use `implement` to turn settled work into verified changes. It is an execution router, not a planning replacement.

## Boundaries

- Start from an approved spec, plan, issue, or a small direct request whose behavior is already decision-complete.
- If the source artifact says to pause for approval, stop until approval exists.
- If product behavior, API contracts, UI direction, invariants, or error behavior are unresolved, stop and route back to `spec`, `design-doc`, or `grilling`.
- If the work is too broad to execute safely in one pass, route to `plan` for portable task splitting.
- If the hard part is sequencing, handoff, recovery, or durable proof across sessions, route to `plan`.
- Do not commit, push, deploy, or close tracker items unless the user asks or the repo workflow explicitly requires it.

## Workflow

1. Identify the source artifact and approval state. Read the relevant repo guidance (`AGENTS.md`, `CLAUDE.md`, README, docs) and the files/tests the source names.
2. If starting from a plan, execute the plan contract tightly:
   - Select the next unchecked task, or the task the user explicitly requested.
   - Treat the task's Goal, Acceptance criteria, and Verify steps as the execution contract.
   - Do not broaden scope beyond that task.
   - If the plan lacks enough detail to implement safely, stop and route back to `plan`.
   - For meaningful behavior changes, use `tdd`: identify the public seam from the plan, write one failing test, implement the smallest passing slice, then repeat.
   - After each completed slice, update any living plan status, progress, decisions, discoveries, handoff notes, and verification evidence.
3. Classify the execution mode before editing:
   - **Direct implementation**: tiny, obvious, low-risk edits. Implement, then run focused proof.
   - **TDD**: meaningful new or changed behavior. Use `tdd`: agree the public seam when it is not already specified, write one failing behavior test, implement only enough to pass, then repeat in vertical slices.
   - **Repro-first debugging**: bugs, flakes, failures, or performance regressions. Build one command or test that reproduces the symptom before fixing it.
   - **Characterization/refactor**: behavior-preserving cleanup. Lock current behavior through public interfaces when risk warrants, then refactor in small reversible steps.
   - **Contract-first**: APIs, schemas, events, integrations, or data migrations. Pin the contract and compatibility expectations before filling in internals.
   - **Frontend implementation**: use `frontend-skill` for visual direction and `uncodixfy` as the restraint pass, then verify in a browser when practical.
   - **Plan-backed execution**: follow the approved plan and keep status, progress, decisions, discoveries, handoff notes, and verification current when the plan is a living artifact.
4. Implement in small vertical slices. Stay inside the source scope and match existing repo patterns.
5. Update adjacent docs, fixtures, examples, migrations, or scripts only when the change makes them stale.
6. Verify with the narrowest useful checks first, then the repo's broader proof path when available: targeted tests, typecheck, lint, build, smoke, browser screenshot, or full suite. Report environment failures distinctly from code failures.
7. Review the final diff against the source artifact. Check for missing requirements, scope creep, stale docs, brittle tests, and unnecessary abstraction.

## Done

Implementation is done only when:

- The approved behavior works.
- The chosen proof commands ran, or any inability to run them is clearly reported.
- The diff is scoped to the request.
- Any living plan was updated with progress, decisions, discoveries, handoff notes, and outcomes.
- The final response names the important files changed, the verification performed, and any residual risk.
