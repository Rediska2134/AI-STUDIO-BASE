# AI Studio Runtime

This file defines what belongs in the reusable project template and what must stay outside it.

## Repository layer — copied into every project

Use the repository for durable, project-portable behavior:

- `AGENTS.md` — repo-wide operating rules and verification discipline.
- `PROJECT_BRIEF.md` — confirmed project goals, constraints, users, deliverables, and acceptance criteria.
- `PROJECT_STATE.md` — short current-state handoff for fresh sessions.
- `.agents/skills/` — vendored reusable workflows and their references/scripts/assets.
- `.codex/config.toml` — safe project-local Codex configuration such as read-only MCP servers.
- project code, tests, scripts, CI, and safe configuration examples.

Do not store credentials, OAuth tokens, API keys, browser session state, or account-specific plugin authentication here.

## Runtime layer — not installable as repository files

Subagents are a runtime capability. The repository can instruct Codex when delegation is useful, but it cannot make a runtime expose multi-agent tools.

Use subagents for independent, bounded work that can proceed in parallel. Keep dependent or shared-state work in the coordinator.

Application-specific agents belong in the application itself. If a project uses the OpenAI Agents API/SDK, define the actual agent roles, tools, handoffs, model settings, and concurrency in that project's code rather than in this base template.

## Account / workspace layer — connect once, not per repository

External plugins and connectors belong to the user's ChatGPT/Codex account or workspace. Examples include GitHub, Figma, Google Drive, Gmail, Calendar, OpenAI Developers, and current-library documentation providers.

The template may contain instructions for when to use them, but it must never serialize their credentials.

## MCP layer

Use MCP when an agent needs live external data or controlled actions. Prefer remote, credential-free or explicitly authenticated MCP servers over copying stale documentation into the repo.

The base currently configures the official read-only OpenAI developer documentation MCP server. Add another MCP server only when multiple projects genuinely need it.

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

A plugin is useful when a capability needs to bundle skills with MCP servers, hooks, or other runtime resources and be installed outside projects created from this template.

Current decision: do not wrap the whole base into a plugin yet. Repo-local skills are simpler and more reliable for Codex Cloud projects created from this GitHub template. Revisit when we have a stable internal capability that must also work in unrelated repositories.

## Automation rule

Follow the studio rule:

- first occurrence: solve the problem;
- second occurrence: optimize it;
- third genuinely repetitive occurrence: turn it into a reusable script, skill, hook, plugin, or service at the smallest appropriate layer.
