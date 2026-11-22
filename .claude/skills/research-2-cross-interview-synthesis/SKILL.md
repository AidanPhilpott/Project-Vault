---
name: research-2-cross-interview-synthesis
description: >
  Synthesize themes and patterns across a set of completed Stage 1 interview analysis files.
  Use this skill when the user wants to cluster findings across multiple interviews, build an
  affinity diagram, or produce a Cross-Interview Synthesis Document (CISD) ready for Stage 3.
  Trigger when the user mentions "synthesize interviews", "cross-interview synthesis", "affinity
  diagram", "CISD", or provides multiple Stage 1 analysis files to consolidate.
---

# Stage 2 — Multiple Interview Synthesis
**Version 1.0 · Claude skill file**

> **How to use:** Provide all completed Stage 1 interview analysis files. Claude will cluster themes bottom-up across the full set, name each cluster, surface cross-cutting patterns, and produce a structured CISD ready for Stage 3 (Higher-Order Synthesis).
>
> **Input:** All completed Stage 1 Individual Interview Analysis files (N ≥ 2)
> **Output:** Cross-Interview Synthesis Document (CISD) — a structured affinity diagram with named themes, frequency counts, representative quotes, and a confidence label per cluster

---

## Instructions for Claude

1. **Read all input files first.** Do not begin synthesis until every Stage 1 file has been reviewed in full.

2. **Extract data points.** Pull individual observations, quotes, pain points, JTBDs, and surprises from each file. Tag each with the participant's role and organisation.

3. **Cluster bottom-up.** Group related data points into natural clusters. Do not use the Stage 1 theme names as predetermined categories — let the cross-file patterns emerge.

4. **Name each cluster.** Write a short, descriptive theme label that captures the essence of each group. Avoid jargon.

5. **Build hierarchy.** Organise clusters into 3–5 higher-level themes. Each top-level theme should have 2–4 sub-clusters beneath it.

6. **Write a synthesis statement per theme.** One sentence capturing the "so what" — what does this cluster tell us about user behavior, need, or belief?

7. **Record frequency and confidence.** For each cluster, note how many participants contributed data points and whether the pattern is `Explicitly stated` or `Inferred`.

8. **Surface tensions.** Note any clusters where participant data points directly conflict with each other. Do not smooth these over — flag them explicitly for Stage 3.

9. **Carry forward surprises.** Any item marked as a surprise in a Stage 1 file should appear in the CISD, even if it appears only once. Minority voices belong in the record.

10. **Output format.** Present the CISD as a structured document with: Input Summary table, theme hierarchy, frequency counts, representative quotes per cluster, and a tensions section. Save it as `research/synthesis/YYYY-MM-DD_cisd.md` and link each cluster back to its source files in `research/analysis/`.

---

## Output Structure

The CISD Claude produces should follow this structure:

```
CISD — [Project Name] · [Date]

Input Summary
  - Interviews included: N=
  - Participant segments:
  - Date range:

Theme 1 — [Label]
  Synthesis statement: ...
  Sub-clusters:
    1a. [Label] · N= · Confidence:
        Representative quote: "..." — [Role / Org]
    1b. ...

Theme 2 — ...

Tensions flagged:
  - [Description of conflict] · Participants: [roles]

Minority voices:
  - [Observation] · Source: [role / org]
```

---

*Next step: run `research-3-higher-order-synthesis` on the completed CISD.*

*Skill version 1.0 · Stage 2 of 5*
