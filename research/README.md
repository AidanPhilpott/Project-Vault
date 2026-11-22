# Research

> Optional module. Setup keeps it only if research was chosen.

## Structure (create subfolders as content arrives)

```
research/
├── interviews/     ← raw notes / cleaned transcripts, one per interview: YYYY-MM-DD_role-name.md
├── analysis/       ← stage 1 outputs, one per interview
├── synthesis/      ← stage 2 (CISD) and stage 3 (higher-order synthesis)
├── outputs/        ← stage 4 design activation brief, stage 5 client readout (HTML)
└── reference/      ← background docs from others; note the source at the top of each
```

## Conventions

- **Raw notes and interpretation stay in separate files.**
- Scheduled interviews also get a row in `meetings/meeting-log.md`.
- Every synthesis file links to the files it draws on.
- Very large or confidential transcripts stay in `_raw/`. `interviews/` holds the cleaned, shareable version.

## The synthesis pipeline

Five skills, each taking the previous stage's **output** as its input:

| Stage | Skill | In | Out → folder |
|---|---|---|---|
| 1 | `research-1-interview-analysis` | One transcript | One analysis → `analysis/` |
| 2 | `research-2-cross-interview-synthesis` | All stage-1 analyses | CISD (affinity structure) → `synthesis/` |
| 3 | `research-3-higher-order-synthesis` | The CISD | Insights, opportunities, HMWs, tensions → `synthesis/` |
| 4 | `research-4-design-activation-brief` | Stage 3 | Designer-facing HTML brief → `outputs/` |
| 5 | `research-5-client-readout` | Stage 3 (+4) | Client-facing HTML readout → `outputs/` |

**Why staged:** each stage is a reviewable artifact, so a bad stage-2 output is cheap to catch while a bad one-shot readout isn't. Each stage compresses without losing the quotable specifics, and the intermediate files are useful on their own ("what did that participant actually say?").

**How to run it:** run stage 1 **one transcript at a time**, because batching produces noticeably worse analyses. Review the stage-1 outputs yourself before stage 2; it's the cheapest quality gate in the pipeline. Keep every intermediate file.

**Caution:** these skills produce a well-structured artifact from weak input just as readily as from strong input, and structure is not insight. At least once per project, check stages 1–2 against the real transcripts. If the synthesis has smoothed away someone's awkward, inconvenient point, that's usually where the real finding was.

## Status

| Round | Status | Notes |
|---|---|---|
| [Internal SME interviews] | Not started / Scheduled / In progress / Complete | |
| [External / user interviews] | | |
| [Synthesis] | | |
