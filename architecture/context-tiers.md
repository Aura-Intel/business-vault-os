# Context Tier System

> Loading the right information at the right time

---

## The Problem

Claude has a limited context window. Loading your entire vault would:
- Waste context on irrelevant files
- Leave no room for actual work
- Slow down responses
- Dilute focus

**Solution:** Tiered context loading.

---

## The Four Tiers

### Tier 0: Always Load
**What:** Identity and system files
**When:** Every single session
**Size:** ~15-20k tokens

Files in Tier 0:
- `CLAUDE.md` - Business identity and operating instructions
- `Graph Index.md` - Relationship map and blockers
- `Brain Dump Master.md` - Current mental state
- Today's Daily Note - Today's plan and captures

**Why always?** These files define WHO you are and WHAT state the business is in. Without them, Claude lacks context to help effectively.

---

### Tier 1: Task-Specific
**What:** Project files, task lists, active work
**When:** After you choose a focus
**Size:** ~30-50k tokens

Examples:
- Project files for today's work
- Tasks-Backlog.md
- Relevant learning files
- Dependencies of current work

**How it works:**
1. You say: "Working on Pricing Strategy"
2. Claude loads:
   - Pricing-Strategy.md
   - Service-Packages.md (dependency)
   - Competitor-Research.md (informs)

---

### Tier 2: Reference
**What:** Supporting information, research, historical
**When:** On-demand when needed
**Size:** Variable

Examples:
- Completed research
- Industry analysis
- Old meeting notes
- Reference templates

**When loaded:**
- You explicitly request
- Claude needs to answer a question
- Making a decision that requires reference

---

### Tier 3: Archive
**What:** Completed work, old projects, historical
**When:** Never (unless specifically requested)
**Size:** N/A

Examples:
- Completed projects
- Old daily notes
- Superseded strategies
- Historical records

**Why keep?**
- Legal/audit trail
- Pattern analysis over time
- Reference for similar future work

---

## Context Budget Management

### Typical Session Budget

```
Total Available:        ~200k tokens
─────────────────────────────────────
Tier 0 (Identity):      ~15k (8%)
Tier 1 (Task):          ~35k (18%)
Working Space:          ~100k (50%)
Safety Buffer:          ~50k (25%)
```

**Target:** Stay under 50% to leave room for work.

### Monitoring

During Initialize, Claude displays:
```
CONTEXT STATUS: [====------] 25% (~50k/200k)
```

If approaching limits:
```
⚠️ CONTEXT WARNING: 75% used
Consider archiving or reducing Tier 1 scope
```

---

## How Tiers are Assigned

### In File Frontmatter

```yaml
---
context_tier: 1  # 0, 1, 2, or 3
---
```

### Assignment Guidelines

| File Type | Default Tier | Override When |
|-----------|--------------|---------------|
| CLAUDE.md | 0 | Never |
| Graph Index | 0 | Never |
| Brain Dump | 0 | Never |
| Daily Note (today) | 0 | Never |
| Active Projects | 1 | Tier 2 if paused |
| Tasks-Backlog | 1 | Never |
| Completed Projects | 2 | Tier 3 after 90 days |
| Research/Learning | 2 | Tier 1 if actively using |
| Old Daily Notes | 3 | Tier 2 if referencing |

---

## Task-Type Loading

Different tasks need different context. The system maps task types to required files:

| Task Type | Tier 1 Files Loaded |
|-----------|---------------------|
| Strategy work | Strategy files, research, constraints |
| Client outreach | Lead list, templates, messaging |
| Content creation | Content strategy, past posts, analytics |
| Admin | Admin files, compliance docs |

### Detection

Claude detects task type from your request:

"Let's work on pricing" → Strategy task → Load strategy files
"Need to follow up with leads" → Sales task → Load lead files

---

## Manual Override

You can always override:

**Load specific file:**
"Also load the Competitor Analysis"

**Unload file:**
"Don't need the Research file for this"

**Force tier:**
"Load the archive of Project X"

---

## Best Practices

### Do
- Keep Tier 0 lean (identity only)
- Be specific about today's focus
- Archive completed work
- Review tier assignments monthly

### Don't
- Put everything in Tier 0
- Load "just in case" files
- Keep completed projects in Tier 1
- Ignore context warnings

---

## Tier Transition Rules

### Promoting (Tier 2 → Tier 1)
When a reference file becomes active work:
1. Update `context_tier: 1` in frontmatter
2. Add to Graph Index Tier 1 registry
3. Update related files if needed

### Demoting (Tier 1 → Tier 2)
When active work becomes reference:
1. Update `context_tier: 2` in frontmatter
2. Move in Graph Index registry
3. Ensure no active dependencies

### Archiving (Any → Tier 3)
When work is truly complete:
1. Update `context_tier: 3`
2. Move to Archive folder
3. Update Graph Index
4. Clear from blockers list
