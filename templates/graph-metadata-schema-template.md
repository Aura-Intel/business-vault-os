# Graph Metadata Schema Template

> **Purpose:** Standard YAML frontmatter structure for all vault files
> **Implementation:** Add to every file that should be part of the knowledge graph

---

## Overview

Every file in the vault can have metadata that defines:
1. **Identity** - What type of file, when created, current status
2. **Relationships** - How it connects to other files
3. **Context Management** - When and how it should be loaded

---

## Full Schema

```yaml
---
# IDENTITY
file_type: [system/project/task/learning/daily/reference]
file_id: [unique-kebab-case-identifier]
title: [Human-readable title]
created: [YYYY-MM-DD]
updated: [YYYY-MM-DD]
status: [planning/active/blocked/complete/archived]
confidence: [high/medium/low]

# RELATIONSHIPS
depends_on:
  - "[[File that must exist/complete first]]"
blocks:
  - "[[File that cannot progress until this completes]]"
informs:
  - "[[File that uses information from this file]]"
related:
  - "[[Loosely connected file]]"
parent: "[[Parent file if hierarchical]]"
children:
  - "[[Child file 1]]"
  - "[[Child file 2]]"

# CLASSIFICATION
tags: [tag1, tag2, tag3]
first_client_relevant: [true/false]
priority: [critical/high/medium/low]
owner: [founder/team-member/external]
blockers:
  - blocker_id: [id]
    description: [what's blocking]
    severity: [HIGH/MEDIUM/LOW]
    resolution_path: [how to unblock]

# CONTEXT MANAGEMENT
context_tier: [0/1/2/3]
est_tokens: [estimated token count when loaded]
task_type: [task type for auto-loading]
decision_weight: [critical/high/medium/low]
refresh_triggers:
  - [event that should trigger reload]
required_context:
  always:
    - "[[Always load with this file]]"
  for_decisions:
    - "[[Load when making decisions about this]]"
  for_modifications:
    - "[[Load when modifying this file]]"
---
```

---

## Field Definitions

### Identity Fields

| Field | Required | Description |
|-------|----------|-------------|
| `file_type` | Yes | Category of file (system, project, task, etc.) |
| `file_id` | Yes | Unique identifier in kebab-case |
| `title` | Yes | Human-readable name |
| `created` | Yes | Creation date (YYYY-MM-DD) |
| `updated` | Yes | Last modification date |
| `status` | Yes | Current state of the file |
| `confidence` | No | How certain you are about the content |

### Relationship Fields

| Field | Required | Description |
|-------|----------|-------------|
| `depends_on` | No | Files that must exist/complete before this |
| `blocks` | No | Files that cannot progress until this completes |
| `informs` | No | Files that use information from this file |
| `related` | No | Loosely connected files |
| `parent` | No | Parent file in hierarchy |
| `children` | No | Child files in hierarchy |

### Classification Fields

| Field | Required | Description |
|-------|----------|-------------|
| `tags` | No | Searchable tags |
| `first_client_relevant` | No | Affects first client goal? |
| `priority` | No | Importance level |
| `owner` | No | Who is responsible |
| `blockers` | No | Active blockers on this file |

### Context Management Fields

| Field | Required | Description |
|-------|----------|-------------|
| `context_tier` | Yes | 0=always, 1=task-specific, 2=reference, 3=archive |
| `est_tokens` | No | Estimated tokens when loaded |
| `task_type` | No | Used for automatic context loading |
| `decision_weight` | No | How important for decisions |
| `refresh_triggers` | No | Events that should reload this file |
| `required_context` | No | Other files to load with this one |

---

## Minimal Schema (Quick Add)

For files where you want basic tracking without full metadata:

```yaml
---
file_type: [type]
file_id: [unique-id]
title: [Title]
created: [YYYY-MM-DD]
updated: [YYYY-MM-DD]
status: active
context_tier: 1
---
```

---

## Schema by File Type

### System Files
```yaml
---
file_type: system
context_tier: 0
priority: critical
owner: claude
---
```

### Project Files
```yaml
---
file_type: project
context_tier: 1
first_client_relevant: true
priority: [based on importance]
depends_on: [list dependencies]
blocks: [list what this blocks]
---
```

### Task Files
```yaml
---
file_type: task
context_tier: 1
parent: "[[Parent Project]]"
priority: [based on urgency]
---
```

### Learning Files
```yaml
---
file_type: learning
context_tier: 2
informs: [what this knowledge applies to]
---
```

### Daily Notes
```yaml
---
file_type: daily
context_tier: 0
tags: [daily, planning]
---
```

---

## Relationship Types Explained

### depends_on
**Meaning:** This file cannot be completed until the dependency is done.
**Example:** "Service Packages" depends_on "Niche Definition" (can't define services until niche is clear)

### blocks
**Meaning:** Other files are waiting for this one to complete.
**Example:** "Niche Definition" blocks "Service Packages", "Pricing Strategy", "Lead Generation"

### informs
**Meaning:** Information from this file is used elsewhere (but not a hard dependency).
**Example:** "Founder Background" informs "CLAUDE.md" (background context helps AI understand you)

### related
**Meaning:** Loosely connected, useful for navigation.
**Example:** "Sales Playbook" related to "Objection Handling" (related topics, not dependent)

### parent / children
**Meaning:** Hierarchical structure.
**Example:** "First Client Acquisition" (parent) has children "Service Packages", "Pricing Strategy"

---

## Validation Rules

1. **file_id must be unique** across entire vault
2. **Wikilinks must use exact file names** in `[[brackets]]`
3. **Dates must be YYYY-MM-DD format**
4. **Status values must be from allowed list**
5. **context_tier must be 0, 1, 2, or 3**

---

## Adding a New File Checklist

- [ ] Add YAML frontmatter with at least minimal schema
- [ ] Set appropriate context_tier
- [ ] Add to Graph Index
- [ ] Link dependencies (depends_on, blocks)
- [ ] Update related files' relationships if needed
