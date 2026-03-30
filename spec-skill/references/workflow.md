# Spec Workflow Reference

## Decision Rule

Apply the lightest process that still protects correctness:

- Direct change:
  Use for small edits with low ambiguity and no public contract impact.
- Spec only:
  Use when the request is significant enough to need clear requirements, but implementation is not yet requested.
- Full spec flow:
  Use for contract changes, payment flows, security-sensitive work, refactors, migrations, multi-step features, and repos newly adopting spec-driven development.

## Baseline Spec Pattern

When adapting an existing project:

1. Inspect runtime entrypoints, config files, docs, and tests.
2. Identify the current public behavior.
3. Write a baseline `spec.md` for what already exists.
4. Write `plan.md` to map the actual code structure.
5. Write `tasks.md` for the next hardening or implementation steps.
6. Only then start structural refactors or new feature work.

This prevents "spec drift" where the new process describes an imagined system instead of the deployed one.

## Practical Artifact Sequence

Use this order by default:

1. constitution update if repository rules are unclear
2. `spec.md`
3. `plan.md`
4. `tasks.md`
5. implementation
6. validation

If the repo already has these files, extend them instead of recreating them.

## Good Spec Characteristics

A good spec:

- describes user-visible behavior
- states assumptions explicitly
- includes edge cases
- separates requirements from implementation
- is short enough to guide coding decisions quickly

A bad spec:

- is just a changelog
- mirrors code structure without explaining behavior
- contains vague tasks like "improve system"
- has no acceptance criteria or validation path

## Handoff To Implementation

When moving from artifacts to code:

- implement the highest-priority independent story first
- preserve consistency between code and spec
- update the spec if engineering reality forces a change
- validate the changed behavior with targeted checks

Do not treat `tasks.md` as busywork. It should make execution easier, not longer.
