# MoviQ Research Document Summary

## Research Direction

MoviQ is positioned between automated short-form clip tools and professional video editors. The opportunity is to combine AI-assisted clip discovery with a premium human-controlled editor and reliable export pipeline.

## Competitive Categories

- Text-based video editors
- AI clip generators
- Browser video editors
- Caption tools
- Creator workflow platforms

## Product Implications

- Users need explainable AI suggestions.
- Clip ranking must be editable and reviewable.
- Export reliability matters as much as AI quality.
- The editor must feel premium because perceived quality influences trust.
- Accessibility and fallback design are required for glass UI.

## Technical Implications

- Use FFmpeg/FFprobe as final media authority.
- Use Temporal for durable workflow orchestration.
- Use LangGraph for stateful AI/media workflows.
- Use Supabase RLS for workspace isolation.
- Use R2/MinIO storage abstraction.
- Use Remotion for composition and final export flow.

## Final Research Conclusion

Build a focused MVP vertical slice first. Defer marketplace, social automation and enterprise features until the core workflow proves reliable.
