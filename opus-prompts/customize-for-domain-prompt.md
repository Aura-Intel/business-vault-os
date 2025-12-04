# Opus Prompt: Domain Customization

> **Purpose:** Have Opus adapt the vault system for your specific industry/use case
> **Time:** 15-20 minutes for Opus to complete
> **Output:** Domain-specific file types, relationships, and workflows

---

## The Prompt

Copy and paste everything below to Opus:

---

You are customizing a Business Vault OS (Obsidian + Claude Code knowledge graph system) for a specific industry and use case.

## Context

**Industry/Domain:** [FILL IN: e.g., "SaaS startup", "Marketing agency", "Freelance consulting", "E-commerce", "Real estate"]

**Business Model:** [FILL IN: e.g., "B2B services", "Subscription software", "Project-based consulting", "Product sales"]

**Team Size:** [FILL IN: e.g., "Solo founder", "2-5 people", "10+ team"]

**Primary Activities:** [FILL IN: e.g., "Client delivery, lead generation, product development", "Content creation, community management, course sales"]

**Unique Challenges:** [FILL IN: e.g., "Long sales cycles", "Multiple client projects simultaneously", "Seasonal demand", "Regulatory compliance"]

## Base System

The system already includes:
- Knowledge graph with relationships (depends_on, blocks, informs)
- Context tier system (0-3)
- Session lifecycle (Initialize, Work, End Session)
- Safety protocols (freshness, validation)
- Brain dump and task management

## Customization Needed

### 1. Domain-Specific File Types

Design file types unique to this industry:

For each type:
- Name and purpose
- YAML frontmatter schema
- Standard sections
- Relationship patterns
- Tier assignment

### 2. Industry-Specific Relationships

Beyond the standard relationships, what connections matter in this domain?

Examples to consider:
- Client relationships
- Project phases
- Deliverable dependencies
- Compliance requirements
- Revenue connections

### 3. Custom Workflows

What recurring workflows exist in this domain?

For each workflow:
- Trigger conditions
- Steps involved
- Files created/updated
- Success criteria

### 4. Domain Metrics

What should be tracked and surfaced?

- Key performance indicators
- Pipeline/funnel metrics
- Capacity utilization
- Risk indicators

### 5. Modified Protocols

How should standard protocols adapt?

- Initialize modifications
- Priority surfacing changes
- Challenge protocol adjustments
- Safety protocol additions

### 6. Integration Points

What external systems might connect?

- CRM systems
- Project management
- Accounting/invoicing
- Communication tools
- Industry-specific software

## Output Format

Provide:

### Part 1: File Type Definitions

```yaml
# [File Type Name]
---
file_type: [type]
# [Domain-specific fields]
---

# Standard Sections
## [Section 1]
## [Section 2]
```

### Part 2: Relationship Map

```
[File Type A] ──[relationship]──▶ [File Type B]
```

With explanations for each relationship type.

### Part 3: Workflow Definitions

```markdown
## [Workflow Name]

### Trigger
[When this workflow starts]

### Steps
1. [Step]
2. [Step]

### Files Affected
- [File changes]

### Success Criteria
- [How you know it's done]
```

### Part 4: Metrics Dashboard

```markdown
## [Domain] Dashboard

### Key Metrics
| Metric | Source | Target |
|--------|--------|--------|
| [Metric] | [File/calculation] | [Goal] |
```

### Part 5: Modified Initialize Protocol

Show how Initialize should differ for this domain.

### Part 6: Integration Recommendations

Which integrations would add most value and how to approach them.

## Design Principles

- **Domain authenticity** - Use industry terminology
- **Practical focus** - Only add what will actually be used
- **Progressive complexity** - Start simple, add as needed
- **Measurable value** - Connect to business outcomes

Please design the complete domain customization now.

---

## After Opus Completes

1. Review for relevance to YOUR specific situation
2. Remove anything that adds complexity without value
3. Start with 2-3 most important customizations
4. Add rest incrementally as you use the system
5. Iterate based on what actually helps
