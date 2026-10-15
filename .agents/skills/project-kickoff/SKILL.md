---
name: project-kickoff
description: Initialize or resume a project created from AI-STUDIO-BASE. Use when starting a new repository/project, opening a fresh Codex thread for a project, converting a vague idea into the first executable milestone, or when PROJECT_BRIEF.md / PROJECT_STATE.md need to be grounded before substantial work. Read existing repository context first, fill only confirmed facts, choose the smallest useful first milestone, select only relevant skills, and leave the project resumable for the next session.
---

# Project Kickoff

Use this workflow to turn a fresh template checkout or a new substantial project request into an executable, durable starting state.

## 1. Read before asking

Read, in this order when present:

1. `AGENTS.md`
2. `PROJECT_BRIEF.md`
3. `PROJECT_STATE.md`
4. `AI_RUNTIME.md` when the task changes AI tooling, skills, MCP, hooks, plugins, or agent architecture
5. the repository tree and relevant existing source/config files

Do not ask the user to repeat facts already present in these files or the repository.

## 2. Ground the brief

Update `PROJECT_BRIEF.md` with confirmed facts only. Keep unknown fields explicitly `TBD` rather than inventing requirements.

At minimum, establish enough to act safely:

- desired outcome;
- primary users/audience;
- concrete deliverable for the current phase;
- important constraints;
- non-goals or scope boundary when ambiguity could cause wasted work;
- acceptance criteria for the first milestone.

Do not turn kickoff into an interview when the request already supplies enough information to start.

## 3. Inspect the execution environment

Check the repository and environment needed for the requested work. Examples:

- current branch and `git status`;
- existing package manager / language / framework;
- available tests, lint, typecheck, build, and run commands;
- relevant external integrations already represented in project configuration;
- whether a requested CLI/runtime is actually installed before claiming it is available.

Never expose or commit secrets while inspecting setup.

## 4. Select capabilities deliberately

Choose only the repo-local skills that materially help the first milestone.

Examples:

- website/frontend: `ui-ux-pro-max`, `frontend-design`, `web-design-guidelines`, `copywriting`, `agent-browser` as relevant;
- browser QA or live-page verification: `agent-browser`;
- planning stress-test when assumptions are still weak: `grill-me` / `grilling`;
- video/motion: `hyperframes` and relevant HyperFrames domain skills;
- issue/PR workflow: `triage` and its declared dependencies.

Do not invoke every installed skill merely because it exists.

If native subagent tools are available, delegate only independent workstreams that benefit from parallel execution. Keep shared-state or sequential work with the coordinator.

## 5. Define the first executable milestone

Prefer one milestone that creates visible or testable progress rather than a large master plan.

For the milestone, record:

- what will exist when it is done;
- which files/systems are expected to change;
- the strongest practical verification method;
- what is explicitly deferred.

If the project is complex, keep later milestones as a short ordered list, not a speculative implementation blueprint.

## 6. Update persistent state

Write `PROJECT_STATE.md` so a fresh session can immediately see:

- current objective;
- what is already complete;
- what is in progress;
- blockers/risks;
- next steps;
- durable decisions;
- verification status.

Keep it concise. Do not use it as a chat transcript.

## 7. Start work when unblocked

When the brief and first milestone are sufficiently clear, proceed with the milestone instead of stopping for ceremonial confirmation.

If a genuine blocker remains, state exactly what is blocked and why. Ask only for information or approval that cannot be safely inferred or obtained from the repository/environment.

Apply the repository rule throughout:

**SEE THE PROBLEM → STATE IT → ASSESS IMPORTANCE → FIX IT → VERIFY IT → CONTINUE**
