# 🩹 PROMPTGRAFT Deployment Checklist

Use this checklist to verify your PROMPTGRAFT installation is complete and working.

---

## Pre-Deployment Checklist

### Environment
- [ ] Claude Code is installed and accessible
- [ ] You have a workspace directory ready
- [ ] You have write permissions to create directories

### Source Materials
- [ ] You have a base prompt file to work with
- [ ] You know the current version number (e.g., v1.0)
- [ ] You have a feature in mind to add first
- [ ] You have estimated a character budget

---

## Installation Checklist

### Step 1: Directory Structure
- [ ] Created `promptgraft/` directory
- [ ] Created `promptgraft/promptgraft-internals/` directory
- [ ] Created `promptgraft/promptgraft-internals/prompts/` directory
- [ ] Created `promptgraft/base/` directory
- [ ] Created `promptgraft/briefs/` directory
- [ ] Created `promptgraft/blueprints/` directory
- [ ] Created `promptgraft/output/` directory

**Verify with:**
```bash
tree promptgraft/
# Should show all 7 directories
```

### Step 2: Specialist Prompts
- [ ] `orchestrator.md` in `promptgraft-internals/prompts/`
- [ ] `architect.md` in `promptgraft-internals/prompts/`
- [ ] `surgeon.md` in `promptgraft-internals/prompts/`
- [ ] `auditor.md` in `promptgraft-internals/prompts/`
- [ ] `executor.md` in `promptgraft-internals/prompts/`
- [ ] `inspector.md` in `promptgraft-internals/prompts/`
- [ ] `chronicler.md` in `promptgraft-internals/prompts/`

**Verify with:**
```bash
ls promptgraft/promptgraft-internals/prompts/
# Should list 7 .md files
```

### Step 3: Base Version
- [ ] Copied your current prompt to `promptgraft/base/`
- [ ] Named it with version number (e.g., `v1.0.txt`)
- [ ] File is complete and readable
- [ ] No corruption or encoding issues

**Verify with:**
```bash
wc -c promptgraft/base/v1.0.txt
# Should show character count
```

---

## First Run Checklist

### Initialization Test

**Command:**
```
promptgraft status
```

**Expected Output:**
```
📊 PROMPTGRAFT STATUS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pipeline: IDLE
No active pipeline.

Use: promptgraft new <feature> <base> <target> --budget=<N>
```

- [ ] Status command works
- [ ] Shows "IDLE" state
- [ ] Suggests next action

### First Feature Test

**Command:**
```
promptgraft new "Test Feature" v1.0 v1.1 --budget=200
```

**Expected Behavior:**
- [ ] Claude reads orchestrator prompt (you pasted it)
- [ ] Claude creates/reads state.json
- [ ] Claude loads architect.md
- [ ] Claude reads base/v1.0.txt
- [ ] Claude generates strategic brief
- [ ] Claude saves to briefs/architect-brief-v1.1.md
- [ ] Claude updates state.json
- [ ] Claude outputs success message

**Verify with:**
```bash
# Check state was created
cat promptgraft/promptgraft-internals/state.json

# Check brief was created
ls promptgraft/briefs/
```

### Continue Through Pipeline

**Command:**
```
promptgraft continue
```

**Run this 5 more times** (once per stage).

**Expected Final State:**
- [ ] All 6 stages completed
- [ ] No errors encountered
- [ ] Files created:
  - [ ] `briefs/architect-brief-v1.1.md`
  - [ ] `blueprints/implementation-v1.1.md`
  - [ ] `output/v1.1.txt`
  - [ ] `output/release-notes-v1.1.md`

**Verify with:**
```bash
tree promptgraft/
# Should show all generated files
```

---

## Validation Checklist

### File Integrity

**Check each generated file:**

#### Architect Brief
```bash
cat promptgraft/briefs/architect-brief-v1.1.md
```
- [ ] Contains feature name
- [ ] Has architectural approach
- [ ] Lists integration zones
- [ ] Recommends budget
- [ ] Well-formatted markdown

#### Implementation Blueprint
```bash
cat promptgraft/blueprints/implementation-v1.1.md
```
- [ ] Has "INSERTION" blocks
- [ ] Each has "Find:", "Position:", "Add exactly:"
- [ ] Character counts specified
- [ ] Total budget calculated
- [ ] Well-formatted markdown

#### Output Artifact
```bash
cat promptgraft/output/v1.1.txt
```
- [ ] File is complete (not truncated)
- [ ] Contains base content
- [ ] Contains new feature
- [ ] No placeholders like "[TBD]"
- [ ] Version number updated

#### Release Notes
```bash
cat promptgraft/output/release-notes-v1.1.md
```
- [ ] Has version number
- [ ] Describes feature
- [ ] Lists integration points (if dev audience)
- [ ] Includes changelog entry
- [ ] Well-formatted markdown

### Character Count Verification

**Manual verification:**
```bash
# Base version size
wc -c promptgraft/base/v1.0.txt

# New version size
wc -c promptgraft/output/v1.1.txt

# Difference should match blueprint
```

- [ ] New version is larger than base
- [ ] Difference ≈ budget specified
- [ ] No massive overruns (>110% of budget)

### State File Verification

```bash
cat promptgraft/promptgraft-internals/state.json
```

- [ ] Valid JSON (no syntax errors)
- [ ] `status` is "complete"
- [ ] `feature_name` matches what you entered
- [ ] `current_stage` is 6
- [ ] `stage_history` has 6 entries
- [ ] All file paths are correct

---

## Functional Testing Checklist

### Test 1: Status Command
```bash
promptgraft status
```
- [ ] Shows "COMPLETE" status
- [ ] Lists completed stages
- [ ] Shows generated file paths

### Test 2: Reset Command
```bash
promptgraft reset
promptgraft status
```
- [ ] State resets to "IDLE"
- [ ] Files remain (not deleted)
- [ ] Ready for new pipeline

### Test 3: Second Feature
```bash
promptgraft new "Second Feature" v1.1 v1.2 --budget=300
promptgraft continue  # Run until complete
```
- [ ] Uses v1.1 as base (builds on first feature)
- [ ] Creates new files:
  - [ ] `briefs/architect-brief-v1.2.md`
  - [ ] `blueprints/implementation-v1.2.md`
  - [ ] `output/v1.2.txt`
  - [ ] `output/release-notes-v1.2.md`
- [ ] v1.2 contains BOTH features

### Test 4: Error Recovery
```bash
# Intentionally give impossible budget
promptgraft new "Complex Feature" v1.2 v1.3 --budget=50
```
- [ ] Surgeon reports budget infeasible
- [ ] System doesn't crash
- [ ] Provides actionable recommendation
- [ ] Can reset and retry with higher budget

---

## Production Readiness Checklist

### Documentation
- [ ] README.md is available
- [ ] Quick Start guide is available
- [ ] All specialist prompts are documented
- [ ] Example workflows are provided

### Backup Strategy
- [ ] Plan for backing up `promptgraft/` directory
- [ ] Version control for base versions
- [ ] Archiving old briefs/blueprints

### Workflow Established
- [ ] Team knows how to use PROMPTGRAFT
- [ ] Feature request → budget estimation process defined
- [ ] Code review process for generated artifacts
- [ ] Deployment process for new versions

### Monitoring
- [ ] Method to track pipeline success rate
- [ ] Process for handling failed stages
- [ ] Escalation path for persistent issues

---

## Common Issues & Solutions

### Issue: "Orchestrator doesn't respond"

**Cause:** Orchestrator prompt not loaded

**Solution:**
- [ ] Copy ENTIRE `orchestrator.md` content
- [ ] Paste into Claude Code
- [ ] Wait for initialization message
- [ ] Then give command

### Issue: "File not found" errors

**Cause:** Wrong version number in command

**Solution:**
- [ ] Check actual filename: `ls promptgraft/base/`
- [ ] Match version exactly: `v1.0.txt` → use `v1.0` in command
- [ ] Check for typos

### Issue: "Invalid JSON" in state.json

**Cause:** Manual editing broke JSON syntax

**Solution:**
- [ ] Run `promptgraft reset`
- [ ] Or fix JSON manually
- [ ] Or delete state.json (will recreate)

### Issue: Pipeline stuck, won't continue

**Cause:** State corruption or unexpected error

**Solution:**
- [ ] Check `promptgraft status`
- [ ] Review last stage's output files
- [ ] Try `promptgraft reset` and restart
- [ ] Check Claude Code logs for errors

---

## Performance Benchmarks

### Expected Timings
- **Architect:** 10-30 seconds
- **Surgeon:** 30-60 seconds
- **Auditor:** 10-30 seconds
- **Executor:** 5-15 seconds
- **Inspector:** 10-30 seconds
- **Chronicler:** 15-30 seconds

**Total pipeline:** ~2-4 minutes per feature

If times are significantly longer:
- [ ] Check base version file size (large files take longer)
- [ ] Check budget size (larger budgets = more reasoning)
- [ ] Verify Claude Code connection is stable

---

## Final Verification

**If ALL checklists pass:**

```
✅ PROMPTGRAFT IS READY FOR PRODUCTION

You can now:
- Add features with surgical precision
- Maintain strict character budgets
- Generate documentation automatically
- Track changes through version control
- Scale to multiple developers

Next: Start building features!
```

**If ANY checklist fails:**

```
⚠️ ISSUES DETECTED

Review failed items above and:
1. Fix directory structure issues
2. Verify all prompts are in place
3. Test with simple feature first
4. Check documentation for help

Don't proceed to production until all checks pass.
```

---

## Support Resources

- **Full Documentation:** `README.md`
- **Quick Start:** Quick Start Guide
- **Specialist Details:** Individual prompt files in `promptgraft-internals/prompts/`
- **State Inspection:** `cat promptgraft-internals/state.json`
- **File Structure:** `tree promptgraft/`

---

## Deployment Sign-Off

**Date:** _______________
**Deployed By:** _______________
**Version:** PROMPTGRAFT v1.0
**Status:** [ ] Ready / [ ] Not Ready

**Notes:**
________________________________
________________________________
________________________________

**Approved By:** _______________