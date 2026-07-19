---
name: harness
description: "Audit, design, or improve a repository harness for AI coding agents. Use when the user asks about harness engineering, agent readiness, AGENTS.md/CLAUDE.md, repo-as-system-of-record, verification commands, smoke/e2e proof, progress state, feature tracking, observability, clean handoff, or making a repo easier for Codex/Claude-style agents to execute reliably."
---

# Harness

Use this skill to make a repo easier for coding agents to navigate, execute, verify, recover, and hand off. A harness is not a prompt file; it is the repo-local system around the model.

Core model: **instructions, tools, environment, state, feedback**.

## Workflow

1. Identify the target repo and task. If the user does not name a repo, use the current working tree.
2. Read the first-layer map: `AGENTS.md`, `CLAUDE.md`, README, Makefile, package scripts, pyproject, docker/devcontainer files, and testing docs.
   - Treat `AGENTS.md` as a table of contents, not the knowledge base. Durable repo knowledge should live in a small set of routed docs, usually capitalized files under `docs/`.
   - Inventory any capital-doc spine that already exists: `docs/ARCHITECTURE.md`, `docs/DESIGN.md`, `docs/BRAND.md`, `docs/TESTING.md`, and repo-specific peers such as `SECURITY.md`, `RELIABILITY.md`, `OPERATIONS.md`, or `PLANS.md`.
   - Do not treat a missing capital doc as a gap by itself. First determine whether an agent would fail, duplicate stale instructions, miss an invariant, or lack a proof path without it.
   - When durable guidance mixes independent domains, first try routing it into the smallest relevant existing `docs/<CAPITALDOC>.md` file. Recommend a new capital doc only when no existing doc can own the guidance cleanly.
3. Run a fresh-session test from repository artifacts only:
   - What is this project?
   - How do I set it up and run it?
   - How do I verify a small change, a cross-component change, and a production-sensitive change?
   - What invariants must not be broken?
   - Where does durable state live: specs, plans, progress, feature list, docs, or tests?
4. Score the five subsystems from 1-5. Cite concrete files or missing files for each score.
5. Pick the smallest high-leverage improvement. Prefer the weakest subsystem only when it is actually blocking agent success.
6. Implement or propose the improvement with repo-native conventions. Do not introduce a template pack when a short Makefile target, AGENTS pointer, test command, or doc correction would solve the problem.
7. Verify the harness change. At minimum run `git diff --check`; also run any relevant command touched by the change.

## Subsystem Checks

### Instructions

- `AGENTS.md` or `CLAUDE.md` should be a map, not an encyclopedia.
- It should name read-first docs, repo layout, critical invariants, and validation defaults.
- Prefer a capital-doc spine when a repo needs durable guidance:
  - `docs/ARCHITECTURE.md`: system map, runtime ownership, layers, dependency direction, integration boundaries, and invariants.
  - `docs/DESIGN.md`: product behavior, UX/gameplay principles, state-machine rules, and intentional tradeoffs.
  - `docs/BRAND.md`: product identity, voice, visual taste, copy rules, and user-facing quality bar.
  - `docs/TESTING.md`: command hierarchy, proof artifacts, smoke/manual checks, and what each check proves.
- Consider conditional capital docs only when they carry real repo guidance:
  - `docs/API.md`: public/private routes, request and response contracts, auth boundaries, and API compatibility rules.
  - `docs/DATA.md`: schema ownership, migrations, persistence rules, seed data, fixtures, and data-retention constraints.
  - `docs/SECURITY.md`: secrets, authentication, authorization, permissions, threat-sensitive flows, and required reviews.
  - `docs/OPERATIONS.md`: deployment, rollback, production configuration, runbooks, and release ownership.
  - `docs/RELIABILITY.md`: background jobs, retries, idempotency, failure modes, recovery behavior, and SLO-sensitive paths.
  - `docs/OBSERVABILITY.md`: logs, metrics, traces, dashboards, local inspection commands, and evidence queries.
  - `docs/CONTENT.md`: editorial standards, product copy rules, localization, content sources, and approval boundaries.
- Determine and state which capital doc should own separable domains such as `auth`, `payments`, `api`, `data`, `jobs`, `ui`, `gameplay`, `assets`, `audio`, `deploy`, or `observability`; ask only when ownership is genuinely ambiguous after reading the repo.
- Before adding or recommending a new capital doc, cite concrete evidence: files with repeated or stale guidance, missing read-first routing, domain-specific invariants that do not fit existing docs, separate validation commands, production risk, or recurring agent mistakes.
- Recommend a new capital doc only when the evidence shows a durable routing or proof problem that an existing capital doc cannot absorb cleanly. Otherwise recommend an existing-doc edit or no doc split.
- Preferred routing is `AGENTS.md` -> capital docs. Do not list every detailed artifact in `AGENTS.md` unless the repo is tiny and the list is shorter than the routing rule.
- If guidance exceeds about 100 lines, split durable detail into the relevant `docs/<CAPITALDOC>.md` file and link to it.
- Remove stale or duplicate instructions; stale guidance is worse than missing guidance.

### Tools

- Prefer repo-native commands: `make setup`, `make dev`, `make test`, `make smoke`, `make build`, `make deploy`.
- Commands should be discoverable from README, Makefile help, or AGENTS.
- UI work should have a browser/screenshot/smoke path when practical.
- Recurring review comments should become executable checks when possible.

### Environment

- Runtime versions and dependency managers should be discoverable from lockfiles, `.nvmrc`, `.python-version`, Docker, devcontainers, or Makefile checks.
- Setup should fail with actionable messages when required tools or secrets are missing.
- Secrets must be named by source and location without exposing values.

### State

- Long-running or multi-session work needs durable state: approved specs, plans, progress files, issue references, or feature lists.
- Do not add state machinery by default. Use it when work spans sessions, agents, or risky sequencing.
- At most one active feature or plan should be in progress unless the repo already has a stronger convention.
- Specs and plans should be indexed or routed from the relevant capital doc instead of being exhaustively listed in `AGENTS.md`.

### Feedback

- Feedback is the highest-ROI subsystem. Make verification commands explicit.
- Use a validation hierarchy: unit checks first, integration next, smoke/e2e when cross-component behavior matters.
- Error messages in custom checks should say what failed, why it matters, and how to fix it.
- Evidence matters: screenshots, smoke output directories, logs, curl transcripts, and test commands are better than "looks good."

## Local Patterns To Imitate

- `voidfall`: concise root routing, `make setup/dev/test/smoke/assets`, repo-local specs/plans, Playwright smoke proof frames, asset validation, and clear game invariants. If specs/plans crowd the root map, route them through existing capital docs first; add a new capital doc only when the audit proves a separate durable domain.
- `bookagree`: read-first docs, secrets policy, public/private API boundary, `docs/specs/<feature>.md`, Makefile commands for local dev, production harness, tests, deploy, and database work. Treat older plan/doc locations as historical until the current repo files prove otherwise.
- `slothmetry`: direct API validation with `curl`, Docker-based development, explicit deploy chain, and route source-of-truth guidance.
- `laggysloth-dash`: server-side auth invariants, root Makefile as the command surface, Supabase migration source-of-truth, and route-specific UI verification.

## Doc-Domain Decision Examples

- Bad: create `docs/API.md` because the repo has routes.
- Better: keep route ownership in `docs/ARCHITECTURE.md` if it is concise, current, and shares the same proof path as the rest of the app.
- Good: add `docs/API.md` only when route contracts, auth boundaries, compatibility rules, or API-specific verification are repeated, stale, risky, or too large for `docs/ARCHITECTURE.md`.
- Good: report "no doc split needed" when existing capital docs already route the domain clearly and the audit finds no drift.

## Output Shape

For audits, report:

- Target repo
- Current harness map
- Five subsystem scores
- Highest-leverage gap
- Smallest recommended change
- Doc-domain recommendation: new capital doc, existing-doc edit, or no doc split needed
- Verification to run

For edits, make the change and report files changed, commands run, and residual risks.

## Guardrails

- Keep the harness smaller than the code it controls.
- Do not add empty capital docs just to satisfy a pattern. Add or recommend only docs that will carry real routing, invariants, or proof guidance for the repo.
- Do not add capital docs because names exist. Add them only after the harness audit shows their invariants, commands, owners, data boundaries, or proof paths differ enough that a focused top-level doc will prevent drift.
- If existing `ARCHITECTURE`, `DESIGN`, `BRAND`, or `TESTING` docs can absorb the guidance without becoming bloated or ambiguous, edit those instead of creating another doc.
- Treat "no doc split needed" as a valid high-quality outcome when the current routing is already legible.
- Do not create `feature_list.json`, progress files, or broad docs unless the repo's work pattern needs them.
- Do not replace existing repo conventions with generic harness templates.
- Do not create extra planning machinery by default; use `plan` when complex approved work needs living execution state.
- Do not mark a harness complete without proof commands or a clear reason why proof could not run.
