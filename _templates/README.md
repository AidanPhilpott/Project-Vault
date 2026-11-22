# _templates

Blank templates. **Copy one, never edit it in place.** Keeping templates out of the working folders stops placeholder files from showing up as real meetings or decisions when anyone (or Claude) searches the project.

| Template | Copy to |
|---|---|
| `meeting.md` | `meetings/YYYY-MM-DD_short-name.md` |
| `decision.md` | `decisions/YYYY-MM-DD_short-name.md` |
| `weekly-summary.md` | `weekly-summaries/YYYY-MM-DD_week-N.md` |
| `experiment.md` | `experiments/YYYY-MM-DD_short-name.md` |
| `retrospective.md` | `closeout/YYYY-MM-DD_retrospective.md` |
| `feedback-and-outcomes.md` | `closeout/YYYY-MM-DD_feedback-and-outcomes.md` |
| `deliverables-index.md` | `closeout/YYYY-MM-DD_deliverables-index.md` |

The research stage templates live inside their skills (`.claude/skills/research-*`).

**Adding your own:** if a project needs a new output type (e.g. one-pagers for sharing ideas with a wider team), put its template here, give it its own folder, and add a row to the routing table in `CLAUDE.md`.
