# Planet Builder (Pre-Life) — Full Proposal

## 1) Executive Summary

**Planet Builder** is a deterministic, map-driven simulation game where you craft an Earth-like planet from the birth of the Solar System up to (but not past) the moment the world first becomes plausibly habitable for life (“**Life Spark**”). You play as a near-future **Surveyor** operating a legal world simulator. You set **big geologic dials**, run short simulations (“Eras”), **compare multiple outcomes side-by-side**, and **promote one** to become **Canon** before advancing time. The presentation is **overhead/atlas-first** with a matching **space-view sphere**; visuals are generated directly from simulation data—no heavy art pipeline.

---

## 2) Vision & Tenets

* **Simulation First, Data-Driven:** Physics-inspired rules and parameters generate the world. Content is data.
* **Deterministic & Inspectable:** Same seed + same events → same world; event log, snapshots, and time-branching.
* **Small Core, Infinite Edges:** Tiny stable kernel; everything else is module/plugins added over years.
* **Player = Boundary Conditions:** You don’t paint mountains; you nudge deep processes (impacts, greenhouse, tectonics).
* **One Renderer, Two Feels:** Space sphere when far; atlas map when near—same data, different overlays.
* **Forward-Only Canon:** You can branch to compare results, but once you choose Canon for an Era, time advances from it.
* **Pre-Life Scope:** This phase stops at **Life Spark**; biosphere systems come later as a separate module.

---

## 3) Player Fantasy

You’re a **Surveyor** in a near-future setting who designs and oversees a world simulation from the comfort of orbit: you plan an Era (set a few dials), run the model, react to one or two event prompts, compare outcomes, and lock in a planetary path. You’re methodical, not omnipotent.

---

## 4) Game Loop (per Era)

1. **Plan:** Spend a small pool of **Intervention Points (IP)** to set Era dials (e.g., impact style, water budget, CO₂ baseline, rotation/day length, tectonics on/off timing). Optionally place a **hotspot** or **microplate**.
2. **Run:** Advance the sim quickly (minutes → millions of years) to generate **2–4 Outcomes** (what-ifs).
3. **React:** Optional **Event Cards** appear, offering 1–2 constrained choices (e.g., flood basalt pulse, polar wander).
4. **Compare & Commit:** See map thumbnails, stats, and diff tools. **Promote** one Outcome to **Canon**.
5. **Advance:** Move to the next Era with newly unlocked dials.

**Resources:**

* **IP (Intervention Points):** Tune big dials.
* **Credibility Meter:** Soft realism guardrail; extreme combos are allowed but costly/uncertain.
* **Focus Tokens (optional):** Mark 1–3 regions for higher-detail rivers/coasts this Era.

---

## 5) Scope Boundaries (Pre-Life Only)

### In-Scope

* Protoplanetary disk → accretion → **Giant Impact** (Moon formation).
* **Magma ocean**, core formation, geodynamo onset, early atmosphere outgassing.
* Cooling/condensation → **oceans**; early greenhouse (N₂/CO₂/H₂O/CH₄).
* **Tectonics switch** (onset timing), ridges/trenches/arcs, craton growth.
* **Climate bands**, orographic rain, storminess, **rivers** & basic erosion/sedimentation.
* Sea level & shelves, large igneous provinces, bombardment tail.

### Out-of-Scope (deferred)

* Oxygenation feedbacks (GOE/NOE), Snowball Earths, full supercontinent cycles past early Archean.
* Nutrient cycles, biomes, any life/biology, human/anthro effects.

---

## 6) Stop Condition — **Life Spark**

Simulation halts and produces a handoff dossier when all thresholds are met (tunable):

* **Stable liquid oceans** for ≥ *X* Myr (e.g., 50–100 Myr).
* **Global mean temperature** within *Y–Z* °C (e.g., 0–60 °C) with moderate variance.
* Persistent **shallow shelf area** ≥ *A%* of ocean.
* Sustained **hydrothermal flux** ≥ *B* (energy gradients).
* Active **magnetosphere** ≥ *C* (geodynamo on).
* Atmosphere composition: **N₂/CO₂/H₂O**, trace **CH₄**, **very low O₂**.

When triggered, you **Promote Canon** (if not already) and archive **Life Spark Pack** (maps + JSON stats). Simulation for this module ends.

---

## 7) Eras & First Choices

### Opening (Space View)

* **Starfield + Disk:** Dust/gas ring; seeded clumps.
* **Accretion:** Planetesimals converge; proto-planet grows; camera orbits/zooms.
* **Magma Ocean:** Glowing sphere; cutaway shows core/mantle fraction.

### **Tuning #1: Giant Impact (“The Big Impact”)**

**Presets:**

* **Balanced Graze** — classic Moon, moderate tilt/spin, survivable heat.
* **Deep Hit** — fast spin, smaller Moon, very hot start.
* **Soft Clip** — larger Moon, stronger tilt, more volatile loss.

**Advanced sliders (optional):** impactor mass, speed, angle, volatile loss, angular momentum target.
**Live readouts:** day length, axial tilt, expected Moon mass, initial temp.
**Run Era →** 2–4 Outcomes → **Compare → Promote**.

### Early Archean (subsequent Eras)

* **Tectonics on/off timing**, mantle heat level, crust buoyancy, hotspot seed(s), microplate drift.
* Event cards: **Late Bombardment Tail**, **Flood Basalt Pulse**, **True Polar Wander**.

---

## 8) What the Planet Looks Like at Handoff

### Space View (far)

* A mostly **ocean world** with scattered **proto-continents/archipelagoes**.
* **Volcanic plumes** and occasional impact flashes (if within tail).
* **Cloud bands**; possibly shorter days, stronger tides (Moon closer).
* Atmosphere tint (CO₂/H₂O/CH₄ haze), **no green** (no biosphere).

### Atlas View (near)

* **Elevation & Ocean:** broad oceanic basins; buoyant continental nuclei (TTG/greenstone belts).
* **Tectonics:** mid-ocean ridges, trenches, island arcs; one or a few stabilizing cratons.
* **Hydrology:** steep, flashy **braided rivers**, early delta systems on wide shelves.
* **Coasts:** intricate shorelines; high shelf area; back-arc basins.
* **Volcanism:** komatiitic/mafic provinces; occasional LIP footprints.
* **Climate:** warm mean temps (faint sun offset by greenhouse), rain shadows downwind of arcs.
* **Chemistry overlay (optional):** anoxic deep oceans (BIF potential).
* **Atmosphere overlay:** N₂/CO₂-dominated; **\~zero O₂**; UV high but magnetosphere active.

---

## 9) Presentation & Rendering (Asset-Light)

**One renderer, two feels.** Space and atlas share the same data and palette logic.

* **Space:** Sphere mesh with data-to-color shaders (temperature, crust mask, later elevation/ocean), procedural starfield, thin disk gradient, few particles for debris.
* **Atlas:** Map overlays (hypsometric tints, hillshade, contours, rivers/flowlines, lithology hatches).
* **Icons:** 30–40 SDF glyphs (ridge, trench, hotspot, volcano, impact, shelf, craton, delta…).
* **Palettes:** elevation, temperature, rainfall, chemistry; 20-ish colors each.
* **Patterns:** stipple, hatch, wavelet, dune ripples (procedural).
* **LOD:** Coarser sampling at far zoom; switches overlays at defined zoom bands.

**ASCII sketch of stacking:**

```
[Background stars]
   ↓
[Sphere or Map Quad]
   ↓
[Base tint (elevation/temperature)]
   + Hillshade
   + Contours (zoom≥M)
   + Rivers/Coastlines
   + Lithology Hatches
   + Icons/Labels
```

---

## 10) Player Choices (Concise Menu)

**Era Dials (pre-run):**

* Water budget, CO₂ baseline, solar brightness, day length/rotation, tectonics start time, mantle heat level.

**Process Placements (map picks):**

* **Hotspot seed** (1–2), **microplate** with drift vector, **continental nuclei** bias points (optional).

**Policies (Era-wide):**

* Erosion regime (gentle ↔ dramatic), wind-belt position, sea-level ramp vs. pulse.

**Event Cards (during run):**

* **Late Bombardment Tail** (mild vs strong), **True Polar Wander** (accept small axis shift or veto), **Large Igneous Province** (short-term warming + soils later vs calm), **Ridge Jump** (oceanic spreading reorganizes).

---

## 11) Comparison & Commit

* **Outcome Board:** 2–4 thumbnails + stats: % ocean/land, mean temp & variance, coastline length, tallest range, shelf area, flood risk, **Shelf-Niche Index**, **Climate Stability Index**, **Hydrothermal Energy Index**.
* **Diff Tools:** Swipe/overlay to see coastline, rainfall, uplift, plate boundaries differences.
* **Badges:** *Shelf-Rich, Arc-Active, Stable Climate Window, Big Tides, Low Impact Risk.*
* **Promote to Canon:** Locks branch; moves to next Era.

---

## 12) Systems & Parameters (MVP slice)

Keep the parameter surface small at start; wire the rest later. Initial focus:

**Disk/Impact:**

* Impact mass/speed/angle, volatile loss, angular momentum target.

**Thermal/Cooling:**

* Mantle initial temp, magma-ocean solidification timescale, radiogenic heat scale.

**Volatiles & Atmosphere:**

* Water inventory, CO₂ baseline, cloud albedo, greenhouse sensitivity, aerosol lifetime.

**Tectonics:**

* Tectonics start time, plate count target, velocity scale, ridge push/slab pull, boundary friction, hotspot flux.

**Climate & Hydro:**

* Insolation bands, orographic factor, base precip, evaporation coefficient, stream power (K, m, n), hillslope diffusivity.

**Sea Level & Shelves:**

* Global offset, thermal expansion coefficient, shelf slope angle.

**Rendering:**

* Palettes & overlay switch thresholds, river min upstream area, hillshade intensity, contour interval.

*(A comprehensive master list exists; use this MVP subset to ship quickly.)*

---

## 13) Data Model & Determinism

* **Event-Sourced Timeline:** Each player action → `{tick, type, params}`.
* **Fixed Timestep:** e.g., Δt = 0.05 Myr.
* **Pure Systems:** `state_{t+1} = F(state_t, inputs_t)`; no wall-clock.
* **Seeded PRNG per subsystem:** consistent tie-breaks.
* **Snapshots & Branches:** Save graph as *Era Cards*; Canon is the mainline.
* **File Formats:** Human-readable **YAML/TOML/JSON** for parameters; binary delta for world state if needed.

**Minimal data fields (grids/layers):**
`elevation`, `crust_thickness`, `lithology`, `temperature`, `precip`, `runoff`, `flow_dir`, `discharge`, `sediment_thickness`, `ice_mask` (later), `ocean_depth`, `magnetism_strength`, `volcanic_flux`, `shelf_mask`.

**Indices (derived):**
`shelf_niche_index`, `hydrothermal_index`, `climate_stability_index`, `flood_risk_index`.

---

## 14) Tools & UI

* **Plan Panel:** Sliders/presets, IP counter, Credibility hint, live readouts.
* **Map Picks:** One-click hotspot/microplate placement with validation.
* **Run Screen:** Progress bar, optional Event Cards, quick replay scrub.
* **Compare Board:** Thumbnails + stats + diff; “Promote to Canon.”
* **Inspector:** Click any tile → show local time series; draw cross-section → stratigraphic profile (age, lithology).
* **Atlas Export:** Images (PNGs) + JSON stats per Outcome; Life Spark Pack at stop.

---

## 15) MVP (8–10 Weeks, Solo-Friendly)

**Goal:** From **Disk** to **Life Spark** via Hadean → Early Archean.

**Deliverables**

* **Opening Space Scene** with orbit/zoom controls.
* **Giant Impact Tuning** (presets + 2–3 sliders) + live readouts.
* **Thermal & Cooling** → magma ocean → crust fraction over time.
* **Early Atmosphere & Greenhouse** (N₂/CO₂/H₂O/CH₄ simplified).
* **Oceans & Sea Level** (global mask, shelves).
* **Toy Tectonics:** ridges, trenches, arcs; plate motion field.
* **Climate Bands & Orographic Rain**; **Rivers v1** (flow routing + stream power).
* **Outcome Board & Diff**, Promote to Canon.
* **Life Spark** detection + **Dossier Export** (maps + JSON).
* **Renderer:** space sphere + atlas overlays; palettes, contours, rivers.
* **Saves:** Era Cards (event log + snapshot) and Life Spark Pack.

**Quality Bar**

* Mass/energy sanity checks; no negative thicknesses.
* Golden Seeds (fixed seeds + actions that must replay identically).
* Performance: targeted 60 FPS UI; 10–60s Era runs (configurable).

---

## 16) Roadmap (First 12 Months)

* **0.1 Magma→Ocean (ship):** opening, impact tuning, cooling/oceans, basic compare.
* **0.2 Tectonics & Climate:** toy plates, orographic rain, Outcome Board polish.
* **0.3 Rivers & Shelves:** erosion/dep v1, deltas, shelf metrics, Life Spark metrics v1.
* **0.4 Volcanism & LIPs:** flood basalt events, aerosol forcing, compare badges.
* **0.5 Sea-Level Pulses & Gateways (simple toggles).**
* **0.6 Polish & Accessibility:** input remaps, color-blind palettes, save inspector.
* **0.7 Performance pass & mod/plugin API skeleton.**

---

## 17) Risks & Mitigations

* **Physics scope creep:** Keep parameter tables simple; expose few dials/era; add depth later.
* **Art asset bloat:** Stick to data-driven atlas style; SDF icons; no textures/characters.
* **Performance:** Equal-area grid + quadtree tiles; headless sim; cache derived layers.
* **Complexity for players:** Limit choices to 3–6 per Era; presets; clear badges; diff tools.
* **Breaking determinism:** Event-sourced log, per-system seeds, golden seeds, pure update functions.

---

## 18) Non-Goals (for this module)

* Life evolution, oxygenation feedbacks, biome rendering, human civilization.
* Cinematic cutscenes or photorealistic visuals.
* Networked multiplayer (single-player only for now).

---

## 19) Example Parameter File (tiny excerpt)

```yaml
world:
  seed: 219745
  dt_myr: 0.05
  era_length_myr: 50

impact:
  preset: balanced_graze
  projectile_mass_rel: 0.1
  speed_km_s: 15
  angle_deg: 35
  volatile_loss_frac: 0.25

atmosphere:
  co2_ppm: 150000
  n2_bar: 0.8
  h2o_humidity_scale: 1.0
  cloud_albedo: 0.22
  greenhouse_sensitivity: 3.0  # K per doubling (effective)

oceans:
  water_budget_rel: 1.0
  sea_level_offset_m: 0

tectonics:
  enable_at_Ga: 3.6
  plate_velocity_scale_cm_yr: 5
  ridge_push: 1.0
  slab_pull: 1.0
  hotspot_flux: 0.8

climate:
  orographic_factor: 1.2
  precip_base_mm_yr: 900
  evaporation_coef: 0.8

rivers:
  stream_power_K: 5e-6
  m: 0.5
  n: 1.0
  hillslope_diffusivity: 0.02

render:
  palette_elevation: "hypsometric_classic"
  hillshade_intensity: 0.5
  contour_interval_m: 200
  river_min_area_km2: 2500
```

---

## 20) Handoff: **Life Spark Dossier** (auto-generated)

* **Global Stats:** % ocean/land, mean temp & variance, day length, axial tilt, lunar distance.
* **Maps:** elevation, ocean/shelves, rainfall, rivers, tectonic boundaries, volcanic flux, hydrothermal vents.
* **Indices:** Shelf-Niche, Hydrothermal Energy, Climate Stability, Flood Risk.
* **Narrative Card:** “Why Life Sparked Now” (thresholds met + key contributors).
* **Export:** `/exports/lifespark_<seed>_<era>.json` + PNG atlas set.

---

## 21) Minimal Backlog (first 4–6 weeks)

1. Repo scaffolding; parameter loader; seeded RNG per subsystem.
2. Fixed-timestep kernel; event bus; event log; snapshotting.
3. Space renderer: starfield, disk gradient, sphere; orbit/zoom controls.
4. Giant Impact tuning panel (3 presets + 2–3 sliders) with live readouts.
5. Thermal/cooling model; magma-ocean state → crust fraction.
6. Atmosphere/greenhouse simplified EBM; oceans/sea level mask.
7. Atlas renderer: elevation tint + hillshade + contours; coastlines.
8. Toy plates: ridges/trenches; plate velocity field; simple uplift.
9. Climate bands + orographic rain; rivers v1 (routing + stream power).
10. Outcome Board (+ diff swipe); Promote to Canon.
11. Life Spark metric roll-up and dossier export.
12. Golden seed tests; invariants (no negative thickness, mass sanity).

---

## 22) Glossary (quick)

* **Canon:** The chosen outcome that becomes the official timeline for the next Era.
* **Era Card:** A saved snapshot + event log you can replay/branch from.
* **Life Spark:** The stop condition when habitability thresholds are met.
* **IP (Intervention Points):** Your limited per-Era budget to change big dials.
* **Credibility:** A soft constraint indicating how physically plausible your settings are.
* **SDF Icons:** Resolution-independent vector glyphs used for map symbols.

---

## 23) Closing Note

Planet Builder (Pre-Life) is a tight, shippable slice: a beautiful **map-driven** world that you **compose** through a handful of consequential choices, stopping at the precise moment the stage for life is set. The approach keeps art lightweight, simulation central, and the design expandable for decades.
