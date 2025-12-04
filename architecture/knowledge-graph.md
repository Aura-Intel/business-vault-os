# Knowledge Graph Architecture

> How files relate to each other and why it matters

---

## What is a Knowledge Graph?

A knowledge graph is a network of connected information. In Business Vault OS, every file can declare its relationships to other files, creating a map that Claude can traverse to understand:

- What depends on what
- What's blocking progress
- What information flows where
- How completing one thing unlocks others

---

## The Graph Index

The Graph Index (`00-System/Graph-Index.md`) is the central map of your vault. It contains:

1. **File Registry** - Every tracked file with its type, status, and tier
2. **Relationship Map** - All declared dependencies
3. **Active Blockers** - What's currently blocking what
4. **Critical Path** - The sequence to reach your goal

### Why a Central Index?

Claude can't efficiently scan your entire vault every session. The Graph Index provides:
- Quick lookup of what exists
- Immediate visibility into blockers
- Dependency chains without reading every file

---

## Relationship Types

### depends_on
**Meaning:** This file cannot be completed until the dependency is done.

```yaml
# In Pricing-Strategy.md
depends_on:
  - "[[Service-Packages]]"
```

**Use when:** Work literally cannot proceed without the other file being complete.

**Example:** You can't price services you haven't defined.

---

### blocks
**Meaning:** Other files are waiting for this one.

```yaml
# In Service-Packages.md
blocks:
  - "[[Pricing-Strategy]]"
  - "[[Proposal-Template]]"
```

**Use when:** Completing this file unblocks other work.

**Note:** `blocks` is the inverse of `depends_on`. If A depends_on B, then B blocks A.

---

### informs
**Meaning:** Information from this file is used elsewhere (soft dependency).

```yaml
# In Competitor-Research.md
informs:
  - "[[Pricing-Strategy]]"
  - "[[Service-Packages]]"
```

**Use when:** Information flows from one file to another, but it's not a hard blocker.

**Example:** Competitor research informs pricing decisions, but you could price without it.

---

### related
**Meaning:** Loosely connected files (for navigation).

```yaml
# In Sales-Playbook.md
related:
  - "[[Objection-Handling]]"
  - "[[Lead-Qualification]]"
```

**Use when:** Files are in the same domain but don't have dependency relationships.

---

## YAML Frontmatter Schema

Every file that participates in the graph needs YAML frontmatter:

```yaml
---
file_type: project          # system/project/task/learning/daily/reference
file_id: service-packages   # unique kebab-case identifier
title: Service Packages     # human-readable name
created: 2024-01-05
updated: 2024-01-15
status: active              # planning/active/blocked/complete/archived

depends_on:
  - "[[Dependency-File]]"
blocks:
  - "[[Blocked-File]]"
informs:
  - "[[Informed-File]]"
related:
  - "[[Related-File]]"

context_tier: 1             # 0/1/2/3
priority: high              # critical/high/medium/low
---
```

---

## Critical Path

The critical path is the sequence of dependencies leading to your goal:

```
[Service Packages] → [Pricing Strategy] → [First Client]
     (active)           (blocked)           (goal)
```

**How to identify:**
1. Start with your goal
2. Ask: "What must be complete before this?"
3. Repeat until you reach something with no dependencies
4. That chain is your critical path

**Why it matters:**
- Work on the critical path has highest impact
- Clearing a blocker on the critical path accelerates everything downstream

---

## Keeping the Graph Accurate

### When to Update

- **Add file:** Add to Graph Index registry
- **Complete file:** Update status, remove from blockers
- **New dependency discovered:** Add to both files
- **Relationship obsolete:** Remove from both files

### Validation Protocol

The system should verify:
1. Every `depends_on` has a corresponding `blocks`
2. Blocked files actually exist
3. No circular dependencies
4. Critical path is traversable

---

## Graph Queries

Common queries Claude runs during Initialize:

| Query | Purpose |
|-------|---------|
| "What's blocked?" | Surface active blockers |
| "What does X unlock?" | Show downstream impact |
| "What's stale?" | Files not updated recently |
| "What's 80% done?" | Quick wins |

---

## Example: Tracing Impact

When you complete Service Packages:

```
Service Packages COMPLETE
        │
        └──▶ Pricing Strategy UNBLOCKED
                    │
                    └──▶ Proposal Template UNBLOCKED
                    │
                    └──▶ First Client Outreach UNBLOCKED
```

The graph makes this cascade visible.

---

## Best Practices

1. **Be explicit** - If there's a dependency, declare it
2. **Keep it current** - Update when things change
3. **Validate weekly** - Check for phantom blockers
4. **Don't over-connect** - Only meaningful relationships
5. **Use `related` sparingly** - Navigation aid, not tracking
