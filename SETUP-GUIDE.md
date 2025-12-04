# Business Vault OS - Setup Guide

> Detailed step-by-step setup instructions for getting Business Vault OS running in your vault.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Installation Options](#installation-options)
3. [Option A: Clone Starter Vault](#option-a-clone-starter-vault)
4. [Option B: Add to Existing Vault](#option-b-add-to-existing-vault)
5. [Essential Configuration](#essential-configuration)
6. [Testing Your Setup](#testing-your-setup)
7. [Common Setup Issues](#common-setup-issues)
8. [Next Steps](#next-steps)

---

## Prerequisites

### Required

- [ ] **Obsidian** installed (any recent version)
- [ ] **Claude Code** or Claude with file system access
- [ ] **2-4 hours** for initial setup (less for minimal setup)

### Recommended

- [ ] Basic familiarity with YAML frontmatter
- [ ] Understanding of wikilinks `[[like this]]`
- [ ] Clear idea of your current business/project goal

---

## Installation Options

Choose your approach:

| Option | Best For | Time Required | Complexity |
|--------|----------|---------------|------------|
| **A: Clone Starter** | New vault, clean start | 1-2 hours | Low |
| **B: Add to Existing** | Have content to preserve | 2-4 hours | Medium |

---

## Option A: Clone Starter Vault

### Step 1: Copy the Starter

1. Locate `/vault-starter/` in this repository
2. Copy the entire directory to your preferred location
3. Rename the folder to your business/project name

**Example:**
```
/vault-starter/  -->  /MyBusiness-Vault/
```

### Step 2: Open in Obsidian

1. Open Obsidian
2. Click "Open folder as vault"
3. Select your copied directory
4. Trust the vault when prompted

### Step 3: Verify Structure

Your vault should have:
```
MyBusiness-Vault/
├── CLAUDE.md
├── 00-System/
│   ├── Graph Index.md
│   ├── Brain Dump Master.md
│   ├── Daily Note Template.md
│   └── User Rules - Quick Reference.md
├── 01-Daily/
├── 02-Projects/
├── 03-Learning/
└── 04-Tasks/
```

**If anything is missing:** Re-copy from `/vault-starter/`

### Step 4: Proceed to Essential Configuration

Jump to [Essential Configuration](#essential-configuration) below.

---

## Option B: Add to Existing Vault

### Step 1: Create System Folder

1. Create `00-System/` folder in your vault root
2. This will hold all system files

### Step 2: Add Core Files

Copy these files from `/templates/` to your `00-System/`:
- `graph-index-template.md` (rename to `Graph Index.md`)
- `brain-dump-template.md` (rename to `Brain Dump Master.md`)
- `daily-note-template.md` (rename to `Daily Note Template.md`)

### Step 3: Create CLAUDE.md

1. Copy `CLAUDE-TEMPLATE.md` from `/templates/` to your vault root
2. Rename to `CLAUDE.md`

### Step 4: Organize Existing Content

Create folders if they don't exist:
- `01-Daily/` - Daily notes
- `02-Projects/` - Project files
- `03-Learning/` - Learning content
- `04-Tasks/` - Task files

**Optional:** Move existing files to appropriate folders.

### Step 5: Add Frontmatter to Existing Files

For files you want in the knowledge graph, add YAML frontmatter.

**Minimum frontmatter:**
```yaml
---
file_type: project
file_id: unique-kebab-case-name
title: Your File Title
created: 2025-01-15
updated: 2025-01-15
status: active
context_tier: 1
---
```

**Full frontmatter (for important files):**
See `/templates/graph-metadata-schema-template.md`

---

## Essential Configuration

### Configure CLAUDE.md (CRITICAL)

This is the most important step. Open `CLAUDE.md` and fill in every section.

#### Section 1: Business Overview

```markdown
## Business Overview

### Company/Project Name
**[Your Business Name]** (website if applicable)

### Mission Statement
[One sentence: What you're trying to accomplish]

### Current Stage
- [ ] Ideation
- [x] Validation  <-- Mark your current stage
- [ ] Launch
- [ ] Growth

### Primary Goal
[What's your next major milestone? Be specific.]
```

#### Section 2: Working Preferences

```markdown
## Working Preferences

### Communication Style
[Direct? Detailed? Encouraging? Challenging?]

### Decision-Making Approach
[What's your framework? ROI-focused? Speed-first? Risk-averse?]

### Daily Energy Patterns
[When are you most productive? When do you crash?]
```

#### Section 3: Current Context

```markdown
## Current Focus

### Active Projects
1. [Project 1] - Status: [status]
2. [Project 2] - Status: [status]

### Current Blockers
- [What's blocking progress right now?]

### Key Resources
- [Important links, contacts, tools]
```

**Tip:** The more specific you are, the better Claude performs. Vague context = generic advice.

### Configure Graph Index

Open `00-System/Graph Index.md`:

1. **Update Quick Stats** with your actual file counts
2. **Add your projects** to "Files by Type"
3. **Map dependencies** - What blocks what?
4. **Identify critical path** - What's the sequence to your goal?

**Example:**
```markdown
## Critical Path to [Your Goal]

1. [CURRENT] Define target customer
   ↓ unlocks
2. [BLOCKED] Create service offerings
   ↓ unlocks
3. [BLOCKED] Set pricing
   ↓ enables
4. [GOAL] First paying customer
```

### Configure Brain Dump

Open `00-System/Brain Dump Master.md`:

1. Do a 10-minute unfiltered brain dump
2. List everything on your mind about your business/project
3. Categorize roughly (Worries, Ideas, Tasks, Questions)
4. Don't overthink - this is meant to be messy

---

## Testing Your Setup

### Test 1: Basic Initialize

Start Claude Code in your vault directory.

**Type:** `Initialize`

**Expected Response:**
- Claude reads and confirms loading CLAUDE.md
- Claude reads Graph Index
- Claude displays business state summary
- Claude recommends priority for today

**If this works:** Basic setup complete.

**If this fails:**
- Check CLAUDE.md exists in vault root
- Check file permissions
- See [Common Setup Issues](#common-setup-issues)

### Test 2: Context Verification

**Type:** `Context status`

**Expected Response:**
- Shows what files are loaded
- Shows token usage estimate
- Shows tier breakdown

### Test 3: Blocker Query

**Type:** `What's blocking me?`

**Expected Response:**
- Lists blockers from Graph Index
- Shows downstream impact
- Recommends next action

### Test 4: Session End

**Type:** `End session`

**Expected Response:**
- Captures session summary
- Documents progress made
- Sets priority for next session

---

## Common Setup Issues

### Issue: Claude doesn't recognize Initialize command

**Cause:** CLAUDE.md not being read or formatted incorrectly.

**Solution:**
1. Verify CLAUDE.md is in vault root (not in a subfolder)
2. Check YAML frontmatter is valid (no syntax errors)
3. Ensure file encoding is UTF-8

### Issue: Graph Index not loading

**Cause:** File path mismatch or missing file.

**Solution:**
1. Verify file is at `00-System/Graph Index.md`
2. Check wikilinks in CLAUDE.md point to correct path
3. Verify file has valid frontmatter

### Issue: Token warnings not appearing

**Cause:** Session Management Protocol not configured.

**Solution:**
1. This is a nice-to-have, not critical
2. Add Session Management Protocol from templates if wanted
3. System works without it (just no warnings)

### Issue: Daily note not auto-creating

**Cause:** Template not in correct location.

**Solution:**
1. Verify `Daily Note Template.md` exists in `00-System/`
2. Check template has correct structure
3. This feature requires explicit support in CLAUDE.md Initialize section

---

## Next Steps

Once setup is complete:

1. **Use it daily** - The system improves with use
2. **Iterate on CLAUDE.md** - Update as your business evolves
3. **Add files to graph** - More files = smarter system
4. **Read `/architecture/`** - Deeper understanding helps customization

---

## Getting Help

If you're stuck:
1. Check `/guides/troubleshooting-common-issues.md`
2. Review the `/examples/` Acme vault for reference
3. Re-read architecture docs for conceptual clarity

The system is designed to be self-documenting once basics are working.
