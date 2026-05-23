---
name: frontend-svelte
description: Design and build distinctive, production-grade Svelte interfaces with high visual quality. Use this skill when the user asks for Svelte or SvelteKit components, pages, layouts, flows, or frontend applications that should feel intentional, polished, and non-generic.
author: "https://github.com/gdewitte"
---

This skill guides creation of distinctive, production-grade Svelte interfaces that avoid generic frontend output. Build real working Svelte or SvelteKit code with strong visual direction, clean structure, and idiomatic framework usage.

The user may ask for a component, page, route, layout, or full interface. They may include product context, audience, constraints, or an existing design system.

## Design Direction

Before coding, decide on a clear aesthetic and execute it precisely:
- Purpose: Define what the interface needs to help the user do.
- Tone: Pick an intentional visual direction instead of defaulting to generic SaaS UI.
- Constraints: Respect existing product patterns, accessibility, responsiveness, and performance limits.
- Differentiation: Make one or two visual choices memorable and coherent.

Then implement code that is:
- Production-grade and functional
- Visually distinctive and cohesive
- Responsive on desktop and mobile
- Consistent with the surrounding product if one already exists

## Svelte Rules

- Prefer Svelte or SvelteKit primitives over React or Vue mental models.
- Use idiomatic `.svelte` component structure with minimal ceremony.
- Avoid React-style patterns such as hooks, effect-heavy state wiring, or needless abstraction.
- Use Svelte reactivity, derived values, component composition, and stores only when they clarify the implementation.
- Use Svelte transitions, keyframes, and motion intentionally for a few high-value moments rather than adding generic animation everywhere.
- Keep component APIs small and explicit.

## Visual Standards

Focus on:
- Typography: Choose expressive, purposeful type and avoid default-looking stacks when the project allows it.
- Color: Commit to a clear palette with deliberate contrast and accents.
- Layout: Use spacing, hierarchy, and composition that feel designed rather than templated.
- Motion: Favor meaningful entrance, hover, and state transitions with restrained timing.
- Atmosphere: Use gradients, textures, shapes, or layered surfaces where they strengthen the concept.

Avoid generic AI aesthetics such as interchangeable dashboards, purple-on-white defaults, bland system-font compositions, and repetitive card grids with no point of view.

## Implementation Guidance

- Preserve existing design-system and codebase conventions when editing an established Svelte app.
- For new work, prefer simple component structure and readable CSS over heavy indirection.
- Use scoped component styles when local styling is enough; use shared styles only when a pattern is intentionally reused.
- Keep accessibility intact with semantic HTML, keyboard support, and visible focus states.
- Make loading, empty, hover, and error states feel considered.

## Output Expectation

Deliver working Svelte code, not mockups. Favor strong execution over long explanation.
