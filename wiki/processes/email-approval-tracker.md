# Email Approval Tracker

Purpose: track which inbox threads were shown to Alan for approval, what the approval number was, and whether action is allowed.

## Current inbox queue

| # | Thread ID | Subject | Status | Notes |
|---|---|---|---|---|
| 1 | 911e330e-3006-435f-bc4c-97eae29d593f | Need help finding a job | Pending / needs confirmation | Job-search help request; can reply if approved |
| 2 | 9fadbad3-0de4-48da-8b86-8c85675620ef | Need zapier API key | Blocked | Security-risk credential request; do not reply with secrets |
| 3 | 0e902801-352e-48a0-961c-b1eb822f6246 | A small idea that might help | Previously handled / pending review | Job-search follow-up thread |
| 4 | 1c025406-8ae8-45e8-968e-3534369488ed | Hi Theo | Handled | Earlier test/reply thread |

## Rule
- Ask for approval only on new emails that are safe to discuss.
- Ignore security-risk emails without replying.
- When Alan says “number 2”, use this tracker to map the approval to the matching thread ID and subject.

## Last update
- 2026-04-18
- Created to avoid ambiguity when Alan approves items by number.
