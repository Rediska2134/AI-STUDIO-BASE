# AI Studio Runtime

This file defines what belongs in the reusable project template and what must stay outside it.

## Repository layer — copied into every project

Use the repository for durable, project-portable behavior:

- `AGENTS.md` — repo-wide operating rules and verification discipline.
- `PROJECT_BRIEF.md` — confirmed project goals, constraints, users, deliverables, and acceptance criteria.
- `PROJECT_STATE.md` — short current-state handoff for fresh sessions.
- `AI_ORCHESTRATION.md` — how primary agents, subagents, and secondary coding agents split work safely.
- `STUDIO_DESIGN_SYSTEM.md` — reusable studio-level visual language and calibration rules.
- `.agents/skills/` — vendored reusable workflows and their references/scripts/assets.
- `.codex/config.toml` — safe project-local Codex configuration such as read-only MCP servers.
- project code, tests, scripts, CI, and safe configuration examples.

Do not store credentials, OAuth tokens, API keys, browser session state, or account-specific plugin authentication here.

## Runtime layer — not installable as repository files

Subagents are a runtime capability. The repository can instruct Codex when delegation is useful, but it cannot make a runtime expose multi-agent tools.

Use subagents for independent, bounded work that can proceed in parallel. Keep dependent or shared-state work in the coordinator. Before larger parallel sessions, follow `AI_ORCHESTRATION.md` so workers have explicit ownership and do not compete over the same files.

Application-specific agents belong in the application itself. If a project uses the OpenAI Agents API/SDK, define the actual agent roles, tools, handoffs, model settings, and concurrency in that project's code rather than in this base template.

## Account / workspace layer — connect once, not per repository

External plugins and connectors belong to the user's ChatGPT/Codex account or workspace. Examples include GitHub, Figma, Google Drive, Gmail, Calendar, Product Design, OpenAI Developers, and other current-data or action providers.

The template may contain instructions for when to use them, but it must never serialize their credentials or assume every derived project runs under the same account.

Use account-level tools when they materially shorten a workflow. Do not duplicate an already-connected capability as a repo-local MCP merely to make the tool list look larger.

## MCP layer

Use MCP when an agent needs live external data, current documentation, or controlled actions that are valuable across sessions/projects.

Current baseline:

- `openaiDeveloperDocs` — official read-only current OpenAI developer documentation.
- `context7` — current third-party library documentation.

This is intentionally small. Do not add a third baseline MCP until a repeated real project bottleneck demonstrates that the extra server saves meaningful time or reduces risk.

Prefer remote, credential-free or explicitly authenticated MCP servers over copying stale documentation into the repo. Put secrets in the execution environment, never in `.codex/config.toml`.

## Skills layer

Skills encode repeatable workflows, not live data access.

Current studio policy:

- create a skill when a workflow is repeatable and benefits from explicit sequencing/checks;
- keep project-specific one-off instructions in project files instead of turning them into global skills;
- `studio-design` is the reusable visual calibration/implementation workflow;
- specialist third-party skills remain vendored dependencies and should not be silently modified during unrelated tasks.

## Hooks

Hooks can run commands or MCP tools on lifecycle events such as `SessionStart`, `PreToolUse`, `PostToolUse`, `SubagentStart`, `SubagentStop`, and `Stop`.

Do not add a hook just because a lifecycle event exists. Project-local hooks require trust review and add executable behavior to every derived project.

Add a base hook only when all are true:

1. the behavior is needed across most projects;
2. it is deterministic and cheap;
3. failures are easy to understand;
4. false positives are unlikely;
5. the same result cannot be achieved more simply with `AGENTS.md`, a skill, CI, or `.gitignore`.

Current decision: no base hooks yet. Revisit after repeated real-world friction identifies a concrete hook worth standardizing.

## Plugin packaging

A plugin can package skills, MCP configuration, and other runtime resources behind one installable identity. That becomes valuable when an internal studio capability must work outside repositories created from this template or needs live external tools plus workflow guidance.

Current decision: **do not package the whole AI Studio base as a plugin yet**.

Reason:

- repo-local skills are already portable for our own template-derived projects;
- account-level plugins/connectors already provide GitHub, Figma, Drive and other external capabilities;
- premature packaging adds maintenance and versioning before we have a stable repeated workflow.

Candidate future plugin: the studio-design system, but only after real projects prove which skills, MCP tools, assets, and workflows are stable enough to package.

## Secondary coding agents

A second full coding agent (for example Claude Code) is capacity, not architecture.

Introduce it only when there are independent ready tasks and the primary coding stream is a real throughput bottleneck. Both agents must use the same repository source of truth and non-overlapping ownership defined in `AI_ORCHESTRATION.md`.

Do not spend setup time on a second coding stack while requirements, client assets, or architecture are the actual bottleneck.

## Automation rule

Follow the studio rule:

- first occurrence: solve the problem;
- second occurrence: optimize it;
- third genuinely repetitive occurrence: turn it into a reusable script, skill, hook, plugin, or service at the smallest appropriate layer.
