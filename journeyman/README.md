# Journeyman

**Structured Development Through 5 Rigorous Phases**

> Stop coding without a plan. Journeyman is a methodology that ensures every task is completed with discipline, quality, and traceability - from simple refactors to complex systems.

## Quick Stats

- **5 phases**: Blueprint → Foundation → Assembly → Finishing → Verification
- **TDD mandatory**: Tests before implementation, always
- **Quality gates**: Can't advance until criteria met
- **Full traceability**: Every decision documented in JOURNEY.md

---

## Installation

### 1. Download this folder

Download or clone the `journeyman/` folder to your workspace.

### 2. Done!

The folder structure is ready:

```
journeyman/
├── journeyman-internals/
│   ├── prompts/
│   │   ├── master-orchestrator.md       # The brain (59 KB) - paste this!
│   │   ├── journeyman-protocol.md       # Core 5-phase protocol (8 KB)
│   │   └── implementation-framework-library.md  # Framework library (54 KB)
│   └── templates/
│       ├── journey-template.md          # Full 5-phase template
│       └── simple-path.md               # 6-step quick template
├── journeys/                            # Your journey files go here
└── README.md                            # You are here
```

---

## How to Use Journeyman (Infinite Ways!)

**There's no single "right way" to activate Journeyman.** Once the folder is in your workspace, your AI assistant understands context. Use whatever method fits your workflow.

### Natural Language (Easiest)

Just tell your AI what you want:

```
"I want to use Journeyman to build this feature"

"Let's use the Journeyman methodology"

"Can we follow Journeyman for this refactoring?"

"Guide me through the 5 phases for this task"

"I need structured development - use Journeyman"
```

### Paste the Master Orchestrator (Full Power)

Copy the entire contents of `journeyman-internals/prompts/master-orchestrator.md` into your AI assistant (Claude Code, ChatGPT, etc.). This is the complete 59 KB protocol with all frameworks.

### As a Skill (Claude Code)

Drop the `journeyman/` folder into `.claude/skills/` and Claude Code can invoke it autonomously.

### As a Slash Command

Create a `/journeyman` command in `.claude/commands/` that loads the orchestrator.

### Direct Reference

Point your AI to the folder:

```
"Use the Journeyman methodology at ./journeyman/ for this task"
```

### Formal Commands (Also Available)

```
journeyman new "Build authentication system"
journeyman status
journeyman continue
journeyman simple
journeyman reset
```

> **Note:** These examples barely scratch the surface. There are **infinite ways** to invoke Journeyman. The methodology adapts to YOU, not the other way around.

---

## The 5 Phases

```
Phase 1: Blueprint 🏗️      → Design first, NO CODE
Phase 2: Foundation 🧪     → Tests FIRST (TDD Red)
Phase 3: Assembly 🔧       → Build to pass tests (TDD Green)
Phase 4: Finishing 📝      → Polish and document
Phase 5: Verification ✅   → Validate everything works
```

### Phase 1: Blueprint
- Architecture and design
- Risk analysis
- Framework selection
- Success criteria (SMART)
- **Zero code written**

### Phase 2: Foundation
- Directory structure
- Data models
- Test suite written FIRST
- All tests FAIL (expected!)

### Phase 3: Assembly
- TDD Red-Green-Refactor
- Feature by feature
- Tests pass incrementally
- SOLID + Clean Code

### Phase 4: Finishing
- Code quality review
- Documentation
- Security audit
- Edge cases

### Phase 5: Verification
- All tests pass
- Requirements verified
- Ready for delivery

---

## Simple vs Complex Path

### Simple Path (6 Steps)
For tasks < 2 days with 1-5 files:

```
1. Confirm scope (2 min)
2. Setup structure (5 min)
3. Tests first (20 min)
4. Implement (25 min)
5. Minimal README (10 min)
6. Verify (5 min)
```

### Full Protocol (5 Phases)
For tasks 2+ days with 5-30 files:

Execute each phase completely before advancing.

---

## Peek Inside the Methodology

### Risk Analysis Format

```markdown
| Risk | Impact | Prob | Score | Mitigation |
|------|--------|------|-------|------------|
| Breaking existing code | 4 | 2 | 8 | Comprehensive tests |
| Time overrun | 3 | 3 | 9 | Buffer + prioritization |
```

### Framework Selection

```markdown
**Frameworks Applied:**
- TDD: Mandatory for all implementations
- SOLID: Clean architecture
- Clean Code: Readable, maintainable

**Frameworks Pruned:**
- BDD: No business stakeholders
- C4 Level 4: Overkill for this scope
```

### Success Criteria (SMART)

```markdown
- **S**pecific: Logger utility with 5 log levels
- **M**easurable: ≥80% coverage, 119 statements replaced
- **A**chievable: Simple utility, clear requirements
- **R**elevant: Foundation for debugging
- **T**ime-bound: 30-60 minutes
```

### Phase Gate Example

```markdown
**Gate Criteria (Phase 2 → 3):**
- [ ] Directory structure created
- [ ] Data models defined
- [ ] Test suite written
- [ ] All tests FAILING (TDD Red)

Status: ✅ All criteria met, advancing to Phase 3
```

### Commission Complete Block

```markdown
## ✅ COMMISSION COMPLETE

**Status**: DELIVERED
**Duration**: 2.5 hours

**Deliverables**:
- ✅ API service (224 lines)
- ✅ Test suite (395 lines)
- ✅ Documentation

**Tests**: 23/23 passing
**Coverage**: 100%

**The Journeyman's work is complete.**
```

---

## JOURNEY.md - Your Progress Tracker

Every commission creates a journey file:

```
journeys/
├── JOURNEY_auth-system.md
├── JOURNEY_api-refactor.md
└── JOURNEY_css-consolidation.md
```

This is your **single source of truth** for:
- What was decided and why (ADRs)
- What was built and when
- What risks were identified
- What tests were written
- What the final outcome was

---

## When to Use Journeyman

**Perfect for:**
- Features that need to work the first time
- Refactoring with zero regressions
- Team collaboration (shared JOURNEY.md)
- Complex systems (5+ files)
- Learning TDD discipline

**Skip for:**
- Quick exploration ("not sure what I want")
- One-line fixes
- Throwaway prototypes

---

## Guiding Principles

1. **No code in Phase 1** - Design first, implement later
2. **Tests before implementation** - TDD is mandatory
3. **One phase at a time** - Complete before advancing
4. **Gate criteria are strict** - Don't skip quality
5. **Document decisions** - ADRs capture the "why"
6. **Track everything** - JOURNEY.md is truth

---

## Files Reference

### Core Prompts (The Real Power)

| File | Size | Purpose |
|------|------|---------|
| `journeyman-internals/prompts/master-orchestrator.md` | 59 KB | **The brain** - Complete protocol with all frameworks |
| `journeyman-internals/prompts/journeyman-protocol.md` | 8 KB | Core 5-phase protocol (original) |
| `journeyman-internals/prompts/implementation-framework-library.md` | 54 KB | Framework library with playbooks |

### Templates

| File | Purpose |
|------|---------|
| `journeyman-internals/templates/journey-template.md` | Full 5-phase JOURNEY.md template |
| `journeyman-internals/templates/simple-path.md` | 6-step quick template |
| `journeys/` | Your journey files live here |

---

## License

MIT - Use freely, modify as needed.

---

**Quality delivered with discipline. Every time.**
