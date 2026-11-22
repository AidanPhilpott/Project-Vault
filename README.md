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

## How it's maintained

New material gets filed through the `pos-intake` skill: a meeting note, a meeting-log row, and updates to the affected context files, with every change listed for review. The full rules are in `CLAUDE.md`.
