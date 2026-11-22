# Changelog: v1 → v2

*Reviewed 2026-11-19 against v1, plus how it was actually used on two live projects.*

## Headline numbers

| | v1 | v2 | |
|---|---|---|---|
| `CLAUDE.md` (loaded **every session**) | 13.9 KB | 7.0 KB | **−49%**, now including a live Status block |
| `context/` templates | 22.1 KB | 12.4 KB | −44% |
| All markdown | 136 KB | 102 KB | −25%, while adding 3 new skills |
| Skills Claude can discover automatically | 0 of 7 | 10 of 10 | |

---

## 1. Efficiency: less context loaded, fewer files read

- **The setup interview moved out of `CLAUDE.md` into the `pos-setup` skill.** In v1, about 5 KB of interview instructions loaded in every session for the life of the project, long after setup had finished. Now `CLAUDE.md` carries a two-line trigger, and the interview loads only when it's needed.
- **One routing table instead of three.** v1 had "What goes where" and "Key reference points" in CLAUDE.md, a third copy in the intake skill, and a folder map in three files. v2 keeps one routing table (in CLAUDE.md) and one folder map (in README).
- **"Read on demand" instruction.** CLAUDE.md now tells Claude not to preload the whole `context/` folder and to use the routing table to fetch only what's relevant.
- **Single source of truth per fact.** Duplicated sections were removed and replaced with one-line pointers:
  - MVP / priority stack: was in both `project-overview` and `future-state` → now only `future-state`
  - Org structure: was in both `people` and `users-and-stakeholders` → now only `users-and-stakeholders`
  - "Open questions" sections in five context files (each saying "keep these in sync") → now only `open-questions.md`
  - The current-vs-future table in `users-and-stakeholders` (duplicated `current-state` / `future-state`) → removed
  - "Risks to delivery timing" in `plan` (duplicated the risks file) → removed
  - Timeline-change guidance, written out in full in four files → kept once in `closeout/CHECKLIST.md`, pointed to from the others
  - The decision template existed twice with different fields → one template
- **Tables instead of repeated sections.** Open questions went from 5 identical tables to one table with an `Area` column. The glossary went from 6 tables to one with a `Type` column. Risks and assumptions moved from bullet sub-sections to tables with a `Status` column. They're easier to append to, search and scan.
- **Repeated placeholder blocks collapsed.** Research stages 1 and 3 repeated identical blocks 3–5 times ("Insight 1… Insight 5"). Each now has one block marked "repeat for each".

## 2. Fixes: things that were broken in v1

- **Skills weren't discoverable.** `_shared/skills/` and `experiments/SKILL.md` aren't locations Claude looks in for skills. All skills now live in `.claude/skills/<name>/SKILL.md`.
- **The experiments skill pointed at folders that don't exist:** `experiment-tracker/`, `context/ai-planning.md` (UC-XX), `research/ai/time-savings-log.md`, plus the Cowork-only tool `mcp__cowork__present_files`. All fixed or removed.
- **Research stage 5 saved to `/mnt/user-data/outputs/`** (a claude.ai sandbox path) using `present_files`. It now saves to `research/outputs/` in the project.
- **The research README pointed at `../findings/`**, a folder that didn't exist. The research folder structure is now consistent: `interviews/ → analysis/ → synthesis/ → outputs/`.
- **Stages 1 and 3 had no skill frontmatter,** although the README said all five did. All five are now real skills (`research-1` … `research-5`), with the stage 1 and 3 output templates kept beside their skills.
- **Inconsistent status markers.** The intake skill used `[TBD]` / `[ASKED]`, while `open-questions.md` used `[OPEN]` / `[ASKED]` / `[BLOCKING]`. Now it's `OPEN` / `ASKED` everywhere, with blocking as a separate Y/N column (see §6) and `TBD` reserved for unknown field values.
- **The close-out checklist referenced a `communications/` folder** that didn't exist. It's now `closeout/communications/`.
- **The setup module choice couldn't express "research + design"** without also adding experiments. It's now a multi-select.
- **The experiment template's example model** ("Claude Sonnet 4.6") was replaced with a generic placeholder.

## 3. Structural tweaks, from how v1 was used in practice

- **Templates moved to `_templates/`.** On one project, `meetings/YYYY-MM-DD_meeting-name.md` and `decisions/YYYY-MM-DD_decision-name.md` were still sitting among the real files. Placeholder files in working folders pollute searches and meeting-log checks.
- **New `_raw/` folder (git-ignored)** for original transcripts, PDFs and exports. It gives the "markdown-first, don't commit raw binaries" rule a concrete home, and intake knows to look there.
- **`.gitignore` extended:** Office lock files (`~$*`), `_raw/`, and `.claude/settings.local.json`.
- **`_kit/` folder for kit-only docs** (this changelog and SETUP.md). Setup deletes it, so it never clutters a live project.
- **Room for custom modules.** One project added a `distilled/` folder with its own template. `_templates/README.md` now documents how to add a module: template, folder, and a routing row.
- **`CLOSEOUT-CHECKLIST.md` renamed to `CHECKLIST.md`.**

## 4. New capabilities

- **`pos-weekly-summary` skill.** Drafts the summary from that period's meetings, decisions and question changes; detects missed periods and writes labelled reconstructions; marks the last one FINAL. This directly addresses the cadence drift that v1 identifies as its most common failure.
- **`pos-health-check` skill.** A 10-point drift audit: `ASKED` questions older than 14 days, missing summaries, a **reporting end date earlier than the project end date** (the extended-project failure), meeting files missing from the log, decisions not recorded, stale milestones, leftover placeholders, glossary backlog, and close-out readiness. It's read-only and proposes fixes.
- **Setup can start from documents.** Step 0 of `pos-setup` reads a brief or SOW first and asks only about the gaps.
- **Setup verifies itself.** It searches for leftover `[` placeholders at the end and lists them.
- **`plan.md` has an explicit "Reporting runs until" field,** shown alongside the end date with a "must move whenever End moves" note. It also has Planned vs Actual columns, so stale metadata gets corrected without overwriting history.
- **Beat 4 answers have dedicated homes:** benefit claims → a table in `project-overview.md`; tool dependencies → a table in `risks-and-assumptions.md`; "how this ends" → a section in `plan.md`.
- **Meeting template has a `Source:` line** (transcript / notes / reconstructed), which enforces the "label reconstructions" rule at the point of writing.
- **Intake processes multiple documents oldest-first** and presents one combined plan instead of one per document.

## 5. Fixes from a full test run (2026-11-19)

v2 was run end to end on a fictional client project (SOW in `_raw/`, research + experiments, no git): setup → intake of a sprint-review transcript → health check. Everything worked. All 10 skills' frontmatter parses, setup filled CLAUDE.md and README with no leftovers, and the health check caught every piece of seeded drift (6 missing summaries, a stale milestone, a 20-day meeting gap, an overdue `ASKED` question). Four tweaks came out of it:

- **Guidance vs blanks.** Six guidance lines used `[brackets]` like fill-in blanks, so they tripped setup's leftover check after the section was filled. They're now `>` notes, and `[ ]` means "fill this in".
- **Floated vs agreed timeline changes.** Intake used to trigger the full extension checklist on a rumour ("Dana's floated January"). Now floated changes become an open question that names what they'd block; only agreed ones touch the plan.
- **Unraised questions.** The health check now flags `OPEN` questions older than 7 days (never raised with anyone), not only `ASKED` ones older than 14 days.
- **Placeholder noise.** The health check now treats placeholders in not-yet-started context files as "not started", not as faults. Only the setup-filled files are must-fix. Intake also deletes a table's example row once real rows are added.

## 6. Fixes from an independent Fable 5.2 review (2026-11-19)

Claude Fable 5.2 was given the kit (without this changelog) and asked to break it by simulating a messy 16-week engagement. All 12 findings were checked against the files and applied.

1. **Drift checks were all passive.** Nothing ran unless someone asked, which is the failure the kit exists to prevent. Added a **Status block** to `CLAUDE.md` (End, Reporting until, Cadence, Audiences, Last summary, Last meeting note), kept current by the skills. **Every session** now compares it with today's date and flags an overdue summary, a meeting-note gap, an end date within 14 days, being past the reporting end date, or an open end-date question.
2. **Unresolved conflicts lived only in chat.** They now become `ASKED` open questions owned by the lead, listing the files left un-updated.
3. **Contradiction and FINAL risk.** CLAUDE.md said to act when a change is "mentioned"; intake said only when it's "agreed". Now both say *agreed*, and floated changes become `End date` / `Scope` questions. No summary can be marked FINAL while one is open, or without asking "is work actually stopping?"
4. **The header held a second copy of dates and team.** Dates now live only in `plan.md` (mirrored in the Status block); the header and README point to `plan.md` and `people.md`.
5. **Unmerged git work was invisible.** CLAUDE.md now has a Git section covering all writes: at session start, list unmerged `pos-*` branches and open PRs and work on top of them. The health check flags them (check 13).
6. **Team changes and actions.** `people.md` has Since / Until (replaced by) columns, and there's a new events row for joiners and leavers (reassign their questions and actions). Meeting actions have a Done column; weekly summaries and the health check (check 7) report overdue ones.
7. **Setup safety.** Setup never deletes a module folder with content in it, every `TBD` gets an open-question row, the health check searches for `TBD`, and "skip setup" renames the marker to `.pos-setup-skipped` instead of asking every session.
8. **Timeline steps were single-use and date-only.** The checklist section is now numbered steps, ticked in each decision record (a new block in `_templates/decision.md`), so a second extension starts from a clean list. It covers re-scopes too (scope table, MVP boundary, success criteria). Checks use "effective date = Revised if filled, else Planned". The close-out readiness check judges by files that exist, not checkboxes.
9. **Who can agree a change was undefined.** `people.md` has a "Can agree scope/dates?" column. Rule 1 now says a more recent statement doesn't automatically win between two people, and only someone marked `Y` makes a change agreed.
10. **Two audiences.** The health check counts summaries per audience, and the cadence has an effective date. Meeting notes have an **Internal only** section that never goes into client drafts.
11. **Trigger collisions.** Intake now routes research interviews to `research/interviews/` and offers stage 1. Experiment-capture no longer triggers on "write this up". Research stage 5 no longer triggers on "client deliverable" or "jobs to be done". Weekly-summary now triggers on "client update", "steering report" and "status report".
12. **Missing history.** Open questions have an Asked date (the 14-day clock) and a separate Blocking flag. Plan changes in summaries come from `decisions/`, not a diff. A `_raw/` file counts as new if no `Source:` line cites it.

## 7. Fixes from re-testing the Fable changes (2026-11-19)

The full simulation was re-run on the updated kit. Setup, intake and the health check covered an extension floated by someone without authority, a conflict between two stakeholders, a designer leaving mid-sprint, an "Internal only" remark, a research interview, and summaries missing for one audience. Every new safeguard fired, and nothing from "Internal only" reached a client summary. Three small gaps were fixed:

- **The Status block now records the meeting rhythm** (`Meetings:`). The session-start check couldn't judge a meeting gap without opening the log.
- **`Last summary` holds one date per audience.** A single date hid the fact that the client summaries were further behind than the internal ones.
- **Related TBDs can share one open-question row**, which keeps setup from producing a row per contact detail.

## Unchanged, deliberately

The philosophy and hard-won rules are intact: propose before executing, flag every conflict, the precedence rule, one file per meeting, the 14-day escalation, `closeout/` from day one, honest losses in experiments, and the stage 4/5 research prompts (integrity rules and visual system kept verbatim). The changes are about delivery, not doctrine.
