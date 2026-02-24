# CLAUDE.md — Cowork Folder Instructions

**Version:** 5.3
**Date:** 17 February 2026
**Folder:** C:\Users\colin\ClaudeCoworkSandbox
**Owner:** Colin Greenstreet

---

## 1. Purpose

This is a **test sandbox folder** for experimenting with Claude Cowork. All files in this folder are copies — not originals. Treat this environment as an experimental workspace where safety and caution take priority over speed.

---

## 2. Safety Rules (MANDATORY)

- **NEVER delete any existing files** without explicit written confirmation from Colin in the conversation.
- **NEVER access, read, or modify files or folders outside this directory** (`C:\Users\colin\ClaudeCoworkSandbox` and its subfolders only).
- **NEVER access cloud-synced folders** (OneDrive, Google Drive, Dropbox) under any circumstances.
- **Ask for confirmation** before modifying any existing file. Describe the planned changes and wait for approval.
- **Creating new files is permitted** without prior approval, but always report what was created and why.
- **If in doubt, stop and ask.** Do not guess or assume intent.

---

## 3. File Naming and Versioning Conventions

### Filename conventions

All new files created in this folder must follow these conventions:

- Include a **version number** (e.g., v1.0, v2.3).
- Include the **date of creation** in the filename using format DDMMYYYY.
- Use **underscores** between words in filenames (e.g., `HTR_Analysis_Report_v1.0_11022026.md`).
- Prefer **.md** (Markdown) format unless another format is specifically requested.

**Exceptions:**

- Files in `.claude/rules/` are configuration files and use simple descriptive names without version numbers or dates in their filenames (e.g., `ottoman-htr-pipeline.md`, `ra-mcp.md`).
- Files in skill file `references/` directories use simple descriptive names in kebab-case without version numbers or dates (e.g., `workflow-principles.md`, `swedish-authority-guide.md`). Version tracking for these files is maintained via in-text headers.
- Skill files (`SKILL.md`) follow Anthropic's skill file format, which uses YAML frontmatter and a fixed filename. Version tracking is via in-text headers.

### In-text versioning for rules files, skill files, and reference files

Because rules files, skill files, and reference files use simple filenames, version tracking is maintained within the file text itself. Every such file must include a version header near the top of the file:

```
**Version:** 1.0
**Date:** 12 February 2026
```

Increment the version number when the file's content is substantively changed. Minor corrections (typos, formatting) do not require a version increment. Use whole numbers (1.0, 2.0) for structural changes and decimal increments (1.1, 1.2) for content additions within the existing structure.

CLAUDE.md follows the same in-text versioning convention in its own header.

### Archiving superseded versions

When a versioned file is substantively revised, the superseded version must be archived before overwriting:

- **CLAUDE.md** → archive to `Archive/` using the naming pattern `CLAUDE_vX.Y_DDMMYYYY.md`.
- **Rules files** (`.claude/rules/`) → no separate archive; version history is tracked in-text and old versions of CLAUDE.md record which rules file versions were current at each point.
- **Skill reference files** (`references/*.md` within a skill directory) → archive to `references/archive/` within the same skill directory, using the naming pattern `filename_vX.Y_DDMMYYYY.md`. Add a `**Status:** SUPERSEDED` line at the top of the archived copy explaining what changed.
- **Skill files** (`SKILL.md`) → archive to `references/archive/` within the same skill directory, using the naming pattern `SKILL_vX.Y_DDMMYYYY.md`.
- **Output memos and other dated files** → these already carry version numbers and dates in their filenames, so multiple versions coexist naturally. No archiving step is needed unless the user requests cleanup.

This archiving practice ensures that no substantive work is lost when files are revised.

---

## 4. Communication Style

- Respond **Socratically** — use questions to guide understanding rather than simply giving answers.
- Explain reasoning and decisions clearly, assuming the reader is intelligent but not a software developer.
- When summarising or analysing files, note anything that appears incomplete, inconsistent, or worth questioning.

---

## 5. Project Context

The files in this sandbox relate to two interconnected strands of the **"Opening the Ottoman Archive" initiative**, an academic research project:

**Ottoman HTR/OCR pipeline** — developing two-stage pipelines for Ottoman Turkish documents in multiple scripts, evaluating Visual Language Models for historical document transcription, building collaborative workflows with partners (Nabil Al-Tikriti, Gül Şen, Özgür Türesay, Dimitra Grigoriou, and others), and creating reusable skill files and protocols for Claude-assisted transcription.

**MCP as an interface with historical databases** — exploring Model Context Protocol (MCP) as a bridge between AI agents and historical databases. Current workstreams include: (a) the Riksarkivet MCP server (ra-mcp), which provides full-text and metadata search across AI-transcribed Swedish archival holdings; (b) a custom MCP server for the MarineLives Semantic MediaWiki, wrapping the MediaWiki Action API and SMW Ask API; and (c) preparation for the AI + History Collaboratory session on 24 February 2026.

The GitHub repository associated with this sandbox is: `ottoman-archive/colin-claude-cowork-sandbox` (private, restricted access via Claude GitHub App).

---

## 6. Folder Structure

```
C:\Users\colin\ClaudeCoworkSandbox\
├── CLAUDE.md                      ← This file (global instructions)
├── .claude/
│   └── rules/                     ← Rules files (loaded automatically)
│       ├── ottoman-htr-pipeline.md    ← HTR/OCR pipeline architecture & skill file protocol
│       ├── marinelives-mcp.md         ← MarineLives custom MCP server & HCA corpus guidance
│       ├── ra-mcp.md                  ← Riksarkivet MCP server & collaborative research workflow
│       └── plugins.md                 ← Installed plugin documentation
├── Archive/                       ← Superseded CLAUDE.md versions (v1.2–v4.0), Setup Guide v1.0 & v2.0
├── Cowork-Learnings/              ← Setup guides (current: v3.0), process reflections, session planning
├── Financial-modelling/           ← Financial modelling experiments
├── marinelives-mcp-server/        ← Local copy of the MarineLives custom MCP server code
├── MCP/                           ← MCP session preparation, MarineLives architecture, HCA variant dictionary
│   ├── Meeting-transcripts/           ← Transcripts from collaboratory and planning meetings
│   ├── mcp-server-debug-windows/      ← Skill file for debugging MCP server connections on Windows
│   │   ├── SKILL.md                       ← Six-phase debugging protocol (MSIX config path bug, etc.)
│   │   └── references/                    ← Server-specific reference data (ra-mcp config examples)
│   ├── ra-mcp-server-output/          ← Research memos, TODO lists, source PDFs from ra-mcp sessions
│   └── Skills-ra-mcp-collaborative-research/  ← Skill file for structured ra-mcp research
│       ├── SKILL.md                       ← Five-phase workflow, documentation conventions, constraints
│       └── references/                    ← Companion reference files
│           ├── workflow-principles.md         ← Tool behaviour, source-quality heuristics, search strategy
│           ├── swedish-early-modern-legal-terminology.md  ← Legal/judicial vocabulary (Liliequist & Almbjär 2012)
│           ├── swedish-authority-guide.md      ← Thematic index of Swedish administrative domains
│           └── archive/                       ← Superseded reference file versions
├── Ottoman-archives-context/      ← Background research: HTR/OCR landscape, collaborator matrix
├── Ottoman-archives-wiki/         ← Draft wiki pages for the GitHub repository wiki
├── Research-historian-plugins/    ← Plugin development for historian research workflows
├── Skills-github-pages/           ← Skill file for building and publishing GitHub Pages sites from Cowork
│   └── github-pages-from-cowork/
│       ├── SKILL.md                       ← Six-phase workflow (Plan → Extract → Build → Optimise → Publish → Verify)
│       └── references/
│           ├── performance-patterns.md        ← Chart.js async loading, animation control, lazy loading, boot sequence
│           └── publish-workflow.md             ← Robocopy commands, git workflow, common errors and fixes
├── Skills-htr/                    ← HTR/OCR skill files: triage (V3-Triage), visual capture (V3-S), semantic processing (V3-T)
├── Skills-htr-output/             ← Outputs from applying skill files to documents (e.g., Takvîm-i Vekâyi experiments)
├── SOLM/                          ← School of Oriental Languages materials
└── Tech-capabilities/             ← VLM landscape assessments and visual capture comparisons
```

---

## 7. Registry of Governance Files

This section is the single index of all files that govern how Claude behaves in this sandbox. If you are looking for a rules file, a skill file, or a reference file, start here.

### 7.1 Master instructions

| File | Location | Version | Purpose |
|------|----------|---------|---------|
| CLAUDE.md | Root | 5.3 | Global safety rules, naming conventions, archiving workflow, project context, this registry |

### 7.2 Rules files

Rules files are stored in `.claude/rules/` and loaded automatically at the start of every Cowork session. They fall into two categories: **domain-specific** (relevant only within their topic area) and **cross-cutting** (applicable across all topics).

| File | Category | Version | Scope |
|------|----------|---------|-------|
| `ottoman-htr-pipeline.md` | Domain | 1.1 | Two-stage HTR/OCR pipeline architecture, skill file protocol, processing conventions |
| `marinelives-mcp.md` | Domain | 2.0 | MarineLives custom MCP server, HCA 13/71 deposition corpus, Collaboratory session 3 |
| `ra-mcp.md` | Domain | 1.0 | Riksarkivet MCP server tools, collaborative research skill activation, search best practices |
| `plugins.md` | Cross-cutting | 1.0 | Installed plugin documentation, capabilities, and status |

Rules files can be extended at any time by adding new `.md` files to `.claude/rules/`. All rules files must include in-text versioning as described in Section 3.

### 7.3 Skill files

Skill files encode reusable workflows. Each lives in its own directory with an optional `references/` subdirectory for companion knowledge files.

| Skill | Location | Version | Purpose |
|-------|----------|---------|---------|
| ra-mcp-collaborative-research | `MCP/Skills-ra-mcp-collaborative-research/SKILL.md` | 1.0 | Five-phase workflow for structured research using the Riksarkivet MCP server |
| mcp-server-debug-windows | `MCP/mcp-server-debug-windows/SKILL.md` | 2.0 | Six-phase debugging protocol for MCP server connections on Windows (MSIX config path bug, etc.) |
| github-pages-from-cowork | `Skills-github-pages/github-pages-from-cowork/SKILL.md` | 1.0 | Six-phase workflow for building and publishing GitHub Pages sites from Cowork (data dashboards, static sites) |
| V3-Triage | `Skills-htr/V3-Triage_V1_1_29012026.md` | 1.1 | Document reconnaissance: visual-only assessment of unknown Ottoman documents |
| V3-S-Minimal | `Skills-htr/V3-S-Minimal_28012026.md` | 1.0 | Visual capture for standard nesih script (Gemini) |
| V3-S-Minimal (Takvîm) | `Skills-htr/V3-S-Minimal-Takvim-i-Vekayi-11022026.md` | 1.0 | Visual capture tuned for Takvîm-i Vekâyi gazette (Gemini) |
| V3-S-Siyakat | `Skills-htr/V3-S-Siyakat_Draft_v0_1_03022026.md` | 0.1 | Visual capture for siyakat financial script (draft) |
| V3-T-Takvîm-i-Vekâyi | `Skills-htr/V3-T-Takvîm-i-Vekâyi-V1.1_11022026.md` | 1.1 | Semantic processing for the official gazette |
| V3-T-E-5035-Chronicle | `Skills-htr/V3-T-E-5035-Chronicle-Variant_V1_1_29012026.md` | 1.1 | Semantic processing for historiographical manuscripts |
| V3-T-C17 | `Skills-htr/HTR_V3-T-C17_Transliteration_Translation_V1_28012026.md` | 1.0 | Semantic processing for classical Ottoman correspondence |
| V3-T-Correspondence | `Skills-htr/HTR_V3-T-Correspondence_Transliteration_Translation.md` | — | Semantic processing for general correspondence |
| V3-T-C-Personal | `Skills-htr/HTR_V3-T-C-Personal_Transliteration_Translation.md` | — | Semantic processing for personal correspondence |
| S0-V1-LayoutAnalysis | `Skills-htr/S0-V1-LayoutAnalysis-SKILL-v1_1_03022026.md` | 1.1 | Layout analysis (Stage 0) |
| S0-V1.2-Layout | `Skills-htr/S0-V1.2-Layout-Analysis.md` | 1.2 | Layout analysis (revised) |
| V0-Zone-Analysis | `Skills-htr/V0-Zone-Analysis_v0_2.md` | 0.2 | Zone-level visual analysis (draft) |

The `Skills-htr/` folder also contains two meta-documents: `HTR_Skill_File_Catalog_04022026_v1_1.md` (catalogue of all HTR skill files) and `Metaskill_Architecture_Memo_v1_1_07022026.md` (design rationale for the skill file system).

### 7.4 Reference files

Reference files are companion knowledge for skill files. They live in `references/` subdirectories within each skill directory. Superseded versions are archived to `references/archive/` (see Section 3).

**ra-mcp-collaborative-research references** (`MCP/Skills-ra-mcp-collaborative-research/references/`):

| File | Version | Purpose |
|------|---------|---------|
| `workflow-principles.md` | 1.1 | Tool behaviour, source-quality heuristics, survivorship bias, controlled vocabulary approach |
| `swedish-early-modern-legal-terminology.md` | 1.1 | Legal/judicial vocabulary with English equivalents (Liliequist & Almbjär 2012) |
| `swedish-authority-guide.md` | 1.2 | Thematic index of Swedish administrative domains with search terms |

**mcp-server-debug-windows references** (`MCP/mcp-server-debug-windows/references/`):

| File | Version | Purpose |
|------|---------|---------|
| `ra-mcp-specifics.md` | 1.0 | Known-good config entries, debugging history, Cowork constraints for the ra-mcp server |

**github-pages-from-cowork references** (`Skills-github-pages/github-pages-from-cowork/references/`):

| File | Version | Purpose |
|------|---------|---------|
| `performance-patterns.md` | 1.0 | Chart.js async loading, animation disabling, staggered rendering, lazy loading, boot sequence |
| `publish-workflow.md` | 1.0 | Robocopy commands, git stage/commit/push, common errors (rejected push, nothing to commit, stale cache) |

---

## 8. Version History

**Current version:** 5.3 (17 February 2026) — Added `github-pages-from-cowork` skill file to registry (Section 7.3), its two reference files (Section 7.4), and the `Skills-github-pages/` directory to the folder structure (Section 6). This skill encodes the workflow for building and publishing static GitHub Pages sites from Cowork, developed from the social-media-analysis dashboard project.

**v5.2** (17 February 2026) — Replaced Section 7 (Rules Files) with a comprehensive Registry of Governance Files covering CLAUDE.md, all rules files, all skill files (HTR and MCP), and all reference files with current version numbers and locations. This is now the single index for finding any governance file in the sandbox.

**v5.1** (17 February 2026) — Updated folder structure diagram to match actual sandbox contents (Section 6). Added: `Financial-modelling/`, `marinelives-mcp-server/`, `MCP/Meeting-transcripts/`, `MCP/mcp-server-debug-windows/`, `Research-historian-plugins/`, `SOLM/`. Corrected folder names: `Skills/` → `Skills-htr/`, `Skills-output/` → `Skills-htr-output/`.

**v5.0** (17 February 2026) — Added Riksarkivet MCP server to project context (Section 5). Updated folder structure to show `MCP/` subfolders and the ra-mcp skill file directory (Section 6). Split MCP rules into two domain-specific files: `marinelives-mcp.md` and `ra-mcp.md`; updated rules table (Section 7). Broadened filename exceptions to cover skill files and reference files (Section 3). Added archiving workflow for all versioned file types (Section 3). Archived v4.0.

Full version history (v1.0–v4.0) is preserved in the archived files in `Archive/`.
