# Safety Protocols Template

> **Purpose:** Prevent silent failures - stale data, phantom blockers, wrong assumptions
> **Implementation:** Reference in master context, run automatically during Initialize

---

## Overview

AI assistants fail silently. They confidently recommend based on stale data, work on resolved blockers, or make decisions on outdated assumptions. These protocols catch failures BEFORE they waste your time.

---

## PROTOCOL 1: Freshness Verification

### Purpose
Prevent recommendations based on outdated Graph Index

### When It Runs
- Before any priority recommendation
- During Initialize
- When user asks "What should I work on?"

### Logic

```
1. Read Graph Index → Check "Last Sync" timestamp
2. Calculate age: Current time - Last Sync

FRESHNESS LEVELS:
- < 4 hours: FRESH ✅ → Proceed with confidence
- 4-12 hours: STALE ⚠️ → Verify critical path before recommending
- 12-24 hours: VERY STALE 🔴 → Update required before proceeding
- > 24 hours: CRITICAL 🚫 → Refuse to recommend until updated
```

### Output Format

```
FRESHNESS CHECK:
 Graph Index: [X] hours old
 Status: [FRESH/STALE/VERY STALE/CRITICAL]
 Action: [Proceeding / Verifying / Updating required]
```

### Verification Process (for STALE)

```
1. Identify files on critical path
2. Read each file's actual status
3. Compare to Graph Index status
4. If mismatch: Flag for update
5. If match: Proceed with recommendation
```

---

## PROTOCOL 2: Blocker Validation

### Purpose
Prevent working on phantom blockers (resolved but not updated in graph)

### When It Runs
- Before surfacing any blocker to user
- During Initialize blocker summary
- When user asks "What's blocking me?"

### Logic

```
For each blocker listed in Graph Index:
1. Read the actual blocker file
2. Check status field
3. Look for completion markers (✅, DONE, RESOLVED)
4. Compare to Graph Index status

IF file shows complete but Graph shows blocked:
  → PHANTOM BLOCKER detected
  → Auto-resolve OR flag for user
```

### Output Format

```
BLOCKER VALIDATION:
 Checking [X] blockers from Graph Index...

 ✅ [Blocker 1]: Validated (still blocked)
 🚨 [Blocker 2]: PHANTOM - File shows COMPLETE
    → Auto-resolving in Graph Index

 Result: [X] valid blockers, [Y] phantom blockers removed
```

### Auto-Resolution Rules

```
AUTO-RESOLVE when:
- File status explicitly says "complete" or "resolved"
- Completion markers present (✅, DONE, etc.)
- Updated timestamp is recent

ASK USER when:
- Ambiguous status
- Partial completion
- External dependency (can't verify)
```

---

## PROTOCOL 3: Constraint Verification

### Purpose
Prevent decisions based on outdated constraints (budget, timeline, capacity)

### When It Runs
- Before investment/spending recommendations
- Before strategic direction advice
- When constraint data is >7 days old AND decision is high-stakes

### Logic

```
1. Identify constraints relevant to current decision
2. Check when each constraint was last verified
3. If >7 days old + high-stakes decision: Verify with user

CONSTRAINT TYPES:
- Financial (budget, capital, revenue)
- Capacity (time available, team size)
- Timeline (deadlines, milestones)
- External (market conditions, dependencies)
```

### Output Format

```
CONSTRAINT CHECK:
 Decision: [What we're deciding]
 Stakes: [HIGH/MEDIUM/LOW]

 Constraints used:
 - Budget: £[X] (verified [date]) ✅
 - Timeline: [X] weeks (verified [date]) ⚠️ STALE
 - Capacity: [X] hours/week (verified [date]) ✅

 Action: Confirming timeline constraint before proceeding.
 Current timeline assumption: [X]. Still accurate?
```

---

## PROTOCOL 4: Brain Dump Health Check

### Purpose
Prevent mental capture system from becoming overwhelming

### When It Runs
- During Initialize
- When Brain Dump >20 items
- Weekly (Sunday planning)

### Logic

```
1. Count pending items in Brain Dump
2. Check days since last full processing

HEALTH LEVELS:
- 0-10 items: HEALTHY ✅
- 11-20 items: ATTENTION ⚠️ (process soon)
- 21-30 items: OVERLOAD 🔴 (process now)
- >30 items: CRITICAL 🚫 (blocking productivity)

PROCESSING AGE:
- <7 days: Current
- 7-14 days: Due for processing
- >14 days: Overdue
```

### Output Format

```
BRAIN DUMP HEALTH:
 Items pending: [X]
 Last processed: [Date] ([X] days ago)
 Status: [HEALTHY/ATTENTION/OVERLOAD/CRITICAL]

 [If ATTENTION+]:
 Recommendation: Process Brain Dump before starting new work.
 Top 3 items by age:
  1. [Item]
  2. [Item]
  3. [Item]
```

---

## PROTOCOL 5: Truth-First Verification

### Purpose
Ensure AI responses are evidence-based, not hallucinated

### Core Principles

```
1. VERIFY before claiming
   - Check if evidence exists in current chat or files
   - If no evidence: Say "INSUFFICIENT DATA"

2. CONFIDENCE LABELS
   - High: Direct evidence in files/conversation
   - Medium: Inferred from multiple sources
   - Low: Single source or partial evidence

3. QUOTE-BACK for claims
   - When referencing prior conversation: Quote exact text
   - When referencing files: Cite file name and relevant section

4. STOP instead of guess
   - Unknown dates: Ask, don't assume
   - Missing context: Request, don't invent
   - Ambiguous instructions: Clarify, don't interpret
```

### User Verification Commands

```
"Spot check" → Verify last 3 claims made
"Show your work" → Explain reasoning with sources
"What could go wrong?" → List failure modes
"Verify this" → Re-check specific claim
"Prove it" → Show exact file/line evidence
```

---

## Implementation

### Step 1: Add to Master Context

Include in your CLAUDE.md or equivalent:

```markdown
## Safety Protocols (Non-Negotiable)

Before any recommendation:
1. Run Freshness Verification on Graph Index
2. Run Blocker Validation on active blockers
3. Run Constraint Verification for high-stakes decisions
4. Check Brain Dump health

After any file creation:
5. Run Enforcement Verification (proof required)
```

### Step 2: Create Protocol Files

Create individual protocol files with detailed logic (optional - can keep in master context if simple).

### Step 3: Test Each Protocol

- Freshness: Let Graph Index go stale, verify warning appears
- Blocker: Manually complete a blocked item, verify phantom detection
- Constraint: Make high-stakes decision, verify constraint check runs
- Brain Dump: Add 25 items, verify overload warning

---

## Common Failure Modes These Catch

| Failure | Protocol | Detection |
|---------|----------|-----------|
| Recommending completed task | Freshness | Graph stale, task already done |
| Working on resolved blocker | Blocker Validation | Phantom blocker detected |
| Budget decision on old numbers | Constraint | Stale financial data flagged |
| Overwhelm from uncaptured tasks | Brain Dump Health | Item count too high |
| AI making up facts | Truth-First | No evidence = "INSUFFICIENT DATA" |

---

## Trust Guarantee

With these protocols active:
- ✅ Recommendations based on current state (not stale)
- ✅ Blockers are real (not phantom)
- ✅ Constraints are verified (not assumed)
- ✅ Mental state is manageable (not overwhelming)
- ✅ Claims are evidence-based (not hallucinated)

**The user can trust the system because failures are caught automatically.**
