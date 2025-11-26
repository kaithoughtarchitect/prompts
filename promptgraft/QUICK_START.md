# 🩹 PROMPTGRAFT Quick Start Guide
**For Claude Code**

This guide gets you up and running with PROMPTGRAFT in 5 minutes.

---

## What You Need

1. **Claude Code** installed and working
2. **A prompt file** you want to add features to
3. **5 minutes** for setup

---

## 1. Setup (One-Time)

### Create Directory Structure

In your Claude Code workspace, run:

```bash
mkdir -p promptgraft/.promptgraft/prompts
mkdir -p promptgraft/{base,briefs,blueprints,output}
```

### Copy Specialist Prompts

Download these 7 files and place them in `promptgraft/.promptgraft/prompts/`:

```
promptgraft/
└── .promptgraft/
    └── prompts/
        ├── architect.md        ← Strategic planner
        ├── surgeon.md          ← Implementation planner
        ├── auditor.md          ← Functional QA
        ├── executor.md         ← Mechanical assembler
        ├── inspector.md        ← Post-execution verifier
        └── chronicler.md       ← Documentation generator
```

### Add Your Base Version

Copy your current prompt to the base folder:

```bash
cp my-prompt.txt promptgraft/base/v1.0.txt
```

**Done!** You're ready to use PROMPTGRAFT.

---

## 2. Using PROMPTGRAFT

### Basic Usage Pattern

```
1. Talk to Claude Code
2. Paste the Orchestrator prompt
3. Give a command
4. Claude does everything
```

### Step-by-Step Example

#### Step 1: Open Claude Code

```bash
claude code
```

#### Step 2: Paste the Orchestrator Prompt

Copy the **ENTIRE** `orchestrator.md` file and paste it into Claude Code.

This tells Claude it's now the PROMPTGRAFT Orchestrator.

#### Step 3: Give a Command

```
promptgraft new "Verbal Stumbles" v1.0 v1.1 --budget=400
```

#### Step 4: Watch It Work

Claude will:
- Read `state.json` (or create it)
- Load the Architect specialist prompt
- Read your base version `v1.0.txt`
- Analyze and create strategic brief
- Save to `promptgraft/briefs/architect-brief-v1.1.md`
- Ask you to continue

#### Step 5: Continue Through Stages

```
promptgraft continue
```

Keep running this command until pipeline completes!

---

## 3. Complete Example Session

### Session Transcript

```
YOU: [Paste entire orchestrator.md prompt]

CLAUDE: 🩹 PROMPTGRAFT INITIALIZED
        Ready to coordinate pipeline...

YOU: promptgraft new "False Starts" v1.0 v1.1 --budget=350

CLAUDE: 🏗️ ARCHITECT STAGE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Feature: False Starts
        Approach: Pure integration
        Budget: 350 chars ✅

        Strategic brief saved to:
        promptgraft/briefs/architect-brief-v1.1.md

        Next: promptgraft continue

YOU: promptgraft continue

CLAUDE: 🔬 SURGEON STAGE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Budget: 350/350 characters (100%)
        Integration Points: 3

        Blueprint saved to:
        promptgraft/blueprints/implementation-v1.1.md

        Next: promptgraft continue

YOU: promptgraft continue

CLAUDE: 🔍 AUDITOR STAGE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Verdict: ✅ PASS
        Blueprint is functionally complete.

        Next: promptgraft continue

YOU: promptgraft continue

CLAUDE: ⚙️ EXECUTOR STAGE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Artifact generated: v1.1
        Output saved to:
        promptgraft/output/v1.1.txt

        Next: promptgraft continue

YOU: promptgraft continue

CLAUDE: ✔️ INSPECTOR STAGE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Verdict: ✅ APPROVED
        Fidelity: PASS
        Functionality: PASS

        Next: promptgraft continue

YOU: promptgraft continue

CLAUDE: 📝 CHRONICLER STAGE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Documentation generated

        🎉 PIPELINE COMPLETE
        ━━━━━━━━━━━━━━━━━━━━━━━━
        Version: v1.1 ✅
        Artifact: promptgraft/output/v1.1.txt
        Docs: promptgraft/output/release-notes-v1.1.md
```

---

## 4. What Gets Created

After a successful pipeline run, you'll have:

```
promptgraft/
├── .promptgraft/
│   ├── state.json                      ← Pipeline state
│   └── prompts/                        ← [7 prompt files]
├── base/
│   └── v1.0.txt                        ← Your original
├── briefs/
│   └── architect-brief-v1.1.md         ← Strategic plan
├── blueprints/
│   └── implementation-v1.1.md          ← Detailed instructions
└── output/
    ├── v1.1.txt                        ← NEW VERSION! ✨
    └── release-notes-v1.1.md           ← Documentation
```

**Your new version is ready:** `promptgraft/output/v1.1.txt`

---

## 5. Common Commands

### Check Status
```
promptgraft status
```

Shows where you are in the pipeline.

### Reset Pipeline
```
promptgraft reset
```

Clears state, starts fresh.

### Continue to Next Stage
```
promptgraft continue
```

Advances one stage. **Use this most often!**

---

## 6. Tips & Tricks

### Tip 1: Always Check Status
If you're not sure where you are:
```
promptgraft status
```

### Tip 2: Use Conservative Budgets
Start small (100-300 chars) for first features.

### Tip 3: Let the System Retry
If Inspector finds an error, just run:
```
promptgraft continue
```
The system fixes itself!

### Tip 4: Review Intermediate Files
After Architect, check the brief:
```
cat promptgraft/briefs/architect-brief-v1.1.md
```

After Surgeon, check the blueprint:
```
cat promptgraft/blueprints/implementation-v1.1.md
```

### Tip 5: Keep Base Versions Clean
Never edit files in `promptgraft/base/` - they're historical records!

---

## 7. Troubleshooting

### Problem: "File not found"

**Cause:** Base version missing or wrong path

**Solution:**
```bash
# Check if file exists
ls promptgraft/base/

# Make sure filename matches command
promptgraft new "Feature" v1.0 v1.1 --budget=400
#                          ^^^^ This should match file in base/
```

### Problem: "State file corrupted"

**Cause:** JSON syntax error in state.json

**Solution:**
```bash
# Reset state
promptgraft reset

# Or manually fix
nano promptgraft/.promptgraft/state.json
```

### Problem: "Budget exceeded"

**Cause:** Feature too complex for budget

**Solution:**
```bash
# Option 1: Increase budget
promptgraft new "Feature" v1.0 v1.1 --budget=600

# Option 2: Simplify feature
# (Use simpler description)

# Option 3: Split into parts
promptgraft new "Feature Part 1" v1.0 v1.1 --budget=300
promptgraft new "Feature Part 2" v1.1 v1.2 --budget=300
```

---

## 8. Advanced: Skipping Stages

If you already have intermediate files, you can jump to specific stages:

### Jump to Surgeon
```
promptgraft plan --brief=my-brief.md --budget=400
```

### Jump to Executor
```
promptgraft build --blueprint=my-blueprint.md --base=v1.0.txt
```

### Jump to Inspector
```
promptgraft verify --blueprint=my-blueprint.md --artifact=v1.1.txt --base=v1.0.txt
```

### Jump to Chronicler
```
promptgraft docs --blueprint=my-blueprint.md --audience=all
```

---

## 9. Building Multiple Features

Each feature builds on the previous:

```bash
# Feature 1: Add false starts
promptgraft new "False Starts" v1.0 v1.1 --budget=300
# ... run through pipeline ...

# Feature 2: Add self-corrections (builds on v1.1)
promptgraft new "Self Corrections" v1.1 v1.2 --budget=400
# ... run through pipeline ...

# Feature 3: Add hesitations (builds on v1.2)
promptgraft new "Hesitations" v1.2 v1.3 --budget=250
# ... run through pipeline ...
```

**Result:** v1.3 has all three features!

---

## 10. Documentation Options

Control what gets documented:

### For End Users Only
```
promptgraft docs --blueprint=implementation-v1.1.md --audience=users
```

Focuses on:
- What changed
- How to use it
- Benefits

### For Developers Only
```
promptgraft docs --blueprint=implementation-v1.1.md --audience=developers
```

Focuses on:
- Implementation details
- Character budgets
- Integration points

### For Everyone
```
promptgraft docs --blueprint=implementation-v1.1.md --audience=all
```

Includes both user and developer sections.

---

## Quick Reference Card

```
┌─────────────────────────────────────────┐
│  PROMPTGRAFT QUICK REFERENCE            │
├─────────────────────────────────────────┤
│  promptgraft new [feat] [base] [target] │
│    --budget=[N]                         │
│    → Start new pipeline                 │
│                                         │
│  promptgraft continue                   │
│    → Advance to next stage              │
│                                         │
│  promptgraft status                     │
│    → Check current stage                │
│                                         │
│  promptgraft reset                      │
│    → Clear state                        │
└─────────────────────────────────────────┘

Files:
📁 Input:  promptgraft/base/v[X].txt
📁 Output: promptgraft/output/v[Y].txt
📁 Docs:   promptgraft/output/release-notes-v[Y].md

Stages:
🏗️ Architect  → Strategic plan
🔬 Surgeon    → Detailed blueprint
🔍 Auditor    → Quality check
⚙️ Executor   → Build artifact
✔️ Inspector  → Verify result
📝 Chronicler → Generate docs
```

---

## Next Steps

1. **Run your first pipeline** with a simple feature
2. **Review the outputs** to understand the process
3. **Experiment with budgets** to find the right size
4. **Build incrementally** - small features, often
5. **Trust the system** - it catches errors automatically

**Happy grafting!** 🩹

---

**Need help?**
- Check full documentation in `README.md`
- Review specialist prompts in `.promptgraft/prompts/`
- Inspect state file: `cat .promptgraft/state.json`