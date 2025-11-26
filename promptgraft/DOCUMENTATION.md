# 🩹 PROMPTGRAFT
**Surgical Feature Grafting for Prompts**

A pure LLM-based development pipeline for adding features to prompt artifacts with surgical precision and strict budget adherence.

---

## Overview

PROMPTGRAFT is a file-based, stateful orchestration system that coordinates specialist AI agents to implement new features in prompt-based systems (like character cards, system prompts, etc.) without exceeding character budgets.

### Key Principles

- **Surgical Precision:** Every character counts, nothing wasted
- **Budget Discipline:** Hard character limits are never exceeded
- **Quality Gates:** Multiple verification stages catch errors
- **File-Based:** Works with Claude Code's filesystem
- **Stateful:** Tracks progress, enables recovery
- **Pure LLM:** No code required, just prompts and reasoning

---

## System Architecture

```
┌─────────────┐
│ ORCHESTRATOR│  ← Main coordinator (reads state, delegates)
└──────┬──────┘
       │
       ├─→ 🏗️  ARCHITECT    (Strategic planning)
       ├─→ 🔬  SURGEON      (Detailed implementation)
       ├─→ 🔍  AUDITOR      (Functional QA)
       ├─→ ⚙️  EXECUTOR     (Mechanical assembly)
       ├─→ ✔️  INSPECTOR    (Fidelity verification)
       └─→ 📝  CHRONICLER   (Documentation)
```

---

## Directory Structure

```
workspace/
└── promptgraft/
    ├── .promptgraft/
    │   ├── state.json                    # Pipeline state tracker
    │   └── prompts/                      # Specialist prompt library
    │       ├── architect.md
    │       ├── surgeon.md
    │       ├── auditor.md
    │       ├── executor.md
    │       ├── inspector.md
    │       └── chronicler.md
    ├── base/                             # Source versions
    │   ├── v30.3.txt
    │   └── v30.4.txt
    ├── briefs/                           # Architect outputs
    │   ├── architect-brief-v30.4.md
    │   └── architect-brief-v30.5.md
    ├── blueprints/                       # Surgeon outputs
    │   ├── implementation-v30.4.md
    │   └── implementation-v30.5.md
    └── output/                           # Final artifacts
        ├── v30.4.txt
        ├── v30.5.txt
        ├── release-notes-v30.4.md
        └── release-notes-v30.5.md
```

---

## Installation & Setup

### Step 1: Create Directory Structure

```bash
mkdir -p promptgraft/{.promptgraft/prompts,base,briefs,blueprints,output}
```

### Step 2: Install Specialist Prompts

Place all specialist prompt files in `promptgraft/.promptgraft/prompts/`:

- `architect.md` - Strategic planner
- `surgeon.md` - Implementation planner
- `auditor.md` - Functional QA
- `executor.md` - Mechanical assembler
- `inspector.md` - Post-execution verifier
- `chronicler.md` - Documentation generator

### Step 3: Add Base Version

Place your current prompt version in `promptgraft/base/`:

```bash
cp my-current-prompt.txt promptgraft/base/v1.0.txt
```

### Step 4: Initialize State (Optional)

The Orchestrator will create `state.json` automatically on first run, but you can initialize it manually:

```json
{
  "pipeline": {
    "status": "idle",
    "feature_name": null,
    "base_version": null,
    "target_version": null,
    "character_budget": null,
    "current_stage": 0,
    "total_stages": 6,
    "created_at": null,
    "updated_at": null
  },
  "files": {
    "base": null,
    "brief": null,
    "blueprint": null,
    "artifact": null
  },
  "stage_history": []
}
```

---

## Usage

### Command Reference

```bash
# Start a new feature pipeline
promptgraft new "Feature Name" v1.0 v1.1 --budget=400

# Continue to next stage
promptgraft continue

# Check current status
promptgraft status

# Reset pipeline
promptgraft reset

# Jump to specific stage (advanced)
promptgraft architect "Feature Name" v1.0 v1.1
promptgraft plan --brief=architect-brief-v1.1.md --budget=400
promptgraft audit --blueprint=implementation-v1.1.md
promptgraft build --blueprint=implementation-v1.1.md --base=v1.0.txt
promptgraft verify --blueprint=implementation-v1.1.md --artifact=v1.1.txt --base=v1.0.txt
promptgraft docs --blueprint=implementation-v1.1.md --audience=all
```

---

## Complete Workflow Example

### Scenario: Adding "Verbal Stumbles" Feature

**Budget:** 384 characters
**Base Version:** v30.3
**Target Version:** v30.4

### Step 1: Initiate Pipeline

```bash
promptgraft new "Verbal Stumbles" v30.3 v30.4 --budget=384
```

**Output:**
```
🏗️ ARCHITECT STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Feature: Verbal Stumbles
Approach: Pure integration, extending TEXT AUTHENTICITY
Recommended Budget: 350 characters
Your Budget: 384 characters ✅

Strategic brief saved to:
promptgraft/briefs/architect-brief-v30.4.md

Next: promptgraft continue (to Surgeon)
```

### Step 2: Continue to Surgeon

```bash
promptgraft continue
```

**Output:**
```
🔬 SURGEON STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Budget: 384/384 characters (100%)
Integration Points: 4
Blueprint saved to:
promptgraft/blueprints/implementation-v30.4.md

Next: promptgraft continue (to Auditor)
```

### Step 3: Continue to Auditor

```bash
promptgraft continue
```

**Output:**
```
🔍 AUDITOR STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Verdict: ✅ PASS
The blueprint is functionally complete.

Next: promptgraft continue (to Executor)
```

### Step 4: Continue to Executor

```bash
promptgraft continue
```

**Output:**
```
⚙️ EXECUTOR STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Artifact generated: v30.4
Output saved to:
promptgraft/output/v30.4.txt

Next: promptgraft continue (to Inspector)
```

### Step 5: Continue to Inspector

```bash
promptgraft continue
```

**Output:**
```
✔️ INSPECTOR STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Verdict: ✅ APPROVED
- Fidelity: PASS
- Functionality: PASS

Artifact ready for release!

Next: promptgraft continue (to generate docs)
```

### Step 6: Continue to Chronicler

```bash
promptgraft continue
```

**Output:**
```
📝 CHRONICLER STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Documentation generated for: All audiences
Release notes saved to:
promptgraft/output/release-notes-v30.4.md

🎉 PIPELINE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Feature: Verbal Stumbles
Version: v30.4 ✅
Artifact: promptgraft/output/v30.4.txt
Docs: promptgraft/output/release-notes-v30.4.md

Pipeline complete! Start new feature: promptgraft new
```

---

## State Management

### State File Schema

```json
{
  "pipeline": {
    "status": "architect|surgeon|auditor|executor|inspector|chronicler|complete|idle",
    "feature_name": "string",
    "base_version": "string (e.g., v30.3)",
    "target_version": "string (e.g., v30.4)",
    "character_budget": "number",
    "current_stage": "number (1-6)",
    "total_stages": 6,
    "created_at": "ISO timestamp",
    "updated_at": "ISO timestamp"
  },
  "files": {
    "base": "relative path",
    "brief": "relative path",
    "blueprint": "relative path",
    "artifact": "relative path"
  },
  "stage_history": [
    {
      "stage": "string",
      "status": "complete|failed",
      "timestamp": "ISO timestamp"
    }
  ]
}
```

### Checking Status

```bash
promptgraft status
```

**Output:**
```
📊 PROMPTGRAFT STATUS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pipeline: ACTIVE
Feature: Verbal Stumbles
Version: v30.3 → v30.4
Budget: 384 characters

Stage Progress:
✅ 1. Architect   (complete)
✅ 2. Surgeon     (complete)
🔄 3. Auditor     (in progress)
⏳ 4. Executor
⏳ 5. Inspector
⏳ 6. Chronicler

Files:
📁 Base:      promptgraft/base/v30.3.txt
📁 Brief:     promptgraft/briefs/architect-brief-v30.4.md
📁 Blueprint: promptgraft/blueprints/implementation-v30.4.md
📁 Output:    (pending)

Next Action:
promptgraft continue
```

---

## Pipeline Stages

### 1. 🏗️ ARCHITECT (Strategic Planning)

**Input:**
- Base version file
- Feature name
- Version identifiers

**Output:**
- `promptgraft/briefs/architect-brief-v[TARGET].md`

**Purpose:**
- High-level architectural design
- Integration zone identification
- Budget recommendation
- Risk assessment

**Typical Duration:** Fast (1 analysis)

---

### 2. 🔬 SURGEON (Detailed Implementation Planning)

**Input:**
- Architect's strategic brief
- Base version file
- Character budget (hard limit)

**Output:**
- `promptgraft/blueprints/implementation-v[TARGET].md`

**Purpose:**
- Precise insertion point specification
- Exact text to add at each location
- Character count for every addition
- Budget verification

**Typical Duration:** Medium (detailed planning)

---

### 3. 🔍 AUDITOR (Functional QA)

**Input:**
- Implementation blueprint

**Output:**
- PASS (no file) or FAIL (corrected blueprint)

**Purpose:**
- Find functional gaps
- Verify logic completeness
- Check for unreachable code
- Validate integration paths

**Typical Duration:** Fast (logical analysis)

---

### 4. ⚙️ EXECUTOR (Mechanical Assembly)

**Input:**
- Implementation blueprint
- Base version file

**Output:**
- `promptgraft/output/v[TARGET].txt`

**Purpose:**
- Execute insertions with zero creativity
- Follow blueprint exactly
- Verify character counts
- Produce complete artifact

**Typical Duration:** Fast (mechanical copy-paste)

---

### 5. ✔️ INSPECTOR (Post-Execution Verification)

**Input:**
- Implementation blueprint
- Generated artifact
- Base version (for comparison)

**Output:**
- APPROVED / EXECUTION FAILURE / BLUEPRINT FLAW

**Purpose:**
- Verify blueprint fidelity
- Check functional integrity
- Validate character counts
- Detect unauthorized changes

**Typical Duration:** Fast (comparison analysis)

---

### 6. 📝 CHRONICLER (Documentation)

**Input:**
- Implementation blueprint
- Target audience

**Output:**
- `promptgraft/output/release-notes-v[TARGET].md`

**Purpose:**
- Generate release notes
- Create changelog entries
- Document implementation
- Explain changes to users/developers

**Typical Duration:** Fast (document generation)

---

## Error Handling & Recovery

### Execution Failure (Executor didn't follow blueprint)

**Symptom:**
```
✔️ INSPECTOR STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Verdict: ❌ EXECUTION FAILURE

Issue: Character count mismatch
Expected: 12,384 chars
Actual: 13,813 chars
```

**Recovery:**
```bash
promptgraft continue  # Automatically retries Executor
```

**What happens:**
- State resets to `status = "executor"`
- Executor runs again with strict instructions
- Blueprint remains unchanged

---

### Blueprint Flaw (Auditor missed a gap)

**Symptom:**
```
✔️ INSPECTOR STAGE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Verdict: 🔧 BLUEPRINT FLAW

Issue: Feature is unreachable (no trigger)
```

**Recovery:**
```bash
# State automatically resets to Surgeon stage
promptgraft continue  # Creates revised blueprint
```

**What happens:**
- State resets to `status = "surgeon"`
- Surgeon revises blueprint with Inspector feedback
- Pipeline continues from Auditor

---

### Budget Overrun (Surgeon can't fit feature)

**Symptom:**
```
⚠️ BUDGET INFEASIBLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Feature: Complex Feature
Budget: 200 characters
Required: ~450 characters
```

**Recovery:**
```bash
# Option 1: Increase budget
promptgraft new "Complex Feature" v1.0 v1.1 --budget=500

# Option 2: Simplify scope
# (Manually adjust feature requirements)

# Option 3: Split into multiple versions
promptgraft new "Complex Feature Part 1" v1.0 v1.1 --budget=200
```

---

## Best Practices

### 1. Budget Estimation

**Conservative approach:**
- Low complexity: 100-300 characters
- Medium complexity: 300-600 characters
- High complexity: 600-1000 characters

**Add 10-20% safety margin** for unexpected formatting.

### 2. Feature Scope

**Good scope (fits in one version):**
- Single new state
- One trigger addition
- Small behavioral tweak
- Minor example update

**Bad scope (too large):**
- Complete system redesign
- Multiple new abstractions
- Many interconnected features

**When in doubt:** Split into multiple versions.

### 3. Base Version Management

**Keep organized:**
- One file per version
- Clear version numbering (semantic versioning)
- Never modify base versions after creation
- Archive old versions for reference

### 4. Character Budget Strategy

**Budget allocation:**
- 60% for primary feature
- 20% for examples/demonstrations
- 10% for integration glue
- 10% for safety margin

**Don't:**
- Spend entire budget on documentation
- Skimp on examples
- Forget about version number changes

### 5. Reviewing Outputs

**After Architect:**
- Verify the approach makes sense
- Confirm budget recommendation is reasonable
- Check that integration zones are appropriate

**After Surgeon:**
- Review blueprint for completeness
- Verify character counts add up
- Check that all insertions are justified

**After Inspector:**
- If APPROVED: Trust it, move forward
- If FAILURE: Let system retry automatically
- If BLUEPRINT FLAW: Review root cause

---

## Troubleshooting

### Problem: "Find string not found"

**Cause:** Executor can't locate the text specified in blueprint

**Solution:**
- Verify base version is correct
- Check that blueprint "Find:" text is exact
- Ensure no typos in blueprint

### Problem: "Character count mismatch"

**Cause:** Executor added more/less than specified

**Solution:**
- Let Inspector catch it (automatic)
- System will retry with stricter instructions
- If persists, check for hidden characters

### Problem: "Blueprint has functional gaps"

**Cause:** Auditor found incomplete logic

**Solution:**
- System automatically corrects (Auditor creates fixed blueprint)
- If corrections exceed budget, increase budget
- If corrections break design, revise feature scope

### Problem: "Pipeline stuck at stage X"

**Cause:** State file corruption or error

**Solution:**
```bash
# Check state
promptgraft status

# Reset if corrupted
promptgraft reset

# Restart pipeline
promptgraft new "Feature" vX vY --budget=Z
```

---

## Advanced Usage

### Partial Pipeline Execution

Skip stages if you have pre-existing files:

```bash
# Already have strategic brief, jump to Surgeon
promptgraft plan --brief=my-brief.md --budget=400

# Already have blueprint, jump to Executor
promptgraft build --blueprint=my-blueprint.md --base=v1.0.txt

# Already have artifact, jump to Inspector
promptgraft verify --blueprint=my-blueprint.md --artifact=v1.1.txt --base=v1.0.txt
```

### Custom Audience Documentation

```bash
# Generate user-facing docs only
promptgraft docs --blueprint=implementation-v1.1.md --audience=users

# Generate developer docs only
promptgraft docs --blueprint=implementation-v1.1.md --audience=developers

# Generate comprehensive docs
promptgraft docs --blueprint=implementation-v1.1.md --audience=all
```

### Batch Processing Multiple Features

```bash
# Feature 1
promptgraft new "Feature A" v1.0 v1.1 --budget=300
promptgraft continue  # Run through pipeline

# Feature 2
promptgraft new "Feature B" v1.1 v1.2 --budget=400
promptgraft continue  # Run through pipeline

# Feature 3
promptgraft new "Feature C" v1.2 v1.3 --budget=250
promptgraft continue  # Run through pipeline
```

**Note:** Each feature builds on the previous version's output.

---

## System Guarantees

### ✅ What PROMPTGRAFT Guarantees

1. **Budget Adherence:** Character budgets are never exceeded
2. **Fidelity:** Executor follows blueprints exactly
3. **Quality:** Multiple verification gates catch errors
4. **Traceability:** Complete audit trail in state.json
5. **Recoverability:** Failed stages can be retried
6. **Documentation:** Release notes always generated

### ⚠️ What PROMPTGRAFT Does NOT Guarantee

1. **Feature Quality:** System executes plans, doesn't evaluate feature value
2. **Optimal Design:** Architects make best effort, not perfect decisions
3. **Bug-Free Output:** Functional gaps can exist if Auditor misses them
4. **Performance:** No optimization for execution speed
5. **Backward Compatibility:** Features may introduce breaking changes

---

## Contributing

### Adding New Specialists

1. Create prompt file in `promptgraft/.promptgraft/prompts/`
2. Follow file-based I/O conventions
3. Update Orchestrator to invoke new specialist
4. Document in README

### Improving Existing Specialists

1. Maintain file I/O compatibility
2. Preserve output format contracts
3. Update version numbers in specialist prompts
4. Test with example feature before committing

---

## License

[Your License Here]

---

## Credits

**Developed by:** [Your Name]
**System Architecture:** Pure LLM orchestration
**Inspired by:** Surgical development practices and budget-constrained engineering

---

**PROMPTGRAFT** - "Every feature grafted with surgical precision" 🩹