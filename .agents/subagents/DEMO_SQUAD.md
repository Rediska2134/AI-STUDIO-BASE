# Demo Squad — Default UI Milestone Pattern

Use this pattern for a fast premium demo / storefront milestone when the runtime supports parallel workers.

## Coordinator
Owns milestone, contracts, task split, integration, final verification and state updates.

## Lane A — Frontend Implementer
Builds the assigned screen/component set only.

## Lane B — Design Reviewer
Runs independently after a renderable slice exists. Reviews against studio/project design rules and references. Does not silently edit implementation.

## Lane C — QA Reviewer
Tests the runnable slice for broken flows, responsive issues, runtime errors and edge states.

## Lane D — Researcher / Reference Analyst
Runs only when current docs/reference analysis can unblock design or implementation while Lane A continues.

## Continuous guard — Scope / Delivery Guard
Invoked at milestone start and again before calling the milestone complete. Checks for scope drift, premature provider/backend assumptions, unnecessary tooling and missing client decisions.

## Default loop
1. Coordinator freezes the current slice and ownership.
2. Implementer builds.
3. Design reviewer + QA reviewer inspect independently.
4. Coordinator classifies findings: blocker / important / polish.
5. Implementer fixes assigned findings.
6. QA rechecks fixes.
7. Coordinator runs integration verification and updates project state.

Do not spawn every lane for tiny tasks. The squad is a default pattern for substantial UI milestones, not a mandatory ceremony.