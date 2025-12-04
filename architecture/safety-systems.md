# Safety Systems

> Preventing silent failures before they waste your time

---

## Why Safety Systems?

AI assistants can fail silently:
- Recommend tasks you already completed
- Miss that a blocker was resolved
- Base advice on stale assumptions
- Create phantom problems that don't exist

**Safety systems catch these failures BEFORE they cause harm.**

---

## Core Safety Protocols

### 1. Freshness Verification

**Problem:** Graph Index might be outdated, leading to stale recommendations.

**Solution:** Check staleness before trusting the graph.

```
FRESHNESS CHECK

Graph Index age: [X] hours

< 4 hours:  ✅ Current - proceed normally
4-24 hours: ⚠️ Verify critical path before proceeding
> 24 hours: 🛑 Update required before continuing
```

**When it runs:**
- During Initialize
- Before priority recommendations
- When asking "What should I work on?"

**What it does:**
1. Check Graph Index last-updated timestamp
2. If stale, verify key files match graph status
3. Detect completed work not reflected in graph
4. Warn or auto-update based on severity

---

### 2. Blocker Validation

**Problem:** Blockers in Graph Index might be resolved (phantom blockers).

**Solution:** Verify blockers actually exist before surfacing them.

```
BLOCKER VALIDATION

Checking: [Blocker Name]
Graph says: BLOCKING [X files]
Actual file status: COMPLETE

⚠️ PHANTOM BLOCKER DETECTED
Auto-resolving and updating graph.
```

**When it runs:**
- During Initialize (all critical path blockers)
- Before surfacing any blocker
- When you ask "What's blocking me?"

**What it does:**
1. Read each blocker file directly
2. Compare file status to Graph Index
3. If mismatch: flag as phantom
4. Auto-resolve clear cases, ask for ambiguous

---

### 3. Constraint Verification

**Problem:** Business constraints (budget, stage, capacity) change over time.

**Solution:** Verify constraints before high-stakes recommendations.

```
CONSTRAINT CHECK

Before recommending: [Major decision]

Verifying constraints:
- Capital: $0 (last updated: 3 days ago) ✅
- Stage: Pre-launch (current) ✅
- Capacity: 6 hours/day (assumed) ⚠️

Constraint "Capacity" may be stale.
Please confirm before proceeding.
```

**When it runs:**
- Before investment recommendations
- Before strategic advice
- Before capacity-dependent planning

**What it does:**
1. Identify which constraints affect the recommendation
2. Check when each was last verified
3. If stale + high-stakes: ask to confirm
4. Timestamp all constraints in recommendations

---

### 4. Brain Dump Health

**Problem:** Brain Dump can accumulate until it creates overwhelm.

**Solution:** Monitor capacity and trigger processing.

```
BRAIN DUMP HEALTH

Items: 24/30
Last processed: 16 days ago

⚠️ OVERFLOW WARNING
Brain Dump at 80% capacity and stale.
Recommend processing session before new work.

Process now? (y/n)
```

**Triggers:**
- >20 items: Process recommended
- >14 days unprocessed: Weekly review overdue
- "I'm overwhelmed": Automatic processing session

**What it does:**
1. Count pending items
2. Check last processing date
3. If unhealthy: recommend or require processing
4. Guide through structured processing

---

### 5. Truth-First Mode

**Problem:** AI can hallucinate or make confident claims without evidence.

**Solution:** Require evidence for all claims, admit uncertainty.

```
TRUTH-FIRST ACTIVE

All recommendations include:
- Evidence source (which file)
- Confidence level (high/medium/low)
- "INSUFFICIENT DATA" when uncertain

Verification commands:
- "Spot check" - verify recent claims
- "Show your work" - explain reasoning
- "Prove it" - show exact evidence
```

**Always active.** This isn't a sometimes protocol—it's an operating mode.

**What it means:**
- Never guess, always verify
- Quote sources when making claims
- Say "I don't know" when evidence lacking
- Confidence labels on all recommendations

---

## Safety Protocol Integration

### During Initialize

```
Initialize
    │
    ├─▶ Load Tier 0
    │
    ├─▶ SAFETY: Freshness Verification
    │        └─ Is Graph Index current?
    │
    ├─▶ SAFETY: Blocker Validation
    │        └─ Are blockers real?
    │
    ├─▶ SAFETY: Brain Dump Health
    │        └─ Is Brain Dump manageable?
    │
    └─▶ Surface Priorities (with verified data)
```

### Before Recommendations

```
Recommendation Request
    │
    ├─▶ SAFETY: Constraint Verification
    │        └─ Are assumptions current?
    │
    ├─▶ SAFETY: Truth-First Check
    │        └─ Can I evidence this?
    │
    └─▶ Deliver Recommendation (with confidence)
```

---

## User Verification Commands

You can trigger safety checks manually:

| Command | Action |
|---------|--------|
| "Spot check" | Verify last 3 claims |
| "Show your work" | Explain reasoning with sources |
| "What could go wrong?" | List failure modes |
| "Verify this" | Re-check specific claim |
| "Prove it" | Show exact file/line evidence |
| "Truth-First check" | Full self-correction audit |

---

## Handling Safety Failures

### When a Check Fails

1. **Pause** - Don't proceed with flawed data
2. **Display** - Show what was found
3. **Ask** - Get direction on how to proceed
4. **Fix** - Update the source of truth
5. **Continue** - Resume with accurate data

### Example Flow

```
⚠️ SAFETY CHECK FAILED

Issue: Phantom blocker detected
- Graph says: "Pricing Strategy" blocked by "Service Packages"
- Actual status: "Service Packages" is COMPLETE

Options:
A) Auto-resolve (update graph, remove blocker)
B) Manual review (show me the files)
C) Proceed anyway (trust graph)

Your choice?
```

---

## Auto-Resolution Rules

Some failures can be auto-fixed:

| Failure Type | Auto-Fix | Notify |
|--------------|----------|--------|
| Phantom blocker (clear evidence) | Yes | Yes |
| Missing daily note | Yes (create) | Yes |
| Stale graph (<24h) | No (warn only) | Yes |
| Constraint uncertainty | No (ask) | Yes |
| Evidence not found | No (stop) | Yes |

**Rule:** Auto-fix only when evidence is unambiguous. Ask when uncertain.

---

## Building Trust

These systems exist to make the vault trustworthy:

1. **When told blocked, you actually are**
2. **Recommendations based on current reality**
3. **Claims backed by evidence**
4. **Failures caught before causing harm**

The system earns trust through verification, not assumption.
