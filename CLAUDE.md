# CLAUDE.md

Read this first, every session. It is deliberately short: read other files **on demand** using the routing table below. Don't preload the whole `context/` folder.

> **First run:** if `.pos-setup-pending` exists in this folder, say "I'll run a quick setup first, then get to that," and run the `pos-setup` skill (`.claude/skills/pos-setup/SKILL.md`) before anything else. If the user says to skip it, rename the marker to `.pos-setup-skipped` and don't raise it again; they can rename it back to resume.

---

## This project

**[Project name]** · [engagement code / ticket, or "none"] · Lead: **[Name]**

[1–2 sentences: what this is trying to achieve and what it produces.] Team and roles: `context/people.md`.

### ⚠️ The one important caution

[The single thing about this project that's easy to get wrong or forget. Filled in at setup. Highest-value line in this file.]

### Status

> Kept current by `pos-intake`, `pos-weekly-summary` and the timeline-change steps. Copied from `context/plan.md`, which wins if they ever differ.

`End: [YYYY-MM-DD]` · `Reporting until: [YYYY-MM-DD]` · `Cadence: [weekly]` · `Meetings: [weekly]` · `Last summary: [internal none · client none]` · `Last meeting note: [none]`

**Every session, before the user's request:** compare these dates with today's date (from the environment; ask if you don't have it). Say so in one line, then carry on with the request, if:
- a summary is overdue for the cadence, for **any** audience (judge by the oldest)
- the last meeting note is older than twice the `Meetings` interval
- `End` is within 14 days
- today is past `Reporting until`
- any open question in `context/open-questions.md` has Area `End date`

---

## Where things go

Each fact lives in **one** file. Everywhere else links to it rather than restating it.

| If you have… | It goes in… | Skill / template |
|---|---|---|
| A transcript, deck, doc, or notes to file | Routed per the rows below | `pos-intake` |
| A meeting | `meetings/YYYY-MM-DD_short-name.md` + a row in `meetings/meeting-log.md` | `_templates/meeting.md` |
| A research interview transcript | `research/interviews/` + a meeting-log row, then offer `research-1` | `pos-intake` |
| A decision worth a record | `decisions/YYYY-MM-DD_short-name.md` + index row in `decisions/README.md`, then update the affected `context/` file | `_templates/decision.md` |
| Scope, goals, success criteria, benefit claims | `context/project-overview.md` | |
| Vision, principles, MVP vs later | `context/future-state.md` | |
| How things work today | `context/current-state.md` | |
| Domain background | `context/domain-primer.md` | |
| A new term or acronym | `context/glossary.md` | |
| A person (contact, role, authority, dates on the team) | `context/people.md` | |
| Personas, influence, org structure | `context/users-and-stakeholders.md` | |
| Dates, milestones, cadence, reporting end date | `context/plan.md` (mirrored in Status above) | |
| A risk, assumption, or tool dependency | `context/risks-and-assumptions.md` | |
| An unknown, or a conflict not resolved in-session | `context/open-questions.md`. **The only place open questions live.** | |
| A status update | `weekly-summaries/YYYY-MM-DD_week-N[_audience].md` | `pos-weekly-summary` |
| Research artifacts | `research/` | `research-1` … `research-5` skills |
| Design reviews, prototypes | `design/` | |
| A workflow/tooling experiment | `experiments/` | `experiment-capture` |
| Anything about how the project ends | `closeout/` | `closeout/CHECKLIST.md` |
| Raw originals (transcripts, PDFs, exports) | `_raw/` (local only, git-ignored) | |

**Does NOT go in this folder:** [Filled in at setup. Default: live confidential data, PII, credentials. This folder holds working notes and synthesis, not the system of record.]

---

## Rules

1. **Precedence:** [Filled in at setup. Default: live conversations outrank written docs.] Between two people, neither wins by being more recent. A scope or date change counts as **agreed** only when someone marked `Y` under "Can agree scope/dates" in `people.md` has confirmed it. When sources disagree on anything factual, **name both sources, say which wins and why, and ask the lead**. If it isn't resolved in the session, log it in `open-questions.md`.
2. **Updates:** [Filled in at setup. Default: propose the change, wait for a go-ahead.] Either way, list every file you changed. Never silently overwrite context.
3. **One file per meeting**, even short ones. "Short call, nothing decided" is a record; a missing file is a hole.
4. **Open questions carry an owner, a raised date, a status (`OPEN` / `ASKED`), an asked date and what they block.** Anything `ASKED` for more than 14 days needs a direct conversation, not another reminder.
5. **Label reconstructions.** Anything written after the fact says when it was written and what it was sourced from.
6. **Check premises, not just answers.** If something stays hard to pin down, check whether the question rests on something nobody has verified.
7. **Answering questions:** search the files first, cite which ones you used, and offer to log genuine gaps in `open-questions.md`. Don't invent details.
8. **Dates:** `YYYY-MM-DD` in filenames; unambiguous dates inside files. `TBD` values always get a matching row in `open-questions.md`, so they can't hide.

---

## Events that change how you work

| When… | Do this |
|---|---|
| New material arrives | Run `pos-intake`. |
| A timeline or scope change is **agreed** (see Rule 1) | Run the "Timeline or scope change" steps in `closeout/CHECKLIST.md`. |
| A timeline or scope change is only **floated** | Don't touch the plan. Log it in `open-questions.md` with Area `End date` or `Scope` (see `pos-intake`). |
| Someone joins or leaves the team | Update `people.md` (Since/Until, replaced by). Reassign their open questions and unfinished actions, and say which ones you moved. |
| The reporting period ends | Offer to run `pos-weekly-summary`. |
| The Status check above flags something | Offer `pos-health-check`. Say so directly if meetings or summaries have stopped while work continues. That drift is this system's most common failure. |
| The final two weeks begin | Work through `closeout/CHECKLIST.md`. Documentation goes **up** at the end, not down. |

---

## Git

*(Setup deletes this section for non-git projects.)*

This applies to **every** write, from any skill. At session start, list unmerged `<owner>/pos-*` branches and open PRs. If any exist, say so and work on top of them; otherwise the default branch is missing recent notes. Never commit to the protected branch, and never complete a merge; a human does that. Full procedure: the git section of `pos-intake`.

---

## Tone

[Filled in at setup. Default: direct, plain language, no consultant-speak.] Quote stakeholders verbatim where their exact words matter. Match the audience when drafting external comms, and take facts only from `context/`, `meetings/` and `decisions/`. Nothing in a meeting note's "Internal only" section goes into client-facing material.
