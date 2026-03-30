---
name: spec-skill
description: Spec-driven software delivery workflow for turning product or engineering requests into repository artifacts such as constitution updates, feature specs, implementation plans, task lists, and validation steps. Use when a user asks to develop "by spec", "按 spec 方法", "先写规格再做", to introduce Specify/Spec Kit into a repo, to baseline an existing project's public contract before refactoring, or to continue implementation from an existing `specs/` directory.
---

# Spec Skill

Use this skill to move a repository through a disciplined sequence:

- define or update project rules
- capture the feature or service contract in a spec
- derive a concrete implementation plan
- break work into tasks
- implement and validate against the spec

Do not treat spec writing as paperwork. The goal is to reduce ambiguity before code changes, especially for public APIs, payment flows, security-sensitive behavior, migrations, and refactors.

## Workflow Decision

Choose the smallest spec process that matches the request:

- Tiny change, no contract impact:
  Make the change directly, but still state assumptions and run verification.
- Non-trivial feature in an existing repo:
  Create or update `specs/<id>-<name>/spec.md`, then `plan.md`, then `tasks.md`.
- Existing project with unclear boundaries:
  Start by writing a baseline spec for the current behavior before refactoring.
- New repo or repo newly adopting spec-driven work:
  Initialize the spec structure first, then write the baseline constitution and first spec.

## Repository Intake

Before writing artifacts:

- inspect the repository layout and existing `specs/`, `.specify/`, `.agents/`, `AGENTS.md`, `README.md`, and core runtime files
- identify the public contract, risk areas, and validation path
- preserve uncommitted user changes
- avoid introducing spec files that contradict the current codebase

If the repo already uses Specify or Spec Kit, extend the existing conventions instead of inventing new ones.

## Artifact Rules

### Constitution

Use for durable repository rules:

- public API stability requirements
- security handling
- testing obligations
- operational simplicity constraints

Keep it short and enforceable. Do not fill it with generic engineering values.

### spec.md

Write the feature or baseline contract in user-visible terms:

- prioritized user stories
- acceptance scenarios
- edge cases
- functional requirements
- measurable success criteria
- explicit assumptions

Prefer observable behavior over implementation detail.

### plan.md

Turn the spec into an implementation strategy:

- technical context
- source tree involved
- constitution checks
- structure decision
- constraints and dependencies

The plan should explain how the work will be executed, not restate the spec verbatim.

### tasks.md

Break work into executable steps:

- exact file paths
- dependency order
- independent test points
- clear split between setup, foundations, user stories, and polish

Mark only genuinely parallel work as parallel.

## Implementation Rules

After artifacts are ready:

1. implement the smallest coherent slice first
2. keep code changes aligned with the current spec
3. update artifacts when reality changes
4. run targeted verification, not vague "looks good" checks
5. report both completed validation and remaining gaps

For contract-sensitive repos, prefer `spec -> tests -> refactor -> feature` over direct rewrites.

## Output Expectations

When using this skill, produce or update some combination of:

- `.specify/memory/constitution.md`
- `specs/<id>-<name>/spec.md`
- `specs/<id>-<name>/plan.md`
- `specs/<id>-<name>/tasks.md`

If a user asks to "continue", infer the next artifact or execution step from the latest existing spec directory before writing code.

## Reference

Read [`references/workflow.md`](./references/workflow.md) when you need:

- a decision rule for how much process to apply
- a baseline-spec pattern for existing repos
- a handoff pattern from spec artifacts to implementation

Keep the skill lean. Do not add ceremonial docs that duplicate repository artifacts.
