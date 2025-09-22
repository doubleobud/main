# Visual Presentation & World Representation\

* **5.1. The Aesthetic Vision Statement**  
  * **5.1.1.** The "Postcard from the World": A narrative description of the ideal visual experience.  
  * **5.1.2.** Core Inspirations & Anti-Inspirations.  
* **5.2. The Pillars of Visual Design**  
  * **5.2.1.** The Principle of Readability: Ensuring clarity in all visual communication.  
  * **5.2.2.** The Principle of Atmosphere: The approach to light, color, and mood.  
  * **5.2.3.** The Principle of Form Language: The consistent use of shapes and architecture.  
* **5.3. The Philosophy of the User Interface (UI)**  
  * **5.3.1.** The Diegetic vs. Non-Diegetic Approach.  
  * **5.3.2.** The Principles of Information Hierarchy & Accessibility.

## North Stars

* **Clarity first:** direct overhead grid reads instantly (no foreshortening).
* **Character empathy second:** units feel like people, not tokens.
* **Spatial warmth third:** the map looks like a lived-in place, not just a plan.

---

## Camera & Framing

* **Projection:** **direct overhead (orthographic)**, fixed view.
* **Zoom ladder:**

  * **L3 — Macro/Planning:** strong grid, simplified props.
  * **L2 — Tactical (default):** normal play view.
  * **L1 — Intimate:** close-up; cutaways, stronger shadows/emotes.
* **Occlusion / Cutaways:** roofs auto-hide when units are inside; exterior walls fade if they occlude a selected unit; keep ghosted rim outlines so structure remains legible.
* **Subtle parallax cheats:** background drifts slightly slower; light foreground FX (snow/dust) drift slightly faster.

---

## World Representation

* **Ground truth:** **tile/grid world** (2D tilemap).
* **Height:** **discrete floors (z-layers)**; cliffs/ramps are authored features, not continuous terrain math.
* **Mining & caves:** **sparse voxel pockets** attached to specific tiles, allocated only where needed (dig/reveal).
* **Renderer choice is a surface concern:** simulation stays cell-based; later, tiles could be extruded to low-poly geometry without changing game logic.

---

## Characters

* **Form:** **low-poly 3D rigs**, viewed from overhead.
* **Why:** reusable animations, procedural gear swaps, hit reactions/ragdolls; remains readable at gameplay scale.
* **Empathy stack:** bold silhouettes, idle/micro-animations, overhead emote glyphs; portraits/busts in UI for “face time.”

---

## Objects & Props

* **Hybrid approach:**

  * **Sprites/billboards** for “soft clutter” (plants, rubble, small deco).
  * **Low-poly 3D meshes** for gameplay-critical objects (doors, turrets, generators, vehicles, large walls/shells).
* **Rationale:** cheap procedural stamping for clutter; satisfying destruction/animation where it matters.

---

## Art Direction (Option A)

* **Tiles:** **hand-painted textures** (illustrative, not photo), repeated/blended across the grid.
* **3D (characters/critical props):** **flat-shaded/stylized** materials.
* **Overall vibe:** **“toy diorama on a painted map.”**
* **Lighting & depth cues (overhead-friendly):** contact shadows + soft AO halos at ground contact; thin rim/edge highlights; subtle height tint bands; no heavy post that harms grid readability.

---

## Destructibility & Mining

* **State ladder:** **intact → cracked → breached → rubble** (silhouette changes, not just textures).
* **Tiles:** simple **sprite/tile swaps**.
* **3D props:** **mesh swaps or procedural breakup**; short destruction burst (≈0.25–0.4s) with dust/impact FX; leave readable rubble that affects pathing/cover.
* **Voxel pockets:** mining reveals a small pocket under targeted tiles (edge highlight + dust FX).
* **Tactical clarity:** after changes, briefly flash updated **LoS / cover / movement cost**.

---

## Readability & UI

* **Overlays on demand:** grid, line-of-sight cones/lines, AoE footprints; selection/hover shows cover and tile info.
* **In-world icon budget:** max \~3 status icons above units; overflow to portrait pane.
* **Occlusion control:** auto-fades as above; provide a temporary “peek” to hide occluders under cursor when needed.

---

## Concrete Parameters (for authoring & tuning)

* **Tile size (authoring):** **1.0 m** per tile.
* **On-screen density (L2):** \~**20×12 tiles** in 16:9.

  * **L3:** \~40×24 tiles; **L1:** \~10×6 tiles (targets).
* **Pawn footprint:** humans 1×1 tile; larger units 2×2 or 3×3.
* **Texel density (tiles):** \~**256 px per tile** (downsample at distance).
* **Simulation timebase:** fixed **Δt = 0.05 s** (deterministic); turn systems consume multiple ticks per turn.
* **Seeding:** `{world_seed} → {domain_seed} → {system_seed}` (stable derivation).

---

## Scope Notes (kept explicit)

* **World stays tile-based**; verticality is via discrete floors and authored features.
* **3D is applied selectively** (characters, important props) to add life and destruction without full 3D terrain.
* **Procedural friendliness** is preserved (auto-tiling, blends, decals; sparse voxels only where used).

---

## Validation Slices (for implementation alignment)

* **Three-Floor Safehouse:** stairs, roof cutaways, interior light pools; breach a wall → dust + rubble; LoS/cover flash update.
* **Cliff Mine Entrance:** exterior height cues; dig a **2×2** voxel pocket under a tile (dust/echo; torchlight in pocket).

*(These slices prove clarity at L2 and warmth at L1 with the chosen pipeline.)*
