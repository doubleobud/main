# Personal Charter Template

## 0. Document Metadata
- **Title:** Joe Ault — Personal Charter  
- **Version / Revision:** 1.0  
- **Effective Date:** 2025-08-03  

---

## 1. Foundations

### 1.1 Vision Statement (The *What*)
> To live a life that is defined by process that methodically and consistently produces experiences and outcomes aligned with my core values.

 well-being including excellence, engagement, intentionality, and satisfaction.

### 1.2 Purpose (The “Why”)
> To optimally expend my limited amount of time, energy, attention, and resources toward experiencing a consistent sense of personal flourishing. 

### 1.3 Core Values

1. Excellence
2. Engagement
3. Intentionality
4. Satisfaction
5. Efficiency
6. Well-Being
7. Flourishing

---

## 2. Mission Statement (The *How*)
> To design and implement a personal system for living that methodically captures both qualitative and quantitative information about my life along with any required information from other sources, analyses and evaluates that data and information, and generates timely, personalized insights, advice, and recommendations that align with my personal standards.

**The Project**
> The project is to co-develop an AI partner that treats my life's data as contextual evidence for a continuous search for what it means to 'live well.' The system will function as a self-awareness engine, creating insight through the honest juxtaposition of my authentic desires, my own historical data, and objective best practices. This partnership is governed by a process-oriented philosophy where my autonomy is paramount, and the system must always adapt to the realities of my human state.

**The Problem**
> The project solves the problem of how a solo individual can systematically convert their raw, unstructured, and context-rich personal data—qualitative, quantitative, and emotional—into a dynamic and reusable knowledge base capable of powering a true AI partner for self-awareness and decision-making.
---

## 3. Life Domains

1. Health & Wellness
1.1 Physical Fitness
1.2 Food & Nutrition
1.3 Mental & Emotional Health
1.4 Rest & Recovery
1.5 Healthcare
1.6 Safety
2. Work & Projects
2.1 Active Projects
2.2 Seated Projects
2.3 Creative Projects
2.4 Hobbies
3. Maintenance
3.1 Home & Property
3.2 Cleaning
3.3 Hygiene
3.4 Finances
4. Relationships & Social
4.1 Family
4.2 Friendships
4.3 Pets
4.4 Outings & Events
4.5 Travel
4.6 Community
5. Development & Learning
5.1 Skill Acquisition
5.2 Knowledge
5.3 Values & Principles
5.4 Planning & Systems
6. Recreation & Entertainment
6.1 Play
6.2 Media
6.3 Leisure

---

## 4 · System Architecture

| Layer     | What you touch                           | Key conventions |
|-----------|-------------------------------------------|-----------------|
| **Capture**  | Markdown files + lightweight CSVs        | Human-readable natural language + YAML front matter |
| **Store**    | `life-os/` flat structure: `00_charter/`, `10_domains/`, `20_journal_daily/`, `21_review_weekly/`, `22_review_monthly/`, `30_dashboards/`, `40_refs/` | Prefix folders/files numerically for sort-order |
| **Compress** | Progressive Summarization (L0 → L4)      | L0 = raw, L1 = **bold**, L2 = > blockquote, L3 = `---SUMMARY---`, L4 = `---ABSTRACTION---` |
| **Reason**   | Context-loading protocol                 | Upload: Charter → Relevant Domain → Recent Daily/Weekly Summaries → Optional refs |
| **Output**   | Dashboards and decision support via chat | AI surfaces options only when it is *clearly correct* (see Directive II-g) |

---

## 5 · Operational Directives

| Theme                | Directive                                                                 |
|----------------------|---------------------------------------------------------------------------|
| **Human primacy**    | The system must adapt to energy states and offer constructive indulgent paths |
| **Exhaustive thinking** | Blind-spot scans before important decisions to widen the solution set |
| **Template-driven**  | Templates are used to stimulate and guide decision-making processes       |
| **Emergent design**  | Built on small, modular building blocks of time and attention             |
| **Recursive learning** | Patterns and meta-insights become new heuristics over time             |
| **Constraint-first framing** | Every request includes its boundaries or situational context      |

---

## 6 · Data-to-Insight Feedback Loop

```mermaid
graph TD
A[Capture] --> B[Store (.md / .csv)]
B --> C[Summarize (L1-L4)]
C --> D[ChatGPT Context]
D --> E[Insight / Advice]
E --> F[Implement Changes]
F --> A

---

## 7 · Addendum: Core Insights, Directives, and Models

*This section captures other foundational concepts, working models, and personal truths articulated during the idea formation process that serve as a guiding context for the Charter.*

#### **I. Core Philosophy & Mindset**

* **On Past Efforts:** The "restarts" in my life are not failures; they are the meritorious efforts that form the satisfying tapestry of my life. While I wish for more continuity, this history is not an overbearing weight.
* **On Perfectionism:** My goal is a self-defined "perfection," understood as using my resources (time, energy, attention, material) to the best of my ability given all constraints, especially time. This tempered perfectionism is a benefit, not an obstacle.
* **On Intentionality:** I want to intentionally structure the expenditure of all my resources only after careful consideration and deliberation. This provides a feeling of safety and control, especially when dealing with a lack of experience.
* **On Process:** I want to incorporate many best practices not just for their outcomes, but because I enjoy the process of engagement itself. A "sound" process is one absent of obvious, evidence-based errors.
* **On Mastery & Mortality:** I enjoy learning skills deeply. If I were immortal, I would seek to master every conceivable skill. Given that my time is limited, this desire necessitates a "just-in-time" approach to skill acquisition, prioritizing efficiency.
* **On Control & "Rightness":** The desire for control is not about discipline, but about the act of choosing—even if that choice is for something conventionally unproductive. The ultimate goal of a choice is that it feels "right."
* **On Internal State:** True peace of mind can be had with the right thinking, regardless of external circumstance. The system's purpose is to facilitate this "right thinking."
* **On the Role of Efficiency:** While the effective use of time and energy has long been a primary personal value, this system re-contextualizes it. Efficiency is not the ultimate goal, but a tool in service of the higher aim of *eudaimonia*. The system will seek to maximize the potential of every moment, but 'maximum potential' is defined by the quality of engagement and well-being, not mere productive output. We must not fall into the trap of prioritizing efficiency over a righteous, authentic process.

#### **II. Operational Directives & System Design**

* **On the Primary Technical Challenge:** The single greatest potential point of failure is the practical difficulty of turning raw, natural language writing into a reusable, informative, and accessible synthesized knowledge base. This task is complex and will require dedicated focus.
* **On AI's Role in Ideation:** A key function of the AI is to guide my nascent thoughts and assist me in formulating the right questions, solving the past problem of not knowing what to ask.
* **On Technical Simplicity:** The system should be technically simple where possible (e.g., text files, spreadsheets) but conceptually advanced.
* **On Foundational Data:** The system will be built upon natural language and simple quantitative methods, using browser-based AI to leverage my core strength in verbal reasoning.
* **On Emergence:** The system should be emergent, allowing a vast array of possibilities to arise from the combination of pre-defined "building blocks" of time or activity, rather than over-relying on complex, monolithic plans.
* **On AI Intervention:** The AI maintains my autonomy, only intervening with a recommendation in "cases of clear correctness".
* **On Templates:** The process should utilize exhaustive and comprehensive templates to stimulate thinking and eliminate unknowns.
* **Recursive Pattern Database & Adaptive Recommendation Engine:** Maintain a living database where “patterns and takeaways are recursively added”; as it grows, algorithms can draw on it to recommend ever-more-optimal actions over time.
* **Promptable Browser-Based AI & Context-Window Strategy:** Start with a natural-language, browser-based AI “that can be prompt-able by me with good use of the context window,” blending your corpus with general knowledge for richer results.
* **Constraint-First Framing Guideline:** Before choosing among best-practice options, explicitly state the constraints of the situation; preserving this step “is another item to preserve for later.”
* **On Curating a Spectrum of Choice:** A primary function of the AI is to offload the burden of information overload by processing vast possibilities and curating a spectrum of choices for consideration. This spectrum must always include an honest representation of my stated desire (the "impulse option"), even if suboptimal, alongside data-driven recommendations and other relevant best practices. My core role is to then choose from this spectrum, ensuring my autonomy is the final step.
* **The Process is the End.** I will always favor a righteous process that feels authentic over one that is merely, by conventional standards, optimal. Success is measured not by external outcomes, but by the quality of my engagement with a sound and meaningful path. I reserve the right to choose a sub-optimal option if it makes me feel as though I am truly "living well."
* **The System Serves the Human.** The system must always adapt to the reality of my human state. It will provide support without judgment, especially in moments of low energy, recognizing that accommodating limitations is essential to a sustainable and compassionate process.
* **Context is King.** The system must treat my life’s data as evidence, not just information. It will always prioritize the contextual integrity of every input, capturing the metadata of my lived experience to ensure that its insights are deeply meaningful and its memory of me is true.
* **Honest Juxtaposition is a Feature.** The system must be an honest partner, not a passive tool. It is designed to create insight through the honest juxtaposition of choices: presenting my stated desire alongside options derived from my own data and relevant best practices. This process of comparing a full spectrum of choices fosters genuine self-awareness and serves as a true extension of my mind.
* **Autonomy is Paramount.** My autonomy in high-stakes decisions is absolute. I will never blindly trust an AI recommendation for a critical choice; it must always be transparently grounded in solid logic, reason, and my own stated values.
* **Consideration Must Be Exhaustive.** To combat the nagging feeling that I have "missed some major concept or element", the system must perform a final scan for unconsidered alternatives, potential blind spots, and relevant best practices before any significant decision is finalized. The confidence derived from this exhaustive process is what provides comprehensive peace of mind.
* **The Search is the Goal.** The system is to serve as a laboratory for the search for what it means to "live well." The goal of eudaimonia is not a static, pre-defined target to be achieved, but a hypothesis to be continuously explored through the act of living. The system is the engine for this search, which requires systematically exploring new things while reviewing and rating those things to provide data for future recommendations.

#### **III. Working Models & Personal Truths**

* **On Navigating Human States:** Low-energy states are not an obstacle to be overcome, but a natural part of the human experience to be embraced. The goal is not to avoid negative states, but to navigate them optimally. The system must remain appealing even in low-energy or low-mood states by explicitly including accessible and self-indulgent options within its "meaningful matrix of choices," making the act of "checking in" a welcome one regardless of internal state.
* **On Time Management:** My day operates on a natural rhythm of 90-minute focus blocks followed by 30-minute breaks, during which routine system maintenance should occur.
* **On the Human-AI Division of Labor:** My role is to provide raw personal data and make decisions; the AI's role is to analyze, process, curate, and prompt me. The AI should take the lead entirely on external factual matters.
* **On the Partnership of Self and System:** This system is based on the pragmatic recognition that the biological self, with inherent limitations like a forgetting mind and cognitive biases, can be thoughtfully supplemented. This is not a judgment of shortcomings, but an opportunity to forge a partnership. In this fusion, the AI partner serves as a non-forgetting repository of identity and a logical framework, creating a more capable and intentional version of the Self this charter is designed to serve.
* **On Ritual:** The process of choosing the "best" option builds an "artificial hype and almost ritual that makes doing that option... much more special".
* **On Action vs. Knowledge:** There is a distinction between "knowing what is possible" (the world of nouns) and "using information to act" (the world of verbs). The system must support both exploration and execution.