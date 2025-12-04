# Architecture Documentation

> Technical deep-dive into how Business Vault OS works

---

## Contents

1. **[knowledge-graph.md](knowledge-graph.md)** - How the relationship system works
2. **[context-tiers.md](context-tiers.md)** - The tiered context loading system
3. **[session-lifecycle.md](session-lifecycle.md)** - Initialize → Work → End Session flow
4. **[safety-systems.md](safety-systems.md)** - Verification and validation protocols

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                      Business Vault OS                          │
├─────────────────────────────────────────────────────────────────┤
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐      │
│  │   CLAUDE.md  │───▶│  Graph Index │───▶│   Projects   │      │
│  │   (Identity) │    │   (Map)      │    │   (Work)     │      │
│  └──────────────┘    └──────────────┘    └──────────────┘      │
│         │                   │                   │               │
│         ▼                   ▼                   ▼               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │              Context Tier System                         │   │
│  │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐        │   │
│  │  │ Tier 0 │  │ Tier 1 │  │ Tier 2 │  │ Tier 3 │        │   │
│  │  │ Always │  │  Task  │  │  Ref   │  │Archive │        │   │
│  │  └────────┘  └────────┘  └────────┘  └────────┘        │   │
│  └─────────────────────────────────────────────────────────┘   │
│         │                   │                   │               │
│         ▼                   ▼                   ▼               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │              Safety Protocols                            │   │
│  │  • Freshness Verification                               │   │
│  │  • Blocker Validation                                   │   │
│  │  • Truth-First Mode                                     │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

---

## Core Design Principles

### 1. Single Source of Truth
Every piece of information has ONE authoritative location. The Graph Index points to where things live; it doesn't duplicate them.

### 2. Explicit Relationships
Dependencies between files are declared in YAML frontmatter, not implied. If File A blocks File B, both files say so explicitly.

### 3. Tiered Loading
Not everything needs to be loaded every session. The tier system ensures Claude has the right context for the task at hand.

### 4. Fail Visibly
Silent failures are the enemy. Safety protocols catch stale data, phantom blockers, and outdated assumptions before they cause wasted effort.

### 5. Human-AI Partnership
The system enhances human judgment; it doesn't replace it. Claude recommends, challenges, and assists—but you decide.

---

## How Components Connect

```
Initialize
    │
    ├──▶ Load CLAUDE.md (who you are, how to work)
    │
    ├──▶ Load Graph Index (what exists, what's blocked)
    │
    ├──▶ Run Safety Checks (validate before recommending)
    │
    ├──▶ Surface Priorities (what needs attention)
    │
    └──▶ Wait for Direction (you choose the focus)
           │
           └──▶ Load Tier 1 Context (task-specific files)
                  │
                  └──▶ Begin Work (with full context)
```

---

## File Relationships

The system uses four relationship types:

| Relationship | Meaning | Example |
|--------------|---------|---------|
| `depends_on` | Cannot complete until dependency done | Pricing depends_on Services |
| `blocks` | Other files waiting on this | Services blocks Pricing |
| `informs` | Information flows to (soft link) | Research informs Strategy |
| `related` | Loosely connected (navigation) | Sales related to Marketing |

---

## Context Budget

Claude has a limited context window. The tier system manages this:

| Tier | Load When | Typical Size |
|------|-----------|--------------|
| 0 | Always (every session) | ~15-20k tokens |
| 1 | Task-specific | ~30-50k tokens |
| 2 | On-demand reference | As needed |
| 3 | Never (archived) | N/A |

**Target:** Stay under 50% context usage for room to work.

---

## Further Reading

- [knowledge-graph.md](knowledge-graph.md) - Deep dive on relationships
- [context-tiers.md](context-tiers.md) - How tiers work in practice
- [session-lifecycle.md](session-lifecycle.md) - The full session flow
- [safety-systems.md](safety-systems.md) - Verification protocols
