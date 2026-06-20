# MoviQ TRD — Technical Requirements

MoviQ MVP technical stack:

- Next.js / React web app
- Tailwind + shadcn/ui + Radix
- FastAPI backend
- Supabase Postgres/Auth
- Temporal Python workflows
- LangGraph AI orchestration
- Cloudflare R2 / MinIO storage
- Remotion render service
- FFmpeg media validation

## Main Technical Requirements

- Build the MVP vertical slice first.
- Keep frontend, API, worker and render service separated.
- Use OpenAPI contracts for API design.
- Generate frontend client from API schema.
- Use workspace-scoped data model.
- Use V2 UX and Design System for all UI work.
- Validate export output before marking render complete.
- Add tests for API, database, editor, workflows and export flow.
