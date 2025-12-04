# CLAUDE.md - Acme Consulting Business Context

> **MASTER CONTEXT FILE** - Read this first, every session, without exception
> This file controls how AI agents operate in this vault

---

## Session Initialization Protocol

**When user says: "Initialize" or "Load context" or "Start session"**

### BOOT SEQUENCE

**Step 1: System Health Check**
- Read `00-System/Graph Index.md`
- Scan for blockers
- Verify today's daily note exists
- Calculate system health score

**Step 2: Load Business Context (TIER 0)**

Read in exact order:
1. `CLAUDE.md` (this file)
2. `00-System/Graph Index.md`
3. `00-System/Brain Dump Master.md`
4. `01-Daily/[Today's Date].md`

**Step 3: Display Context Verification**

```
TIER 0 CONTEXT VERIFICATION

EXPECTED (4 files)          LOADED              STATUS
CLAUDE.md                   [x] ~2,500 tok      OK
Graph Index                 [x] ~800 tok        OK
Brain Dump Master           [x] ~600 tok        OK
Today's Daily Note          [x] ~400 tok        OK

CONTEXT STATUS: [==--------] 8% (~4.3k/50k)
STATE: TIER 0 COMPLETE
```

**Step 4: Business State Summary**

```
BUSINESS STATE

Stage: Pre-Launch | Revenue: $0/$50k target

CRITICAL PATH:
 [1] Define Service Packages (75% complete)
    ↓
 [2] Create Pricing Strategy → unlocks sales
    ↓
 [3] First Paying Client

BLOCKERS (1):
 - Pricing Strategy blocked by Service Packages

Projects: 3 active | 1 completed
```

**Step 5: Priority Surfacing**

```
WHAT NEEDS ATTENTION TODAY

FROM CRITICAL PATH:
 → Complete Service Packages definition
   Impact: Unblocks Pricing Strategy + Sales

FROM TASKS-BACKLOG:
 1. [Critical Path] Finalize service tiers
 2. [This Week] Create proposal template
 3. [Backlog] Set up CRM

RECOMMENDATION: Complete Service Packages (1-2 hours work remaining)

What's the focus?
```

---

## Business Overview

### Company Name
**Acme Consulting** (fictional example)

### Mission Statement
Helping small businesses optimize operations through practical consulting

### Vision
Become the go-to operational consultant for local businesses

### Core Values
- Practical over theoretical
- Measurable results
- Long-term relationships

---

## Business Model

### Target Market
**Primary:** Local small businesses (5-50 employees)
**Focus:** Service businesses ready for operational improvement

### Value Proposition
Practical consulting that delivers measurable improvements in efficiency and profitability

### Revenue Streams
1. **Primary:** Consulting engagements
2. **Secondary:** Workshop facilitation
3. **Upsell:** Ongoing advisory retainers

---

## Current Stage

**Phase:** Pre-Launch / First Client Acquisition

### Completed
- [x] Business registration
- [x] Website draft
- [x] Service concept defined

### In Progress
- [ ] Service packages (75%)
- [ ] Pricing strategy (blocked)
- [ ] First client outreach

### Current Focus
1. Complete service packages
2. Finalize pricing
3. Reach out to warm leads

---

## Working Preferences

### Communication Style
Direct and action-oriented

### Decision-Making
ROI-focused - every decision should lead to first client

### Schedule
- Morning: Deep work (9am-12pm)
- Afternoon: Admin and calls
- Evening: Planning

---

## Agent Instructions

### Primary Responsibilities
1. Help organize tasks toward first client
2. Challenge scope creep
3. Maintain momentum
4. Keep context updated

### Challenge Protocol
Push back when:
- Adding complexity before first client
- Analysis paralysis
- Avoiding sales activities
- Unrealistic daily goals

### Session End Protocol
When user says "End session":
1. Save task state
2. Update relevant files
3. Set tomorrow's priority
4. Display session summary

---

## Active Projects

### Critical Path
1. **Service Packages** - 75% complete
2. **Pricing Strategy** - Blocked by #1
3. **First Client Acquisition** - Planning

### Supporting
- Website content
- Proposal template

---

## Key Resources

- Website: www.acme-consulting.example
- Email: hello@acme-consulting.example

---

*This is a FICTIONAL example for demonstration purposes.*
