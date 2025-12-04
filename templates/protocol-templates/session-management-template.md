# Session Management Protocol Template

> **Purpose:** Structured start/end workflows ensuring nothing is lost between sessions
> **Implementation:** Reference in master context, run automatically during Initialize

---

## Overview

Every session has a beginning and an end. Without structured protocols, context is lost, progress isn't captured, and next session starts from scratch. This protocol fixes that.

---

## SESSION START PROTOCOL

### Trigger
User says: "Initialize" or "Start session" or "Load context"

### Boot Sequence (6 Steps)

**Step 1: System Health Check (30 seconds)**
```
- Capture current date/time from system
- Check Graph Index staleness (when was it last updated?)
- Count pending items in Brain Dump
- Verify critical files exist
- Calculate system health score
```

**Step 2: Load Tier 0 Context**
```
Read in order (mandatory):
1. Master context file (CLAUDE.md equivalent)
2. Graph Index (relationship map)
3. Brain Dump / Inbox (current mental state)
4. Task Context Log (saved positions)
5. Core protocols (operating rules)
```

**Step 3: Display Context Verification**
```
Show user what was loaded:

CONTEXT LOADED:
 [x] Master Context (~3,500 tokens)
 [x] Graph Index (~2,200 tokens)
 [x] Brain Dump (~1,800 tokens)
 [x] Task Log (~800 tokens)

CONTEXT STATUS: [====------] 18% used
```

**Step 4: Run Graph Intelligence Queries**
```
Automatically query:
- Active blockers (what's stuck?)
- Critical path status (where are we?)
- Quick wins (what's almost done?)
- Stale files (what needs attention?)
```

**Step 5: Check for Saved Task State**
```
If task was saved mid-progress last session:
- Display: "Previous session: [Task] @ [Position] ([X]% complete)"
- Ask: "Resume or different focus?"
```

**Step 6: Surface Priority Recommendation**
```
Based on graph analysis, recommend:
- THE ONE THING for today
- Why this matters (what it unlocks)
- Ask user to confirm or redirect
```

### Initialize Output Format

```
═══════════════════════════════════════════════════
INITIALIZED
═══════════════════════════════════════════════════

CONTEXT: [====------] 18% | Tier 0 loaded

CRITICAL PATH: [Current step] → [Next step] → [Goal]
BLOCKERS: [Count] active
QUICK WINS: [Count] items near completion

PREVIOUS SESSION: [Task name] @ [Position]

RECOMMENDATION:
→ [Priority task]
→ Why: [What this unlocks]

What's the focus today?
═══════════════════════════════════════════════════
```

---

## SESSION END PROTOCOL

### Trigger
User says: "End session" or "Wrap up" or "Done for today"

### Close Sequence (7 Steps)

**Step 1: Capture Task State (if mid-task)**
```yaml
Save to Task Context Log:
  task_name: [Current task]
  position: [Exact position - file, section, item]
  progress: [X]%
  last_action: [What was just completed]
  next_action: [What to do next]
  open_questions: [Unresolved items]
```

**Step 2: Update Vault Files**
```
- Mark completed tasks as done
- Update project files with progress
- Add new items to Brain Dump if emerged
- Update Graph Index if relationships changed
```

**Step 3: Log Session Summary**
```yaml
Session Log Entry:
  date: [Today]
  duration: [X hours]
  tasks_worked: [List]
  files_created: [List]
  files_modified: [List]
  decisions_made: [List]
  blockers_changed: [Resolved/New]
```

**Step 4: Set Tomorrow's Priority**
```
Based on today's progress:
- What's the ONE THING for next session?
- Why does this matter?
- What files will be needed?
```

**Step 5: Display Session Summary**
```
═══════════════════════════════════════════════════
SESSION ENDED
═══════════════════════════════════════════════════

DURATION: [X] hours

COMPLETED:
 - [Task 1]
 - [Task 2]

SAVED STATE:
 - [Task in progress]: [Position] ([X]% complete)

DECISIONS MADE:
 - [Decision 1]
 - [Decision 2]

FILES UPDATED:
 - [File 1]
 - [File 2]

═══════════════════════════════════════════════════
NEXT SESSION
═══════════════════════════════════════════════════

RESUME: [Task name]
 Position: [Exact location]
 Next action: [Specific step]

PRIORITY: [Tomorrow's ONE THING]

QUICK COMMAND: "Initialize" or "Resume [task]"
═══════════════════════════════════════════════════
```

**Step 6: Verify Graph Index Updated**
```
If files were created/modified:
- Confirm Graph Index reflects changes
- Show proof: "Graph Index updated: [X] files added"
```

**Step 7: Confirm Save**
```
"All progress saved. See you next session."
```

---

## RESUME COMMAND

### Trigger
User says: "Resume" or "Resume [task name]"

### Quick Start Sequence

```
RESUMING: [Task name]
═══════════════════════════════════════════════════

Position: [Exact saved position]
Progress: [X]% complete
Last action: [What was done]

LOADING CONTEXT:
 [x] Task-specific files
 [x] Required context from metadata

NEXT STEP:
→ [Specific next action]

Ready to continue. Proceed?
═══════════════════════════════════════════════════
```

---

## Task Context Log Structure

Create this file to persist task state:

```yaml
# Task Context Log

## Active Tasks

### Task: [Name]

task_id: [unique-id]
task_type: [type]
parent_project: [Project name]
files_involved:
  - [File 1]
  - [File 2]

# POSITION
position:
  phase: [Current phase]
  section: [Section name]
  item: [Specific item]

completion:
  overall_pct: [0-100]
  phase_pct: [0-100]

# STATE
last_action: [What was done]
next_action: [What to do next]
decisions_made:
  - [Decision 1]
open_questions:
  - [Question 1]

# METADATA
saved_at: [Timestamp]
reason_for_save: [Why saved]

## Session History

### [Date] - [Session Type]
- Duration: [X hours]
- Tasks: [List]
- Outcome: [Summary]
```

---

## Implementation Checklist

- [ ] Create master context file with session protocol reference
- [ ] Create Task Context Log file
- [ ] Add "Initialize" trigger to your workflow
- [ ] Add "End session" trigger to your workflow
- [ ] Test full cycle: Initialize → Work → End session → Resume

---

## Common Mistakes

1. **Skipping End Session:** Progress not captured, next session starts blind
2. **Not saving task position:** Can't resume where you left off
3. **Forgetting to update Graph Index:** Files created but graph doesn't know
4. **Generic saves:** "In progress" instead of exact position (file, section, item)
5. **No verification display:** User can't confirm what was loaded/saved
