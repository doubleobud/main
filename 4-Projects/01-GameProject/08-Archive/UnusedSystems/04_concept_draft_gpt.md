# **Project Constellation** — Concept Document

*(codename; use any title you like — this reflects your unique “genre ladder” approach while presenting it professionally.)*

---

## 1) Overview

**Elevator:** Constellation is a decades-scale, solo-built game that **ascends across genres**—from text roleplay to god game to colony/city/4X and beyond—letting players **create a world, then step into it**, zooming up and down scales as systems persist.

**Core idea:** Play the *history of games and civilizations* as one coherent experience: **words → life → creation → embodiment → settlement → city → region → globe**.

**Audience:** Players who love systemic sandboxes, builder/strategy layers, and role-playing; tinkerers who value emergent stories and long-term progression.

**Platforms:** PC first, controller+KB friendly. Engine-agnostic design; solo-friendly tooling.

**Opening Premise (Diegetic Frame):** The experience opens as a **pure digital novel** rendered like **earliest computer readouts**. In-fiction, you and the player **co-build a simulation together**: the narrator openly frames themselves as a **novice developer**, starting with the simplest foundation and “building the game in front of you.” This simplicity is also diegetic: the player's outside life is revealed (over time) to be an **illusion produced by a brain‑computer interface (BCI)** sustaining them during a **coma**. Participating in the simulation provides **brain data** that could help diagnose their condition and **bring them back** as the interface becomes more connected to their mind. The **BCI’s initial bandwidth limits** the complexity that can be delivered—**justifying the primitive start** and the genre‑by‑genre expansion. Within the fiction, the player’s meta‑avatar and the narrator share a small **bunker** in a **post‑collapse world**—the **actual reality** in which the comatose body exists; from here they co‑author the simulation together.

---

## 2) Player Promise

* **Create first, inhabit later:** Shape the world as a god, then become a character who lives in what you made.
* **Persistent causality:** Actions at one layer **meaningfully persist** into the next (terrain, economies, reputations, myths).
* **Genre ladder:** Each new “release package” unlocks a **fresh genre lens** without discarding previous layers.
* **Play how you like:** Freeform, **creative sandbox** spirit with optional challenges and structural modes (idle, **meta‑progression planning**).
* **Multi‑role identity:** Create a **digital reflection** of yourself (meta‑avatar) who knows about the simulation and advances the **meta‑progression front‑end**; **train and guide a God** entity (more direct control early, policy‑level later); and **incarnate into NPCs** temporarily or for a full lifespan, with parties/organizations and clear control limits.

---

## 3) Design Principles (values, not “pillars”)

1. **Clarity over clutter** – simple rule sets that rhyme across scales.
2. **Elegant depth** – few mechanics, rich combinations.
3. **Unified grammar** – consistent inputs, resources, and feedback at every layer.
4. **Diegetic continuity** – the world explains itself; systems feel in-world.
5. **Solo-dev feasibility** – incremental slices, reusable tech, data-driven content.
6. **Player agency** – creation and meaningful choice trump scripted outcomes.
7. **Diegetic scaffolding of complexity** – “novice dev” voice + **BCI bandwidth** justify the gradual feature ramp.

---

## 4) Core Systems (shared across all layers)

**4.1 Unified Resource Tokens**

* **Time** (ticks/turns/schedule), **Energy/Stamina**, **Materials**, **Knowledge**, **Influence/Reputation**, **Population**.
  These tokens translate across layers (e.g., Knowledge discovered in Text/IF unlocks build options in God/Colony).

**4.2 Input & Camera Stack**

* **Inputs:** the same verbs mean the same things (Select, Act, Inspect, Place, Travel).
* **Cameras:** View tiers — **Tactical (Top‑Down Grid, locked)** for individuals; **City** for districts/services; **Regional** for networks/terrain; **Global** for planet projects; plus **Embodied** when appropriate. Only 2–3 active per layer. Supports **z‑layers**, height indicators, and **voxel dig reveals**.

**4.3 Time & Save Model**

* One canonical timeline with **zoom-in saves** (return to any layer without desync).
* **Dual time domains:**

  * **Meta‑Avatar Time = real‑time.** The meta‑avatar lives on the **actual clock**; they **age**, follow **schedules**, and continue when you are away.
  * **Simulation World Time = player‑driven ticks/turns.** The player has **tick authority**; no background advancement occurs unless explicitly processed.
* Short sessions always produce progress (10–15 min “wins”).

**4.4 Resolution Engines (battle/encounter)**

* **TBT** (small tactical), **Auto-Battler** (mid-scale), **TBS** (large operational). The game chooses the engine based on **encounter scale**; player can override when allowed.

**4.5 Data-Driven Content**

* Entities as tagged data (biomes, items, recipes, units).
* Procedural tables for names, events, relics; authored seeds where needed.

**4.6 Diegetic Progression Gate (BCI Bandwidth)**

* **BCI Bandwidth Meter:** a behind‑the‑scenes scalar that gates UI affordances, system density, and content complexity.
* **Calibration Moments:** short IF/choice or micro‑puzzles that “collect signal” (in‑fiction brain data), unlocking mechanics.
* **Narrator Layer:** optional “novice dev” commentary toggle; integrates with tutorials & patch‑note‑as‑lore; **diegetic role: bunker operator** in a collapsed world addressing the player directly.

**4.7 Player Roles & Control Model**

* **Meta‑Avatar (Digital Reflection):** Player‑created persona that is *aware of the sim*. Lives “outside” the world in the diegesis, accrues **account‑like progression** (blueprints, perks), and interfaces with the **meta‑progression front‑end** unlocks.
* **God:** Early on, the player can **directly control** the God—placing tiles, nudging agents, authoring rules. Over time (as the God is **trained**), control shifts to **policy knobs**, priorities, and constraints; the God increasingly **operates autonomously** using learned heuristics.
* **Incarnations (NPC Possession):** The player can **jump into** NPCs to become them for a session, arc, or entire lifespan. Form **parties/organizations** of such characters. Control is bounded by an **Agency Budget** (time/attention currency) and **possession windows** with cooldowns.
* **Control Rules:** One **active embodiment** at a time; queued orders and **delegation** persist after leaving a body. Organizations act as **containers** for multi‑agent goals within the budget. UI signposts role, scope of control, and consequences.
* **Identity & Save:** A lightweight **Identity Ledger** records who the player has been, what they changed, and what persists; supports replay and provenance.

**4.8 Time Domains & Away‑Time Resolver**

* **Meta‑Avatar (Real‑Time):** Schedules run on the real clock; when the player is offline, an **Away‑Time Resolver** simulates outcomes (jobs, study, rest, random events) according to the plan and traits.
* **Bunker Loop:** The meta‑avatar shares a **bunker** with the narrator; activities here (maintenance, crafting, comms, diagnostics) generate **knowledge/blueprint fragments** for the sim.
* **Simulation (Tick‑Based):** The simulation world never advances while you’re away unless explicitly ticked. **No idle loops** inside the sim.
* **Interfaces:** On return, an **Away‑Time Summary** surfaces key outcomes; the player can accept, roll back within guardrails, or branch.
* **Safeguards:** Quiet hours, vacation mode, and caps on negative drift to avoid punishing time‑zones or life breaks.

**4.9 Creative Blueprint & Construction System**

* **Parametric Blueprints:** Author designs as templates with inputs/outputs, constraints, variants, and **versioning**; stamp at different scales.
* **Assembly & Manufacturing:** Craft chains and work orders; cost/time estimation; integrates with **Materials** and **Population** tokens.
* **Networks Graph:** Roads/rails/power/water/comms as layered graphs with **capacity, loss, and maintenance**.
* **ECS Composition:** Systems are components; emergent behavior arises from **composable interactions** (heat, fluids, traffic, signals, economy, ecology).
* **Iteration Tools:** Staging sandbox with **simulation preview**, performance budget meters, and validation checks.
* **Export/Import:** Blueprints become **world tokens** used by Colony/City/Tycoon; can be **retrofitted** or mass‑upgraded.

**4.11 Survival & Crafting (Spec)**

* **Survival Loop:** exposure (temperature, wetness, wind), hunger, thirst, fatigue, injury/disease; mitigated by **shelter, clothing, fire, clean water, medicine**.
* **Resource Graph:** **harvest → process → component → tool/structure** tiers with **workbenches/stations**; item **quality & durability**.
* **Discovery & Experimentation:** learn recipes by **combination**, **environmental hints**, and **Knowledge Keywords**; journals record findings.
* **Assignment & Trades:** early **personal crafting** grows into **assigned tradesmen** as settlements form; integrates with **AI & Jobs**.
* **Mining/Refining Pipeline:** small‑scale mining/refining appears here; **full industrial logistics** unlock during **Construction/City** layers.
* **Outputs:** produces **blueprint seeds**, **starter kits**, and **crafted artifacts** that carry legacy tags for lineages.

**4.12 Immersive Systems & Discovery (Spec)**

* **Material Database & Affordance Tags:** centralized material/property tables; state machines for wet/dry, temperature, charge, integrity.
* **Reaction Matrix:** rule set for **heat/combustion**, **electricity/circuits**, **fluids/gases/pressure**, **mechanics/constraints**; tuned for clarity and performance.
* **Perception/Discovery Lens:** scan overlay with **hint tiers**; integrates with **Knowledge Keywords**; logs observations to the **Identity Ledger**.
* **Idea Alchemy:** combine **concepts + materials + methods** to derive **recipes/practices/devices**; supports inference from partial knowledge.
* **Experiment Harness:** clone small scenes into a controlled **testbed**; record outcomes and generate **repro seeds** for debugging/balance.
* **Causality Log:** capture **why** something happened (inputs → reactions → effects) for player feedback and QA.
* **Safety Budgets:** cap reaction chains per tick; graceful degradation to avoid perf spirals.
* **Outputs:** produces **blueprint seeds**, **starter kits**, and **crafted artifacts** that carry legacy tags for lineages.

**4.13 Parties, Synergy & Influence Scaling (Spec)**

* **Recruitment Pipeline:** encounter → rapport checks → persuade → cohort → controlled; **control** costs paid from **Agency Budget** and **Influence**.
* **Synergy Graph:** persistent graph of **duo/formation/role** synergies; diminishing returns to prevent stacking abuse; **training** spreads practices over time.
* **Training & Mentorship:** schedules for drills/study; adjacency and facility bonuses; unlocks **ability exchanges** and **combo techniques**.
* **Collection/Compendium:** roster cards with **lineage/race tags**, history notes, set bonuses, and provenance from the **Identity Ledger**.
* **Influence Scaling:** abstractions for **party → squad → company → guild → province/nation**; direct control narrows as scale rises, shifting to **doctrines/policies**.
* **Tradeoffs:** controlling more bodies reduces bandwidth for **God/meta** actions; cooldowns on multi‑control; **possession windows** enforced.
* **Interfaces:** Party screen (roles, formation, synergy web), Compendium, recruitment dialogs with **persuasion checks**; organization dashboards.

---

## 5) Genre-Ladder Progression (your sequence, professionally framed)

Each step adds a new lens while **carrying forward** world state.

1. **Interactive Fiction (Text RPG) — Opening Sequence & Fiction Justification** – Roleplay via text; establish myths, map seeds, first lore tokens.

   * Begin with a **pure digital novel** presented as **earliest computer readouts**.
   * Progress to **primitive IF (CYOA)** and then **early text‑adventure**.
   * **Co‑building the simulation with “me”:** the narrator acknowledges being a complete novice and *builds the game in front of the player*; at first there isn’t even a “game,” only a **story**.
   * **Diegetic setup & reveal:** the life the player believes they’re living **outside the game** is an **illusion created by a BCI** keeping them *healthy, stimulated, and alive* during a **coma**. By building and acting in the simulation, they provide **brain data** that could **help understand their condition and possibly bring them back**, as the interface becomes increasingly connected to their mind.
   * **Why the primitive start:** both the narrator’s novice stance and **BCI bandwidth limits** cap complexity at first; as the connection **strengthens**, more genres/systems unlock.
   * The opening **paces toward a major reveal**, foreshadowed through calibration moments and system unlocks.
   * **Bunker reading loop:** Return to your room to read short “stories” I provide—initially perceived as fiction, later revealed to be **interconnected**.
   * **Not Earth:** The setting of those stories is an **Earthlike planet**, and the narrator **lives there**.
   * **Pockets of tech:** Collapsed society with pockets of technology, including **primitive BCIs** that foreshadow the coma link.
   * **Shattering reveal:** The player's “real life” is **BCI‑generated**; they are **in a coma**. The simulation exists to **preserve and probe** the mind.
   * **Handover to world‑building:** Text adventure escalates into **in‑bunker world creation**, initiating the **God Simulation**.
2. **Life Sim (Stats Layer)** – Needs/traits/time; introduce schedules and personal arcs.

   * **Begins primitively** alongside the IF prologue; expands as **BCI bandwidth** increases.
   * **Scope ambition:** Over time, grow toward a **robust life‑sim** with schedules, habits, relationships, jobs, skills, and personal arcs that connect to higher layers (colony/city/4X economies and histories).
   * **Digital Reflection:** Encourage the player to create a **meta‑aware character** that mirrors themselves. This persona interacts **outside the sim**, curates incarnations, and ties directly into the **meta‑progression front‑end** (collect blueprint fragments, unlock meta‑progression).
   * **God Training:** Early life‑sim slices include **guided tutorials** where the player and God co‑author routines and community rules; later, the God applies these patterns autonomously.
   * **Incarnations & Parties:** Allow **jumping into NPCs** (incarnations) for moments or lifetimes; form **parties/organizations** with **control restrictions** governed by an **Agency Budget** and **possession windows**. Delegation persists when the player exits a body.
   * **Personal Arcs:** Traits and needs drive **emergent goals** (study, craft, relationships); journals/diaries create **memory trails** that persist into Colony/City history.
3. **Idle / Incremental Mechanics** – Optional automation; background progression loops **for the meta‑avatar only**.

   * **Early‑game focus:** The **meta‑avatar** is the concern. They live with the narrator in a **bunker** while you co‑develop the simulation.
   * **Real‑time schedules:** The meta‑avatar runs on the **real clock** (sleep, work, study, maintenance). The player plans a schedule; **while away**, the character continues, **aging** and evolving.
   * **Away‑time events:** Planned tasks, trait checks, and low‑frequency events resolve via the **Away‑Time Resolver**, yielding progress (or setbacks) and **front‑end unlocks**.
   * **No sim‑idle:** **Inside the simulation world, there is no idle progression.** The player **controls when ticks are processed**; all sim changes are explicit.
   * **Why it fits:** Keeps engagement when the player is off, while preserving **strict authorship** over the simulation timeline.
4. **Meta‑Progression Front‑End (Permanent World; No Runs)** – The world **persists**. There are **no procedural runs** or resets unless the player explicitly **wipes their meta‑profile** and starts anew.

   * **No runs, no resets:** Once a world is created, the player remains in it; continuity is the point. Wiping the meta‑profile is a deliberate, rare action.
   * **Timeline inhabitation:** Progress comes from **inhabiting NPCs** across the world’s timeline (incarnations) and making enduring changes.
   * **Meta‑avatar growth:** A deep **character‑build layer** for the meta‑avatar (scope inspired by *Owlcat‑scale* breadth) including feats/perks, specialties, and long arcs.
   * **Roster synergy:** Characters on the player’s **roster** also progress; **meta‑avatar bonuses** and doctrines **affect controlled NPCs** during incarnations.
   * **Knowledge Keyword System:** Collect and combine **knowledge keywords** (concept tags) to “**build the brain**” — unlocking research paths, interfaces, and higher‑order reasoning tools.
   * **Unlock administration hub:** **Blueprints, features, functions, and cosmetics** are **iteratively unlocked** here, though almost always **earned inside the simulation** through actions and discoveries.
   * **BCI & gating:** The front‑end surfaces what the **BCI bandwidth** now allows (systems/UI density) and what next calibrations might unlock.
   * **Profile management:** Tools for **meta‑profile creation**, **backup/export**, and **full wipe** with clear consequences.
5. **God Simulation (World Builder) — Dynasty & Planet Builder (Bunker‑Born World)** – The God phase begins **inside the bunker** right after the IF reveals. It functions as both a **Sim‑Earth/planet builder** and a **dynasty/history simulator** with extremely **abstract visuals at first**, upgraded incrementally via unlocks.

   * **Entry from IF:** The stories you read seed initial **planet parameters** and **mythic constraints**; stepping into God mode makes those seeds editable.
   * **Visual progression:** Start with **symbolic maps** and terminal overlays → **wireframe grid** → **textured 2D** as BCI bandwidth grows.
   * **World genesis:** Author **axial tilt, climate bands, ocean/continent ratios, biomes**, and **resource distributions**; export **heightmaps/biomemaps** for later layers.
   * **Rules & constraints:** Place **natural laws, ecological rules, and cultural principles** (taboos, rites, calendar); define **spawn tables** and hazards.
   * **Epoch control:** Advance **epochs** (ice ages, volcanic eras, migrations) and set **timescale**; run **epoch ticks** to settle geology/biota.
   * **Proto‑civilizations:** Inhabit **proto‑humans** via text‑adventure style **symbolic expeditions** on the map; establish **lineages** and **genealogies**.
   * **Dual role:** For now, the player toggles between **God actions** and selective **incarnations** in proto‑beings to experience consequences directly.
   * **Training the God:** Convert authored choices into **policies/heuristics**; over time the God executes these autonomously.
   * **Outputs to later layers:** Terrain, biomes, **history events**, **lineage trees**, **myth tokens**, and **law flags** feed Tabletop/CRPG/Colony/City.
   * **BCI gating:** Higher‑fidelity renderers, denser systems, and additional brushes unlock as bandwidth and knowledge increase.
6. **Creative Sandbox — Planet‑Scale Maker Mode** – A true sandbox for shaping an entire **planet over decades** (played in **chunks & iterations** that accumulate). Systems are built to **compose**, yielding vast **emergent behaviors**; the goal is a toybox you and other players can enjoy endlessly—**no fail pressure**, just **build → simulate → iterate**.

   * **Planet‑scale authorship:** Manipulate terrain, climates, biomes, and settlements from **local tiles** to **regional networks** to **global projects**—with changes persisting.
   * **ECS‑driven systems toys:** Reusable components (power, fluids, traffic, heat, signal, economy, ecology) that **combine** to create new behaviors.
   * **Maker workflows:** **Research → Prototype → Blueprint → Manufacture → Deploy → Maintain**. Turn ad‑hoc builds into **standard designs** you can stamp, version, and upgrade later.
   * **What you can build:** **Infrastructure** (roads/rails/pipelines/power/water/comms), **buildings** (habitation, industry, civic), **vehicles** (ground/air/sea; later orbital), **tools**, and **everything in between**.
   * **Blueprint Studio:** Parametric templates with constraints; materials & labor budgets; performance stats; **cosmetic layers** for style.
   * **Networks & logistics:** Lay transportation and supply routes; simulate flow, bottlenecks, and maintenance.
   * **Low‑friction iteration:** Snap/grids, preview ghosts, bulk‑edit, multi‑select, **undo/redo**, **version control** for blueprints, and a **staging yard** to test builds safely.
   * **Progression tie‑ins:** Unlock new components via **Knowledge Keywords**, **BCI bandwidth**, and **world discoveries**.
7. **Tabletop Mode (Top‑Down Grid) — Tactical Read & World Look** – Focused on **portraying the world clearly** at close range while staying **procedural and efficient**. This is the **primary tactical view** when controlling individual characters.

   * **Locked top‑down perspective:** Optimized for **tick‑based, tile maps** and procedural graphics. Consider **3⁄4 top‑down** only if it materially improves immersion without sacrificing clarity/perf.
   * **Textures over sprites:** Environment uses **textured tiles/meshes**, not flat sprites. **3D models** for characters and key props render from a **locked camera** to leverage modeling/animation while keeping a 2D read.
   * **Human warmth:** **Character portraits** (and optional barks) build attachment and fight the usual top‑down “coldness.” Ambient motion, weather, decals, footprints, and light FX add life.
   * **Verticality & digging:** **Z‑levels** with clear **height indicators**; **voxel‑like dig layers** for mines/caves with cross‑section views when underground.
   * **Zoom band:** Close/tactical zoom roughly akin to **RimWorld** scale (art style is different); objects remain **readable** at all times.
   * **Four view tiers:** **Tactical**, **City**, **Regional**, **Global**. Each first appears in its **simplest** presentation and **upgrades over time** via meta‑progression as the simulation improves.
   * **Purpose:** Board‑like clarity that **prepares POV transition** into Embodied/CRPG while sharing the same tokens, rules, and maps.
8. **CRPG / WRPG (Incarnate) — Lineages, Succession, and Embodied Play** – This is where **characters come online inside the simulation**. It begins with the first **proto‑humans** and advances through epochs.

   * **Embodied entry:** Toggle from Tabletop/God into a **single character** view; early eras use **time chunking** (large steps) that narrow as societies mature.
   * **Lineage simulator:** Characters **live, age, and die**. Death isn’t failure—**legacy** persists via **traits, artifacts, buildings, and myths** that feed the world state.
   * **Main Line (Meta‑Avatar Dynasty):** At a milestone, the meta‑avatar establishes a **personal lineage**—a chain of “main” in‑sim characters (successors) chosen by the player, carrying **family banners, doctrines, and oaths**.
   * **Party & organization control:** Spend a **control resource** (extension of the **Agency Budget**) to temporarily **multi‑control** party members or issue org‑level commands; cooldowns maintain balance.
   * **Progression depth:** The **most expansive unlock system** lives here: talents/feats, specialties, backgrounds, destinies, and **Knowledge Keyword** integrations that unlock new interfaces and reasoning tools.
   * **Quests from the world:** Missions are **read from prior steps** (terrain, laws, myths, lineages, hazards). A **Quest Weaver** assembles objectives from world flags—no hard resets.
   * **Succession play:** Near a character’s end, choose **heirs/successors** with **previewed inheritances** (traits, relationships, holdings). Optionally designate a **companion** or **rival** to become the next POV.
   * **Micro and meaning:** As systems grow, the game enables enough **micro** to make **every character feel worth knowing**, while offering delegation for the rest.
9. **Survival‑Crafting — First Embodied Trials & Early Manufacturing** – After the planet forms and biosphere eras reach **proto‑humans**, your **first inhabited character** begins **isolated** in a small region—your **first exposure to the Tactical view**.

   * **Isolated start:** Alone in nature with minimal gear; learn **foraging, shelter, fire, water, and first tools**.
   * **Persisting survival:** Survival systems **persist and grow** from here, integrating with **RPG** traits/status effects and **Life Sim** schedules.
   * **Early manufacturing:** Crafting serves as the **earliest manufacturing layer** that later feeds Colony/City—**collect resources → discover uses → craft chains → assign trades**.
   * **Crafting scope:** A very large tree (to be detailed) covering **tools, clothing, shelters, medicines, foods, fuels, simple machines**; quality/condition/durability matter.
   * **Mining → refining → transport → manufacturing:** Present in principle, but **major industrialization** unlocks later (City/Construction & Management tiers) with proper logistics.
   * **Lineage kickoff:** When the **Main Line** (meta‑avatar dynasty) begins, it also starts with an **isolated survival scenario** to inaugurate that phase—**all alone**.
   * **Integration:** Uses **Tabletop** clarity for placement, ties into **Immersive‑Sim** interactions at small scale, and produces **blueprint seeds** for the maker systems.
10. **Immersive Sim (Physics‑Driven) — Materials, Affordances & Discovery** – Not necessarily first‑person; this layer ensures **materials and resources are always viable solutions**. The ethos: *a solution is one discovery away*.

* **Materials & affordances:** Every object carries **material tags** (wood/stone/metal/cloth/leather/organic) and **properties** (flammable, conductive, porous, magnetic, acidic/alkaline, tensile, brittle) with **state** (wet/dry, charged, temperature, integrity).
* **Reaction systems:** Interplay across **locks**, **power**, **fluids/gases/pressure**, **heat/combustion/smoke**, **mechanical linkages** (ropes, pulleys, levers), and **chemistry‑lite**—emergent outcomes over authored puzzles.
* **Perception/Discovery Mode:** A toggleable lens that surfaces **latent affordances**, highlights **unknown interactions**, and proposes **experiment prompts**. Improves with **Knowledge Keywords** and practice.
* **Idea Alchemy:** An extensible system (think a much broader, systemic version of Skyrim’s alchemy) applied to **materials, techniques, concepts, and practices**. Combine **keywords + items + methods** to synthesize new recipes, devices, and procedures.
* **Environment leverage:** Use the **environment itself**—water to short a circuit, smoke to reveal beams, heat to weaken resin, sand to increase friction, wind to carry scents.
* **Experiment safely:** Small scenarios can be cloned into a **staging yard** (bunker or tabletop test space) to experiment **fail‑soft** before committing in the real timeline.
* **Outputs:** Discovered interactions become **blueprints/practices** and **journal entries**; world flags update to unlock further systemic quests.

11. **JRPG Party Mechanics — Recruitment, Synergy & Scale‑Up** – Early in the timeline, the player can embody **only one** character for a long while. Eventually, they can **recruit** others—first by **persuasion/influence** only. Over a longer arc, they can **gain direct control** of select members, but **at a cost** to other control forms (draws from the **Agency Budget** and reduces God/meta bandwidth).

* **Recruitment ladder:** Meet → befriend → persuade → cohort → **controlled**. Control privileges are **earned**, time‑limited, and **trade off** with other powers.
* **Synergy & training networks:** Characters **train** each other in **knowledge and practices**, unlocking **ability exchanges** and **combo synergies** (mentor↔apprentice, duo techs, formation bonuses).
* **Scale growth:** Parties evolve into **organizations**, then into **factions/nations** under influence—scaling from **tens → hundreds → thousands → hundreds of thousands**. Interfaces and control **abstract up** as other modes come online (TBT/Colony/City/4X), while still honoring party comps at the tip of the spear.
* **Collection & lineage:** A light **collection vibe** (think GI Joe/Pokémon inspiration) where each character is **unique**, tied to **lineages/races**, histories, and specialties. A **Compendium** tracks provenance, bonds, and set‑style bonuses.
* **Narrative beats:** Loyalty arcs, recruitment quests, mentorships, rivalries; **synergy stories** give texture to combos beyond raw stats.
* **BCI gating:** Party size, direct‑control privileges, and synergy depth **unlock gradually** as bandwidth and Knowledge Keywords increase.

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
* **Bunker UI:** utilitarian terminals, status boards, schedule planner; **Away‑Time Summary** panel when returning.
* **Prologue visuals:** CRT/teletype terminal readouts; UX grows in‑world as bandwidth expands.
* **World‑builder visuals:** symbolic map → wireframe grid → textured 2D; UI presents brushes, epoch sliders, and rule plaques.
* **Maker‑mode visuals:** blueprint overlays, ghost placement, connection gizmos, and flow/heat/traffic overlays; plan/elevation toggles for precise editing.
* **Tabletop visuals:** locked top‑down with **textures (not sprites)**; **3D character/key prop models** from a fixed camera; **portraits** for bonding; **z‑level overlays** & **height indicators**; **voxel‑like** dig cross‑sections; ambient life to reduce top‑down coldness.
* **Embodied/CRPG visuals:** top‑down/iso camera within a locked zoom band; readable silhouettes, portrait panels with expressions, dialog/bark system, interaction highlights; configurable text speed and accessibility toggles.
* **Party & Roster visuals:** party formation UI, **role icons**, **synergy web**, **bond/loyalty meters**, and collection/compendium cards with **lineage/heritage badges**.
* **Survival visuals:** inventory/equipment panels (paper‑doll), status/ailment icons, **weather/temperature overlays**, campfire/light cones, placement ghosts for shelters/workbenches.
* **Immersive‑sim visuals:** **Perception/Discovery** lens outlines and iconography, **reaction vectors** (arrows for flow/force), particle/decals for **heat/smoke/water**, circuit and linkage highlights; clean read of states (wet, charged, hot, damaged). **Perception/Discovery** lens outlines and iconography, **reaction vectors** (arrows for flow/force), particle/decals for **heat/smoke/water**, circuit and linkage highlights; clean read of states (wet, charged, hot, damaged).

---

## 7) Accessibility & UX

* Scalable text, color-blind safe palettes, input remap, motion options.
* “One new idea at a time” onboarding; tooltips and diegetic hints.
* **Survival assists:** optional **softer survival** presets, recipe hinting, and **auto‑stack** inventory tools; clear consent for harsh modes.
* **Real‑time clarity:** schedule editor with previews of likely outcomes; optional notifications; clear opt‑ins for away‑time processing.
* **Role‑switch clarity:** persistent HUD badges, short overlays describing control scope and what persists after you leave a body.
* **Maker‑mode UX:** snap/grid, param inspector, constraint hints, viability checks, staging area, **undo/redo**, and blueprint libraries.
* **Role‑switch clarity:** persistent HUD badges, short overlays describing control scope and what persists after you leave a body.
* Session respect: quick save everywhere; micro-goals designed for short play.
* **Content warnings & consent toggles** for coma/medical themes; tone controls for narrator presence.
* **Succession & death UX:** obituary/memento screens, heir selection with previews, legacy summaries; optional softer modes.
* **Discovery/Perception UX:** toggleable lens, color‑blind‑safe outlines, textual **why‑it‑worked** logs, and a **Try It** micro‑sandbox for experiments with previewed costs.

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
* **Risk:** **Real‑time pressure / unfairness** (players penalized for sleep/work/time‑zone).
  **Mitigation:** **Quiet hours**, **vacation mode**, catch‑up curves, and caps on negative drift; schedules simulate conservatively when away.
* **Risk:** **Offline exploits** (clock manipulation).
  **Mitigation:** Soft server/seed checksums, tolerance windows, and focusing rewards on **knowledge/blueprints** rather than scarce currencies.
* **Risk:** Player overwhelm.
  **Mitigation:** Optionality (Idle on/off, **Meta‑Progression guidance on/off**), smart defaults, gradual unlocks.
* **Risk:** **Identity/role confusion** (who am I controlling, where do changes apply?).
  **Mitigation:** Strong **role HUD**, color/FX per role, **one active embodiment** rule, and clear **scope previews** before actions finalize.
* **Risk:** **Control creep** (unlimited possession breaks sim).
  **Mitigation:** Enforce **Agency Budget**, cooldowns, and organization‑level delegation rather than micromanagement.
* **Risk:** **Creative sprawl / analysis paralysis.**
  **Mitigation:** Curated **starter kits**, goal prompts, and recipe cards; progressive disclosure of components; gentle auto‑suggested defaults.
* **Risk:** **Performance / scale creep** at planet scope.
  **Mitigation:** Planet **streaming & LOD**, perf budget meters, and hard caps per layer.
* **Risk:** **Degenerate designs** that trivialize systems.
  **Mitigation:** Physical and economic constraints, upkeep costs, and periodic balance passes.
* **Risk:** **Risk:** **UI complexity** in maker tools.
  **Mitigation:** Template‑first workflows, presets, and inline tutorials; “simple/advanced” toggles.
* **Risk:** **Power creep & synergy stacking** breaking balance.
  **Mitigation:** synergy caps, diminishing returns, and encounter scaling that reads the Synergy Graph.
* **Risk:** **Collection grind / pseudo‑gacha vibes.**
  **Mitigation:** no paid pulls, **fair acquisition** with pity systems, narrative‑based recruitment, and caps on duplicate filler.
* **Risk:** **Scale overwhelm** (hundreds → thousands under influence).
  **Mitigation:** cohort abstractions, **organization templates**, AI commanders, and workload budgets per tier.
  **Mitigation:** Template‑first workflows, presets, and inline tutorials; “simple/advanced” toggles.
* **Risk:** **Permadeath fatigue / loss aversion.**
  **Mitigation:** Strong **legacy systems** (mementos, heir previews, inheritance), difficulty sliders, and story‑protection toggles.
* **Risk:** **Lineage RNG frustration** (bad heir rolls).
  **Mitigation:** Limited **breeding/mentorship** influence, reroll tokens from Knowledge Keywords, and **doctrine** buffs.
* **Risk:** **Narrative dissonance / grind** from time chunking.
  **Mitigation:** **Epoch Focus Windows**, rich **auto‑summaries**, and optional vignette fast‑forwards.
* **Risk:** **Punitive survival loops** (death spirals, weather RNG).
  **Mitigation:** fail‑soft design, safe‑camp guarantees, forecast cues, and adjustable difficulty.
* **Risk:** **Crafting bloat / recipe overwhelm.**
  **Mitigation:** progressive disclosure, **starter kits**, search & favorites, and **Knowledge Keyword** hinting.
* **Risk:** **Inventory tedium.**
  **Mitigation:** smart stacks, weight/encumbrance clarity, quick‑craft and work order batching.
* **Risk:** **Combinatorial explosion** of interactions.
  **Mitigation:** tiered **Reaction Matrix**, clear **affordance grammar**, and hard caps per scene; prune rarely used combos.
* **Risk:** **Unintended exploits** trivializing challenges.
  **Mitigation:** systemic **costs/upkeep**, diminishing returns, and designer‑authored **guardrails** on edge cases.
* **Risk:** **Opacity** (players don’t understand why outcomes happen).
  **Mitigation:** **Causality Log**, perception hints, and repeatable testbeds with repro seeds.
* **Risk:** **Performance & determinism** under heavy physics.
  **Mitigation:** discrete‑step physics‑lite, reaction budgets, and deterministic replay for QA.

---

## 10) High-Level Technical Frame (engine-agnostic)

* **Core modules:**

  * **World Kernel:** terrain/biomes/time; save/versioning.
  * **Entity/Item System:** tagged data, recipes, stats.
  * **AI & Jobs:** schedulers (colony), simple planners.
  * **Resolution Engines:** TBT, Auto-Battler, TBS pluggable.
  * **Physics Lite:** interactions for ImmSim.
  * **UI Shell:** common widgets, map overlays, tooltip lore.
  * **Control Arbiter:** manages **ownership/possession windows**, concurrency, and **Agency Budget**.
  * **Role Router & Identity Ledger:** routes inputs per role (Meta‑Avatar/God/Incarnation) and records provenance of changes.
  * **Narrative Memory:** journals/diaries and memory trails that propagate into higher layers.
  * **Clock Service & Away‑Time Resolver:** real‑time scheduling, offline outcome simulation, quiet hours/vacation settings.
  * **World Genesis & Climate:** planet parameters, plate/erosion approximations, climate bands/biomes.
  * **History & Lineage Engine:** names, genealogies, migrations, era events; exports history to World State.
  * **Symbolic Map Renderer:** terminal/abstract cartography that upgrades toward textured 2D over time.
  * **ECS Runtime & Systems Graph:** data‑oriented ECS with a cross‑domain **systems graph** for power, fluids, traffic, ecology, and economy.
  * **Blueprint Studio & Construction Solver:** param inspector, constraint solving, and cost/time estimation for designs.
  * **Network & Logistics Graph:** multi‑layer pathing/flow with capacity and maintenance modeling.
  * **Planet Streaming & Chunking:** quadtree/patch LOD and streaming edits for **planet‑scale** builds.
  * **Top‑Down Tile Renderer & Procedural Texturing:** tile/mesh renderer with biome palettes, instancing, and decal layers.
  * **Z‑Layer & Voxel Dig Manager:** heightfields, contour/indicator generation, and underground cross‑sections.
  * **Model Impostor/LOD Batcher:** locked‑camera 3D models rendered efficiently for units and key props.
  * **Portrait & Relationship Hooks:** portrait generation pipeline with ties into traits/relationships.
  * **Incarnation Controller & Time Chunker:** embodiment switching, rate‑of‑time controls, and epoch focus windows for early eras.
  * **Lineage & Succession System:** inheritance rules, heir previews, legacy artifacts, mementos.
  * **Quest Weaver:** reads world flags (terrain, laws, myths, hazards, factions) to synthesize objectives and rewards.
  * **Organization & Doctrine Engine:** parties/guilds/clans with policies that interact with meta‑avatar auras.
  * **Physics & Reaction Graph:** deterministic, budgeted interactions across heat, electricity, fluids, pressure, and mechanics.
  * **Affordance Tagger & Inspector:** material/property tagging and runtime inspection.
  * **Perception/Discovery Lens & Experiment Harness:** overlays, hint tiers, scene cloning, repro seeds.
  * **Causality Logger & Replay:** why‑trace, debugging, and deterministic playback.
  * **Party AI & Tactics Roles:** role behaviors (tank/support/controller/striker), formation logic, and encounter scripting hooks.
  * **Synergy Graph & Training Pipeline:** runtime combo detection, mentor/apprentice scheduling, ability exchange rules.
  * **Influence Scaling & Control Manager:** abstracts control at scale and manages Agency Budget tradeoffs.
  * **Compendium/Collection Service:** roster provenance, set bonuses, and lineage metadata.

**4.9 Meta‑Progression Front‑End (Systems Spec)**

* **World permanence:** No automatic resets; only explicit **meta‑profile wipe** creates a new start.

* **Knowledge Keywords:** Collectible concept tags that combine into **recipes for cognition** (unlock UIs, advisors, research, diagnostics).

* **Blueprints & Functions:** Iterative unlocks for **features, systems, and tools**; cosmetic unlocks for expression.

* **Roster Progression:** Cross‑character perks; **meta‑avatar auras** affecting incarnations; organization doctrines.

* **Earning vs. Admin:** Unlocks are **earned in‑sim** (quests, discoveries, builds) but **administered here** (spend, equip, configure).

* **Gating surfaces:** Shows **BCI bandwidth** thresholds and hints at next calibrations.

* **Safeties:** Preview impacts, rollback windows, provenance in the **Identity Ledger**.

* **Testing:** simulation seeds, deterministic replays.

**4.10 Incarnation & Lineage Systems (Spec)**

* **Embodiment Rules:** one active body; swap via sanctioned points (shrines, camps, safehouses) or costly mid‑action interventions.

* **Control Resource:** extends **Agency Budget**—costs scale with party size, distance, and risk; regenerates via rest, rituals, or achievements.

* **Succession Toolkit:** heir selection UI with **inheritance previews** (traits, holdings, relationships, unfinished vows), **memento** creation, and obituary/journal entries.

* **Death & Legacy:** permadeath by default; difficulty options for **legacy carry‑over** and **story protection** toggles.

* **Quest Weaving:** pulls from World State API (myth tokens, law flags, resource scarcities) to produce arcs that feel authored but are systemic.

* **Time Chunking:** **Epoch Focus Windows** compress centuries early; expand to day/hour near key beats; player chooses focus cadence.

* **Content pipeline:** CSV/JSON tables → importers → prefabs.

* **Testing:** simulation seeds, deterministic replays.

---

## 11) Very High-Level Roadmap (release packages that feed forward)

> Each package is shippable on its own and **feeds** the next. You’ll still split each into smaller week-sized slices.

**RP-0 — Seed & Word**

* *Deliverables:* **Prologue digital novel** (earliest computer readouts), **primitive IF (CYOA → text adventure)**, Life Sim stats, optional Idle **(meta‑avatar only)**, **Meta‑Progression Front‑End**; **BCI calibration** scenes; “build‑it‑in‑front‑of‑you” narrator layer; **Meta‑Avatar creation v0**; **God training v0**; **Incarnation prototype** with Agency Budget & possession windows; **Bunker UI & Scheduler v0**; **Away‑Time Summary v0**.
* *Outcome:* World seed, first lore & knowledge tokens; working save/time; **diegetic justification for progression** established; **bandwidth meter** initialized; **role triad** (Meta‑Avatar / God / Incarnations) stood up with basic UI and save hooks; **real‑time loop** proven without sim‑idle.

**RP-1 — World from Above**

* *Deliverables:* **Abstract planet builder v0** (symbolic map + brushes), **World genesis tools** (planet params/biomes/resources), **Rule & Epoch controls**, **Lineage/Proto‑civilization text expeditions**, **Creative Sandbox toys**, **Blueprint Studio v0** (param templates, stamping, undo), **Construction Kits v0** (roads/power/water), **Network & Logistics Graph v0**, **Tabletop view v0** (locked top‑down, **z‑level overlay**, **height indicators**, **portrait panel**, early **3D character impostors**).
* *Outcome:* Seeded **heightmaps/biomemaps**, early **history events & lineage trees**, **rule flags** and **myth tokens**; **readable grid** with symbolic → wireframe progression; world ready for **incarnation** and downstream Colony/CRPG layers.

**RP-2 — Step Into the World**

* *Deliverables:* CRPG/WRPG **embodiment v0** (single body), **Incarnation Controller v0**, **Lineage & Succession v0** (heir preview, legacy traits), **Party control via Agency Budget v0**, **Survival‑Crafting loop v0** (isolated start scenario, core survival stats, camp & basic workbenches, small crafting chains), Immersive‑Sim interactions v0 (physics‑lite reactions, locks/power/fluid puzzles), **Perception Mode v0**, **Idea Alchemy v0** (knowledge keyword combos), **Reaction Matrix v0**, **Quest Weaver v0**, **Time Chunker v0**.
* *Outcome:* A 10–15 min **embodied** slice from early humans onward with **succession** to a designated heir; quests generated from existing world flags; clear feel of **death → legacy → continuity** rather than reset.

**RP-3 — Parties & Tactics**

* *Deliverables:* **JRPG party systems v0** (recruitment → persuasion → cohort), **party comp UI v0** (roles, formation, synergy web), **training/mentorship loops v0**, **multi‑control via Agency Budget v0** (costs & cooldowns), **Compendium v0**, Turn‑Based Tactics encounters (uses Tabletop).
* *Outcome:* Parties grow from **one** to a **small team**; players feel the **synergy & mentorship** loop; organizations gain first policies; TBT missions showcase formation/role combos.

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
