# PROJECT_OVERVIEW.md

## Purpose

**The Project Overview document** is a human-readable, public file that acts as the canonical source of project context for GPT. Its primary purpose is to enable ChatGPT to understand and persistently recall the full design scope of the ImperionWorld universe—including file structures, project goals, domain workflows, and architectural intent. It serves as the root reference for all future parsing, rule-following, and content creation in the project.

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


