# Project Operating System v2: setup

*Kit documentation. The setup skill deletes `_kit/` once the project is configured.*

A markdown-first, git-friendly project knowledge base that keeps a project legible to both people and AI assistants while it runs. It was extracted from an 18-week, 35-meeting project and revised based on what actually broke. v2 is an efficiency pass; see `CHANGELOG.md`.

## Automatic setup (recommended)

1. Copy this folder's **entire contents, including the hidden `.claude/` folder and `.pos-setup-pending`**, to the project root or a new empty repo. In Finder, press ⌘⇧. to show hidden files.
2. Optional: put your brief, SOW or kickoff deck in `_raw/`. Setup reads it first and only asks about the gaps.
3. Open the folder in Claude and start talking. Claude sees `.pos-setup-pending` and runs the `pos-setup` skill: basics, structural choices, logistics, and four questions that come from real post-mortems.
4. It fills in `CLAUDE.md`, `README.md` and the first context files, prunes unused modules, and deletes `_kit/` and the marker file.

To re-run setup, recreate an empty `.pos-setup-pending` and start a new session.

## Manual setup

1. Fill the placeholders in `CLAUDE.md`, especially **the one important caution** and the **Status block**, then `README.md`.
2. Fill `context/project-overview.md`, `people.md`, `plan.md` (set **reporting runs until** = the end date) and `risks-and-assumptions.md` (including tool dependencies).
3. Delete the optional modules you won't use (`research/`, `design/`, `experiments/`) along with their skills in `.claude/skills/`.
4. Read `closeout/CHECKLIST.md` now.
5. Delete `.pos-setup-pending` and `_kit/`.

## The skills

| Skill | Use it to |
|---|---|
| `pos-setup` | Configure the project (first run) |
| `pos-intake` | File transcripts, docs and notes into the right places |
| `pos-weekly-summary` | Draft the period's status update from the record |
| `pos-health-check` | Find drift: stale questions, missed summaries, a plan that no longer matches reality |
| `experiment-capture` | Interview someone and write up a workflow experiment |
| `research-1` … `research-5` | The interview → readout synthesis pipeline |

They live in `.claude/skills/`, where Claude Code and Cowork discover them automatically. If your tool doesn't, `CLAUDE.md` names each one by path, so you can say "run the pos-intake skill" and Claude will read the file.

## Tips from the source project

- **Start the glossary on day one.** The faster it builds, the sooner newcomers and AI can contribute.
- **The domain primer feels like overhead at kickoff and pays off in month three.**
- **Update context straight after decisions.** Delay is how drift starts.
- **Propose before executing** exists because silent rewrites worked until Claude got something confidently wrong.
- **Plan for the ending at the beginning.** Documentation usually stops 3–4 weeks before the work does, right in the middle of the handoff decisions.
