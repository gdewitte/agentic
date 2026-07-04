---
name: explain-visually
description: Create a concise, self-contained HTML explanation of a technical spec, architecture, implementation, repo, PR, system, or concept. Use when the user asks to visualize, diagram, explain, or build an HTML artifact that lets internal or external readers understand the design in one to two minutes. Infer a strong teaching path and preserve important contracts through diagrams, cards, and real tables. Use frontend-skill for design polish and uncodixfy for the final anti-generic cleanup pass.
---

# Explain Visually

Create a human-facing HTML artifact that explains a technical design visually. Beauty serves clarity. The reader should understand what the system is, how it operates, and the important implementation contracts well enough to retell it after a one-to-two-minute read.

## Workflow

### 1. Understand

Read the source material. Identify the audience, core idea, moving parts, decisions, tradeoffs, data contracts, and what the human should remember.

Assume a mixed audience by default: team members who need implementation detail and external readers who lack local context. Make the artifact self-contained. Expand project-specific acronyms once, explain why each major component exists, and avoid relying on tribal knowledge.

Ground the explanation in facts from the source. Prefer concrete names, paths, commands, interfaces, schemas, examples, and observed behavior over positioning language.

Default to explaining for a smart technical reader who is new to this system. Define jargon before using it. If a term needs domain context, replace it with plain language or explain it visually.

Set a strict reading budget: the full artifact should be scannable in one to two minutes. Prefer a small number of high-signal sections, short paragraphs, and tables that can be skimmed. Omit background that does not change the reader's mental model or implementation decisions.

### 2. Outline

Write the teaching path before building:

- what the reader should understand;
- the simplest useful top-level mental model;
- which source details belong in tables, schemas, or model cards;
- the order of sections in the responsive navigation or section index;
- which ideas need diagrams;
- what can be omitted; and
- which source facts support the explanation.

Default teaching path:

1. what this is and why it exists;
2. a simple architecture overview;
3. how it operates end to end;
4. data models, telemetry, or interfaces;
5. key decisions, risks, and next steps.

#### Commit to a direction

Do not pause to ask the user which sections to include. Infer the smallest complete teaching path from the source and state the assumed outline briefly before building. If the user already specified sections, follow them exactly.

#### Coordinate design polish

Use this skill for the teaching path, source grounding, diagram/table decisions, and explainer structure. For visual direction, layout polish, imagery, motion, and final interface quality, explicitly use `frontend-skill`. After drafting the artifact, use `uncodixfy` as the anti-generic cleanup pass. Do not duplicate those skills' detailed frontend rules here.

#### Preserve an established visual baseline

When the user provides an existing HTML artifact, screenshot, or local file as a style reference, inspect it before building and treat it as the canonical visual baseline. Adapt the reference surgically instead of creating a fresh interpretation.

Preserve the reference's:

- information architecture and section count;
- page geometry, navigation placement, and spacing rhythm;
- typography scale, font roles, and heading treatment;
- palette, border language, surface hierarchy, and destination colors;
- diagram medium and density, such as SVG-first architecture diagrams versus CSS cards or Mermaid;
- table treatment, including complete normative columns and field detail;
- interaction patterns, responsive behavior, and provenance treatment; and
- strongest teaching device, such as an early failure-mode-versus-intended-boundary contrast.

Change only the content, stale facts, and explicitly requested scope unless the user asks for a redesign. If the reference conflicts with the current source material, keep its visual system while updating the incorrect content. Do not silently simplify a full contract table, replace SVG diagrams with a different visual language, add extra sections, or change the reading path.

Resolve conflicts deliberately:

1. Source facts and explicit user scope win for content and behavior.
2. Explicit user visual direction and a supplied reference win for visual decisions.
3. `frontend-skill` decides design polish when no reference decides the question.
4. `uncodixfy` handles the final anti-generic cleanup pass.

A supplied reference may justify a pattern that the default quality gate would otherwise discourage, such as a sticky rail, rounded paper surfaces, or short uppercase section labels. Preserve it only when it belongs to the reference's system; do not add it merely because it is convenient.

When the user does not provide a reference, inspect `assets/reference-architecture-spec.html` and use it as the default visual baseline for architecture and technical-spec explainers. The file is intentionally anonymized with lorem ipsum placeholders: copy its visual system and structure, never its placeholder content. Replace every visible string, diagram label, table value, schema field, and provenance path with facts grounded in the current source.

Decide three content-structure things before writing HTML:

- Who is looking: developer, PM, reviewer, operator, or mixed audience.
- What kind of content dominates: architecture, flowchart, data flow, schema, state machine, timeline, dashboard, data table, or prose-first explanation.
- Which explanation structure fits: overview, comparison, flow, contract table, state machine, timeline, or staged walkthrough.

### 3. Build

Create a responsive, self-contained HTML explainer. Use Tailwind CSS via CDN for layout and responsive behavior. Use custom CSS only for fonts, theme tokens, diagrams, and small refinements.

#### Choose the rendering approach

Use the rendering method that matches the content rather than forcing everything into one diagram:

| Content | Default treatment |
|---|---|
| Text-heavy architecture under 15 elements | CSS Grid cards with explicit placement and flow arrows |
| Topology, flowchart, sequence, data flow, ER/schema, state machine, mind map, class diagram, or C4 | Mermaid with matching theme variables |
| Complex architecture with 15+ elements | Simple 5-8 node overview plus detailed CSS Grid cards |
| Data table, comparison, audit, endpoint inventory, or configuration matrix | Real semantic HTML table |
| Timeline or roadmap | CSS timeline with phase cards |
| Dashboard or KPI summary | CSS Grid cards; Chart.js only for real charts |

Never cram 15+ elements into one diagram. Use a hybrid overview plus detail cards. For Mermaid, prefer top-down layout for complex graphs, center the diagram, match it to the page palette, and provide zoom/reset/expand controls when the diagram can become too small to read. Never define a page-level `.node` class because Mermaid uses it internally.

#### Default information architecture

Use a progressive-disclosure structure:

- Start with a generous split hero: the plain-language lesson and one concrete takeaway on the left, and a sparse diagram inside a bordered paper surface on the right. The first visualization should show only the essential components, direction of flow, and main destinations. A reader should understand it in seconds.
- For pages with four or more sections, use a responsive table of contents: a 170px sticky left rail on desktop and a sticky horizontal scrollable bar below 1000px. The TOC is the first child of a two-column wrapper; all page content is inside a main column with `min-width: 0`. Keep link labels short, highlight the active section, and do not duplicate the same navigation in a top header.
- Use the TOC metadata area for provenance only: show `Source` plus the relevant repo/code path when visualizing code, or the source document/spec path when visualizing an artifact. Do not fill it with generic reading instructions.
- For pages with fewer than four sections, skip the TOC and use a compact top header only.
- Present the core mental model as a visual contrast early: failure mode versus intended boundary, before/after, or two different questions answered by two different outputs.
- If the source contains JSON, telemetry, metrics, events, schemas, datasets, or APIs, make the next visualization a scannable contract view. Prefer a small set of grouped visual cards when the primary distinction is destination, cadence, or data class; use a table when exact repeated field mappings are the reader's main implementation question.
- Place richer implementation detail after the overview: dataset tables, field mappings, API/model cards, metric labels, event schemas, failure modes, and rollout phases.
- Keep detailed tables and models visible in the artifact rather than flattening them into prose. Use horizontal scrolling or responsive stacking when needed.
- On mobile, convert the TOC to a compact sticky horizontal bar with hidden scrollbar; never let navigation consume the content width.

For architecture and spec explainers, the default page structure is:

1. What this is
2. How it operates
3. Data model or telemetry contract
4. Key implementation details
5. Decisions, deferred scope, and next steps

Adapt section names to the source, but keep the same progression: plain-language purpose first, simple operation second, structured implementation detail third. Keep the left table of contents aligned to this short reading path.

#### Tables and models

When the source contains datasets, APIs, metrics, events, schemas, or implementation phases:

- preserve exact names and paths;
- use tables for repeated field comparisons;
- use compact code or schema cards for individual models;
- distinguish metrics from structured events visually;
- show labels separately from JSON payload fields;
- mark deferred, beta, out-of-scope, or unresolved items clearly;
- keep tables scannable with sticky headers when long;
- use a real semantic `table`, not CSS Grid pretending to be one;
- add alternating row tones, row hover, column width hints, and an optional sticky first column for wide tables;
- do not bury critical contracts inside diagram labels.

The first contract view should answer the reader's most likely implementation question. For telemetry specs, first group the contract into enrichment, metrics, and structured events when that distinction is the main lesson; then include a compact exact-name table only if the reader needs repeated dataset, source, cadence, destination, metric/event name, and labels or JSON fields. For API or JSON models, default columns are model or object, purpose, important fields, producer, and consumer.

### 4. Verify

Before using a browser, ask the user whether they want visual verification and which surface to use: the local Codex browser or Chrome. Do not run `browser-verify`, Playwright, start a local server, or navigate an existing browser session without that explicit choice.

If the user chooses a browser, use the corresponding browser workflow to check desktop and mobile viewports. Fix overflow, overlap, clipped text, unreadable scale, cramped spacing, broken table behavior, and navigation that obscures content. If the user declines verification or the chosen browser is unavailable, perform static checks where practical and clearly report that the artifact was not visually verified.

Specifically verify:

- the first overview remains understandable without reading the detailed tables;
- the artifact can be scanned end to end in roughly one to two minutes;
- a four-or-more-section page has a usable sticky desktop TOC and a compact mobile horizontal bar;
- wide tables scroll or stack without clipping;
- model cards remain readable at narrow widths; and
- diagram labels stay centered and contained.

Before final delivery:

- run `frontend-skill` for design direction and polish;
- run `uncodixfy` to remove generic AI UI patterns;
- run the completeness test: every source fact needed for the reader's mental model is present;
- run the overflow test: every grid/flex child can shrink, long tokens wrap, and no content escapes its container.

## Rules

- Explain, do not decorate.
- When a reference artifact is supplied, visual continuity is a requirement, not a suggestion.
- Teach before summarizing.
- Lead with the simplest correct mental model.
- State what the system is before explaining how it works.
- Explain how it operates before presenting field-level detail.
- Preserve detail through tables and model sections instead of overloading the opening diagram.
- Use the responsive sticky TOC pattern for four or more sections; skip it for shorter pages.
- Simple words beat abstract titles.
- Define loaded terms before relying on them.
- The first screen must state the core lesson in plain language.
- Show at least one transformation: before/after, problem/solution, vague/clear, or hidden/visible.
- Give the reader one reusable mental model.
- Include one concrete example from the source material.
- End with the action the reader should take next.
- Make factual claims the source material supports.
- Use concrete names, paths, commands, examples, labels, and fields when they help the reader trust the explanation.
- Diagrams should make the idea easier to understand.
- Diagram text must be centered, aligned, and contained inside its shapes.
- Do not use `overflow: hidden` on content containers to hide layout problems.
- Give every grid/flex child `min-width: 0` and let long technical tokens wrap or scroll inside deliberate containers.
- Use recessed, wrapping code blocks with explicit whitespace preservation; never dump large source files when structure or a short snippet will explain the point.
- Prefer useful clarity over clever phrasing.
- The artifact fails if the reader cannot explain the idea back.
- The artifact fails if the overview is as dense as the implementation details.
- The artifact fails if a new reader needs local context or more than two minutes to find the main point.
- The artifact fails if important tables or models are omitted when the source depends on them.
- The artifact fails if text overlaps, clips, or overflows.
