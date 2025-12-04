# Session Lifecycle

> The complete flow from Initialize to End Session

---

## Overview

Every session follows a predictable lifecycle:

```
Initialize → Choose Focus → Load Context → Work → End Session
     │            │              │           │          │
     ▼            ▼              ▼           ▼          ▼
  Load T0    Recommend     Load T1      Execute    Save State
  Health     Priorities    Verify       Tasks      Summary
  Check                                            Next Steps
```

---

## Phase 1: Initialize

**Trigger:** User says "Initialize" or "Start session"

### Step 1: Load Tier 0

Read in order:
1. CLAUDE.md
2. Graph Index.md
3. Brain Dump Master.md
4. Today's Daily Note

### Step 2: Health Check

- Verify Graph Index freshness
- Count pending brain dump items
- Check for stale files
- Calculate health score

### Step 3: Run Safety Protocols

- Freshness Verification
- Blocker Validation
- Brain Dump Health Check

### Step 4: Display Business State

```
BUSINESS STATE

Stage: [Current] | Revenue: $X

CRITICAL PATH:
 [1] Current Step (X%)
 [2] Next Step
 [3] Goal

BLOCKERS: X active
Projects: X active | Y completed
```

### Step 5: Surface Priorities

```
WHAT NEEDS ATTENTION

FROM CRITICAL PATH: [Next step]
FROM TASKS: [Top 5]
FROM PREVIOUS SESSION: [Saved state]
FROM BRAIN DUMP: [Pending items]

RECOMMENDATION: [Suggested priority]

What's the focus?
```

### Output: User chooses direction

---

## Phase 2: Context Loading

**Trigger:** User chooses focus

### Step 1: Detect Task Type

Parse user's request for keywords:
- "pricing" → strategy
- "outreach" → sales
- "content" → marketing
- "admin" → operations

### Step 2: Load Tier 1 Files

Based on task type, load:
- Primary project files
- Dependencies
- Informing files
- Task-specific resources

### Step 3: Verify Load

```
SESSION CONFIGURED

Focus: [User's choice]
Task Type: [Detected]

Loading Tier 1:
 [x] File 1 (~Xk tokens)
 [x] File 2 (~Xk tokens)
 [x] File 3 (~Xk tokens)

CONTEXT: XX% used

Ready to work.
```

---

## Phase 3: Work Session

**The actual work happens here**

### During Work

- Execute tasks
- Capture decisions
- Update files as needed
- Track progress
- Challenge when appropriate

### Session Duration Awareness

**90 minutes:** Gentle reminder
**2 hours:** Suggest break
**3 hours:** Strong recommendation to pause

### Ongoing Tracking

- Progress logged
- Decisions captured
- Blockers updated
- Brain dump items added if they arise

---

## Phase 4: End Session

**Trigger:** User says "End session" or "Wrap up"

### Step 1: Capture Task State

If mid-task:
```yaml
Task: [Name]
Position: [Exact location]
Progress: X%
Next step: [What to do first]
Open questions: [List]
```

### Step 2: Update Files

- Mark todos complete
- Update project progress
- Add new brain dump items
- Document decisions made

### Step 3: Update Graph Index

- Status changes
- New blockers
- Resolved blockers
- New files created

### Step 4: Session Summary

```
SESSION ENDED

Duration: X hours
Tasks: [List worked on]
Progress: [Accomplishments]

SAVED STATE:
 - [Task]: [Position] (X%)

DECISIONS MADE:
 - [Decision 1]
 - [Decision 2]

FILES UPDATED:
 - [File 1]
 - [File 2]

NEXT SESSION:
 Resume: [Task]
 Priority: [Tomorrow's focus]

"Initialize" or "Resume [task]" to continue
```

---

## Quick Commands

| Command | Action |
|---------|--------|
| Initialize | Full boot sequence |
| Quick init | Abbreviated health check |
| Resume | Continue from saved state |
| Resume [task] | Load specific saved task |
| End session | Full close protocol |
| Quick close | Fast save without summary |

---

## Resume Protocol

**Trigger:** User says "Resume" or "Resume [task]"

### What Happens

1. Load Task-Context-Log
2. Find saved state
3. Load required Tier 1 files
4. Quick health check
5. Display resume point

```
RESUMING: [Task Name]

Position: [Exact location saved]
Progress: X%

Context loaded:
 [x] [File 1]
 [x] [File 2]

Next step: [Specific action]

Ready to continue?
```

---

## Error Handling

### Missing Daily Note
Auto-create from template, notify user

### Stale Graph Index
Warn, offer to update before proceeding

### Missing Required File
Alert, ask how to proceed

### Context Overflow
Warn, suggest reducing scope or archiving

---

## Session Patterns

### Deep Work Session
- Initialize
- Single focus (2-3 hours)
- End session with thorough summary

### Sprint Session
- Quick init
- Specific task (30-60 mins)
- Quick close

### Planning Session
- Initialize
- Multiple context loads
- Brain dump processing
- End session with next week's priorities

### Review Session
- Initialize
- Graph maintenance
- Archive processing
- Health improvements
