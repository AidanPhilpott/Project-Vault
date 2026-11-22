# Open Questions

> **The only place open questions live.** Other files link here rather than keeping their own lists, so there's nothing to keep in sync.

Every question carries an **owner**, a **raised** date, a **status**, an **asked** date once it's been put to someone, and what it **blocks**. Without those it's a wish list.

| Field | Meaning |
|---|---|
| Status `OPEN` | Identified, not yet put to anyone. The health check flags it after 7 days. |
| Status `ASKED` | Put to the owner on the Asked date, awaiting an answer |
| Blocking `Y` | Something is waiting on this. Escalate, don't wait. |
| Area `End date` / `Scope` | A floated timeline or scope change that isn't agreed yet. While one is open, no summary can be marked FINAL and the session-start check mentions it. |

**Escalation rule:** anything `ASKED` for more than **14 days** (counted from the Asked date) needs a direct conversation, not a re-listing or a nudge in a status update. The questions that go stale are usually the ones whose deadline sits on *your* work rather than on their answer.

**Unresolved conflicts** between sources land here too: status `ASKED`, owner = the lead, Blocks = the files left un-updated because of it.

## Open

| Question | Area | Owner | Raised | Status | Asked | Blocking | Blocks |
|---|---|---|---|---|---|---|---|
| [Question] | [End date / Scope / Domain / Current state / Future state / Users / Technical / Logistics / Conflict] | [Who can answer] | [YYYY-MM-DD] | `OPEN` | [YYYY-MM-DD once asked] | [Y/N] | [What's waiting, or "nothing yet"] |

## Answered

> Fold the answer into the right context file, then move the question here.

| Question | Answer | Source, date | Documented in |
|---|---|---|---|
| [Question] | [Answer in plain language] | [Meeting / person, YYYY-MM-DD] | [file] |

## Never resolved *(fill in at close-out)*

> Don't quietly delete unresolved questions. One that mattered and never got answered is a finding.

| Question | Asked of | Why it didn't land | What it cost |
|---|---|---|---|
| [Question] | [Who] | [No forcing function / person left / overtaken by events] | [What was decided without it] |
