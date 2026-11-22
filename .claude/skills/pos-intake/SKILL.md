---
name: pos-intake
description: >-
  File one or more documents (meeting transcripts, notes, decks, PDFs, Word docs,
  spreadsheets, research interview transcripts) into this Project Operating System, the
  team's living project knowledge base or "second brain". Works out what's new, changed or
  contradicted, proposes an update plan, writes the meeting note, context updates,
  decisions and open questions, and flags every conflict. Routes research interviews to
  `research/`. If the project uses git, works on a personal branch and ends in a PR. Use
  whenever someone says "add this to the project", "process this transcript / meeting",
  "update the notes from this", "file this", or drops material in `_raw/`, even if they
  don't name the system. Not for standalone deliverables that aren't being filed into
  the project.
---

# POS intake

`CLAUDE.md` is the spec: its routing table says where things go, and its rules set precedence, update mode and what counts as "agreed". **Read it first and defer to it.** This skill is the procedure.

## 1. Read everything properly

- Locate the material: attached, pasted, a path, or files in `_raw/`. A `_raw/` file is **new** if no `Source:` line in `meetings/` or `research/` cites its filename. If something is attached but you can't see a path, ask.
- Use the right reader: PDF → `pdf` skill · Word → `docx` · PowerPoint → `pptx` · Excel/CSV → `xlsx` · text/markdown → read directly.
- **Read it in full; don't skim.** With several documents, process them **oldest first**, so later material correctly supersedes earlier material.
- **Research interview?** (one participant being interviewed about their work, rather than a project meeting) If `research/` exists, file the cleaned transcript in `research/interviews/YYYY-MM-DD_role-name.md`, add a meeting-log row, and offer `research-1-interview-analysis`. Don't write a meeting note for it.
- Don't copy raw originals into the tracked folders. The synthesized note is the artifact; cite the original by filename (`_raw/…`) or by where it lives.

## 2. Diff and propose

Search the relevant `context/` files, `meetings/meeting-log.md` and recent meeting notes. Then present **one plan covering all the documents**:

- **New:** files to create (meeting note, decision record…)
- **Changed:** existing files and a one-line "what changes" for each
- **Contradicted:** each conflict, naming both sources and which wins under the precedence rule (`CLAUDE.md` Rule 1). Ask the lead to resolve anything that can't wait.

Under "propose and wait" mode, stop here for a go-ahead (unless the user said "just go"; then proceed and state your assumptions). Under "update and flag" mode, go straight on.

## 3. Write, in this order

1. **Meeting note** from `_templates/meeting.md`. One per meeting, even short ones. Set the `Source:` line honestly. Put anything that mustn't reach the client (friction, margins, people issues) under **Internal only**.
2. **Context files**, per the routing table: terms → glossary, people → people, risks → risks-and-assumptions, scope → project-overview, direction → future-state, dates → plan.
3. **Decisions** that meet the bar in `decisions/README.md` → a new file from `_templates/decision.md` + an index row.
4. **`meetings/meeting-log.md`:** an index row, plus a Themes entry if a pattern is emerging.
5. **`context/open-questions.md`:**
   - Add new questions (owner, raised date, status, what they block).
   - Every **conflict not resolved in this session** becomes a row: status `ASKED`, owner = the lead, Blocks = the files you left un-updated because of it. Mention it in the meeting note too.
   - Move answered questions to Answered, with the source.
   - Flag any `ASKED` question whose asked date is more than 14 days old.
6. **`CLAUDE.md` Status block:** update `Last meeting note`.

When you add the first real row to a table, delete the `[placeholder]` example row in the same table.

**Timeline or scope changes** (see `CLAUDE.md` Rule 1 for who can agree one):
- **Agreed** → stop and run the "Timeline or scope change" steps in `closeout/CHECKLIST.md` before moving on.
- **Only floated** ("might", "Dana's thinking about…"), or agreed by someone without authority → don't touch `plan.md`. Add an open question with Area `End date` or `Scope`, the person who can confirm it as owner, and what it would block (usually the reporting end date). Call it out in your summary.

**People changes:** if someone joins or leaves, follow that row in the `CLAUDE.md` events table.

## 4. Confirm

Show: files created, files edited (one line each), conflicts still open (now logged as questions), and anything left `TBD`. If using git, also show the branch. Get an explicit yes before committing (or, with no git, before finishing under "propose" mode).

## If this project uses git

*(Setup deletes this section for non-git projects.)*

- **Never commit to the protected branch, and never complete the merge.** A human reviews and merges.
- **Before writing:** list unmerged `<owner>/pos-*` branches and open PRs. If earlier intake work is still unmerged, tell the user and branch from it (or add to it), not from the default branch. Otherwise you'll be working without the latest notes.
- If you're on the default branch, create `<owner>/pos-<topic>` (owner from `git config user.email`). Try a `git pull --ff-only`, but don't let it block you.
- After confirmation:
  ```bash
  git add <changed paths>
  git commit -m "POS intake: <what was filed>"
  git push -u origin <branch>
  ```
- Open the PR with: `[HOST PR COMMAND: filled in at setup]`. If no CLI is available, give the user a ready-to-click PR link.
- Report back: what was filed and where, unresolved conflicts, the branch, and the PR link. Remind them the merge is theirs. The same branch-and-PR flow applies to writes from `pos-weekly-summary`, `pos-health-check` fixes and the timeline-change steps.
