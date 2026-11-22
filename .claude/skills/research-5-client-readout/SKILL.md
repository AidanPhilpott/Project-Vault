---
name: research-5-client-readout
description: >
  Stage 5 of the research synthesis pipeline. Build a polished, client-facing HTML research
  readout from a completed Stage 3 Higher-Order Synthesis: insight cards with participant
  quotes, jobs to be done, design principles and decision framing. Use when the user asks for
  a "research readout", "findings readout", "insight cards", "run stage 5", or provides a
  Stage 3 synthesis and wants to present it to stakeholders. Not for status updates or
  general client deliverables (use `pos-weekly-summary` for updates).
---

# Stage 5 — Client-Facing Readout
**Version 1.0 · Claude skill file**

> **How to use:** Provide the completed Stage 3 Higher-Order Synthesis document (and Stage 4 Design Activation Brief if available). Claude will build a polished single-file HTML readout following the structure and visual system below. Work section by section — align on structure first, then populate content, then refine iteratively.
>
> **Input:** Completed Stage 3 Higher-Order Synthesis document (Stage 4 brief optional but useful)
> **Output:** A single self-contained HTML file — a client-facing research readout with sticky navigation, expandable insight cards, collapsible JTBD themes, and design principles

---

## Document Structure

The standard document flow is:

1. **Overview** — project context, research stats, user profile, how-to-read block
2. **Findings** — insight cards (collapsed by default, expandable to reveal participant quotes)
3. **Jobs To Be Done** — themes with collapsible job lists
4. **Design Principles** — 3 principles derived from the research
5. **Decision & Next Steps** — decision framing criteria

This order can be modified, but each section should earn its place before the next. Concepts or design explorations are optional and sit between Principles and Decision if included.

---

## Visual Design System

Always apply these tokens — never hardcode colours:

```css
--paper: #f1ece1          /* page background */
--paper-2: #e9e2d3        /* card backgrounds */
--ink: #1c1a14            /* primary text */
--ink-soft: #4a463a       /* secondary text */
--ink-faint: #7d7868      /* labels, metadata */
--line: #cfc7b4           /* borders */
--accent: #c0381c         /* red — primary accent */
--build: #1f5f54          /* teal — affirmative */
--placeholder: #a86a1a    /* amber — cautionary */
```

**Typography:**
- Headlines: `Fraunces` (serif, italic for numbers and emphasis)
- Body: `Hanken Grotesk` (sans-serif)
- Labels / monospace: `JetBrains Mono`

**Layout:**
- Sticky topbar: project mark left, document label right
- Sticky left side nav with scrollspy (highlights active section)
- Main content column with generous padding

---

## Section-by-Section Build Guide

### Topbar
```
[Client × Partner] / [Project Name]     [Document Type Label]
```

### Overview
- Eyebrow: document type + version + date
- H1: editorial headline (e.g. "What we heard. What we *explored.*")
- Lede: one paragraph — sample size, method, what this doc is and isn't
- Stat strip: N interviews, firm split, workshops, insights
- **User profile block**: left-border accent card. "Who this research is about." 2 short paragraphs.
- **How-to-read block**: 3-cell grid — "What this is", "What this isn't", "How to read it"

### Findings
- Section eyebrow: `Section 02`
- 4–7 insight cards, collapsed by default
- Each card contains:
  - Italic number (large, accent colour)
  - Short label (monospace, e.g. `Insight — The view nobody else has`)
  - **Headline**: the insight itself — written as a human truth, not a finding
  - **So what**: design or strategic implication. One short paragraph.
  - `▶ View participant quotes` text link (expands a quote drawer)
- Quote drawer: verbatim quotes with full attribution (Name, Role · Firm)

**Insight writing principles:**
- Findings are the what (observable patterns). Insights are the why and so what.
- Insights should provoke a response — not just describe, but reframe.
- Headlines should be editorial, not clinical. Use plain language over jargon.
- The so what should name a design implication, not list solution features.

### Jobs To Be Done
- Section eyebrow: `Section 03`
- 5 theme cards, collapsed by default
- Each theme: icon, theme number + job count, theme name, one-line summary, job count pill
- Expanded: individual job rows with job number, job title, outcome statement
- Job number format: `J1–J15` for standard jobs; `E1` for edge/single-source jobs

### Design Principles
- Section eyebrow: `Section 04`
- 3 principles (fewer is better — only include what is genuinely derived from the research)
- Each principle: large italic number, bold headline, one explanatory sentence
- Principles should form a coherent set — test whether they read as a sequence

**Good principle format:**
> **Simple by default, deep on demand**
> The default view should be clean, oriented, and immediately legible. Depth is always one step away — but it never leads.

### Decision & Next Steps
- Section eyebrow: `Section 05`
- Short intro paragraph
- Decision framing block: header + 4 lettered criteria (A–D)
- Each criterion: bold question as the label, 1–2 sentences of expansion
- Criteria should trace back to specific insights — make the connection explicit

---

## Feature-Level Signals Block

If recurring but non-insight-level signals emerged from research, include an "Also noted consistently" block at the bottom of the Findings section. Compact numbered list — not cards — with a title and one-sentence description per item. Visually subordinate to the insight cards above it.

---

## Working Process

### 1. Structure first
Before writing any content, align on which sections to include and whether concepts are included. Build the HTML shell with placeholder content before populating.

### 2. Populate from source
Read the Stage 3 synthesis before writing. Priority order:
1. Stage 3 Higher-Order Synthesis (insight statements, opportunities, tensions)
2. Stage 2 CISD (theme frequency, representative quotes)
3. Stage 1 Individual Interview Analyses (verbatim quotes, specific details)

### 3. Refine insights collaboratively
Work through each insight one at a time. For each:
- Pressure-test whether it reads as an insight or a finding
- Offer 3–4 headline options before writing
- Confirm label, headline, and so-what separately

### 4. Quote curation principles
- Always prefer verbatim quotes over paraphrased synthesis
- Include full attribution: Name, Role · Firm
- Each insight should have 3–7 quotes covering multiple firms
- The strongest quote in the set should lead

### 5. Iterative HTML editing
- Make targeted edits — never rewrite the whole file
- After each significant change, open or present the file so the user can review
- Keep CSS variables consistent — never hardcode colours
- Scrollspy navigation must cover all `section[id]` elements

---

## HTML Technical Patterns

### Expandable insight cards
```javascript
function toggleInsight(id) {
  document.getElementById(id).classList.toggle('open');
}
```

### Scrollspy
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      navItems.forEach(item => item.classList.remove('active'));
      const active = document.querySelector(`.nav-item[href="#${entry.target.id}"]`);
      if (active) active.classList.add('active');
    }
  });
}, { rootMargin: '-20% 0px -70% 0px' });
sections.forEach(s => observer.observe(s));
```

### Collapsible theme cards (Jobs section)
```javascript
function toggleTheme(id) {
  document.getElementById(id).classList.toggle('open');
}
```

---

## Common Pitfalls to Avoid

- **Don't conflate findings and insights.** If the headline describes what happened, it's a finding. If it names why it matters and what to do about it, it's an insight.
- **Don't list solution features in the so-what.** The so-what is a design implication, not a feature spec.
- **Don't use "verdict"** — prefer: signal, answer, direction, clarity, the call.
- **Don't front-load all quote drawers open** — collapsed by default keeps the page scannable.
- **Don't populate the stat strip with placeholder [N] values** — fill them from the Stage 2 CISD.

---

## Output

A single self-contained HTML file. All CSS and JS inline. No external dependencies except Google Fonts (CDN). Save to `research/outputs/` in this project and open it for the user to review.

File naming convention: `[Client]-[Project]-Readout.html`

---

*This is the final stage of the research workflow. The completed readout is the primary stakeholder-facing deliverable. Stage 4 (Design Activation Brief) is the parallel designer-facing deliverable.*

*Skill version 1.0 · Stage 5 of 5*
