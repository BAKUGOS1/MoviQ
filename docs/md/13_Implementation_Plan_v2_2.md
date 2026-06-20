# MoviQ Implementation Plan v2.2

Build the MVP vertical slice first:

```text
Upload -> Transcript -> Ranked Clips -> Web Editor -> Validated MP4 Export
```

## Phases

1. Repository scaffold and environment checks
2. Supabase schema, roles and RLS baseline
3. FastAPI service and OpenAPI contract
4. Upload and media asset ingestion
5. Temporal processing workflow
6. Transcript and clip intelligence
7. Premium web editor from UX Flow v2
8. Render and export pipeline
9. QA gates and deployment readiness

## Required Build Rules

- Use UX Flow v2 and Design System v2 for UI.
- Keep MVP scope strict.
- Use semantic tokens, not hardcoded UI values.
- Use RLS for workspace-scoped data.
- Use Remotion plus FFmpeg for final render authority.
- Add tests for API, database rules, workflows, editor UX and export validation.

## First Coding-Agent Task

Read `docs/md/00_MASTER_CONTEXT.md`, then return a phase-by-phase implementation plan and file tree before coding.
