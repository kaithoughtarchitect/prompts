# The Prompt Creation Trilogy

This folder contains a three-stage prompt engineering system designed to systematically analyze a problem, generate a targeted prompt, and then improve that prompt to a high standard.

The system follows a logical workflow: **Analyze → Generate → Improve**.

## The Three Stages

### 1. [The Multi-Framework Analyzer](./1-analyzer.md)

**Purpose:** To gather deep context and understanding about a problem *before* writing a prompt.

This first stage uses a phase-by-phase analytical framework to break down any question or problem into actionable insights. It employs methods like Ishikawa fishbone diagrams, the Five Whys, and OODA loops to ensure a thorough analysis. The output is a progressively built `Analysis-[Topic]-[Date].md` file that documents the entire analytical process.

**Best for:** Situations where you need to deeply understand a complex problem before attempting to solve it with an AI prompt.

### 2. [The Agentic Prompt Generator](./2-generator.md)

**Purpose:** To create a targeted, high-quality prompt based on a set of requirements.

This second stage acts as an autonomous prompt architect. It takes your requirements, chooses an appropriate architecture, and then iteratively builds a prompt, scoring its own work and making decisions until it meets quality targets. It logs its entire process in a `prompt_gen.md` file, providing a complete audit trail of its reasoning.

**Best for:** Generating robust, well-structured prompts for specific tasks when you have a clear goal in mind.

### 3. [The Adaptive Prompt Improver](./3-improver.md)

**Purpose:** To take *any* existing prompt and systematically enhance it to achieve 90%+ quality scores.

The final stage is an adaptive improvement loop. It auto-detects the prompt's domain (e.g., analysis, creative, technical) and applies specialized enhancements using military-grade OODA loops. It creates a `prompt_improvement_[timestamp].md` file that documents each improvement loop, showing you exactly how the prompt evolves and teaching prompt engineering principles along the way.

**Best for:** Polishing a rough or basic prompt into a production-ready, high-performance tool.

---

## Future Updates

**Note:** This trilogy is planned to be updated into a fully integrated, sub-agent workflow in the near future. This will allow for a seamless, automated flow from analysis to generation to final improvement.
