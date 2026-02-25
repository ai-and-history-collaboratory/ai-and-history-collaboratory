MCP Server Architectures for Archives, Historical Databases, and Libraries
==========================================================================

**Three Structural Models with Use Cases and Development Landscape**

Version 1.5 \| 17 February 2026

Prepared for: Colin Greenstreet

Context: Opening the Ottoman Archive Initiative \| AI + History Collaboratory

> *A note for Collaboratory participants: This document introduces a typology for thinking about MCP servers in the context of accessing historical databases --- archives, libraries, and digital humanities projects. It has been prepared with the Ottoman Archive initiative in mind, but the three architectural models apply to any research domain. As you read, consider your own sources and workflows: where could an MCP server change how you interact with the collections that matter to your research?*

1. Introduction: Why Architecture Matters
-----------------------------------------

When a historian connects an AI assistant to an archive or library, the connection passes through a bridge: a Model Context Protocol (MCP) server. MCP is a standard developed by Anthropic (released November 2024, open-sourced) that defines how AI models request and receive information from external tools and data sources. Think of it as a universal plug that lets Claude (or another AI) speak to any data source that implements the protocol.

The question this document explores is: how should those bridges be designed? The answer is not merely technical. The architecture of an MCP server shapes what a historian can ask, how flexibly they can work across sources, and who controls the infrastructure. Three distinct structural models have emerged in early MCP development, each with different strengths, different communities of developers, and different implications for historical research.

> ***🤔 Socratic Question:** Before reading further, consider your own research workflow. When you search for primary sources, do you think first about where to look (a specific archive), what to do (search, compare, annotate), or what format or protocol the source uses (IIIF images, metadata records, full text)? Your instinct here may reveal which architectural model would feel most natural to you.*

2. The Three Architectural Models {#the-three-architectural-models-1}
---------------------------------

The three models differ in their organising principle. Each answers the question "what does one MCP server correspond to?" differently.

                             **Source-Oriented**                                     **Task-Oriented**                                            **Protocol-Oriented**
  -------------------------- ------------------------------------------------------- ------------------------------------------------------------ ----------------------------------------------------
  **Organising principle**   One server per archive, library, or database            One server per research function across sources              One server per data standard or protocol
  **Analogy**                A dedicated assistant for each library you visit        A research assistant who can search many libraries for you   A translator who speaks every library's language
  **Mirrors how...**         Historians already think ("I need to check Gallica")    Digital humanities platforms work (federated search)         Interoperability standards work (IIIF, OAI-PMH)
  **Strengths**              Deep integration; can exploit full API of each source   Researcher-centric; reduces cognitive load                   Scales to any institution using the standard
  **Weaknesses**             Must install/configure a separate server per source     Shallow coverage of any single source                        Only works for sources that implement the standard

3. Category A: Source-Oriented MCP Servers
------------------------------------------

A source-oriented MCP server is built to connect to one specific archive, library, or database. It wraps that institution's particular API in the MCP protocol, giving Claude deep access to a single collection. This is by far the most common model in current MCP development.

### 3.1 Actual MCP Servers in This Category

-   **Gallica / BnF MCP Server.** Built by an individual developer ("Kryzo"), open source under MIT licence. Available in both Python and TypeScript/Node.js versions. Provides search by title, author, subject, date, and document type across the Bibliothèque nationale de France's digital collections. Also provides IIIF image access, OCR text retrieval, and item metadata. Uses the BnF's SRU (Search/Retrieve via URL) endpoint.

-   **Open Library MCP Server.** Built by an individual developer (8enSmith), open source. Connects to the Internet Archive's Open Library API. Provides book search by title, author search, detailed author information, and book cover image URLs. Returns structured data including ISBNs, OCLC numbers, and links to Internet Archive digital copies.

-   **European Cultural Heritage MCP Server.** Aggregates data from Europeana's API and individual museum APIs (Rijksmuseum, MoMA). Provides search, detail viewing, institution browsing, and AI-powered recommendations. Built in Python, open source.

-   **Archive.org Advanced Search MCP Server.** Available via Apify, enabling advanced search of the Internet Archive's collections. Bridges the Wayback Machine and digital library into the MCP ecosystem.

-   **Riksarkivet MCP Server (Swedish National Archives).** Built by AIRA (AI at Riksarkivet), the in-house AI lab of the Swedish National Archives. This is the most advanced archival MCP implementation found. The server exposes three MCP tools --- search\_transcribed (full-text search across millions of AI-transcribed pages), search\_metadata (archival metadata search), and browse\_document (page-level retrieval with transcriptions and IIIF images). Built in Python 3.12+ using FastMCP, it integrates with IIIF, ALTO XML, and OAI-PMH standards. Open source under Apache 2.0 licence. A hosted endpoint is available at riksarkivet-ra-mcp.hf.space/mcp, requiring no authentication, API key, or IP registration. Colin Greenstreet has installed and tested this server in Claude Desktop (both remote and local paths); a use skill and a debugging skill are available, with associated reference files, in Anthropic-compliant Skill.md format.

-   **MarineLives MCP Server (custom).** A custom Python MCP server built by Colin Greenstreet wrapping the MarineLives Semantic MediaWiki (www.marinelives.org) via the Action API and SMW Ask API. Provides semantic queries against approximately 700 C17th biographical records (mariners, merchants, and others drawn from High Court of Admiralty depositions), including structured properties for occupation, residence, literacy, and deposition metadata. The server is a Proof of Concept demonstrating how MCP can interface with legacy MediaWiki installations (MW 1.25alpha, 2015 vintage) where the REST API is unavailable. Currently the wiki is very slow to respond; Colin has contacted the developer Rowan Beentje to explore whether there are quick fixes to wiki response time without a major server update. Colin has installed and tested this server in Claude Desktop; a use skill is in preparation, with associated reference files, in Anthropic-compliant Skill.md format. Planned open source under MIT licence.

### 3.2 Use Cases for Historical Research

**Use Case A1: Ottoman Newspaper Research via Gallica**

A historian studying late Ottoman press culture in French-language newspapers published in Istanbul could use the Gallica MCP server to search for periodicals by date range (1880--1914), retrieve OCR text of specific issues, and pull IIIF images of original pages. Claude could then cross-reference names and places mentioned across issues, producing a structured index that would take weeks to compile manually.

**Use Case A2: Biographical Research via Open Library**

A researcher building prosopographical data on Ottoman reformers could use the Open Library MCP server to locate published biographies and memoirs, retrieve bibliographic metadata (publication dates, editions, publishers), and identify which texts are available as full digital copies via the Internet Archive. Claude could compile a comprehensive bibliography with availability information in a single session.

**Use Case A3: Cross-Museum Material Culture via European Cultural Heritage**

An art historian researching Ottoman ceramics held in European collections could search across the Rijksmuseum, V&A, and other Europeana-connected institutions from a single interface, comparing catalogue descriptions, provenance records, and available imagery.

### 3.3 Who Is Driving Development?

Source-oriented servers are overwhelmingly built by individual developers, typically working alone and releasing under MIT or similar open-source licences. The Gallica server was created by one person; the Open Library server by another. Neither the BnF nor the Internet Archive has built or endorsed an official MCP server. This pattern --- individual developers wrapping existing public APIs --- is the dominant mode across the entire MCP ecosystem as of early 2026. The institutions themselves are, with very few exceptions, not yet building MCP servers (though see Section 6 for notable exceptions emerging in the university library sector).

> ***🤔 Socratic Question:** If the institutions that own the data are not building MCP servers, but individual developers are, what does that imply about quality assurance, maintenance, and long-term sustainability? What happens when a public API changes and the solo developer has moved on?*

4. Category B: Task-Oriented MCP Servers
----------------------------------------

A task-oriented MCP server is organised around a research function rather than a specific source. Instead of connecting to one archive, it performs a type of work --- such as searching for academic papers, harvesting metadata, or generating bibliographies --- across multiple sources simultaneously.

### 4.1 Actual MCP Servers in This Category

-   **Paper Search MCP Server.** Built by an individual developer (openags), open source under MIT licence, Python. Searches and downloads academic papers from arXiv, PubMed, bioRxiv, medRxiv, Google Scholar, and IACR simultaneously. Returns results in a standardised format regardless of source. This is the clearest example of a task-oriented architecture: one tool, one function (paper search), many backends.

-   **Multi-Source Academic Search (afrise).** Aggregates nine or more scholarly databases including Semantic Scholar, OpenAlex, Crossref, and Google Scholar. Provides unified search, metadata retrieval, PDF download, and full-text extraction. Handles the differences between each source's API internally.

-   **Trove (Australian Archives).** Trove is an aggregation service run by the National Library of Australia (NLA) that federates searches across hundreds of partner institutions' collections via a single API. Although a Trove MCP server was referenced in some MCP registries (attributed to littlebearapps), no public source repository has been identified and the entry has been removed from this document's appendix. The Trove API (v3) remains technically available and API key registration is open, but the NLA's February 2025 actions cast doubt on its reliability for research use: the NLA revoked prominent developer Tim Sherratt's API keys without warning, retrospectively reinterpreted the terms of use to treat full-text access as a breach (even though the API was designed and documented to deliver full text), and imposed a four-level review matrix for new API key applications. Sherratt subsequently archived all his Trove-related code repositories, ceased active development on the Trove sections of the GLAM Workbench (https://glam-workbench.net/), and stated he could "no longer recommend Trove as a reliable source for digital research." The GLAM Workbench itself remains online and its non-Trove tools are unaffected; it is Sherratt's engagement with Trove that has ended. The NLA also disabled unauthenticated API access (previously available under v3 for experimentation and teaching) without notice. See Section 7 for a comparative analysis of institutional API access policies.

### 4.2 Use Cases for Historical Research

**Use Case B1: Historiographic Survey Across Databases**

A researcher preparing a literature review on Ottoman military reforms could use the Paper Search MCP server to simultaneously query arXiv (for computational history papers), Google Scholar (for traditional historiography), and PubMed (for papers on military medicine in the Ottoman context). Claude could synthesise the results into a structured literature review, identifying clusters of scholarship, key authors, and gaps in the literature.

**Use Case B2: Cross-Institutional Newspaper Harvest via Trove**

An Australian historian researching coverage of the Ottoman Empire in Australian newspapers during the Gallipoli campaign could, in principle, use the Trove MCP server to harvest articles across hundreds of digitised newspapers from multiple state libraries simultaneously. The server handles the complexity of searching across the National Library's aggregated collections, returning structured results that Claude could analyse for patterns in language, geographic coverage, and editorial framing. However, this use case is currently uncertain: the NLA's February 2025 revocation of Tim Sherratt's API keys and tightening of terms of use (see Section 4.1) means that researchers cannot rely on sustained, uninterrupted API access for projects of this kind.

**Use Case B3: Citation Network Analysis**

A digital humanities researcher could use the multi-source academic search server to trace how a foundational work (such as Bernard Lewis's *The Emergence of Modern Turkey*) has been cited across different disciplinary databases, comparing reception in area studies, political science, and comparative history journals.

### 4.3 Who Is Driving Development?

Task-oriented servers are also predominantly built by individual developers and small teams, but there is a subtle difference: the aggregation logic required is more complex, and these servers tend to emerge from developers with experience in data engineering or search systems. The Trove example is notable because the underlying API is institutionally maintained by the National Library of Australia, though the MCP wrapper itself is community-built. However, the NLA's February 2025 revocation of Tim Sherratt's API keys --- without warning or prior consultation --- and subsequent tightening of terms of use demonstrates that institutional API maintenance does not guarantee stable access for third-party developers. No major library consortium or archival organisation has yet built a task-oriented MCP server as an official product.

> ***🤔 Socratic Question:** The Paper Search server treats arXiv and Google Scholar as interchangeable sources of "academic papers." But a historian knows that the provenance and selection criteria of different databases matter enormously. What is gained and what is lost when a task-oriented server abstracts away the differences between sources?*

5. Category C: Protocol-Oriented MCP Servers
--------------------------------------------

A protocol-oriented MCP server is built around a data standard or query language rather than a specific source or task. It can connect to any institution or database that implements that standard. This is the most architecturally elegant model, but also the least developed in the current MCP ecosystem.

### 5.1 Actual MCP Servers in This Category

-   **Wikidata SPARQL MCP Servers.** Multiple implementations exist (by zzaebok, QuentinCody, ebaenamar, and others), all providing access to Wikidata's knowledge graph via the SPARQL query language. These allow Claude to execute structured queries against Wikidata's 100+ million items. Crucially, while these are currently pointed at Wikidata, the SPARQL protocol is universal --- the same server could, in principle, query any SPARQL endpoint.

-   **Generic SPARQL MCP Server (ekzhu).** A more explicitly protocol-oriented design: this server takes any SPARQL endpoint URL as a configuration parameter. You can point it at Wikidata, at a library's linked data endpoint, at a museum's RDF store, or at any other SPARQL-compatible service. The server itself is endpoint-agnostic.

-   **IIIF MCP Servers.** Two standalone IIIF MCP servers have been identified, both built by individual developers. The first, by Kohei Otsuka (Code for History), offers broad IIIF specification coverage --- Image, Presentation, Search, Annotation, Change Discovery, and Authorization APIs in both v2 and v3 --- but has near-zero community adoption (1 star, no forks, built in a two-day sprint in July 2025). The second, by Michael Appleby of the Yale Center for British Art, is deliberately narrower (manifest retrieval and image fetching only) but carries stronger IIIF community pedigree and ships as a Claude Desktop Extension for one-click installation. Neither has significant uptake. What is missing is not any IIIF MCP server, but an institutionally supported, widely adopted one --- a gap that matters given IIIF's backing by a 70-member global consortium including the Library of Congress, the British Library, the BnF, the Smithsonian, and hundreds of universities and museums.

-   **IIIF-Aware Functionality in the Gallica Server.** The Node.js version of the Gallica MCP server includes IIIF image retrieval tools alongside its source-specific search tools. While the server itself is source-oriented (Gallica only), the IIIF tools within it demonstrate the protocol-oriented principle: they use standardised IIIF Image API calls that would work against any IIIF-compliant server.

### 5.2 The Missing Servers: Institutional IIIF and OAI-PMH

The existence of two solo-developer IIIF MCP servers does not close the gap. Neither is maintained by the IIIF Consortium or any member institution; neither has attracted a user community; and the more comprehensive of the two (Code for History) has seen no commits since July 2025. For the IIIF MCP bridge to fulfil its potential --- enabling historians to retrieve, compare, and annotate images from any IIIF-compliant institution through a single protocol --- it would need institutional backing, active maintenance, and community adoption that these early efforts have not achieved.

Similarly, no OAI-PMH MCP server has been identified. Over 7,100 repositories were registered as OAI-PMH data providers before the Open Archives Initiative discontinued its registration service in July 2025. OAI-PMH remains the standard protocol for metadata harvesting across thousands of institutional repositories worldwide; the absence of an MCP bridge represents a clear opportunity.

### 5.3 Use Cases for Historical Research

**Use Case C1: Prosopography via Wikidata SPARQL**

A historian researching Ottoman provincial governors could use a Wikidata SPARQL MCP server to query for all individuals with the "position held" property matching Ottoman administrative titles, retrieve their birth/death dates, places of origin, and other positions held, and build a prosopographical database in minutes. Claude could construct the SPARQL queries automatically from natural language requests.

**Use Case C2: Cross-Institutional Manuscript Comparison via IIIF**

A palaeographer could use either existing IIIF MCP server to retrieve high-resolution images of a specific manuscript folio from the British Library, a related manuscript from the Bodleian, and a third from the BnF, then display them side by side for script comparison. The IIIF protocol makes this technically possible today; the practical barrier is not the absence of an MCP bridge but its immaturity and lack of institutional endorsement.

**Use Case C3: Linked Data Enrichment via Generic SPARQL**

A digital humanities project could use the generic SPARQL server pointed at multiple endpoints successively: first querying Wikidata for biographical data on Ottoman intellectuals, then querying the Virtual International Authority File (VIAF) for cross-references, then querying a library's linked data endpoint for catalogue records. The same MCP server handles all three queries because all three speak SPARQL.

### 5.4 Who Is Driving Development?

Protocol-oriented servers are built by individual developers (like all current MCP servers), but they tend to come from the semantic web and linked data community rather than the cultural heritage sector. The IIIF Consortium and the OAI community are well-established institutional players in the standards world, but neither has engaged with MCP as of early 2026. This creates an interesting opening: the standards infrastructure exists and is mature, but the MCP bridge has not been built at institutional quality.

> ***🤔 Socratic Question:** The generic SPARQL server can connect to any SPARQL endpoint. But SPARQL queries require knowledge of each endpoint's schema --- what properties exist, how entities are classified, what vocabulary is used. Does this mean that protocol-oriented servers shift the complexity from the developer (who builds the server) to the user (who must understand the data model)? And if so, is Claude well-positioned to absorb that complexity on the historian's behalf?*

6. Who Is Building MCP Servers? A Development Landscape
-------------------------------------------------------

The following table summarises who is driving MCP development for cultural heritage and research applications, based on the evidence gathered in February 2026.

  **Actor Type**                       **Role in MCP Development**                                                                                                             **Examples**                                                                                                **Open Source?**             **Sustainability**
  ------------------------------------ --------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------- ---------------------------- ---------------------------------------------------------------------------
  **Individual developers**            Building nearly all existing MCP servers for archives and libraries                                                                     Kryzo (Gallica), 8enSmith (Open Library), zzaebok (Wikidata), Kohei Otsuka (IIIF), Michael Appleby (IIIF)   Almost always (MIT)          Low: depends on one person's continued interest
  **Small teams / startups**           Building MCP infrastructure and registries                                                                                              LobeHub, PulseMCP, Glama (MCP directories), Smithery (installer)                                            Mixed                        Moderate: venture-funded but MCP is early
  **University libraries**             Earliest institutional MCP adopters; building servers for their own catalogues and collections                                          Northeastern University Library (Dan Cohen), UConn/Sourcery (Tom Scheinfeldt)                               Not yet (code unpublished)   Moderate: institutionally supported but dependent on individual champions
  **Cultural heritage institutions**   Providing the APIs that MCP servers wrap, but generally NOT building MCP servers themselves (Riksarkivet/AIRA is a notable exception)   BnF (Gallica API), NLA (Trove API), Europeana, IIIF Consortium                                              APIs are typically open      High for APIs; near-zero for MCP (Riksarkivet/AIRA the key exception)
  **Anthropic**                        Created the MCP protocol itself; maintains specification and SDKs                                                                       MCP specification, Python and TypeScript SDKs                                                               Yes (open spec)              High: core to Anthropic's strategy
  **Academic / DH community**          Using APIs extensively but not yet building MCP servers (with the university library exceptions noted above)                            GLAM Workbench (Tim Sherratt), Computational Archival Science programs                                      Yes                          Moderate: grant-funded, community-sustained

The most striking finding remains the near-total absence of institutional involvement in MCP server development. The institutions that control the richest data --- national libraries, state archives, major museums --- provide APIs but have not yet engaged with MCP. The earliest exceptions are in the university library sector, where Dan Cohen at Northeastern and Tom Scheinfeldt at UConn have built MCP servers connecting to library catalogues and archival management systems respectively.

Cohen's server wraps Northeastern's library catalogue using vector search and a concept he calls "Library-Augmented Generation"; Scheinfeldt's wraps ArchivesSpace, an open-source archives management system used by thousands of institutions. ArchivesSpace natively supports OAI-PMH (Open Archives Initiative Protocol for Metadata Harvesting), the standard protocol through which institutional repositories expose their metadata for automated harvesting. This means Scheinfeldt's MCP server indirectly bridges OAI-PMH-compliant data into the MCP ecosystem --- a significant connection given that no standalone OAI-PMH MCP server has been identified (see Section 5.2). Scheinfeldt's server also embeds professional archival reference interview practices in its prompt templates.

Neither server's code has been published, but both demonstrate that institutional actors can build MCP infrastructure that reflects domain expertise rather than merely wrapping APIs. The broader landscape, however, remains one where access to cultural heritage via AI is mediated overwhelmingly by volunteer developers, with no institutional quality assurance, maintenance commitments, or strategic coordination.

> ***🤔 Socratic Question:** Tim Sherratt's GLAM Workbench project in Australia built sophisticated tools for harvesting and analysing Trove data, but his API keys were cancelled by the National Library of Australia in early 2025 without warning --- leading Sherratt to archive his Trove-related repositories and step back from the project entirely. If institutional APIs can be revoked unilaterally, what does that mean for the sustainability of any MCP server that depends on them? And does this risk change depending on which architectural model you use?*

7. The Policy Environment: Metadata Access, Full-Text Access, and Institutional Control
---------------------------------------------------------------------------------------

The viability of MCP servers for archives depends not only on technical architecture but on institutional willingness to provide stable, programmatic access to collections. A striking divergence has emerged between national archives and libraries in their policies toward API access for metadata and full-text content. This section contrasts three institutions --- the National Library of Australia (NLA), the U.S. National Archives and Records Administration (NARA), and the Swedish National Archives (Riksarkivet) --- whose policies span the spectrum from restrictive to fully open.

### 7.1 National Library of Australia (Trove API): Restrictive and Unpredictable

The Trove API (v3) provides access to metadata and full-text content from over 271 million Australian cultural records aggregated from hundreds of partner institutions. However, the NLA's approach to API governance has become increasingly restrictive. In February 2025, the NLA revoked Tim Sherratt's API keys without warning, retrospectively reinterpreting its terms of use to treat full-text access via the API as a breach --- even though the API was explicitly designed and documented to deliver full text, and Sherratt had used it in this way for fifteen years. The NLA subsequently imposed a four-level application review matrix for new API keys, with "Level 3" review required for anyone downloading or harvesting full-text records, and "Level 4" review (with reputational risk assessment) for any use involving AI training. Unauthenticated API access, previously available under v3 for experimentation and teaching, was disabled without notice. The Australian Historical Association issued a public statement describing the restrictions as "a troubling restriction to the work of researchers in Australia and overseas."

**Implications for MCP server builders:** Any MCP server wrapping the Trove API is exposed to unilateral policy changes. A developer could build and distribute a server in good faith, only to have its users' API keys revoked without warning. The NLA's unwillingness to consult before changing terms makes the Trove API an unreliable foundation for sustained MCP integration. No publicly verifiable Trove MCP server has been identified (see Section 4.1).

### 7.2 U.S. National Archives and Records Administration (NARA Catalog API): Open by Default

NARA's Catalog API occupies the opposite end of the spectrum. As works of the U.S. federal government, NARA's archival metadata and most digital images are in the public domain. The API (v2, released September 2022) requires a free API key for all requests but the key is issued to anyone who emails a request --- no application form, no review matrix, no justification required. The API explicitly supports bulk export of metadata in JSON, XML, CSV, and PDF formats, and NARA additionally makes the entire catalogue dataset available for bulk download via the Amazon Web Services Registry of Open Data. The default rate limit is 10,000 queries per month, with higher limits available on request. The API source code itself is released under CC0 (public domain dedication). NARA has not imposed any distinction between metadata access and content access in its terms; researchers can retrieve metadata, OCR text, and digital objects through the same API without seeking special permission.

**Implications for MCP server builders:** NARA's open policies make it an ideal candidate for MCP server development. A server can be built, distributed, and used with confidence that the underlying API access will not be unilaterally restricted. The IP registration requirement noted in the companion TNA API and MCP Research memo (which applies to the UK's Discovery API) does not apply here --- NARA's API key is portable and personal.

### 7.3 Swedish National Archives (Riksarkivet): Open Access, No Authentication

Riksarkivet goes further than NARA. Its public APIs require no API key, no authentication, no IP registration, and no application of any kind. The data exposed through the APIs --- catalogue metadata, AI-transcribed full text, IIIF images, and ALTO XML --- covers material older than 110 years and is freely reusable. In 2017, the Swedish Parliament allocated 10 million SEK specifically to make Riksarkivet's digital collections freely available; the subscription charge was removed in February 2018. Riksarkivet has gone further than simply providing APIs: through its AIRA lab, it has built and published its own MCP server (ra-mcp), open source under Apache 2.0, with a hosted endpoint on Hugging Face that anyone can connect to without credentials. This makes Riksarkivet, to date, the only national archive in the world that has both built an MCP server and made it freely available.

**Implications for MCP server builders:** Riksarkivet's model eliminates every friction point that constrains MCP development elsewhere. There is no API key to manage or distribute, no terms of use that could be retrospectively reinterpreted, and no risk of access revocation. The institutional MCP server itself can serve as a reference implementation for other archives considering the same approach.

### 7.4 The Broader Context

The NLA's restrictive turn does not occur in a vacuum. As David Braue noted in Information Age, cultural heritage institutions face a genuine tension: their mission is to curate and make publicly available works of cultural significance, but the rise of generative AI has created new anxieties about large-scale data harvesting for commercial model training. The OECD's February 2025 report on "Intellectual Property Issues in Artificial Intelligence Trained on Scraped Data" acknowledged the "complex issues" and "significant challenges" that data scraping practices create for intellectual property. National archives occupy a particularly challenging middle ground: most of their holdings are in the public domain (by age, by law, or both), yet the institutions feel pressure to control how that public-domain content is used.

The three policies compared here illustrate divergent responses to this tension. Riksarkivet and NARA have concluded that open access to public-domain material is consistent with their institutional mission and have not restricted it in response to generative AI. The NLA, by contrast, has chosen to restrict access pre-emptively, imposing gatekeeping mechanisms that affect non-commercial researchers and commercial AI developers alike. For MCP server builders, the practical consequence is clear: an MCP server is only as stable as the API policy it depends on. Institutional policy, not technical architecture, is the binding constraint.

Dan Cohen, writing in his Humane Ingenuity newsletter in August 2025, offered a framework that reframes this debate. Cohen argues for "loose coupling" between AI and cultural heritage institutions --- but "loose" here is an architectural term, not a synonym for permissive. The contrast is with tight coupling: the wholesale ingestion of institutional collections into centralised model training, where the institution cedes control entirely. Under loose coupling, an archive instead provides structured access to its collections via open protocols such as MCP, retaining the ability to "shape them for external use in whatever formats they wish, within the limits set by the organization or by stakeholders such as artists, authors, or communities." An MCP server, in Cohen's framing, allows an institution to configure precisely what can be accessed and how --- for example, limiting AI's access to metadata rather than entire objects, so that students find non-hallucinated citations and links to primary sources but are then encouraged to read or view the full text themselves. Crucially, the degree of openness is a dial, not a switch: institutions can set it wherever their mission, legal framework, and risk appetite dictate. Cohen notes that cultural heritage institutions have already done much of the groundwork through existing web infrastructure and protocols like IIIF, and that MCP extends this logic rather than disrupting it. Viewed through this lens, all three institutions discussed above could operate within a loosely-coupled architecture. Riksarkivet and NARA have chosen to set the dial wide open --- no authentication, no usage restrictions, permissive licences --- making them natural early adopters. The NLA has chosen a much tighter setting, requiring authentication, imposing a review matrix, and reserving the right to revoke access. That is not a rejection of loose coupling; it is an exercise of exactly the institutional control that Cohen's model places in the institution's hands. What is open to question is not the NLA's right to set the dial, but the manner in which it did so --- with minimal consultation, poor communication, and consequences that fell disproportionately on the non-commercial researchers and digital humanists who had done most to extend Trove's public value.

8. Long Term Implications for the Ottoman Archive Initiative
------------------------------------------------------------

The "Opening the Ottoman Archive" initiative is positioned at an interesting intersection of all three architectural models. Consider the following questions for your project and your Collaboratory:

1.  **Source-oriented servers for Ottoman-specific collections.** The Gallica MCP server already provides access to the BnF's Ottoman-language holdings. Does an equivalent exist for the Başbakanlık Osmanlı Arşivi (BOA) in Istanbul? If not, could one be built around the BOA's digital catalogue? What about the collections at SALT Research, the Atatürk Library, or the Topkapı Palace archives?

2.  **Task-oriented servers for HTR workflows.** Your skill files define specific transcription and analysis tasks. Could these be formalised as MCP tools --- a "transcribe Ottoman manuscript" server that handles image retrieval, HTR processing, and output formatting as a single workflow, regardless of which archive the image comes from?

3.  **Protocol-oriented servers for cross-institutional comparison.** Many of the institutions holding Ottoman materials --- the BnF, the British Library, university libraries --- support IIIF. The existing IIIF MCP servers, though immature, already let you retrieve and compare manuscript images across these institutions. The Wikidata SPARQL server could provide structured prosopographical data to enrich your document analyses.

4.  **The suggested June hackathon.** The suggested June hackathon could include a challenge to build an MCP server for one of the gaps identified in this document --- particularly an institutionally robust IIIF MCP server, which would benefit the entire digital humanities community, not just Ottoman studies.

> ***🤔 Socratic Question:** Of the three architectural models, which would deliver the most immediate value to your collaborators' day-to-day research? And which would have the greatest long-term impact on the field? Are those the same answer?*

8. Summary: Three Models, One Emerging Ecosystem
------------------------------------------------

  **Dimension**           **Source-Oriented**                                                              **Task-Oriented**                                    **Protocol-Oriented**
  ----------------------- -------------------------------------------------------------------------------- ---------------------------------------------------- ------------------------------------------------------------------------
  **Maturity**            Most developed; dozens of examples                                               Emerging; a handful of examples                      Earliest stage; SPARQL and IIIF only
  **Developers**          Individual open-source contributors                                              Individual developers with data engineering skills   Semantic web / linked data community
  **Institutions**        Provide APIs but not MCP servers (with emerging university library exceptions)   NLA provides Trove API; no official MCP              IIIF Consortium not yet engaged; two solo-developer IIIF servers exist
  **Biggest gap**         No servers for most national archives                                            No multi-source historical document search           No institutionally supported IIIF or OAI-PMH MCP server
  **Ottoman relevance**   Gallica server already useful; BOA server needed                                 Could unify HTR workflows across archives            IIIF servers enable manuscript comparison today (limited)

The MCP ecosystem for cultural heritage is in its infancy. The protocol is barely sixteen months old, the developer community is building fast but without institutional coordination, and the most architecturally powerful models (protocol-oriented) are the least developed. This is a landscape where early movers --- particularly those who combine domain expertise with technical capacity --- can shape the infrastructure rather than merely use it.

> ***🤔 Socratic Question:** Your Collaboratory brings together historians and coders. The hackathon will mix technical and non-technical participants. Looking at the gaps in this landscape, where could your group make a contribution that would be both useful for Ottoman studies and valuable to the wider digital humanities community? And which of the three architectural models offers the best entry point for that contribution?*

Appendix: MCP Servers Referenced in This Document
-------------------------------------------------

  **Name**                          **Category**   **Developer**                             **GitHub / Source**                                                                                                                                  **Licence**     **Status (Feb 2026)**
  --------------------------------- -------------- ----------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------- --------------- --------------------------------------------
  Archive.org Advanced Search       A (Source)     Apify                                     Available via Apify                                                                                                                                  Proprietary     Active
  European Cultural Heritage        A (Source)     Community                                 Available via MCP registries                                                                                                                         Open source     Active
  Gallica / BnF                     A (Source)     Kryzo                                     [github.com/Kryzo/mcp-bibliotheque\_nationale\_de\_France](https://github.com/Kryzo/mcp-bibliotheque_nationale_de_France) \[STARS = 7; FORKS = 5\]   MIT             Active; Python + Node.js versions
  Generic SPARQL                    C (Protocol)   ekzhu                                     [github.com/ekzhu/mcp-server-sparql](https://github.com/ekzhu/mcp-server-sparql) \[STARS = 8; FORKS = 6\]                                            Open source     Active
  IIIF (Code for History)           C (Protocol)   Kohei Otsuka                              <http://github.com/code4history/IIIF_MCP> \[STARS = 1; FORKS = 0\]                                                                                   MIT             Dormant (last commit Jul 2025)
  IIIF (Yale/mikeapp)               C (Protocol)   Michael Appleby                           <http://github.com/mikeapp/mcp-iiif-images> \[STARS = 5; FORKS = 0\]                                                                                 Not stated      Active; Desktop Extension available
  MarineLives (custom)              A (Source)     Colin Greenstreet                         Planned: <http://github.com/Addaci/marinelives-mcp-server> \[NOT YET IMPLEMENTED\]                                                                   MIT (planned)   Proof of Concept; tested in Claude Desktop
  Multi-Source Academic Search      B (Task)       afrise                                    Available via MCP registries                                                                                                                         Open source     Active
  Northeastern University Library   A (Source)     Dan Cohen / Northeastern                  Not published                                                                                                                                        Closed          In use at Northeastern
  Open Library                      A (Source)     8enSmith                                  [github.com/8enSmith/mcp-open-library](https://github.com/8enSmith/mcp-open-library) \[STARS = 56; FORKS = 15\]                                      Open source     Active
  Paper Search                      B (Task)       openags                                   <http://github.com/openags/paper-search-mcp> \[STARS = 664; FORKS = 95\]                                                                             MIT             Active
  Riksarkivet (ra-mcp)              A (Source)     AIRA / Swedish National Archives          [github.com/AI-Riksarkivet/ra-mcp](https://github.com/AI-Riksarkivet/ra-mcp) \[STARS = 6; FORKS = 1\]                                                Apache 2.0      Active; tested in Claude Desktop
  Sourcery / ArchivesSpace          A (Source)     Tom Scheinfeldt / UConn                   Not published                                                                                                                                        Closed          Prototype
  Wikidata SPARQL (multiple)        C (Protocol)   zzaebok, QuentinCody, ebaenamar, others   Various GitHub repos                                                                                                                                 Open source     Active

Reading List: API Access Policy and Institutional Data Governance
-----------------------------------------------------------------

Australian Historical Association (2025, 24 March). "AHA Statement on New Restrictions to Trove." [theaha.org.au](https://theaha.org.au/wp-content/uploads/2025/03/AHA-Statement-on-New-Restrictions-to-Trove.pdf)

Braue, D. (2025, 10 March). "National Library cracks down on public data access." Information Age / ACS. [ia.acs.org.au](https://ia.acs.org.au/article/2025/national-library-cracks-down-on-public-data-access.html)

Cohen, D. (2025, August). "AI and Libraries, Archives, and Museums, Loosely Coupled." Humane Ingenuity. [newsletter.dancohen.org](https://newsletter.dancohen.org/archive/ai-and-libraries-archives-and-museums-loosely-coupled/)

National Library of Australia (2025). "Using the API" and "Trove API Terms of Use." [trove.nla.gov.au](https://trove.nla.gov.au/about/create-something/using-api)

OECD (2025, 9 February). "Intellectual Property Issues in Artificial Intelligence Trained on Scraped Data." OECD Artificial Intelligence Papers, No. 33. [doi.org/10.1787/d5241a23-en](https://doi.org/10.1787/d5241a23-en)

Riksarkivet (n.d.). "PSI och öppna data från statliga myndigheter" \[PSI and Open Data from Government Agencies\]. [riksarkivet.se/psi-oppna-data](https://riksarkivet.se/psi-oppna-data); see also Dataplattform wiki: [github.com/Riksarkivet/dataplattform/wiki](https://github.com/Riksarkivet/dataplattform/wiki)

Sherratt, T. (2025, 24 February). "15 years of work on Trove threatened by the NLA." [updates.timsherratt.org](https://updates.timsherratt.org/2025/02/24/years-of-work-on-trove.html)

Sherratt, T. (2025, 2 March). "Trove API users beware! --- the latest in the saga of my cancelled API keys." [updates.timsherratt.org](https://updates.timsherratt.org/2025/03/02/trove-api-users-beware-the.html)

Sherratt, T. (2025, 11 April). "Update on Trove data access and my suspended API keys." [updates.timsherratt.org](https://updates.timsherratt.org/2025/04/11/update-on-trove-data-access.html)

Sherratt, T. (2025, 7 May). "Farewell Trove." [updates.timsherratt.org](https://updates.timsherratt.org/2025/05/07/farewell-trove.html)

Sherratt, T. (n.d.). GLAM Workbench. [glam-workbench.net](https://glam-workbench.net/)

U.S. National Archives and Records Administration (n.d.). "API for the National Archives Catalog." [archives.gov](https://www.archives.gov/research/catalog/help/api)

Version History
---------------

  **Version**   **Date**           **Changes**
  ------------- ------------------ ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  1.0           14 February 2026   Initial creation. Three architectural models defined; actual MCP servers identified and documented; use cases developed; development landscape analysis; implications for Ottoman Archive project.
  1.1           14 February 2026   Corrected IIIF MCP server claim (two servers exist, by Otsuka and Appleby; reframed gap as institutional adoption rather than absence). Added Cohen (Northeastern) and Scheinfeldt (UConn/Sourcery) to development landscape. Added university libraries row to actor table. Clarified Trove classification rationale. Updated OAI-PMH data (registration discontinued July 2025). Sharpened Sherratt API key reference. Added Collaboratory reader introduction. Added appendix of all referenced MCP servers. Changed to UK date format.
  1.2           14 February 2026   Added pagination; added several page breaks; adjusted front headline formatting; adjusted appendix column widths; adjusted paragraph structure ins ection six
  1.5           17 February 2026   Corrected three broken GitHub URLs in appendix (Gallica, Open Library, Generic SPARQL --- all had incorrect repository names). Added GitHub stars and forks counts to all verified repositories. Added Riksarkivet ra-mcp and MarineLives MCP servers to Section 3.1 and appendix. Fixed "ROKS" typo to "FORKS" in IIIF entry. Substantially revised Section 4.1 Trove entry: removed unverifiable Trove MCP server (no public repository found); added GLAM Workbench context (still online, Trove engagement ended); added NLA four-level review matrix and unauthenticated access removal. Removed Trove from appendix. Added new Section 7 comparing API access policies of NLA, NARA, and Riksarkivet, with MCP implications. Added Reading List on API access policy and institutional data governance. Renumbered former Section 7 to Section 8. Added OAI-PMH explanation and ArchivesSpace/OAI-PMH connection in Section 6. Changed IIIF phrasing from "exist" to "have been identified". Updated hackathon reference to "suggested June hackathon". Updated Section 6 table to note Riksarkivet/AIRA as exception. Changed to A4 page size and darker heading colours.
