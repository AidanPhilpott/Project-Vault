---
name: pos-setup
description: >-
  First-run setup interview for this Project Operating System (POS). Run it when a
  `.pos-setup-pending` file exists in the project root (or `.pos-setup-skipped` and the user asks to resume), or when the user asks to
  "set up", "configure", "re-run setup" or "kick off" the project operating system.
  Interviews the user (or extracts answers from kickoff docs they provide), then
  fills in CLAUDE.md, README.md and the first context files, and prunes unused modules.
---

# POS setup interview

Turn the `[bracketed placeholders]` into a configured project in one focused conversation, not twenty questions spread over two weeks. The interview *is* the permission to write files: don't ask before each write, and show the result at the end.

## Step 0: Start from documents if there are any

Ask once: *"Do you have a brief, SOW, proposal or kickoff deck I can read first? I'll pull what I can from it and only ask about the gaps."* If yes, read it (or look in `_raw/`), pre-fill answers, and **only ask what's still missing** in the beats below. Confirm anything you inferred instead of asking it fresh.

## Beat 1: Basics (one plain message)

- Project name, plus any job code, engagement number or ticket
- Relationship: external client, internal cross-team, or solo/small team
- What it's trying to achieve and what it produces (1–2 sentences)
- Lead, plus team names and roles. Who can actually agree a change to scope or dates (on both sides, if there's a client)?
- Start date, expected end (or "ongoing"), and the phase/sprint structure if there is one

## Beat 2: Structural choices (one `AskUserQuestion` call)

1. **Optional modules** (multiSelect): `research/` · `design/` · `experiments/` · none. The core folders (context, meetings, decisions, weekly-summaries, closeout) are always kept.
2. **Context updates:** *Propose and wait for a go-ahead* (Recommended: prevents silent drift) / *Update, then flag what changed*
3. **When sources disagree:** *Live conversations win* (Recommended) / *Written docs and contracts win* / *No default, always ask*
4. **Version control:** *Existing git repo* / *New git repo, help me set it up* / *Local folder, no git*

## Beat 3: Logistics (one message)

- If git: which host (GitHub, Azure DevOps, GitLab…)? Is the default branch protected, so changes go through a PR?
- Reporting cadence (weekly, biweekly, sprint-end, none), and does it go to one audience or two (internal + client)?
- What must **never** be written into this folder? There's always something (confidential data, NDA material, PII, live client data). Push gently if the first answer is "nothing."
- Any tone preference for docs (default: direct, plain language)

## Beat 4: The four questions that earn their keep

Each one comes from a real post-mortem. Don't skip them, even if the user is eager to move on.

1. **"What's the one thing about this project that's easy to get wrong or forget if it isn't written down?"** → the caution in `CLAUDE.md`
2. **"What tools does this depend on, and what happens if one is unavailable for a week?"** → the Tool dependencies table in `context/risks-and-assumptions.md`
3. **"Is this project claiming a benefit someone will want evidenced later?"** If yes: how will it be measured, and can you see historical data or only a rolling window? → the Benefit claims section in `context/project-overview.md`
4. **"How will you know this is ending, and who needs what when it does? How likely is an extension or a reshape?"** → the "How this ends" section in `context/plan.md`

## Step 5: Write it up

1. **`CLAUDE.md`:** fill every placeholder (project block, caution, "does NOT go in", precedence rule, update mode, tone) and the **Status block** (End, Reporting until = End, Cadence, usual Meetings rhythm, Last summary with one date per audience, all `none` to start, and Last meeting note = `none`). In the routing table, delete rows for modules that weren't chosen.
2. **`README.md`:** fill the header and summary, and remove unchosen modules from the folder map.
3. **`context/`:** fill `project-overview.md`, `people.md` (including **Can agree scope/dates?** for each person and Since = start date), `plan.md` (including **reporting end date = project end date**) and `risks-and-assumptions.md` from the answers. Leave the rest as templates; they fill in through real work. Delete sections that clearly don't apply (e.g. invoicing on an internal project, the counterpart section on a solo project).
4. **Prune unchosen modules:**
   - no research → delete `research/` and `.claude/skills/research-*`, and the research row in the `CLAUDE.md` routing table
   - no design → delete `design/`
   - no experiments → delete `experiments/`, `.claude/skills/experiment-capture/` and `_templates/experiment.md`
   - **never delete `closeout/`**
   - **Never delete a module folder that contains anything except its README** (this matters when setup is re-run). List what's in it and ask.
5. **Git:**
   - If git was chosen: confirm the repo, or offer `git init`. In `.claude/skills/pos-intake/SKILL.md`, replace the host placeholder with the exact PR command (`gh pr create`, `az repos pr create`, `glab mr create`) and note whether the branch is protected.
   - If no git: delete the "Git" section from `CLAUDE.md` and the "If this project uses git" section from `pos-intake`.
6. **Clean up:** delete `.pos-setup-pending` (or `.pos-setup-skipped`) and the `_kit/` folder.
7. **Verify:** search `CLAUDE.md`, `README.md` and the four filled context files for leftover `[placeholders]` (ignore markdown links). Replace each with a real answer or `TBD: ask <person>`. **Every `TBD` also gets a row in `open-questions.md`** (owner = that person), so the health check can see it. Related TBDs can share one row (e.g. "Acme contact details"). Delete example table rows once real rows are in. `>` guidance notes stay.
8. **Report back** in a few lines: what was filled in, what's still TBD, and the next step (usually: "drop your kickoff materials into `_raw/` and I'll run `pos-intake`").

To re-run setup later, recreate an empty `.pos-setup-pending` (or rename `.pos-setup-skipped` back) and start a new session. A re-run updates the existing files rather than starting from blank templates.
