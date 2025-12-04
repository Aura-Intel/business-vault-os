# Getting Started

> Your first session with Business Vault OS

---

## Before You Begin

### Requirements

1. **Obsidian** - Free markdown editor (obsidian.md)
2. **Claude Code** - AI assistant with file access (or Claude with file upload)
3. **30 minutes** - For initial setup

### Mindset

This system works best when you:
- Are honest about your business state
- Commit to the session protocols
- Trust the prioritization process
- Update files as things change

---

## Step 1: Set Up Your Vault (10 mins)

### Option A: Clone the Starter

```bash
git clone https://github.com/[repo]/business-vault-os
cd business-vault-os
cp -r vault-starter my-vault
```

### Option B: Manual Setup

Create this folder structure:
```
my-vault/
├── CLAUDE.md
├── 00-System/
│   ├── Graph-Index.md
│   └── Brain-Dump-Master.md
├── 01-Daily/
├── 02-Projects/
├── 03-Learning/
├── 04-Tasks/
│   └── Tasks-Backlog.md
└── 05-Archive/
```

---

## Step 2: Customize CLAUDE.md (15 mins)

Open `CLAUDE.md` and fill in:

### Business Identity
```markdown
### Company Name
**[Your actual business name]**

### Mission
[What you do and for whom]

### Target Market
[Who you serve]

### Current Stage
[Where you are: ideation/validation/launch/growth]
```

### Your Working Style
```markdown
### Communication Style
[How you like to work: direct/detailed/collaborative]

### Best Work Hours
- Peak focus: [Your peak hours]
- Low energy: [When you crash]

### Challenges
[What you struggle with]
```

### Your Goal
```markdown
### Primary Goal
[The ONE thing you're focused on]
```

---

## Step 3: Initialize Your First Session

Open Claude Code in your vault directory, then say:

```
Initialize
```

### What Should Happen

1. Claude reads your CLAUDE.md
2. Creates today's daily note (if missing)
3. Shows business state summary
4. Asks what you want to focus on

### Expected Output

```
INITIALIZED

TIER 0: 4/4 loaded
CONTEXT: 15% used

BUSINESS STATE:
Stage: [Your stage]
Goal: [Your goal]
Blockers: None yet

Ready to work. What's the focus?
```

---

## Step 4: Your First Work Session

### Tell Claude Your Focus

Example:
```
Let's define my service packages
```

### Claude Will:
1. Create a project file (if needed)
2. Load relevant context
3. Start helping you work

### As You Work

- Claude tracks progress
- Decisions get documented
- Blockers get flagged
- Brain dump catches stray thoughts

---

## Step 5: End Your Session

When done, say:

```
End session
```

### Claude Will:
1. Save your current position
2. Update files with progress
3. Set tomorrow's priority
4. Show summary

### Expected Output

```
SESSION ENDED

Duration: 1.5 hours
Worked on: Service Packages
Progress: 50% complete

SAVED STATE:
 - Service Packages: Tier definitions (50%)

NEXT SESSION:
 Resume: Service Packages
 Next step: Define deliverables per tier
```

---

## Common First-Session Questions

### "It didn't create a daily note"

Make sure your vault has the `01-Daily/` folder. Claude creates notes there.

### "The context verification looks wrong"

Your CLAUDE.md might be missing required sections. Compare with the template.

### "Claude didn't understand Initialize"

Make sure CLAUDE.md is in your vault root and contains the Session Initialization Protocol section.

### "How do I know it's working?"

Look for:
- Context verification display
- Business state summary
- Priority recommendations
- Session end summaries

---

## Next Steps

1. **Complete your first week** → See [first-week.md](first-week.md)
2. **Learn the daily rhythm** → See [daily-workflow.md](daily-workflow.md)
3. **Handle overwhelm** → See [brain-dump-guide.md](brain-dump-guide.md)

---

## Quick Reference

| Command | What it does |
|---------|--------------|
| Initialize | Start session, load context |
| End session | Save state, show summary |
| Resume | Continue from last position |
| Brain dump | Capture overwhelming thoughts |
