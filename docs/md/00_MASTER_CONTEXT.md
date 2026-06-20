# MoviQ Master Context

This is the AI-ready master context for building MoviQ.

## Product One-Liner

MoviQ is an AI-native video editing and short-form clip intelligence platform that turns long-form video into ranked, captioned, editable short clips through a rights-first workflow and validated export pipeline.

```text
Upload -> Transcript -> Ranked Clips -> Web Editor -> Validated MP4 Export
```

## Product Thesis

MoviQ should not behave like a generic social clip generator. The product must combine AI-assisted clip discovery with human editorial control, reliable rendering, workspace permissions, and a premium cinematic web editor.

The strongest moat is not only clip ranking; it is the complete workflow from media ingestion to validated export.

## MVP Boundary

### In Scope

- Authentication
- Workspace/project model
- Video upload
- Media metadata extraction
- Transcript creation and review
- AI-ranked clip candidates
- Manual clip selection/override
- Web editor with preview, trimming, caption editing, layout/style controls and export intent
- Render job creation
- Remotion composition service
- FFmpeg/FFprobe final media authority
- Cloudflare R2 storage in production; MinIO locally
- Supabase Postgres/Auth with RLS
- Temporal workflow orchestration
- LangGraph AI/media workflow orchestration
- Observability and audit events
- QA, accessibility and visual-regression gates

### Out of Scope for MVP

- Marketplace
- Full social publishing automation
- Enterprise SSO
- Mobile editor parity
- Realtime collaboration
- Advanced billing
- Multi-language dubbing
- Automated reposting/farming workflows

## Non-Negotiable Product Principles

1. **Rights-first:** Do not build around platform bypass, DRM evasion, or unauthorized reposting.
2. **Human-in-the-loop:** AI suggests; the editor/user approves.
3. **Render reliability:** FFmpeg/FFprobe are final authority for media output validation.
4. **Local-first preview, hosted final render:** Browser editor should feel responsive, but final MP4 is server-validated.
5. **Workspace security:** Supabase RLS and app-level role checks must be enforced.
6. **Premium UX:** Follow UX Flow v2 and Design System v2; no generic SaaS layout.
7. **MVP discipline:** Build the vertical slice first.

## Final UI Authority

Use these documents as final UI authority:

- `docs/md/07_UX_Flow_v2_Premium_Blueprint.md`
- `docs/md/08_Design_System_v2_Cinematic_Precision.md`
- `assets/design/tokens-v2.css`
- `docs/adr/ADR-UI-001_Glass_UI_Refresh.md`

Visual direction:

```text
Graphite cinematic editor + controlled glass surfaces + violet/sky/rose accents + accessible opaque fallbacks
```

## Recommended Tech Stack

| Area | Decision |
|---|---|
| Web | Next.js / React |
| UI | Tailwind + shadcn/ui + Radix primitives |
| Forms | React Hook Form + Zod |
| Editor State | Zustand |
| Server State | TanStack Query |
| API Client | Orval generated from OpenAPI |
| Backend | Python FastAPI |
| Database | Supabase Postgres |
| Auth | Supabase Auth + JWT claims + app role checks |
| RLS | Supabase/Postgres RLS with workspace isolation |
| Worker | Python worker services |
| Workflow | Temporal Python |
| AI Flow | LangGraph |
| Storage | Cloudflare R2 + MinIO local |
| Render | Remotion service + FFmpeg final authority |
| Media | FFmpeg/FFprobe, scene detection, transcription adapters |
| Testing | Pytest, Playwright, Testcontainers, visual regression, axe accessibility checks |
| Observability | OpenTelemetry/Langfuse-style traces |

## Required Repository Shape

```text
apps/web
apps/render-service
services/api
services/worker
packages/ui
packages/config
packages/api-client
packages/media-contracts
infra/docker
infra/supabase
infra/temporal
infra/r2-minio
docs/md
docs/adr
tests/e2e
tests/visual
tests/integration
```

## Core User Journey

1. User signs in.
2. User creates or selects workspace.
3. User creates project.
4. User uploads long-form video.
5. System records asset metadata and creates processing job.
6. Worker extracts media metadata and transcript.
7. AI ranks clip candidates with reason, hook, confidence and suggested caption style.
8. User reviews candidate clips.
9. User opens editor.
10. User adjusts timing, captions, layout, brand style and safe zones.
11. User exports.
12. Temporal orchestrates render.
13. Remotion prepares composition.
14. FFmpeg validates/finalizes MP4.
15. Output is stored in R2 and shown in project export history.

## Primary Entities

- users
- workspaces
- workspace_members
- projects
- media_assets
- transcripts
- transcript_segments
- clip_candidates
- editor_projects
- timeline_tracks
- timeline_items
- caption_styles
- render_jobs
- render_artifacts
- audit_events
- ai_runs
- usage_events

## Required Roles

| Role | Level | Purpose |
|---|---:|---|
| viewer | 0 | View project/assets where permitted |
| editor | 1 | Edit clips/timeline/captions |
| admin | 2 | Manage members/projects/settings |
| owner | 3 | Full workspace authority |

Role hierarchy must be numeric and explicit.

## RLS Requirements

- Every workspace-scoped table must include `workspace_id`.
- Policies must verify workspace membership.
- Worker policies must verify job ownership and workspace association.
- Do not use generic elevated DB connection for API runtime.
- Use separate API, worker and migration credentials.
- SECURITY DEFINER functions must use safe fixed `search_path`, fully qualified tables, explicit grants and no unsafe dynamic SQL.

## API Groups

- `/auth/session`
- `/workspaces`
- `/projects`
- `/media-assets`
- `/transcripts`
- `/clip-candidates`
- `/editor-projects`
- `/render-jobs`
- `/exports`
- `/audit-events`
- `/health`

API contracts must be OpenAPI-first. The frontend client should be generated through Orval and consumed with TanStack Query.

## Render Contract

- Browser preview is not final authority.
- Final MP4 must be validated server-side.
- Render artifacts need deterministic R2 keys.
- Export must define resolution, FPS, pixel format, audio codec, caption burn-in behavior, safe-zone behavior and retention policy.
- Failed render jobs must expose user-readable failure reason and internal trace ID.

## UX Requirements

The interface must prioritize:

- Clear project status
- Fast clip review
- Editor confidence
- Caption readability
- Strong timeline hierarchy
- Recovery from processing/render failures
- Accessible keyboard/focus behavior
- No hidden destructive actions

## Design System Requirements

- Graphite cinematic editor background
- Controlled glass only where useful
- Opaque fallback for every glass surface
- Strong contrast for text/video-adjacent panels
- Violet primary action and AI selection language
- Sky processing/progress language
- Rose highlight sparingly
- shadcn-owned components with Radix accessibility
- Storybook states for all editor-critical components

## QA Gates

- Unit tests for validation and service logic
- Integration tests with database/RLS
- Worker workflow tests
- API contract tests
- Playwright E2E for MVP happy path
- Visual regression for premium UI surfaces
- Accessibility checks for keyboard/focus/contrast
- Render validation using FFprobe output
- Security checks for RLS and role boundary

## First Build Milestones

1. Repo scaffold and environment validation
2. Supabase schema + RLS baseline
3. FastAPI skeleton + OpenAPI contracts
4. Upload and asset ingestion
5. Media metadata and transcript workflow
6. Clip candidate generation
7. Editor shell and state model
8. Render job orchestration
9. Export artifact validation
10. QA gates and release readiness

## Implementation Instruction For AI Agents

Do not begin coding by guessing UI. First read:

1. `README.md`
2. `00_START_HERE.md`
3. `docs/README.md`
4. `docs/md/07_UX_Flow_v2_Premium_Blueprint.md`
5. `docs/md/08_Design_System_v2_Cinematic_Precision.md`
6. `docs/adr/ADR-UI-001_Glass_UI_Refresh.md`

Then produce a build plan before implementation.
