# AI Studio Project Rules

This repository is created from the AI Studio base. Treat these rules as persistent operating instructions for Codex in every project derived from it.

## 1. Repository-local skills

All vendored skills live under `.agents/skills/` and travel with the repository.

- Prefer these repo-local copies over reinstalling or fetching a duplicate during normal project work.
- Do not silently update, replace, delete, or re-vendor a skill while doing an unrelated task.
- Change the skill set only when the task explicitly asks for a skill update or maintenance pass.
- Treat third-party skill source files as vendored dependencies: preserve their contents unless intentionally updating them.

## 2. Project source of truth

Read `PROJECT_BRIEF.md` before substantial implementation work.

If the brief still contains placeholders, replace only the sections that are known from the current task or repository context. Do not invent business requirements, users, constraints, or acceptance criteria just to make the document look complete.

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

## 5. Secrets and external services

- Never commit API keys, passwords, access tokens, private certificates, or production credentials.
- Use `.env` / secret stores for secrets; only safe placeholders belong in `.env.example`.
- Subscription access and API billing are separate concerns; do not assume one grants the other.
- Do not make client-specific paid purchases or infrastructure commitments unless explicitly approved.

## 6. Git hygiene

- Keep commits focused and understandable.
- Do not commit generated caches, local editor state, dependency folders, build output, or temporary files unless the project explicitly needs them versioned.
- Before destructive Git operations, confirm they are necessary and avoid rewriting unrelated history.

## 7. UI, design, and media work

Use the installed specialist skills when they match the task. For example:

- UI / website direction: `ui-ux-pro-max`, `frontend-design`, `web-design-guidelines`
- planning stress-test: `grill-me` / `grilling`
- video / motion: `hyperframes`, with `hyperframes-creative` when relevant
- issue / PR triage: `triage`, with `domain-modeling` when its workflow requires it

Do not stack every skill into every task. Load only what materially helps the current work.
