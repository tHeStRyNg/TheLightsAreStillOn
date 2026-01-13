# The Lights Are Still On

## DESIGN DOCUMENT

This document defines the **core gameplay systems, mechanics, and rules** for *The Lights Are Still On*. It exists to prevent scope creep and to ensure all gameplay decisions align with the narrative and emotional goals of the project.

---

## 1. Core Design Philosophy

* One core tool: **the lantern**
* No traditional combat weapons
* Fear comes from **choice, exposure, and consequence**
* The player is a child: actions must feel vulnerable and grounded
* Systems must be reusable and simple

If a mechanic does not reinforce **light vs truth**, it does not belong in the game.

---

## 2. Player Controls (Baseline)

* Move (left / right)
* Jump
* Interact
* Toggle lantern spectrum

No advanced movement (wall jumps, dashes, combos).

---

## 3. The Lantern System (Core Mechanic)

The lantern is the player’s only tool and primary interaction system.

### 3.1 Light Spectrums

#### Normal Light — *The Lie*

* Warm, stable, comforting
* Shows the town as it wants to be remembered
* Hides ethereal entities and truths
* Safer for navigation

#### Spectral Light — *The Truth*

* Cold, unstable, distorted
* Reveals ethereal realm, demons, and hidden paths
* Allows interaction with bound souls
* Dangerous to use for extended periods

Only one spectrum can be active at a time.

---

## 4. Lantern Instability

The lantern has a **hidden instability value**.

Instability increases when:

* Spectral light is used too long
* Demons are exposed or burned
* The player takes damage
* Story milestones are reached

### 4.1 Effects of Instability

* Lantern flickers
* Spectral mode shuts off briefly
* Visual and audio distortion
* Unintended reveals

Instability never causes instant death.
It creates panic, not unfair punishment.

---

## 5. Enemies & Entities

### 5.1 Design Rule

Enemies are **states**, not complex combat units.

No hit-point bars. No combos. No loot.

---

### 5.2 Enemy Types

#### Watchers

* Passive observers
* Appear only in spectral light
* Increase tension
* Punish overuse of spectral mode

#### Stalkers

* Slow-moving hostile entities
* Kill on contact
* Can be revealed, weakened, or displaced

#### Bound Souls (Family)

* Appear monstrous when revealed
* Tied to anchors (objects or locations)
* Can sometimes be released

---

## 6. Player Damage & Failure

* Demons physically touching the player causes damage
* 2–3 hits result in failure
* No visible health UI

### 6.1 Failure Consequences

* Respawn at last checkpoint
* Increased lantern instability
* Subtle world hostility increase

---

## 7. Confrontations

### 7.1 Optional Encounters

* Player may avoid or retreat
* Consequences persist

### 7.2 Forced Confrontations

Triggered when:

* A story-critical space is entered
* A bound soul must be faced

Forced confrontations:

* Seal exits temporarily
* Escalate music and tension
* Require lantern usage to progress

Outcomes:

* Release
* Bind
* Fail / flee

---

## 8. Difficulty Modes

Difficulty affects **risk**, not content.

### Easy

* Spectral light limited by time
* Lantern instability rises slowly

### Medium

* Spectral light limited by danger
* Enemies react faster

### Nightmare

* Spectral light unlimited
* Lantern fails frequently
* Psychological pressure increased

---

## 9. Audio Design (Gameplay-Relevant)

* Ambient layer (exploration)
* Tension layer (spectral use)
* Confrontation layer (forced encounters)

Music escalates during danger and cuts sharply on lantern failure.

---

## 10. Level Design Rules

* Same space supports both light spectrums
* No separate maps per dimension
* Changes are visibility, collision, and behavior-based

Reuse spaces heavily to control scope.

---

## 11. Player Choice & Consequence

Choices are mechanical, not dialog-based.

The game tracks:

* Spectral light reliance
* Family members freed
* Lantern instability level

These values influence:

* World tone
* Final chapter state
* Ending outcome

---

## 12. Non-Goals (Explicitly Excluded)

* Skill trees
* Inventory management
* Complex AI behaviors
* Boss fights
* Dialogue trees

---

## 13. Design Guardrails

If a feature:

* adds new mechanics
* requires unique systems
* breaks tone consistency

It must be rejected or simplified.

---

## Summary

*The Lights Are Still On* is built around restraint, atmosphere, and risk.

The lantern is power.
The lantern is danger.
And sometimes, the lantern is wrong.

