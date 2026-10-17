# Agent Roles

This directory stores reusable **role specifications** for agents used across AI Studio projects.

A role file does not create an agent by itself. Runtime tools decide whether an agent/subagent can actually be spawned. These files define how a worker should behave when that role is assigned.

## Role spec should define

- objective;
- owned system boundary / files;
- allowed inputs;
- forbidden areas;
- expected output;
- verification responsibility;
- handoff format;
- stop / escalation conditions.

## Initial reusable roles

Planned candidates:

- `coordinator.md` — primary owner of architecture, decomposition, integration and final verification;
- `frontend-implementer.md` — bounded frontend/UI implementation;
- `backend-implementer.md` — bounded API/data implementation;
- `design-reviewer.md` — independent visual review against studio/project rules;
- `qa-reviewer.md` — tests, edge cases, browser/runtime verification;
- `researcher.md` — current docs/reference/research without silent production edits.

Create a concrete role only when we are about to use it. Avoid building a fantasy org chart before real workload exists.
