---
title: AlanNotion X Content Pipeline v1
version: 1.0
created: 2026-06-04
status: Connected to Notion + Typefully
owner: Theo / Hermes
account: "@alannotion"
---

# AlanNotion X Content Pipeline v1

## Purpose
Create an operating workflow where Alan can send a rough topic, phone-note idea, voice memo, screenshot, or picture, and the AlanNotion X operator turns it into a quality-controlled X content calendar for batch approval.

## Current decision
- Approval mode: **Option B first** — draft the full weekly calendar, then Alan approves the whole batch.
- Future mode: **Option D later** — schedule approved drafts automatically once trust is proven.
- Calendar home: **Notion database** supplied by Alan. Hermes may add or modify fields needed for the workflow.
- Posting goal: work toward **3 posts/day**.
- Default slots: **08:00, 12:30, 19:30 Europe/Stockholm**.
- Content lanes: **Value, Connection, Systems**.
- Scheduling options to evaluate: **X native scheduling** and **Typefully**.
- Public posting/scheduling rule: **No public post, reply, quote, like, repost, follow, DM, delete, or schedule action without Alan's explicit approval of the final copy/batch.**

## Inputs Alan can send
- Topic: short phrase or theme.
- Phone idea: rough text dump, notes, bullets, or messy thought.
- Voice memo: captured idea, story, reaction, or observation.
- Image/screenshot/photo: visual source for a lesson, story, workflow, proof, or commentary.
- Link: X post, YouTube video, product page, Notion template, community post, or relevant inspiration.

## Intake workflow
1. Capture the raw input exactly enough that the original idea is not lost.
2. Identify the core idea and audience relevance.
3. Classify the lane:
   - Value: practical AI/productivity/creator advice.
   - Connection: busy dad, full-time job, kids, channels, business, creator life.
   - Systems: Notion workflows, YouTube operating systems, checklists, dashboards.
4. Select the best format:
   - Single tweet
   - Thread
   - Long-form post
   - Giveaway / lead magnet post
   - Reply
   - Quote tweet
5. Develop the angle:
   - sharpen the hook
   - add Alan-specific proof/context
   - remove generic phrasing
   - decide whether it is one post or part of a series
6. Send to ghostwriting standards:
   - one idea per post
   - mobile-first shape
   - no AI-sounding filler
   - score every draft before showing it
7. Store the output in the Notion content calendar.

## Weekly calendar workflow
1. Gather the available idea backlog from Notion plus any new Telegram inputs.
2. Build a weekly mix across Value / Connection / Systems.
3. Draft posts for the week using these default slots:
   - Morning: 08:00
   - Lunch: 12:30
   - Evening: 19:30
4. Balance the week:
   - avoid three heavy how-to posts on the same day
   - include personality/proof, not just tips
   - include lead magnets only when the week has enough trust-building content around them
5. Quality-control each draft through the ghostwriting score gate.
6. Return the full weekly batch to Alan for approval.
7. After approval, move approved items to Approved / Ready to Schedule.
8. Scheduling is manual or semi-manual until the scheduling path is proven.

## Recommended initial cadence
Target the 3/day calendar as draft inventory, but do not force public posting quality below standard.

Recommended launch mode:
- Draft 21 weekly slots.
- Publish/schedule only the batch Alan approves.
- If quality is uneven, prioritize 7–14 strongest posts rather than filling all 21 slots.
- Keep reply-target workflow separate from main feed slots.

## Implemented Notion database
Alan provided the production Notion content calendar database:

- Database: `X_Calendar_DB`
- Database ID: `375fca354191806a9487fe0e32ddb59d`
- Existing fields preserved: `Title`, `Summary`, `File`, `Type`, `Topic`, `status`, `Publish Date`, `created`.
- Existing `status` is kept simple: `Not started`, `In progress`, `Done`.

Fields added by Hermes for the AlanNotion X pipeline:
- `Workflow Stage` — Inbox, Developed, Drafted, Awaiting Batch Approval, Approved, Typefully Drafted, Scheduled, Published, Rejected.
- `Lane` — Value, Connection, Systems.
- `Format` — Single post, Thread, Reply, Quote, Giveaway, Poll.
- `Approval` — Not ready, Needs Alan approval, Approved, Changes requested.
- `Recommended` — checkbox for strongest weekly candidates.
- `Quality Score` — numeric combined draft score.
- `Slot` — 08:00, 12:30, 19:30.
- `Typefully Draft ID` — draft identifier after Typefully draft creation.
- `Typefully URL` — private/draft URL when available.
- `Published URL` — final X URL after publishing.
- `Source` — Telegram text, Voice, Image, Link, Manual, Cron.
- `Raw Idea` — original idea/input summary.
- `Final Copy` — approved final candidate text when short enough for a property; longer copy can live in the page body.
- `Media Notes` — image/video/screenshot handling notes.

Verification item created:
- Title: `Hermes pipeline test — raw idea intake`
- Page ID: `375fca35-4191-815f-8e33-c70a514555be`
- URL: `https://app.notion.com/p/Hermes-pipeline-test-raw-idea-intake-375fca354191815f8e33c70a514555be`
- No public X action, Typefully draft, or schedule action was taken from this Notion item.

## Batch approval protocol
When a weekly batch is ready, Hermes sends Alan:
- Week covered.
- Number of posts drafted.
- Slots filled.
- Lane mix.
- Any posts Hermes recommends cutting.
- Full post copy grouped by day and time.
- Approval options:
  - Approve batch as-is.
  - Approve selected posts only.
  - Request edits.
  - Reduce cadence.

Approval must be explicit, for example:
- “Approved for the full batch.”
- “Approve posts 1–10 only.”
- “Approve all except Wednesday evening.”

## Scheduling path to verify
Before automatic scheduling is enabled, test and document one safe path:

### X native scheduling
Open question: whether Hermes can automate native X scheduled posts reliably and safely from this environment.

### Typefully
Initial investigation result: **best first candidate**.

Typefully has a public API at `https://api.typefully.com/v2` that supports:
- Creating drafts: `POST /v2/social-sets/{social_set_id}/drafts`
- Saving as draft when `publish_at` is omitted
- Scheduling with `publish_at` using an ISO 8601 datetime with timezone
- Publishing immediately with `publish_at: "now"`
- Scheduling to the next queue slot with `publish_at: "next-free-slot"`
- Queue schedule inspection/replacement
- Media upload flow for images/video/GIF/PDF
- Attaching uploaded media to individual posts via `media_ids`
- X quote posts via `quote_post_url`
- X reply drafts/posts via `settings.reply_to_url`
- Published URL retrieval after publishing
- X analytics endpoints for posts and followers

Media support is strong enough for Alan's requirement: Typefully supports upload file extensions `.jpg`, `.jpeg`, `.png`, `.webp`, `.gif`, `.mp4`, `.mov`, and `.pdf`. Upload flow is:
1. Create media upload with filename.
2. PUT raw bytes to returned presigned S3 URL using no extra headers.
3. Poll media status until `ready`.
4. Add returned `media_id` to the post's `media_ids`.

Verification result: **connected and working**.

- `TYPEFULLY_API_KEY` is installed and authenticates successfully.
- `TYPEFULLY_MCP_SERVER_URL` is installed and works as a Streamable HTTP MCP server.
- Hermes MCP server `typefully` is configured in `~/.hermes/config.yaml` with 25 tools enabled; a new session / gateway restart is required before those tools appear as native Hermes tools.
- Typefully social set: `257912`.
- Connected X account: `@AlanNotion`.
- Publishing quota at verification: 1000 remaining, resets 2026-07-01 00:00 Europe/Stockholm.
- Queue timezone: Europe/Stockholm.
- Current queue slots: 08:00, 13:00, 19:45 daily.
- Media/draft verification succeeded: uploaded a tiny PNG, media reached `ready`, created an X draft with media, verified draft status `draft`, then deleted the test draft. No public post was scheduled or published.

Recommendation: use Typefully as the first scheduling path, especially for image/media posts. Before changing queue times from current 08:00 / 13:00 / 19:45 to target 08:00 / 12:30 / 19:30, ask Alan because replacing the Typefully queue schedule is an admin-level full replacement.

### x-cli / local X tooling
Likely usable for posting after approval, but may not support native future scheduling. If it only supports immediate posting, use cron jobs or an external scheduler only after approval and safety checks.

## Safety rules
- Drafting is autonomous.
- Editing Notion fields is allowed after Alan provides the database.
- Public actions require explicit approval.
- Scheduling approved posts still counts as a public action because it creates future publication.
- Never optimize for generic virality over the right audience.
- Never publish posts that fail the ghostwriting score floor.
- Push back if 21 posts/week lowers trust or quality.

## Open questions for Alan
1. Provide the Notion database URL or ID.
2. Confirm whether Hermes should add the proposed fields directly when database access is available.
3. Confirm whether Typefully is the preferred scheduler to investigate first.
4. Confirm whether approved batches should be scheduled immediately after approval or held in Ready to Schedule until a final scheduling command.
5. Confirm if the first weekly batch should be 21 drafted slots or a safer 7–14 best-post batch.

## Definition of done for v1 setup
- Notion database connected and schema inspected.
- Missing fields added or mapped to existing fields.
- One test idea moves through Inbox → Drafted → Awaiting Batch Approval.
- One weekly batch is generated.
- Alan approves or edits the batch.
- Scheduling path is tested without public posting, where possible.
- Automatic scheduling is enabled only after Alan approves the operating behavior.
