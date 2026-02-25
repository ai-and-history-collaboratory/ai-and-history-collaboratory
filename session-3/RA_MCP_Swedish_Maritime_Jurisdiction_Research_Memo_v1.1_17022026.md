# Riksarkivet MCP Server: Exploratory Research on Swedish Maritime Jurisdiction

**Version:** 1.1
**Date:** 17 February 2026
**Author:** Colin Greenstreet and Claude (Anthropic, Claude Opus 4.6)
**Session type:** Collaborative human-AI research using Claude Cowork with Riksarkivet MCP server

**Version history:**
- v1.0 (17 Feb 2026): Initial synthesis of session findings, methodology, and recommendations.
- v1.1 (17 Feb 2026): Incorporated content from the "Hitta i Svea hovrätts handlingar" finding aid (Riksarkivet, 1998). Added Section 3.7 on Svea hovrätt archival structure. Revised Section 4.4 to reflect finding aid content. Added Section 4.5 recommending creation of a collaborative research skill file. Added Appendix D (draft skill file).

---

## 1. Goal

This memo documents an exploratory research session conducted on 17 February 2026, using the Riksarkivet (Swedish National Archives) MCP server (ra-mcp) within Claude Cowork. The session had two intertwined objectives:

1. **Substantive research question:** To investigate whether Sweden had a dedicated Admiralty Court or Prize Court equivalent to the English High Court of Admiralty (HCA), and to compare the jurisdictional, structural, and legal frameworks of the two systems during the early modern period (c.1600-1800).

2. **Methodological evaluation:** To assess the ra-mcp server's capabilities and limitations as a tool for structured academic research, particularly in combination with web-based secondary sources, and to develop recommendations for future collaborative research workflows.

The session arose organically from an initial exploratory query about the ra-mcp tools and developed into a substantive comparative legal-historical investigation.

---

## 2. Methodology

### 2.1 Tools Used

The research drew on three categories of tool:

**Riksarkivet MCP server (ra-mcp):**
- `search_metadata` — searches archival metadata (titles, creator names, places, institutional descriptions) across the Nationell Arkivdatabas (NAD)
- `search_transcribed` — searches AI-transcribed (HTR/OCR) text within digitised documents, supporting Solr query syntax including wildcards, fuzzy search, Boolean operators, and proximity searches
- `browse_document` — retrieves full page transcriptions by archival reference code

**Web research:**
- `WebSearch` — general web searches to locate secondary literature, finding aids, and institutional descriptions
- `WebFetch` — retrieval and processing of specific web pages

**Published finding aids (supplied by researcher):**
- "Hitta i Svea hovrätts handlingar" (Riksarkivet, Forskarserviceavdelningen, mars 1998) — a structured guide to the internal series of the Svea hovrätt archive. This PDF was identified by web search during the session but could not be fetched automatically; it was subsequently supplied by the researcher and incorporated in v1.1.

**Synthesis and analysis:**
- Claude's training knowledge (cutoff: May 2025) provided baseline knowledge of English and Swedish legal history, supplemented and verified by the above tools

### 2.2 Search Strategy

The ra-mcp searches followed a systematic, incremental approach designed to avoid server timeouts and to map the semantic field methodically:

| Step | Search term(s) | Tool | Rationale |
|------|---------------|------|-----------|
| 1 | `Stockholm` (metadata, 1610-1620) | search_metadata | Establish baseline volume of holdings for the period |
| 2 | `((Stockholm AND ship*) OR (Stockholm AND skepp*))` | search_transcribed | Test bilingual search; identify maritime content |
| 3 | `SE/RA/420422/01` (metadata + browse) | search_metadata, browse_document | Investigate the dominant archival series (Svea hovrätt) |
| 4 | `amiralitetsr*` | search_transcribed + search_metadata | Search for "Admiralty Court" as an institution |
| 5 | `prisrätt*` | search_transcribed | Search for "Prize Court" |
| 6 | `sjörätt*` | search_metadata | Search for "Maritime Court" as an institution |
| 7 | `"sjörätten"` (definite form) | search_transcribed | Confirm Sjörätt as a named functioning court |
| 8 | `amiralitetskolleg*` + `amiralitet` | search_metadata | Locate Admiralty Board holdings and determine their archival home |
| 9 | `"sjölagen"` | search_transcribed | Map references to the codified Maritime Code |
| 10 | `"prisdom*"` | search_transcribed | Search for prize judgments as compound terms |
| 11 | `Kommerskollegium sjö*` | search_metadata | Investigate Board of Commerce's maritime role |

Web searches supplemented the archival evidence at three points: (a) to locate published finding aids for Svea hovrätt; (b) to contextualise the English HCA for comparison; and (c) to search for secondary literature on Swedish maritime courts.

### 2.3 Documentation Approach

Throughout the session, findings were reported incrementally with explicit confidence assessments. Each claim was tagged with:

- **Source type** (ra-mcp transcription, ra-mcp metadata, web search, published finding aid, training knowledge)
- **Evidence strength** (strong/direct attestation, moderate/inferred, weak/argument from silence)
- **Gaps and limitations** flagged in real time

This approach was adopted to maintain academic credibility when working with a novel and incompletely understood research tool (the ra-mcp server), where the coverage, transcription quality, and institutional scope of the underlying data are not fully documented.

---

## 3. Synthesised Findings

### 3.1 The Sjörätt: A Local Maritime Court

**Evidence strength: Strong (direct archival attestation)**

Sweden had functioning local maritime courts called **Sjörätt** (plural: Sjörätter) in port towns. The ra-mcp transcription searches produced direct references to named courts:

- **SjöRätten i Skanör** — referenced in a 1784 case (SE/VaLA/03825/01/A II/68, pp. 602-603)
- **SjöRätten i Helsingborg** — a 1802 case (SE/VaLA/03825/01/A II/94, p. 278)
- **Sjörrättens LandsCrona** — a 1783 case (SE/VaLA/03825/01/A II/67, p. 376)
- **SjöRätten** (generic) — an 1789 case involving skipper Lundgren (SE/VaLA/03825/01/A II/73, p. 426)

All four references appear in **Göta hovrätt appeal records** (held at Riksarkivet i Vadstena), confirming that the Sjörätt functioned as a **first-instance court** whose rulings were appealed to the general hovrätt — not to a separate admiralty appellate court. The cases concerned maritime commercial disputes (crew disputes, cargo claims, skippers' conduct).

**Unresolved:** Whether the Sjörätt was a permanent standing court or a specialist session of the town court (Rådhusrätt). The modern Swedish system has seven designated "maritime courts" (sjörättsdomstolar) which are specialist chambers within designated district courts, suggesting possible historical continuity.

### 3.2 The Sjölagen: A Codified Maritime Law

**Evidence strength: Strong (abundant references)**

The search for *"sjölagen"* returned **153 page-level hits across 100+ volumes**, overwhelmingly from Svea hovrätt (SE/RA/420422/01). The transcriptions show courts citing the Sjölagen by chapter and section, with named divisions (balkar) including:

- **Skeppmanna Balken** (Seamen's Code)
- **Skeplego Balken** (Ship Charter Code)
- **Bodeneri Balken** (Bottomry Code)
- **Försäkrings Balken** (Insurance Code)
- **Skepps Tings Balken** (Ship's Court Code)

The references cluster in the late 18th and early 19th centuries, consistent with the 1667 Maritime Code of Karl XI as consolidated in the 1734 Sveriges Rikes Lag. This codification is a fundamental structural difference from the English HCA, which operated under a mixture of Roman civil law, maritime custom, and precedent.

### 3.3 The Amiralitetskollegium: Military, Not Judicial

**Evidence strength: Moderate (clear archival provenance)**

The metadata search for *amiralitetskolleg** returned **100+ records**, held entirely at **Krigsarkivet** (the War Archives, SE/KrA/0500-0503), not at Riksarkivet. The archival creator is **Amiralitetskollegium (1634-1791)**, with records classified under *Flottans arkiv* (Fleet Archives) — chancellery records, crew rosters, ship expedition records, logbooks.

The placement within military archives, and the absence of any series titled *Amiralitetsrätt* in either metadata or transcriptions, strongly suggests this was an **administrative and military body** governing the navy, not a civilian court. The only transcription hits for *amiralitets** were two references to *AmiralitetsRådet* — a personal title (Admiralty Councillor), not a court name.

### 3.4 Prize Jurisdiction: Not Resolved

**Evidence strength: Weak (absence of evidence)**

Searches for *prisrätt** (prize court), *prisdom** (prize judgment), and related terms returned **zero results**. This is the most significant gap in the findings. Prize cases during the Great Northern War (1700-1721) or the Napoleonic Wars must have been adjudicated somewhere. Possible explanations:

- Prize cases may have been handled by the Amiralitetskollegium under military authority, with records at Krigsarkivet (partially covered by ra-mcp but with uneven transcription coverage)
- The terminology may differ — *uppbringning* (capture/seizure), *sjörov* (sea robbery/piracy), or other terms
- Relevant records may not yet be digitised or transcribed

### 3.5 The Kommerskollegium: Regulatory, Not Judicial

**Evidence strength: Moderate**

The **Kommerskollegium** (Board of Commerce, est. 1651) appeared in metadata as creator of maritime regulatory records (SE/RA/420132/1), but in a regulatory/advisory capacity, not as a court. Maritime commercial disputes went to the Sjörätt or Rådhusrätt, with appeal to the hovrätt.

### 3.6 Comparative Summary: Swedish System vs. English HCA

| Dimension | English HCA | Swedish System |
|-----------|------------|----------------|
| **Institutional type** | Centralised national specialist court | Local Sjörätter in port towns, feeding into general appellate hovrätter |
| **Legal tradition** | Civil/Roman law (anomalous in common law England) | Civil law (standard for Sweden); codified in Sjölagen |
| **Maritime civil cases** | Primary jurisdiction (contracts, collisions, salvage) | First instance at Sjörätt; appeal to hovrätt alongside all other civil matters |
| **Maritime criminal** | Piracy, discipline at sea | Apparently handled by military courts under Amiralitetskollegium |
| **Prize jurisdiction** | Dedicated prize court within HCA | Unknown — possibly Amiralitetskollegium (military); not found in civilian archives |
| **Legal basis** | Roman law, custom, precedent | Sjölagen (statutory code, 1667/1734) with named divisions |
| **Record survival** | Centralised at TNA (HCA series) | Dispersed: civilian courts at Riksarkivet; military at Krigsarkivet; local courts at regional archives |

### 3.7 The Svea Hovrätt Archive: Internal Structure (from the "Hitta i..." Finding Aid)

**Source: "Hitta i Svea hovrätts handlingar," Riksarkivet, Forskarserviceavdelningen, mars 1998.**

The finding aid, supplied by the researcher after the initial session, provides the definitive guide to the Svea hovrätt Huvudarkivet (SE/RA/420422/01). Its content significantly enriches our understanding of where maritime cases sit within the archive and explains several patterns observed in the ra-mcp searches.

**Institutional context:** Svea hovrätt was founded in 1614 as the king's court (*konungens domstol*) but lost this status as early as 1615, when the king's judicial authority was instead exercised by the Council (*rådet*) and, after 1789, by the Supreme Court (*Högsta Domstolen*). Svea hovrätt nevertheless retained a special position among the hovrätter, notably as the **first-instance court for the nobility**. From 1910-1948 it was divided into two divisions: the Svealand division and the Norrland division.

**Key series relevant to our maritime research:**

| Series | Signum | Description | Significance for this research |
|--------|--------|-------------|-------------------------------|
| **Protokoll i civila mål** | A I a | Minutes in civil cases. Brief for older periods; supplemented by *codices rationum* (A II a, A II b) covering 1636-1800, which contain the judges' reasoning (*ledamöternas domskäl*). | Maritime civil disputes would appear here. The codices rationum are critical: they contain the legal reasoning that bare minutes omit. |
| **Protokoll i brottmål** | A I b | Minutes in criminal cases. Fair-copied protocols missing before 1756. | Maritime criminal matters (smuggling, piracy) would appear here, but the pre-1756 gap is significant for the early modern period. |
| **Protokoll inför Kungl. Maj:t** | A I c | Protocols in cases submitted to the king. 1619-1695: death sentences were always submitted. | Prize or piracy cases resulting in death sentences might appear here. |
| **Protokoll i särskilda mål** | A I d | Protocols where the hovrätt was first instance — cases against senior officials. Contains the trials of Field Marshal Nils Bielke, the Dala uprising, the murder of Gustav III, the treason case against Gustaf Mauritz Armfelt. | Confirms the hovrätt's role as first-instance court for high-status defendants. |
| **Koncept och registratur (domböcker)** | A II a, A II b | Judgments in the main series, from 1614 onwards. Distinguishes between *instämda mål* (cases where the hovrätt was first instance), *vädjade mål* (appeals from lower courts), *ansöknings- och besvärsmål* (petitions and complaints), and *kriminella mål* (criminal cases). | The domböcker from 1614 are the primary record of the hovrätt's judicial output. Maritime appeals from Sjörätter would be classified as *vädjade mål*. |
| **Akter i instämda och vädjade mål (liber causarum)** | E VI a 2 aa | Case files for instituted and appealed cases. Called *liber causarum* until 1712. **Critical gap: for 1689-1704 and 1713-1804, only remnants survive.** | This is the E VI series that dominated our Stockholm + ship search. The finding aid confirms that the survival gap (1689-1804) means most 18th-century maritime case files are lost, even though judgments survive in the A II series. |
| **Akter i besvärs- och ansökningsmål (liber supplicationum)** | E VI a 3 aa | Case files for petition and complaint cases. Called *liber supplicationum* until 1682. | Petitions related to maritime grievances would appear here. |
| **Remisser från Kungl. Maj:t** | E VI b 1 | Criminal case files — cases remitted from the king and cases taken up directly by the hovrätt. Contains material from several *högmålsprocesser* (treason trials). | Prize cases or maritime cases of state interest might have been remitted through this channel. |
| **Bouppteckningar (noble estate inventories)** | E IX | Noble estate inventories, with a name index covering 1734-1916. | Not directly relevant to maritime jurisdiction, but potentially useful for tracing maritime wealth and ship ownership among the nobility. |

**Research aids within the archive:**

The finding aid identifies the **Kuylenstierna register** — a card index (*lappkatalog*) available on microfiche in the Riksarkivet research room, with supplementary name, place, and subject indexes in card cabinet 1. The name register also exists as a bound list. This register documents the hovrätt's judgments in chronological order with party names, summary of the judgment, and the location of case files in the *liber causarum* (E VI a 2 aa). It covers **1615-1680** — precisely the early period where maritime jurisdiction questions are most acute.

The finding aid also notes that the *Janus regius* (D I) — an alphabetical register by petitioner name over case files — covers 1614-1748, and is replaced by formal diaries (*diarier*) from 1734 onwards.

**Implications for the E VI series gap:** The finding aid explains why our ra-mcp search for Stockholm + ships in E VI a 2 aa produced hits mostly from the early 17th century and post-1804: the intervening period (1689-1704 and 1713-1804) has only fragmentary survival of case files. Judgments from this period survive in the A II domböcker, but the supporting evidence (depositions, correspondence, inventories) that would be most comparable to the English HCA Examinations series is largely lost.

---

## 4. Recommendations for Future Collaborative Research Workflows

### 4.1 RA-MCP Server: Capabilities and Limitations

**Strengths observed:**
- Full-text transcription search with advanced Solr syntax (wildcards, Boolean, fuzzy, proximity) enables discovery that metadata search alone cannot achieve
- The tool's deduplication and session memory reduce redundant calls
- Page-level hits with snippet context allow rapid triage of relevance
- Metadata search across both digitised and non-digitised holdings provides broader discovery

**Limitations observed:**
- **No exact count capability:** The tool caps at "100+" without providing precise totals, limiting quantitative analysis
- **Date filtering is imprecise:** The year_min/year_max filter catches any volume whose catalogued date range intersects the search window, not individual documents or pages dated within that range
- **Transcription quality varies:** AI-transcribed (HTR/OCR) text contains errors, particularly for older hands and non-standard orthography. Fuzzy search (~) is essential
- **Institutional coverage is uneven:** Krigsarkivet material is partially included but less consistently transcribed than Riksarkivet civilian holdings
- **Timeout risk on broad queries:** Large result sets or browsing at the fonds level can timeout; small, incremental searches are essential
- **No cross-archive aggregation:** The tool cannot tell you "how many total references to X exist across all archives" — it returns paginated results capped at reporting thresholds

### 4.2 Recommended Workflow: Structured Archival Research with RA-MCP

Based on this session, the following workflow is recommended for future research:

**Phase 1 — Scoping (metadata search + web research)**
1. Begin with metadata searches to identify relevant archival fonds, series, and creators
2. Use web search to locate published finding aids (e.g., the "Hitta i..." PDF guides) and secondary literature
3. Establish the archival hierarchy before diving into transcriptions

**Phase 2 — Systematic term mapping (transcription search)**
1. Develop a controlled vocabulary of search terms in Swedish (and variant historical spellings)
2. Search incrementally, one term cluster at a time, keeping max_results low to avoid timeouts
3. Use wildcards for morphological variants (e.g., `skepp*` catches *skepp*, *skepparen*, *skeppund*)
4. Use fuzzy search (~) for OCR/HTR error tolerance
5. Record which terms produce hits and which produce nulls — the nulls are informative

**Phase 3 — Deep reading (browse_document)**
1. For promising hits, browse full page transcriptions to understand context
2. Download nearby pages to compensate for missing context in snippets
3. Cross-reference with the original images via the bildvisaren links provided

**Phase 4 — Triangulation (web research + finding aids)**
1. Verify archival findings against secondary literature
2. Use finding aids to understand what the archive *should* contain vs. what is digitised/transcribed
3. Flag discrepancies between expected and found content
4. **Critical lesson from this session:** Published finding aids can explain patterns in ra-mcp results that the tool itself cannot. The E VI a 2 aa survival gap (1689-1804) explains why our maritime search skewed toward early 17th-century and post-1804 results — a pattern that was invisible without the finding aid.

**Phase 5 — Synthesis with explicit confidence grading**
1. Tag every claim with its source type and evidence strength
2. Distinguish direct attestation from inference from silence
3. Document search terms that returned null results — these constrain interpretation

### 4.3 Identifying High-Quality vs. Low-Quality Web Sources

A key challenge in this session was supplementing archival evidence with web research of appropriate academic quality. The following heuristics are recommended:

**Acceptable high-quality sources:**
- **Institutional websites of archives and libraries** (e.g., riksarkivet.se, nationalarchives.gov.uk) — authoritative for holdings descriptions, finding aids, and institutional history
- **Published finding aids and research guides** (e.g., "Hitta i Svea hovrätts handlingar" PDF) — these are professional archival products, though they may be dated. The Svea hovrätt guide dates from March 1998, so structural descriptions are reliable but any references to digitisation or online access may be outdated.
- **Peer-reviewed scholarship** accessible via JSTOR, DiVA (diva-portal.org for Swedish dissertations), ResearchGate, university press catalogues — the gold standard for interpretive claims
- **Encyclopaedia entries** (Britannica, Wikipedia for factual framework) — useful as starting points but must be verified. Wikipedia is acceptable for uncontroversial factual claims (dates, institutional structures) but not for interpretive arguments
- **Government and judiciary websites** (judiciary.uk, government.se) — authoritative for current and recent institutional descriptions

**Low-quality sources to treat with caution:**
- **General travel and tourism sites** (e.g., travel guides mentioning Helsingborg) — may contain historical claims but without scholarly sourcing
- **Genealogy sites** (e.g., FamilySearch, MyHeritage) — useful for understanding record types but often simplified or US-centric in framing
- **AI-generated content farms** — increasingly common in search results; identifiable by generic phrasing, lack of specific citations, and absence of named authors
- **Unattributed blog posts** — may contain valuable specialist knowledge but cannot be cited without verification

**Practical indicators of quality:**
- Does the source name its author(s) and their institutional affiliation?
- Does it cite primary sources or specific archival references?
- Is it hosted by a recognised institution (university, archive, government body, scholarly publisher)?
- Can its claims be cross-referenced against at least one other independent source?

### 4.4 Specific Recommendations for This Research Thread

If this comparative investigation of Swedish vs. English maritime jurisdiction is to be pursued further, the following steps would strengthen it:

1. **Search Krigsarkivet holdings more systematically** — the ra-mcp tool includes some KrA material (SE/KrA references appeared in our searches). A targeted search for military court-martial records (*krigsrätt*) and Amiralitetskollegium judicial records could resolve the prize court question.

2. **Consult Mia Korpiola's scholarship** — her edited volume *The Svea Court of Appeal in the Early Modern Period* (Institutet för Rättshistorisk Forskning, 2014) appeared in web search results and would likely address maritime jurisdiction directly. Available via DiVA or institutional libraries.

3. **Exploit the Kuylenstierna register** — the finding aid identifies this card index (covering 1615-1680) as the key research tool for tracing individual cases through the hovrätt. If this register has been digitised or is accessible via Riksarkivet's research room, it would allow systematic identification of maritime cases in the hovrätt's earliest decades — the period of greatest interest for understanding how maritime jurisdiction was organised before the 1667 Sjölag codification.

4. **Search the A II domböcker for the gap period** — the finding aid confirms that while E VI case files are largely lost for 1689-1804, the A II domböcker (judgments) survive from 1614. Searching transcriptions in the A II series for maritime terminology could recover evidence of maritime cases that the E VI gap obscures.

5. **Search for *uppbringning* and related terms** — if prize cases used different terminology than *prisrätt*, a broader semantic search could locate them.

6. **Compare with Danish and Norwegian systems** — the Sjölagen of 1667 was part of a broader Scandinavian codification wave (Danish 1683, Norwegian following Danish law). Comparative Scandinavian scholarship may illuminate what is distinctive about the Swedish approach.

7. **Consult Lennart Lundquist's revised PM** — the finding aid references this document (held in the Riksarkivet research room) as supplementary literature. It may contain guidance on navigating maritime-related cases within the hovrätt archive.

### 4.5 Recommendation: Create an RA-MCP Collaborative Research Skill File

This session has demonstrated that effective use of the ra-mcp server for academic research requires a specific workflow discipline that is unlikely to emerge spontaneously in each new Cowork session. The following knowledge needs to be encoded and made reusable:

- The five-phase research workflow (scoping → term mapping → deep reading → triangulation → synthesis)
- The incremental search strategy to avoid timeouts
- The controlled vocabulary approach for Swedish-language archival searches
- The confidence-grading framework for tagging claims
- The source-quality heuristics for web research
- The principle that finding aids explain patterns that the ra-mcp tool alone cannot
- Documentation conventions for recording null results alongside positive findings

**Recommendation:** Create a skill file named `ra-mcp-collaborative-research` conforming to the Anthropic Agent Skills standard (as documented in the Metaskill Architecture Memo v1.1, 7 February 2026). The skill file should:

1. Use **Architecture A (Distributed, Principle-Oriented)** from the Metaskill memo — a lean SKILL.md with companion reference files — because the research workflow is inherently open-ended and principle-based, not template-driven. New research topics will differ substantially from Swedish maritime jurisdiction, so pattern-matching from a single worked example would be less useful than understanding the underlying workflow principles.

2. Place the SKILL.md in the `Skills/` subfolder (or a dedicated skill bundle directory) with YAML frontmatter conforming to Anthropic validation requirements.

3. Include a `references/` directory designed to grow over time, with reference files for specific archival domains (e.g., `references/svea-hovratt-guide.md` summarising the "Hitta i..." finding aid, `references/hca-comparison.md` encoding what we learned about HCA for future comparative work). Each new research session could contribute a reference file, building institutional knowledge incrementally.

4. Include this memo (or a condensed version) as a reference file documenting the founding research session and the rationale behind the workflow design.

A draft SKILL.md conforming to the Anthropic standard is provided in **Appendix D**.

---

## 5. Reflections on the Collaborative Research Process

This session demonstrated both the power and the limitations of human-AI collaborative research using MCP-connected archival databases. Several observations are worth recording:

**What worked well:**
- The Socratic approach — Colin's questions drove the investigation in productive directions, while Claude's systematic search strategy mapped the semantic field methodically
- Incremental searching avoided timeouts and built understanding progressively
- Explicit confidence grading maintained intellectual honesty about what the evidence supports
- The combination of archival search (primary evidence) and web search (secondary context) provided triangulation
- The late-stage incorporation of the published finding aid demonstrated the importance of human-supplied context that no automated tool could have retrieved

**What could be improved:**
- The session would have benefited from a pre-planned controlled vocabulary of Swedish legal-historical terms before beginning searches
- The distinction between what the ra-mcp tool covers (primarily Riksarkivet civilian holdings) and what it does not (full Krigsarkivet coverage) should have been established earlier
- The inability to fetch certain web resources (PDFs, paywalled scholarship) created gaps that could not be filled within the session — but the finding aid example shows that the researcher can bridge these gaps by supplying content directly
- A more systematic approach to recording null results (terms searched that returned nothing) would strengthen the argument from silence

**On the nature of the evidence:**
The ra-mcp server provides access to AI-transcribed historical documents — not original manuscripts, not scholarly editions, but machine-generated readings of handwritten and printed historical texts. This creates an unusual evidential situation: the transcriptions are useful for *discovery* (finding that a Sjörätt existed in Skanör) but must be treated with caution for *close reading* (exact wording, spelling, precise legal terminology). Any claim derived from these transcriptions that will be used in published scholarship should be verified against the original page images via the bildvisaren links.

The finding aid also reveals a **survivorship bias** in the ra-mcp results: the E VI case files are largely lost for 1689-1804, meaning that searches across this period are systematically biased toward documents that happen to survive, not a representative sample of what the court actually handled. Without the finding aid, this bias would be invisible.

---

## Appendix A: Conversation Prompts (Sequential)

The following are the prompts given by Colin Greenstreet during this research session, in chronological order:

### Prompt 1
> Do you have access to ra-mcp tools?

### Prompt 2
> Search metadata across the whole api for the period 1610-1620 and tell me how many instances you have of Stockholm

### Prompt 3
> Can you search "Stockholm" AND "ship" for that period?

### Prompt 4
> Tell me more about SE/RA/420422/01

### Prompt 5
> Does the Swedish National Archive have published finding aids for the Svea Hovrätt — Huvudarkivet (Svea Court of Appeal — Main Archive)? Try a web search

### Prompt 6
> How does the Huvudarkivet (Svea Court of Appeal — Main Archive) compare with the English High Court of Admiralty in terms of jurisdiction, legal approach, structure? Did Sweden have a separate Court of Admiralty at national, regional or local levels. Be very clear what your sources are in your answer and how clear or not you are about different parts of the comparison.

### Prompt 7
> Search the ra=mcp server carefully and in small steps to avoid time outs to look for the Swedish language equivalent of "Prize Court" or "Admiralty Court" or related terms. Summarise your findings in a structured academically credible manner, citing sources

### Prompt 8
> Now write a MD memo and store in a new subfolder in the MCP folder called mcp-server-output
>
> Describe the goal, methodology, documentation approach, methodical academic approach, with clear citation, and the full synthesised content output, and include as an appendix all the prompts (sequentially) I have given you in this conversation
>
> Make recommendations based on our interaction in this conversation and your knowledge of how the ra-mcp server works, and existence of online finding aids, how we can improve in collaborative research in the future, in terms of workflows, centred on the ra-mcp server but contextualised and supplemented by web research. Include suggestions as to how we might find "acceptable high quality academic websources" vs. low quality sources

### Prompt 9
> Here is the PDF you could not access. Should any of its content be included in a revised versioned MD file? [PDF content of "Hitta i Svea hovrätts handlingar" supplied]
>
> Make a recommendation that a ra-mcp-collaborative-research-skill.md file should be created, with the ability to add further reference md files. Consult the metaskill file in the Sandbox skill subfolder [Metaskill_Architecture_Memo_v1_1_07022026.md] and draft an initial file which is fully Anthropic format compliant and put in the appendix

---

## Appendix B: Key Archival References Cited

| Reference Code | Institution | Description | Source |
|----------------|-------------|-------------|--------|
| SE/RA/420422/01 | Riksarkivet i Stockholm/Täby | Svea Hovrätt, Huvudarkivet | ra-mcp metadata |
| SE/VaLA/03825/01/A II/68 | Riksarkivet i Vadstena | Göta hovrätt (contains SjöRätten i Skanör reference, 1784) | ra-mcp transcription |
| SE/VaLA/03825/01/A II/94 | Riksarkivet i Vadstena | Göta hovrätt (contains SjöRätten i Helsingborg reference, 1802) | ra-mcp transcription |
| SE/VaLA/03825/01/A II/67 | Riksarkivet i Vadstena | Göta hovrätt (contains Sjörrättens LandsCrona reference, 1783) | ra-mcp transcription |
| SE/VaLA/03825/01/A II/73 | Riksarkivet i Vadstena | Göta hovrätt (contains SjöRätten reference, 1789) | ra-mcp transcription |
| SE/KrA/0500-0503/0500/001 | Krigsarkivet | Amiralitetskollegium, kansliet (1630-1807) | ra-mcp metadata |
| SE/RA/420132/1/F V a/1 | Riksarkivet i Stockholm/Täby | Kommerskollegium, sjöfartsbestämmelser (1665-) | ra-mcp metadata |

## Appendix C: Key Web Sources Cited

- Riksarkivet. "Svea Hovrätt — overview." https://sok.riksarkivet.se/?postid=ArkisRef+SE/RA/420422
- Riksarkivet, Forskarserviceavdelningen. "Hitta i Svea hovrätts handlingar." Mars 1998. PDF: https://cdn.abicart.com/shop/25093/art71/17617871-40bf95-hitta_i_svea_hovratts_handlingar.pdf
- Britannica. "High Court of Admiralty." https://www.britannica.com/topic/High-Court-of-Admiralty
- Britannica. "Maritime law." https://www.britannica.com/topic/maritime-law
- UK Judiciary. "History of the Admiralty Court." https://www.judiciary.uk/courts-and-tribunals/business-and-property-courts/admiralty-court/history/
- Högman, Hans. "Swedish Maritime Piloting History." https://www.hhogman.se/maritime-piloting-swe.htm
- Korpiola, Mia, and Hemmer. "Early modern court records and petitions in Sweden (c.1400-1809)." ResearchGate. https://www.researchgate.net/publication/332835229
- IEG-EGO. "The Scandinavian Legal System." https://www.ieg-ego.eu/en/threads/crossroads/legal-families/wilhelm-brauneder-the-scandinavian-legal-system

## Appendix D: Draft Skill File — ra-mcp-collaborative-research

The following is a draft SKILL.md conforming to the Anthropic Agent Skills standard as documented in the Metaskill Architecture Memo v1.1 (7 February 2026). It follows Architecture A (Distributed, Principle-Oriented) with a lean SKILL.md and companion reference files.

### SKILL.md

```yaml
---
name: ra-mcp-collaborative-research
description: Use this skill when conducting structured academic research using the
  Riksarkivet (Swedish National Archives) MCP server (ra-mcp). Triggers when the
  user asks to search Swedish archival holdings, investigate historical questions
  using Riksarkivet data, or conduct systematic research combining archival
  transcription searches with metadata searches and web-based secondary sources.
  Covers workflow design, search strategy, confidence grading, source evaluation,
  and structured documentation of findings.
---
```

# RA-MCP Collaborative Research Skill

## Purpose

This skill guides structured academic research using the Riksarkivet MCP server (ra-mcp) within Claude Cowork. It encodes a five-phase workflow for combining archival primary evidence with web-based secondary sources, producing findings with explicit confidence grading and academic citation.

## Prerequisites

Before beginning a research session, read the following reference files if they exist in `references/`:

1. `references/workflow-principles.md` — the five-phase research workflow and rationale
2. Any domain-specific reference files relevant to the research topic (e.g., `references/svea-hovratt-guide.md`, `references/hca-comparison.md`)

If no reference files exist yet, proceed using the workflow principles embedded in this SKILL.md and create reference files as the session produces reusable knowledge.

## The Five-Phase Workflow

### Phase 1 — Scoping

**Goal:** Establish what archives exist, what is digitised, and what published finding aids are available.

**Actions:**
1. Use `search_metadata` with broad terms to identify relevant archival fonds, series, and creators
2. Use `WebSearch` to locate published finding aids (especially Riksarkivet's "Hitta i..." PDF guides) and secondary literature
3. Map the archival hierarchy before diving into transcriptions
4. Identify which institutions hold relevant records (Riksarkivet, Krigsarkivet, regional archives)
5. Note the distinction between digitised (searchable via ra-mcp) and non-digitised holdings

**Constraint:** Keep `max_results` low (10-25) and `max_response_tokens` moderate (5000-10000) to avoid timeouts.

### Phase 2 — Systematic Term Mapping

**Goal:** Map the semantic field in the target language(s) using the transcription search.

**Actions:**
1. Develop a controlled vocabulary of search terms in Swedish (and variant historical spellings)
2. Search incrementally — one term cluster at a time
3. Use wildcards (`*`) for morphological variants (e.g., `skepp*` catches *skepp*, *skepparen*, *skeppund*)
4. Use fuzzy search (`~`) for OCR/HTR error tolerance and historical spelling variants
5. Use Boolean operators for compound concepts: `((term1 OR term2) AND (term3 OR term4))`
6. **Record every search term and its result count**, including nulls — null results constrain interpretation

**Constraint:** The ra-mcp transcriptions are AI-generated (HTR/OCR). Expect errors, especially in older hands. Never trust a single transcription reading for close textual analysis.

### Phase 3 — Deep Reading

**Goal:** Understand the context of promising hits by reading full page transcriptions.

**Actions:**
1. Use `browse_document` to retrieve full pages for high-value hits
2. Browse nearby pages to compensate for missing context in search snippets
3. Note the bildvisaren links for verification against original images
4. Record reference codes, page numbers, and relevant excerpts

**Constraint:** Browse specific volumes (e.g., `SE/RA/420422/01/E VI a 2 aa/19`), not fonds-level reference codes, to avoid timeouts.

### Phase 4 — Triangulation

**Goal:** Verify archival findings against external evidence and identify gaps.

**Actions:**
1. Cross-reference ra-mcp findings with secondary literature (web search)
2. Use published finding aids to understand what the archive *should* contain vs. what is searchable
3. Flag survivorship bias — archival gaps (e.g., lost series, undigitised holdings) create systematic distortions in search results
4. Evaluate web sources using the quality heuristics below

**Source quality heuristics:**

*High quality:* Institutional archive/library websites; published finding aids; peer-reviewed scholarship (JSTOR, DiVA, university presses); government/judiciary websites; encyclopaedias (for factual claims only).

*Low quality:* Travel/tourism sites; genealogy sites (useful but simplified); AI-generated content farms; unattributed blog posts.

*Quality indicators:* Named author with institutional affiliation; cites primary sources or archival references; hosted by recognised institution; cross-referenceable against independent sources.

### Phase 5 — Synthesis

**Goal:** Produce a structured account of findings with explicit confidence grading.

**Actions:**
1. Tag every claim with its **source type**: ra-mcp transcription, ra-mcp metadata, web search, published finding aid, training knowledge
2. Tag every claim with its **evidence strength**: strong (direct attestation), moderate (inferred from clear evidence), weak (argument from silence)
3. Document null results alongside positive findings — what you searched for and did not find
4. Produce a structured output (typically markdown) with clear sections for methodology, findings, and source citations
5. Separate archival sources (with full reference codes) from web sources in the citation apparatus

## Documentation Conventions

**For ra-mcp archival citations:** Use full reference codes with institution, page numbers, and date where available. Example: SE/VaLA/03825/01/A II/68, pp. 602-603 (Riksarkivet i Vadstena, 1784).

**For web citations:** Use author/institution, title, URL. Note access date if content may change.

**For null results:** Record as: "Search for [term] in [tool] with [parameters] returned zero results."

**For confidence assessments:** Use the three-tier scale consistently: Strong / Moderate / Weak, with a brief justification for each rating.

## Growing the Reference Library

After each research session, consider whether any findings should be saved as a new reference file in `references/`. Good candidates include:

- Summaries of published finding aids (e.g., the "Hitta i..." guides)
- Controlled vocabularies developed for specific archival domains
- Comparative frameworks (e.g., English HCA vs. Swedish courts)
- Lessons learned about ra-mcp tool behaviour and limitations
- Domain-specific search strategies that proved effective

Reference files should be named descriptively in kebab-case (e.g., `svea-hovratt-guide.md`, `maritime-terminology-swedish.md`) and include a version header.

## Constraints

1. **Never present ra-mcp transcriptions as definitive text.** They are AI-generated readings of historical manuscripts. Always note this evidential status.
2. **Always search incrementally.** Keep max_results low, search one term cluster at a time, avoid fonds-level browse_document calls.
3. **Always record null results.** They are evidence, not failures.
4. **Always distinguish source types.** Never blend ra-mcp evidence with training knowledge without flagging the distinction.
5. **Always check for published finding aids** before interpreting ra-mcp search patterns. Archival gaps explain search patterns that the tool alone cannot.

```

### Proposed references/ directory (initial contents)

```
ra-mcp-collaborative-research/
├── SKILL.md                                    # As above
└── references/
    ├── workflow-principles.md                   # Extracted from this memo, Sections 4.2 and 4.3
    ├── svea-hovratt-guide.md                    # Summary of "Hitta i Svea hovrätts handlingar" (1998)
    ├── swedish-maritime-jurisdiction-session.md  # Condensed version of this memo as a worked example
    └── ra-mcp-tool-behaviour.md                 # Documented capabilities, limitations, and workarounds
```

Each file would include a version header per the conventions in CLAUDE.md Section 3. New research sessions would contribute additional reference files as the knowledge base grows.
