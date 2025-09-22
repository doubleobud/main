# **Project Constellation** — Concept Document

*(codename; use any title you like — this reflects your unique “genre ladder” approach while presenting it professionally.)*

---

## 1) Overview

**Elevator:** Constellation is a decades-scale, solo-built game that **ascends across genres**—from text roleplay to god game to colony/city/4X and beyond—letting players **create a world, then step into it**, zooming up and down scales as systems persist.

**Core idea:** Play the *history of games and civilizations* as one coherent experience: **words → life → creation → embodiment → settlement → city → region → globe**.

**Audience:** Players who love systemic sandboxes, builder/strategy layers, and role-playing; tinkerers who value emergent stories and long-term progression.

**Platforms:** PC first, controller+KB friendly. Engine-agnostic design; solo-friendly tooling.

---

## 2) Player Promise

* **Create first, inhabit later:** Shape the world as a god, then become a character who lives in what you made.
* **Persistent causality:** Actions at one layer **meaningfully persist** into the next (terrain, economies, reputations, myths).
* **Genre ladder:** Each new “release package” unlocks a **fresh genre lens** without discarding previous layers.
* **Play how you like:** Freeform, **creative sandbox** spirit with optional challenges and structural modes (idle, roguelike runs).

---

## 3) Design Principles (values, not “pillars”)

1. **Clarity over clutter** – simple rule sets that rhyme across scales.
2. **Elegant depth** – few mechanics, rich combinations.
3. **Unified grammar** – consistent inputs, resources, and feedback at every layer.
4. **Diegetic continuity** – the world explains itself; systems feel in-world.
5. **Solo-dev feasibility** – incremental slices, reusable tech, data-driven content.
6. **Player agency** – creation and meaningful choice trump scripted outcomes.

---

## 4) Core Systems (shared across all layers)

**4.1 Unified Resource Tokens**

* **Time** (ticks/turns/schedule), **Energy/Stamina**, **Materials**, **Knowledge**, **Influence/Reputation**, **Population**.
  These tokens translate across layers (e.g., Knowledge discovered in Text/IF unlocks build options in God/Colony).

**4.2 Input & Camera Stack**

* **Inputs:** the same verbs mean the same things (Select, Act, Inspect, Place, Travel).
* **Cameras:** **God View** (map/brush), **Tabletop Grid** (tactics/board), **Embodied** (top-down/iso/first-person when appropriate). Only 2–3 active per layer.

**4.3 Time & Save Model**

* One canonical timeline with **zoom-in saves** (return to any layer without desync).
* Short sessions always produce progress (10–15 min “wins”).

**4.4 Resolution Engines (battle/encounter)**

* **TBT** (small tactical), **Auto-Battler** (mid-scale), **TBS** (large operational). The game chooses the engine based on **encounter scale**; player can override when allowed.

**4.5 Data-Driven Content**

* Entities as tagged data (biomes, items, recipes, units).
* Procedural tables for names, events, relics; authored seeds where needed.

---

## 5) Genre-Ladder Progression (your sequence, professionally framed)

Each step adds a new lens while **carrying forward** world state.

1. **Interactive Fiction (Text RPG)** – Roleplay via text; establish myths, map seeds, first lore tokens.
2. **Life Sim (Stats Layer)** – Needs/traits/time; introduce schedules and personal arcs.
3. **Idle / Incremental Mechanics** – Optional automation; background progression loops.
4. **Roguelike Front-End** – Procedural runs establish unlocks/blueprints for the world.
5. **God Simulation (World Builder)** – Sculpt terrain/biomes; place rules, resources, and high-level constraints.
6. **Creative Sandbox** – Free build with low friction; validate systems toys (no fail pressure).
7. **Tabletop Mode (Top-Down Grid)** – Board-like read of the world; prepares POV transition.
8. **CRPG / WRPG (Incarnate)** – Become a character inside the world you shaped; quests emerge from prior steps.
9. **Survival-Crafting** – Isolated start; gather/craft using materials from earlier world gen.
10. **Immersive Sim (Physics-Driven)** – Small-scale systems interplay (locks, power, fluids).
11. **JRPG Party Mechanics** – Party comp, roles, ability synergies; narrative beats.
12. **Turn-Based Tactics (Small Squad)** – Grid movement, cover, objectives; links to Tabletop.
13. **Colony Simulation** – Settlers with needs; jobs, schedules, pathing, hazards.
14. **Tower Defense (Colony Events)** – Raids/disasters resolved via defensive builds.
15. **Open-World RPG** – Leave the valley; world traversal, factions, light vehicles/mounts.
16. **Construction & Management Sim** – Services, logistics, territory expansion.
17. **City Builder** – Zoning, traffic, utilities; policy knobs appear.
18. **Tycoon / Business Sim** – Markets, firms, supply chains, price dynamics.
19. **Auto-Battler (Mid-Scale Conflicts)** – Resolve mass skirmishes efficiently using builds/synergies.
20. **4X Strategy (Regional)** – Found new cities; abstract map; diplomacy & exploration.
21. **Turn-Based Strategy (Large Battles)** – Operational combat over turns; attrition & supply.
22. **Grand Strategy (Globe)** – Fully abstracted world stage; ideology, treaties, catastrophes.

**Continuity rule:** *Nothing is throwaway.* Each layer **reads** earlier state and **produces** artifacts for later layers.

---

## 6) Aesthetics & Presentation

* **Art direction:** readable, stylized, **textured 2D on grid** for Tabletop and TBT; clean top-down/iso for colony/city; minimalist materials for ImmSim.
* **Audio:** feedback-first; soft motifs recur across scales (same “theme,” different instrumentation).
* **UI:** consistent lexicon (Inspect, Place, Route, Craft); color and iconography carry meanings across layers.

---

## 7) Accessibility & UX

* Scalable text, color-blind safe palettes, input remap, motion options.
* “One new idea at a time” onboarding; tooltips and diegetic hints.
* Session respect: quick save everywhere; micro-goals designed for short play.

---

## 8) Scope Boundaries (for a solo dev)

* Prefer **systems over content**; reuse patterns.
* Each release package targets **Playtestable → Content-Complete → Stabilized → Certified** gates.
* Avoid full fidelity at first (graybox everything), ship clarity.

---

## 9) Risks & Mitigations

* **Risk:** Feature sprawl across genres.
  **Mitigation:** Hard caps on mechanics per layer; ADR for any new system.
* **Risk:** Persistence complexity.
  **Mitigation:** Define a thin **World State API** (terrain, tokens, flags, history events).
* **Risk:** Context switching burnout.
  **Mitigation:** Work in **area slices** with clear “done” checklists; alternate complexity with cozy tasks.
* **Risk:** Player overwhelm.
  **Mitigation:** Optionality (Idle off/on, Roguelike off/on), smart defaults, gradual unlocks.

---

## 10) High-Level Technical Frame (engine-agnostic)

* **Core modules:**

  * **World Kernel:** terrain/biomes/time; save/versioning.
  * **Entity/Item System:** tagged data, recipes, stats.
  * **AI & Jobs:** schedulers (colony), simple planners.
  * **Resolution Engines:** TBT, Auto-Battler, TBS pluggable.
  * **Physics Lite:** interactions for ImmSim.
  * **UI Shell:** common widgets, map overlays, tooltip lore.

* **Content pipeline:** CSV/JSON tables → importers → prefabs.

* **Testing:** simulation seeds, deterministic replays.

---

## 11) Very High-Level Roadmap (release packages that feed forward)

> Each package is shippable on its own and **feeds** the next. You’ll still split each into smaller week-sized slices.

**RP-0 — Seed & Word**

* *Deliverables:* IF/Text RPG, Life Sim stats, optional Idle, Roguelike front-end.
* *Outcome:* World seed, first lore & knowledge tokens; working save/time.

**RP-1 — World from Above**

* *Deliverables:* God Game sculpt & rules; Creative Sandbox toys; Tabletop view.
* *Outcome:* Playable terrain/biomes, placeable resources, readable grid.

**RP-2 — Step Into the World**

* *Deliverables:* CRPG/WRPG embodiment; Survival-Crafting loop; Immersive-Sim interactions.
* *Outcome:* A 10–15 min character slice inside your world.

**RP-3 — Parties & Tactics**

* *Deliverables:* JRPG party systems; Turn-Based Tactics encounters (uses Tabletop).
* *Outcome:* Small squad missions; first dungeons/POIs informed by world seed.

**RP-4 — Founding the Settlement**

* *Deliverables:* Colony Sim core (jobs, needs, hazards); Tower Defense events.
* *Outcome:* Stable settlement sandbox with defendable loops.

**RP-5 — Beyond the Valley**

* *Deliverables:* Open-World RPG traversal; light vehicles/mounts; quest generation.
* *Outcome:* Cohesive region exploration tied to colony economy.

**RP-6 — Services & Streets**

* *Deliverables:* Construction & Management Sim; logistics, utilities, zoning start.
* *Outcome:* Territory expansion; early traffic and services.

**RP-7 — Town to City**

* *Deliverables:* City Builder systems (policies, traffic, budgets).
* *Outcome:* Urban management layer; KPIs and citizen simulation.

**RP-8 — Markets in Motion**

* *Deliverables:* Tycoon/Business simulation; trade routes & firms.
* *Outcome:* Macro-economy driving prices, jobs, and conflicts.

**RP-9 — Clashes at Scale**

* *Deliverables:* Auto-Battler for mid-scale; integration with TBT.
* *Outcome:* Efficient resolution of growing conflicts.

**RP-10 — Region & World**

* *Deliverables:* 4X layer (explore/expand/exploit/exterminate), Turn-Based Strategy for large battles, Grand Strategy world map.
* *Outcome:* Fully abstracted strategic play that still reads and writes the same world state.

**Gates per package:**

* **Playtestable:** 10-minute loop runs cleanly.
* **Content-Complete:** all planned systems present (ugly ok).
* **Stabilized:** bugs/perf within budget; saves safe.
* **Certified:** readability, accessibility, docs done.

---

## 12) Success Criteria

* Every package **stands alone** yet **enriches** the next.
* Players can **feel** the continuity: “the valley I carved,” “the route I paved,” “the city I founded,” “the empire I shaped.”
* You can keep shipping **small, satisfying slices** for years while climbing the ladder.

---

If you want, I can turn this into a one-page **PDF brief** and a **tracker template** (areas, slices, gates) so you can start RP-0 immediately.
