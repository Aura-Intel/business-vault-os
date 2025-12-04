# Opus Prompts

> **Purpose:** Prompts for designing and customizing the vault system using Claude Opus 4.5
> **When to use:** Complex architecture decisions, major protocol creation, system redesign

---

## Why Opus?

Claude Opus 4.5 has:
- Larger context window (better for complex system design)
- Stronger reasoning (better for architecture decisions)
- More thorough analysis (better for edge case identification)

**Workflow:**
1. Use Opus for architecture design and major protocol creation
2. Use Sonnet (or Claude Code default) for daily operation
3. Iterate based on real usage

---

## Available Prompts

### 1. knowledge-graph-design-prompt.md
**Use for:** Initial vault setup or major restructure
**Output:** Complete knowledge graph architecture including metadata schemas, relationship types, and maintenance protocols

### 2. safety-protocol-design-prompt.md
**Use for:** Designing or improving safety protocols
**Output:** Verification systems, failure detection, and auto-correction logic

### 3. customize-for-domain-prompt.md
**Use for:** Adapting the system to a specific industry/use case
**Output:** Domain-specific file types, relationships, and workflows

---

## How to Use These Prompts

### In Claude Code:
```
1. Start Claude Code session
2. Use Task tool with model="opus"
3. Paste the relevant prompt
4. Let Opus design (5-15 minutes)
5. Review output
6. Implement with Sonnet
```

### Tips:
- Give Opus your full context (current vault structure, business type)
- Let it think thoroughly (don't rush)
- Ask follow-up questions if unclear
- Implement incrementally, test each component
