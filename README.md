# Project Vault: Project Operating System v2

*Kit documentation. When you set up a project, `pos-setup` replaces this file with the project's own README (from `_kit/project-README.md`) and deletes `_kit/`.*

A markdown-first, git-friendly project knowledge base that keeps a project legible to both people and AI assistants while it runs. Every fact has one home, every meeting gets a file, open questions have owners and dates, and a set of Claude skills does the filing, reporting and drift-checking for you.

## Why it exists

Projects rarely fail for lack of information. They fail because the information is scattered and goes stale. Decisions live in someone's memory or a transcript nobody reopens. Open questions get asked once and then forgotten. The plan quietly stops describing reality while still looking authoritative. Status updates stop a few weeks before the work does, just when the handoff decisions are being made. And when someone new joins, or an AI assistant is asked to help, there's no reliable place to start.

The vault fixes this by giving every project **one trustworthy, current record**: what we're doing, why, who decided what, what's still unknown, and how it ends.

## How it works

- **A fixed structure with one home per fact.** Scope, people, plan, risks, decisions, meetings and open questions each live in exactly one file. Everything else links to them, so there's nothing to keep in sync.
- **A short bootstrap file (`CLAUDE.md`)** that Claude reads every session. It holds the rules, a routing table that says where everything goes, and a live **Status block** of key dates.
- **Skills that do the upkeep.** Claude files new material, drafts status updates, and audits the folder for drift. It proposes every change before making it and flags every conflict, rather than silently overwriting.
- **Checks that run without being asked.** Each session starts by comparing the Status block with today's date and saying so if a summary is overdue, meetings have stopped being logged, or the end date is close.
- **Plain markdown in git.** It's readable by anyone, works with any editor, and changes go through branches and PRs, so a person always reviews what changed.

## What it helps with

- **Turning meetings and documents into a usable record.** Drop in a transcript, deck or PDF, and you get a meeting note, updated context, decision records and new open questions, with contradictions flagged.
- **Status reporting.** Weekly or sprint summaries for internal and client audiences, drafted from what's actually in the record. Missed weeks are caught up and clearly labelled as reconstructions.
- **Catching drift early.** Stale questions, missing summaries, unlogged meetings, overdue actions, and a plan that no longer matches reality.
- **Onboarding.** A newcomer, or an AI assistant, can get up to speed from the domain primer, glossary, overview and meeting log instead of a week of catch-up calls.
- **Scope and timeline changes.** Only people with authority can agree a change. Rumoured extensions are tracked as questions, and agreed ones run a checklist so nothing is left pointing at the old date.
- **Research.** An optional five-stage pipeline from interview transcripts to insights, design briefs and client readouts.
- **Ending well.** Close-out is planned from day one, so documentation goes up at the end of the project, not down.

## Where it comes from

The foundations were laid across several complex projects, with more than 300 meetings between them. Each rule exists because its absence caused a real problem: a missed handoff, a forgotten question, a plan that drifted, or a summary that never got written. This is v2, an efficiency and reliability pass; see [`_kit/CHANGELOG.md`](_kit/CHANGELOG.md).

---

## Start a new project

### 1. Copy the kit

Pick one:

- **GitHub template / clone:** create a new repo from this one, or clone it and repoint `origin` at the project's repo.
- **Plain folder:** copy the **entire contents, including the hidden `.claude/` folder and `.pos-setup-pending`**, into the project folder. In Finder, press ⌘⇧. to show hidden files.

One vault per project. Don't run several projects out of one folder.

### 2. (Optional) Drop in kickoff material

Put the brief, SOW, proposal or kickoff deck in `_raw/`. Setup reads it first and only asks about the gaps. `_raw/` is git-ignored, so originals never get committed.

### 3. Open the folder in Claude and say anything

Claude sees `.pos-setup-pending` and runs `pos-setup` before your first request. It takes one focused conversation:

| Beat | What it asks |
|---|---|
| Basics | Name, code, relationship, goal, team, who can agree scope/dates, start and end |
| Structure | Optional modules (research / design / experiments), propose-vs-update mode, which source wins in a conflict, git or not |
| Logistics | Git host and branch protection, reporting cadence and audiences, what must never go in the folder, tone |
| Four post-mortem questions | The one easy-to-forget caution · tool dependencies · benefit claims that need evidence · how the project ends |

It then fills in `CLAUDE.md` (including the Status block), `README.md`, `context/project-overview.md`, `people.md`, `plan.md` and `risks-and-assumptions.md`, prunes the modules you didn't choose, deletes `_kit/` and the marker, and lists anything left as `TBD` (each with a row in `open-questions.md`).

- **Skip it:** say "skip setup". The marker is renamed to `.pos-setup-skipped` and won't nag you again.
- **Resume or re-run:** rename it back, or create an empty `.pos-setup-pending`, and start a new session.

### Manual setup (no Claude, or you prefer to do it by hand)

1. Copy `_kit/project-README.md` over `README.md` and fill its header.
2. Fill the placeholders in `CLAUDE.md`, especially **the one important caution** and the **Status block**.
3. Fill `context/project-overview.md`, `people.md`, `plan.md` (set **Reporting runs until** = the end date) and `risks-and-assumptions.md` (including tool dependencies).
4. Delete the optional modules you won't use (`research/`, `design/`, `experiments/`) and their skills in `.claude/skills/`.
5. Read `closeout/CHECKLIST.md` now.
6. Delete `.pos-setup-pending` and `_kit/`.

---

## Using the vault day to day

The rhythm is: **material in → intake → context stays current → summaries go out → health check catches drift → close-out at the end.**

### What Claude does every session

`CLAUDE.md` is loaded automatically. It's kept short on purpose and routes Claude to other files only when needed. Before your request, Claude compares the **Status block** with today's date and says so in one line if:

- a summary is overdue for any audience
- the last meeting note is older than twice the meeting rhythm
- the end date is within 14 days, or today is past "Reporting until"
- there's an open question about the end date

If you're using git, it also lists unmerged `pos-*` branches and open PRs so you build on the latest notes.

### The working loop

| When… | Do this |
|---|---|
| A meeting happens | Paste or drop the transcript/notes and say "file this". **One file per meeting**, even "short call, nothing decided". |
| A doc, deck or spreadsheet arrives | Same: "add this to the project". Intake works out what's new, changed or contradicted. |
| A decision is made | Intake records it in `decisions/` and updates the affected `context/` file. Do it straight away; delay is how drift starts. |
| Something is unknown or disputed | It goes in `context/open-questions.md` with an owner, raised date, status and what it blocks. Nowhere else. |
| The reporting period ends | "Draft this week's update" (per audience: internal / client). |
| Things feel out of date, or before a status meeting | "Health check". |
| The end date or scope changes **and is agreed** | Claude runs the timeline/scope steps in `closeout/CHECKLIST.md`. Only **floated**? It becomes an open question and the plan isn't touched. |
| Someone joins or leaves | Tell Claude. Their row gets Since/Until dates and their open items are reassigned. |
| The final two weeks begin | Work through `closeout/CHECKLIST.md`. Documentation goes **up** at the end, not down. |

### Rules worth knowing

- **Propose before writing** (default). Claude lists every file it will change, waits for a go-ahead, then lists what it changed.
- **Conflicts are named, never silently resolved.** Both sources, which wins and why, and the lead is asked. Unresolved ones become open questions.
- **Only someone marked `Y` under "Can agree scope/dates?" in `people.md` can agree a change.** A more recent statement doesn't automatically win.
- **Reconstructions are labelled** with when they were written and from what.
- **"Internal only"** sections of meeting notes never reach client-facing drafts.
- **Not in this folder:** live confidential data, PII, credentials (set per project at setup).

### Git flow

For git projects, every write from any skill goes on a personal branch `<owner>/pos-<topic>`, is committed and pushed, and ends in a PR. Claude never commits to the protected branch and never merges; a human does.

---

## The skills

They live in `.claude/skills/<name>/SKILL.md`, where Claude Code and Cowork find them automatically. You don't need to name them: describe what you want and Claude picks the skill. If your tool doesn't discover skills, say "run the pos-intake skill" and Claude will read the file.

### Core (always kept)

| Skill | Use it when | Say something like | What you get |
|---|---|---|---|
| `pos-setup` | First run, or reconfiguring | (automatic) · "re-run setup" | Filled `CLAUDE.md`, README and core context; pruned modules |
| `pos-intake` | Any new material: transcripts, notes, decks, PDFs, Word docs, spreadsheets | "File this meeting" · "Add this to the project" · "Process what's in `_raw/`" | A combined update plan, then the meeting note + log row, context updates, decisions, open questions, and every conflict flagged. Multiple docs are processed oldest first. Research interviews are routed to `research/interviews/`. |
| `pos-weekly-summary` | End of a reporting period | "Weekly update" · "Client update" · "Steering report" · "Sprint summary" | One summary per audience from that period's meetings, decisions, question changes and overdue actions. Missed periods are caught up as labelled reconstructions. |
| `pos-health-check` | Something feels stale, the Status check flags it, or before a status meeting | "Health check" · "What's stale?" · "Is the folder up to date?" | A read-only drift report (stale questions, missing summaries, unlogged meetings, overdue actions, plan vs reality, hidden TBDs, unmerged branches, close-out readiness) with proposed fixes. It never fixes silently. |

### Optional modules

| Skill | Module | Use it when | Say something like |
|---|---|---|---|
| `experiment-capture` | `experiments/` | You just tried a workflow or AI tooling approach and want it written up: wins, losses, time impact, verbatim prompts, how to reproduce | "Log an experiment" · "Capture what I built" |
| `research-1-interview-analysis` | `research/` | One interview transcript → structured analysis with confidence labels | "Analyse this interview" · "Run stage 1" |
| `research-2-cross-interview-synthesis` | `research/` | Several stage 1 analyses → themes and affinity clusters (CISD) | "Synthesize the interviews" |
| `research-3-higher-order-synthesis` | `research/` | CISD → insights, opportunity spaces, How-Might-Wes, tensions | "Run stage 3" · "Insights and HMWs" |
| `research-4-design-activation-brief` | `research/` | Stage 3 → a brief a designer can start sketching from | "Design activation brief" |
| `research-5-client-readout` | `research/` | Stage 3 → a polished client-facing HTML readout | "Research readout" · "Insight cards" |

The research pipeline runs `interviews/ → analysis/ → synthesis/ → outputs/`. Run stage 1 once per interview, then stages 2 and 3 across the set; 4 and 5 are two different outputs from stage 3.

---

## Folder map

```
├── CLAUDE.md            ← AI bootstrap: rules, routing table, Status block (loaded every session)
├── README.md            ← this guide in the kit; the project's README after setup
├── context/             ← long-lived project knowledge, one topic per file
│   ├── project-overview.md      scope, goals, success criteria, benefit claims
│   ├── future-state.md          vision, principles, MVP vs later
│   ├── current-state.md         how things work today
│   ├── domain-primer.md         plain-language orientation
│   ├── glossary.md              terms and acronyms
│   ├── people.md                who's who, contacts, who can agree changes
│   ├── users-and-stakeholders.md  personas, influence, org structure
│   ├── plan.md                  dates, milestones, cadence, how this ends
│   ├── risks-and-assumptions.md risks, assumptions, tool dependencies
│   └── open-questions.md        the ONLY place open questions live
├── decisions/           ← decision records + index
├── meetings/            ← one file per meeting + meeting-log.md
├── weekly-summaries/    ← status updates, per audience
├── closeout/            ← how the project ends (present from day one)
├── research/            ← optional: interviews + synthesis pipeline
├── design/              ← optional: reviews, prototypes
├── experiments/         ← optional: workflow/tooling experiments
├── _templates/          ← blank templates; copy, never edit in place
├── _raw/                ← local-only originals (git-ignored)
├── _kit/                ← kit-only docs; deleted at setup
└── .claude/skills/      ← the skills that run this system (hidden folder)
```

Need a module that isn't here (e.g. a `distilled/` folder)? See `_templates/README.md`: add a template, a folder and a routing row in `CLAUDE.md`.

---

## Tips from the projects behind it

- **Start the glossary on day one.** The faster it builds, the sooner newcomers and AI can contribute.
- **The domain primer feels like overhead at kickoff and pays off in month three.**
- **Update context straight after decisions.** Delay is how drift starts.
- **Propose before executing** exists because silent rewrites worked until Claude got something confidently wrong.
- **Plan for the ending at the beginning.** Documentation usually stops 3–4 weeks before the work does, right in the middle of the handoff decisions.
- **Meetings or summaries stopping while work continues** is this system's most common failure. The Status block and health check exist to catch it.

## Maintaining the kit

Change the kit in this repo, on a branch, via PR. Note what changed and why in `_kit/CHANGELOG.md`. Opening this repo in Claude will trigger the setup interview (the marker is part of the kit); say "skip setup" for the session, and don't commit the renamed marker.
