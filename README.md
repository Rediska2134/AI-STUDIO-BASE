# AI-STUDIO-BASE

Reusable project base for AI Studio work with repo-local Codex skills already vendored under `.agents/skills/`.

## What this base gives every new project

- Autonomous repo-local skills: no reinstall is required when a new Codex Cloud workspace starts from the repository.
- Root `AGENTS.md`: persistent operating rules for Codex.
- `PROJECT_BRIEF.md`: one project-specific source of truth to fill in when a project starts.
- Safe default `.gitignore` for secrets, dependencies, build output, caches, and local machine files.

## Installed skills

- `ui-ux-pro-max`
- `grill-me`
- `grilling`
- `frontend-design`
- `hyperframes`
- `triage`
- `domain-modeling`
- `hyperframes-creative`
- `web-design-guidelines`

`grilling` is required by `grill-me`. `domain-modeling` is required by `triage`.

## Starting a new project

1. Create a new repository from this GitHub template.
2. Give the new repository the real project name.
3. Fill in `PROJECT_BRIEF.md` before substantial implementation.
4. Add project code and project-specific instructions without editing vendored skills unless the task is explicitly to update the skill set.
5. Keep secrets in local environment files or a secret manager, never in Git.

## Updating the base

Update skills here first, verify them here, and then let future projects inherit the verified base. Existing projects should not silently replace their vendored skills during unrelated work.
