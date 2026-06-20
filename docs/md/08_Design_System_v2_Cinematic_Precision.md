# MoviQ Design System v2 — Cinematic Precision

**Status:** Final visual/UI authority.

MoviQ should feel like a premium cinematic AI video workspace, not a generic SaaS dashboard.

```text
Graphite cinematic base + controlled glass surfaces + violet/sky/rose accents + opaque accessibility fallbacks
```

## Visual Personality

| Trait | Direction |
|---|---|
| Premium | Cinematic, precise, calm, high-contrast |
| AI-native | Intelligent recommendations and explainable feedback |
| Editor-first | Preview/timeline clarity above decoration |
| Fresh | Violet/sky accents instead of old maroon/gold-heavy UI |
| Accessible | Readability always wins |

## Token Families

| Family | Purpose |
|---|---|
| Graphite | Main backgrounds and editor canvas |
| Glass | Sidebars, inspector, floating bars and cards |
| Violet | Primary actions and selected AI intelligence |
| Sky | Processing, upload, export, progress |
| Rose | Brand warmth and selective highlight |
| Semantic | Success, warning, danger, info |
| Neutrals | Text, borders, structure |

## Core Colors

| Token | Value | Use |
|---|---|---|
| `--background` | `#07080D` | Primary app/editor base |
| `--foreground` | `#F8FAFC` | Main text |
| `--muted-foreground` | `#94A3B8` | Secondary text |
| `--surface` | `#11131B` | Opaque panels |
| `--surface-glass` | `rgba(255,255,255,0.07)` | Standard glass surface |
| `--surface-glass-strong` | `rgba(255,255,255,0.12)` | Strong glass surface |
| `--border-glass` | `rgba(255,255,255,0.14)` | Glass borders |
| `--primary` | `#8B5CF6` | AI/primary action |
| `--accent-sky` | `#38BDF8` | Progress/export |
| `--accent-rose` | `#F43F5E` | Selective emphasis |
| `--success` | `#22C55E` | Success |
| `--warning` | `#F59E0B` | Warning |
| `--danger` | `#EF4444` | Error/destructive |

## Material Rules

Glass is a progressive enhancement, not a universal surface.

Use glass for app shell, top command bar, clip candidate cards, AI panel, editor inspector, floating timeline controls, export modal and progress overlays.

Use opaque surfaces for dense data, legal text, permission tables, critical dialogs, long forms and detailed errors.

Every glass component must provide an opaque fallback for unsupported browsers, reduced transparency preference, low-end devices and video backgrounds with poor contrast.

## Typography

Recommended primary font: Inter or comparable modern UI sans.

Editor UI must prioritize legibility over style. Labels, timeline markers, transcript rows and export states must remain readable at all times.

## Components

Core components:

- Button
- Input
- Textarea
- Select
- Dialog
- Sheet
- Tabs
- Tooltip
- Toast
- Badge
- Progress
- Card
- Command menu

MoviQ-specific components:

- Project card
- Upload dropzone
- Processing stage tracker
- Clip candidate card
- AI reason panel
- Transcript segment row
- Caption editor row
- Timeline track
- Timeline item
- Trim handle
- Safe-zone overlay
- Export status card
- Render artifact card

## Editor Anatomy

The editor uses four primary zones:

```text
Top command bar
Left transcript/AI panel
Center preview canvas
Right inspector panel
Bottom timeline
```

## Accessibility

- Text contrast must meet WCAG AA target.
- Focus rings must stay visible.
- Status states must not rely on color alone.
- Reduced motion must be respected.
- Reduced transparency must be supported.
- Keyboard support is required for critical editor actions.
- Captions and transcript must remain readable.

## Implementation Contract

Use Tailwind CSS variables, shadcn/ui owned components, Radix primitives, Storybook, Playwright visual regression and accessibility checks.

Implementation must use `assets/design/tokens-v2.css` and should avoid hardcoded colors in product components.

## Acceptance Criteria

Design implementation is acceptable when:

- UI looks premium and editor-first.
- Dashboard does not look like a generic SaaS template.
- Editor hierarchy is obvious.
- Glass surfaces are controlled and readable.
- Opaque fallback works.
- V2 tokens are used consistently.
- Component states are documented in Storybook.
