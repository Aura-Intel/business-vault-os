# Opus Prompt: Knowledge Graph Architecture Design

> **Purpose:** Have Opus design a complete knowledge graph architecture for your vault
> **Time:** 10-15 minutes for Opus to complete
> **Output:** Full architecture specification

---

## The Prompt

Copy and paste everything below to Opus:

---

You are designing a knowledge graph architecture for an Obsidian vault that will be used with Claude Code (AI assistant with file access).

## Context

**Business/Project Type:** [FILL IN: e.g., "AI automation consultancy", "SaaS startup", "Freelance design"]

**Current Vault State:** [FILL IN: e.g., "New vault, starting fresh" or "Existing vault with ~50 files"]

**Primary Goal:** [FILL IN: e.g., "Land first paying client", "Launch MVP", "Scale to 10 clients"]

**Key Challenges:** [FILL IN: e.g., "Losing context between sessions", "Don't know what's blocking what", "Vault is chaotic"]

## Requirements

Design a complete knowledge graph architecture that includes:

### 1. Metadata Schema
- YAML frontmatter structure for all file types
- Required vs optional fields
- Validation rules

### 2. Relationship Types
- Define relationship types (depends_on, blocks, informs, etc.)
- Explain when to use each
- Show examples

### 3. File Type Definitions
- What file types exist (project, task, daily, learning, etc.)
- Standard structure for each
- Naming conventions

### 4. Graph Index Structure
- Central index file format
- What it tracks
- How it's maintained

### 5. Context Tier System
- Define tiers (0, 1, 2, 3)
- What goes in each tier
- Loading rules

### 6. Initialize Protocol
- What happens when user says "Initialize"
- Step-by-step sequence
- Output format

### 7. Session Management
- Start protocol
- End protocol
- Task state preservation

### 8. Auto-Maintenance
- Daily checks
- Weekly scans
- Monthly cleanup
- Archive rules

### 9. Safety Protocols
- Freshness verification
- Blocker validation
- Truth-first principles

### 10. Scaling Rules
- Maximum active files
- When to archive
- How to compress old content

## Output Format

For each component, provide:
1. **Specification** - Detailed description of how it works
2. **Template** - Ready-to-use template file
3. **Examples** - Concrete examples of usage
4. **Edge Cases** - What could go wrong and how to handle

## Design Principles

- Prioritize simplicity over completeness
- Make it self-documenting
- Fail visibly (no silent failures)
- User should be able to trust the system
- System should get smarter with use

Please design the complete architecture now.

---

## After Opus Completes

1. Review each component
2. Ask clarifying questions if needed
3. Save outputs to appropriate template files
4. Implement incrementally
5. Test each component before adding the next
