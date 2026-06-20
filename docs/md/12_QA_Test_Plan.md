# MoviQ QA Test Plan

## QA Objective

Verify the MVP loop from upload to validated export.

## Test Areas

- Authentication and workspace selection
- Project creation
- Upload and asset ingestion
- Processing states
- Transcript review
- Clip candidate review
- Editor shell and timeline state
- Caption editing
- Render job lifecycle
- Export artifact validation
- Permissions
- Accessibility
- Visual regression

## Required E2E Flow

```text
Sign in -> Create project -> Upload media -> Wait for processing -> Review clips -> Open editor -> Edit captions/timeline -> Start export -> Validate completed export
```

## Visual QA

Use Design System v2. Test dashboard, upload, processing, clip review, editor and export surfaces. Include glass and opaque fallback states.

## Release Gate

Release only when the full MVP flow passes and failures have clear recovery paths.
