# Agent Roles

This directory stores reusable **role specifications** for agents used across AI Studio projects.

A role file does not create an agent by itself. Runtime tools decide whether an agent/subagent can actually be spawned. These files define how a worker should behave when that role is assigned.

## Active reusable roles

- `coordinator.md` — primary owner of architecture, decomposition, integration and final verification;
- `frontend-implementer.md` — bounded frontend/UI implementation;
- `design-reviewer.md` — independent visual review against studio/project rules;
- `qa-reviewer.md` — independent runtime, responsive and edge-case verification;
- `scope-guard.md` — scope drift, delivery risk and premature-assumption review;
- `researcher.md` — current docs/reference/research without silent production edits.

## Every role spec defines

- objective;
- required context;
- owned system boundary / files where relevant;
- forbidden areas;
- expected output;
- verification responsibility;
- handoff / escalation conditions.

Use the smallest set of roles that materially improves the current task. Do not spawn a fantasy org chart for tiny work.

See `.agents/subagents/TASK_TEMPLATE.md` for delegation contracts and `.agents/subagents/DEMO_SQUAD.md` for the default substantial UI milestone pattern.
