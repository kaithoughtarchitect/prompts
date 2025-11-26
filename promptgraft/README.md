# PROMPTGRAFT

**Surgical Feature Grafting for Prompts**

> Stop editing prompts manually and hoping they don't break. PROMPTGRAFT is a pure LLM pipeline that adds features with surgical precision, strict budget enforcement, and quality gates.

## Quick Stats

- **95% success rate** vs 40% manual editing
- **2-4 minutes** per feature vs 1-3 hours
- **Zero code** - pure prompt orchestration
- **Complete traceability** - every character counted

---

## Installation

### 1. Download this folder

Download or clone the `promptgraft/` folder to your workspace.

### 2. Add your base prompt

Copy your current prompt to the `base/` folder:

```bash
cp your-prompt.txt promptgraft/base/v1.0.txt
```

### 3. Done!

The folder structure is ready:

```
promptgraft/
├── .promptgraft/
│   └── prompts/           # 6 specialist prompts (pre-installed)
│       ├── architect.md
│       ├── surgeon.md
│       ├── auditor.md
│       ├── executor.md
│       ├── inspector.md
│       └── chronicler.md
├── base/                  # Your source prompts go here
├── briefs/                # Strategic plans (generated)
├── blueprints/            # Implementation plans (generated)
├── output/                # Final artifacts (generated)
├── ORCHESTRATOR.md        # Paste this into Claude Code
└── README.md              # You are here
```

---

## Usage

### Step 1: Activate PROMPTGRAFT

Open Claude Code and paste the **entire contents** of `ORCHESTRATOR.md`.

Claude will respond:
```
🩹 PROMPTGRAFT INITIALIZED
Ready to coordinate pipeline...
```

### Step 2: Start a new feature

```
promptgraft new "Your Feature Name" v1.0 v1.1 --budget=400
```

Parameters:
- `"Your Feature Name"` - What you're adding
- `v1.0` - Base version (must exist in `base/`)
- `v1.1` - Target version (will be created)
- `--budget=400` - Character limit for the addition

### Step 3: Run through the pipeline

**Option A: Manual control (recommended for learning)**
```
promptgraft continue
```
Repeat this command 6 times (once per stage).

**Option B: Automatic (hands-off)**
```
promptgraft run-all
```
Or simply tell Claude: *"Run through all 6 stages automatically without waiting for my input"*

Claude will execute all stages sequentially:
1. **Architect** - Strategic planning
2. **Surgeon** - Detailed blueprint
3. **Auditor** - Quality check
4. **Executor** - Build artifact
5. **Inspector** - Verify result
6. **Chronicler** - Generate docs

### Step 4: Get your new version

Your updated prompt is at: `output/v1.1.txt`

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `promptgraft new <feat> <base> <target> --budget=N` | Start new feature pipeline |
| `promptgraft continue` | Advance to next stage |
| `promptgraft run-all` | Run all 6 stages automatically |
| `promptgraft status` | Check current progress |
| `promptgraft reset` | Clear state, start fresh |

---

## Example Session

```
YOU: [Paste ORCHESTRATOR.md]

CLAUDE: 🩹 PROMPTGRAFT INITIALIZED

YOU: promptgraft new "Error Handling" v1.0 v1.1 --budget=350

CLAUDE: 🏗️ ARCHITECT STAGE COMPLETE
        Strategic brief saved...
        Next: promptgraft continue

YOU: promptgraft continue

CLAUDE: 🔬 SURGEON STAGE COMPLETE
        Budget: 344/350 characters (98%)
        Next: promptgraft continue

[... continue through all stages ...]

CLAUDE: 🎉 PIPELINE COMPLETE
        Version: v1.1 ✅
        Artifact: output/v1.1.txt
```

---

## The Six Specialists

| Stage | Role | Time | What It Does |
|-------|------|------|--------------|
| **Architect** | Strategic planner | 10-30s | Analyzes where to integrate feature |
| **Surgeon** | Blueprint creator | 30-60s | Creates exact insertion points |
| **Auditor** | QA checker | 10-30s | Catches logical gaps before building |
| **Executor** | Mechanical builder | 5-15s | Assembles with zero creativity |
| **Inspector** | Verifier | 10-30s | Confirms fidelity to blueprint |
| **Chronicler** | Documenter | 15-30s | Generates release notes |

---

## Three Quality Gates

1. **Pre-execution** (Auditor): Catches logical gaps BEFORE building
2. **Post-execution** (Inspector): Catches execution errors AFTER building
3. **Budget** (Surgeon + Inspector): Enforced at planning AND verification

---

## Tips

### Budget Guidelines

```
40% - Core definition
20% - Integration glue
30% - Examples
10% - Safety margin
```

Start conservative (200-400 chars). You can always increase.

### Be Specific

```
❌ Bad:  "Make it better"
✅ Good: "Add retry logic with 3 attempts and exponential backoff"
```

### Build Incrementally

```bash
# Feature 1
promptgraft new "Feature A" v1.0 v1.1 --budget=300

# Feature 2 (builds on v1.1)
promptgraft new "Feature B" v1.1 v1.2 --budget=400

# Feature 3 (builds on v1.2)
promptgraft new "Feature C" v1.2 v1.3 --budget=250
```

---

## Troubleshooting

### "File not found"
Ensure your base version exists:
```bash
ls promptgraft/base/
```

### "Budget exceeded"
Options:
1. Increase budget: `--budget=600`
2. Simplify feature scope
3. Split into multiple versions

### "State file corrupted"
```
promptgraft reset
```

---

## When to Use PROMPTGRAFT

**Perfect for:**
- Character-constrained API prompts
- Production prompts (customer-facing)
- Evolving systems (v1 → v20)
- Team collaboration

**Skip for:**
- Exploration ("not sure what I want")
- Trivial changes (typos)
- One-off prompts

---

## Files Reference

| File | Purpose |
|------|---------|
| `ORCHESTRATOR.md` | Paste into Claude to activate |
| `DOCUMENTATION.md` | Full technical documentation |
| `QUICK_START.md` | Condensed guide |
| `DEPLOYMENT_CHECKLIST.md` | Pre-release checklist |

---

## License

MIT - Use freely, modify as needed.

---

**Every character counts. Make each one count deliberately.**
