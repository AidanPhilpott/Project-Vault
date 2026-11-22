---
name: research-4-design-activation-brief
description: >
  Transform a completed Stage 3 Higher-Order Synthesis into a designer-facing activation brief.
  Use this skill when the user wants to reframe research findings for a UX or product designer,
  produce a Design Activation Brief, or create a shareable asset a designer can open and start
  sketching from immediately. Trigger when the user mentions "design brief", "activation brief",
  "designer-facing", "HMW deck", "surface map", or "design directions". Also trigger when the
  user provides a Stage 3 synthesis document and wants to move into design exploration.
---

# Stage 4 — Design Activation Brief
**Version 1.0 · Claude skill file**

> **How to use:** Provide the completed Stage 3 Higher-Order Synthesis document. Swap the three bracketed fields in the prompt below, then run it. The most important part is the Core Transformation paragraph — if you ever trim the prompt for length, keep that and the section list. The Integrity Rules are what stop the brief from laundering thin evidence into confident directives; keep them verbatim.
>
> **Input:** Completed Stage 3 Higher-Order Synthesis document
> **Output:** A single self-contained HTML file — a designer-facing activation brief with status filters, HMW deck, and an evidence-layer toggle

---

## The Prompt

```
You are a senior design strategist. I'm going to give you a research synthesis
(or interview/discovery findings). Transform it into a DESIGN ACTIVATION BRIEF:
a self-contained, shareable asset a UX/Product designer can open and immediately
start early design exploration from.

INPUT:
- Source document: [PASTE OR ATTACH the completed Stage 3 synthesis document]
- Project context: [1–2 lines: what's being designed, for whom, what stage]
- MVP / primary audience: [who the design is actually for]

CORE TRANSFORMATION (this is the whole point):
Re-pivot the material from a RESEARCHER's frame to a DESIGNER's frame.
- A researcher's doc is organized by finding → evidence → confidence.
- A designer needs the opposite: surface → directive → what-to-avoid → what's-unsettled.
Lead with what to DESIGN, not what was FOUND. Keep the research receipts available
but out of the way (see "evidence layer" below). Never make the designer parse
frequency counts or theme codes to know what to draw.

REQUIRED SECTIONS (in this order):
1. North Stars — the key insights distilled into ~5–7 crisp design principles,
   each a short imperative headline + 2–3 sentences + a tiny source tag.
2. Surface Map — the concrete screens/surfaces to start sketching. One card per
   surface, each with: (a) a one-line design directive, (b) "what to avoid,"
   (c) the generative How-Might-We to sketch against, (d) a status tag (below),
   and (e) a hidden evidence line with the backing data/quote.
3. Tensions to design through — every genuine conflict between user needs. Show
   both sides with attribution, then a "recommended design territory" (a direction,
   not a verdict). Do NOT smooth tensions away.
4. Lock before you wireframe — the few decisions that shape every downstream screen.
5. Don't over-build yet — anything that looks solid but rests on thin/absent evidence
   for the primary audience. Tell the designer to sketch loosely here, not commit structure.
6. HMW deck — all the How-Might-We questions pulled out as quick-reference cards.

STATUS TAXONOMY (use on every surface, color-code it meaningfully):
- "Build now" = validated for the primary audience, design it.
- "Reserve IA" = real need but later phase; leave it a home in the IA now, build it later.
- "Decision needed" = blocked on an unresolved question; don't harden structure yet.

FORMAT & INTERACTIVITY:
- Output a single self-contained HTML file (inline CSS/JS, no external dependencies
  beyond web fonts). If the desired format is ambiguous, default to this.
- Include a STATUS FILTER (chips) so the designer can isolate surfaces by status.
- Include an EVIDENCE-LAYER TOGGLE: directives show clean by default; flipping it on
  reveals the frequency/confidence/quote backing under each one. Default = off.
- Make it responsive and shareable as a standalone link.

DESIGN QUALITY BAR:
- Editorial, studio-grade, intentional. Avoid generic "AI" aesthetics: no Inter/Roboto/
  system fonts, no purple-gradient-on-white, no cookie-cutter card grids.
- Pick a distinctive type pairing (characterful display + clean body + a mono for tags)
  and a restrained palette where color carries MEANING (tie it to the status taxonomy).

INTEGRITY RULES (do not skip):
- Every directive must be traceable to something in the source — no inventions.
- Preserve minority/dissenting voices; surface them in a tension or a caveat, don't bury them.
- Carry forward any caveats from the source (e.g. "pending review," small sample,
  unvalidated assumptions). Flag provisional directives AS provisional.
- Distinguish what's validated for the PRIMARY audience from what comes from adjacent
  segments; don't let adjacent-segment confidence drive primary-audience decisions.

If the source is missing something a section needs, leave a clearly-labeled gap
rather than filling it in. Ask at most one clarifying question only if format or
audience is genuinely unclear; otherwise proceed.
```

---

## Why each part is there

| Part | What it protects against |
|---|---|
| **Core Transformation** | The default failure mode — a "nicely summarized" research doc that's still organized for a researcher, not a designer. |
| **Required Sections** | Ensures the brief answers a designer's real questions: what to draw, what to avoid, what to resolve first, what not to over-commit to. |
| **Status Taxonomy** | Stops everything from reading as equally "ready." Separates validated work from placeholders and blocked decisions. |
| **Evidence-layer toggle** | Keeps the brief designer-clean by default while staying defensible when a stakeholder asks "says who?" |
| **Design Quality Bar** | Prevents generic AI output; makes the asset feel studio-made and worth sharing. |
| **Integrity Rules** | Stops thin or adjacent-segment evidence from being laundered into confident directives, and preserves dissenting voices and source caveats. |

---

## Output

Save as `research/outputs/YYYY-MM-DD_design-activation-brief.html`, then open it for the user to review.

*Next step: share the brief with the design team, then run `research-5-client-readout` for stakeholders.*

*Skill version 1.0 · Stage 4 of 5*
