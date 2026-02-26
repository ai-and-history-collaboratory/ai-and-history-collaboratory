# AI + History Collaboratory

**The AI + History Collaboratory is an online forum with synchronous and asynchronous components.** We meet monthly online and maintain the [ai-and-history-collaboratory GitHub repository](https://github.com/ai-and-history-collaboratory/ai-and-history-collaboratory) for asynchronous communication between sessions. This collaboratory is a continuation of the December 2024 MarineLives Collaboratory, in terms of its focus on AI and history.

Depending on how the collaboratory develops, we may identify potential collective collaboratory projects, or simply share projects of individual members of the collaboratory. The repository has both a wiki and a discussion board.

**This season's AI + History Collaboratory (2025/26) runs for six monthly sessions from December 2025 to May 2026, with a possible History Hackathon in June 2026. A second season (2026/27) is planned to run monthly from September 2026 to May 2027.**

---

## Contents

**2025/26 Season**

| # | Session | Date | Status |
|---|---------|------|--------|
| 1 | [Socratic Research Agents](#session-1--socratic-research-agents) | 9 Dec 2025 | Past |
| 2 | [HTR/NER](#session-2--htrner) | 20 Jan 2026 | Past |
| 3 | [Exploring MCP as an Interface with Historical Databases](#session-3--exploring-mcp-as-an-interface-with-historical-databases) | 24 Feb 2026 | Past |
| 4 | [Cowork for Historians: Skills and Workflows](#session-4--cowork-for-historians-skills-and-workflows) | 31 Mar 2026 | **Upcoming** |
| 5 | [Simulations](#session-5--simulations) | Apr 2026 | Future |
| 6 | [Skills/Tools/Knowledge](#session-6--skillstoolsknowledge) | May 2026 | Future |
| — | [History Hackathon](#history-hackathon) | Jun 2026 | Future |

**Beyond**

- [2026/27 Season — Draft Topics](#202627-season--draft-topics)

**About**

- [Collaboratory Members](#collaboratory-members)

---

## 2025/26 Season

### Session 1 — Socratic Research Agents

**Tuesday 9 December 2025** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom

<details>
<summary><strong>Session details</strong></summary>

**Conceptualising, designing, and building a Socratic Research Agent for historical research powered by Gemini 3 Pro Preview** — Colin Greenstreet

- Introduction to Research Agents
- Demonstration of [Socratic Research Agent](https://github.com/Addaci/Generative-Lives-Research-App/wiki) in Google AI Studio
- Hands-on testing and improvement of the Agent in real time by members of the Collaboratory

</details>

---

### Session 2 — HTR/NER

**Tuesday 20 January 2026** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom · *2 hours (1 hour reserved for discussion)*

**LLM-enabled HTR and its integration into historical research processes.** Our discussion focused on the Opening the Ottoman Archives use case detailed in [Colin Greenstreet's January 4th 2026 Substack article](https://generativelives.substack.com/p/opening-the-ottoman-archive), illustrating broader principles of LLM-enabled HTR/OCR for low and medium resource languages.

<details>
<summary><strong>Session details</strong></summary>

**Languages covered:**

- Ottoman Turkish
- Other Ottoman Empire languages (Albanian, Bulgarian, Greek, Armenian) as well as modern Turkish
- Batch HTR for both Ottoman Archives use case and for C17th English Admiralty Court depositions

**Methodologies:**

- HTR Skills markdown files
- GitHub repository for co-created markdown files by historical research community
- Two-stage HTR (visual capture of digital transcription vs. transliteration, translation, NER, contextualised summarisation)
- Validation (statistical methods and human in loop)

**Discussion topics:**

- Integration of LLM-supported HTR into existing (and modified) historical research processes
- Reasons for resistance amongst historians to LLM-supported historical research methods
- Level of interest amongst AI + History Collaboratory members and Ottoman Turkish/Ottoman language historians in pursuing a well-defined piece of academic research for publication as proof of concept

<details>
<summary><em>Suggested reading</em></summary>

- Crosilla G, Klic L, Colavizza G (2025), "Benchmarking large language models for handwritten text recognition". *Journal of Documentation*, Vol. 81 No. 7 pp. 334–354. [doi:10.1108/JD-03-2025-0082](https://doi.org/10.1108/JD-03-2025-0082)
- Greenstreet, Colin, "Opening the Ottoman Archive," *Generative Lives*, January 4th 2025. [Read here](https://generativelives.substack.com/p/opening-the-ottoman-archive)
- Greenstreet, Colin, "A New Lens into the Archive," *Generative Lives*, December 4th 2025. [Read here](https://generativelives.substack.com/p/a-new-lens-into-the-archive)
- Humphries, Mark, "Gemini 3 Solves Handwriting Recognition and it's a Bitter Lesson," *Generative History*, November 24th 2025. [Read here](https://generativehistory.substack.com/p/gemini-3-solves-handwriting-recognition)

</details>

</details>

---

### Session 3 — Exploring MCP as an Interface with Historical Databases

**Tuesday 24 February 2026** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom · *1 hour*

**Session goals:** Understand why MCP matters for institutional control over historical databases; see how document agents interact with structured and unstructured data; recognise that building an MCP interface for your own databases is within reach.

Session materials: [Session plan (PDF)](https://github.com/ai-and-history-collaboratory/ai-and-history-collaboratory/blob/main/session-3/AI_History_Collaboratory_Session_3_v3.1_24022026.pdf)

<details>
<summary><strong>Session details</strong></summary>

**1. Quick introductions (5 min)** — Members and session guests.

**2. What is MCP? Three architectural models (10 min)** — Model Context Protocol as a universal plug for AI access to external data sources. Three architectural models compared: source-oriented (one server per archive, e.g. Riksarkivet, Gallica, MarineLives), task-oriented (one server per research function across sources), and protocol-oriented (one server per data standard, e.g. SPARQL, IIIF, OAI-PMH). Who's building MCP servers for humanities — mostly solo developers, with notable institutional exceptions.

**3. Dan Cohen — loose coupling (5 min)** — Northeastern University Library MCP server + Claude plugin. Institutions retain control while providing structured AI access — "a dial, not a switch." Three-way comparison: library search (overwhelming), ChatGPT (popular web articles, no depth), Claude + MCP (curated scholarly articles, linked).

**4. Tom Scheinfeldt — the reference interview (10 min)** — Sourcery for ArchivesSpace: a conversational AI archivist. Key design patterns: iterative search refinement, transparent scope explanation, graceful escalation ("Connect with Archivist" button), and conversational guidance through unfamiliar collections. Live demo.

**5. Ra-MCP — what we built and found (20 min)** — Adapting Scheinfeldt's reference interview into a formalised five-phase academic research methodology (Scoping → Term Mapping → Deep Reading → Triangulation → Synthesis). Extensions beyond Scheinfeldt: confidence grading (strong/moderate/weak), null results as evidence, survivorship bias awareness, triangulation against secondary literature, growing reference library. Live demo of Swedish maritime jurisdiction research — comparing *Sjörätt* (local maritime courts) with the English High Court of Admiralty.

**6. IWAC + use cases + wrap-up (10 min)** — Frédérick Madore's Islam West Africa Collection (14,500+ documents, Omeka S with REST API, IIIF-compliant, existing AI pipelines). Discussion: your collections, your databases, and what you'd want to build by June.

**New members joining from this session:** Frédérick Madore (University of Bayreuth) and Folami Kolade (Temple University).

<details>
<summary><em>Suggested pre-reading</em></summary>

1. "What is the Model Context Protocol (MCP)" — the official introduction. [Read here](https://modelcontextprotocol.io/docs/getting-started/intro)
2. Anthropic, "Claude can now connect to your world" (May 2025). [Read here](https://claude.com/blog/integrations)
3. Dan Cohen, "AI and Libraries, Archives, and Museums, Loosely Coupled," *Humane Ingenuity* (August 2025). [Read here](https://newsletter.dancohen.org/archive/ai-and-libraries-archives-and-museums-loosely-coupled/)
4. Dan Cohen, "The Library's New Entryway," *Humane Ingenuity* (October 2025). [Read here](https://newsletter.dancohen.org/archive/the-librarys-new-entryway/)
5. Tom Scheinfeldt, "Making an AI Frontend for ArchivesSpace," *Found History* (November 2025). [Read here](https://foundhistory.org/making-an-ai-frontend-for-archivesspace/)
6. *(Optional)* ProfessionalWiki, "Let AI access your wiki with MCP," MediaWiki Conference (Fall 2025). [Read here](https://www.semantic-mediawiki.org/wiki/MediaWiki_Users_and_Developers_Conference_Fall_2025/Let_AI_access_your_wiki_with_MCP)

</details>

</details>

---

### Session 4 — Cowork for Historians: Skills and Workflows

**Tuesday 31 March 2026** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom · *1 hour*

**From installation to your first skill file.** An introduction to Claude Cowork as a desktop research environment for historians, followed by a deep dive into skill files — markdown instructions that turn an LLM into a processor, codifying procedural knowledge into reusable, versionable, model-agnostic files. Workflows can be built into skills, making them far more than simple prompts. Includes a case study from Jacob Forward's PhD research and a hands-on group exercise.

<details>
<summary><strong>Provisional agenda</strong></summary>

**1. Introducing Claude Cowork (15 min)** — Colin Greenstreet

- What is Cowork and why it matters for historians
- Installation, setting up a sandbox folder, and security considerations
- Getting started: your first session

**2. Skills: what, why, and when (10 min)** — Colin Greenstreet

- Codifying procedural knowledge into markdown files
- The context efficiency of progressive disclosure
- Versioning, human and machine editing, reuse
- Building skills that can call on documentation and execute scripts
- Building workflows into skills
- Skills are model-agnostic, but there are merits to Anthropic's implementation
- Identifying repetitive digital procedures and decomposing complex tasks
- The historian de-skilling risk — and where *not* to apply skills

**3. Case study: skills for historical research (15 min)** — [Jacob Forward](https://www.hist.cam.ac.uk/people/jacob-forward), University of Cambridge

- Skills for local database interrogation
- A 2,500-word skill for multi-stage metaphor extraction in PhD research
- How skills turn the LLM into a processor, with the skill as software

**4. Group work and discussion (15 min)**

- Each participant identifies one area of their work where they could use skills
- Discussion and sharing
- Those who haven't yet tried commit to building a skill, using a prompt template to get started

**5. Wrap-up (5 min)** — Next steps, preview of Session 5.

<details>
<summary><em>Getting started: skill-building prompt template</em></summary>

Paste this into Claude to create your first skill:

> *"I would like your assistance to build a Skill.md file. Please begin by asking me 5–10 questions to discover the particular use-case I have in mind, including all the relevant details. Ask one question at a time and allow my answers to each to inform the next question you pose, until you have a complete picture. After 5–10 questions, use my answers, as well as your native skill-building skill, to write an Anthropic-compliant skill closely focused on my use-case and achieving my goal. Then encourage me to read, test, and refine it."*

</details>

<details>
<summary><em>Suggested pre-reading</em></summary>

1. Anthropic, "Agent Skills — Overview," Claude Platform documentation. [Read here](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
2. Anthropic, "Skill Creator" — the reference skill for building new skills. [Read here](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md)

</details>

</details>

---

### Session 5 — Simulations

**April 2026** · Date TBC · Zoom · *1 hour*

**Developing historical simulations for teaching and research purposes.** Explore how students themselves can develop simulations, thus improving their generative-AI skills, including understanding Python basics, the software development process, and the UI/UX design process.

<details>
<summary><strong>Session details</strong></summary>

Members of the collaboratory to suggest ideas for simulations which are bite size and which interest them.

**Use case:** A simulation to explore the writing of charter parties by scriveners and how merchants, masters, and ship owners engaged in discussions and negotiations resulting in drafting of terms. Drawing on high quality images and full transcriptions of actual charter parties from the 1620 to 1680 period, plus statute and case law regarding charter parties and contracts grounded in C17th English practice.

</details>

---

### Session 6 — Skills/Tools/Knowledge

**May 2026** · Date TBC · Zoom · *1 hour*

**Developing a core skills and knowledge inventory for history-tech enhanced historical research. Reinventing the History PhD in the world of AI-enabled research.**

<details>
<summary><strong>Session details</strong></summary>

**Skills** — Building historical research agents to automate work processes; designing, populating and interrogating flat databases using LLMs; designing, populating and interrogating RAG databases; structuring and critiquing prompts and chains of thought.

**Tools** — Colab, Gemini 3 Pro, Claude 4.5, ChatGPT 5.1, Google AI Studio, Python.

**Knowledge** — Fundamentals of search and discovery; fundamentals of HTR, NER and Knowledge Graphs.

<details>
<summary><em>Discussion questions</em></summary>

- What skills, tools and knowledge have you been using drawing on history tech?
- What would a process to develop a skills training curriculum look like?
- What would a one year preparatory skills training course look like? Would it increase non-academic post-PhD employability?
- How about a June 2026 face to face or online history tech hackathon for PhD and postdoc historians and computer scientists?

</details>

</details>

---

### History Hackathon

**June 2026** · Format TBC

Possible face-to-face or online history tech hackathon for PhD and postdoc historians and computer scientists.

---

## 2026/27 Season — Draft Topics

*Planned to start September 2026 after a summer break. Monthly sessions September 2026 to May 2027.*

<details>
<summary><strong>Draft topic areas</strong></summary>

**Metacognition** — Developing your own "voice" and confidence when interacting with an LLM; designing and recording experiments to conduct with an LLM (Lab Notebooks); co-development and documentation of hypotheses and arguments with an LLM (Research Notebooks).

**Tool Building** — Developing your own tools vs. using existing tools; repurposing old tools for new purposes using generative AI to redesign or power them; common protocols to enable tools to connect with each other and with LLMs (e.g. MCP); building tools into workflows.

</details>

---

## Collaboratory Members

Confirmed members (alphabetical):

[Gavin Beinart-Smollan](https://www.linkedin.com/in/beismo/) · [Maurice Brenner](https://www.linkedin.com/in/maurice-brenner-448134a/) · [David Brown](https://www.tcd.ie/history/staff/david-brown.php) · [Abi Cunningham](https://www.linkedin.com/in/abi-cunningham-1b4481273/) · [Marc Eagle](https://www.wku.edu/history/staff/marc_eagle) · [Jacob Forward](https://www.hist.cam.ac.uk/people/jacob-forward) · [Colin Greenstreet (convenor)](https://marinelives.academia.edu/ColinGreenstreet) · [Lucas Haasis](https://www.dsm.museum/en/about-us/team/dr-lucas-haasis) · [Sam Kaislaniemi](https://kaislaniemi.fi/samuli/) · [Folami Kolade](https://www.linkedin.com/in/folami-kolade-64523721/) · [Thiago Krause](https://clasprofiles.wayne.edu/profile/hq8728) · [Frédérick Madore](https://www.frederickmadore.com/) · [Oren Okhovat](https://jewishstudies.yale.edu/profile/oren-okhovat) · [Mark L. Thompson](https://research.rug.nl/en/persons/mark-thompson/publications/)

Our members are associated with a wide range of universities and institutions in the US, UK, and continental Europe, including the University of Bayreuth, University of Cambridge, University of East Anglia, German Maritime Museum (Deutsches Schifffahrtsmuseum, Bremerhaven), University of Groningen, New York University, Temple University, Trinity College Dublin, Wayne State University, Western Kentucky University, Yale University, and University of York.
