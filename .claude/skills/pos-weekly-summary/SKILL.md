---
name: pos-weekly-summary
description: >-
  Draft this project's weekly (or sprint/period) status summary from what's already in
  the folder: meeting notes, decisions, open questions, overdue actions and plan changes
  since the last summary. One version per audience (internal / client). Use when the user
  asks for a "weekly update", "status update", "status report", "client update", "steering
  report", "sprint summary", "week N summary", or at the end of a reporting period. Also
  catches up missed periods as clearly labelled reconstructions.
---

# Weekly summary

## 1. Establish the period

- Read `context/plan.md` for the cadence (and its effective date), the audiences, and the **reporting end date**. Use Revised values where they're filled in, otherwise Planned.
- Find the latest summary in `weekly-summaries/` **for each audience**. The new period starts the day after it ends.
- **If more than one period is missing** for any audience, say so. Offer to write one entry per missing period, each marked as a reconstruction (see step 4). Don't silently roll several weeks into one.
- **If today is past the reporting end date but meetings are still being added,** flag it. The cadence has stopped while the work hasn't, which is the failure this system exists to catch. Ask whether `plan.md` needs a new end date.

## 2. Gather

For the period, read:
- meeting notes dated inside it (check `meetings/meeting-log.md`)
- decisions dated inside it. These are also the source for any plan or date changes; don't try to diff `plan.md`.
- `context/open-questions.md`: questions raised or answered in the period (by date), anything blocking, and anything `ASKED` more than 14 days ago
- **actions** from the Actions tables of recent meeting notes that are past due and not marked done
- experiment entries, if the module exists

## 3. Draft

Use `_templates/weekly-summary.md`, filename `YYYY-MM-DD_week-N.md` (or `…_internal.md` / `…_client.md` with two audiences), dated to the **end** of the period.

- **Quiet week?** Still write it. Three lines saying it was quiet is a record; a missing week is a hole.
- **Two audiences?** Write both from the same facts. The internal one can name friction and half-formed concerns. The client one **never** includes anything from a meeting note's "Internal only" section, and shouldn't name internal friction.
- **FINAL:** before marking any summary FINAL, ask "Is work actually stopping on [end date]?" Never mark it FINAL while an open question with Area `End date` or `Scope` exists. If it is final, point readers at `closeout/`.
- Take facts only from the files. If something the user mentions isn't documented, ask, or offer to log it through `pos-intake`.

## 4. Reconstructions

When writing a past period after the fact, add a banner at the top: `> Reconstructed on YYYY-MM-DD from: [list of source files]`. If there's no source material for a week, write the entry anyway, say plainly that there's no record, note what the meetings either side imply, and list what's unknown.

## 5. Confirm and record

Show the draft(s), and save once the user is happy. Then update the date for **that audience** under `Last summary` in the `CLAUDE.md` Status block. Offer to send or paste it wherever the summary normally goes. Don't send anything without an explicit yes. If the project uses git, follow the branch-and-PR flow in `pos-intake`.
