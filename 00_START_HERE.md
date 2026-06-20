# Start Here — MoviQ

Use this repository as the final handoff for building MoviQ.

## Open First

1. `README.md` — product and repo overview
2. `docs/md/00_MASTER_CONTEXT.md` — AI/Codex/Claude/Gemini handoff context
3. `docs/README.md` — document index and authority order
4. `docs/md/07_UX_Flow_v2_Premium_Blueprint.md` — final UX authority
5. `docs/md/08_Design_System_v2_Cinematic_Precision.md` — final visual/UI authority
6. `docs/adr/ADR-UI-001_Glass_UI_Refresh.md` — UI design decision record

## Build Scope

Build only the MVP vertical slice first:

```text
Upload -> Transcript -> Ranked Clips -> Web Editor -> Validated MP4 Export
```

## Do Not Start With

- Marketplace
- Full social publishing automation
- Enterprise SSO
- Realtime collaboration
- Mobile editor parity
- Billing/subscriptions

These are post-MVP unless explicitly approved.

## Important Authority Rule

Use **UX Flow v2** and **Design System v2**. Older design files are historical reference only.

## Recommended AI Prompt

```text
You are the lead engineer for MoviQ. Read docs/md/00_MASTER_CONTEXT.md first. Build the MVP only: Upload -> Transcript -> Ranked Clips -> Web Editor -> Validated MP4 Export. Use UX Flow v2 and Design System v2 as final UI authority. Before coding, return a phase-by-phase implementation plan, file tree, database migrations, API contracts, test gates, and risk controls.
```
