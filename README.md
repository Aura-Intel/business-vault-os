# Business Vault OS

> A knowledge graph architecture for Obsidian + Claude Code that transforms your vault into an intelligent business operating system.

---

## What This Is

Business Vault OS is a complete blueprint for building an AI-assisted business management system using:
- **Obsidian** (markdown-based knowledge management)
- **Claude Code** (AI assistant with file access)
- **Knowledge graph architecture** (relationships between all information)
- **Safety protocols** (preventing AI from giving stale/wrong advice)

**Result:** Type "Initialize" and get your complete business state in 30 seconds. Claude becomes your external brain that actually understands your business context.

---

## Who This Is For

- Solo founders / consultants managing complex businesses
- Anyone using Obsidian who wants AI that understands their vault
- Claude Code users who want structured, reliable AI assistance
- People tired of re-explaining context to AI every session

**You should have:**
- Basic familiarity with Obsidian (markdown, folders, wikilinks)
- Access to Claude Code (or similar AI with file access)
- Willingness to spend 2-4 hours on initial setup

---

## What's Included

```
business-vault-os/
├── /architecture/     # Deep documentation on how the system works
├── /templates/        # Blank templates for immediate use
├── /examples/         # Fictional example vault (Acme Consulting)
├── /guides/           # How-to guides for customization
├── /opus-prompts/     # Prompts for designing with Opus 4.5
└── /vault-starter/    # Minimal starter vault (clone and go)
```

**Two ways to use this:**

1. **Quick Start:** Clone `/vault-starter/` and customize CLAUDE.md for your business
2. **Deep Understanding:** Read `/architecture/`, study `/examples/`, then build your own

---

## Core Concepts (5-Minute Overview)

### 1. Knowledge Graph Architecture

Every file in your vault has YAML frontmatter that defines:
- **Identity:** What type of file, when created, status
- **Relationships:** What it depends on, what it blocks, what it informs
- **Context:** When this file should be loaded for AI conversations

This creates a queryable map of your entire business.

### 2. Context Tier System

Files are organized into tiers based on when they should be loaded:

| Tier | Purpose | When Loaded | Example |
|------|---------|-------------|---------|
| 0 | Identity | Every session | CLAUDE.md, Founder Background |
| 1 | Task-specific | For relevant work | Niche Analysis files, Project files |
| 2 | Reference | On demand | Transcripts, detailed guides |
| 3 | Archive | Rarely | Completed projects, old notes |

This prevents context window bloat while ensuring Claude has what it needs.

### 3. Session Lifecycle

**Initialize:** Claude reads core context, checks graph freshness, surfaces priorities
**Active:** Claude tracks token usage, warns at thresholds, maintains state
**End:** Claude saves task state, documents progress, sets next session priority

### 4. Safety Protocols

Built-in protections against common AI failure modes:
- **Freshness Verification:** Prevents recommendations based on stale state
- **Blocker Validation:** Catches phantom blockers (resolved but not updated)
- **Truth-First Protocol:** Forces evidence-based responses, quote-back verification

### 5. AI Security (Prompt Injection Defense)

If you're building AI workflows that process external data (web scraping, APIs, user input), you need security layers to prevent prompt injection attacks.

**[Read the AI Security Protocol →](guides/ai-security-protocol.md)**

Includes:
- 5-layer defense framework
- Copy-paste JavaScript sanitization functions
- Secure prompt templates
- Output validation patterns
- Quality gates checklist

---

## Quick Start Guide

### Prerequisites

- [ ] Obsidian installed and working
- [ ] Claude Code access (or Claude with file access capability)
- [ ] 2-4 hours for initial setup

### Step 1: Clone the Starter Vault (5 minutes)

1. Copy the entire `/vault-starter/` directory to your preferred location
2. Open it as a new vault in Obsidian
3. Verify folder structure: `00-System/`, `01-Daily/`, `02-Projects/`, etc.

### Step 2: Customize CLAUDE.md (30-60 minutes)

Open `CLAUDE.md` and fill in:

**Business Overview:**
- Your business name and website
- Mission/vision/values
- Business model and target market
- Current stage (ideation/validation/launch/growth)

**Working Preferences:**
- Communication style
- Decision-making approach
- Daily energy patterns
- Professional background

**Current Context:**
- Active projects
- Key blockers
- First/next major goal

**Tip:** Be thorough here. This is what makes Claude actually useful. Generic context = generic advice.

### Step 3: Set Up Graph Index (15-30 minutes)

1. Open `00-System/Graph Index.md`
2. Add your current projects to "Files by Type" section
3. Map any dependencies (what blocks what?)
4. Identify your critical path to main goal

**Start simple:** You can add complexity later. Just get the main projects and their dependencies.

### Step 4: Populate Brain Dump (15 minutes)

1. Open `00-System/Brain Dump Master.md`
2. Do a 10-minute brain dump of everything on your mind
3. Categorize items: Worries, Ideas, Tasks, Questions
4. This becomes Claude's window into your mental state

### Step 5: Test Initialize (5 minutes)

Start a Claude Code session in your vault and type: `Initialize`

**Expected behavior:**
- Claude reads Tier 0 files (CLAUDE.md, Graph Index, etc.)
- Displays business state summary
- Shows current blockers and critical path
- Recommends THE ONE THING for today

**If this works:** You're set up! Start using the system.

**If this doesn't work:** Check SETUP-GUIDE.md for troubleshooting.

---

## Verification Checklist

Use this to confirm each feature works:

### Core Features

- [ ] **Initialize loads context:** Claude reads files and displays verification
- [ ] **Blocker surfacing works:** Claude identifies what's blocked and why
- [ ] **Critical path shows:** Claude can explain path to your goal
- [ ] **Task switching tracked:** Context saved when switching between tasks
- [ ] **Session end captures state:** Progress documented at session end

### Safety Protocols

- [ ] **Freshness check triggers:** Claude warns if Graph Index is stale
- [ ] **Blocker validation runs:** Claude verifies blockers before surfacing
- [ ] **Truth-First enforcement:** Claude cites sources, admits uncertainty

### Quality of Life

- [ ] **Token warnings appear:** Claude warns at 60%/75%/90% context usage
- [ ] **Daily note auto-creates:** Template used when today's note missing
- [ ] **Brain Dump processing:** Items get routed to proper locations

---

## Adapting for Your Business

This system is designed to be customized. See `/guides/adapting-for-your-business.md` for:

- Changing file types for your domain
- Modifying relationship types
- Adjusting safety protocol thresholds
- Creating domain-specific task types

---

## Building Your Own with Opus

The `/opus-prompts/` directory contains prompts for designing this system with Claude Opus 4.5.

**Why Opus?** Complex system design benefits from larger context windows and stronger reasoning. Opus designed the architecture; Sonnet implements it daily.

**Workflow:**
1. Use Opus for architecture design and major protocol creation
2. Use Sonnet (or Claude Code default) for daily operation
3. Iterate based on real usage

---

## Credits

Built by a founder going through the same journey. Inspired by the Obsidian + Claude Code approach.

This is a blueprint, not a finished product. Your implementation will evolve through use.

---

## License

MIT License - Use freely, modify as needed, no attribution required.
