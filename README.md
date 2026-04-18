# AI + History Collaboratory

**The AI + History Collaboratory is an online forum with synchronous and asynchronous components.** We meet monthly online and maintain the [ai-and-history-collaboratory GitHub repository](https://github.com/ai-and-history-collaboratory/ai-and-history-collaboratory) for asynchronous communication between sessions. This collaboratory is a continuation of the December 2024 MarineLives Collaboratory, in terms of its focus on AI and history.

Depending on how the collaboratory develops, we may identify potential collective collaboratory projects, or simply share projects of individual members of the collaboratory. The repository has both a wiki and a discussion board.

**This season's AI + History Collaboratory (2025/26) runs for six monthly sessions from December 2025 to June 2026, with a History Hackathon planned for September 2026. A second season (2026/27) is planned to run monthly from September 2026 to May 2027.**

---

## Contents

**2025/26 Season**

| # | Session | Date | Status |
|---|---------|------|--------|
| 1 | [Socratic Research Agents](#session-1--socratic-research-agents-past-event) | 9 Dec 2025 | Past |
| 2 | [HTR/NER](#session-2--htrner-past-event) | 20 Jan 2026 | Past |
| 3 | [Exploring MCP as an Interface with Historical Databases](#session-3--exploring-mcp-as-an-interface-with-historical-databases-past-event) | 24 Feb 2026 | Past |
| 4 | [Cowork for Historians: Skills and Workflows](#session-4--cowork-for-historians-skills-and-workflows-past-event) | 31 Mar 2026 | Past |
| 5 | [Shaping the Historian's Desktop](#session-5--shaping-the-historians-desktop-upcoming-event) | 5 May 2026 | **Upcoming** |
| 6 | [Skills/Tools/Knowledge](#session-6--skillstoolsknowledge-future-event) | Jun 2026 | Future |
| - | [History Hackathon](#history-hackathon-future-event) | Sep 2026 | Future |

**Beyond**

- [2026/27 Season: Draft Topics](#202627-season-draft-topics)

**About**

- [GitHub Organisation Members](#github-organisation-members)
- [Collaboratory Session Attendees](#collaboratory-session-attendees)

---

## GitHub Organisation Members

Since the launch of our [history-skills-repository](https://github.com/ai-and-history-collaboratory/history-skills-repository) at Session 4 on 31 March 2026, GitHub organisation membership has grown significantly. The repository requires GitHub membership to access, and this has drawn in historians, archivists, and technologists from across three continents.

**[View an interactive map of all current GitHub members, outstanding invitations and planned invitations, showing their city and country.](https://ai-and-history-collaboratory.github.io/ai-and-history-collaboratory/membership-map.html)**

To join the GitHub organisation, contact [Colin Greenstreet](https://marinelives.academia.edu/ColinGreenstreet) with your GitHub username.

---

## 2025/26 Season

### Session 1: Socratic Research Agents [PAST EVENT]

**Tuesday 9 December 2025** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom

<details>
<summary><strong>Session details</strong></summary>

**Conceptualising, designing, and building a Socratic Research Agent for historical research powered by Gemini 3 Pro Preview** - Colin Greenstreet

- Introduction to Research Agents
- Demonstration of [Socratic Research Agent](https://github.com/Addaci/Generative-Lives-Research-App/wiki) in Google AI Studio
- Hands-on testing and improvement of the Agent in real time by members of the Collaboratory

</details>

---

### Session 2: HTR/NER [PAST EVENT]

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

### Session 3: Exploring MCP as an Interface with Historical Databases [PAST EVENT]

**Tuesday 24 February 2026** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom · *1 hour*

**Session goals:** Understand why MCP matters for institutional control over historical databases; see how document agents interact with structured and unstructured data; recognise that building an MCP interface for your own databases is within reach.

Session materials: [Session plan (PDF)](https://github.com/ai-and-history-collaboratory/ai-and-history-collaboratory/blob/main/session-3/AI_History_Collaboratory_Session_3_v3.1_24022026.pdf)

<details>
<summary><strong>Session details</strong></summary>

**1. Quick introductions (5 min)** - Members and session guests.

**2. What is MCP? Three architectural models (10 min)** - Model Context Protocol as a universal plug for AI access to external data sources. Three architectural models compared: source-oriented (one server per archive, e.g. Riksarkivet, Gallica, MarineLives), task-oriented (one server per research function across sources), and protocol-oriented (one server per data standard, e.g. SPARQL, IIIF, OAI-PMH). Who's building MCP servers for humanities: mostly solo developers, with notable institutional exceptions.

**3. Dan Cohen: loose coupling (5 min)** - Northeastern University Library MCP server + Claude plugin. Institutions retain control while providing structured AI access, "a dial, not a switch." Three-way comparison: library search (overwhelming), ChatGPT (popular web articles, no depth), Claude + MCP (curated scholarly articles, linked).

**4. Tom Scheinfeldt: the reference interview (10 min)** - Sourcery for ArchivesSpace: a conversational AI archivist. Key design patterns: iterative search refinement, transparent scope explanation, graceful escalation ("Connect with Archivist" button), and conversational guidance through unfamiliar collections. Live demo.

**5. Ra-MCP: what we built and found (20 min)** - Adapting Scheinfeldt's reference interview into a formalised five-phase academic research methodology (Scoping → Term Mapping → Deep Reading → Triangulation → Synthesis). Extensions beyond Scheinfeldt: confidence grading (strong/moderate/weak), null results as evidence, survivorship bias awareness, triangulation against secondary literature, growing reference library. Live demo of Swedish maritime jurisdiction research, comparing *Sjörätt* (local maritime courts) with the English High Court of Admiralty.

**6. IWAC + use cases + wrap-up (10 min)** - Frédérick Madore's Islam West Africa Collection (14,500+ documents, Omeka S with REST API, IIIF-compliant, existing AI pipelines). Discussion: your collections, your databases, and what you'd want to build by June.

**New members joining from this session:** Frédérick Madore (University of Bayreuth) and Folami Kolade (Temple University).

<details>
<summary><em>Suggested pre-reading</em></summary>

1. "What is the Model Context Protocol (MCP)", the official introduction. [Read here](https://modelcontextprotocol.io/docs/getting-started/intro)
2. Anthropic, "Claude can now connect to your world" (May 2025). [Read here](https://claude.com/blog/integrations)
3. Dan Cohen, "AI and Libraries, Archives, and Museums, Loosely Coupled," *Humane Ingenuity* (August 2025). [Read here](https://newsletter.dancohen.org/archive/ai-and-libraries-archives-and-museums-loosely-coupled/)
4. Dan Cohen, "The Library's New Entryway," *Humane Ingenuity* (October 2025). [Read here](https://newsletter.dancohen.org/archive/the-librarys-new-entryway/)
5. Tom Scheinfeldt, "Making an AI Frontend for ArchivesSpace," *Found History* (November 2025). [Read here](https://foundhistory.org/making-an-ai-frontend-for-archivesspace/)
6. *(Optional)* ProfessionalWiki, "Let AI access your wiki with MCP," MediaWiki Conference (Fall 2025). [Read here](https://www.semantic-mediawiki.org/wiki/MediaWiki_Users_and_Developers_Conference_Fall_2025/Let_AI_access_your_wiki_with_MCP)

</details>

</details>

---

### Session 4: Cowork for Historians: Skills and Workflows [PAST EVENT]

**Tuesday 31 March 2026** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom · *90 minutes*

**From installation to your first skill file.** An introduction to Claude Cowork as a desktop research environment for historians, followed by a deep dive into skill files, markdown instructions that turn an LLM into a processor, codifying procedural knowledge into reusable, versionable, model-agnostic files. Included a case study from Jacob Forward's PhD research, practitioner snapshots from three core team members, a live demonstration of the Historian's Desktop Skill Builder, announcement of the shared history-skills-repository, and a hands-on group exercise in which participants built their first skill files.

<details>
<summary><strong>Session details</strong></summary>

**1. What Is the Historian's Desktop? (12 min)** - Colin Greenstreet. Framing the concept: a curated ecosystem of skill files, MCP servers, and governance files from which individual historians assemble a workspace tailored to their research. Built on Claude Cowork. Starts with what you already have (folders of archival photographs, PDFs, Zotero libraries), not remote archives.

**2. What Is a Skill File? (10 min)** - Colin Greenstreet. A prompt is a one-off instruction; a skill is a reusable, versionable, inspectable set of instructions encoding a research workflow. Skills are model-agnostic in principle; Anthropic's SKILL.md format is the most mature implementation. Introduced Jamel Ostwald's INPUT-TRANSFORM-OUTPUT framework.

**3. Skills in Practice: Two Perspectives (18 min)**

- **3a. Case Study: Skills for a Local Corpus (12 min)** - Jacob Forward (Cambridge). Working demonstration of skills applied to a local corpus of presidential speeches: the data is on the researcher's machine, processed through skills the researcher can read and modify.
- **3b. Practitioner Snapshots (6 min)** - Mark Thompson (Groningen) on building his own Riksarkivet server app independently; Frédérick Madore (Bayreuth) on connecting a 10,000-reference Zotero library via MCP and building skills with Claude Code; Jamel Ostwald (Eastern Connecticut) on building two Zotero skills in an hour, two weeks after joining the Collaboratory.

**4. The Historian's Desktop Skill Builder: Live Demonstration (10 min)** - Colin Greenstreet. Demonstrated the meta-skill that helps historians create Desktop-conformant skills through a conversational interview protocol.

**5. The Shared Repository: Announcement (5 min)** - Colin Greenstreet. Announced the [history-skills-repository](https://github.com/ai-and-history-collaboratory/history-skills-repository), a shared library of skills for historical research seeded with contributions from Jacob, Frédérick, Jamel, and Colin.

**6. Group Exercise: Identify Your Skill (10 min)** - Participants identified research tasks they do repeatedly that could be streamlined with a skill file.

**7. Hands-On: Build Your First Skill (20 min)** - Participants built their first skill file using either the Historian's Desktop Skill Builder or a prompt template.

**8. Wrap-Up (5 min)** - Next steps and invitation to join the GitHub organisation.

</details>

---

### Session 5: Shaping the Historian's Desktop [UPCOMING EVENT]

**Tuesday 5 May 2026** · 4 pm UK · 5 pm CET · 11 am EST · 9 am MT · 8 am PT · Zoom · *90 minutes*

**Shaping the Historian's Desktop: Collaboratory member input.** The Historian's Desktop is an initiative to develop a governed, AI-enabled research environment by historians for historians, built on Claude Desktop, connecting skill files, MCP servers, and the documents, PDFs, images, and datasets already on historians' hard disks and cloud accounts. A core development team of Colin Greenstreet, Jacob Forward (Cambridge), Mark Thompson (Groningen), Frédérick Madore (Bayreuth), Jamel Ostwald (Eastern Connecticut), and Thiago Krause (Wayne State) is designing and developing the environment, drawing on input from the whole Collaboratory. Following the rapid growth in GitHub membership and engagement since Session 4, this session gathers structured input from Collaboratory members on the priorities, design, and direction of the Desktop. Details to follow.

---

### Session 6: Skills/Tools/Knowledge [FUTURE EVENT]

**June 2026** · Date TBC · Zoom · *1 hour*

**Developing a core skills and knowledge inventory for history-tech enhanced historical research. Reinventing the History PhD in the world of AI-enabled research.**

<details>
<summary><strong>Session details</strong></summary>

**Skills** - Building historical research agents to automate work processes; designing, populating and interrogating flat databases using LLMs; designing, populating and interrogating RAG databases; structuring and critiquing prompts and chains of thought.

**Tools** - Gemini 3.1 Pro, Claude 4.6/4.7, ChatGPT 5.4, open-source near-frontier models (Llama, Mistral, Qwen), Google AI Studio, Colab, Python.

**Knowledge** - Fundamentals of search and discovery; fundamentals of HTR, NER and Knowledge Graphs.

<details>
<summary><em>Discussion questions</em></summary>

- What skills, tools and knowledge have you been using drawing on history tech?
- What would a process to develop a skills training curriculum look like?
- What would a one year preparatory skills training course look like? Would it increase non-academic post-PhD employability?
- How about a history tech hackathon for PhD and postdoc historians and computer scientists?

</details>

</details>

---

### History Hackathon [FUTURE EVENT]

**September 2026** · Format TBC

Possible face-to-face or online history tech hackathon for PhD and postdoc historians and computer scientists.

---

## 2026/27 Season: Draft Topics

*Planned to start September 2026 after a summer break. Monthly sessions September 2026 to May 2027.*

<details>
<summary><strong>Draft topic areas</strong></summary>

**Metacognition** - Developing your own "voice" and confidence when interacting with an LLM; designing and recording experiments to conduct with an LLM (Lab Notebooks); co-development and documentation of hypotheses and arguments with an LLM (Research Notebooks).

**Tool Building** - Developing your own tools vs. using existing tools; repurposing old tools for new purposes using generative AI to redesign or power them; common protocols to enable tools to connect with each other and with LLMs (e.g. MCP); building tools into workflows.

</details>

---

## Collaboratory Session Attendees

The following have attended one or more Collaboratory Zoom sessions (alphabetical):

[Nabil Al-Tikriti](https://cas.umw.edu/historyamericanstudies/faculty-2/al-tikriti/) · [Gavin Beinart-Smollan](https://www.linkedin.com/in/beismo/) · [Maurice Brenner](https://www.linkedin.com/in/maurice-brenner-448134a/) · [David Brown](https://www.tcd.ie/history/staff/david-brown.php) · [Abi Cunningham](https://www.linkedin.com/in/abi-cunningham-1b4481273/) · [Marc Eagle](https://www.wku.edu/history/staff/marc_eagle) · [Jacob Forward](https://www.hist.cam.ac.uk/people/jacob-forward) · [Ben Goldstein](#) · [Colin Greenstreet (convenor)](https://marinelives.academia.edu/ColinGreenstreet) · [Lucas Haasis](https://www.dsm.museum/en/about-us/team/dr-lucas-haasis) · [David Haskiya](https://www.linkedin.com/in/david-haskiya/) · [Henry James](#) · [Sam Kaislaniemi](https://kaislaniemi.fi/samuli/) · [Matthew Kidd](https://lifelong-learning.ox.ac.uk/profiles/matthew-kidd) · [Folami Kolade](https://www.linkedin.com/in/folami-kolade-64523721/) · [Thiago Krause](https://clasprofiles.wayne.edu/profile/hq8728) · [Frédérick Madore](https://www.frederickmadore.com/) · [Israa Mahgoub](#) · [Ian Milligan](https://ianmilligan.ca/) · [Alexander T Myrick](#) · [Oren Okhovat](https://jewishstudies.yale.edu/profile/oren-okhovat) · [Jamel Ostwald](https://www.easternct.edu/faculty-directory/ostwald.html) · [Fabricio Prado](https://www.wm.edu/as/history/faculty-directory/prado_f.php) · [Mark L. Thompson](https://research.rug.nl/en/persons/mark-thompson/publications/)

Our session attendees are associated with universities and institutions across the US, UK, continental Europe, and the Middle East, including the University of Bayreuth, University of Cambridge, University of East Anglia, University of Eastern Connecticut, German Maritime Museum (Deutsches Schifffahrtsmuseum, Bremerhaven), University of Groningen, University of Mary Washington, New York University Abu Dhabi, University of Oxford, Riksarkivet (Swedish National Archives), Temple University, Trinity College Dublin, University of Waterloo, Wayne State University, Western Kentucky University, College of William and Mary, Yale University, and University of York.

---
