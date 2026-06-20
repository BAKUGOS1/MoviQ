# MoviQ

**AI-native video editing and short-form clip intelligence platform.**

MoviQ converts long-form video into ranked, captioned, editable short clips through a rights-first workflow and a validated export pipeline.

```text
Upload -> Transcript -> Ranked Clips -> Web Editor -> Validated MP4 Export
```

This repository is the official build handoff for MoviQ. It contains the product strategy, PRD/TRD/SRS, premium UX v2, Design System v2, database/API/security/QA/deployment planning, and AI-ready implementation context.

---

## Product Positioning

MoviQ is designed for creators, agencies, marketing teams, educators, founders, and media operators who need to turn long-form video into polished short-form content without losing editorial control.

The product should feel like:

```text
A premium cinematic AI video workspace — not a generic SaaS dashboard.
```

The current visual authority is:

```text
UX Flow v2 Premium Blueprint + Design System v2 Cinematic Precision
```

Older UX/design files are reference-only. Implementation must follow V2.

---

## MVP Scope

### In Scope

- User authentication and workspace/project model
- Video upload with resumable/multipart behavior
- Media metadata extraction
- Transcript generation and review
- AI-ranked clip candidates
- Clip review and manual override
- Web editor for trimming, captions, layout, brand styling and export intent
- Render job orchestration
- Remotion composition + FFmpeg final authority
- R2/MinIO asset storage
- Supabase Postgres/Auth with RLS
- Temporal workflow orchestration
- LangGraph agent orchestration for AI/media workflows
- Observability, audit logs and QA gates

### Out of Scope for MVP

- Full social publishing automation
- Marketplace
- Full mobile editor parity
- Enterprise SSO
- Multi-language dubbing
- Realtime collaborative editing
- Advanced billing system

---

## Recommended Technical Stack

| Layer | Decision |
|---|---|
| Frontend | Next.js / React, JavaScript-first implementation allowed |
| UI | Tailwind + shadcn/ui + Radix primitives |
| Forms/Validation | React Hook Form + Zod |
| Editor State | Zustand |
| Server State | TanStack Query generated through Orval |
| Backend | Python FastAPI |
| Workflows | Temporal Python |
| AI Orchestration | LangGraph |
| Database/Auth | Supabase Postgres/Auth + RLS |
| Storage | Cloudflare R2 in production, MinIO locally |
| Rendering | Remotion composition service + FFmpeg final authority |
| Media Intelligence | FFmpeg/FFprobe, PySceneDetect, faster-whisper/WhisperX/Silero-style adapters |
| Testing | Pytest, Playwright, Testcontainers, visual regression, accessibility checks |
| Observability | OpenTelemetry/Langfuse-style tracing |

---

## Suggested Repository Structure

```text
moviq/
  apps/
    web/                 # Next.js web app and editor shell
    render-service/      # Remotion composition/render adapter
  services/
    api/                 # FastAPI API
    worker/              # Temporal workers and media jobs
  packages/
    ui/                  # shadcn-owned UI components
    config/              # shared env/config validation
    api-client/          # Orval generated client
    media-contracts/     # render/export schemas
  infra/
    docker/
    supabase/
    temporal/
    r2-minio/
  docs/
    md/
    adr/
  tests/
    e2e/
    visual/
    integration/
```

---

## Documentation Authority Order

When documents conflict, use this order:

1. `docs/md/00_MASTER_CONTEXT.md` — single-file AI handoff context
2. `docs/md/03_PRD_v3_Final.md` — product scope
3. `docs/md/05_TRD.md` — technical requirements
4. `docs/md/06_SRS.md` — formal requirements
5. `docs/md/07_UX_Flow_v2_Premium_Blueprint.md` — UX behavior and screen architecture
6. `docs/md/08_Design_System_v2_Cinematic_Precision.md` — visual implementation authority
7. `docs/md/13_Implementation_Plan_v2_2.md` — implementation sequencing
8. `docs/adr/ADR-UI-001_Glass_UI_Refresh.md` — UI refresh decision record

---

## AI Usage

For Codex, Claude, Gemini, Cursor, Windsurf, or ChatGPT agents:

- Start with `00_START_HERE.md`.
- Then read `docs/md/00_MASTER_CONTEXT.md`.
- Use `docs/md/` for feature-specific planning.
- Use PDFs only for human review/layout checking, not AI ingestion.

Recommended instruction:

```text
You are the lead product engineer for MoviQ. Read docs/md/00_MASTER_CONTEXT.md first. Build only the MVP vertical slice: Upload -> Transcript -> Ranked Clips -> Web Editor -> Validated MP4 Export. Use the V2 UX and Design System as final UI authority. Do not implement marketplace, social publishing automation, enterprise SSO, or non-MVP features unless explicitly requested. Before coding, create a phase-by-phase task plan with file structure, migrations, API contracts, test gates, and risk controls.
```

---

## Required Before Real Deployment

Documentation is ready. Before production deployment, still lock:

- Final product logo/name
- Supabase project and environment URLs
- Cloudflare R2 bucket names and credentials
- AI model/provider keys and budget limits
- Deployment target/domain
- Legal/privacy/copyright wording

---

## Current Status

**Status:** Documentation and build handoff repository initialized.  
**Implementation:** Not started in this repo yet.  
**Next step:** Generate the MVP implementation plan from `docs/md/00_MASTER_CONTEXT.md`, then scaffold `apps/`, `services/`, `packages/`, `infra/`, and `tests/`.
