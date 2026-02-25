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

# RA-MCP Collaborative Research Skill

**Version:** 1.1
**Date:** 24 February 2026

**Changes from v1.0 (17 February 2026):**
- Added proximity search and boosting (with silent failure caveat) to Phase 2 actions (items 6–7)
- Added in-text version header per CLAUDE.md conventions

## Purpose

This skill guides structured academic research using the Riksarkivet MCP server (ra-mcp) within Claude Cowork. It encodes a five-phase workflow for combining archival primary evidence with web-based secondary sources, producing findings with explicit confidence grading and academic citation.

## Prerequisites

Before beginning a research session, read the following reference files if they exist in `references/`:

1. `references/workflow-principles.md` — the five-phase research workflow, source-quality heuristics, and ra-mcp tool behaviour
2. `references/swedish-early-modern-legal-terminology.md` — controlled vocabulary of Swedish legal and judicial terms with English equivalents, historical context, and academic source attribution (drawn from Korpiola's overview of court records and petitions, c. 1400–1809)
3. `references/swedish-authority-guide.md` — thematic index of Swedish administrative domains with search terms for `search_transcribed` and `search_metadata`, organised by topic (justice, taxation, church, regional government, etc.)
4. Any additional domain-specific reference files relevant to the research topic (e.g., `references/svea-hovratt-guide.md`, `references/hca-comparison.md`)

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
6. Use proximity search (`"term1 term2"~N`) to find terms appearing within N words of each other
7. Use boosting (`term^4`) to weight important terms higher in results — always wrap boosted multi-term queries in explicit Boolean grouping (e.g., `(trolldom^4 OR häxeri)` not `trolldom^4 häxeri`; the bare syntax silently returns zero results)
8. **Record every search term and its result count**, including nulls — null results constrain interpretation

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
4. Evaluate web sources using the quality heuristics in `references/workflow-principles.md`

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

After each research session, consider whether any findings should be saved as a new reference file in `references/`. Good candidates include summaries of published finding aids, controlled vocabularies for specific archival domains, comparative frameworks, lessons about ra-mcp tool behaviour, and domain-specific search strategies. Reference files should be named descriptively in kebab-case (e.g., `svea-hovratt-guide.md`) and include a version header.

## Constraints

1. **Never present ra-mcp transcriptions as definitive text.** They are AI-generated readings of historical manuscripts. Always note this evidential status.
2. **Always search incrementally.** Keep max_results low, search one term cluster at a time, avoid fonds-level browse_document calls.
3. **Always record null results.** They are evidence, not failures.
4. **Always distinguish source types.** Never blend ra-mcp evidence with training knowledge without flagging the distinction.
5. **Always check for published finding aids** before interpreting ra-mcp search patterns. Archival gaps explain search patterns that the tool alone cannot.
