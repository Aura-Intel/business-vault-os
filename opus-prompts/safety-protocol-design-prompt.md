# Opus Prompt: Safety Protocol Design

> **Purpose:** Have Opus design or improve safety protocols for your vault
> **Time:** 10-15 minutes for Opus to complete
> **Output:** Complete safety protocol specifications

---

## The Prompt

Copy and paste everything below to Opus:

---

You are designing safety protocols for an Obsidian vault knowledge graph system used with Claude Code.

## Context

**Current Safety Concerns:** [FILL IN: e.g., "Recommendations based on stale data", "Working on phantom blockers", "Decisions with outdated constraints"]

**Existing Protocols:** [FILL IN: e.g., "None yet" or "Basic freshness check exists but isn't working well"]

**Failure Modes Experienced:** [FILL IN: e.g., "Spent 2 hours on a task that was already complete", "Made decision based on old financial data"]

**Trust Level Needed:** [FILL IN: e.g., "High - I need to trust recommendations completely" or "Medium - I can verify important things manually"]

## Requirements

Design safety protocols that prevent silent failures. For each protocol, specify:

### 1. Detection Logic
- What triggers the check?
- What data is examined?
- What constitutes a failure?

### 2. Validation Rules
- Specific conditions that must be true
- Thresholds and tolerances
- Edge cases to handle

### 3. Response Actions
- What happens when check passes?
- What happens when check fails?
- Escalation path for ambiguous cases

### 4. Auto-Resolution Rules
- What can be fixed automatically?
- What requires human input?
- How to prevent false positives?

### 5. User Commands
- How can user trigger manual checks?
- What verification commands exist?
- How to override false positives?

## Protocols to Design

Based on the concerns above, design protocols for:

1. **Data Freshness** - Preventing stale recommendations
2. **Blocker Validation** - Catching phantom blockers
3. **Constraint Verification** - Ensuring current assumptions
4. **Capacity Management** - Preventing overwhelm (brain dump, backlog)
5. **Truth Verification** - Requiring evidence for claims

## Output Format

For each protocol, provide:

```markdown
## [Protocol Name]

### Purpose
[What problem this solves]

### Triggers
- [When this runs automatically]
- [How user can trigger manually]

### Detection Logic
[Step-by-step what is checked]

### Validation Rules
[Specific conditions and thresholds]

### Response Matrix

| Condition | Action | Notify User |
|-----------|--------|-------------|
| [State] | [Action] | Yes/No |

### Auto-Resolution
[What can be auto-fixed vs requires human]

### User Commands
- `[command]` - [what it does]

### Edge Cases
[What could go wrong and how handled]
```

## Design Principles

- **Fail visible** - Never fail silently
- **Ask don't assume** - When uncertain, ask
- **Protect time** - Catching errors > saving 2 minutes
- **Build trust** - User should be able to rely on the system
- **Minimal friction** - Don't interrupt unnecessarily

Please design the complete safety protocol system now.

---

## After Opus Completes

1. Review each protocol for your specific needs
2. Adjust thresholds based on your tolerance
3. Save to `00-System/` as individual protocol files
4. Add protocol references to CLAUDE.md
5. Test each protocol manually before relying on it
