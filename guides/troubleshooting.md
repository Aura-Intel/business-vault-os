# Troubleshooting

> Common issues and how to fix them

---

## Initialization Issues

### "Claude doesn't recognize Initialize"

**Symptoms:** Claude responds generically, doesn't load context

**Causes:**
1. CLAUDE.md not in vault root
2. Missing Session Initialization Protocol section
3. Working directory not set correctly

**Fix:**
1. Verify CLAUDE.md exists at vault root
2. Check it contains the Initialize protocol
3. Make sure Claude Code is opened in the vault folder

---

### "Context verification shows missing files"

**Symptoms:** `[ ]` marks in verification display

**Causes:**
1. Files don't exist yet
2. Files in wrong location
3. Filename mismatch

**Fix:**
1. Check the expected file path
2. Create missing files using templates
3. Ensure exact naming (case-sensitive)

---

### "Daily note not auto-created"

**Symptoms:** Initialize completes but no daily note appears

**Causes:**
1. `01-Daily/` folder doesn't exist
2. Template missing
3. Date format mismatch

**Fix:**
1. Create `01-Daily/` folder
2. Add daily note template to templates folder
3. Check date format matches template expectations

---

## Context Issues

### "Context overflow warning"

**Symptoms:** `⚠️ CONTEXT WARNING: 75%+ used`

**Causes:**
1. Too many Tier 1 files loaded
2. Files too large
3. Accumulated session history

**Fix:**
1. Reduce Tier 1 scope (focus on one task)
2. Split large files into smaller ones
3. Start fresh session if history bloated

---

### "Wrong files loading"

**Symptoms:** Claude loads irrelevant context

**Causes:**
1. Task type misdetected
2. Tier assignments wrong
3. Required_context misconfigured

**Fix:**
1. Be explicit: "Load [specific file]"
2. Review tier assignments in frontmatter
3. Update task-type mappings in CLAUDE.md

---

### "Claude forgot what we discussed"

**Symptoms:** Claude seems to lose context mid-session

**Causes:**
1. Session too long (context eviction)
2. Information wasn't in loaded files
3. Didn't end session properly last time

**Fix:**
1. End session and resume (reloads cleanly)
2. Document important info in project files
3. Always use End Session protocol

---

## Graph Issues

### "Phantom blockers appearing"

**Symptoms:** Told you're blocked by resolved items

**Causes:**
1. Graph Index not updated after completion
2. Blocker validation skipped
3. Status mismatch between files

**Fix:**
1. Update Graph Index blockers list
2. Run blocker validation: "Validate my blockers"
3. Sync file status with graph status

---

### "Critical path unclear"

**Symptoms:** Can't identify what to work on

**Causes:**
1. Dependencies not declared
2. Goal not defined
3. Graph Index stale

**Fix:**
1. Add `depends_on` and `blocks` to project files
2. Define clear goal in CLAUDE.md
3. Refresh Graph Index

---

### "Relationships not showing"

**Symptoms:** Files exist but aren't connected

**Causes:**
1. Missing YAML frontmatter
2. Wikilinks malformed
3. Not registered in Graph Index

**Fix:**
1. Add frontmatter with relationship fields
2. Use exact format: `"[[File Name]]"`
3. Add file to Graph Index registry

---

## Session Issues

### "End session doesn't save properly"

**Symptoms:** Next session doesn't have saved state

**Causes:**
1. Task-Context-Log missing
2. Interrupted before save complete
3. File write failed

**Fix:**
1. Create Task-Context-Log.md in 00-System
2. Wait for full End Session output
3. Check file was actually written

---

### "Resume doesn't work"

**Symptoms:** "Resume" doesn't load previous state

**Causes:**
1. Didn't end session properly
2. Task-Context-Log empty
3. Different task name used

**Fix:**
1. Use "End Session" to save state
2. Check Task-Context-Log has saved state
3. Use exact task name: "Resume [task name]"

---

### "Session too slow"

**Symptoms:** Long delays between responses

**Causes:**
1. Too much context loaded
2. Large files being processed
3. Complex queries

**Fix:**
1. Reduce loaded context
2. Split large files
3. Simplify requests

---

## Safety System Issues

### "Freshness check always warns"

**Symptoms:** Always see stale warnings

**Causes:**
1. Not updating Graph Index regularly
2. Timestamp not being set
3. Threshold too aggressive

**Fix:**
1. Update Graph Index at end of each session
2. Check `Last Updated` field is set
3. Adjust threshold in protocol if needed

---

### "Too many false positives"

**Symptoms:** Safety checks flag things that aren't problems

**Causes:**
1. Overly strict validation
2. Data format mismatches
3. Edge cases not handled

**Fix:**
1. Review what's being flagged
2. Ensure consistent data formats
3. Adjust validation rules if needed

---

## Performance Issues

### "Vault feels slow"

**Symptoms:** Initialize takes too long

**Causes:**
1. Too many files in vault
2. Large files in Tier 0
3. Complex graph calculations

**Fix:**
1. Archive old content
2. Keep Tier 0 files lean
3. Simplify graph structure

---

### "Can't find files"

**Symptoms:** Claude can't locate referenced files

**Causes:**
1. Files moved or renamed
2. Wikilinks broken
3. Path issues

**Fix:**
1. Update references when moving files
2. Fix broken wikilinks
3. Use consistent file paths

---

## General Fixes

### Nuclear Option: Fresh Start

If vault is too broken to fix:

1. Export any valuable content
2. Delete current vault
3. Start fresh from vault-starter
4. Re-add content gradually

### Debug Mode

Ask Claude:
```
Debug mode: show what you loaded
```

This displays exactly what context Claude has, helping identify mismatches.

### Manual Override

When automation fails:
```
Ignore protocols. Let's just [specific action]
```

Sometimes you need to work around the system while fixing it.

---

## Getting Help

If you can't resolve an issue:

1. Document exactly what happens
2. Note what you expected
3. Share relevant file contents
4. Ask in the community forum
