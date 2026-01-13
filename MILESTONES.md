# MILESTONES.md

## The Lights Are Still On — Development Milestones

This document defines a **realistic, solo-developer roadmap** for building *The Lights Are Still On*. Milestones are ordered to minimize risk, avoid scope creep, and ensure a playable vertical slice early.

> Guiding rule: **Ship something playable early. Polish later.**

---

## Phase 0 — Project Setup (2–3 Weeks)

**Goal:** Establish a stable foundation before content.

### Deliverables

* Unity project created (2D, URP)
* GitHub repository initialized
* Folder structure aligned with repo plan
* Basic scene loading pipeline
* Version control workflow verified

### Exit Criteria

* Project opens cleanly
* Builds run without errors
* Repo structure matches documentation

---

## Phase 1 — Core Player & Camera (3–4 Weeks)

**Goal:** Make the game *feel good* to control.

### Deliverables

* Player movement (walk, jump)
* Camera follow with soft damping
* Basic collision and slopes
* Death / respawn placeholder

### Exit Criteria

* Player movement feels responsive
* Camera never causes motion discomfort

---

## Phase 2 — Lantern Core System (4–5 Weeks)

**Goal:** Implement the game’s central mechanic early.

### Deliverables

* Lantern object and visuals
* Toggle between Normal and Spectral light
* Global color grading swap
* Spectral-only object visibility
* Basic lantern UI feedback (flicker, sound)

### Exit Criteria

* Lantern switching is instant and readable
* Spectral mode clearly changes the world

---

## Phase 3 — Instability & Risk (3–4 Weeks)

**Goal:** Add tension without adding complexity.

### Deliverables

* Hidden instability value
* Flicker effects tied to instability
* Temporary spectral shutdown
* Audio distortion hooks

### Exit Criteria

* Lantern feels powerful but unreliable
* Instability never feels random or unfair

---

## Phase 4 — Enemy Prototype (3–4 Weeks)

**Goal:** Prove encounters are fun and scary.

### Deliverables

* Watcher entity (passive)
* Stalker entity (slow, lethal)
* Contact damage and failure
* Enemy reveal / weaken behavior

### Exit Criteria

* Encounters readable without UI
* Player understands danger quickly

---

## Phase 5 — Forced Confrontation System (3 Weeks)

**Goal:** Lock the core horror loop.

### Deliverables

* Area lockdown triggers
* Music escalation logic
* Confrontation states (reveal → pressure → resolve)
* Release / bind / fail outcomes

### Exit Criteria

* One full forced confrontation playable
* No softlocks or unclear outcomes

---

## Phase 6 — Vertical Slice (6–8 Weeks)

**Goal:** Build the first 15–20 minutes of the game.

### Deliverables

* Town entrance
* Grandfather’s house
* Lantern discovery
* Watchers introduction
* First forced confrontation

### Exit Criteria

* Playable start-to-finish slice
* Capturable trailer footage
* Steam page ready

---

## Phase 7 — Audio & Visual Identity (4–6 Weeks)

**Goal:** Lock mood and presentation.

### Deliverables

* Music layers integrated
* Ambient sound design pass
* Lighting and fog polish
* Shader tuning

### Exit Criteria

* Game has strong identity without content expansion

---

## Phase 8 — Content Expansion (6–12 Months)

**Goal:** Build remaining chapters using locked systems.

### Deliverables

* Bound soul encounters
* Town variations
* Lantern instability escalation
* Father confrontation

### Exit Criteria

* All chapters playable
* No new core mechanics added

---

## Phase 9 — Polish & Stability (3–4 Months)

**Goal:** Make the game shippable.

### Deliverables

* Bug fixing
* Performance optimization
* Difficulty tuning
* Save/load system

### Exit Criteria

* No game-breaking bugs
* Consistent performance

---

## Phase 10 — Demo & Release Prep (2–3 Months)

**Goal:** Prepare for public release.

### Deliverables

* Public demo build
* Trailer finalized
* Steam page assets
* QA feedback applied

### Exit Criteria

* Demo approved
* Release pipeline ready

---

## Scope Guardrails

* No new mechanics after Phase 5
* Reuse enemies and systems
* Content scales horizontally, not vertically

---

## Summary

This roadmap prioritizes:

* Early playability
* System reuse
* Emotional consistency
* Solo-dev sustainability

If a task does not support a milestone, it should be deferred or cut.
