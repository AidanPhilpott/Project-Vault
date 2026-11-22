---
name: pos-health-check
description: >-
  Audit this Project Operating System for drift: stale or unraised open questions,
  missing weekly summaries (per audience), meetings missing from the log, overdue
  actions, a plan or Status block that no longer matches reality, hidden TBDs, unmerged
  intake branches, and close-out risk. Use when the user asks "is the project folder up
  to date?", "health check", "what's stale?", "audit the POS", when the session-start
  Status check flags something, or before a status meeting. Read-only: reports problems
  and proposes fixes, never fixes silently.
---

# POS health check

Run every check, then report. **Don't change files during the check.** Propose fixes at the end and apply them only on a yes. You need today's date: take it from the environment, or ask.

**Effective dates:** wherever `plan.md` has both a Planned and a Revised value, use Revised if it's filled in, otherwise Planned.

## Checks

| # | Check | How | Flag when |
|---|---|---|---|
| 1 | **Questions** | `context/open-questions.md` | Rows with Blocking = `Y` → list them first. `ASKED` with an asked date more than 14 days ago → recommend a direct conversation, naming the owner. `OPEN` more than 7 days after raised → never raised with anyone; recommend who should ask whom. Any open Area `End date` / `Scope` question → must-fix. |
| 2 | **Reporting cadence** | `weekly-summaries/` against the cadence in `plan.md`, **per audience**, counting from the cadence's effective date (or the project start) to today | Any missing period for any audience. Count them. |
| 3 | **Cadence vs timeline** | Effective reporting end date vs effective project end date vs latest meeting date | The reporting end date is earlier than the project end date, or meetings exist after the reporting end date. **This is the classic failure.** |
| 4 | **Status block** | `CLAUDE.md` Status block vs `plan.md`, the latest summary **per audience**, and the latest meeting note | Any value out of date |
| 5 | **Meeting log integrity** | `meetings/*.md` (excluding `meeting-log.md`) and `research/interviews/` against the log's index rows | A file with no row, or a row with no file |
| 6 | **Meeting gaps** | Gaps between meeting dates vs the `Meetings` rhythm in the Status block | A gap more than twice the usual interval while work is ongoing. Ask: no meetings, or no notes? |
| 7 | **Overdue actions** | Actions tables in meeting notes | Past due and not marked done, especially those owned by someone with an Until date in `people.md` |
| 8 | **Decisions drift** | Recent meeting notes' Decisions sections against `decisions/README.md` | Decisions that change scope, timeline or a convention but have no record |
| 9 | **Plan freshness** | `context/plan.md` milestones | Milestones past their effective date with no status. End date passed with no close-out activity. |
| 10 | **Placeholders and TBDs** | Search for `[Capitalised placeholders]` (ignoring markdown links) and for `TBD` | **Must fix:** placeholders in `CLAUDE.md`, `README.md`, `project-overview`, `people`, `plan` or `risks-and-assumptions` (setup should have filled these; the caution is top priority), and any `TBD` with no matching row in `open-questions.md`. A `TBD` in a date field disables the date checks above, so say so. **Informational:** placeholders in other context files. Report them as "not started yet", one line each, not as faults. |
| 11 | **Glossary backlog** | "Heard but not yet defined" in `context/glossary.md` | Items more than 2 weeks old |
| 12 | **Close-out readiness** | Today vs the effective end date | Within 2 weeks of the end with no retrospective, deliverables index or scope-freeze decision started. Judge by files that exist, not by checkboxes. |
| 13 | **Unmerged work** *(git only)* | `<owner>/pos-*` branches and open PRs | Anything unmerged for more than 3 days. The default branch is missing those notes. |

## Report format

Lead with a one-line verdict: **Healthy**, **Drifting**, or **Stalled**. Then list the issues with the most serious first:

```
🔴 Must fix:   [issue]: [evidence: file, date] → [proposed fix]
🟡 Should fix: …
🟢 Fine:       [checks that passed, one line]
```

End by offering to apply the fixes, grouped into one go-ahead. Files that would need reconstructing (missed summaries, missing meeting notes) go through `pos-weekly-summary` or `pos-intake` and get labelled as reconstructions.
