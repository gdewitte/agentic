---
name: tdd
description: "Test-driven development. Use when the user wants to build features or fixes test-first, mentions red-green-refactor, asks for integration tests, or when implement chooses TDD for meaningful behavior changes."
---

# Test-Driven Development

TDD is the red -> green loop. This skill keeps that loop focused on tests worth keeping: what a good test is, where tests go, the anti-patterns, and the rules of the loop. Apply these rules during each cycle, not after.

When exploring the codebase, read `CONTEXT.md` when it exists so test names and interface vocabulary match the project's domain language, and respect ADRs in the area you touch.

## What A Good Test Is

Tests verify behavior through public interfaces, not implementation details. Code can change internally; tests should still hold. A good test reads like a specification: `user can checkout with valid cart`.

See [tests.md](tests.md) for examples and [mocking.md](mocking.md) for mocking guidance.

## Seams

A seam is the public boundary you test at: the interface where behavior is observed without reaching inside.

Test only at agreed seams. Before writing tests, identify the seam under test from the spec, plan, current request, or existing public interface. If the seam is unclear and materially changes test scope, ask the user to confirm it.

Ask: "What is the public interface, and which seams should we test?"

## Anti-Patterns

- **Implementation-coupled**: mocks internal collaborators, tests private methods, or verifies through a side channel.
- **Tautological**: recomputes the expected value the same way the code does, so the assertion passes by construction.
- **Horizontal slicing**: writes a batch of imagined tests first, then a batch of implementation.

Expected values must come from an independent source of truth: the spec, a known-good literal, a worked example, a fixture, or documented behavior.

## Rules

- Red before green. Write the failing test first, then only enough code to pass it.
- One slice at a time. One seam, one behavior, one minimal implementation per cycle.
- Use vertical slices. Start with a tracer bullet that proves one path end to end, then widen.
- Refactor only when green. Do not refactor while the suite is red.
- Prefer public behavior tests over private method tests.
