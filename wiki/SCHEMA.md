# Wiki Schema

## Domain
Business and project operating notes for the user's active ventures, companies, side projects, experiments, decisions, and ongoing work.

## Purpose
This wiki is a permanent working memory for what the user is building, running, deciding, and tracking. It should preserve durable context, surface relationships between projects and people, and keep a searchable record of progress, decisions, and open questions.

## Conventions
- File names: lowercase, hyphen-separated, no spaces (e.g. `acme-launch-plan.md`)
- Every wiki page starts with YAML frontmatter
- Use `[[wikilinks]]` to connect related pages
- Prefer concise, scannable pages that can be read in under 30 seconds
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`
- When updating a page, bump the `updated` date
- Avoid duplicate pages; search existing pages before creating new ones
- Keep raw source material immutable in `raw/`

## Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | project | company | person | decision | meeting | comparison | query | summary
tags: [from taxonomy below]
sources: []
contradictions: []
---
```

## Tag Taxonomy
Use only tags from this taxonomy. Add new tags here before using them.

- business
- company
- project
- person
- team
- product
- strategy
- operations
- finance
- sales
- marketing
- engineering
- research
- decision
- meeting
- task
- timeline
- risk
- customer
- vendor
- legal
- hiring
- metrics
- note
- archive

## Page Thresholds
- Create a page when something is central to an active business/project or appears in 2+ notes/sources
- Add to an existing page when the note is incremental or clearly related
- Do not create pages for passing mentions or one-off trivia
- Split a page when it exceeds ~200 lines
- Archive a page when it is obsolete or fully superseded

## Page Types

### Entity / Company / Person Pages
Include:
- What it is / who it is
- Key facts and timeline
- Relationships to other pages
- Important links, docs, or source references

### Project Pages
Include:
- Goal and status
- Owner(s)
- Milestones and next steps
- Risks / blockers
- Related people, companies, and decisions

### Decision Pages
Include:
- Decision made
- Date and context
- Alternatives considered
- Why this decision was taken
- Follow-ups

### Meeting Pages
Include:
- Date and attendees
- Notes / decisions / action items
- Follow-up links to project pages

### Concept Pages
Include:
- Definition / context
- Why it matters to the user's work
- Related projects, companies, and decisions

## Update Policy
When new information conflicts with existing content:
1. Check dates; newer information generally wins
2. If both claims may still be true, preserve both with context
3. Mark contradictions in frontmatter
4. Flag notable contradictions in the log for review

## Cross-linking Rule
Every new page should link to at least two other pages when possible. If the wiki is still small and that is not practical, link to the most relevant existing pages and revisit during later updates.

## Logging Rule
Append one log entry per meaningful operation. Include created/updated files in the bullet list.
