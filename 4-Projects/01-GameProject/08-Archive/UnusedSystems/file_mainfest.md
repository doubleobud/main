/OMEGA
├── 00_Admin_Biz
│   ├── 01_ProgramManagement
│   │   ├── Roadmaps
│   │   ├── Milestones
│   │   ├── Risks
│   │   ├── StatusReports
│   │   └── OKRs
│   ├── 02_HR_Onboarding
│   │   ├── Roles
│   │   ├── Hiring
│   │   ├── Training
│   │   ├── Policies
│   │   └── OrgCharts
│   ├── 03_Finance
│   │   ├── Budgets
│   │   ├── Forecasts
│   │   ├── Invoices
│   │   ├── Purchases
│   │   └── Grants
│   └── 04_Partners_Vendors
│       ├── Contracts
│       ├── NDAs
│       ├── SOWs
│       ├── Contacts
│       └── SLAs
├── 01_Production
│   ├── 01_Planning
│   │   ├── Roadmaps
│   │   ├── Backlogs
│   │   ├── SprintBoards
│   │   ├── Staffing
│   │   └── Dependencies
│   ├── 02_Tracking
│   │   ├── Standups
│   │   ├── Reviews
│   │   ├── Retros
│   │   ├── Burndowns
│   │   └── KPIs
│   └── 03_Reports
│       ├── Exec
│       ├── Milestones
│       ├── Risks
│       ├── Budgets
│       └── Compliance
│── 02_Design
│   ├── 00_Index_Taxonomy
│   │ ├── DesignIndex.yaml # authoritative list of docs & parents
│   │ ├── Tags.yaml # controlled vocabulary
│   │ └── Glossary.md
│   ├── 01_GDDs # working, evolving; one parent per doc
│   │ ├── 00_Vision
│   │ │ ├── Vision.md
│   │ │ └── Audience_Constraints.md
│   │ ├── 01_Pillars
│   │ │ ├── Experience_Pillars.md
│   │ │ └── Quality_Bars.md
│   │ ├── 02_Systems
│   │ │ ├── Combat_GDD.md
│   │ │ ├── Progression_GDD.md
│   │ │ ├── Economy_GDD.md
│   │ │ ├── Narrative_GDD.md
│   │ │ └── World_GDD.md
│   │ └── 03_Features # features grouped under their owning system
│   │ ├── Combat
│   │ │ ├── Weapons_Feature.md
│   │ │ ├── Cover_Feature.md
│   │ │ └── Enemies_Feature.md
│   │ └── Progression
│   │ ├── SkillTrees_Feature.md
│   │ └── Achievements_Feature.md
│   ├── 02_Specs # precise specs that implement GDD intent
│   │ ├── Systems
│   │ │ ├── Combat_Spec.md
│   │ │ └── Progression_Spec.md
│   │ └── Features
│   │ ├── Combat_Weapons_Spec.md
│   │ └── Progression_SkillTrees_Spec.md
│   ├── 03_Prototypes
│   │ ├── Paper
│   │ ├── Greybox
│   │ └── UX_Clickthroughs
│   ├── 04_Components # physical level 4; each Component file can contain Elements
│   │ ├── Combat
│   │ │ ├── Recoil_Component.md
│   │ │ ├── HitScan_Component.md
│   │ │ └── Damage_Model_Component.md
│   │ └── Progression
│   │ ├── XP_Curve_Component.md
│   │ └── Reward_Table_Component.md
│   ├── 05_Templates # canonical authoring templates
│   │ ├── Vision_Template.md
│   │ ├── Pillar_Template.md
│   │ ├── System_Template.md
│   │ ├── Feature_Template.md
│   │ ├── Component_Template.md
│   │ └── Spec_Template.md
│   ├── 06_Manifests # machine-parsable indices for AI
│   │ ├── design_manifest.yaml
│   │ └── design_manifest.json
│   ├── 07_AI_Context # pre-built “context packs” for GPT
│   │ ├── Packs
│   │ │ ├── Combat_Build_Pack.md
│   │ │ └── Progression_Balance_Pack.md
│   │ └── Recipes
│   │ └── Context_Assembly_Recipes.md
│   └── 08_Conventions
│   ├── Naming_IDs.md
│   ├── Linking_Graph.md
│   ├── Versioning_Policy.md
│   └── Authoring_Guide.md
├── 03_Narrative
│   ├── 01_Lore
│   │   ├── Timeline
│   │   ├── Worldbuilding
│   │   ├── Factions
│   │   ├── Cosmology
│   │   └── TechLevels
│   ├── 02_Scripts
│   │   ├── Quests
│   │   ├── Cutscenes
│   │   ├── Barks
│   │   ├── Branching
│   │   └── Variables
│   ├── 03_CharacterBibles
│   │   ├── Heroes
│   │   ├── Villains
│   │   ├── NPCs
│   │   ├── Races
│   │   └── Cultures
│   └── 04_Tools
│       ├── Twine
│       ├── Ink
│       ├── DialogueGraph
│       ├── LocalizationTags
│       └── VO_Cues
├── 04_Engineering
│   ├── 01_Client
│   │   ├── Rendering
│   │   ├── Gameplay
│   │   ├── Input
│   │   ├── UI
│   │   └── SaveLoad
│   ├── 02_Server
│   │   ├── GameServer
│   │   ├── Matchmaking
│   │   ├── Persistence
│   │   ├── Chat
│   │   └── Social
│   ├── 03_Engine
│   │   ├── Core
│   │   ├── Physics
│   │   ├── Audio
│   │   ├── Scripting
│   │   └── Editor
│   └── 04_Scripting
│       ├── Lua
│       ├── Python
│       ├── CSharp
│       ├── UnrealBP
│       └── Automation
├── 05_Content
│   ├── 01_Genres_Action
│   │   ├── FPS
│   │   ├── TPS
│   │   ├── BeatEmUp
│   │   ├── Platformer
│   │   └── Stealth
│   ├── 02_Genres_Adventure
│   │   ├── Narrative
│   │   ├── Metroidvania
│   │   ├── VisualNovel
│   │   ├── InteractiveFiction
│   │   └── WalkingSim
│   ├── 03_Genres_RPG
│   │   ├── JRPG
│   │   ├── ARPG
│   │   ├── WRPG
│   │   ├── TacticsRPG
│   │   └── Soulslike
│   ├── 04_Genres_Strategy
│   │   ├── RTS
│   │   ├── 4X
│   │   ├── GrandStrategy
│   │   ├── TBS
│   │   └── TowerDefense
│   ├── 05_Genres_Sim
│   │   ├── LifeSim
│   │   ├── CityBuilder
│   │   ├── Tycoon
│   │   ├── Farming
│   │   └── Flight
│   ├── 06_Genres_Sports_Racing
│   │   ├── Sports
│   │   ├── ArcadeRacing
│   │   ├── SimRacing
│   │   ├── Kart
│   │   └── VehicularCombat
│   ├── 07_Genres_Puzzle_Party
│   │   ├── Puzzle
│   │   ├── Party
│   │   ├── Trivia
│   │   ├── BoardCard
│   │   └── Idle
│   ├── 08_Genres_Survival_Horror
│   │   ├── Survival
│   │   ├── Horror
│   │   ├── BattleRoyale
│   │   ├── Roguelike
│   │   └── Extraction
│   └── 09_Genres_Edu_Music_Other
│       ├── Educational
│       ├── MusicRhythm
│       ├── Sandbox
│       ├── MMO
│       └── ARGS
├── 06_Art
│   ├── 01_2D
│   │   ├── Concepts
│   │   ├── Textures
│   │   ├── UI
│   │   └── Sprites
│   ├── 02_3D
│   │   ├── Characters
│   │   ├── Environments
│   │   ├── Props
│   │   ├── Vehicles
│   │   └── Weapons
│   ├── 03_TechArt
│   │   ├── VFX
│   │   ├── Shaders
│   │   ├── Materials
│   │   ├── Rigging
│   │   └── Tools
│   └── 04_Photogrammetry
│       ├── RawScans
│       ├── Cleaned
│       ├── Atlases
│       ├── Calibration
│       └── Reference
├── 07_Audio
│   ├── 01_SFX
│   │   ├── Foley
│   │   ├── Combat
│   │   ├── UI
│   │   ├── Ambience
│   │   └── Vehicles
│   ├── 02_Music
│   │   ├── Themes
│   │   ├── Stems
│   │   ├── Loops
│   │   ├── MIDI
│   │   └── SheetMusic
│   ├── 03_VO
│   │   ├── Cast
│   │   ├── Languages
│   │   ├── Processing
│   │   ├── Pickups
│   │   └── ADR
│   └── 04_Middleware
│       ├── Wwise
│       ├── FMOD
│       ├── Integration
│       ├── Banks
│       └── Profiles
├── 08_UI_UX
│   ├── 01_Flows
│   │   ├── Onboarding
│   │   ├── HUD
│   │   ├── Menus
│   │   ├── Settings
│   │   └── Store
│   ├── 02_Wireframes
│   │   ├── Mobile
│   │   ├── Console
│   │   ├── PC
│   │   ├── VR
│   │   └── Web
│   └── 03_Prototypes
│       ├── Clickable
│       ├── Greybox
│       ├── Animations
│       ├── UsabilityStudies
│       └── Iterations
├── 09_Worlds_Levels
│   ├── 01_Procedural
│   │   ├── Generators
│   │   ├── Seeds
│   │   ├── Rulesets
│   │   ├── Biomes
│   │   └── Validation
│   ├── 02_Handcrafted
│   │   ├── Graybox
│   │   ├── Blockout
│   │   ├── Final
│   │   ├── Lighting
│   │   └── Optimization
│   ├── 03_Tilesets
│   │   ├── Terrain
│   │   ├── Urban
│   │   ├── Dungeon
│   │   ├── Space
│   │   └── Underwater
│   └── 04_LevelKits
│       ├── Props
│       ├── Materials
│       ├── Decals
│       ├── ReusablePrefabs
│       └── ReferenceScenes
├── 10_Game_Systems
│   ├── 01_Movement
│   │   ├── Parkour
│   │   ├── Vehicles
│   │   ├── Flight
│   │   ├── Swimming
│   │   └── Mounts
│   ├── 02_Combat
│   │   ├── Melee
│   │   ├── Ranged
│   │   ├── Magic
│   │   ├── Cover
│   │   └── Combo
│   ├── 03_Progression
│   │   ├── XP
│   │   ├── SkillTrees
│   │   ├── Crafting
│   │   ├── Quests
│   │   └── Factions
│   └── 04_Interaction
│       ├── Dialogue
│       ├── Inventory
│       ├── Minigames
│       ├── Building
│       └── Camera
├── 11_AI_NPCs
│   ├── 01_Behavior
│   │   ├── BehaviorTrees
│   │   ├── UtilityAI
│   │   ├── GOAP
│   │   ├── StateMachines
│   │   └── Blackboards
│   ├── 02_Perception
│   │   ├── Vision
│   │   ├── Audio
│   │   ├── Smell
│   │   ├── Touch
│   │   └── Sensors
│   ├── 03_Navigation
│   │   ├── NavMesh
│   │   ├── Crowd
│   │   ├── Pathfinding
│   │   ├── Cover
│   │   └── LocalAvoidance
│   └── 04_ML
│       ├── Imitation
│       ├── RL
│       ├── PCG
│       ├── AnomalyDetection
│       └── Tools
├── 12_Physics_Sim
│   ├── 01_Rigid
│   │   ├── Colliders
│   │   ├── Constraints
│   │   ├── Destruction
│   │   ├── Vehicles
│   │   └── Ragdolls
│   ├── 02_Soft
│   │   ├── Cloth
│   │   ├── Hair
│   │   ├── Fluids
│   │   ├── Gels
│   │   └── Deformables
│   └── 03_Environmental
│       ├── Weather
│       ├── Ocean
│       ├── Fire
│       ├── Terrain
│       └── Volumetrics
├── 13_Network_Backend
│   ├── 01_Services
│   │   ├── Matchmaking
│   │   ├── Presence
│   │   ├── Chat
│   │   ├── Inventory
│   │   └── Leaderboards
│   ├── 02_Infrastructure
│   │   ├── Kubernetes
│   │   ├── Terraform
│   │   ├── Observability
│   │   ├── Scaling
│   │   └── Cost
│   ├── 03_APIs
│   │   ├── GraphQL
│   │   ├── REST
│   │   ├── WebSockets
│   │   ├── gRPC
│   │   └── SDKs
│   └── 04_DataStores
│       ├── SQL
│       ├── NoSQL
│       ├── Caches
│       ├── Blobs
│       └── AnalyticsExport
├── 14_Platforms_Ports
│   ├── 01_PC
│   │   ├── Windows
│   │   ├── Linux
│   │   └── macOS
│   ├── 02_Console
│   │   ├── PlayStation
│   │   ├── Xbox
│   │   └── Nintendo
│   ├── 03_Mobile
│   │   ├── iOS
│   │   ├── Android
│   │   └── Handhelds
│   ├── 04_Web
│   │   ├── WebGL
│   │   ├── WebGPU
│   │   └── WASM
│   └── 05_Cloud
│       ├── GeForceNOW
│       ├── xCloud
│       ├── Luna
│       └── Custom
├── 15_Build_CI
│   ├── 01_Pipelines
│   │   ├── Jenkins
│   │   ├── GitHubActions
│   │   ├── GitLabCI
│   │   ├── TeamCity
│   │   └── AzurePipelines
│   ├── 02_Builds
│   │   ├── Nightly
│   │   ├── RC
│   │   ├── Release
│   │   ├── Hotfix
│   │   └── Experimental
│   ├── 03_Distribution
│   │   ├── Internal
│   │   ├── External
│   │   ├── QA
│   │   ├── Marketing
│   │   └── Partners
│   └── 04_Symbols_Crash
│       ├── Symbols
│       ├── CrashDumps
│       ├── Minidumps
│       ├── Reports
│       └── Telemetry
├── 16_QA_Testing
│   ├── 01_TestPlans
│   │   ├── Master
│   │   ├── Regression
│   │   ├── Smoke
│   │   ├── Soak
│   │   └── Platform
│   ├── 02_TestCases
│   │   ├── Functional
│   │   ├── NonFunctional
│   │   ├── Accessibility
│   │   ├── Localization
│   │   └── Compliance
│   ├── 03_Automation
│   │   ├── Unit
│   │   ├── Integration
│   │   ├── EndToEnd
│   │   ├── Load
│   │   └── Scripts
│   └── 04_BugTracking
│       ├── Triages
│       ├── Reports
│       ├── ReproCases
│       ├── Screenshots
│       └── CrashDumps
├── 17_Performance_Optimization
│   ├── 01_Profiling
│   │   ├── CPU
│   │   ├── GPU
│   │   ├── Memory
│   │   ├── IO
│   │   └── Network
│   ├── 02_Budgets
│   │   ├── Polycount
│   │   ├── Texture
│   │   ├── DrawCalls
│   │   ├── Audio
│   │   └── Platform
│   └── 03_Guides
│       ├── Mobile
│       ├── Console
│       ├── PC
│       ├── VR
│       └── Web
├── 18_Accessibility
│   ├── 01_Guidelines
│   │   ├── Visual
│   │   ├── Audio
│   │   ├── Motor
│   │   ├── Cognitive
│   │   └── Subtitles
│   ├── 02_Tooling
│   │   ├── Checklists
│   │   ├── Simulators
│   │   ├── TestScenes
│   │   ├── Telemetry
│   │   └── Reports
│   └── 03_Advocacy
│       ├── Research
│       ├── Playtests
│       ├── Feedback
│       ├── Vendors
│       └── Outreach
├── 19_Localization
│   ├── 01_SourceStrings
│   │   ├── Gameplay
│   │   ├── UI
│   │   ├── Narrative
│   │   ├── Store
│   │   └── Marketing
│   ├── 02_Locales
│   │   ├── en-US
│   │   ├── fr-FR
│   │   ├── es-ES
│   │   ├── zh-CN
│   │   └── ja-JP
│   ├── 03_LQA
│   │   ├── Plans
│   │   ├── Reports
│   │   ├── Screenshots
│   │   ├── Audio
│   │   └── Fixes
│   └── 04_Vendors
│       ├── Contracts
│       ├── StyleGuides
│       ├── Glossaries
│       ├── TMs
│       └── Invoices
├── 20_Analytics
│   ├── 01_Schemas
│   │   ├── GameplayEvents
│   │   ├── EconomyEvents
│   │   ├── PerformanceEvents
│   │   ├── ErrorEvents
│   │   └── Privacy
│   ├── 02_Pipelines
│   │   ├── ETL
│   │   ├── Streaming
│   │   ├── Warehousing
│   │   ├── ModelTraining
│   │   └── Visualization
│   ├── 03_Dashboards
│   │   ├── KPI
│   │   ├── Cohorts
│   │   ├── Monetization
│   │   ├── LiveOps
│   │   └── QA
│   └── 04_Experiments
│       ├── A_B
│       ├── Multivariate
│       ├── Segments
│       ├── PreReg
│       └── PostMortems
├── 21_Monetization_Economy
│   ├── 01_Storefronts
│   │   ├── Bundles
│   │   ├── Skins
│   │   ├── Consumables
│   │   ├── Subscriptions
│   │   └── Rotations
│   ├── 02_Currency
│   │   ├── Soft
│   │   ├── Hard
│   │   ├── Premium
│   │   ├── Earned
│   │   └── ExchangeRates
│   ├── 03_Compliance
│   │   ├── Regional
│   │   ├── LootBox
│   │   ├── AgeRatings
│   │   ├── Refunds
│   │   └── Parental
│   └── 04_EconomyDesign
│       ├── Sinks
│       ├── Sources
│       ├── Balance
│       ├── Progression
│       └── AntiInflation
├── 22_LiveOps_Events
│   ├── 01_Seasons
│   │   ├── S01
│   │   ├── S02
│   │   ├── S03
│   │   ├── Roadmaps
│   │   └── Rewards
│   ├── 02_Events
│   │   ├── LimitedTime
│   │   ├── Holidays
│   │   ├── Crossovers
│   │   ├── Community
│   │   └── Tournaments
│   ├── 03_Patches
│   │   ├── PatchNotes
│   │   ├── RolloutPlans
│   │   ├── Hotfixes
│   │   ├── Rollbacks
│   │   └── KnownIssues
│   └── 04_EconomyTweaks
│       ├── Pricing
│       ├── DropRates
│       ├── Crafting
│       ├── Balancing
│       └── SinksSources
├── 23_Modding_UGC
│   ├── 01_SDK
│   │   ├── APIs
│   │   ├── Samples
│   │   ├── Tooling
│   │   ├── Packaging
│   │   └── Validation
│   ├── 02_Workshop
│   │   ├── Submissions
│   │   ├── Curation
│   │   ├── Moderation
│   │   ├── Featured
│   │   └── Takedowns
│   ├── 03_Guides
│   │   ├── GettingStarted
│   │   ├── BestPractices
│   │   ├── Legal
│   │   ├── Monetization
│   │   └── Support
│   └── 04_CommunityMods
│       ├── Maps
│       ├── Skins
│       ├── Scripts
│       ├── TotalConversions
│       └── Tools
├── 24_Community_Support
│   ├── 01_Support
│   │   ├── Tickets
│   │   ├── FAQs
│   │   ├── KnownIssues
│   │   ├── Troubleshooting
│   │   └── Refunds
│   ├── 02_Community
│   │   ├── Forums
│   │   ├── Discord
│   │   ├── Social
│   │   ├── Moderation
│   │   └── UGC_Guidelines
│   └── 03_UserResearch
│       ├── Surveys
│       ├── Playtests
│       ├── Interviews
│       ├── Analytics
│       └── Reports
├── 25_Docs_Knowledgebase
│   ├── 01_Specs
│   │   ├── GDD
│   │   ├── TDD
│   │   ├── ArtBible
│   │   ├── AudioBible
│   │   └── UXBible
│   ├── 02_StyleGuides
│   │   ├── Code
│   │   ├── Art
│   │   ├── Narrative
│   │   ├── Audio
│   │   └── Localization
│   ├── 03_KnowledgeBase
│   │   ├── HowTos
│   │   ├── Playbooks
│   │   ├── FAQs
│   │   ├── CheatSheets
│   │   └── Index
│   └── 04_MeetingNotes
│       ├── AllHands
│       ├── Design
│       ├── Engineering
│       ├── Production
│       └── Partners
├── 26_Tools_Pipelines
│   ├── 01_Pipeline
│   │   ├── AssetImport
│   │   ├── BuildAutomation
│   │   ├── Deployment
│   │   ├── Validation
│   │   └── Notifications
│   ├── 02_Editors
│   │   ├── LevelEditor
│   │   ├── DialogueEditor
│   │   ├── MaterialEditor
│   │   ├── BehaviorTreeEditor
│   │   └── ParticleEditor
│   ├── 03_Scripts
│   │   ├── Python
│   │   ├── Bash
│   │   ├── PowerShell
│   │   ├── Batch
│   │   └── Node
│   └── 04_Plugins
│       ├── Unity
│       ├── Unreal
│       ├── Blender
│       ├── Maya
│       └── DCCs
├── 27_Cinematics
│   ├── 01_Previs
│   │   ├── Storyboards
│   │   ├── Animatics
│   │   ├── ShotLists
│   │   ├── CameraRigs
│   │   └── Moodboards
│   ├── 02_Capture
│   │   ├── Mocap
│   │   ├── Facial
│   │   ├── Audio
│   │   ├── Stage
│   │   └── Reference
│   └── 03_Post
│       ├── Editing
│       ├── Color
│       ├── Compositing
│       ├── VFX
│       └── Encoding
├── 28_Research_Prototyping
│   ├── 01_Exploration
│   │   ├── Whitepapers
│   │   ├── Competitive
│   │   ├── TechSpikes
│   │   ├── Feasibility
│   │   └── Demos
│   ├── 02_Labs
│   │   ├── ExperimentalBuilds
│   │   ├── Sandboxes
│   │   ├── ThrowawayCode
│   │   ├── Benchmarks
│   │   └── Findings
│   └── 03_Standards
│       ├── Coding
│       ├── Art
│       ├── Design
│       ├── QA
│       └── Release
├── 29_Marketing_PR
│   ├── 01_Brand
│   │   ├── Guidelines
│   │   ├── Logos
│   │   ├── KeyArt
│   │   ├── ToneOfVoice
│   │   └── Fonts
│   ├── 02_Campaigns
│   │   ├── Beats
│   │   ├── Trailers
│   │   ├── Influencers
│   │   ├── Social
│   │   └── Events
│   └── 03_Comms
│       ├── PressReleases
│       ├── FactSheets
│       ├── Interviews
│       ├── QnA
│       └── Crisis
├── 30_Esports_Broadcast
│   ├── 01_Tournaments
│   │   ├── Rulesets
│   │   ├── Brackets
│   │   ├── AntiCheat
│   │   ├── Prizing
│   │   └── Admin
│   ├── 02_Broadcast
│   │   ├── ObserverTools
│   │   ├── Replays
│   │   ├── SpectatorHUD
│   │   ├── Streams
│   │   └── Overlays
│   └── 03_CommunityPlay
│       ├── Ladders
│       ├── Leagues
│       ├── MatchReports
│       ├── TeamProfiles
│       └── Stats
├── 31_Security_AntiCheat
│   ├── 01_AppSec
│   │   ├── ThreatModels
│   │   ├── CodeReview
│   │   ├── SAST
│   │   ├── DAST
│   │   └── Dependencies
│   ├── 02_GameSecurity
│   │   ├── AntiCheat
│   │   ├── AntiTamper
│   │   ├── Obfuscation
│   │   ├── MemoryProtection
│   │   └── ServerSideChecks
│   └── 03_Privacy
│       ├── GDPR
│       ├── CCPA
│       ├── COPPA
│       ├── DPIA
│       └── DataDeletion
├── 32_Legal_Compliance
│   ├── 01_IP
│   │   ├── Trademarks
│   │   ├── Copyright
│   │   ├── Patents
│   │   ├── Licensing
│   │   └── DMCA
│   ├── 02_Contracts
│   │   ├── Publishing
│   │   ├── Vendor
│   │   ├── Employment
│   │   ├── Talent
│   │   └── NDAs
│   └── 03_Regulations
│       ├── DataPrivacy
│       ├── Gambling
│       ├── Ratings
│       ├── Accessibility
│       └── Tax
├── 33_Publishing_Storefront
│   ├── 01_PlatformSubmissions
│   │   ├── TRC_TCR
│   │   ├── Lotcheck
│   │   ├── Certification
│   │   ├── ComplianceReports
│   │   └── AgeRatings
│   ├── 02_StoreAssets
│   │   ├── Icons
│   │   ├── Screenshots
│   │   ├── Trailers
│   │   ├── Descriptions
│   │   └── Localization
│   └── 03_Distribution
│       ├── Keys
│       ├── DRM
│       ├── Patching
│       ├── Regional
│       └── Pricing
├── 34_Archives
│   ├── 01_Deprecated
│   │   ├── Code
│   │   ├── Assets
│   │   ├── Tools
│   │   ├── Docs
│   │   └── Tests
│   ├── 02_Snapshots
│   │   ├── Milestone
│   │   ├── Release
│   │   ├── Hotfix
│   │   ├── Branch
│   │   └── Compliance
│   └── 03_Legacy
│       ├── Ports
│       ├── Engines
│       ├── Services
│       ├── Vendors
│       └── Agreements
├── 35_Training_Onboarding
│   ├── 01_Curriculum
│   │   ├── Engineering
│   │   ├── Art
│   │   ├── Design
│   │   ├── QA
│   │   └── Production
│   ├── 02_Tutorials
│   │   ├── Tools
│   │   ├── Pipelines
│   │   ├── Standards
│   │   ├── Platforms
│   │   └── Security
│   └── 03_Reference
│       ├── Glossary
│       ├── Acronyms
│       ├── Architecture
│       ├── Datasets
│       └── Links
├── 36_DLC_Expansions
│   ├── 01_Packs
│   │   ├── Story
│   │   ├── Mode
│   │   ├── Map
│   │   ├── Cosmetics
│   │   └── Soundtracks
│   ├── 02_Seasons
│   │   ├── Passes
│   │   ├── Rewards
│   │   ├── Challenges
│   │   ├── Missions
│   │   └── Achievements
│   └── 03_Tools
│       ├── Packaging
│       ├── Entitlements
│       ├── Store
│       ├── Bundling
│       └── QA
├── 37_Saves_Profiles
│   ├── 01_SaveFormats
│   │   ├── Binary
│   │   ├── JSON
│   │   ├── Cloud
│   │   ├── Encryption
│   │   └── Compatibility
│   ├── 02_Profiles
│   │   ├── Accounts
│   │   ├── CrossSave
│   │   ├── Privacy
│   │   ├── Parental
│   │   └── DataDeletion
│   └── 03_Backups
│       ├── Migration
│       ├── Restore
│       ├── Versioning
│       ├── TestData
│       └── Tools
├── 38_VR_AR_XR
│   ├── 01_VR
│   │   ├── OpenXR
│   │   ├── Oculus
│   │   ├── SteamVR
│   │   ├── PSVR
│   │   └── Performance
│   ├── 02_AR
│   │   ├── ARKit
│   │   ├── ARCore
│   │   ├── MarkerBased
│   │   ├── SLAM
│   │   └── UX
│   └── 03_MR
│       ├── HoloLens
│       ├── MagicLeap
│       ├── SpatialAnchors
│       ├── HandTracking
│       └── UX
└── 39_ThirdParty_Partners
    ├── 01_Engines_DCC
    │   ├── Unity
    │   ├── Unreal
    │   ├── Godot
    │   ├── Blender
    │   └── Maya
    ├── 02_Services
    │   ├── PlayFab
    │   ├── Photon
    │   ├── Vivox
    │   ├── Discord
    │   └── AnalyticsVendors
    └── 03_Middleware
        ├── Havok
        ├── PhysX
        ├── SpeedTree
        ├── Umbra
        └── Simplygon
