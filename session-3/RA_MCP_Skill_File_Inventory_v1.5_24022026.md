# RA-MCP Skill File Inventory

**Version:** 1.5
**Date:** 24 February 2026
**Author:** Claude Opus 4.6, prompted by Colin Greenstreet
**Purpose:** Comprehensive inventory of all skill files, reference files, and skill-adjacent documents developed around the Riksarkivet MCP server (ra-mcp), prepared for Collaboratory Session 3 planning.

**Version history:**
- **v1.5** (24 Feb 2026) — Added table of contents (this section). Noted author. Added intellectual path summary to Section 0 (Summary). Updated SKILL.md version to 1.1 (24 Feb) and workflow-principles.md version to 1.2 (24 Feb) throughout Sections 1.3, 2.1, 3, and 7. Added two new archived files (SKILL_v1.0_17022026.md and workflow-principles_v1.1_17022026.md) to Section 3. Updated Section 6 silent failure note to reflect that the warning has now been written into both skill files.
- **v1.4** (24 Feb 2026) — Added boosting test results (Test 6a–6c): boosting works but only with explicit Boolean grouping; bare space-separated syntax silently returns zero results. Updated test table in Section 6 and added "Silent failure" warning.
- **v1.3** (24 Feb 2026) — Added intellectual provenance for the collaborative research skill file: documents how it adapts Tom Scheinfeldt's digital reference interview model (Section 1.3 and new Section 8). Noted boosting (`term^4`) as standard Solr syntax, assumed operational but untested (Section 6). Updated relationship diagram.
- **v1.2** (24 Feb 2026) — Corrected attribution for ra-research-studio-plus: created by Mark Thompson (University of Groningen), not by Riksarkivet. Added provenance details (sent to Colin 19 Feb 2026, built using Google AI Studio). Mark Thompson may demo the application at today's Collaboratory session.
- **v1.1** (24 Feb 2026) — Added Section 6: Solr syntax retest results (all five query types pass, resolving the 16 Feb discrepancy). Clarified ra-research-studio-plus description (client application, not server copy; Docker status uncertain). Updated timeline. **Note:** v1.0 was overwritten in error rather than preserved as a separate file — an archiving protocol violation.
- **v1.0** (24 Feb 2026) — Initial inventory. Flagged Solr syntax discrepancy as unresolved.

---

## Table of Contents

- [Summary](#summary)
- [1. Formal Skill Files (Anthropic YAML-Compliant)](#1-formal-skill-files-anthropic-yaml-compliant)
  - [1.1 mcp-server-debug-windows](#11-mcp-server-debug-windows-skillmd)
  - [1.2 ra-mcp (basic use) — SUPERSEDED](#12-ra-mcp-basic-use--superseded)
  - [1.3 ra-mcp-collaborative-research — CURRENT](#13-ra-mcp-collaborative-research-skillmd--current)
- [2. Active Reference Files](#2-active-reference-files)
  - [2.1 workflow-principles.md](#21-workflow-principlesmd)
  - [2.2 swedish-authority-guide.md](#22-swedish-authority-guidemd)
  - [2.3 swedish-early-modern-legal-terminology.md](#23-swedish-early-modern-legal-terminologymd)
  - [2.4 ra-mcp-specifics.md](#24-ra-mcp-specificsmd)
- [3. Archived/Superseded Files](#3-archivedsuperseded-files)
- [4. Skill-Adjacent Documents](#4-skill-adjacent-documents-not-formal-skill-files)
- [5. Development Timeline](#5-development-timeline)
- [6. Key Discrepancy — RESOLVED](#6-key-discrepancy--resolved-24-february-2026)
- [7. Relationship Diagram](#7-relationship-diagram)
- [8. Intellectual Provenance: The Scheinfeldt Connection](#8-intellectual-provenance-the-scheinfeldt-connection)

---

## Summary

Colin has developed **three formal skill files** related to the ra-mcp server, supported by **four active reference files** and **seven archived versions**. Development spanned **16–17 February 2026** (8 days before the Collaboratory session), with refinements and testing continuing on **24 February 2026**.

The most substantive skill file — `ra-mcp-collaborative-research` — adapts the **digital reference interview** model demonstrated by Tom Scheinfeldt (University of Connecticut) into a formalised academic research methodology for the Riksarkivet archive. The intellectual path ran from Scheinfeldt's conversational AI archivist through Colin's maritime jurisdiction research session to a five-phase workflow that adds structured confidence grading, null result documentation, survivorship bias awareness, and a growing reference library (see [Section 8](#8-intellectual-provenance-the-scheinfeldt-connection) for the full mapping).

A separate **browser-based research application** (ra-research-studio-plus) was created by Collaboratory member **Mark Thompson** (University of Groningen) and shared with Colin on 19 February 2026.

---

## 1. Formal Skill Files (Anthropic YAML-Compliant)

### 1.1 mcp-server-debug-windows (SKILL.md)

| Field | Value |
|-------|-------|
| Location | `MCP/mcp-server-debug-windows/SKILL.md` |
| Version | 2.0 (16 February 2026) |
| YAML compliant | **Yes** — has `name` and `description` in YAML frontmatter |
| Parent/child | **Parent** of all other ra-mcp skill work — without solving the connection problem, nothing else was possible |
| Goal | Structured, non-repeating debugging protocol for MCP servers that fail to load in Claude Desktop on Windows |
| Approach | Six-phase decision tree: Phase Zero (MSIX config path verification), then Phases 1–5 (log reading → PATH/environment → config parsing → timeout → transport mismatch), plus anti-patterns |
| Key discovery | The MSIX config path bug — Claude Desktop installed from Microsoft Store reads a virtualised config path, not the one its own "Edit Config" button opens. Bug reported to Anthropic (support ID 215473123211857) |
| Reference files | 1 active: `references/ra-mcp-specifics.md` (v1.0, 16 Feb) |
| History | v1.0 was created and archived same day; v2.0 added YAML frontmatter, extracted server-specific data to reference file, added three content improvements |

### 1.2 ra-mcp (basic use) — SUPERSEDED

| Field | Value |
|-------|-------|
| Location | `MCP/Skills-ra-mcp-collaborative-research/references/archive/ra-mcp-SKILL_v2.0_16022026_SUPERSEDED.md` |
| Version | 2.0 (16 February 2026) — **superseded** |
| YAML compliant | **Yes** — has `name: ra-mcp` and `description` in YAML frontmatter |
| Parent/child | **Daughter** of debug skill (created same day after connection was established); **parent** of the collaborative research skill (its content was absorbed and restructured) |
| Goal | Operational guide for using the three ra-mcp tools (`search_transcribed`, `search_metadata`, `browse_document`) |
| Approach | Tool descriptions, critical constraints (especially single-keyword limitation), recommended workflows, workarounds |
| Key finding | `search_transcribed` accepts **single-keyword queries only** — **this was later shown to be incorrect** (see Section 6) |
| Reference files at time of supersession | `test-findings.md` (v1.0, 16 Feb — also superseded), `swedish-authority-guide.md` (v1.0, 16 Feb — superseded, then revised) |
| History | v1.0 was created on 16 Feb without YAML frontmatter; v2.0 added YAML compliance, extracted reference files, restructured. Both versions were superseded on 17 Feb when the collaborative research skill absorbed their content |

### 1.3 ra-mcp-collaborative-research (SKILL.md) — CURRENT

| Field | Value |
|-------|-------|
| Location | `MCP/Skills-ra-mcp-collaborative-research/SKILL.md` |
| Version | 1.1 (24 February 2026) |
| YAML compliant | **Yes** — has `name: ra-mcp-collaborative-research` and `description` in YAML frontmatter |
| Also registered | In Anthropic's skill system (appears in `<available_skills>` at session start) |
| Parent/child | **Daughter** of the basic use skill (v2.0) — absorbed its operational content and added a five-phase research methodology |
| Intellectual provenance | Adapts the **digital reference interview** model demonstrated by **Tom Scheinfeldt** (University of Connecticut) in his ArchivesSpace MCP demo ("Sourcery for ArchivesSpace"). Colin, working with Claude Cowork, took Scheinfeldt's conversational approach to archival research — iterative search refinement, transparent explanation of collection scope and limitations, escalation when searches fail — and formalised it into an academically structured methodology tailored to the Riksarkivet archive and the ra-mcp server's specific capabilities. See Section 8 for a detailed mapping |
| Goal | Structured academic research using the ra-mcp server, combining archival primary evidence with web-based secondary sources, producing findings with explicit confidence grading |
| Approach | Five-phase workflow: (1) Scoping — map archives and finding aids; (2) Systematic Term Mapping — build controlled vocabulary in Swedish; (3) Deep Reading — browse full pages; (4) Triangulation — verify against secondary literature; (5) Synthesis — structured output with confidence grading and source-type tagging |
| Key principles | Never present AI transcriptions as definitive; always record null results; always distinguish source types; check published finding aids before interpreting search patterns |
| What the skill file adds beyond Scheinfeldt | (a) Structured confidence grading (three-tier: strong/moderate/weak) with explicit source-type tagging; (b) Systematic documentation of null results as evidence; (c) Triangulation against secondary literature and published finding aids; (d) Survivorship bias awareness — interpreting search patterns in light of what the archive *should* contain; (e) Growing reference library — each session produces reusable reference files for future research |
| Reference files | 3 active (see Section 2 below) |
| History | Created 17 Feb after a full research session on Swedish maritime jurisdiction that demonstrated the need for a structured methodology beyond basic tool usage. Shared with Tom Scheinfeldt on 18 Feb 2026. Updated to v1.1 on 24 Feb: added proximity search and boosting (with silent failure caveat) to Phase 2 actions; added in-text version header |

---

## 2. Active Reference Files

### 2.1 workflow-principles.md

| Field | Value |
|-------|-------|
| Location | `MCP/Skills-ra-mcp-collaborative-research/references/workflow-principles.md` |
| Version | 1.2 (24 February 2026) |
| Parent skill | ra-mcp-collaborative-research |
| Content | Tool behaviour observations (including boosting silent failure warning), source-quality heuristics for web research, the survivorship bias problem, controlled vocabulary approach, documentation standards (three-tier confidence grading, citation format, null result recording) |
| Derived from | The 17 Feb maritime jurisdiction research session; boosting caveat added from 24 Feb structured testing |

### 2.2 swedish-authority-guide.md

| Field | Value |
|-------|-------|
| Location | `MCP/Skills-ra-mcp-collaborative-research/references/swedish-authority-guide.md` |
| Version | 1.2 (17 February 2026) |
| Parent skill | ra-mcp-collaborative-research |
| Content | Thematic index of Swedish administrative domains (justice, taxation, church, regional government, land, social welfare, education, trade/transport, military, crisis/rationing) with Swedish search terms for `search_transcribed` and `search_metadata`. Derived from the ra-mcp server's `get_table_of_contents` resource |
| History | v1.0 (16 Feb) → v1.1 (17 Feb) → v1.2 (17 Feb). Two superseded versions archived |

### 2.3 swedish-early-modern-legal-terminology.md

| Field | Value |
|-------|-------|
| Location | `MCP/Skills-ra-mcp-collaborative-research/references/swedish-early-modern-legal-terminology.md` |
| Version | 1.1 (17 February 2026) |
| Parent skill | ra-mcp-collaborative-research |
| Content | Controlled vocabulary of Swedish early modern legal and judicial terms with English equivalents, covering courts, legal codes, judicial officers, administrative geography, punishments, petitions, court records, and research themes. Primary source: Liliequist & Almbjär (2012) on court records and petitions c. 1400–1809 |
| History | v1.0 (17 Feb) archived. v1.0 misattributed the article to Mia Korpiola; v1.1 corrected the attribution |

### 2.4 ra-mcp-specifics.md

| Field | Value |
|-------|-------|
| Location | `MCP/mcp-server-debug-windows/references/ra-mcp-specifics.md` |
| Version | 1.0 (16 February 2026) |
| Parent skill | mcp-server-debug-windows |
| Content | Server identity (v0.5.3, FastMCP 3.0.0b2), installation procedure, three known-good config entries (venv executable, uv with env, HTTP transport), startup verification output, complete debugging history (all eight failed approaches before MSIX discovery), known Cowork VM constraints |

---

## 3. Archived/Superseded Files

| File | Location | Version | Date | Superseded by |
|------|----------|---------|------|---------------|
| `SKILL_v1.0_17022026.md` | `references/archive/` | 1.0 | 17 Feb | Current SKILL.md v1.1 (24 Feb) |
| `workflow-principles_v1.1_17022026.md` | `references/archive/` | 1.1 | 17 Feb | Current workflow-principles.md v1.2 (24 Feb) |
| `workflow-principles_v1.0_17022026.md` | `references/archive/` | 1.0 | 17 Feb | v1.1 (17 Feb) |
| `ra-mcp-SKILL_v2.0_16022026_SUPERSEDED.md` | `references/archive/` | 2.0 | 16 Feb | Current ra-mcp-collaborative-research SKILL.md |
| `test-findings_v1.0_16022026_SUPERSEDED.md` | `references/archive/` | 1.0 | 16 Feb | Absorbed into workflow-principles.md |
| `swedish-authority-guide_v1.0_16022026_SUPERSEDED.md` | `references/archive/` | 1.0 | 16 Feb | Current v1.2 |
| `swedish-authority-guide_v1.1_17022026.md` | `references/archive/` | 1.1 | 17 Feb | Current v1.2 |
| `swedish-early-modern-legal-terminology_v1.0_17022026.md` | `references/archive/` | 1.0 | 17 Feb | Current v1.1 |

---

## 4. Skill-Adjacent Documents (Not Formal Skill Files)

### 4.1 ra-research-studio-plus (application)

| Field | Value |
|-------|-------|
| Location | `MCP/ra-research-studio/ra-research-studio-plus/` |
| Type | Browser-based research application (HTML + Python server), **not a skill file** |
| Author | **Mark Thompson** (University of Groningen, Collaboratory member) |
| Provenance | Built using Google AI Studio ("Google Antigravity's IDE"). Sent to Colin as `ra-research-studio-plus.zip` on **19 February 2026**. Mark had tried the Riksarkivet MCP setup, got it working as a "guided terminal", then built this HTML/Gemini interface as an alternative front end |
| Content | An interactive web interface with AI-powered chat (Google Gemini) for searching the Riksarkivet archives. Includes manual search tabs and an AI chat that translates English queries to Swedish, searches, and summarises results |
| Architecture | User's browser → Google Gemini API → Python proxy server (serve.py) → Docker container running ra-mcp on port 7860 → Riksarkivet APIs |
| Audience | Non-technical researchers; README includes "How to Open a Terminal" instructions |
| YAML compliant | **No** — this is an application, not a skill file |
| Relationship to skill files | Provides a **parallel access route** to the same underlying Riksarkivet data, but via Gemini rather than Claude. Complementary, not competitive |
| Important distinction | This is a **client application**, not a copy of the ra-mcp server. It requires a separate Docker container running `riksarkivet/ra-mcp:latest` on port 7860. The locally installed server at `C:\Users\colin\ra-mcp\` (which connects to Claude Desktop via `ra-serve.exe`) is a separate installation. They access the same Riksarkivet APIs but are independent processes |
| Status | Mark Thompson may demo this application at today's Collaboratory session (24 Feb 2026) |

### 4.2 Test documentation

| File | Date | Type |
|------|------|------|
| `ra-mcp_Test_Prompts_v1.0_16022026.md` | 16 Feb | Seven structured test prompts for verifying ra-mcp connectivity and functionality |
| `ra-mcp-test-report_v1.0_16022026.md` | 16 Feb | Detailed results from executing all seven test prompts |

### 4.3 Research output

| File | Date | Type |
|------|------|------|
| `ra-mcp-server-output/RA_MCP_Swedish_Maritime_Jurisdiction_Research_Memo_v1.1_17022026.md` | 17 Feb | The founding research session that generated the collaborative research skill — a full investigation of Swedish maritime jurisdiction using ra-mcp |
| `ra-mcp-server-output/TODO_RA_MCP_Research_Follow_Up_v1.0_17022026.md` | 17 Feb | Follow-up tasks identified during the maritime jurisdiction session |
| `ra-mcp-server-output/EarlymoderncourtrecordsandpetitionsinSwedenc.1400-1809overviewandresearchtrends.pdf` | 17 Feb | Source PDF (Liliequist & Almbjär 2012) used to build the legal terminology reference file |

---

## 5. Development Timeline

| Date | What happened |
|------|---------------|
| **16 Feb** | (1) Attempted to connect ra-mcp to Claude Desktop; failed repeatedly due to MSIX config path bug. (2) Created debug skill file v1.0, then v2.0. (3) Once connected, ran seven structured tests. Created test prompts, test report, and basic use skill file v1.0 → v2.0. Created swedish-authority-guide v1.0 and test-findings v1.0 |
| **17 Feb** | (4) Conducted full maritime jurisdiction research session. (5) Created collaborative research skill file (absorbing basic use skill, adapting Scheinfeldt's reference interview model into a formalised five-phase methodology). Created workflow-principles, swedish-early-modern-legal-terminology, revised swedish-authority-guide to v1.2. Multiple archive cycles |
| **18 Feb** | (6) Tom Scheinfeldt shared ArchivesSpace MCP demo URL. Colin shared collaborative research skill file and three reference files back to Scheinfeldt |
| **19 Feb** | (7) Mark Thompson (Groningen) sent ra-research-studio-plus.zip — a Gemini-powered browser interface for the Riksarkivet archive, built using Google AI Studio |
| **24 Feb** | (8) Created IWAC briefing for Collaboratory session. (9) This inventory (v1.0–v1.5). (10) Retested Solr syntax — all five query types pass; 16 Feb single-keyword limitation finding was wrong. (11) Tested boosting — works with explicit Boolean grouping but bare space-separated syntax silently fails. (12) Updated SKILL.md to v1.1 and workflow-principles.md to v1.2 to document proximity search and boosting (with silent failure caveat) |

---

## 6. Key Discrepancy — RESOLVED (24 February 2026)

The **superseded basic use skill** (v2.0, 16 Feb) and the **test report** (v1.0, 16 Feb) documented that `search_transcribed` accepted single-keyword queries only, with multi-word, Boolean, wildcard, and proximity queries returning HTTP 400 errors. However, the **current collaborative research SKILL.md** (17 Feb) describes full Solr query syntax support.

**Resolution:** Retesting on 24 February 2026 (via Claude Desktop Chat) confirmed that the **current skill file is correct**. Full Solr syntax is operational. The 16 February test findings were wrong — the server was not updated; the original tests were flawed (cause unknown but possibly a transient issue or parameter formatting error).

### Retest results (24 February 2026)

| Test | Query | Result | Hits | Notes |
|------|-------|--------|------|-------|
| 1 | `trolldom` | **PASS** | 63 / 42+ volumes | Baseline confirmed |
| 2 | `troll*` | **PASS** | 236 / 100+ volumes | Wildcard operational — matches trolldom, Trollhättan, trolleuren, etc. |
| 3 | `((troll* OR häx*) AND Stockholm)` | **PASS** | 300 / 100+ volumes | Boolean + wildcards work. Contradicts 16 Feb HTTP 400 finding |
| 4 | `"trolldom Stockholm"~10` | **PASS** | 3 / 2 volumes | Proximity search operational |
| 5 | `trolldom~1` | **PASS** | 219 / 100+ volumes | Fuzzy search operational — found trulldoms, troldom, Throlldom, drolldom, trolldomb |
| 6a | `trolldom^4 häxeri` | **FAIL** | 0 results | Implicit multi-term with boost — silently returns zero results (no error) |
| 6b | `trolldom^4` | **PASS** | 63 / 42+ volumes | Boost on single term works (same count as unboosted; affects ranking only) |
| 6c | `(trolldom^4 OR häxeri)` | **PASS** | 72 / 46+ volumes | Boost with explicit Boolean grouping works correctly |

**Full Solr query syntax confirmed operational as of 24 February 2026, with one constraint on boosting.**

### Silent failure warning

Boosting (`term^4`) works, but **only within explicit Boolean grouping**. The bare space-separated syntax `trolldom^4 häxeri` silently returns zero results rather than erroring — which is more dangerous than an HTTP 400, since it gives no indication that the query was malformed. The fix is straightforward: always wrap boosted multi-term queries in parentheses with an explicit operator (e.g., `(trolldom^4 OR häxeri)` rather than `trolldom^4 häxeri`).

This silent failure pattern has been documented in both **SKILL.md v1.1** (Phase 2, item 7) and **workflow-principles.md v1.2** (Section 1, boosting caveat paragraph).

### Implications

- The **superseded skill file's** "Critical Constraints" section (single-keyword limitation and workarounds) is obsolete and should not be relied upon
- The **current collaborative research skill file** (v1.1) correctly describes the server's capabilities, including the boosting constraint
- The **IWAC briefing** (v1.0) comparison table entry "Single-keyword full-text only; no boolean/phrase" for ra-mcp is **wrong** and must be corrected
- The ra-mcp server's search capabilities are substantially richer than previously documented: wildcards for morphological variation, Boolean for compound queries, proximity for co-occurrence, fuzzy matching for scribal/OCR variation, and boosting for term weighting (with explicit grouping)

---

## 7. Relationship Diagram

```
mcp-server-debug-windows (SKILL.md v2.0, 16 Feb)
  └── references/ra-mcp-specifics.md (v1.0)
  └── [Enabled connection to ra-mcp server]
        │
        ▼
ra-mcp basic use (SKILL.md v2.0, 16 Feb) ← SUPERSEDED
  └── references/test-findings.md (v1.0) ← SUPERSEDED
  └── references/swedish-authority-guide.md (v1.0) ← SUPERSEDED
  └── [Content absorbed into ↓]
        │
        ▼
ra-mcp-collaborative-research (SKILL.md v1.1, 24 Feb) ← CURRENT
  ├── Intellectual provenance: Scheinfeldt's digital reference interview
  ├── Added: confidence grading, null result documentation, triangulation,
  │   survivorship bias awareness, growing reference library
  ├── references/workflow-principles.md (v1.2)
  ├── references/swedish-authority-guide.md (v1.2)
  └── references/swedish-early-modern-legal-terminology.md (v1.1)

ra-research-studio-plus (Mark Thompson, Groningen, 19 Feb) ← PARALLEL ACCESS ROUTE
  └── README.md, index.html, serve.py
  └── [Requires Docker container; uses Gemini not Claude]
```

---

## 8. Intellectual Provenance: The Scheinfeldt Connection

The `ra-mcp-collaborative-research` skill file adapts the **digital reference interview** model demonstrated by Tom Scheinfeldt (University of Connecticut) in his ArchivesSpace MCP demo ("Sourcery for ArchivesSpace", shared 18 February 2026 at https://talented-beauty-production.up.railway.app/).

### What Scheinfeldt's demo does

Scheinfeldt's application implements a conversational AI reference archivist for ArchivesSpace collections. Its key principles:

- **Iterative search refinement** — when initial search terms fail, the AI suggests alternative terms and approaches (e.g., when "merchants" returns nothing, it suggests "business", "trade", "commerce")
- **Transparent scope explanation** — the AI explains what the collection contains and what it doesn't ("The Allen Doe Research Center focuses primarily on folk art and cultural materials, so railway collections might not be our specialty area")
- **Graceful escalation** — a "Connect with Archivist" button allows escalation to a human when the AI reaches its limits
- **Conversational guidance** — the researcher is guided through unfamiliar collections by an AI that knows the archive's structure

### How the skill file adapts these principles

Colin, working with Claude Cowork, took Scheinfeldt's conversational reference interview model and formalised it into an academically structured five-phase research methodology, tailored to the Riksarkivet archive and the ra-mcp server's specific capabilities:

| Scheinfeldt's reference interview | Skill file's five-phase workflow |
|-----------------------------------|----------------------------------|
| Opening orientation: "What are you looking for? Let me explain what we have" | **Phase 1 (Scoping):** Map archives, identify digitised holdings, locate published finding aids |
| Iterative term suggestion: "Try 'trade' instead of 'merchants'" | **Phase 2 (Term Mapping):** Build controlled vocabulary in Swedish with wildcards, fuzzy search, and historical spelling variants |
| Drilling into results: browsing specific items | **Phase 3 (Deep Reading):** Browse full page transcriptions, record reference codes, note bildvisaren links for verification |
| Transparent about limitations | Embedded throughout: always note AI-generated transcription status, flag coverage gaps, disclose archival biases |

### What the skill file adds beyond Scheinfeldt

The skill file extends the reference interview model with capabilities that go beyond what a reference archivist would typically provide:

1. **Structured confidence grading** — a three-tier scale (strong/moderate/weak) with explicit source-type tagging (ra-mcp transcription, ra-mcp metadata, web search, published finding aid, training knowledge)
2. **Systematic documentation of null results** — what was searched and not found is recorded as evidence, not discarded
3. **Triangulation against secondary literature** (Phase 4) — cross-referencing archival findings with published scholarship, finding aids, and web sources, using explicit quality heuristics
4. **Survivorship bias awareness** — interpreting search patterns in light of what the archive *should* contain (from finding aids) versus what is digitised and searchable
5. **Growing reference library** — each research session produces reusable reference files (controlled vocabularies, domain guides, terminology lists) that accumulate over time

### Chronology

- **17 Feb 2026:** Colin created the collaborative research skill file, adapting the reference interview model
- **18 Feb 2026 (12:38):** Tom Scheinfeldt shared the ArchivesSpace MCP demo URL
- **18 Feb 2026 (12:46):** Colin shared the skill file and three reference files back to Scheinfeldt
- **20 Feb 2026:** Scheinfeldt responded: "I've been planning to play around more with Claude skills. This will be a big help"
