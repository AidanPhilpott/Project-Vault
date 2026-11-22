# Design

> Optional module. Setup keeps it only if design was chosen.

Working space for design exploration, prototypes, and review records.

---

## Intended structure

```
design/
├── README.md                          ← you are here
├── concepts/                          ← early directions, sketches, exploration docs
├── prototypes/                        ← prototype files, links, iteration notes
├── reviews/                           ← critique notes, feedback logs, sign-off records
└── assets/                            ← icons, images, brand material
```

Create subfolders as you need them, not upfront.

---

## Naming

`YYYY-MM-DD_short-description_vN.ext` — e.g. `2026-03-14_onboarding-flow_v2.html`

---

## What lives here vs. in the design tool

This folder is **not** a replacement for Figma, Miro, or whatever the project actually designs in. Those tools hold the working files. This folder holds:

- **The record of what was decided and why** — review notes, critique outcomes, sign-offs
- **Self-contained prototypes** that need to run standalone (HTML, code sketches)
- **Links into the design tool**, with enough context that a link rot event doesn't erase what the file contained

The test: if someone loses access to the design tool, what in here still tells them what happened? That's what belongs here.

---

## Review notes

One file per review session, same convention as meetings. Record what was shown, what changed as a result, and what was explicitly rejected — **rejections are the most valuable and least recorded part of a design review.** "We considered X and decided against it because Y" saves the next person from proposing X again in three months.

---

## A prototyping heuristic worth keeping

**Prototype only what earns its keep; narrate the rest.**

When building a prototype for a walkthrough or demo, the instinct is to make everything interactive. It's rarely worth it. One worked example of an interaction pattern establishes it conversationally — building it across every instance is effort spent on something the audience will see once.

The corollary: be deliberate about which rough edges you show. The line isn't finished vs. unfinished, it's whether the gap undermines the story being told. An obviously-placeholder chart is fine; a visible error state in the middle of a client demo is not.
