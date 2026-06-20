# MoviQ API Documentation Summary

## API Principles

- FastAPI backend.
- OpenAPI-first contract.
- Generated frontend client through Orval.
- Consistent validation errors.
- Workspace-aware authorization.

## Endpoint Groups

| Group | Purpose |
|---|---|
| `/auth/session` | Session and identity context |
| `/workspaces` | Workspace selection and members |
| `/projects` | Project CRUD |
| `/media-assets` | Upload and asset metadata |
| `/transcripts` | Transcript and segments |
| `/clip-candidates` | AI-ranked clip review |
| `/editor-projects` | Editor state |
| `/render-jobs` | Render lifecycle |
| `/exports` | Completed export artifacts |
| `/health` | Runtime health |

## Standard Response Rules

- Use typed schemas.
- Return trace IDs for failures.
- Keep user-facing error copy clear.
- Do not expose internal stack details.
