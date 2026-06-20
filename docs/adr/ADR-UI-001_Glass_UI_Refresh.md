# ADR-UI-001: Glass UI Refresh for MoviQ

**Status:** Accepted  
**Date:** 2026-06-20  
**Decision Owner:** MoviQ Product / Design / Engineering

## Context

The earlier MoviQ visual direction used a heavier maroon/gold premium palette. It communicated luxury, but it also risked feeling dated and less aligned with a modern AI video editor.

MoviQ needs a fresh, cinematic, AI-native product interface that supports dense editor workflows without sacrificing readability.

## Decision

MoviQ will use **Design System v2 — Cinematic Precision** as the final visual authority.

Accepted direction:

```text
Graphite Glass + Violet/Sky/Rose Accents + Cinematic Editor Focus
```

The old maroon/gold treatment may remain as minor brand heritage, but it is not the primary application UI palette.

## Rules

- Glass is a progressive enhancement, not the whole interface.
- Every glass surface needs an opaque fallback.
- Text contrast and editor readability are more important than decorative blur.
- AI and selected states use violet.
- Progress and export states use sky/electric blue.
- Rose is used only as selective emphasis.
- Status colors remain semantic and independent from brand colors.

## Use Glass For

- App shell/sidebar
- Command bar
- Clip candidate cards
- AI analysis panel
- Editor inspector
- Floating timeline controls
- Export modal
- Toast/progress overlays

## Use Opaque Surfaces For

- Dense tables
- Legal/compliance text
- Permission screens
- Destructive confirmation
- Long forms
- Detailed errors

## Affected Docs

| Document | Treatment |
|---|---|
| PRD / BRD / TRD / SRS | No major product logic change |
| UX Flow | Use v2 premium blueprint |
| Design System | v2 is authority |
| QA Test Plan | Include glass contrast, fallback and visual regression |
| Implementation Plan | Reference v2 design tokens and components |
| README | Mention v2 authority |

## Non-Goals

This ADR does not change database schema, API contracts, permission model, RLS, Temporal workflows, LangGraph architecture, rendering pipeline or business model.

## Outcome

Any future UI implementation, Figma work, Storybook setup or web-app styling must use UX Flow v2, Design System v2 and this ADR as source of truth.
