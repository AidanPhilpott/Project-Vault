# Close-out Checklist

> **Read this at kickoff.** Several items (feedback capture, measurement, the deliverables index) are much cheaper if you know they're coming. Work through the main list in the **final two weeks**, not the final two days.

---

## Timeline or scope change: run this every time one is agreed

**Run it the day an extension, descope, re-scope or date change is *agreed*** (by someone marked `Y` under "Can agree scope/dates" in `people.md`). If it's only been floated, log it as an open question with Area `End date` or `Scope` instead. This is the most commonly skipped step, and the one that most reliably leaves a hole. An extension feels like more of the same work, so nothing prompts anyone to re-point the reporting cadence, the plan or the close-out date, all of which were set against the original end. The unreported stretch that follows is where the lost decisions turn up.

These steps can happen more than once per project, so **they're not ticked here.** Each change gets a decision record, and the record's "Timeline or scope change steps" checklist (in `_templates/decision.md`) is where they get ticked:

1. **Log the decision** in `decisions/`: what changed, when, who agreed it, what it covers.
2. **Update `plan.md`'s Revised column**: end date, **reporting end date** (confirm explicitly that summaries continue through the new period, for every audience), milestones, sprint and invoicing tables. Keep Planned as it was.
3. **Update the Status block** in `CLAUDE.md`.
4. **Re-scope?** Update the scope table in `project-overview.md` and the MVP boundary in `future-state.md`, marking changed rows `(changed YYYY-MM-DD, see decision)`. Re-check the success criteria and benefit claims.
5. **Close the related `End date` / `Scope` open questions.** An "Is the extension confirmed?" left open while the extension is happening means the record has stopped tracking reality.
6. **Tell the team** out loud.

## Two weeks out

- [ ] **Announce the close internally:** the date, and what "done" means.
- [ ] **Freeze scope in writing.** Agree what's in the final delivery and what moves to whose backlog, with the backlog owner.
- [ ] **Start the deliverables index** (`_templates/deliverables-index.md`). The people who know where things live roll off first.
- [ ] **Name an owner for every open thread.** A person, not a team.
- [ ] **Run `pos-health-check`.** If the cadence has slipped, catch up now while the meetings are recent enough to reconstruct.

## Final week

- [ ] **Write the retrospective** (`_templates/retrospective.md`) while people are still around.
- [ ] **Close out open questions honestly.** Unanswered ones move to "Never resolved" with who was asked and what it cost.
- [ ] **Mark superseded and stale files** with a status banner. Don't rewrite history.
- [ ] **Correct stale metadata.** Record actual against planned; don't overwrite the plan.
- [ ] **Capture access and handover logistics** in one place, and confirm the receiving side can actually use them.
- [ ] **Collect the validation signals** (moments where the work demonstrably landed) into `feedback-and-outcomes`.

## At close

- [ ] **Send the wrap-up messages,** one per audience with every link consolidated. Save copies in `closeout/communications/`.
- [ ] **Write the final weekly summary**, marked FINAL.
- [ ] **Capture inbound feedback** verbatim and attributed, as it arrives.
- [ ] **Update `README.md` and `CLAUDE.md`** (including the Status block) to say the project is closed, and point at this folder.

## After close

- [ ] **Deal with the remote.** If you're losing access to a client or partner repo, rename the remote (e.g. `<host>-archive`) so syncs stop failing confusingly.
- [ ] **Remove scaffolding and stale exports:** old zips, template copies, machine-specific paths.
- [ ] **Extract what's reusable** (methods, templates, skills, prompts) back into the POS kit. This is the highest-value and most-skipped step.
- [ ] **Answer the measurement question.** Can you still evidence the benefit claims in `project-overview.md`? If not, write down that they're unevidenced, even if that's unflattering.

---

## The retrospective must answer

1. What did we believe at kickoff that turned out to be wrong?
2. Where did our process break, and when exactly?
3. What would we do identically next time?
4. What did we get away with that we shouldn't count on twice?
5. What one thing would have made the biggest difference?
