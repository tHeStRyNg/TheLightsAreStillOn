# LEVEL_01_UNITY_TASKS.md

## Level 01 — Unity Task Checklist

This checklist translates `LEVEL_01.md` into concrete Unity implementation tasks. Follow it in order. Do not add new mechanics.

**Target:** a playable 15–20 minute vertical slice.

---

## 0) Prerequisites

* `UNITY_SETUP.md` completed
* Scenes created:

  * `SC_Bootstrap`
  * `SC_Level01_TownEntrance`
* Persistent prefab exists: `PF_GameManager`
* Player prefab exists: `PF_Player`
* Lantern system stub exists (Normal/Spectral toggle)

---

## 1) Scene Blockout (Fast Greybox)

**Goal:** Build the full level flow before polishing.

### Tasks

* [ ] In `SC_Level01_TownEntrance`, create empty GameObjects as section roots:

  * [ ] `S01_TownEntrance`
  * [ ] `S02_MainStreet`
  * [ ] `S03_GrandfatherExterior`
  * [ ] `S04_HouseInterior`
  * [ ] `S05_LanternTutorial`
  * [ ] `S06_SkyIsWrong`
  * [ ] `S07_FirstWatchers`
  * [ ] `S08_InstabilityIntro`
  * [ ] `S09_ConfrontSetup`
  * [ ] `S10_FirstConfrontation`
  * [ ] `S11_ResolutionExit`

* [ ] Greybox platforms using Tilemap or simple sprites

* [ ] Add colliders to ground/platforms

* [ ] Add camera bounds volumes per section (simple box collider triggers)

### Done when

* [ ] You can run from start to confrontation room without getting stuck

---

## 2) Section 1 — Town Entrance (Mood + Movement)

### Tasks

* [ ] Place Player start point
* [ ] Add “1:00 PM” clock prop (visual only)
* [ ] Add Global Light 2D + a few Point Lights (streetlights)
* [ ] Add fog overlay sprite layer (simple scrolling or static)
* [ ] Add ambient audio loop (wind + faint hum)

### Optional

* [ ] Add small interact prompt: “The air feels late.”

### Done when

* [ ] Player movement feels stable in this space

---

## 3) Section 2 — Main Street (Town Is Empty + Locked)

### Tasks

* [ ] Add 2–3 locked doors with interact prompt:

  * [ ] “Locked.”
  * [ ] “No answer.”
* [ ] Create Exit Attempt trigger (end of street):

  * [ ] Trigger fades screen slightly
  * [ ] Teleport player back to town center marker
  * [ ] Play subtle audio cue (low hum)

### Done when

* [ ] Player understands: cannot leave

---

## 4) Section 3 — Grandfather’s House Exterior

### Tasks

* [ ] Place house facade
* [ ] Warm interior window glow (2D light)
* [ ] Interactable door to enter
* [ ] Add small text beat: “Grandfather?”

### Done when

* [ ] Player is guided inside naturally

---

## 5) Section 4 — House Interior (Lantern Pickup)

### Tasks

* [ ] Interior Tilemap/sprites (simple)
* [ ] Place:

  * [ ] Lantern on table (interactable)
  * [ ] Portrait (normal)
  * [ ] Note (readable)

### Implement: Readable Note System

* [ ] Create `PF_ReadableNote` prefab:

  * [ ] Trigger/Interact to open text panel
  * [ ] Close button / confirm input

### Note Text (Grandfather)

* [ ] Add the note text to this specific note instance:

  * [ ] “If you are reading this, it means I failed.”
  * [ ] “The light shows what we hid.”
  * [ ] “Do not stare too long.”
  * [ ] “If the lantern flickers—run.”

### Done when

* [ ] Lantern can be picked up
* [ ] Note can be read and closed

---

## 6) Section 5 — Lantern Tutorial (Safe Testing)

### Tasks

* [ ] Implement Lantern toggle input
* [ ] Create two Volume Profiles:

  * [ ] `VP_Normal`
  * [ ] `VP_Spectral`
* [ ] Add `Volume` component to scene
* [ ] On toggle:

  * [ ] Swap Volume profile
  * [ ] Toggle `NormalGroup` and `SpectralGroup`
  * [ ] Play toggle SFX

### Create tutorial props

* [ ] One object visible only in spectral mode (e.g., hidden symbol on wall)
* [ ] One object visible only in normal mode (optional)

### Done when

* [ ] Player can see clear difference between modes

---

## 7) Section 6 — Sky Is Wrong (Time Anomaly)

### Tasks

* [ ] Create outdoor set piece:

  * [ ] Visible frozen sun/moon near horizon
  * [ ] Long shadow shapes
* [ ] Add a clock/watch prop that still reads ~1:00 PM
* [ ] Add short optional text line:

  * [ ] “It’s one in the afternoon.”
  * [ ] “Why is it dark?”

### Done when

* [ ] Vibe is unmistakable

---

## 8) Section 7 — First Watchers (Optional Fear)

### Tasks

* [ ] Create `PF_Watcher` prefab:

  * [ ] Sprite + subtle idle
  * [ ] Only visible in spectral mode (put in `SpectralGroup`)
  * [ ] No collider damage

* [ ] Place 3–6 Watchers in alley scene

* [ ] Add audio sting when first watcher becomes visible

### Done when

* [ ] Player experiences first reveal without dying

---

## 9) Section 8 — Instability Intro

### Tasks

* [ ] Implement `LanternInstability`:

  * [ ] Hidden float value
  * [ ] Increases while spectral is active
  * [ ] Decreases slowly in normal

* [ ] Add flicker thresholds:

  * [ ] Mild flicker
  * [ ] Heavy flicker
  * [ ] Forced spectral shutdown (brief)

* [ ] Add audio distortion hook:

  * [ ] Low-pass filter or mixer snapshot when instability spikes

### Done when

* [ ] Lantern feels risky but fair

---

## 10) Section 9 — Confrontation Setup (Lockdown)

### Tasks

* [ ] Create a small interior room/space with a single entrance
* [ ] Add trigger: on enter

  * [ ] Lock doors (enable blockers)
  * [ ] Start Confrontation music layer
  * [ ] Disable exit

### Done when

* [ ] Player understands they must face something

---

## 11) Section 10 — First Forced Confrontation (Stalker)

### Enemy Prefab: `PF_Stalker`

**Behavior requirements:**

* [ ] Invisible by default (normal mode)
* [ ] Visible in spectral mode
* [ ] Moves toward player slowly when revealed
* [ ] Contact damages player
* [ ] Can be weakened/stunned by sustained spectral exposure

### Tasks

* [ ] Implement `StalkerStateMachine`:

  * [ ] Dormant
  * [ ] Revealed
  * [ ] Approaching
  * [ ] Stunned
  * [ ] Bound/Retreated

* [ ] Implement “Burn” mechanic:

  * [ ] If spectral light aimed at Stalker for X seconds → stun
  * [ ] Increase instability faster while burning

* [ ] Add player damage system:

  * [ ] 2–3 hits = death
  * [ ] Respawn at last checkpoint

### Encounter scripting

* [ ] Place an anchor object (e.g., cracked painting or sealed door)
* [ ] Define encounter resolution:

  * [ ] Option A: Bind (stalker retreats after 2 stuns)
  * [ ] Option B: Survive for N seconds → doors unlock
  * [ ] Option C: Death → respawn outside room

### Done when

* [ ] Encounter is survivable
* [ ] Player learns: reveal → pressure → manage lantern → escape

---

## 12) Section 11 — Resolution & Exit

### Tasks

* [ ] Unlock doors on resolution
* [ ] Stop confrontation music
* [ ] Play silence or low ambient
* [ ] Add a short text line:

  * [ ] “It touched you.”
  * [ ] “It felt cold.”

### Done when

* [ ] Player exits confrontation room and continues

---

## 13) Checkpoints & Flow

### Tasks

* [ ] Place checkpoints:

  * [ ] Start of level
  * [ ] Before confrontation room
  * [ ] After confrontation room (optional)

* [ ] Ensure death reload is instant and stable

### Done when

* [ ] No softlocks, no long reloads

---

## 14) Vertical Slice Capture Checklist (for Trailer)

Capture these moments once stable:

* [ ] Letter close-up (UI or prop)
* [ ] 1:00 PM clock with night sky
* [ ] Wide town shot (all lights on)
* [ ] Lantern pickup
* [ ] Spectral toggle reveal (watchers)
* [ ] Lantern flicker moment
* [ ] Forced confrontation lock-in
* [ ] Stalker reveal + approach
* [ ] Bind/escape resolution
* [ ] Title card

---

## Scope Guardrails

Do NOT add:

* New enemy types
* New traversal abilities
* Inventory
* Upgrade systems
* Branching paths

Level 01 exists to prove the core loop.
