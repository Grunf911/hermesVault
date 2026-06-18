---
title: AlanNotion X Analytics Feedback Loop
created: 2026-06-18
type: operating-system
owner: Hermes / alannotion-x-analytics
---

# AlanNotion X Analytics Feedback Loop

Purpose: close the loop between Typefully scheduling, X performance, analytics, and the next content batch without letting the system mutate public marketing without Alan's approval.

## Loop

```text
Typefully queue → Published X posts → Typefully/X metrics → Analytics read → One-variable test → Ideation/Ghostwriting constraints → Next approved Typefully batch
```

## Guardrails

- Analytics may update logs, briefs, and recommendations autonomously.
- Analytics may influence future drafts and batch briefs.
- Analytics must not publish, reschedule, delete, or rewrite public content without Alan's explicit approval.
- Only one strategy variable changes per week unless Alan overrides it.
- Compare against AlanNotion baseline first: 200 impressions, 4 likes, 1 reply, 1 bookmark.
- Treat early low-volume metrics as weak signals, not proof.

## Files

| File | Purpose |
|---|---|
| `performance-log.jsonl` | Append/update-style records for scheduled/published posts and checkpoint metrics. |
| `feedback-loop-state.json` | Current baseline, active experiment, cron/job state, and latest report pointers. |
| `weekly-trend-log.md` | Human-readable index of weekly insights and one-variable tests. |
| `pre-batch-brief.md` | Latest constraints to inject before the next Typefully batch. |
| `weekly-reports/` | Full weekly analytics reports. |
| `snapshots/` | Raw-ish queue/analytics snapshots when useful. |

## Data schema

Each performance record should include, when available:

```json
{
  "typefully_draft_id": 9546906,
  "x_post_id": "2067487477062058328",
  "x_url": "https://x.com/AlanNotion/status/...",
  "status": "scheduled|published",
  "scheduled_at": "2026-06-19T08:00:00+02:00",
  "published_at": "2026-06-19T08:00:00+02:00",
  "draft_title": "Pain Point Question 2 — AI Assistant",
  "campaign": "Vacation-Proof Creator Systems|Quote Series|Pain Point Questions|Other",
  "lane": "Value|Connection|Systems|Unknown",
  "format": "Tweet|Thread|Quote-style|Question|Unknown",
  "hypothesis": "What we expect this post to test",
  "metrics": {
    "impressions": 0,
    "likes": 0,
    "replies": 0,
    "reposts": 0,
    "quotes": 0,
    "bookmarks": 0,
    "profile_clicks": 0
  },
  "checkpoint": "24h|72h|7d|latest",
  "vs_baseline": "above|at|below|too_early",
  "lesson": "Short human-readable lesson",
  "routed_next_action": "analytics|growth-strategy|ideation|ghostwriting|none"
}
```

## Weekly report format

1. Headline insight.
2. Evidence bullets with post URLs and metrics.
3. Pattern confidence: Weak / Medium / Strong.
4. One-variable test for next week.
5. Routing decision: strategy / ideation / ghostwriting.
6. Explicit approval note if the recommendation changes queue/scheduling.

## Current first experiment

Initial hypothesis to validate from June 18 onward:

> Concrete lived-detail posts about busy-parent creator systems will outperform generic quote/advice posts for the right audience.

Default measurement: compare question/pain-point, quote, and Vacation-Proof Creator Systems posts by impressions, replies, and profile clicks at 24h/72h/7d checkpoints.
