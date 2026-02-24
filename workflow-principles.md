# Workflow Principles for RA-MCP Collaborative Research

**Version:** 1.2
**Date:** 24 February 2026

**Change notes (v1.2):** Added boosting silent failure warning to Section 1 (`search_transcribed` description). Finding from structured testing on 24 February 2026.

This reference file documents the workflow principles, source-quality heuristics, and tool behaviour observations underlying the ra-mcp-collaborative-research skill. It was derived from an exploratory research session on Swedish maritime jurisdiction conducted on 17 February 2026 (documented in RA_MCP_Swedish_Maritime_Jurisdiction_Research_Memo_v1.1_17022026.md).

---

## 1. The RA-MCP Server: Three Tools

The Riksarkivet MCP server provides three tools:

**search_metadata** — searches archival metadata (titles, creator names, places, institutional descriptions) across the Nationell Arkivdatabas (NAD). Can include both digitised and non-digitised holdings (controlled by `only_digitised` parameter). Useful for scoping: identifying relevant fonds, series, creators, and institutional provenance.

**search_transcribed** — searches AI-transcribed (HTR/OCR) text within digitised documents. Supports advanced Solr query syntax: wildcards (`*`), fuzzy search (`~`), Boolean operators (`AND`, `OR`, `NOT`), proximity searches (`"term1 term2"~10`), and boosting (`term^4`). Returns page-level hits with text snippets. This is the primary discovery tool for content within documents.

**Boosting caveat (confirmed 24 February 2026):** Boosting works only with explicit Boolean grouping. The bare space-separated syntax `trolldom^4 häxeri` silently returns zero results — no error, no warning, just empty results. Always use explicit grouping: `(trolldom^4 OR häxeri)`. This is the most dangerous failure mode in the query syntax because it gives no indication the query was malformed.

**browse_document** — retrieves full page transcriptions by archival reference code. Provides links to original page images in Riksarkivet's bildvisaren (image viewer) and to ALTO XML transcriptions. Use for deep reading of specific pages identified by search.

---

## 2. Observed Tool Behaviour and Limitations

The following observations were made during the 17 February 2026 session and should inform future research:

**Result count ceiling:** Both search tools report "100+" when results exceed their reporting threshold. No exact count is available. This limits quantitative analysis — you cannot determine "how many references to X exist" beyond knowing "at least 100."

**Date filtering is volume-level:** The `year_min`/`year_max` parameters filter by the catalogued date range of the archival volume, not by the dates of individual documents or pages within it. A volume catalogued as "1600-1840" will match a search for 1610-1620 even if no individual document within it dates from that decade. This creates false precision in date-bounded searches.

**Transcription quality varies:** The transcriptions are AI-generated (HTR/OCR) readings of historical manuscripts. Expect: misread characters (especially in older hands), merged or split words, garbled passages, and inconsistent handling of abbreviations. Fuzzy search (`~`) is essential. Never cite transcription text as authoritative without verification against the original image.

**Institutional coverage is uneven:** Riksarkivet civilian holdings are the primary content. Krigsarkivet (War Archives) material appears partially (SE/KrA references were found), but coverage is less consistent. Regional archives (Riksarkivet i Vadstena, Uppsala, Lund, Göteborg) are included but may have variable transcription depth.

**Timeout risk on broad queries:** Browsing at the fonds level (e.g., `SE/RA/420422/01` rather than a specific volume) can timeout. Keep searches and browse requests targeted at specific series or volumes.

**Search-browse coverage gap:** `search_transcribed` indexes a larger corpus than `browse_document` can serve page-by-page. Volumes that return page-level hits in search may return "not digitised or transcribed" when browsed (e.g., SE/RA/420422/01/E VI a 2 aa/276 returned 120 search hits but could not be browsed). This means `search_transcribed` is the more reliable tool for accessing text content (it returns snippets inline), while `browse_document` works for a subset of documents only. Image viewer links (IIIF, Bildvisning) remain accessible regardless. Always use search as the primary access method and browse as a supplement. *(Finding from structured testing on 16 February 2026.)*

**Deduplication:** The tool remembers what it has shown within a session. Re-running the same query returns compact stubs for already-seen documents. Set `dedup=false` to force full results if needed.

---

## 3. Source Quality Heuristics for Web Research

When supplementing ra-mcp archival evidence with web-based sources, apply these heuristics:

### High-quality sources

- **Institutional archive/library websites** (riksarkivet.se, nationalarchives.gov.uk) — authoritative for holdings descriptions, finding aids, institutional history
- **Published finding aids and research guides** (e.g., Riksarkivet's "Hitta i..." PDF series) — professional archival products. Note their publication date; structural descriptions remain valid but digitisation references may be outdated
- **Peer-reviewed scholarship** via JSTOR, DiVA (diva-portal.org for Swedish dissertations), ResearchGate, university press catalogues — gold standard for interpretive claims
- **Government and judiciary websites** (judiciary.uk, government.se) — authoritative for current and recent institutional descriptions
- **Encyclopaedia entries** (Britannica, Wikipedia) — acceptable for uncontroversial factual claims (dates, institutional structures) but not for interpretive arguments

### Low-quality sources (treat with caution)

- **Travel and tourism sites** — may contain historical claims without scholarly sourcing
- **Genealogy sites** (FamilySearch, MyHeritage) — useful for understanding record types but often simplified or US-centric
- **AI-generated content farms** — identifiable by generic phrasing, lack of specific citations, absence of named authors
- **Unattributed blog posts** — may contain valuable specialist knowledge but cannot be cited without verification

### Quality indicators

- Does the source name its author(s) and their institutional affiliation?
- Does it cite primary sources or specific archival references?
- Is it hosted by a recognised institution (university, archive, government body, scholarly publisher)?
- Can its claims be cross-referenced against at least one other independent source?

---

## 4. The Survivorship Bias Problem

A critical lesson from the founding research session: **ra-mcp search results are shaped by archival survival and digitisation patterns, not by historical reality.** Without external knowledge of what the archive *should* contain (from finding aids, secondary literature, or archival descriptions), search results can be systematically misleading.

**Example:** Searches across the Svea hovrätt E VI a 2 aa series (case files) produced hits skewed toward the early 17th century and post-1804. This appeared to show that maritime cases clustered in these periods. In fact, the "Hitta i Svea hovrätts handlingar" finding aid (1998) reveals that case files for 1689-1704 and 1713-1804 survive only as remnants. The pattern in the search results reflected archival loss, not historical reality. Judgments from the same period survive in the A II domböcker — a different series with different search characteristics.

**Implication:** Always seek published finding aids before interpreting ra-mcp search patterns. The question is not just "what did I find?" but "what should I expect to find, and what is missing?"

---

## 5. The Controlled Vocabulary Approach

Historical Swedish texts use vocabulary, spelling, and terminology that differs from modern Swedish. Effective ra-mcp searching requires building a controlled vocabulary for each research domain. Strategies:

- **Start with modern Swedish terms**, then expand to historical variants
- **Use wildcards** to catch morphological variants: `skepp*` catches *skepp*, *skepparen*, *skeppund*, *skeppet*
- **Use fuzzy search** for OCR/HTR errors and orthographic variants: `Stockholm~1` catches common misreadings
- **Test both Swedish and non-Swedish terms** — historical documents may contain Latin, German, or other language terms (e.g., *liber causarum*, *codices rationum*)
- **Record your vocabulary systematically** — document which terms were searched, what they returned, and what variants remain untested. This vocabulary becomes a reusable reference file for future sessions.
- **Search by collection name, not just personal name** — prominent individuals may be catalogued under collection names rather than personal names. For example, Axel Oxenstierna's papers are catalogued under collection titles, not his name; searching `name="Oxenstierna"` returns limited results despite the archive holding extensive material. When researching well-known individuals, search for both personal names and known collection/fonds names. *(Finding from structured testing on 16 February 2026.)*

---

## 6. Documentation Standards

### Confidence grading (three-tier scale)

| Grade | Meaning | Example |
|-------|---------|---------|
| **Strong** | Direct attestation in primary sources or authoritative secondary sources | Named Sjörätt courts appear in transcribed hovrätt appeal records |
| **Moderate** | Inferred from clear but indirect evidence | Amiralitetskollegium records held at Krigsarkivet suggest military rather than civilian jurisdiction |
| **Weak** | Argument from silence or single unreliable source | No *prisrätt* references found — but relevant records may be undigitised or use different terminology |

### Citation format

**Ra-mcp archival sources:** Full reference code, institution, page number(s), date. Example: SE/VaLA/03825/01/A II/68, pp. 602-603 (Riksarkivet i Vadstena, 1784).

**Web sources:** Author/institution, title, URL. Example: Riksarkivet, Forskarserviceavdelningen. "Hitta i Svea hovrätts handlingar." Mars 1998.

**Null results:** "Search for [term] in [tool] with [parameters] returned zero results." These are evidence and should be recorded.

---

*This reference file should be updated as new research sessions reveal additional tool behaviours, workflow refinements, or source-quality observations.*
