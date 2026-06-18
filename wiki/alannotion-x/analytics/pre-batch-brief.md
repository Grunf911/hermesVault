# Latest Pre-Batch Feedback Brief

Status: initialized — XContent Calendar is now the canonical schedule/analytics layer.

## Current lesson to inject

Use the approved hypothesis until replaced by data:

> Concrete lived-detail posts about busy-parent creator systems should be tested against generic quote/advice posts.

## Batch constraints for the next Typefully batch

- Scheduling approval update: autonomous Typefully scheduling is allowed if XContent Calendar is kept in sync.
- Keep one-variable discipline: do not change cadence, lane mix, hook style, and CTA style all at once.
- Include metadata in Typefully draft titles/scratchpad when possible: campaign, lane, format, hypothesis.
- Prioritize posts that tie AI/Notion systems to real family/time leverage.

## Open questions

- Backfill scheduled Typefully posts into XContent Calendar where missing.
- Decide whether existing scheduled Typefully drafts should be enriched with scratchpad metadata or only XContent Calendar metadata.


## Canonical database

Use XContent Calendar / `X_Calendar_DB` for this workflow. Do not use MainDB.

- Data source ID: `375fca35-4191-80d6-973e-000b754b5e60`
- Every Typefully scheduled post should have a matching XContent Calendar row.
- Analytics should update that same row using `Typefully Draft ID`, `Published URL`, and `X Post ID` matching where available.
- Approval is no longer required for autonomous Typefully scheduling if the calendar row is kept in sync.
