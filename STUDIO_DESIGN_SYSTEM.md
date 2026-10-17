# AI Studio Design System

Status: **calibrating**. This file stores durable studio-level visual rules that should survive across projects. Project/client branding may override them explicitly.

Do not lock arbitrary fonts, HEX colors, dimensions, or effects simply to make this file look complete. Unknown values remain provisional until reference calibration and live review justify them.

## 1. Core visual direction

Current durable direction:

- premium / high-quality without ornamental excess;
- calm editorial-tech rather than generic startup/AI hype;
- precise hierarchy and alignment;
- commercial clarity: important actions and information remain obvious;
- expressive when useful, restrained when not;
- motion should feel intentional and smooth, not constantly animated;
- visual decisions should survive desktop and mobile, not depend on one screenshot.

Avoid by default:

- generic neon / cyber-AI palettes;
- decorative glassmorphism without a functional reason;
- gratuitous gradients;
- excessive pill shapes / giant radii everywhere;
- shadows used as decoration instead of elevation/state;
- oversized empty layouts that harm content density or conversion;
- random visual values introduced per component.

## 2. Inheritance model

Every project uses two layers.

### Studio defaults

Reusable behavior and quality standards:

- hierarchy;
- spacing rhythm;
- grid logic;
- interaction quality;
- focus/hover/pressed/disabled behavior;
- motion philosophy;
- responsive principles;
- accessibility baseline;
- rendered visual QA.

### Project theme

Client-specific identity:

- brand colors;
- display/body typefaces;
- logo and marks;
- product photography / imagery;
- campaign art direction;
- domain-specific patterns;
- deliberate deviations from studio defaults.

Project rules win when explicitly confirmed. Studio defaults fill gaps; they do not erase client identity.

## 3. Token architecture

Use semantic tokens instead of scattering raw values through components.

### Typography roles

To calibrate:

- `font.display`
- `font.body`
- `font.mono` when needed
- `type.display-xl`
- `type.display-lg`
- `type.heading-1`
- `type.heading-2`
- `type.heading-3`
- `type.body-lg`
- `type.body`
- `type.body-sm`
- `type.label`
- `type.caption`

Rules to preserve:

- hierarchy must be obvious without relying only on color;
- body copy remains readable at realistic widths;
- display typography may be expressive; transactional UI typography must stay legible;
- letter spacing and line height are role-specific, not globally applied.

### Color roles

Exact palette: **TBD through calibration**.

Semantic roles should include at minimum:

- `bg.canvas`
- `bg.surface`
- `bg.elevated`
- `text.primary`
- `text.secondary`
- `text.muted`
- `border.default`
- `border.strong`
- `action.primary`
- `action.primary-hover`
- `action.secondary`
- `state.success`
- `state.warning`
- `state.danger`
- `focus.ring`

Do not make a project palette global merely because one client uses it.

### Spacing

Exact scale: **TBD through live calibration**.

Use a small deliberate scale. Components should derive spacing from the scale rather than inventing values locally. Dense transactional UI and editorial sections may use different rhythm while sharing the same underlying scale.

### Radius / border / elevation

Exact values: **TBD**.

Rules:

- radius communicates component family, not decoration;
- borders establish structure before shadows do;
- elevation indicates layering, overlays, floating controls, or state;
- subtle surfaces are preferred over stacking many visible containers.

### Motion

Exact durations/easing families: **TBD after reference review**.

Motion should communicate:

- continuity;
- navigation/state transition;
- focus/selection;
- feedback;
- hierarchy changes.

Avoid motion that delays common actions or exists only to show off.

## 4. Layout and composition

Durable rules:

- establish a clear grid before styling individual components;
- preserve a strong main alignment line on each screen;
- use whitespace to separate semantic groups, not to create artificial luxury;
- important commerce/product actions remain visible and scannable;
- sidebars, drawers and panels must have a clear information role;
- mobile reflow is designed intentionally rather than treated as compressed desktop.

Exact container widths, columns, gutters and breakpoint values remain TBD until calibration.

## 5. Navigation / sidebars / panels

To calibrate from references:

- global header behavior;
- desktop nav pattern;
- mobile nav pattern;
- persistent vs contextual sidebar;
- drawer width and layering;
- filters / sort panels;
- account / cart panels;
- sticky behavior;
- overlay / backdrop behavior.

Rules:

- persistent navigation should not compete with primary content;
- contextual panels should close predictably and preserve user state;
- a panel must justify its screen space through useful navigation, controls, or context;
- desktop sidebars should not be copied directly into mobile UI.

## 6. Component principles

Reusable component families should cover only repeated patterns. Candidate primitives:

- buttons / links;
- inputs / selects / checkboxes / radios;
- tabs / segmented controls;
- cards;
- badges / status;
- header / navigation;
- drawer / modal / popover;
- list / table patterns;
- product card and purchase controls when ecommerce becomes a repeated studio domain.

Do not standardize a component after one occurrence if its requirements are still unclear.

## 7. Reference calibration protocol

For visual calibration use:

**REFERENCE → REACTION → REASON → RULE → PROTOTYPE → LIVE REVIEW → ADJUST → LOCK**

A reference contributes only the specific behavior or pattern we choose. We do not inherit the whole site's identity.

Use `docs/REFERENCE_CAPTURE.md` during calibration sessions.

## 8. Quality gate

Substantial UI is not considered visually verified until a runnable version has been inspected in a real browser when practical.

Before locking a direction, check:

- desktop and mobile composition;
- typography hierarchy;
- spacing rhythm;
- component consistency;
- interactive states;
- overflow/breakpoints;
- contrast/accessibility basics;
- motion quality;
- whether the result still feels like the intended project rather than a generic template.

## 9. Promotion rule

A design decision becomes a **studio-level rule** only when at least one is true:

1. the user explicitly says it should apply across future projects;
2. repeated reference sessions show the same preference;
3. repeated production use demonstrates it is a strong reusable default.

Otherwise keep it project-local.
