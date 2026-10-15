# AI Studio Project Rules

This repository is created from the AI Studio base. Treat these rules as persistent operating instructions for Codex in every project derived from it.

## 1. Repository-local skills

All vendored skills live under `.agents/skills/` and travel with the repository.

- Prefer these repo-local copies over reinstalling or fetching a duplicate during normal project work.
- Do not silently update, replace, delete, or re-vendor a skill while doing an unrelated task.
- Change the skill set only when the task explicitly asks for a skill update or maintenance pass.
- Treat third-party skill source files as vendored dependencies: preserve their contents unless intentionally updating them.
- Load only the specialist skills that materially help the current task. Do not stack every skill into every prompt.

## 2. Project source of truth

Read `PROJECT_BRIEF.md` before substantial implementation work.

If the brief still contains placeholders, replace only the sections that are known from the current task or repository context. Do not invent business requirements, users, constraints, or acceptance criteria just to make the document look complete.

For substantial multi-step work, also maintain `PROJECT_STATE.md`. Keep it short and factual: current objective, completed work, current work, blockers, next steps, and durable decisions. Update it at meaningful milestones so a fresh session can resume without relying on chat history.

Project-specific instructions may extend this file. When a project needs durable rules that should survive future sessions, add them explicitly rather than relying on chat history.

## 3. Working discipline

Use this sequence whenever a real problem is found:

**SEE THE PROBLEM → STATE IT → ASSESS IMPORTANCE → FIX IT → VERIFY IT → CONTINUE**

Do not call work complete merely because files were written. Verify the relevant behavior with the strongest practical check available for the task: tests, lint, typecheck, build, runtime smoke test, screenshots, rendered output, or direct file/state inspection.

If verification cannot be performed, state that limitation explicitly instead of implying success.

## 4. Scope and implementation

- Diagnose before changing architecture.
- Prefer the smallest durable solution that satisfies the brief.
- Keep project code and project-specific configuration separate from vendored skills.
- Do not introduce a tool, framework, service, dependency, or abstraction without a concrete reason.
- Reuse a pattern when it is genuinely repetitive; do not prematurely generalize one-off work.
- Preserve existing working behavior unless the task requires changing it.
- First occurrence: solve it. Second occurrence: optimize it. Third genuinely repetitive occurrence: consider turning it into a reusable system, script, or skill.

## 5. Subagents and delegation

Subagents are a runtime capability, not repository files. Use them when the active Codex runtime exposes multi-agent tools and parallel delegation would materially improve speed or quality.

Good delegation targets:
- independent codebase exploration in separate areas;
- independent research or comparison tasks;
- separate implementation components that do not edit the same files;
- independent test, QA, accessibility, or review passes;
- investigating different plausible causes of a failure in parallel.

Keep work in the main agent when the task is small, sequential, depends heavily on the previous step, or would make multiple agents contend over the same mutable files or state.

The coordinator owns synthesis and final verification. A subagent result is evidence, not automatic proof that the overall task is complete.

## 6. Browser automation and visual QA

Use the installed `agent-browser` skill when the task requires browser interaction, screenshots, UI inspection, web-app testing, forms, clicks, or rendered-page verification.

For frontend or portfolio work, do not declare the UI complete from source code alone when a runnable page is available. Prefer a real browser check at relevant desktop and mobile sizes, inspect visible errors, and capture screenshots when visual judgment matters.

If the `agent-browser` CLI is absent in the execution environment, install its runtime as directed by the skill before using it. Do not confuse the vendored skill instructions with the browser binary itself.

## 7. OpenAI product and API work

The project config exposes the official read-only OpenAI developer documentation MCP server as `openaiDeveloperDocs`.

When work depends on current OpenAI API, Agents API/SDK, Codex, plugins, MCP, hooks, models, or product behavior, consult that official documentation source rather than relying on stale memory. If the MCP server is unavailable, state that and use official OpenAI documentation as the fallback.

## 8. Secrets and external services

- Never commit API keys, passwords, access tokens, private certificates, or production credentials.
- Use `.env` / secret stores for secrets; only safe placeholders belong in `.env.example`.
- Subscription access and API billing are separate concerns; do not assume one grants the other.
- Do not make client-specific paid purchases or infrastructure commitments unless explicitly approved.
- OAuth-connected plugins, apps, and external accounts are environment/account state; do not attempt to serialize their credentials into the repository.

## 9. Git hygiene

- Keep commits focused and understandable.
- Do not commit generated caches, local editor state, dependency folders, build output, or temporary files unless the project explicitly needs them versioned.
- Before destructive Git operations, confirm they are necessary and avoid rewriting unrelated history.

## 10. UI, design, media, and business-facing work

Use the installed specialist skills when they match the task. For example:

- browser testing / screenshots / live UI QA: `agent-browser`
- UI / website direction: `ui-ux-pro-max`, `frontend-design`, `web-design-guidelines`
- planning stress-test: `grill-me` / `grilling`
- video / motion: `hyperframes`, with `hyperframes-creative` when relevant
- issue / PR triage: `triage`, with `domain-modeling` when its workflow requires it

Do not use a specialist merely because it exists. Trigger it when its workflow improves the task.
