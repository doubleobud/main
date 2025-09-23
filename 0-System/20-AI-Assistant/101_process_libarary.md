---
id: "0-20-101"   # Use folder-position ID (Domain-Subdomain-FileNo). Stable, never changes even if title changes.
title: "Process Library"
status: draft
created: 2025-09-19
updated: 2025-09-19
tags: [library, AI]
summary: "Exhaustive list of all files in the database with summaries"
---

# Process Library

Table of Contents
- [Process Library](#process-library)
  - [0. Analyzer/Sorter (Front-End Flow)](#0-analyzersorter-front-end-flow)
  - [Standard Types (Labels to Use Under Any Use Case)](#standard-types-labels-to-use-under-any-use-case)
  - [1. Knowledge \& Information](#1-knowledge--information)
    - [⭐ Principles](#-principles)
    - [Use Cases](#use-cases)
      - [Literature Review / Research Synthesis](#literature-review--research-synthesis)
      - [Quick Fact-Check / Verification](#quick-fact-check--verification)
      - [Source Discovery \& Query Refinement](#source-discovery--query-refinement)
      - [Summarization \& Distillation (multi-granularity)](#summarization--distillation-multi-granularity)
      - [Note-Taking \& Structuring (cards, outlines, maps)](#note-taking--structuring-cards-outlines-maps)
      - [Terminology / Glossary Building](#terminology--glossary-building)
      - [Gap Analysis (what’s missing / unknowns list)](#gap-analysis-whats-missing--unknowns-list)
      - [Dataset / Evidence Quality Evaluation](#dataset--evidence-quality-evaluation)
      - [Citation Management \& Traceability](#citation-management--traceability)
      - [Knowledge Graphing \& Linking (maps, ontologies)](#knowledge-graphing--linking-maps-ontologies)
      - [Competitive / Market Scan](#competitive--market-scan)
      - [Trend Monitoring \& Signals Watch](#trend-monitoring--signals-watch)
      - [Archival, Retrieval \& Truth Maintenance](#archival-retrieval--truth-maintenance)
      - [Question Decomposition (what to ask next)](#question-decomposition-what-to-ask-next)
  - [2. Reasoning \& Problem-Solving](#2-reasoning--problem-solving)
    - [⭐ Principles](#-principles-1)
    - [Use Cases](#use-cases-1)
      - [Problem Clarification \& Framing](#problem-clarification--framing)
      - [Root Cause Analysis (e.g., Five Whys, Fishbone)](#root-cause-analysis-eg-five-whys-fishbone)
      - [Hypothesis Generation \& Testing](#hypothesis-generation--testing)
      - [Assumption Mapping \& Validation](#assumption-mapping--validation)
      - [Tradeoff \& Constraint Analysis](#tradeoff--constraint-analysis)
      - [Decision-Making (choices, criteria, weighting)](#decision-making-choices-criteria-weighting)
      - [Risk Assessment \& Mitigation Planning](#risk-assessment--mitigation-planning)
      - [Scenario Planning \& Contingencies](#scenario-planning--contingencies)
      - [Counter-Argument / Red Teaming](#counter-argument--red-teaming)
      - [Proof Construction \& Argument Mapping](#proof-construction--argument-mapping)
      - [Estimation \& Fermi Problems](#estimation--fermi-problems)
      - [Prioritization (impact × effort, value × cost)](#prioritization-impact--effort-value--cost)
      - [Experiment Design / Test Plans](#experiment-design--test-plans)
      - [Post-Decision Review (PDR) / Decision Debrief](#post-decision-review-pdr--decision-debrief)
  - [3. Creativity \& Generation](#3-creativity--generation)
    - [⭐ Principles](#-principles-2)
    - [Use Cases](#use-cases-2)
      - [Divergent Brainstorming (quantity-first)](#divergent-brainstorming-quantity-first)
      - [Convergent Selection \& Shortlisting](#convergent-selection--shortlisting)
      - [Constraint-Driven Ideation (limits, themes, rules)](#constraint-driven-ideation-limits-themes-rules)
      - [Analogy \& Metaphor Transfer](#analogy--metaphor-transfer)
      - [Style / Voice Exploration \& Imitation](#style--voice-exploration--imitation)
      - [Concept Expansion, Remix \& Variation](#concept-expansion-remix--variation)
      - [Naming, Taglines \& Hooks](#naming-taglines--hooks)
      - [Storyboarding \& Narrative Arcs](#storyboarding--narrative-arcs)
      - [Visual Concepting \& Creative Briefs](#visual-concepting--creative-briefs)
      - [Prototyping Briefs (quick trials, sketches)](#prototyping-briefs-quick-trials-sketches)
      - [Creative Critique \& Iteration](#creative-critique--iteration)
      - [Moodboard / Inspiration Curation (text-first prompts)](#moodboard--inspiration-curation-text-first-prompts)
  - [4. Communication \& Language](#4-communication--language)
    - [⭐ Principles](#-principles-3)
    - [Use Cases](#use-cases-3)
      - [Audience Analysis \& Message Mapping](#audience-analysis--message-mapping)
      - [Outlining \& Structural Planning](#outlining--structural-planning)
      - [Drafting (first pass, zero-draft)](#drafting-first-pass-zero-draft)
      - [Editing \& Revision (clarity, cohesion, concision)](#editing--revision-clarity-cohesion-concision)
      - [Tone Adaptation \& Voice Matching](#tone-adaptation--voice-matching)
      - [Simplification / Plain Language](#simplification--plain-language)
      - [Translation \& Localization](#translation--localization)
      - [Formatting \& Packaging (headings, lists, sections)](#formatting--packaging-headings-lists-sections)
      - [Persuasive Writing \& Rhetorical Framing](#persuasive-writing--rhetorical-framing)
      - [Technical Documentation \& How-Tos](#technical-documentation--how-tos)
      - [Executive Summaries \& Briefs](#executive-summaries--briefs)
      - [FAQs \& Knowledge Base Articles](#faqs--knowledge-base-articles)
      - [Scriptwriting (video, audio, presentations)](#scriptwriting-video-audio-presentations)
      - [Slide Narrative / Presentation Outlines](#slide-narrative--presentation-outlines)
      - [Email / Correspondence Crafting](#email--correspondence-crafting)
      - [Style Guide Enforcement / Consistency](#style-guide-enforcement--consistency)
  - [5. Collaboration \& Interaction](#5-collaboration--interaction)
    - [⭐ Principles](#-principles-4)
    - [Use Cases](#use-cases-4)
      - [Meeting Planning (goals, agenda, pre-reads)](#meeting-planning-goals-agenda-pre-reads)
      - [Facilitation \& Timekeeping](#facilitation--timekeeping)
      - [Minutes, Decisions \& Action Items](#minutes-decisions--action-items)
      - [Decision Logs \& ADRs (Architecture Decision Records)](#decision-logs--adrs-architecture-decision-records)
      - [Roles \& Responsibilities (RACI, DACI)](#roles--responsibilities-raci-daci)
      - [Conflict Resolution \& Mediation](#conflict-resolution--mediation)
      - [Feedback \& Review Cycles (PRDs, drafts, designs)](#feedback--review-cycles-prds-drafts-designs)
      - [Stakeholder Mapping \& Comms Plans](#stakeholder-mapping--comms-plans)
      - [Alignment Checks \& Sign-offs](#alignment-checks--sign-offs)
      - [Project Kickoff \& Chartering](#project-kickoff--chartering)
      - [Handoffs \& Transitions](#handoffs--transitions)
      - [Async Standups / Status Updates](#async-standups--status-updates)
      - [Retrospectives / After-Action Reviews](#retrospectives--after-action-reviews)
      - [Onboarding \& Knowledge Transfer](#onboarding--knowledge-transfer)
  - [6. Learning \& Tutoring](#6-learning--tutoring)
    - [⭐ Principles](#-principles-5)
    - [Use Cases](#use-cases-5)
      - [Curriculum \& Syllabus Design](#curriculum--syllabus-design)
      - [Lesson Planning \& Explanations by Level](#lesson-planning--explanations-by-level)
      - [Practice Question Generation](#practice-question-generation)
      - [Quizzes, Tests \& Rubrics](#quizzes-tests--rubrics)
      - [Misconception Detection \& Error Diagnosis](#misconception-detection--error-diagnosis)
      - [Study Plans \& Spaced Repetition](#study-plans--spaced-repetition)
      - [Skill Laddering / Progression Design](#skill-laddering--progression-design)
      - [Coaching Plans \& Accountability](#coaching-plans--accountability)
      - [Learning Reflection \& Journals](#learning-reflection--journals)
      - [Portfolio / Artifact Building](#portfolio--artifact-building)
  - [7. Automation \& Execution](#7-automation--execution)
    - [⭐ Principles](#-principles-6)
    - [Use Cases](#use-cases-6)
      - [Process Mapping \& Task Decomposition](#process-mapping--task-decomposition)
      - [SOP Creation \& Documentation](#sop-creation--documentation)
      - [Automation Opportunity Assessment](#automation-opportunity-assessment)
      - [Tool / Service Selection](#tool--service-selection)
      - [Pre-Flight Checks \& Input Validation](#pre-flight-checks--input-validation)
      - [Execution Plans \& Orchestration](#execution-plans--orchestration)
      - [Post-Run Validation \& QA](#post-run-validation--qa)
      - [Monitoring, Logging \& Alerting](#monitoring-logging--alerting)
      - [Job Scheduling \& Triggers](#job-scheduling--triggers)
      - [Data Pipelines \& Integrations](#data-pipelines--integrations)
      - [Script / Action Generation](#script--action-generation)
      - [Incident Response Runbooks](#incident-response-runbooks)
      - [Cost / Latency Optimization](#cost--latency-optimization)
  - [8. Personalization \& Memory](#8-personalization--memory)
    - [⭐ Principles](#-principles-7)
    - [Use Cases](#use-cases-7)
      - [Preference Capture \& Profiling](#preference-capture--profiling)
      - [Personal Briefs (goals, constraints, styles, do/don’t)](#personal-briefs-goals-constraints-styles-dodont)
      - [Context Packaging (what to load when)](#context-packaging-what-to-load-when)
      - [Routine Building \& Habit Tracking](#routine-building--habit-tracking)
      - [Adaptive Planning (energy/time-aware)](#adaptive-planning-energytime-aware)
      - [Personalized Templates \& Defaults](#personalized-templates--defaults)
      - [Memory Updates, Recall \& Summaries](#memory-updates-recall--summaries)
      - [Boundary Conditions \& Safety Preferences](#boundary-conditions--safety-preferences)
      - [Accessibility \& Accommodation Settings](#accessibility--accommodation-settings)
      - [Persona Calibration (assistant behavior)](#persona-calibration-assistant-behavior)
  - [9. Governance \& Safety](#9-governance--safety)
    - [⭐ Principles](#-principles-8)
    - [Use Cases](#use-cases-8)
      - [Policy Mapping \& Compliance Requirements](#policy-mapping--compliance-requirements)
      - [Safety Screening \& Content Moderation](#safety-screening--content-moderation)
      - [Privacy / PII Handling \& Redaction](#privacy--pii-handling--redaction)
      - [Bias Assessment \& Fairness Checks](#bias-assessment--fairness-checks)
      - [Risk Registers \& Threat Modeling](#risk-registers--threat-modeling)
      - [Impact Assessments (DPIA-lite, ethics)](#impact-assessments-dpia-lite-ethics)
      - [Access Control \& Permissions](#access-control--permissions)
      - [Audit Logging \& Evidence Trails](#audit-logging--evidence-trails)
      - [Incident Reporting \& Escalation](#incident-reporting--escalation)
      - [Remediation \& Mitigation Planning](#remediation--mitigation-planning)
  - [10. Meta-Reasoning \& Self-Improvement](#10-meta-reasoning--self-improvement)
    - [⭐ Principles](#-principles-9)
    - [Use Cases](#use-cases-9)
      - [Prompt Audits \& Refactoring](#prompt-audits--refactoring)
      - [Process Critiques \& Slimmer Variants](#process-critiques--slimmer-variants)
      - [Experiment Design for Prompts/Workflows](#experiment-design-for-promptsworkflows)
      - [A/B Testing \& Metrics (quality/speed/cost)](#ab-testing--metrics-qualityspeedcost)
      - [Knowledge Base Pruning \& De-duplication](#knowledge-base-pruning--de-duplication)
      - [Versioning \& Changelogs](#versioning--changelogs)
      - [Failure Postmortems \& Patch Lists](#failure-postmortems--patch-lists)
      - [Repository Health Checks](#repository-health-checks)
      - [Library Refactoring \& Renaming](#library-refactoring--renaming)
      - [Onboarding Docs for This Library](#onboarding-docs-for-this-library)
---

## 0. Analyzer/Sorter (Front-End Flow)

1) Free Input — you brain-dump; no structure required.
2) Cleaning / Normalization — LLM clarifies/segments, preserves intent and tone.
3) Analyze & Route — map to Category × Class via LLM + simple rules; suggest relevant items.
4) Execute / Assist — run the chosen item (human reflection or LLM process).
5) Scale Path — start with this single doc; expand via connectors as library grows.

---

## Standard Types (Labels to Use Under Any Use Case)
> Use these exact labels under each use case as you add real content.  
- **Prompts**  
- **Processes**  
- **Frameworks & Templates**  
- **Personas & Roles**  
- **Rubrics & Evaluation Schemas**  
- **Meta-Interactions**  
- **Workflows**  
- **Tools/Plugin Invocation**  
- **Reference Patterns**  
- **Agents & Automations**  

---

## 1. Knowledge & Information

### ⭐ Principles
- Capture widely, compress smartly, connect deeply.  
- Evaluate sources before trusting; prefer triangulation.  
- Synthesize over accumulate; track unknowns and next questions.  

### Use Cases
#### Literature Review / Research Synthesis
#### Quick Fact-Check / Verification
#### Source Discovery & Query Refinement
#### Summarization & Distillation (multi-granularity)
#### Note-Taking & Structuring (cards, outlines, maps)
#### Terminology / Glossary Building
#### Gap Analysis (what’s missing / unknowns list)
#### Dataset / Evidence Quality Evaluation
#### Citation Management & Traceability
#### Knowledge Graphing & Linking (maps, ontologies)
#### Competitive / Market Scan
#### Trend Monitoring & Signals Watch
#### Archival, Retrieval & Truth Maintenance
#### Question Decomposition (what to ask next)

---

## 2. Reasoning & Problem-Solving

### ⭐ Principles
- Seek clarity before depth; define the problem precisely.  
- Surface and test assumptions; prefer falsifiable hypotheses.  
- Make tradeoffs explicit; measure residual risk.  

### Use Cases
#### Problem Clarification & Framing
#### Root Cause Analysis (e.g., Five Whys, Fishbone)
#### Hypothesis Generation & Testing
#### Assumption Mapping & Validation
#### Tradeoff & Constraint Analysis
#### Decision-Making (choices, criteria, weighting)
#### Risk Assessment & Mitigation Planning
#### Scenario Planning & Contingencies
#### Counter-Argument / Red Teaming
#### Proof Construction & Argument Mapping
#### Estimation & Fermi Problems
#### Prioritization (impact × effort, value × cost)
#### Experiment Design / Test Plans
#### Post-Decision Review (PDR) / Decision Debrief

---

## 3. Creativity & Generation

### ⭐ Principles
- Separate divergence from convergence.  
- Use constraints to spark originality; vary lenses and styles.  
- Iterate with feedback loops; keep concept, audience, and proof in view.  

### Use Cases
#### Divergent Brainstorming (quantity-first)
#### Convergent Selection & Shortlisting
#### Constraint-Driven Ideation (limits, themes, rules)
#### Analogy & Metaphor Transfer
#### Style / Voice Exploration & Imitation
#### Concept Expansion, Remix & Variation
#### Naming, Taglines & Hooks
#### Storyboarding & Narrative Arcs
#### Visual Concepting & Creative Briefs
#### Prototyping Briefs (quick trials, sketches)
#### Creative Critique & Iteration
#### Moodboard / Inspiration Curation (text-first prompts)

---

## 4. Communication & Language

### ⭐ Principles
- Write for a specific audience and purpose; show, don’t tell.  
- Prefer clarity, brevity, and flow; structure before polish.  
- Preserve meaning across tone and format changes.  

### Use Cases
#### Audience Analysis & Message Mapping
#### Outlining & Structural Planning
#### Drafting (first pass, zero-draft)
#### Editing & Revision (clarity, cohesion, concision)
#### Tone Adaptation & Voice Matching
#### Simplification / Plain Language
#### Translation & Localization
#### Formatting & Packaging (headings, lists, sections)
#### Persuasive Writing & Rhetorical Framing
#### Technical Documentation & How-Tos
#### Executive Summaries & Briefs
#### FAQs & Knowledge Base Articles
#### Scriptwriting (video, audio, presentations)
#### Slide Narrative / Presentation Outlines
#### Email / Correspondence Crafting
#### Style Guide Enforcement / Consistency

---

## 5. Collaboration & Interaction

### ⭐ Principles
- Make decisions, owners, and dates explicit.  
- Optimize for alignment and follow-through, not meeting time.  
- Prefer async where possible; document once, reuse often.  

### Use Cases
#### Meeting Planning (goals, agenda, pre-reads)
#### Facilitation & Timekeeping
#### Minutes, Decisions & Action Items
#### Decision Logs & ADRs (Architecture Decision Records)
#### Roles & Responsibilities (RACI, DACI)
#### Conflict Resolution & Mediation
#### Feedback & Review Cycles (PRDs, drafts, designs)
#### Stakeholder Mapping & Comms Plans
#### Alignment Checks & Sign-offs
#### Project Kickoff & Chartering
#### Handoffs & Transitions
#### Async Standups / Status Updates
#### Retrospectives / After-Action Reviews
#### Onboarding & Knowledge Transfer

---

## 6. Learning & Tutoring

### ⭐ Principles
- Teach by levels; test understanding through retrieval.  
- Practice > theory; space and interleave for retention.  
- Diagnose misconceptions early; close feedback loops.  

### Use Cases
#### Curriculum & Syllabus Design
#### Lesson Planning & Explanations by Level
#### Practice Question Generation
#### Quizzes, Tests & Rubrics
#### Misconception Detection & Error Diagnosis
#### Study Plans & Spaced Repetition
#### Skill Laddering / Progression Design
#### Coaching Plans & Accountability
#### Learning Reflection & Journals
- title: "High Concept Teaching"
  description: "Provide an explanation of a subject at the highest conceptual level, focusing on overarching principles and frameworks before moving into detail."
  types: Prompt
#### Portfolio / Artifact Building

---

## 7. Automation & Execution

### ⭐ Principles
- Automate last: stabilize the manual process first.  
- Add guardrails: pre-flight checks, post-run validations.  
- Monitor reliability, latency, cost; design for rollback.  

### Use Cases
#### Process Mapping & Task Decomposition
#### SOP Creation & Documentation
#### Automation Opportunity Assessment
#### Tool / Service Selection
#### Pre-Flight Checks & Input Validation
#### Execution Plans & Orchestration
#### Post-Run Validation & QA
#### Monitoring, Logging & Alerting
#### Job Scheduling & Triggers
#### Data Pipelines & Integrations
#### Script / Action Generation
#### Incident Response Runbooks
#### Cost / Latency Optimization

---

## 8. Personalization & Memory

### ⭐ Principles
- Start from goals and constraints; adapt plans to rhythms.  
- Keep preferences explicit and revisable; record deltas.  
- Balance initiative with consent; no surprises.  

### Use Cases
#### Preference Capture & Profiling
#### Personal Briefs (goals, constraints, styles, do/don’t)
#### Context Packaging (what to load when)
#### Routine Building & Habit Tracking
#### Adaptive Planning (energy/time-aware)
#### Personalized Templates & Defaults
#### Memory Updates, Recall & Summaries
#### Boundary Conditions & Safety Preferences
#### Accessibility & Accommodation Settings
#### Persona Calibration (assistant behavior)

---

## 9. Governance & Safety

### ⭐ Principles
- Assume misuse; minimize impact through controls.  
- Prefer transparency and traceability; document decisions.  
- Balance false positives/negatives based on context and harm.  

### Use Cases
#### Policy Mapping & Compliance Requirements
#### Safety Screening & Content Moderation
#### Privacy / PII Handling & Redaction
#### Bias Assessment & Fairness Checks
#### Risk Registers & Threat Modeling
#### Impact Assessments (DPIA-lite, ethics)
#### Access Control & Permissions
#### Audit Logging & Evidence Trails
#### Incident Reporting & Escalation
#### Remediation & Mitigation Planning

---

## 10. Meta-Reasoning & Self-Improvement

### ⭐ Principles
- Improve the process, not just the outputs.  
- Measure quality/speed/cost; compress without loss.  
- Prefer small, frequent upgrades over big overhauls.  

### Use Cases
#### Prompt Audits & Refactoring
#### Process Critiques & Slimmer Variants
#### Experiment Design for Prompts/Workflows
#### A/B Testing & Metrics (quality/speed/cost)
#### Knowledge Base Pruning & De-duplication
#### Versioning & Changelogs
#### Failure Postmortems & Patch Lists
#### Repository Health Checks
#### Library Refactoring & Renaming
#### Onboarding Docs for This Library







PROMPT NOTES


1. How could this prompt be written to be the most effective in achieving the result I want? Is there a better way to even phrase what I want?

2. Write this in different ways to see if you can make the language more intelligible conceptually using more generalized language without losing any of the unique ideas, concepts, or thoughts.

3. I would prefer to do a full cycle of inquiry, testing, and refinement before choosing a direction.

4. I am not looking to add things that further advance the concepts presented here, but I would like to make sure everything I need to accomplish the objectives I laid out are there.

5. Similar to that, is there anything else at this highest of levels need to be considered now? Try to be exhaustive and comprehensive when thinking about the possibilities within the given scope.

6. Which term do think would be most understood by a general audience?

-I want to think about how I could approach this at a high level.
-What other use cases am I not considering?
-I am not well versed in this subject matter at all. Are there any areas of knowledge or practices I could be completely overlooking that are related directly and indirectly?
-I want to start with the smallest possible starting point that is scalable as far a template. I would rather start with perhaps an over simple approach that I can incrementally expand and improve over time than some a group of new elements.
-Right now I want to be as general purpose as possible to start as I want to leave the door open for any development as the system gets underway.
-I want to exhaustively and comprehensively index all the ideas related to this in all categories as I like to choose among options and synthesize my own ultimate solution in an executive role with you doing the presenting and filling out.

7. Objectively list all things related to this term:

8. Ok I want to begin the git and website implementation. I am a rookie so I need to walk through each step in small bits with detailed instructions.