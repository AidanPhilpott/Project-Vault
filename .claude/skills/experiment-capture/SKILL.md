---
name: experiment-capture
description: >-
  Walk someone through writing up a workflow or tooling experiment they just ran (often
  an AI-assisted workflow): what they made, wins, losses, time impact, verbatim prompts,
  and how to reproduce it. Then write the entry into `experiments/` and index it. Use when
  someone says "I just tried a workflow", "log an experiment", "write up this experiment",
  "capture what I built", or wants a share-out or retro on an AI-supported task. Not for
  meeting notes or general write-ups (use `pos-intake`).
---

# Experiment capture

Produce **consistent, comparable, honest** write-ups. Output: `experiments/YYYY-MM-DD_short-name.md`, following `_templates/experiment.md` exactly.

## How to behave

- **One question at a time** (two if they're tightly linked). Skip anything already volunteered, and don't repeat their answers back to them.
- **Push for specifics.** "It saved time" isn't an answer. Ask how much, on what task, compared with what baseline. If they don't know, take an honest low estimate.
- **Push for losses.** If they say there were none, ask "what was the most frustrating moment?" or "what would have stopped someone less determined?"
- **Get prompts and configs verbatim.** Never summarize them.
- **Don't editorialize.** Capture *their* experience. Use the tone set in `CLAUDE.md`.
- **Contradictions** (e.g. "30 min" then later "about an hour"): note both and ask which to record.

## The flow (mirrors the template)

1. **Header:** name, date run, status, phase
2. **What they made:** a one-sentence summary first (make them compress it), then the detail, then links to the artifacts
3. **What it's for:** the problem, who'd use it, and **when not to use it** (push gently)
4. **Set-up:** honest time including dead ends, tools (model, skills, MCPs), numbered steps ("if you did it again tomorrow…"), **verbatim prompts**, gotchas
5. **Wins:** time deltas, quality jumps, things that are newly possible
6. **Losses:** cost overruns, brittleness, things it got confidently wrong. Don't accept silence.
7. **Time impact:** AI-supported time vs manual baseline, the difference, re-prompts needed, and the cumulative picture if it's been run several times
8. **Output quality:** would they trust it unsupervised, and where did a human need to be in the loop?
9. **Key learnings:** 3–5 transferable insights. Push back on generic ones.
10. **Reproducibility:** what someone else needs, what looks reusable but isn't, time to first useful output
11. **Next time and next steps:** what they'd change, improvements to the workflow, what it opens up, and the next concrete experiment
12. **Risks:** drift, hallucination, dependence on a particular model version
13. **Tags**

## Writing it

1. Suggest a filename from the one-sentence summary and let them tweak it.
2. Write to `experiments/`. Empty fields become `TBD`; never fabricate a plausible answer.
3. Add a row to the index at the top of `experiments/README.md`.
4. Show the file, then offer **one** relevant follow-up, e.g. adding it to this week's summary under Experiments. Keep the postamble short; the file is the deliverable.

## Why honesty matters here

Performative time-saving numbers are the standard failure of any AI pilot, and the person filling this in may be quietly incentivized to overstate. Ask the probing questions a thoughtful peer would. Specifics, baselines and a real losses section are the antidote.
