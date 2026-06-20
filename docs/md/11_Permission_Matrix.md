# MoviQ Permission Matrix

Roles:

- viewer: read permitted workspace/project content
- editor: edit clips, captions and timelines
- admin: manage workspace projects and members
- owner: full workspace authority

Role levels:

```text
viewer = 0
editor = 1
admin = 2
owner = 3
```

Core rules:

- View access starts at viewer.
- Upload, clip editing, caption editing, timeline editing and export start at editor.
- Member and project administration starts at admin.
- Workspace ownership actions require owner.
- API checks and database policies must agree.
- Important actions must be audited.
