# MoviQ SRS — Software Requirements

## System Purpose

MoviQ enables a user to upload long-form video, generate transcript and ranked clip candidates, edit selected clips in a web editor, and export validated MP4 files.

## Functional Requirements

- User can sign in.
- User can create/select workspace.
- User can create project.
- User can upload video.
- System can show upload and processing state.
- System can generate or attach transcript.
- System can create ranked clip candidates.
- User can accept, reject or edit a candidate.
- User can open a clip in editor.
- User can edit timing, captions, layout and style.
- User can start export.
- System can show render progress.
- System can provide completed export artifact.

## Non-Functional Requirements

- Secure workspace isolation.
- Fast editor interaction.
- Clear failure recovery.
- Accessible keyboard and focus behavior.
- Reliable render validation.
- Observable workflows and traceable errors.

## Acceptance

The MVP is acceptable when a user can complete the full loop from upload to validated export without engineering assistance.
