# Graph Index - Acme Consulting

> **Central Relationship Map** - Single source of truth for vault structure
> **Last Updated:** 2024-01-15 14:30
> **Health Score:** 85/100

---

## Quick Stats

| Metric | Value |
|--------|-------|
| Total Files | 12 |
| Active Projects | 3 |
| Blocked Items | 1 |
| Tasks Pending | 5 |
| Context Tier 0 | 4 files |
| Context Tier 1 | 6 files |
| Context Tier 2 | 2 files |

---

## Critical Path

```
[Define Service Packages] ──blocks──▶ [Pricing Strategy] ──blocks──▶ [First Client]
        75%                              0%                           Planning
```

**Current Bottleneck:** Service Packages (3 decisions remaining)

---

## Active Blockers

| Blocker | Blocks | Severity | Resolution Path |
|---------|--------|----------|-----------------|
| Service Packages incomplete | Pricing Strategy | HIGH | Complete tier definitions |

---

## File Registry

### Tier 0 - Always Load
| File | Type | Status | Updated |
|------|------|--------|---------|
| CLAUDE.md | system | active | 2024-01-15 |
| Graph Index.md | system | active | 2024-01-15 |
| Brain Dump Master.md | system | active | 2024-01-14 |
| Daily Note | daily | active | today |

### Tier 1 - Task Specific
| File | Type | Status | Updated |
|------|------|--------|---------|
| Service Packages.md | project | active | 2024-01-15 |
| Pricing Strategy.md | project | blocked | 2024-01-10 |
| First Client Acquisition.md | project | planning | 2024-01-12 |
| Tasks-Backlog.md | task | active | 2024-01-15 |
| Proposal Template.md | reference | draft | 2024-01-08 |
| Lead List.md | reference | active | 2024-01-14 |

### Tier 2 - Reference
| File | Type | Status | Updated |
|------|------|--------|---------|
| Competitor Research.md | learning | complete | 2024-01-05 |
| Industry Insights.md | learning | active | 2024-01-11 |

---

## Relationship Map

### depends_on Relationships
```
Pricing Strategy ──depends_on──▶ Service Packages
First Client Acquisition ──depends_on──▶ Pricing Strategy
First Client Acquisition ──depends_on──▶ Proposal Template
```

### blocks Relationships
```
Service Packages ──blocks──▶ Pricing Strategy
Pricing Strategy ──blocks──▶ First Client Acquisition
```

### informs Relationships
```
Competitor Research ──informs──▶ Pricing Strategy
Industry Insights ──informs──▶ Service Packages
Lead List ──informs──▶ First Client Acquisition
```

---

## Recent Changes

| Date | Change | Impact |
|------|--------|--------|
| 2024-01-15 | Service Packages 50%→75% | Closer to unblocking Pricing |
| 2024-01-14 | Added 3 leads to Lead List | Pipeline growing |
| 2024-01-12 | Created First Client project | Critical path defined |

---

## Maintenance Log

- **Last Full Scan:** 2024-01-14
- **Next Scheduled:** 2024-01-21
- **Issues Found:** None
- **Auto-corrections:** 0

---

*This is a FICTIONAL example for demonstration purposes.*
