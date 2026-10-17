---
name: studio-design
description: Apply the AI Studio visual language to substantial website, app, dashboard, ecommerce, landing-page, or product UI work. Use when calibrating references, defining or extending design tokens, planning visual direction, implementing key screens, or reviewing UI quality. Read the studio design system and project context first; inherit global rules, allow explicit client-brand overrides, and verify rendered UI in a real browser when possible.
---

# Studio Design Workflow

This skill keeps design work fast without letting the visual language drift between projects.

## 1. Read the source of truth first

Before substantial UI work, read when present:

1. `AGENTS.md`
2. `PROJECT_BRIEF.md`
3. `PROJECT_STATE.md`
4. `STUDIO_DESIGN_SYSTEM.md`
5. project-specific design/token files
6. `docs/REFERENCE_CAPTURE.md` or the project's reference notes

Do not ask for information already present in those files.

## 2. Separate studio DNA from client branding

Treat the design system as two layers:

- **Studio layer:** hierarchy, spacing discipline, composition, interaction quality, motion philosophy, component behavior, responsiveness, accessibility, and QA standards.
- **Project layer:** client colors, fonts, logo, photography, product imagery, campaign art direction, domain-specific components, and explicit brand rules.

A project may override the studio layer only when the brief or calibrated references give a concrete reason. Do not make every client look identical just because the studio has defaults.

## 3. Calibrate from references instead of copying whole sites

For each useful reference, capture the exact element or behavior that matters: typography, header, sidebar, navigation, grid, hero, card, product gallery, checkout step, shadow, transition, motion curve, microinteraction, or responsive behavior.

Convert observations into reusable rules:

**REFERENCE → REACTION → REASON → RULE → PROTOTYPE → LIVE REVIEW → ADJUST → LOCK**

Do not copy an entire site's identity. Extract specific principles and patterns.

## 4. Lock tokens in the correct order

Do not create random one-off values while implementing screens. Prefer semantic tokens and lock them progressively:

1. typography roles and scale;
2. color roles and contrast;
3. spacing rhythm and layout grid;
4. radii and borders;
5. elevation / shadows / surfaces;
6. motion durations and easing families;
7. component states;
8. responsive behavior.

Unknown values stay explicitly provisional. Do not invent final fonts, HEX values, or component geometry merely to remove a placeholder.

## 5. Build the smallest useful visual proof

For a new project, prefer one strong rendered screen or flow before producing a large static design set.

Good first proofs include:

- ecommerce homepage + one product card language;
- product detail hero + gallery + purchase controls;
- dashboard shell + navigation + one data surface;
- landing-page hero + one content section + CTA behavior.

The goal is to validate the visual language quickly, not to finish every screen before learning anything.

## 6. Use specialist capabilities deliberately

When available and relevant:

- use `frontend-design`, `ui-ux-pro-max`, and `web-design-guidelines` for specialist UI reasoning;
- use `agent-browser` for rendered inspection, screenshots, responsive checks, and interaction QA;
- use `copywriting` only when interface or marketing copy materially affects the design;
- use connected Figma/Product Design capabilities for editable design exploration when that is faster than coding the proof directly.

Do not stack tools merely because they exist.

## 7. Prevent visual drift during implementation

- Reuse tokens and shared primitives instead of introducing arbitrary values in individual components.
- Avoid generic AI-neon, gratuitous glassmorphism, gradients, giant rounded cards, or decorative shadows unless the calibrated direction explicitly calls for them.
- Motion must explain hierarchy, continuity, state change, or feedback; animation is not decoration by default.
- Dense information needs stronger hierarchy, not more containers.
- Premium does not mean empty: maintain commercial clarity, scannability, and conversion paths.
- Desktop and mobile should express the same visual language, not become unrelated designs.

## 8. Rendered QA is mandatory for substantial UI

When a runnable page exists, verify the rendered result rather than judging source code alone.

At minimum inspect:

- a representative desktop viewport;
- a representative mobile viewport;
- typography hierarchy and line lengths;
- spacing rhythm and alignment;
- hover/focus/pressed/disabled states where relevant;
- overflow and responsive breakpoints;
- obvious accessibility / contrast problems;
- animation behavior and jank;
- visual consistency with the locked design rules.

If browser verification is unavailable, say so explicitly.

## 9. Update durable design state

When a preference is clearly validated and reusable across projects, update `STUDIO_DESIGN_SYSTEM.md`.

When it is specific to one client/project, keep it in that project's design files instead.

Do not promote a one-off preference into the studio system after seeing it once. Repeated preference or explicit user approval is the threshold for a durable studio rule.
