# Theo Journal — Journals Auto-Stage

Date: 2026-04-28
Agent: Theo
Timezone: Europe/Stockholm

## What I changed
- Updated the HermesVault pre-commit hook so anything under journals/ is auto-staged with git add -A -- journals/.
- Updated the Luma task journal template and workflow guidance to reflect the new tags field and journal capture behavior.

## Why
- The user wanted any new journal file added in journals/ to be automatically included in git commits.
- This keeps journal workflow friction low and prevents missed notes.

## Verification
- Confirmed .githooks/pre-commit is configured through core.hooksPath=.githooks.
- Confirmed the hook now stages the full journals/ path.

## Notes
- I left unrelated untracked journals alone for now.
- Future commits should automatically include any new journal files created under journals/.
