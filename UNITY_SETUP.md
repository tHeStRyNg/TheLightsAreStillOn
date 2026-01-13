# UNITY_SETUP.md

## Unity Setup — The Lights Are Still On

This document defines the **Unity project setup** required to implement *The Lights Are Still On* cleanly and consistently.

Target: **Unity 2022 LTS or 2023 LTS** (pick one and stay on it).

---

## 1) Project Template & Rendering

### Recommended

* **2D (URP)** project template
* URP Renderer: **2D Renderer**

### Why

* Built-in 2D lights, normal maps, and post-processing
* Easy palette control via Volume profiles

---

## 2) Repository Layout

### Repo (top level)

```text
/TheLightsAreStillOn
├── README.md
├── STORYLINE.md
├── DESIGN.md
├── TRAILER.md
├── MILESTONES.md
├── LEVEL_01.md
└── UNITY/
```

### Unity project (inside /UNITY)

```text
/UNITY
├── Assets/
├── Packages/
└── ProjectSettings/
```

---

## 3) Unity Folder Structure (Assets)

Create this structure immediately:

```text
Assets/
├── _Project/
│   ├── Art/
│   │   ├── Characters/
│   │   ├── Environment/
│   │   ├── Props/
│   │   ├── UI/
│   │   └── VFX/
│   ├── Audio/
│   │   ├── Music/
│   │   ├── SFX/
│   │   └── Mixers/
│   ├── Materials/
│   ├── Prefabs/
│   │   ├── Player/
│   │   ├── Enemies/
│   │   ├── Interactables/
│   │   └── LevelPieces/
│   ├── Scenes/
│   ├── Scripts/
│   │   ├── Core/
│   │   ├── Player/
│   │   ├── Lantern/
│   │   ├── Enemies/
│   │   ├── UI/
│   │   └── Level/
│   ├── Settings/
│   └── Volumes/
└── ThirdParty/
```

Naming convention:

* Prefabs: `PF_`
* ScriptableObjects: `SO_`
* Scenes: `SC_`
* Materials: `MAT_`
* Volume profiles: `VP_`

---

## 4) Project Settings (Must-Set)

### General

* **Frame Rate**: set `Application.targetFrameRate = 60` (or 120 if you prefer)
* **VSync**: off (use targetFrameRate)

### Physics2D

* Default Contact Offset: keep default
* Enable Rigidbody2D interpolation for Player

### Time

* Fixed Timestep: default (0.02) is fine

### Quality

* Use one quality level for early dev
* Avoid feature creep (no extra pipelines)

---

## 5) Input

Recommended: **Unity Input System**

### Actions (minimum)

* Move (Vector2)
* Jump
* Interact
* Toggle Lantern Spectrum

Keep it simple; no complex rebinding system until late.

---

## 6) Sorting Layers & Render Order

Create these Sorting Layers (top to bottom):

1. `UI`
2. `Foreground`
3. `Player`
4. `Enemies`
5. `Props`
6. `Environment`
7. `Background`
8. `Fog`

Rules:

* Player always above environment
* Fog layers can be separate sprites or VFX

---

## 7) Tags & Layers

### Tags

* `Player`
* `Enemy`
* `Interactable`
* `Hazard`
* `Checkpoint`

### Layers (Unity layers)

* `Player`
* `Enemy`
* `Ground`
* `Interactable`
* `SpectralOnly`
* `NormalOnly`
* `Triggers`

### Physics2D Layer Collision Matrix

* Player collides with Ground, Hazard, Enemy
* Enemy collides with Ground and Player
* SpectralOnly objects collide with Player ONLY when spectral mode is active (handled via enabling/disabling colliders)

---

## 8) Scene Plan

Create these scenes immediately:

* `SC_Bootstrap`

  * Loads persistent managers and then loads first gameplay scene
* `SC_Level01_TownEntrance`

  * The Level 01 playable slice

Later:

* `SC_MainMenu`
* `SC_Credits`

### Bootstrap Pattern

* Use a single persistent prefab: `PF_GameManager`
* Mark as `DontDestroyOnLoad`

---

## 9) Persistent Managers (Prefabs)

Create a single root prefab:

### `PF_GameManager`

Contains:

* `GameStateManager`
* `SceneLoader`
* `AudioManager`
* `LanternManager`
* `SaveManager` (stub early)
* `UIManager` (stub early)

Keep all global references here.

---

## 10) The Lantern Implementation (Unity Architecture)

### Key concept

Lantern toggles between **Normal** and **Spectral** modes.

Recommended approach:

* A single `LanternManager` controls:

  * Global **Volume Profile** swap
  * Visibility toggles
  * Collider toggles
  * Instability system

### Visibility rules

Preferred (simple):

* Place objects into groups:

  * `NormalGroup`
  * `SpectralGroup`
* Toggle active state of group roots OR toggle SpriteRenderer/Collider enabled.

Avoid per-object custom logic.

---

## 11) Post-Processing / Volumes (Palette Control)

Create Volume profiles:

* `VP_Normal`
* `VP_Spectral`

### VP_Normal

* Warmer tones
* Softer contrast
* Mild vignette

### VP_Spectral

* Cooler tones
* Higher contrast
* Subtle chromatic aberration
* Light film grain (subtle)

Switching profiles should be **instant** and **readable**.

---

## 12) Lighting

Use 2D Lights:

* Global Light 2D per scene (low intensity)
* Point Lights for lamps/windows

Lighting rules:

* Normal mode: warmer, stable
* Spectral mode: cooler + slightly dimmer + sharper shadows

---

## 13) Audio Mixer Setup (3-Layer Music)

Create an AudioMixer: `MIX_Main`

Groups:

* `Master`

  * `Music`

    * `Ambient`
    * `Tension`
    * `Confrontation`
  * `SFX`
  * `UI`

### Music Control

* Use exposed volume parameters:

  * `MusicAmbientVol`
  * `MusicTensionVol`
  * `MusicConfrontVol`

Trailer/Gameplay behavior:

* Exploration: Ambient up, others down
* Spectral use: Tension fades in
* Forced confrontation: Confrontation fades in dramatically
* Lantern failure: hard cut tension/confrontation briefly (silence is impact)

---

## 14) Save / Checkpoints (Early Stub)

For Level 01 prototype:

* Implement simple checkpoints as Transforms
* On death: respawn at last checkpoint

Later expand to:

* Scene-based save
* Choice tracking (family freed, spectral reliance, instability)

---

## 15) Prefab Standards

### Player Prefab: `PF_Player`

Components:

* Rigidbody2D
* CapsuleCollider2D
* PlayerController
* PlayerHealth (simple)
* Animator

### Enemy Prefabs

* `PF_Watcher` (passive)
* `PF_Stalker` (slow lethal)

### Interactable Prefabs

* `PF_InteractPrompt`
* `PF_ReadableNote`
* `PF_DoorLock`

---

## 16) Coding Standards (Solo-Friendly)

* One responsibility per script
* Prefer ScriptableObjects for data:

  * `SO_DifficultySettings`
  * `SO_LanternSettings`
* Avoid deep inheritance
* Prefer state enums + simple state machines

---

## 17) Definition of Done (Setup)

Setup is complete when:

* `SC_Bootstrap` loads `SC_Level01_TownEntrance`
* Player can move/jump
* Lantern toggles Normal/Spectral
* Spectral objects appear/disappear
* Instability can flicker lantern
* Audio mixer layers can be faded by script

---

## Notes

This setup is intentionally minimal. It supports the core design without adding systems that create long-term maintenance burden.

If a new system is proposed, it must:

* be reusable across chapters
* reinforce lantern risk/choice
* not require complex tooling
