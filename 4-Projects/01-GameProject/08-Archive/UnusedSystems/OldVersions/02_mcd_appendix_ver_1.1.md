# **Appendix: Complete Idea Inventory**

This appendix contains a comprehensive, line-item breakdown of every concept, mechanic, and narrative point from the original source documents (concept\_document\_rough\_draft.md and foundational\_context.md). It is organized by the sections established in the Master Concept Document for easy reference.

### **Part I: Foundational Concepts & Vision**

#### **1\. Project Vision & Core Pillars**

* It is a decades-scale, solo-built game that **ascends across genres**.  
* It lets players **create a world, then step into it**, zooming up and down scales as systems persist.  
* The core idea is to play the **history of games and civilizations** as one coherent experience.  
* The progression is summarized as: **words → life → creation → embodiment → settlement → city → region → globe**.  
* The target audience is players who love systemic sandboxes, builder/strategy layers, and role-playing.  
* It also targets tinkerers who value emergent stories and long-term progression.  
* The initial platform is PC.  
* **Create first, inhabit later:** Shape the world as a god, then become a character who lives in what you made.  
* **Persistent causality:** Actions at one layer **meaningfully persist** into the next (e.g., terrain, economies, reputations, myths).  
* **Genre ladder:** Each new release unlocks a **fresh genre lens** without discarding previous layers.  
* **Play how you like:** It is a freeform, **creative sandbox** with optional challenges and structural modes (e.g., idle, roguelike runs).  
* **Design Principle 1\. Clarity over clutter:** Simple rule sets that rhyme across scales.  
* **Design Principle 2\. Elegant depth:** Few mechanics, rich combinations.  
* **Design Principle 3\. Unified grammar:** Consistent inputs, resources, and feedback at every layer.  
* **Design Principle 4\. Diegetic continuity:** The world explains itself; systems feel in-world.  
* **Design Principle 5\. Solo-dev feasibility:** Incremental slices, reusable tech, data-driven content.  
* **Design Principle 6\. Player agency:** Creation and meaningful choice trump scripted outcomes.

#### **2\. Game Premise & Narrative Framework**

* The game is presented as a project where the player builds a simulation in concert with the developer-character.  
* The developer-character will build the game in front of the player's eyes, with their participation.  
* The developer-character will acknowledge being a complete novice, justifying why the experience starts simply.  
* Initially, the developer-character states they cannot offer a game yet, only a story.  
* The player character (meta-avatar) is trapped in a "bunker" with the developer-character.  
* The developer-character will address the player as "myself" but is a character living in a post-apocalyptic world.  
* The player starts the experience by reading stories provided by the developer-character in their bunker room.  
* The player is told the life they believe is real is an illusion created by a Brain-Computer Interface (BCI).  
* The BCI is being used to keep the player "healthy," "stimulated," and "alive" during a coma.  
* The stories the player reads are initially presented as fiction but are secretly about the real world where their comatose body is stored.  
* This "real world" has experienced a societal collapse.  
* The first reveal is that the seemingly disconnected stories are all connected.  
* The second reveal is that the developer-character lives on the Earth-like planet described in the stories, not the historical Earth.  
* The stories will describe pockets of technology in the collapsed society, including primitive BCI for coma patients.  
* The final reveal occurs when the player realizes they are a coma patient and their life is a BCI-generated illusion.  
* The central purpose of building the simulation is to help understand the player's comatose condition and potentially revive them.  
* Player participation provides brain data that will lead to a better understanding of how the brain works.  
* The game's primitive starting point is justified by the limited complexity the BCI can initially transmit to the player's mind.  
* The creation of the simulation universe space begins inside the bunker after the narrative reveals, starting the God Game portion.
* Bunker Loop: The initial gameplay follows a clear loop: the player returns to their room, reads short stories provided by the developer-character, uncovers narrative breadcrumbs, and eventually unlocks the world-builder.
* Sequence of Reveals: The core narrative reveals are delivered in a specific order: (1) the seemingly disconnected stories are all part of a single history, (2) the world described is not historical Earth, but an Earth-like planet, and finally (3) the player is a coma patient connected to a BCI.
* BCI Calibration: The gradual unlocking of game features is diegetically explained as "BCI calibration beats," which increase the bandwidth and allow more complex experiences to be transmitted.
* Content & Tone Controls: The game will include content warnings and consent toggles for its medical and coma-related themes, as well as optional controls for the "novice developer" commentary.
* Developer Commentary: Between story-reading sessions, the developer-character will provide diegetic updates on their current work and progress, reinforcing the collaborative, in-progress nature of the project.

#### **3\. The Player's Roles & Agency**

* The player has different character roles in the game.  
* The player will create a character that they are encouraged to make a digital reflection of themselves (the Meta-Avatar).  
* The meta-avatar exists outside of the simulation world, knows about the simulation, and interacts with it from the outside.  
* The meta-avatar lives in a "bunker" and will age and perform actions there.  
* Time for the meta-avatar will be in real-time, managed by a schedule according to the real-world clock.  
* The meta-avatar's progression is tied to a meta-progression system on par with the breadth of Owlcat games.  
* This includes a knowledge keyword system to build their brain.  
* All simulation expansions (blueprints, features, etc.) are unlocked through this meta-character's progression.  
* The player will create a God that they will control, with more control in the beginning and less over time.  
* The God portion functions as a dynasty simulator, history simulator, and planet builder.  
* The player can jump in and out of controlling NPCs in the simulation.  
* A controlled NPC becomes a version of the player for a period of time or for the character's entire life.  
* The meta-character's progression will affect the NPCs they control.  
* The player will eventually establish their own personal lineage and a series of "main" in-simulation characters.  
* The player will be able to spend a resource to take control of party members.  
* The party can grow to the size of an organization and even a nation.  
* The scale of control can grow from tens to hundreds of thousands of individuals.

### **Part II: Gameplay Systems & Mechanics**

#### **4\. The Two Worlds: Meta vs. Simulation**

* The Meta-Game layer functions as a life sim for the meta-avatar in the "bunker".  
* Time for the meta-avatar is in real-time, tied to the real-world clock.  
* The meta-avatar continues its schedule and can develop or regress while the player is away.  
* Optional idle/incremental mechanics provide background progression loops for the meta-avatar only.  
* The "Roguelike Front-End" is the name for the meta-progression system, not procedural runs.  
* This meta-system is intended to be the most expansive unlock system in gaming history.  
* The player controls when ticks are processed in the simulation world; there are no idle mechanics in the simulation.  
* The simulation is a true sandbox game where a whole planet can be manipulated over time.  
* The game world will be governed by systems that combine to create an enormous variety of emergent behaviors.  
* The design will use ECS (Entity Component System) principles.  
* Players can create blueprints for standard designs to reuse.
* Away-Time Resolver: The meta-game's offline progression includes features like setting quiet hours or vacation modes to prevent negative drift, and a returning "Away-Time Summary" that the player can accept or perform a limited rollback on.
* Meta-Profile Administration: The player will have access to administrative functions for their meta-profile, including backup/export options and a formal, explicit full-wipe function, which is the only way to reset the game's canonical timeline.
* The player controls when ticks are processed in the simulation world; there are no idle mechanics in the simulation.

#### **5\. Core World Systems**

* The design prefers simple rule sets that rhyme across scales ("Clarity over clutter").  
* The goal is elegant depth, with few mechanics leading to rich combinations.  
* The world is designed to explain itself ("Diegetic continuity").  
* A complex discovery mini-mode will be implemented, like a more complicated version of Skyrim's alchemy applied to everything.  
* A "Unified grammar" ensures consistent resources, inputs, and feedback at every layer.  
* The simulation uses Unified Resource Tokens: Time, Energy, Materials, Knowledge, Influence/Reputation, Population.  
* Content is data-driven; entities (biomes, items, etc.) are defined as tagged data.  
* The game has one canonical timeline.  
* The core "Continuity rule" is that *Nothing is throwaway*.
* World State API: The "thin" API governing persistence between layers will track a core set of data, including: terrain/biomes/resources; entities/tags; items/recipes; history events; myth/law flags; lineage trees; and save provenance/versioning.
* Discovery Grammar: The "Idea Alchemy" discovery system works by combining elements, such as [Material] + [Method] + [Concept] to generate a new recipe or practice.
* Unified Lexicon: The unified grammar will be built on a consistent lexicon of verbs, such as Inspect, Place, Route, and Craft, which function predictably at all scales.

#### **6\. The Genre Ladder: A Progression of Lenses**

> * **Digital Novel / Text RPG:** The experience begins with primitive computer readouts, evolving into interactive fiction (CYOA) and text adventures to establish foundational lore and map seeds.
> * **God Simulation (World Builder):**
>     * Visuals ramp from symbolic representations to wireframes and finally to textured 2D.
>     * The player controls "epoch ticks" that advance climate, biota, and geological hazards.
>     * The player establishes foundational rules and constraints (both natural and cultural).
>     * During this phase, the player can inhabit "proto-humans" in text-based adventures on symbolic maps as early history and lineages develop.
>     * The primary output of this phase is the world's heightmaps, biome maps, initial history events, and myth/law tokens for the simulation to read later.
> * **CRPG / WRPG (Incarnate):**
>     * Features a dedicated **Incarnation Controller** and a **Time Chunker** to manage play sessions focused on specific epochs.
>     * A **Succession Toolkit** provides heir previews, mementos, and obituaries to manage the lineage system.
>     * A **Quest Weaver** system dynamically generates objectives by reading world data like terrain, laws, myths, and faction states.
> * **Survival-Crafting:**
>     * Begins with an isolated start vignette.
>     * Models survival variables like temperature, hunger/thirst, fatigue, and injury.
>     * Features a deep resource graph (harvest → process → component → item) utilizing workbenches and item quality/durability.
> * **Immersive Sim (Physics-Driven):**
>     * A **Perception/Discovery Lens** allows the player to inspect objects and a **Reaction Matrix** governs how heat, electricity, fluids, and pressure interact.
>     * An **Experiment Harness** provides a safe, clone testbed environment, and a **Causality Log** tracks the results of systemic interactions.
> * **JRPG Party Mechanics:**
>     * Follows a recruitment ladder (meet → persuade → cohort → controlled).
>     * A **Synergy Graph** tracks character relationships, mentorship, and training opportunities.
>     * Characters are tracked in a **Compendium** to reinforce the "collection" feel.
> * **Turn-Based Tactics (TBT):** Governs all small-squad actions with an action-point economy.
> * **Colony Simulation:** Introduces settlers with needs, jobs, schedules, and hazards.
> * **Tower Defense:** Used for resolving defensive events like raids and disasters.
> * **Open-World RPG:** Introduces world traversal, factions, and vehicles, with movement being tick-based rather than reaction-based.
> * **Construction & Management Sim:** Focuses on logistics, a **Blueprint Studio**, and managing networks (roads, power, etc.).
> * **City Builder:** Includes zoning, traffic, utilities, and policy knobs.
> * **Tycoon / Business Sim:** Introduces markets, firms, and supply chains.
> * **Auto-Battler:** Resolves mid-scale conflicts (hundreds of units).
> * **Turn-Based Strategy (TBS):** Resolves large-scale battles (thousands of units) with a focus on supply and attrition.
> * **Grand Strategy:** A fully abstracted world stage for global politics and diplomacy.

#### **7\. Character & Faction Systems**

* The game functions as a lineage simulator where characters will die.  
* Population is a core, unified resource token.  
* Settlers and characters have needs, jobs, schedules, pathing, and can be affected by hazards.  
* Characters will have a "collection" feel, similar to GI Joe or Pokemon.  
* Each character is unique and part of a lineage and race with unique histories.  
* The player will eventually establish their own personal lineage of "main" characters.  
* There will be a complex system for characters and NPCs to provide synergies and train each other.  
* The party can grow to the size of an organization and even a nation.  
* The scale of control can grow from tens to hundreds of thousands of individuals.  
* Factions will be a feature of the world.
The player's primary lineage of "main" characters begins with an isolated survival-in-nature vignette, tying the start of their generational story directly to the Survival-Crafting layer of the game.

#### **8\. Construction, Crafting, & Economy**

* Crafting functions as the early type of manufacturing and has an enormous crafting tree.  
* A full mining, refining, transport, and manufacturing system will be implemented at the city level.  
* Construction is a major aspect of the game and is key to large-scale success.  
* Players can create blueprints for standard designs to reuse.  
* A mastery system will allow players to delegate more management tasks as they master them.  
* The City Builder layer includes zoning, traffic, and utilities.  
* The Tycoon / Business Sim layer introduces markets, firms, supply chains, and price dynamics.

#### **9\. Conflict & Resolution**

* The game uses a stack of pluggable Resolution Engines based on encounter scale.  
* Turn-Based Tactics (TBT) is used for small tactical encounters and governs *all* character actions.  
* Tower Defense is used for defensive events like raids and disasters.  
* The Auto-Battler is used for mid-scale conflicts involving hundreds of units.  
* Turn-Based Strategy (TBS) is used for large-scale battles involving thousands of units.

### **Part III: Presentation & Player Experience**

#### **10\. Art, Presentation, & Game Views**

* The art direction is readable, stylized, and uses textured 2D on a grid.  
* The primary perspective is top-down, possibly with a 3/4 angle.  
* 3D models will be used for characters and key pieces from a locked perspective.  
* Emotive 2D character portraits will be used to build player bonds.  
* Visuals will start in the simplest possible format and be incrementally upgraded via meta-game unlocks.  
* There are Four Primary Views: Tactical, City, Regional, and Global.  
* The Tactical View's zoom level is compared to Rimworld, though it will use a textured art style rather than a sprite-based one.
* Tabletop View Specifics: The tactical view will use a locked top-down perspective with textured environments (not sprites), 3D models for characters/key props rendered as impostors, 2D portraits for emotional connection, z-level overlays for height, voxel-style cross-sections for digging, and ambient decals to make the world feel lived-in.


#### **11\. User Interface (UI) & User Experience (UX)**

* A "Unified grammar" ensures consistent inputs, resources, and feedback at every layer.  
* The UI will have a consistent lexicon (e.g., Inspect, Place, Craft).  
* Onboarding will follow a “one new idea at a time” principle.  
* The game will feature scalable text, color-blind safe palettes, and full input remapping.  
* The design shows "Session respect" with micro-goals for short play sessions and the ability to quick-save everywhere.
* Role & Time Clarity: The HUD will feature clear role badges (Meta/God/Incarnate) and overlays to explain what state persists when the player leaves a body.
* Succession & Death UX: The UI will include obituary and memento screens, heir previews, and legacy summaries to make the lineage system meaningful.
* Discovery & Perception UX: The UI will use color-blind-safe outlines, tiered hints, a "why-it-worked" log, and a "Try-It" micro-sandbox for the Idea Alchemy system.
* Survival Assists: The UI will include clear overlays for weather/temperature effects, auto-stacking inventory, and recipe hinting to reduce friction.

#### **12\. Audio Design**

* Audio design is "feedback-first."  
* Soft musical motifs will recur across the different scales of play.  
* The game will use the same core "theme" but with different instrumentation depending on the scale.

### **Part IV: Production & Development**

#### **13\. Technical Framework & Architecture**

* The design is engine-agnostic and PC-first.  
* The architecture will use ECS (Entity Component System) principles.  
* The map is a tick-based, tile system.  
* The content pipeline is: CSV/JSON tables → importers → prefabs.  
* Testing will be conducted using simulation seeds and deterministic replays.
> * **Core Architecture:** The game is built on a series of modular, reusable components using ECS principles. Key modules include:
>     * **World & History:** World Genesis & Climate, History & Lineage Engine, Planet Streaming & Chunking.
>     * **Control & Identity:** Control Arbiter, Role Router, Identity Ledger, Narrative Memory.
>     * **Time & Meta:** Clock Service & Away-Time Resolver.
>     * **Characters & Scale:** Party AI & Tactics Roles, Synergy Graph & Training Pipeline, Influence Scaling & Control Manager.
>     * **Immersive-Sim:** Physics & Reaction Graph, Affordance Tagger & Inspector, Perception/Experiment Harness, Causality Logger.
>     * **Maker Systems:** Blueprint Studio & Construction Solver, Network & Logistics Graph.
>     * **Rendering:** Top-Down Tile Renderer, Z-Layer/Voxel Dig Manager, Model Impostor/LOD Batcher.

#### **14\. Development Roadmap & Release Plan**

* The roadmap is broken into shippable Release Packages (RPs) that feed forward.  
* Each package is designed to be shippable on its own.  
* The roadmap progresses from RP-0 (Seed & Word) to RP-10 (Region & World).  
* Each package has four quality gates: Playtestable, Content-Complete, Stabilized, and Certified.

#### **15\. Scope, Risks, & Mitigations**

* The development will prefer **systems over content** and reuse patterns.  
* **Risk: Feature Sprawl** → Mitigation: Hard caps on mechanics per layer.  
* **Risk: Persistence Complexity** → Mitigation: A thin "World State API."  
* **Risk: Developer Burnout** → Mitigation: Work in "area slices" and alternate task complexity.  
* **Risk: Player Overwhelm** → Mitigation: Optionality of complex systems, smart defaults, and gradual unlocks.
* **Risk: Creative Sprawl / Analysis Paralysis** → Mitigation: Provide curated starter kits and "recipe cards" for common designs; use progressive disclosure to introduce systems gradually.
> * **Risk: Performance at Planet Scale** → Mitigation: Heavy reliance on streaming, LODs, and hard performance budgets per system.
> * **Risk: Permadeath Fatigue / Lineage RNG** → Mitigation: Strong legacy carryover, meta-currency to reroll heirs, and clear heir previews.
> * **Risk: Combinatorial Explosion (ImmSim)** → Mitigation: Use a tiered reaction matrix and a clear "affordance grammar" to limit interactions to what is meaningful.
> * **Risk: Opacity / Lack of Feedback** → Mitigation: The Causality Log, perception hints, and reproducible testbeds will allow players to understand *why* things happened.
> * **Risk: Offline Clock Exploits (Meta-Game)** → Mitigation: Use server-side seed checks and tolerance windows; focus rewards on knowledge and blueprints rather than farmable currency.

#### **16\. Success Criteria**

* Every release package **stands alone** yet **enriches** the next.  
* Players can **feel** the continuity of their actions across all layers.  
* The project can continue shipping **small, satisfying slices** for years.