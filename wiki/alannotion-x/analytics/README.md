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
- Typefully scheduling may be autonomous when the matching XContent Calendar record is created/updated.
- Do not use MainDB for X scheduling or analytics; MainDB is YouTube-only.
- Destructive actions and X engagement actions still require Alan's explicit approval.
- Only one strategy variable changes per week unless Alan overrides it.
- Compare against AlanNotion baseline first: 200 impressions, 4 likes, 1 reply, 1 bookmark.
- Treat early low-volume metrics as weak signals, not proof.


## Canonical Notion layer

Alan's X scheduling and analytics loop uses the **XContent Calendar** Notion database, not MainDB. MainDB is reserved for YouTube/MainDB work.

Use this Notion data source for all scheduled Typefully posts and analytics sync:

- Human link: https://app.notion.com/p/X-Content-Calendar-375fca35419180ac9124f6078b310ed1?source=copy_link
- Notion page ID: `375fca35-4191-80ac-9124-f6078b310ed1`
- Embedded child database block ID: `375fca35-4191-806a-9487-fe0e32ddb59d`
- API data source name: `X_Calendar_DB`
- API data source ID: `375fca35-4191-80d6-973e-000b754b5e60`

Every autonomous Typefully scheduling action should create or update a matching XContent Calendar page with the post copy, publish date/slot, lane, format, Typefully draft ID/URL, workflow stage, and eventually X analytics.

Scheduling approval model update: Typefully scheduling can be autonomous as long as the XContent Calendar is kept in sync. Destructive actions and engagement actions such as replies, likes, follows, DMs, deleting, or changing unrelated assets still require explicit approval.

### Analytics fields added to X_Calendar_DB

The feedback loop added these properties to support analytics sync:

- `X Post ID`
- `Impressions`
- `Likes`
- `Replies`
- `Reposts`
- `Quotes`
- `Bookmarks`
- `Profile Clicks`
- `Last Analytics Sync`
- `Analytics Checkpoint`
- `vs Baseline`
- `Analytics Lesson`

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
