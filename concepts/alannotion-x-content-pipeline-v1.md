---
title: AlanNotion X Content Pipeline v1
version: 1.0
created: 2026-06-04
status: Draft for Alan approval
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

## Proposed Notion database fields
Minimum useful fields:
- Name / Title — post title or short identifier.
- Raw Idea — original input or summary.
- Source Type — Topic, Text, Voice, Image, Screenshot, Link, Repurposed, Other.
- Source Link / Asset — URL or file reference when available.
- Content Lane — Value, Connection, Systems.
- Format — Tweet, Thread, Long-form, Giveaway, Reply, Quote tweet, Article.
- Draft Text — final approval candidate.
- Hook — first line / main scroll-stopper.
- Status — Inbox, Developed, Drafted, Needs Edit, Awaiting Batch Approval, Approved, Ready to Schedule, Scheduled, Posted, Rejected, Archived.
- Approval Batch — week or batch name, e.g. 2026-W24.
- Scheduled Date/Time — intended posting time in Europe/Stockholm.
- Platform — X.
- Scheduling Tool — Manual, X Native, Typefully, x-cli, Other.
- Posted URL — final X URL after posting.
- Scores — hook / voice / originality / personalization / density / shape.
- CTA / Lead Magnet — None, Packaging Checklist, Ideation Checklist, YouTube Operator, Skool, Other.
- Notes / Feedback — Alan comments and revision notes.
- Outcome — Accepted, Rejected, Reworked, Ignored.
- Metrics — impressions, likes, replies, reposts, bookmarks, follows, sales/lead signal when available.

Nice-to-have fields:
- Series Name — for multi-post sequences.
- Parent Idea — relation back to original idea.
- Repurpose Source — YouTube video, newsletter, Skool post, old X post, etc.
- Target Reader — busy parent creator, YouTuber, Notion user, AI workflow buyer, etc.
- Confidence — High, Medium, Low.
- Approval Checkbox — quick batch review helper.

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
Open question: whether Typefully exposes an API, integration, email-in flow, browser automation path, or Zapier/Make route that Hermes can safely use.

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
