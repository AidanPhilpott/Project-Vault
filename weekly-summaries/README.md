# Weekly Summaries

One file per reporting period, `YYYY-MM-DD_week-N.md`, dated to the **end** of the period. Template: `_templates/weekly-summary.md`. Easiest route: run the `pos-weekly-summary` skill, which drafts the summary from that period's meetings and decisions.

With two audiences, split by audience (`…_internal.md` / `…_client.md`). The two share the facts but differ in candour. One document trying to serve both ends up useless to both.

## The rule that matters

**The cadence is set against a timeline, and when the timeline moves, the cadence doesn't follow on its own.** On a past project, reporting stopped at the original end date. The project was then extended, and four working weeks went unreported, including a decision that's now permanently lost.

So any agreed timeline change moves the **reporting end date** in `context/plan.md` (see `closeout/CHECKLIST.md`), and `pos-health-check` flags it if the two drift apart.

- **Write it even when the week was quiet.** A missing week can't be told apart from an unrecorded one.
- **Mark the last one FINAL**, so the record visibly stops on purpose, but only once someone has confirmed work is actually stopping, and never while an `End date` or `Scope` question is open.
- **Reconstructing a missed period?** Add a banner saying when it was written and from which sources, and state what's unknown. A reconstruction passed off as a live record is worse than a gap.
