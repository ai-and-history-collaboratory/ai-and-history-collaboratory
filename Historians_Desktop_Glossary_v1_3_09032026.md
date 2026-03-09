# The Historian's Desktop — Glossary

**Version:** 1.3
**Date:** 9 March 2026
**Author:** Colin Greenstreet / Claude
**Audience:** AI + History Collaboratory members
**Classification:** Reference document

---

## How to use this glossary

This glossary has been prepared to support AI + History Collaboratory members at our upcoming "Cowork for Historians: Skills and Workflows" session. This session will introduce the concept of a Historian's Desktop as a research environment for historians.

Terms are grouped into six thematic clusters and ordered alphabetically within each. Every entry has three layers:

1. **Plain English** — a one-sentence definition. Start here.
2. **Historian's context** — when and why you will encounter this term in the Collaboratory's work.
3. **Technical detail** — how it actually works under the hood. You may never need this layer, and that is fine.

In the companion HTML version, layers 2 and 3 are hidden behind expandable sections. In this Markdown version, all three layers are visible but clearly labelled.

---

## Cluster 1 — The Environment

*What you see and use.*

---

### Artifact

**Plain English:** A file or interactive element that Claude creates during a conversation — a document, a chart, a code component, or a web page — displayed in a panel alongside the chat.

**Historian's context:** When you ask Claude to produce something substantial — a timeline, a comparative table, a structured report — it often appears as an artifact in a side panel rather than inline in the conversation. Artifacts can be copied, downloaded, or iterated upon. In the AI + History Collaboratory's sessions, artifacts are the primary way Claude delivers working outputs during History vibe coding.

**Technical detail:** Artifacts render in a sandboxed panel within the Claude interface. Supported formats include Markdown, HTML, React components, SVG, and Mermaid diagrams. Artifacts share no state with each other — each is self-contained. In Claude Chat, artifacts appear in the right-hand panel; in Cowork, Claude creates actual files on disk rather than using the artifact panel.

---

### Claude Chat

**Plain English:** The conversational interface where you type messages to Claude and receive replies — the simplest way to interact with the model.

**Historian's context:** This is where most Collaboratory members will start. Claude Chat is a browser-based conversation. You can create Projects within Chat to organise related conversations, attach files for Claude to read, and save skill files as project knowledge. Chat does not have access to your local file system — it works only with what you upload or paste.

**Technical detail:** Claude Chat runs in a web browser at claude.ai or via the mobile app. Each conversation has a context window — a finite amount of text Claude can hold in working memory at once. Chat supports file uploads (PDFs, images, text files), web search, and tool integrations via MCP servers configured in your account settings. Conversations are stored server-side by Anthropic.

---

### Claude Code

**Plain English:** A command-line tool that lets Claude work directly with files on your computer — reading, writing, and running code from a terminal window.

**Historian's context:** Claude Code is an advanced platform, suitable for developer historians who have worked with Claude Cowork for at least a couple of months, who understand the basic principles of Python (not how to write it, but how to read its structure), and who are comfortable working with the command line (helped by Claude Cowork) and have tried — supervised by Claude Cowork — to successfully push commits to a GitHub site. Claude Code is the environment where you can define and test custom subagents for pipelines like the Ottoman HTR workflow. It runs directly on your machine (not inside a virtual machine), which gives it power but also means it needs careful safety precautions — launching from the right directory, using deny rules (explicit prohibitions that block Claude Code from accessing specific files or directories), and never granting broad file access.

**Technical detail:** Claude Code is a Node.js application installed via npm. It operates with your user-level file permissions on the host operating system. It supports custom subagent definitions as Markdown files placed in `.claude/agents/`, YAML frontmatter for configuration, and explicit tool permissions per agent. Permission modes control how much autonomy Claude Code has: "Normal" (default) asks before every significant action. On macOS, Seatbelt sandboxing provides OS-level isolation; on Windows, no equivalent exists — safety depends on deny rules and careful launch discipline.

---

### Claude Cowork

**Plain English:** An autonomous working environment where Claude can read your files, create new documents, run code, and complete multi-step tasks — working independently within a folder you designate.

**Historian's context:** Cowork is the core of the Historian's Desktop. When you give Cowork a folder of transcribed documents and ask it to summarise, index, and cross-reference them, it works through the task autonomously, creating files as it goes. It reads your CLAUDE.md file for instructions before starting. Cowork is where skill files, workflows, and governance come together as a working research environment. The Collaboratory's hands-on sessions use Cowork as the primary platform.

**Technical detail:** Cowork runs inside a Linux virtual machine (Hyper-V on Windows) rather than directly on your operating system. File access between Windows and the VM is bridged via virtiofs. Only folders explicitly shared with the VM are accessible. Cowork deploys subagents automatically and opaquely — the user cannot currently define custom subagents through the same mechanism as Claude Code, but a well-crafted CLAUDE.md can instruct Cowork to follow a multi-stage workflow within a single context. Cowork conversations are stored locally on your machine and do not sync to claude.ai.

---

### Claude Desktop

**Plain English:** The downloadable application that gives you access to Claude Chat and Claude Cowork from your desktop, without needing a browser.

**Historian's context:** Claude Desktop is the application you install on your Windows or Mac machine. It contains both Chat and Cowork as tabs within the same interface, plus access to Claude Code. For Collaboratory members, installing Claude Desktop is the first step toward using Cowork and the Historian's Desktop environment. The Setup Guide walks through the installation process.

**Technical detail:** Claude Desktop is an Electron application — a desktop app built using web technologies. It runs multiple Chromium-based sub-processes. On Windows, a background service called cowork-svc.exe manages the Cowork virtual machine (starting, stopping, configuring networking, and bridging file access). Claude Desktop requires a paid Claude subscription (Pro, Max, Team, or Enterprise) for Cowork access; it is not available on the free tier.

---

### Claude Project

**Plain English:** A named workspace within Claude Chat that groups related conversations, files, and instructions together.

**Historian's context:** When you create a Claude Project — for instance, "Ottoman Archive HTR" or "Hackathon Planning" — you can attach reference files, save skill files as project knowledge, and set a CLAUDE.md-style instruction document that applies to every conversation within the project. Projects are the organisational unit for focused work in Chat. The Collaboratory's own project files live in a Claude Project.

**Technical detail:** Project knowledge is searched via a dedicated tool (project_knowledge_search) that Claude prioritises over web search and its own training knowledge. Each project has its own memory space — memories from one project do not cross into another. Files attached to a project are available to all conversations within it. Projects exist within Claude Chat and do not directly connect to Cowork's file system.

---

### GitHub organisation

**Plain English:** A shared space on GitHub where a group can publish and manage code repositories collectively, rather than under a single person's account.

**Historian's context:** The AI + History Collaboratory uses the `ai-and-history-collaboratory` GitHub organisation for knowledge development, sharing, and collaborative publishing. The Collaboratory is an asynchronous forum for a group of fourteen historians in the United Kingdom, Europe, and North America — it is not specifically about History vibe coding, but about building and sharing knowledge across a range of historical methods and specialisms. A separate GitHub organisation, `ottoman-archive`, has been created by Colin Greenstreet to support the "Opening the Ottoman Archive" initiative, a spinoff project from the Collaboratory. When you publish a tool built in Cowork, it goes to the relevant organisation's repository. Publishing is optional, but it is how individual tools become community resources.

**Technical detail:** A GitHub organisation is an account type that owns repositories collectively. Members can have different permission levels (owner, member, outside collaborator). Repositories within an organisation can be public or private. The Claude GitHub App can be configured with restricted access to specific repositories only — for the Ottoman Archive work, it is limited to the `colin-claude-cowork-sandbox` repository.

---

### Historian's Desktop

**Plain English:** A historical research environment implemented in Claude Cowork, combining specialised knowledge, structured workflows, external archive connections, and governance files into a coherent platform for scholarly work.

**Historian's context:** The Historian's Desktop is not a product or a single piece of software. It is the name for the research environment you create when you combine Cowork with skill files, workflows, MCP connections, and governance documents like CLAUDE.md. The guiding principle is that the historian is the craftsperson; the AI tools are specialist instruments to be picked up deliberately, used with care, and put down. This stands in deliberate contrast to the default AI philosophy that treats friction as a bug to be automated away. The environment is capable of supporting historians of all types — social, economic, material, political, diplomatic, and beyond.

**Technical detail:** The Historian's Desktop is implemented in Claude Cowork. Its components include: skill files (script-specific, genre-specific, and method-specific knowledge), workflows (multi-stage pipelines with human checkpoints), MCP servers (connections to external archives and services), and governance files (CLAUDE.md safety rules and research protocols). The environment is designed to be extensive and tailorable — historians extend it by adding or modifying skill files, workflows, MCP connections, and governance files to suit their own research domains.

---

### Plugin

**Plain English:** A packaged extension that adds new capabilities to Cowork — currently planned but not yet available.

**Historian's context:** Anthropic has indicated that Cowork will support a plugin system in future, allowing pre-built workflows to be installed and invoked by name. For the Collaboratory, this means that pipelines currently configured through CLAUDE.md instructions — such as the three-stage HTR pipeline — could eventually be packaged as plugins with dedicated commands. This is on the horizon but not yet available for use.

**Technical detail:** The plugin system is expected to support explicit subagent definitions, context isolation between agents, and slash-command invocation. Current workarounds involve encoding multi-stage workflows in CLAUDE.md and skill files, which instruct Cowork to follow the pipeline within a single context rather than running isolated subagents. The transition from CLAUDE.md-encoded workflows to proper plugins is a planned migration path.

---

## Cluster 2 — Governance and Configuration

*The files that control behaviour.*

---

### CLAUDE.md

**Plain English:** A configuration file you place in a working folder that Claude reads before beginning any task — your standing instructions.

**Historian's context:** Think of CLAUDE.md as analogous to a research methodology section. It tells Claude what safety rules to follow, how to name files, what communication style to use, and what the project context is. When Cowork opens your sandbox folder and finds a CLAUDE.md, it reads and follows those instructions before doing anything else. Writing a good CLAUDE.md is one of the first skills Collaboratory members develop — it is how you govern the AI's behaviour in your research environment.

**Technical detail:** CLAUDE.md is a plain-text Markdown file read automatically from the working directory by Cowork, Code, and Chat Projects. It has no enforced schema — its power comes from being natural-language instructions that Claude follows. Multiple CLAUDE.md files can exist at different directory levels; the most local one takes precedence. The file is not encrypted or access-controlled — it relies on Claude's instruction-following rather than technical enforcement. This means CLAUDE.md is a governance mechanism, not a security boundary.

---

### Deny rules

**Plain English:** Explicit prohibitions that block Claude Code from accessing specific files or directories, regardless of what it asks to do.

**Historian's context:** When working in Claude Code, deny rules are your safety net. They are entries in a settings file that prevent Claude from touching sensitive directories — your main Documents folder, your email, system files — even if you accidentally approve an action. For Collaboratory members testing subagent pipelines, setting deny rules before the first test run is a mandatory safety step covered in the Setup Guide.

**Technical detail:** Deny rules are defined in `.claude/settings.json` as an array of glob patterns under the `deny` key. They override all permission modes — even if a user approves an action, deny rules block it. They apply to file reads, writes, and command execution. Project-level settings (in the project root) take precedence over user-level settings (`~/.claude/settings.json`). Deny rules do not exist in Cowork, which relies on VM isolation and virtiofs folder sharing instead.

---

### Markdown

**Plain English:** A lightweight text format that uses simple symbols (like `#` for headings and `**` for bold) to structure documents — readable as plain text and convertible to formatted output.

**Historian's context:** Almost everything in the Historian's Desktop is written in Markdown: CLAUDE.md files, skill files, subagent definitions, memos, and research documents. Learning Markdown's basics (headings, bold, links, lists) takes about ten minutes and is one of the most useful micro-skills for working with Claude. When Claude creates documents in Cowork, it defaults to Markdown unless you ask for something else.

**Technical detail:** Markdown (.md) files are plain UTF-8 text. They can include YAML frontmatter (metadata between `---` markers at the top of the file). Markdown renders natively in GitHub, Claude's artifact panel, and most text editors. It converts cleanly to HTML, PDF, and Word formats. The specific dialect used in the Historian's Desktop is CommonMark with GitHub Flavoured Markdown extensions (tables, task lists, fenced code blocks).

---

### Permission mode

**Plain English:** Claude Code's system for controlling how much it can do without asking you first.

**Historian's context:** Permission mode only applies in Claude Code, not in Cowork. In "Normal" mode (the default and the only mode Collaboratory members should use), Claude Code asks before every significant action — reading a file, writing a file, running a command. You approve each action individually. The rule for Collaboratory work is simple: stay in Normal mode, always choose "Yes" (one time) rather than "Yes for this session."

**Technical detail:** Claude Code offers multiple permission levels. Normal mode requires per-action approval. Other modes reduce friction at the cost of safety. The `--dangerously-skip-permissions` flag disables all safety checks entirely — it exists for isolated Docker containers and should never be used on a workstation with real files. Permission mode interacts with deny rules: deny rules override approvals at any permission level.

---

### Reference file

**Plain English:** A companion document bundled with a skill file that provides background knowledge — terminology, historical context, or domain-specific guidance — for Claude to draw on as needed.

**Historian's context:** When a skill file tells Claude how to do a task, a reference file tells Claude what it needs to know to do it well. For instance, the Riksarkivet collaborative research skill is bundled with reference files on Swedish early modern legal terminology, Swedish administrative structures, and specific court systems. You do not need to write reference files from scratch — they can be built collaboratively with Claude during research sessions, then saved for reuse. Reference files are one of the ways the Historian's Desktop accumulates domain knowledge over time.

**Technical detail:** Reference files are Markdown documents (typically named `references/*.md`) stored alongside the skill file, often bundled together in a ZIP folder for distribution. They have no required schema or YAML frontmatter — they are plain prose or structured reference material. The skill file's instructions tell Claude when and how to consult them (e.g., "Before beginning a research session, read the following reference files if they exist in `references/`"). Reference files are loaded into the context window on demand, so they consume context space only when consulted.

---

### Sandbox

**Plain English:** A restricted area where a program can operate without affecting the rest of your system — like a playpen for software.

**Historian's context:** The sandbox is the specific folder you designate for Cowork or Claude Code to work in. We recommend you place the sandbox at `C:\[Your User Name]\ClaudeSandBox`. Within the sandbox you can develop your own folder and subfolder structure, and add to and modify this structure, working with Claude Cowork. You put only copies of files in the sandbox, never originals. Even though Cowork's VM provides genuine isolation, the sandbox folder remains good practice as an additional safety layer — belt and braces. Setting up a sandbox folder is the first practical step in the Setup Guide.

**Technical detail:** The term "sandbox" is used at two levels. At the application level, it means the designated working directory. At the OS level, Cowork provides genuine sandboxing through its Linux VM — code executes inside the VM, not on the host. macOS provides additional sandboxing for Claude Code via Apple's Seatbelt framework. Windows has no equivalent OS-level sandbox for Claude Code, which is why the working-directory sandbox and deny rules are especially important on Windows.

---

### Skill file

**Plain English:** A document that gives Claude specialised knowledge or instructions for a specific type of task — like handing a colleague a reference sheet before they start work.

**Historian's context:** Skill files are one of the most powerful components of the Historian's Desktop. A skill file for Ottoman Naskh script tells Claude what to look for when checking transcriptions of documents in that script. A skill file for collaborative research with the Riksarkivet encodes a five-phase workflow. You can create skill files for any domain — a particular archive, a document genre, a research methodology. The Skill File Teaching Module helps you understand and evaluate skill files, and the History vibe coding initiative includes building new ones.

**Technical detail:** A skill file is a Markdown document with YAML frontmatter containing at minimum a `name` and `description` field. The description serves as a trigger — it tells Claude when to activate the skill. Anthropic's guidance recommends "pushy" trigger descriptions to combat undertriggering (Claude failing to activate a relevant skill). Skill files are placed in a `skills/` directory and can be loaded in Cowork (from the working folder), Claude Code (via the `skills` YAML field in agent definitions), or Chat Projects (as project knowledge). They have no enforced schema beyond the YAML frontmatter requirement.

---

### Trigger description

**Plain English:** The part of a skill file's metadata that tells Claude when to activate it — a set of conditions that say "use this skill when you see these kinds of tasks."

**Historian's context:** A well-written trigger description is the difference between a skill that activates reliably and one that sits unused. If your Riksarkivet research skill only triggers when someone says "search the Riksarkivet," it will miss requests phrased as "look in the Swedish archives." Anthropic's guidance is to make triggers "pushy" — casting a wide net and listing many synonyms and variations. The Skill File Teaching Module examines trigger quality as one of its core analytical modules.

**Technical detail:** The trigger description lives in the `description` field of a skill file's YAML frontmatter. It is matched against the user's input by Claude's skill selection system. Effective triggers include: positive triggers (when to activate), negative triggers (when not to activate), synonyms and variant phrasings, and specific keywords. Undertriggering (false negatives) is a more common problem than overtriggering (false positives) in practice.

---

### YAML frontmatter

**Plain English:** Structured metadata at the top of a Markdown file — enclosed between two lines of three dashes — that provides machine-readable information about the document.

**Historian's context:** You will encounter YAML frontmatter at the top of every skill file and every subagent definition. It looks like a small block of labelled fields (name, description, tools, model) before the main content begins. You do not need to write YAML from scratch — Claude generates it — but understanding what the fields mean helps you evaluate and modify skill files during teaching sessions and History vibe coding.

**Technical detail:** YAML (YAML Ain't Markup Language) is a human-readable data serialisation format. Frontmatter is delimited by `---` on its own line at the start and end of the block. Required fields for skill files are `name` and `description`. Subagent definitions in Claude Code add `tools` (which tools the agent can use), `model` (which Claude model to use, or `inherit` from the parent), and optionally `allowed_tools` or `disallowed_tools` for fine-grained control. Indentation is significant in YAML — incorrect indentation breaks parsing.

---

## Cluster 3 — Architecture

*What is happening under the hood.*

---

### Context window

**Plain English:** The working memory of a Claude conversation — everything Claude can "see" at once, including your messages, its replies, any documents, and its instructions.

**Historian's context:** The context window is finite. When a conversation grows very long or you feed Claude many documents at once, older material may fall out of what Claude can actively reference. This is why the Historian's Desktop uses versioned files saved to disk rather than relying on conversation history — conversation memory is ephemeral, but files persist. Subagents have separate context windows from each other, which is why they can focus on specific tasks without being overwhelmed by the full pipeline's information.

**Technical detail:** Context windows are measured in tokens (roughly three-quarters of a word). Claude's current models have context windows of 200,000 tokens. The context window contains: the system prompt, CLAUDE.md instructions, skill files, conversation history, uploaded documents, and tool results. When context is exhausted, Claude cannot process additional input without losing earlier material. In subagent architectures, each subagent has its own isolated context window, preventing information leakage between pipeline stages.

---

### Electron

**Plain English:** A framework for building desktop applications using web technologies — it is why Claude Desktop looks and behaves like a web page running in its own window.

**Historian's context:** You will probably never need to think about Electron directly. It matters only when troubleshooting: if Claude Desktop is consuming unexpected memory or CPU, it is because Electron runs multiple browser-like processes in the background. The Task Manager on Windows will show several Claude-related processes — this is normal for an Electron application.

**Technical detail:** Electron bundles Chromium (the browser engine behind Chrome) and Node.js into a single application. Each Electron window runs in its own renderer process. Claude Desktop's main process manages the Cowork VM service, MCP connections, and window management. The multiple sub-processes visible in Task Manager are standard Electron architecture, not a sign of malfunction.

---

### Linux VM (Virtual Machine)

**Plain English:** A complete computer simulated in software — Cowork runs its own miniature Linux computer inside your Windows machine.

**Historian's context:** This is the single most important architectural fact about Cowork for safety purposes. When Cowork runs code, creates files, or processes your documents, it does so inside a self-contained Linux environment, not directly on your Windows system. This provides genuine isolation — if something goes wrong inside the VM, your main system is protected. This was discovered during the Setup Guide's Day Two investigation and significantly improved the safety assessment of Cowork.

**Technical detail:** Cowork uses Hyper-V (Microsoft's built-in virtualisation technology) to run a Linux VM. The VM's filesystem is stored in VHDX (Virtual Hard Disk Extended) files: rootfs.vhdx for the Linux operating system and sessiondata.vhdx for session storage. The VM is managed by cowork-svc.exe, a Windows service that handles startup, shutdown, networking, and file access bridging. File sharing between Windows and the VM uses virtiofs. Only explicitly shared folders are accessible inside the VM.

---

### System prompt

**Plain English:** The instructions loaded into a Claude instance at startup that define its role, expertise, and constraints — what Claude "knows about itself" before you say anything.

**Historian's context:** Every time you start a conversation with Claude, a system prompt is active behind the scenes. In standard Chat, this is Anthropic's default prompt. In a Claude Project, your project instructions are added to it. For subagents in Claude Code, the system prompt is the body of the agent's Markdown definition file — the text below the YAML frontmatter. Understanding that system prompts exist helps explain why Claude behaves differently in different contexts and why well-written CLAUDE.md files and skill files matter.

**Technical detail:** The system prompt occupies the first portion of the context window. It is not visible to the user in the conversation but is always present. System prompts can instruct Claude on persona, domain expertise, output format, safety constraints, and tool usage. They are set by Anthropic (base behaviour), by the application (Claude Chat, Cowork, or Code each add their own instructions), and by the user (via CLAUDE.md, project instructions, or subagent definitions). Later instructions generally override earlier ones when they conflict.

---

### VHDX

**Plain English:** The file format Windows uses for virtual machine disk images — the container that holds Cowork's Linux filesystem.

**Historian's context:** You will never interact with VHDX files directly. They matter only for understanding where Cowork's data lives on your machine and for troubleshooting disk space issues. Cowork uses two VHDX files: one for the Linux operating system itself (rootfs.vhdx) and one for session data (sessiondata.vhdx). If Cowork's VM becomes corrupted, these files may need to be reset — but this is an extreme troubleshooting step.

**Technical detail:** VHDX (Virtual Hard Disk Extended) is Microsoft's format for Hyper-V virtual disk images, supporting disks larger than 2 TB with built-in corruption protection. Cowork's VHDX files are stored in the Claude Desktop application data directory. They are dynamically expanding — they grow as data is written but do not automatically shrink when data is deleted. Session data (conversation history, working files) lives in sessiondata.vhdx and does not sync to claude.ai.

---

### virtiofs

**Plain English:** The file-sharing method that Cowork uses to make your Windows folders accessible inside its Linux virtual machine.

**Historian's context:** virtiofs is the invisible bridge between your sandbox folder on Windows and Cowork's working environment inside the VM. When you tell Cowork to work with files in your sandbox, virtiofs makes that folder appear inside the Linux VM. Only folders you explicitly share are bridged — Cowork cannot see the rest of your file system. If virtiofs fails, Cowork will report an error — the troubleshooting sequence is to restart Cowork, check that the shared folder exists and is accessible, and if the problem persists, restart Claude Desktop.

**Technical detail:** virtio-fs is a high-performance shared file system for virtual machines, built on the FUSE (Filesystem in Userspace) protocol and virtio transport. It provides near-native file access speeds compared to traditional network file sharing. In Cowork's architecture, the Windows cowork-svc.exe service configures the virtiofs mount points when the VM starts. Mount failures typically indicate that the VM service has crashed or that the shared folder path has changed.

---

## Cluster 4 — Workflows and Pipelines

*How work moves through stages.*

---

### Annotation layering

**Plain English:** The practice of each stage in a pipeline adding its own observations to a document while preserving everything previous stages noted — building up a cumulative record.

**Historian's context:** Annotation layering is specific to the HTR pipeline methods being developed in the "Opening the Ottoman Archive" initiative, a spinoff from the AI + History Collaboratory. In that pipeline, the visual capture agent adds flags noting where the machine transcription may have missed text. The palaeographic QA agent then adds its own flags while keeping all the visual capture flags intact. By the time the semantic processing agent finishes, the document carries a multi-layer record of every observation from every stage. This is analogous to marginalia in scholarly editing — each reader's notes accumulate without erasing previous ones.

**Technical detail:** Annotation layering is implemented through structured inline flags in the transcription output. Each flag is prefixed with its stage identifier (VC, PQ, SP) and includes a severity level and description. Flags are preserved in the output file between stages — no stage may delete or modify another stage's flags. The cumulative annotation serves as both an audit trail and a feedback mechanism, since later stages can reference earlier flags (e.g., `[SP-FEEDBACK-PQ: possible misreading at line 4]`).

---

### Deliberate friction

**Plain English:** The design principle that requiring human review at each stage of an AI workflow is a feature, not a limitation — it forces the historian to form judgments rather than passively receive results.

**Historian's context:** Deliberate friction is the philosophical core of the Historian's Desktop. When you review each pipeline stage's output before invoking the next, you are forced to assess the work in progress. You cannot passively receive a finished product. Each review creates an audit trail — your decision to proceed or send work back is itself a scholarly judgment. This stands in contrast to fully automated pipelines that eliminate human involvement. The Historian's Desktop treats the historian as the craftsperson, not the customer.

**Technical detail:** Deliberate friction is implemented through sequential invocation with human checkpoints (see both entries). It produces three practical benefits: intellectual engagement (the historian must evaluate), audit trails (each checkpoint decision is recorded), and feedback loops (observations at later stages can trigger re-examination at earlier stages). The design is informed by the scholarly principle that the process of verification is itself an act of interpretation.

---

### Human checkpoint

**Plain English:** A mandatory pause between pipeline stages where the historian reviews the output, decides whether to proceed, and takes responsibility for the next step.

**Historian's context:** Human checkpoints apply to any historical research workflow, not only HTR pipelines. The principle is the same wherever multi-stage AI processing is involved: you — not the AI — decide whether the output is good enough to pass to the next stage. You might approve it, re-run the stage, flag issues for later, or abandon the task entirely. Each checkpoint is a moment of scholarly judgment. Without checkpoints, the pipeline would be a black box. With them, you maintain intellectual ownership of the research process. See also the Workflow entry for how checkpoints fit within broader research sequences.

**Technical detail:** Human checkpoints are enforced by design rather than by technical mechanism. In Claude Code, sequential invocation naturally requires the user to invoke each subagent manually. In Cowork, checkpoints must be encoded in CLAUDE.md instructions (e.g., "After completing stage 1, present your findings and wait for my approval before proceeding to stage 2"). There is currently no technical enforcement preventing a user from instructing Claude to skip checkpoints — the constraint is procedural and professional.

---

### Pipeline

**Plain English:** A sequence of processing stages where the output of one stage becomes the input of the next — each stage does one job and passes the result forward.

**Historian's context:** Pipelines are the organising metaphor for complex multi-step work in the Historian's Desktop — any research process that has distinct sequential phases can be modelled as a pipeline. A specific example is the Ottoman HTR pipeline, which has three stages: visual capture QA (checking whether the machine transcription matches the image), palaeographic QA (assessing whether the script has been read correctly), and semantic processing (interpreting the content historically). Each stage is handled by a specialised subagent. But the pipeline pattern applies equally to other research workflows — a source discovery, source evaluation, and synthesis pipeline, for instance.

**Technical detail:** In Claude Code, pipelines are implemented through sequential subagent invocation — each agent produces annotated output files that the next agent reads. In Cowork, pipelines are implemented through CLAUDE.md instructions that direct Cowork to follow a defined sequence with human checkpoints between stages. Pipeline stages communicate through files (the annotated transcriptions), not through shared memory or context windows.

---

### Sequential invocation

**Plain English:** The practice of calling pipeline stages one at a time, in order, rather than running them simultaneously — each stage completes before the next begins.

**Historian's context:** You invoke one pipeline stage, review its output, then invoke the next stage, review again, and so on. You never run all stages at once. This is sequential invocation, and it is both a design choice (enabling human checkpoints) and a practical necessity (each stage needs the previous stage's output). The deliberate slowness is the point — it creates the space for scholarly judgment.

**Technical detail:** In Claude Code, sequential invocation is the natural mode — the user invokes each subagent by name using a command or natural language instruction. Each subagent runs in its own context window and produces output files. In Cowork, sequential invocation must be explicitly instructed in CLAUDE.md, since Cowork's default behaviour is to parallelise tasks when it can. The key instruction is: "Complete stage N, present results, and wait for approval before beginning stage N+1."

---

### Subagent

**Plain English:** A specialised AI instance with its own focus, instructions, and working memory, invoked by a main agent to handle a specific task — like calling in a specialist consultant.

**Historian's context:** In the Ottoman HTR pipeline, three subagents play distinct roles: the visual capture agent checks the image against the transcription, the palaeographic QA agent assesses whether the script has been read correctly, and the semantic processing agent interprets the historical content. Each brings different expertise and different instructions. The analogy from academic life is a research team with an archivist, a palaeographer, and a historian — each working on the same material from different perspectives.

**Technical detail:** In Claude Code, subagents are defined as Markdown files in `.claude/agents/` with YAML frontmatter specifying name, description, tools, and model. Each subagent runs in its own isolated context window — observations from one subagent do not bleed into another's context. In Cowork, subagents are deployed automatically and opaquely by the system — the user describes a task and Cowork decides whether and how to parallelise it. Users cannot currently define custom subagents in Cowork through the same mechanism as Claude Code.

---

### Workflow

**Plain English:** A defined sequence of steps for completing a research task — the plan that says what to do first, second, third, and how to handle what goes wrong.

**Historian's context:** A workflow is broader than a pipeline. The Riksarkivet collaborative research skill encodes a five-phase workflow: scoping, systematic term mapping, evidence collection, synthesis, and documentation. Each phase has defined actions, constraints, and outputs. Workflows in the Historian's Desktop are encoded in skill files and CLAUDE.md instructions — they are the "how to do the work" component that turns Claude from a general-purpose assistant into a research environment with disciplined procedures.

**Technical detail:** Workflows are implemented as natural-language instructions in skill files or CLAUDE.md documents. They can include: phase definitions with entry and exit criteria, tool-use patterns (which MCP tools to use at which phase), confidence grading frameworks, output format specifications, and error handling procedures. Workflows are not enforced by technical mechanisms — they rely on Claude's instruction-following. A workflow that spans multiple sessions requires persistence through saved files, since conversation context does not carry between sessions.

---

## Cluster 5 — The MCP Ecosystem

*External connections.*

---

### API / API key

**Plain English:** An API (Application Programming Interface) is a structured way for software to talk to other software. An API key is the credential — like a password — that identifies who is making the request.

**Historian's context:** APIs are how the tools in the Historian's Desktop connect to external services. When Claude searches the Riksarkivet via the ra-mcp server, it is using the Riksarkivet's API. For the AI + History Collaboratory's demonstrations and sessions, the MCP servers we use or have developed connect to publicly accessible APIs that do not require API keys, so API key security is not an issue for current Collaboratory work. API keys become relevant when connecting to paid services like AI model APIs (Gemini, Anthropic), where they should be treated as sensitive credentials: never shared in documents, never committed to GitHub repositories, and stored securely.

**Technical detail:** APIs define endpoints (URLs), request formats (typically JSON), authentication methods (API keys, OAuth tokens), and response formats. REST APIs use HTTP methods (GET, POST, PUT, DELETE) to perform operations. API keys are typically long alphanumeric strings passed in request headers. Rate limits restrict how many requests can be made per time period. Most archival and cultural heritage APIs (IIIF, OAI-PMH, Riksarkivet) are publicly accessible without authentication, but AI model APIs (Gemini, Anthropic) require keys with associated billing.

---

### IIIF

**Plain English:** International Image Interoperability Framework — a set of standards that lets institutions share high-resolution images in a consistent way, so any compatible viewer can display images from any participating collection.

**Historian's context:** IIIF is how many archives and libraries serve their digitised document images. When you view a manuscript page on the British Library's or Gallica's website, you are often using a IIIF viewer. For the Historian's Desktop, IIIF matters because it is the standard way to retrieve the source images that HTR pipelines process. The IIIF Static Viewer for the Ottoman Government Gazette — one of the Collaboratory's completed exemplar projects — demonstrates how IIIF can be used in History vibe-coded tools. A general-purpose IIIF MCP server is identified as a significant gap and opportunity.

**Technical detail:** IIIF defines several APIs: the Image API (requesting images at specific sizes, regions, and rotations), the Presentation API (describing how images relate to each other as pages, canvases, and manifests), and the Search API (full-text search within annotated images). IIIF manifests are JSON-LD documents that describe a collection's structure. Most major cultural heritage institutions publish IIIF endpoints. An MCP server wrapping IIIF would allow Claude to retrieve and examine archival images programmatically during research sessions.

---

### MCP (Model Context Protocol)

**Plain English:** A standard way for AI models like Claude to connect to external tools and services — it defines how Claude asks for information and how services respond.

**Historian's context:** MCP is what makes the Historian's Desktop extensible. Without MCP, Claude can only work with what you upload or paste. With MCP servers connected, Claude can search archives, read RSS feeds, and interact with external databases — all from within a conversation. The Historian's Desktop's current MCP connections include the Riksarkivet server (ra-mcp), an Old Bailey Online MCP server, three mini VRTI MCP servers, and a custom RSS reader. Planned connections include IIIF, OAI-PMH, and Zotero.

**Technical detail:** MCP defines a protocol for tool discovery (what tools are available), tool invocation (calling a tool with parameters), and result handling (processing the response). MCP servers expose tools that Claude can call. The protocol uses JSON-based message passing. MCP servers can run locally (on your machine) or remotely (hosted as web services). Claude Desktop and Claude Chat both support MCP server connections configured in account or application settings.

---

### MCP server

**Plain English:** A small program that acts as a bridge between Claude and an external service — translating Claude's requests into the service's language and returning the results.

**Historian's context:** Each external connection in the Historian's Desktop runs through an MCP server. The ra-mcp server connects Claude to the Riksarkivet's holdings. The RSS reader MCP server connects Claude to Substack and other feeds. When Collaboratory members build IIIF or OAI-PMH MCP servers, they are creating new bridges to new collections. A key finding from the Collaboratory's work is that nearly all MCP servers for cultural heritage are built by individual volunteer developers, not by the institutions that provide the underlying APIs.

**Technical detail:** MCP servers can be built in Python (using the FastMCP library) or TypeScript/Node.js (using the MCP SDK). A server exposes one or more tools, each with a name, description, parameter schema, and handler function. Servers can be configured to run locally via stdio (standard input/output) or remotely via Server-Sent Events (SSE). Claude Desktop discovers available tools at startup by querying each configured server. MCP servers maintain their own authentication to external services — Claude does not need separate credentials for each connected service.

---

### OAI-PMH

**Plain English:** Open Archives Initiative Protocol for Metadata Harvesting — a standard that lets you download catalogue records from libraries and archives in bulk.

**Historian's context:** OAI-PMH is how many institutional repositories and digital libraries make their metadata available for harvesting. If you want to download all the catalogue records from a digital archive to build a local finding aid or search index, OAI-PMH is typically the mechanism. Like IIIF, a general-purpose OAI-PMH MCP server is identified as a significant gap — building one would allow any Claude-based research environment to harvest metadata from any OAI-PMH-compliant repository.

**Technical detail:** OAI-PMH uses HTTP requests with six defined verbs: Identify (describe the repository), ListSets (available collections), ListMetadataFormats (supported schemas), ListIdentifiers (record IDs), ListRecords (full records), and GetRecord (single record). Records are typically returned in Dublin Core (dc) or MARC XML format. The protocol supports selective harvesting by date range and collection set. Responses include resumption tokens for paginating through large result sets.

---

### RSS feed

**Plain English:** A standardised format for websites to publish updates — new posts, articles, or episodes — that readers and software can subscribe to.

**Historian's context:** The Collaboratory's RSS reader MCP server was built to solve a specific problem: Claude cannot reliably access Substack content through standard web tools because of JavaScript rendering and indexing gaps. The MCP server parses RSS feeds directly, giving Claude access to the full text of new posts. This is relevant for staying current with Generative Lives, Generative History, One Useful Thing, and other newsletters the Collaboratory follows.

**Technical detail:** RSS (Really Simple Syndication) feeds are XML documents served at a known URL (typically `/feed` or `/rss`). Each feed contains a list of items with title, link, publication date, and content (either full text or summary). Atom is a related standard with similar functionality. The RSS reader MCP server fetches and parses these XML documents, exposing each feed's contents as searchable tool results. RSS feeds bypass JavaScript rendering entirely, which is why they succeed where web scraping fails for sites like Substack.

---

### Tool *(in the MCP sense)*

**Plain English:** A specific capability that an MCP server offers to Claude — a named action like "search transcriptions" or "fetch catalogue records" that Claude can invoke with defined parameters.

**Historian's context:** When Claude uses the Riksarkivet MCP server, it calls specific tools: `search_transcribed` (searching within transcribed documents), `search_metadata` (searching catalogue records), and others. Each tool has a defined purpose and expects specific inputs. Understanding what tools are available — and what each one does — is part of learning to work effectively with MCP connections. The Riksarkivet collaborative research skill file maps which tools to use at which phase of the research workflow.

**Technical detail:** An MCP tool has a name (string identifier), description (natural language explanation of purpose and usage), input schema (JSON Schema defining required and optional parameters), and a handler function (the code that executes when the tool is called). Claude selects tools based on their descriptions matching the user's intent. Tool results are returned as text or structured data within the conversation context. A single MCP server can expose multiple tools, and multiple MCP servers can be connected simultaneously.

---

## Cluster 6 — Research Methods and Domain Terms

*The scholarly side.*

---

### Finding aid

**Plain English:** A document that describes the contents and organisation of an archival collection — the map that tells researchers what is in a repository and how to locate it.

**Historian's context:** Finding aids are written for archivists, not researchers, which is why they can be dense and abbreviated. Several planned History vibe coding projects address this gap: the Finding Aid Plain-English Guide translates catalogue descriptions into research intelligence, and the Archive Research Planner uses finding aids as inputs for research planning. Finding aids vary enormously in quality and detail between institutions. Published calendars — chronological summaries of document collections — serve a similar function and work equally well as inputs.

**Technical detail:** Finding aids typically follow the Encoded Archival Description (EAD) standard, an XML schema for describing archival collections. They are structured hierarchically: collection, series, sub-series, file, item. Key elements include scope and content notes, access conditions, related materials, and administrative history. Many institutions publish finding aids as PDF or HTML documents alongside or instead of structured EAD. OAI-PMH can be used to harvest finding aid metadata from compliant repositories.

---

### Ground truth

**Plain English:** A verified, human-checked transcription of a document that serves as the benchmark against which automated transcriptions are measured.

**Historian's context:** When testing whether an HTR system can read Ottoman Naskh or Dīvānī script correctly, you need ground truth — a transcription you know is accurate because a qualified human produced it. Building ground truth is slow and requires palaeographic expertise, which is why it is a bottleneck for HTR development. In the Collaboratory's work, ground truth documents are the gold standard against which Gemini and Claude transcription outputs are compared.

**Technical detail:** Ground truth in HTR typically takes the form of line-by-line or region-by-region transcriptions aligned to specific zones of a document image. Quality metrics for HTR include Character Error Rate (CER) and Word Error Rate (WER), both calculated against ground truth. Ground truth creation tools include Transkribus, eScriptorium, and manual transcription in structured formats. For Ottoman documents across eight script types, ground truth creation requires script-specific palaeographic expertise — no single scholar typically covers all variants.

---

### HTR (Handwritten Text Recognition)

**Plain English:** Technology that converts images of handwritten text into machine-readable text — teaching a computer to read handwriting.

**Historian's context:** HTR is the foundational technology for the "Opening the Ottoman Archive" initiative. The challenge is that Ottoman documents use multiple scripts (Naskh, Rik'a, Nastaʿlīq, Dīvānī, Sülüs, Siyakat, Karamanlidika, and Armeno-Turkish), each with distinct conventions and difficulties. The Historian's Desktop's three-stage HTR pipeline exists because no single HTR system produces reliable output across all these scripts — human verification at every stage is essential. Siyakat remains exceptionally difficult, and most HTR engines produce unreliable output for it.

**Technical detail:** HTR systems use machine learning models trained on paired images and transcriptions. Current approaches include Convolutional Recurrent Neural Networks (CRNNs) with Connectionist Temporal Classification (CTC), transformer-based architectures, and Visual Language Models (VLMs) used in a zero-shot or few-shot capacity. The Collaboratory's current pipeline uses Google's Gemini (a VLM) for initial transcription, producing structured JSON output, followed by Claude-based quality assurance. Traditional HTR platforms like Transkribus require training on script-specific datasets; VLMs can attempt transcription without script-specific training but with lower reliability.

---

### OCR (Optical Character Recognition)

**Plain English:** Technology that converts images of printed text into machine-readable text — the printed-text counterpart to HTR.

**Historian's context:** OCR works well for clearly printed modern text but struggles with historical documents — degraded paper, inconsistent typefaces, mixed scripts, and marginal annotations all reduce accuracy. For the Ottoman Archive project, OCR is relevant for printed documents like the Ottoman Government Gazette (Takvim-i Vekayi), while HTR handles the handwritten materials. Many digitised archival collections have been processed with OCR of varying quality, which affects the reliability of full-text search in digital repositories.

**Technical detail:** OCR engines include Tesseract (open source, supports many scripts), ABBYY FineReader (commercial, high accuracy for European scripts), and cloud-based services from Google, Microsoft, and Amazon. Modern OCR increasingly uses deep learning rather than traditional template matching. For Ottoman printed text, OCR must handle Arabic-script typography with connected letters, diacritical marks, and right-to-left reading order. Error rates vary significantly by print quality, script, and time period.

---

### Palaeography

**Plain English:** The study of historical handwriting — the discipline of reading, dating, and interpreting scripts from the past.

**Historian's context:** Palaeographic expertise is what the HTR pipeline's second stage draws on. When the palaeographic QA agent examines a transcription, it assesses whether specific letter forms, ligatures, and conventions have been correctly interpreted — work that traditionally requires years of training with specific scripts. Different Ottoman scripts have different palaeographic challenges: Siyakat uses highly abbreviated forms; Dīvānī uses decorative elongations; Karamanlidika uses Greek characters to write Turkish. The AI + History Collaboratory includes members with palaeographic expertise across several of these traditions.

**Technical detail:** Palaeographic analysis considers letter forms (ductus), abbreviation systems, scribal conventions, dating markers, and regional variations. In the HTR pipeline, palaeographic QA is encoded in the second subagent's system prompt, which includes script-specific guidance for all eight Ottoman script types. The agent flags readings that are graphically implausible — character sequences that no trained scribe would produce in the identified script. Script-specific skill files provide deeper palaeographic knowledge for individual scripts.

---

### Socratic methodology

**Plain English:** An approach to working with AI in which the historian asks questions and interrogates the AI's intentions at every stage — understanding the plan before accepting the output.

**Historian's context:** The Socratic methodology is the pedagogical backbone of History vibe coding. It has four stages: architecture (what are we building and why?), design (what components and how do they connect?), build plan (what is the sequence of construction?), and build and test (make it, then verify it works). At each stage, the historian questions Claude's proposals rather than accepting them passively. The methodology is tool-agnostic — it has been validated in Google AI Studio (Gemini) and Claude Cowork (Opus), and the same principles apply in any AI-assisted research context.

**Technical detail:** The four stages map to a structured conversation pattern: the historian states a goal, Claude proposes an approach, the historian interrogates the proposal (asking about alternatives, risks, assumptions, and trade-offs), and only after this dialogue does building begin. The methodology explicitly rejects "prompt and accept" workflows. It is encoded in the coaching process for History vibe coding rather than in a technical mechanism — it is a disciplined practice, not a software feature.

---

### History vibe coding

**Plain English:** Building working software tools by describing what you want in natural language and collaborating with an AI to produce it — without needing to write code yourself — applied specifically to historical research.

**Historian's context:** History vibe coding is the AI + History Collaboratory's coached programme in which historians build genuine research tools using Claude Cowork and related AI platforms. The name captures the collaborative, conversational nature of the process — you describe what you want, and Claude writes the code. But the Collaboratory's approach adds the Socratic methodology on top: you do not just describe and accept. You interrogate, refine, and verify. Six projects are documented in Colin Greenstreet's Generative Lives article (Colin Greenstreet, "History vibe coding: An offer to coach any and all historians wanting to give it a try", *Generative Lives*, 6 March 2026, https://generativelives.substack.com/p/history-vibe-coding), ranging from finding aid generators to research planners.

**Technical detail:** History vibe coding uses AI code generation (through Claude Cowork, Claude Code, or Google AI Studio) with the historian providing requirements, domain knowledge, and quality judgments. The separation between building (creating the tool in a sandbox) and publishing (pushing to GitHub) is deliberate — building is the learning experience; publishing is optional. The Socratic methodology ensures the historian understands what has been built, not just that it works. Tools built through History vibe coding include web applications (HTML/JavaScript), Python scripts, MCP servers, and skill files.

---

### VLM (Visual Language Model)

**Plain English:** An AI model that can process both images and text together — it can look at a document photograph and produce a transcription or description.

**Historian's context:** VLMs are what make the current HTR pipeline possible without training a custom model for each Ottoman script. Google's Gemini, used in the pipeline's first stage, is a VLM — it takes a document image as input and produces a structured transcription as output. The advantage is flexibility (it can attempt any script without specific training); the disadvantage is unreliability (it has no deep knowledge of specific palaeographic conventions). This is why the pipeline adds two further stages of quality assurance after the VLM's initial pass.

**Technical detail:** VLMs combine vision encoders (processing image data) with language models (generating text). Examples include Google Gemini, OpenAI GPT-4V/GPT-4o, and Anthropic Claude (which has vision capabilities). For HTR, VLMs operate in a zero-shot or few-shot mode — they attempt transcription based on general training rather than script-specific fine-tuning. Output quality varies significantly by script complexity, image quality, and prompt engineering. The Collaboratory's pipeline uses Gemini for initial transcription (producing annotated structured JSON) and Claude for subsequent quality assurance stages.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 9 March 2026 | Initial creation. Forty-one terms across six clusters. Three-layer structure (plain English, historian's context, technical detail). Draws on glossaries from the Cowork Setup Guide v2.0 and Subagents memo v1.0. |
| 1.1 | 9 March 2026 | Revisions from author review. Renamed "Vibe coding" to "History vibe coding" throughout; referenced Generative Lives article (6 March 2026) with six projects. Removed Plan9 entry. Added session introduction. Updated GitHub organisation entry to distinguish ai-and-history-collaboratory from ottoman-archive. Revised Historian's Desktop as research environment, removed workbench metaphor. Updated Claude Desktop subscription requirements (Pro, Max, Team, Enterprise). Updated Claude Code historian's context to position as advanced platform. Updated MCP connections list (added Old Bailey Online, three VRTI servers). Revised API/API key entry to note demonstration MCPs do not require keys. Broadened Human checkpoint beyond HTR example. Clarified Pipeline historian's context. Updated Sandbox with recommended path and folder structure guidance. Noted Annotation layering as HTR-specific. Changed Finding aid projects to "planned." Fixed HTML rendering bugs in companion file. Forty-six terms across six clusters. |
| 1.3 | 9 March 2026 | Search now auto-opens historian's context and technical detail layers when they contain the search term; layers collapse when search is cleared. |
| 1.2 | 9 March 2026 | Search highlighting added (matched terms highlighted in returned entries; dot indicator on unexpanded layers containing matches). Intro block font size increased. Collapsible cluster structure retained from v1.1. |
