# PROJECT_OVERVIEW.md

## Purpose

**The Project Overview document** is a human-readable, public file that acts as the canonical source of project context for GPT. Its primary purpose is to enable ChatGPT to understand and persistently recall the full design scope of the ImperionWorld universe—including file structures, project goals, domain workflows, and architectural intent. It serves as the root reference for all future parsing, rule-following, and content creation in the project.

## 🎯 Project Goals

The ImperionWorld GPT integration is designed to support the following high-level creative tasks:

- **Create summaries by scene of stories I've already written**  
  - Automatically extract and link characters, events, and affiliations from each scene  
  - Generate structured XML output for inclusion in `ImperionSummaries.xml`

- **Track characters, locations, items, definitions, and events across many stories**  
  - Store these in a unified World Bible  
  - Export entries to `ImperionBible.xml`  
  - Dynamically retrieve only the relevant entries for a given task or scene  
  - Enable lightweight mobile access without manual reloading of files

- **Create character portraits for the most important and visible characters that define their psychology using MBTI/Enneagram systems**  
  - Store portraits in a dedicated cache and link them to World Bible entries  
  - Support simplified display views for referencing during writing

- **Use these tools to help ideate new characters, locations, and items**  
  - Leverage psychological models and existing affiliations for ideation  
  - Suggest new relationships and connections to existing world elements

- **Use all of this context to help create outlines for future stories**  
  - Apply the Seven Point Plot Structure and Story Grid frameworks  
  - Suggest arcs, beats, and structure consistent with established world and character logic

- **Use all of this context to expand outlines into lists of scenes**  
  - Generate ordered scene maps with POV, value shifts, and pacing guidance

- **Use all of this context to help create first drafts of these scenes**  
  - Maintain voice, motivation, and continuity from prior material  
  - Load relevant portraits or Bible entries during scene drafting


## 🏗 What We Have to Build (Component Map)

Each of these components supports one or more core system functions.

---

### 1. World Bible System
- `ImperionBible.xml` — primary data store for entries
- `03-worldBibleEntries.md` — rules for formatting and relationships
- XML schema (in `/schema/`) — defines valid structure
- Entry generator — turns raw data into XML blocks
- Entry loader/parser — used to look up or cross-reference entries

---

### 2. Scene Summary System
- `ImperionSummaries.xml` — structured summaries by scene
- `02-storySummaries.md` — rules for defining, expanding, and tagging scenes
- Schema for summaries — with scenePov, sceneSummary, continuityNotes, wordCount, etc.
- Scene parser — identifies characters/events and formats output

---

### 3. Character Portrait System
- `portraitCache.md` — stores full Portraits for key characters
- `08-characterPortraits.md` — rules for MBTI, Enneagram, layout, and linking
- Linkage layer — adds portrait references to Bible entries
- Portrait view renderer — simplified display for writing context

---

### 4. Outline and Structure System
- `04-structuringStories.md` — rules for Seven Point and Story Grid outlines
- Scene expander — turns outline points into scene lists
- Structure tracker — ensures arcs and values evolve across beats

---

### 5. Drafting Support Tools
- `05-writingStories.md` — rules for turning scene plans into prose
- Context integrator — auto-loads relevant Bible/Portrait elements
- Drafting assistant — preserves voice,

## 📁 File & Folder Structure

This section documents where each type of file lives across the three core locations used by the ImperionWorld project:

- `📁 GPT Project` — Loaded directly into ChatGPT via project file uploads  
- `🌐 Public GitHub Repo` — Contains general-purpose rules and non-spoiler docs  
- `🔒 Private GitHub Repo` — Contains proprietary story content, structured data, and working files  

---

### 🔒 Private GitHub Repo — `ImperionWorld/`

This is the main working repository for all structured content, entries, portraits, summaries, and merge scripts.

```
ImperionWorld/
│
├── loader.yaml                       # Tells GPT where to look for public context (e.g. PROJECT_OVERVIEW.md)
├── rulesManifest.md                  # Index of all rule files and their purposes for GPT to load as needed
│
├── RulesManifest/                    # All project-wide rule files (Markdown or YAML)
│   ├── 01-howToMakeRules.md          # Guidelines for writing and formatting rule files
│   ├── 02-storySummaries.md          # Rules for summarizing scenes, POV structure, and continuity notes
│   ├── 03-worldBibleEntries.md       # Formatting, linking, and versioning rules for Bible entries
│   ├── 04-structuringStories.md      # Seven Point / Story Grid outlining conventions
│   ├── 05-writingStories.md          # Converting scene plans into prose with correct tone and continuity
│   ├── 06-editingStories.md          # How GPT helps edit and revise prose using rules
│   ├── 07-creatingAssets.md                     # Rules for generating maps, icons, diagrams, etc.
│   ├── 08-characterPortraits.md                 # Structure for personality portraits and linking to Bible
│   └── 09-loaderRules.yaml                      # Optional YAML that defines dynamic loader logic
│
├── WorldBible/                                  # Canonical World Bible data system
│   ├── ImperionBible.xml                        # Full merged World Bible (one entry per element)
│   └── entries/                                 # Individual entry files (XML format)
│       └── char-Gaius.xml                       # Example: a single character entry for Gaius
│
├── Story Summaries/                             # Parsed scene summaries and story metadata
│   ├── ImperionSummaries.xml                    # Merged master file for all summarized scenes
│   └── Stories/                                 # Folder for individual stories
│       └── The Admiral's Vengeance/
│           ├── TheAdmiralsVengeance.xml         # Metadata for this story (title, filePrefix, etc.)
│           └── Chapters/
│               └── TheAdmiralsVengeance-Ch00.xml # Individual chapter summaries
│
├── CharacterPortraits/                          # Portrait system for psychologically rich characters
│   ├── portraitCache.md                         # Single GPT-readable cache file (used during sessions)
│   └── portraits/                               # One markdown file per character (not loaded all at once)
│       └── Aurelia-Cyclorios.md                 # Full portrait: background, MBTI/Enneagram, key arcs
│
├── schema/                                      # Schemas to validate structure of XML/YAML files
│   ├── worldBible.schema.yaml                   # Declares fields and types used in World Bible entries
│   ├── sceneSummary.schema.yaml                 # Declares structure for scene summaries
│   └── characterPortrait.schema.yaml            # Field-level design for character portraits
│
├── scripts/                                     # Node.js (or other) utilities to automate file merging
│   ├── mergeBible.js                            # Merges all Bible entry files into ImperionBible.xml
│   ├── mergeSummaries.js                        # Merges all chapter summaries into ImperionSummaries.xml
│   └── mergePortraits.js                        # Merges all portrait files into portraitCache.md
│
└── Assets/                                      # Original source material and non-generated assets
    ├── Manuscripts/                             # Drafts of full stories (as DOCX or TXT)
    │   └── The Admiral's Vengeance-v1.5.docx
    ├── Maps/                                    # World maps, planetary charts, regional layouts
    └── Ephemera/                                # Lore fragments, handouts, inspiration docs
```

## 🧭 ImperionWorld Project Design Workflow (Temporary Section)

This section outlines the phased project design plan for the ImperionWorld GPT integration. It will be removed once the project structure is fully implemented.

---

### ✅ Phase 1: Foundation Lock-In (This Week)
Define structure, purpose, and rules without diving into content yet.

#### 🔹 Step 1 — Finalize `PROJECT_OVERVIEW.md`
- Add: project goals, component map, what's in/out of scope  
- Include: link to loader, file responsibilities, repo layout  
- Confirm: any other domains (e.g. music, fitness) don’t conflict

#### 🔹 Step 2 — Build Rules Manifest and File Stubs
- Create `rulesManifest.md` listing all rule files planned  
- Set up empty stubs (e.g. `08-characterPortraits.md`, `09-loaderRules.yaml`)  
- Load only as needed in GPT until active

#### 🔹 Step 3 — Sketch YAML Schemas (lightweight)
- Define schema outlines for:
  - World Bible entries
  - Scene summaries
  - Character portraits
- Keep it declarative—just field names, types, relationships

---

### 🧠 Phase 2: System Design per Domain (Next 2–3 Weeks)
Define rules and flows for one domain at a time—fully modular.

#### 🔹 Example Order:
1. Character Portraits  
2. World Bible entries  
3. Scene summary & structure  
4. Voice presets & tone rules  
5. Asset generation (maps, symbols)

Each gets its own:
- Rule file
- YAML schema (if needed)
- Markdown documentation block

---

### 🛠 Phase 3: Test & Populate (Rolling Forward)
Start feeding content into the system once each domain is stable.

- Begin populating `ImperionBible.xml` with actual entries  
- Summarize real scenes and build your `ImperionSummaries.xml`  
- Generate Portraits into `portraitCache.md` as tested  
- Sync often with private repo for long-term archival

---

### 🔁 Maintenance Loop (Ongoing)
- Use the `loader.yaml`, `PROJECT_OVERVIEW.md`, and `rulesManifest.md` as your durable memory system  
- Update rule files only when workflows change  
- Use GitHub commits and versioning to control schema drift

*Generated on 2025-05-04*


