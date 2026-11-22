# [Project Name]

**Code / ticket:** [XXXXX or none] · **Lead:** [Name] · **Dates and team:** see `context/plan.md` and `context/people.md`

[1–3 sentences: what this is trying to achieve, what gets produced, what makes it distinct.]

---

## Folder map

```
├── CLAUDE.md            ← AI bootstrap: rules + routing table (read first if using AI)
├── README.md            ← you are here
├── context/             ← long-lived project knowledge, one topic per file
├── decisions/           ← decision records + index
├── meetings/            ← one file per meeting + meeting-log.md index
├── weekly-summaries/    ← status updates
├── closeout/            ← how this project ends (present from day one)
├── research/            ← optional: interviews + synthesis pipeline
├── design/              ← optional: reviews, prototypes
├── experiments/         ← optional: workflow/tooling experiments
├── _templates/          ← blank templates; copy, never edit in place
├── _raw/                ← local-only originals (git-ignored)
└── .claude/skills/      ← the skills that run this system (hidden folder)
```

## Quick links

- New here? → `context/domain-primer.md`, then `context/project-overview.md`, then `meetings/meeting-log.md`
- Who's who → `context/people.md` · Jargon → `context/glossary.md`
- Why did we decide X? → `decisions/README.md`
- What's still unknown? → `context/open-questions.md`
- How does this end? → `closeout/CHECKLIST.md`

## Working in this folder

Open the folder in Claude (Claude Code or Cowork) and talk normally. Claude reads `CLAUDE.md` every session, checks the Status block for drift, and picks the right skill from what you ask.

| You want to… | Say something like… | Skill |
|---|---|---|
| File a transcript, deck, doc or notes | "Add this meeting to the project" (or drop it in `_raw/`) | `pos-intake` |
| Send a status update | "Draft this week's client update" | `pos-weekly-summary` |
| Check nothing has gone stale | "Health check" / "What's out of date?" | `pos-health-check` |
| Write up a workflow or AI experiment | "Log an experiment" | `experiment-capture` |
| Analyse research interviews | "Analyse this interview", then "synthesize interviews" | `research-1` … `research-5` |

Every write is proposed first and listed afterwards. If this project uses git, changes land on a `<owner>/pos-*` branch with a PR, and a human merges. The full rules are in `CLAUDE.md`.
