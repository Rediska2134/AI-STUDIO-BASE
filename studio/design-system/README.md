# Studio Design System Workspace

This directory is the durable home for the AI Studio visual system shared across future projects.

It is intentionally separate from client-specific design files.

## Purpose

Use this folder to store design rules that should survive across projects:

- typography system;
- color architecture;
- spacing / grid;
- borders / radius / elevation;
- navigation / sidebars / drawers;
- panels and surfaces;
- component principles;
- motion / microinteractions;
- responsive behavior;
- accessibility baseline;
- visual QA rules;
- validated reference-derived patterns.

## Inheritance model

1. `studio/design-system/` = studio defaults and reusable visual rules.
2. project-local design files = client brand/theme overrides.
3. explicit project requirements win over studio defaults.

Do not force every client into one identical visual identity.

## Calibration rule

Use:

**REFERENCE → REACTION → REASON → RULE → PROTOTYPE → LIVE REVIEW → ADJUST → LOCK**

Do not lock arbitrary values just to fill files.

## Current canonical files

- `STUDIO_DESIGN_SYSTEM.md` — current high-level studio design language.
- `docs/REFERENCE_CAPTURE.md` — live reference-capture workflow.
- `.agents/skills/studio-design/SKILL.md` — Codex workflow for applying and evolving the system.

This directory will gradually absorb the detailed system as it becomes stable through real projects.

## Planned structure

- `TOKENS.md` — semantic tokens and locked values.
- `TYPOGRAPHY.md` — type roles, scale, spacing and usage rules.
- `COLOR.md` — semantic color system.
- `LAYOUT.md` — grid, gutters, containers, density.
- `NAVIGATION.md` — header, sidebar, drawer, panel patterns.
- `SURFACES.md` — borders, radius, elevation, overlays.
- `MOTION.md` — duration/easing families and interaction rules.
- `COMPONENTS.md` — reusable component principles.
- `RESPONSIVE.md` — web/mobile transformation rules.
- `DO_DONT.md` — visual anti-patterns and preferred patterns.

Create or lock a file only when reference calibration or production work gives us enough evidence to make the rules useful.
