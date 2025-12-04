---
file_type: project
file_id: [project-name-kebab-case]
title: [Project Title]
created: [YYYY-MM-DD]
updated: [YYYY-MM-DD]
status: [planning/active/blocked/complete]
confidence: [high/medium/low]

# RELATIONSHIPS
depends_on:
  - "[[Dependency 1]]"
  - "[[Dependency 2]]"
blocks:
  - "[[What this blocks 1]]"
  - "[[What this blocks 2]]"
informs:
  - "[[What this informs]]"
related:
  - "[[Related file]]"
parent: "[[Parent project if applicable]]"
children:
  - "[[Child task/project 1]]"
  - "[[Child task/project 2]]"

# CLASSIFICATION
tags: [project, relevant-tags]
first_client_relevant: [true/false]
priority: [critical/high/medium/low]
owner: [founder/other]
blockers: []

# CONTEXT MANAGEMENT
context_tier: 1
est_tokens: [estimate]
task_type: [project_type]
decision_weight: [critical/high/medium/low]
refresh_triggers:
  - [when to reload this file]
required_context:
  always: []
  for_decisions: []
  for_modifications: []
---

# [Project Title]

> **Status:** [Current status description]
> **Goal:** [What this project achieves]
> **Target:** [Deadline or milestone if applicable]

---

## Overview

[2-3 sentences describing what this project is and why it matters]

---

## Success Criteria

- [ ] [Measurable outcome 1]
- [ ] [Measurable outcome 2]
- [ ] [Measurable outcome 3]

---

## Current Status

**Phase:** [Current phase]
**Progress:** [X]%
**Last Updated:** [Date]

### What's Done
- [x] [Completed item]

### What's In Progress
- [ ] [Current work item]

### What's Blocked
- [ ] [Blocked item] - Blocked by: [[Blocker]]

### What's Next
- [ ] [Upcoming item]

---

## Key Decisions

| Date | Decision | Rationale |
|------|----------|-----------|
| [Date] | [Decision made] | [Why] |

---

## Dependencies

### This Project Depends On:
- [[Dependency]] - Status: [status]

### This Project Blocks:
- [[Downstream project]] - Impact: [what happens when this completes]

---

## Resources

- [Resource 1]
- [Resource 2]

---

## Notes

[Running notes, observations, learnings]

---

## Completion Criteria

**This project is DONE when:**
- [ ] [Final deliverable 1]
- [ ] [Final deliverable 2]
- [ ] [Downstream items unblocked]
