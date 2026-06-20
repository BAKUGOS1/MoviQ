# MoviQ UX Flow v2 — Premium Blueprint

**Status:** Final UX authority  
**Use:** Screen architecture, user journeys, interaction behavior, recovery states, responsive rules.  
**Important:** This replaces the older UX Flow v1.

---

## 1. UX Goal

MoviQ must feel like a premium cinematic AI video workspace, not a generic dashboard. The UX should help users move confidently through:

```text
Upload -> Transcript -> Ranked Clips -> Editor -> Validated Export
```

Every screen must answer three questions:

1. What is happening?
2. What should I do next?
3. Can I trust the output?

---

## 2. Primary Navigation

| Area | Purpose |
|---|---|
| Dashboard | Project overview and recent processing/export states |
| Project Detail | Source video, transcript, clip candidates, export history |
| Upload | Controlled ingestion and metadata readiness |
| Processing | Workflow progress, failure recovery, retry states |
| Clip Review | AI-ranked clips with reasons and manual override |
| Editor | Timeline, preview, transcript/caption controls and export intent |
| Export | Render status, validation, download/share-ready artifact |
| Settings | Workspace, members, brand, storage, permissions |

---

## 3. Key Screens

### 3.1 Dashboard

Purpose: let user quickly understand project status and resume work.

Required sections:

- Top command bar with create/upload action
- Project cards with status chips
- Recent exports
- Failed/retry-required jobs
- Workspace switcher

Premium rule: avoid dense SaaS cards. Use cinematic spacing, strong hierarchy and controlled glass cards.

### 3.2 Upload Screen

Purpose: make ingestion safe, clear and recoverable.

States:

- Empty state
- Drag active
- File selected
- Uploading
- Upload paused/retry
- Upload completed
- Unsupported file
- Rights confirmation required

Required UI:

- Large drop zone
- Supported formats note
- File metadata preview
- Rights-first checkbox/notice
- Progress indicator
- Retry/resume action

### 3.3 Processing Screen

Purpose: explain AI/media work without making user wait blindly.

Stages:

1. Upload received
2. Metadata extraction
3. Transcript generation
4. Scene/segment analysis
5. Clip ranking
6. Editor draft preparation

Required UI:

- Step timeline
- Estimated progress
- Current stage label
- Trace/retry-safe error copy
- Background continuation note

### 3.4 Clip Review Screen

Purpose: let the user evaluate AI-ranked clips quickly.

Each clip candidate must show:

- Preview thumbnail/video scrub
- Hook title
- Score/confidence
- Duration
- Start/end timestamp
- Why this clip was selected
- Caption style preview
- Actions: Open in Editor, Save, Reject, Duplicate, Adjust

### 3.5 Editor Screen

The editor is the core product experience.

Required zones:

```text
┌──────────────────────────────────────────────┐
│ Top Bar: Project / Undo / Redo / Export       │
├──────────────┬───────────────────┬───────────┤
│ Transcript   │ Video Preview      │ Inspector │
│ Clips / AI   │ Safe Zones         │ Style     │
├──────────────┴───────────────────┴───────────┤
│ Timeline: tracks, captions, markers, trim     │
└──────────────────────────────────────────────┘
```

Editor must support:

- Timeline item selection
- Trim handles
- Caption segment editing
- Safe-zone preview
- Brand style application
- AI recommendations panel
- Undo/redo
- Autosave indicator
- Export intent panel

### 3.6 Export Screen

Purpose: make render status trustworthy.

Required states:

- Ready to render
- Render queued
- Rendering
- Validation
- Completed
- Failed with recovery

Required output details:

- Resolution
- FPS
- Duration
- File size if available
- Codec/pixel format validation
- Download action
- Re-render action

---

## 4. Interaction Principles

- AI recommendations must always explain why.
- Destructive actions require confirmation.
- Processing failures need retry paths.
- Editor autosave must be visible.
- Export must never imply success until validation completes.
- Keyboard navigation must work for editor-critical controls.
- Timeline controls need large enough hit targets.

---

## 5. Recovery States

| Failure | UX Response |
|---|---|
| Upload interrupted | Resume/retry upload |
| Unsupported media | Explain supported formats |
| Transcript failed | Retry transcript or allow manual import |
| No strong clips found | Show manual selection flow |
| Render failed | Show stage, reason, retry and trace ID |
| Permission denied | Explain required role/action |
| Network lost | Preserve local state and retry sync |

---

## 6. Responsive Behavior

| Viewport | Behavior |
|---|---|
| Desktop | Full editor with transcript, preview, inspector and timeline |
| Tablet | Collapsible side panels, persistent preview/timeline |
| Mobile | Review/status mode only; full editor parity deferred |

MVP should prioritize desktop/editor quality over mobile parity.

---

## 7. Accessibility

- Visible focus rings on all controls
- Keyboard navigation for core actions
- Non-color-only status signals
- Caption editor readable at all times
- Reduced motion support
- Reduced transparency fallback
- Strong contrast on video-adjacent glass surfaces

---

## 8. Analytics Events

Track:

- `project_created`
- `upload_started`
- `upload_completed`
- `processing_started`
- `transcript_completed`
- `clip_candidate_accepted`
- `clip_candidate_rejected`
- `editor_opened`
- `timeline_item_trimmed`
- `caption_edited`
- `export_started`
- `export_completed`
- `export_failed`

---

## 9. Acceptance Criteria

The UX is acceptable when:

- A new user can complete the MVP loop without support.
- AI suggestions are explainable and editable.
- Export status is clear and validated.
- Editor feels premium, focused and non-generic.
- Failure states are recoverable.
- V2 Design System components are used consistently.
