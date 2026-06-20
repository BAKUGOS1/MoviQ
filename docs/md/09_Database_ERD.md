# MoviQ Database ERD Summary

## Core Tables

- `users`
- `workspaces`
- `workspace_members`
- `projects`
- `media_assets`
- `transcripts`
- `transcript_segments`
- `clip_candidates`
- `editor_projects`
- `timeline_tracks`
- `timeline_items`
- `caption_styles`
- `render_jobs`
- `render_artifacts`
- `ai_runs`
- `audit_events`
- `usage_events`

## Relationship Model

- Workspace owns projects.
- Workspace members define user access.
- Project owns media assets, transcripts, clip candidates, editor state and render jobs.
- Render job produces render artifacts.
- AI runs attach to processing and clip generation stages.
- Audit events capture important workspace/project actions.

## Role Hierarchy

| Role | Level |
|---|---:|
| viewer | 0 |
| editor | 1 |
| admin | 2 |
| owner | 3 |

## Data Rules

- Every workspace-scoped table should include `workspace_id`.
- Project-scoped rows should also include `project_id` where applicable.
- RLS policies should enforce workspace membership and role level.
- Worker access should be tied to valid processing/render jobs.
