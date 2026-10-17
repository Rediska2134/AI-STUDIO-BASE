# AI Studio Orchestration

This file defines how the studio uses a primary coding agent, runtime subagents, and future secondary coding agents without creating duplicated work or conflicting changes.

## 1. One coordinator owns the result

Every substantial task has one coordinator responsible for:

- understanding the brief and current project state;
- splitting work only when parallelism has a real payoff;
- assigning non-overlapping ownership;
- integrating results;
- running final verification;
- updating durable project state.

Parallel workers produce evidence and implementation pieces. They do not independently declare the overall task complete.

## 2. Good parallel lanes

Delegate work when tasks can proceed independently.

Strong examples:

- reference / competitor research while implementation continues;
- frontend implementation and independent visual QA;
- backend/API work and isolated frontend shell work with a frozen interface contract;
- accessibility review separate from feature implementation;
- test coverage for a stable module while another agent works elsewhere;
- mobile-specific screen work separate from web when schemas/API contracts are already fixed;
- investigating multiple plausible causes of a bug independently.

Weak examples:

- two agents editing the same component tree;
- two agents redesigning the same screen simultaneously without explicit variants;
- implementation before the data contract or scope is stable;
- parallel refactors across tightly coupled files;
- agents making independent architectural decisions that affect each other.

## 3. Ownership before execution

Before parallel work starts, record for each worker:

- objective;
- files / directories or system boundary owned;
- inputs / contracts it may rely on;
- files / areas it must not modify;
- expected output;
- verification it must run;
- handoff condition.

If ownership cannot be described clearly, keep the work sequential.

## 4. Suggested studio roles

Roles are temporary task shapes, not permanent personas.

### Coordinator / primary Codex

Owns:

- architecture;
- task decomposition;
- shared contracts;
- integration;
- final QA;
- `PROJECT_STATE.md`.

### Implementation worker

Owns one bounded feature or layer with explicit file boundaries.

### Research / reference worker

Collects current documentation, examples, references, risks, or comparison evidence. Does not silently change production code.

### QA / review worker

Reviews rendered behavior, tests, accessibility, edge cases, or code quality independently from the implementer.

### Secondary coding agent (for example Claude Code)

Use only when there is enough independent work to justify a second full coding stream.

It must receive the same repository source of truth and explicit ownership. Do not use a second agent merely because the first agent is available; use it when parallel throughput is the bottleneck.

## 5. Branch / file conflict rule

For separate full coding agents, prefer one of these:

1. separate branches with a frozen interface contract; or
2. clearly disjoint directories / modules when both are working against the same branch/worktree environment.

Never intentionally assign two coding agents to edit the same files concurrently.

A coordinator reviews and integrates before treating the combined work as complete.

## 6. Context contract

Before substantial work, every coding worker should have access to the relevant subset of:

- `AGENTS.md`
- `PROJECT_BRIEF.md`
- `PROJECT_STATE.md`
- `AI_RUNTIME.md` when tooling/runtime matters
- `AI_ORCHESTRATION.md` for parallel work
- `STUDIO_DESIGN_SYSTEM.md` + project design rules for UI tasks
- relevant code/contracts/tests

Do not depend on chat-only decisions for critical implementation rules.

## 7. Verification ownership

Each worker verifies its own bounded result.

The coordinator then performs integration verification using the strongest practical checks available:

- typecheck / lint / tests;
- build;
- runtime smoke test;
- browser QA;
- screenshots / responsive review;
- API/data contract checks;
- direct state inspection.

Passing one worker's local checks is not proof that the integrated project works.

## 8. When to add another agent

Add parallel capacity when at least one is true:

- the primary agent has a queue of independent ready tasks;
- implementation and QA/research can run concurrently;
- a second platform (web/mobile/backend) can progress against stable contracts;
- waiting for one long-running workstream would otherwise leave useful work idle.

Do not add an agent when the real bottleneck is client feedback, unclear requirements, missing assets, unresolved architecture, or external account access.

## 9. Production-speed rule

The goal of multi-agent work is shorter wall-clock delivery without reducing quality.

If orchestration overhead, context duplication, conflicts, or rework become larger than the saved execution time, reduce parallelism immediately.
