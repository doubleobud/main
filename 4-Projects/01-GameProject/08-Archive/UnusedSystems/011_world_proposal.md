# World Presentation — Proposal

## Overview

Deliver a **direct overhead, tile-based world** that preserves **tactical clarity**, supports **selective destructibility and mining**, and feels **inviting and lived-in**—without committing to a full 3D/voxel terrain. The simulation remains **cell-based**; presentation layers (tiles, sprites, meshes) render on top.

---

## Objectives

* **Clarity first:** grid, ranges, LoS parse instantly.
* **Character empathy:** units feel like people, not tokens.
* **Spatial warmth:** the map reads as a place, not just a plan.
* **Procedural friendliness:** tiles/sprites drive variety; 3D only where it pays off.
* **Determinism:** fixed Δt and stable seeds.

**Non-Goals**

* No free 3D RTS camera.
* No fully voxelized terrain.
* No continuous terrain slopes; height is discrete floors.

---

## Player-Facing Outcomes

* A **top-down tactical view** with strong readability at the default zoom.
* **Cutaways** that reveal interiors when needed (roofs auto-hide, exterior walls fade).
* **Destruction** that’s readable (intact → cracked → breached → rubble).
* **Mining** that reveals **small voxel pockets** only where the player digs.
* Characters that feel **alive** via silhouettes, micro-idles, emotes, and portraits.

---

## Approach (What We’re Building)

### Camera & Framing

* **Projection:** direct overhead **orthographic**, fixed view.
* **Zoom ladder:**

  * **L3** Macro/Planning (strong grid, simplified props)
  * **L2** Tactical (default)
  * **L1** Intimate (cutaways, stronger shadows/emotes)
* **Cutaways/Occlusion:** roofs auto-hide when units are inside; exterior walls fade if they occlude a selected unit; **ghosted rim outlines** keep structure legible.
* **Subtle parallax cheats:** background drifts slightly slower; light foreground FX (snow/dust) slightly faster.

### World Substrate

* **Ground truth:** **tile/grid world** (2D tilemap).
* **Height:** **discrete floors (z-layers)**; cliffs/ramps are authored features.
* **Mining & caves:** **sparse voxel pockets** attached to specific tiles, allocated only where used.
* **Renderer-agnostic sim:** the cell model does not depend on rendering; tiles could be extruded later without changing logic.

### Characters

* **Form:** **low-poly 3D rigs** viewed overhead.
* **Why:** reusable animations, procedural gear swaps, hit reactions/ragdolls; readable at gameplay scale.
* **Empathy stack:** silhouettes, micro-idles, overhead emotes; portraits/busts in UI.

### Objects & Props

* **Hybrid:**

  * **Sprites/billboards** for soft clutter (plants, rubble, small deco).
  * **Low-poly 3D meshes** for gameplay-critical items (doors, turrets, generators, vehicles, large walls/shells).
* **Rationale:** cheap procedural stamping for clutter; satisfying destruction/animation where it matters.

### Destructibility & Mining

* **State ladder:** **intact → cracked → breached → rubble** (silhouette changes, not just textures).
* **Tiles:** tile/sprite swaps.
* **3D props:** mesh swaps or procedural breakup; short destruction burst with dust/impact FX; leave readable rubble that affects pathing/cover.
* **Voxel pockets:** mining reveals a pocket under targeted tiles (edge highlight + dust FX).
* **Clarity update:** brief flash of **LoS / cover / movement cost** after any change.

### Readability & UI

* **On-demand overlays:** grid, LoS cones/lines, AoE footprints.
* **Icon budget:** max \~3 status icons above units; overflow to portrait pane.
* **Peek:** temporary hide of occluders under cursor when needed.

### Art Direction Alignment (Presentation Only)

* **Tiles:** **hand-painted textures** (illustrative).
* **3D (characters/critical props):** **flat-shaded/stylized** materials.
* **Depth cues for overhead:** contact shadows + soft AO halos at ground contact; thin rim/edge highlights; subtle height tint bands.

---

## Concrete Parameters (Authoring Targets)

* **Tile size (authoring):** **1.0 m** per tile.
* **On-screen density (L2, 16:9):** \~**20×12 tiles**.

  * **L3:** \~40×24 tiles; **L1:** \~10×6 tiles.
* **Pawn footprint:** humans 1×1 tile; larger units 2×2 or 3×3.
* **Texel density (tiles):** \~**256 px per tile** (downsample at distance).
* **Timebase:** fixed **Δt = 0.05 s** (deterministic).
* **Seeding:** `{world_seed} → {domain_seed} → {system_seed}` (stable derivation).

---

## Deliverables & Milestones

**M1 — Foundations**

* Tile atlas starter (grass, dirt, stone, interior wood/tile, wall, door, rubble).
* Pawn base rig (low-poly) with **idle, walk, interact, take-hit, downed**.
* Roof/wall **cutaway** + contact shadows/AO halos.

**M2 — Objects & Destruction**

* Object taxonomy implemented (sprite vs mesh) with placement + selection/hover.
* **Destruction ladder** (tiles + 3D props) with dust/impact FX and pathing updates.

**M3 — Mining & Pockets**

* Dig orders reveal **voxel pockets** under tiles (edge highlight + dust/echo SFX).
* Post-change **LoS/cover/move-cost flash**.

**M4 — Validation Slices**

* **Three-Floor Safehouse:** stairs, interiors with cutaways; breach a wall → rubble + LoS/cover flash.
* **Cliff Mine Entrance:** exterior height cues; dig a **2×2** pocket with torchlight inside.

---

## Acceptance Criteria (Definition of Done)

* **Clarity:** at L2, players can read grid, LoS, cover, and movement costs at a glance.
* **Cutaways:** roofs/walls never block critical info; rim outlines preserve structure.
* **Destruction:** state changes are visually distinct; rubble modifies navigation/cover correctly.
* **Mining:** pockets appear only where ordered; visuals communicate depth; no perf spikes.
* **Empathy:** pawns readable at gameplay scale; emotes/portraits convey state.
* **Determinism:** identical seeds/inputs/Δt produce identical results.

---

## Risks & Mitigations

* **Flatness:** reinforce contact shadows/AO halos and rim highlights.
* **Clutter soup:** cap prop density; prefer clusters + clear lanes.
* **Occlusion frustration:** be aggressive with auto-fade; provide “peek.”
* **Icon overload:** limit in-world icons; overflow to portraits.
* **Animation noise:** keep cycles readable; avoid jittery micro-motion.

---

## Open Questions (to resolve during slices)

* Practical **floor count** (hard cap for UI/cutaways).
* Whether ramps/cliffs-as-features suffice initially.
* Any need for slight tilt later (remain orthographic by default).
* Minimum animation bank beyond the five base clips.

---

## Dependencies

* **Spatial & Timebase** (units, frames, fixed Δt, seeds).
* **Art Direction Pillars** (palette, material style, icon grammar).
* **Characters & Presentation** (silhouette rules, emote/portrait UI).
* **Objects & Destruction** (state ladder, FX hooks, persistence notes).

---

## Scope Notes

* World stays **tile-based** with **discrete floors**; cliffs/ramps are authored features.
* **3D applied selectively** (characters, important props).
* **Procedural pipeline** centered on tiles/sprites; voxel pockets are **sparse** and on-demand.
