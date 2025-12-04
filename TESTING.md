# Business Vault OS - Testing Guide

> Verification checklist to confirm each feature works correctly.

---

## How to Use This Guide

Work through each test in order. Mark tests as you complete them.
If a test fails, check the troubleshooting section for that feature.

---

## Test Suite 1: Core Setup

### Test 1.1: CLAUDE.md Loads

**Action:** Start Claude Code session in vault. Type `Initialize`

**Expected:**
- [ ] Claude acknowledges reading CLAUDE.md
- [ ] Business name appears in response
- [ ] No errors about missing files

**If Failed:**
- Verify CLAUDE.md is in vault root
- Check YAML frontmatter syntax
- Verify file is not empty

---

### Test 1.2: Graph Index Loads

**Action:** During Initialize, watch for Graph Index reference

**Expected:**
- [ ] Claude mentions reading Graph Index
- [ ] Blocker count mentioned
- [ ] Critical path referenced

**If Failed:**
- Verify `00-System/Graph Index.md` exists
- Check file has valid frontmatter
- Verify Last Sync field exists

---

### Test 1.3: Brain Dump Accessible

**Action:** Ask `What's in my brain dump?`

**Expected:**
- [ ] Claude reads Brain Dump Master
- [ ] Lists pending items
- [ ] Shows overwhelm indicator (if configured)

**If Failed:**
- Verify `00-System/Brain Dump Master.md` exists
- Check file has items listed
- Verify frontmatter is valid

---

## Test Suite 2: Session Lifecycle

### Test 2.1: Initialize Produces Summary

**Action:** Fresh session, type `Initialize`

**Expected:**
- [ ] Business state summary appears
- [ ] Current blockers listed
- [ ] THE ONE THING recommended
- [ ] Context verification displayed

**If Failed:**
- Check CLAUDE.md Initialize protocol section
- Verify all Tier 0 files exist
- Review error messages

---

### Test 2.2: Session End Captures State

**Action:** Do some work, then type `End session`

**Expected:**
- [ ] Session summary generated
- [ ] Duration/progress noted
- [ ] Tomorrow's priority set
- [ ] Files updated list shown

**If Failed:**
- Check if session had meaningful work to capture
- Verify write permissions on files
- Try shorter session first

---

### Test 2.3: Task Context Saves

**Action:**
1. Start working on task
2. Type `End session` mid-task
3. New session, type `Initialize`

**Expected:**
- [ ] Previous task state mentioned
- [ ] "Resume from" option offered
- [ ] Context preserved between sessions

**If Failed:**
- Verify Task-Context-Log exists
- Check if task was significant enough to save
- May need to configure Task-Context-Log

---

## Test Suite 3: Knowledge Graph

### Test 3.1: Dependency Query

**Action:** `What depends on [File X]?` (use real file name)

**Expected:**
- [ ] Lists files that depend on X
- [ ] Shows downstream impact
- [ ] Indicates blocker severity

**If Failed:**
- Verify file X has `blocks:` field populated
- Check Graph Index has relationships mapped
- Verify wikilink format is correct

---

### Test 3.2: Blocker Query

**Action:** `What's blocked right now?`

**Expected:**
- [ ] Lists all files with blockers
- [ ] Shows what's blocking each
- [ ] Prioritizes by severity/impact

**If Failed:**
- Verify files have `blockers:` arrays
- Check Graph Index "Current Blockers" section
- May need to add blocker information

---

### Test 3.3: Critical Path Query

**Action:** `What's the critical path to [your goal]?`

**Expected:**
- [ ] Shows sequence of steps
- [ ] Indicates current position
- [ ] Highlights next action

**If Failed:**
- Verify Graph Index has Critical Path section
- Check dependencies are mapped correctly
- Goal must be specific and documented

---

## Test Suite 4: Safety Protocols

### Test 4.1: Freshness Verification

**Setup:** Manually change Graph Index Last Sync to 24+ hours ago

**Action:** `What should I work on today?`

**Expected:**
- [ ] Claude notices stale graph
- [ ] Warning displayed about staleness
- [ ] Offers to update before recommending

**Cleanup:** Reset Last Sync to current time

**If Failed:**
- Verify Freshness protocol is in CLAUDE.md
- Check staleness thresholds in protocol
- Protocol may need to be added from templates

---

### Test 4.2: Blocker Validation

**Setup:** Mark a file as blocked in Graph Index, but update the blocking file to "completed"

**Action:** `What's blocking my progress?`

**Expected:**
- [ ] Claude checks actual file status
- [ ] Notices phantom blocker
- [ ] Suggests updating graph

**Cleanup:** Restore original status

**If Failed:**
- Verify Blocker Validation protocol exists
- Check protocol is referenced in CLAUDE.md
- Protocol may need to be added from templates

---

### Test 4.3: Truth-First Quote-Back

**Action:** Have a conversation, then ask `What did I say about X?`

**Expected:**
- [ ] Claude quotes actual text (not paraphrase)
- [ ] If can't find, admits it
- [ ] Doesn't make up quotes

**If Failed:**
- Verify Truth-First Protocol exists
- Check it's in Tier 0 load list
- May be a model behavior issue (not fixable via system)

---

## Test Suite 5: Token Management

### Test 5.1: Context Status Display

**Action:** `Context status`

**Expected:**
- [ ] Token estimate shown
- [ ] Tier breakdown displayed
- [ ] Files loaded listed

**If Failed:**
- Verify Session Management Protocol exists
- Check token tracking is configured
- May need to add protocol from templates

---

### Test 5.2: Warning Thresholds

**Note:** This requires a long session to hit thresholds naturally.

**Expected behavior at thresholds:**
- [ ] 60%: Notice displayed
- [ ] 75%: Warning with recommendation
- [ ] 90%: Strong warning to end session

**If not seeing warnings:**
- Check if thresholds are configured
- May need longer sessions to test
- Protocol may need adjustment for your usage

---

## Test Suite 6: Daily Operations

### Test 6.1: Daily Note Integration

**Action:** On a day with no daily note, run Initialize before 6pm

**Expected:**
- [ ] Daily note auto-created (if configured)
- [ ] Uses Daily Note Template
- [ ] Correct date in filename

**If Failed:**
- Verify Daily Note Template exists in 00-System/
- Check auto-creation is in Initialize protocol
- May need to add this feature

---

### Test 6.2: Brain Dump Processing

**Action:** Add items to Brain Dump, then ask `Process my brain dump`

**Expected:**
- [ ] Items categorized
- [ ] Tasks routed appropriately
- [ ] Clear items offered for archival

**If Failed:**
- Verify Brain Dump Processing Protocol exists
- Check Brain Dump Master has items
- Protocol may need to be added from templates

---

## Scoring Your Setup

Count your passed tests:

| Score | Status | Recommendation |
|-------|--------|----------------|
| 18-20 | Excellent | System fully operational |
| 14-17 | Good | Core features working, polish optional |
| 10-13 | Functional | Basics work, add missing protocols |
| <10 | Needs Work | Review setup guide, check file structure |

---

## Next Steps After Testing

1. **All tests pass:** Start using daily, iterate based on experience
2. **Some tests fail:** Add missing protocols from templates
3. **Many tests fail:** Re-do setup from scratch using setup guide
