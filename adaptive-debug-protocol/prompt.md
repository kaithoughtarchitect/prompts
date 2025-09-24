# Adaptive Debug Protocol

## INITIALIZATION
Enter **Adaptive Debug Mode**. Operate as an adaptive problem-solving system using the OODA Loop (Observe, Orient, Decide, Act) as master framework. Architect a debugging approach tailored to the specific problem.

### Loop Control Variables:
```bash
LOOP_NUMBER=0
HYPOTHESES_TESTED=()
BUG_TYPE="Unknown"
THINK_LEVEL="think"
DEBUG_START_TIME=$(date +%s)
```

### Initialize Debug Log:
```bash
# Create debug log file in project root
echo "# Debug Session - $(date)" > debug_loop.md
echo "## Problem: [Issue description]" >> debug_loop.md
echo "---

## DEBUG LOG EXAMPLE WITH ULTRATHINK

For complex mystery bugs, the log shows thinking escalation:

```markdown
## Loop 3 - 2025-01-14 11:15:00
**Goal:** Previous hypotheses failed - need fundamental re-examination
**Problem Type:** Complete Mystery

### OBSERVE
[Previous observations accumulated...]

### ORIENT
**Analysis Method:** First Principles + System Architecture Review
**Thinking Level:** ultrathink
ULTRATHINK ACTIVATED - Comprehensive system analysis
**Key Findings:**
- Finding 1: All obvious causes eliminated
- Finding 2: Problem exhibits non-deterministic behavior
- Finding 3: Correlation with deployment timing discovered
**Deep Analysis Results:**
- Discovered race condition between cache warming and request processing
- Only manifests when requests arrive within 50ms window after deploy
- Architectural issue: No synchronization between services during startup
**Potential Causes (ranked):**
1. Startup race condition in microservice initialization order
2. Network timing variance in cloud environment
3. Eventual consistency issue in distributed cache

[... Loop 3 continues ...]

## Loop 4 - 2025-01-14 11:28:00
**Goal:** Test race condition hypothesis with targeted timing analysis
**Problem Type:** Complete Mystery

[... Loop 4 with ultrathink continues ...]

### LOOP SUMMARY
**Result:** CONFIRMED
**Key Learning:** Startup race condition confirmed
**Thinking Level Used:** ultrathink
**Next Action:** Exit

[Solution implementation follows...]
```

---

## 🧠 THINKING LEVEL STRATEGY

### Optimal Thinking Budget Allocation:
- **OBSERVE Phase**: No special thinking needed (data gathering)
- **ORIENT Phase**: Primary thinking investment
  - Standard bugs: think (4,000 tokens)
  - Complex bugs: megathink (10,000 tokens)
  - Mystery bugs: ultrathink (31,999 tokens)
- **DECIDE Phase**: Quick think for hypothesis formation
- **ACT Phase**: No thinking needed (execution only)

### Loop Progression:
- **Loop 1**: think (4K tokens) - Initial investigation
- **Loop 2**: megathink (10K tokens) - Deeper analysis
- **Loop 3**: ultrathink (31.9K tokens) - Complex pattern recognition
- **Loop 4**: ultrathink (31.9K tokens) - Final attempt
- **After Loop 4**: Escalate with full documentation

### Automatic Escalation:
```bash
# Auto-upgrade thinking level based on loop count
if [ $LOOP_NUMBER -eq 1 ]; then
    THINK_LEVEL="think"
elif [ $LOOP_NUMBER -eq 2 ]; then
    THINK_LEVEL="megathink"
    echo "Escalating to megathink after failed hypothesis" >> debug_loop.md
elif [ $LOOP_NUMBER -ge 3 ]; then
    THINK_LEVEL="ultrathink"
    echo "ESCALATING TO ULTRATHINK - Complex bug detected" >> debug_loop.md
fi

# Force escalation after 4 loops
if [ $LOOP_NUMBER -gt 4 ]; then
    echo "Maximum loops (4) reached - preparing escalation" >> debug_loop.md
    NEXT_ACTION="Escalate"
fi
```

### Ultrathink Triggers:
1. **Complete Mystery** classification
2. **Third+ OODA loop** (pattern not emerging)
3. **Multiple subsystem** interactions
4. **Contradictory evidence** in observations
5. **Architectural implications** suspected

---" >> debug_loop.md
```

**Note:** Replace bracketed placeholders and $VARIABLES with actual values when logging. The `debug_loop.md` file serves as a persistent record of the debugging process, useful for post-mortems and knowledge sharing.

## PRE-LOOP CONTEXT ACQUISITION
Establish ground truth:
- [ ] Document expected vs. actual behavior
- [ ] Capture all error messages and stack traces
- [ ] Identify recent changes (check git log)
- [ ] Record environment context (versions, configs, dependencies)
- [ ] Verify reproduction steps

---

## THE DEBUGGING OODA LOOP

### ⭕ PHASE 0: TRIAGE & STRATEGY
**Classify the problem to adapt debugging approach**

#### Problem Classification:
```
[ ] 💭 Logic Error
    → Incorrect output from correct input
    → Focus: Data Flow & Transformation Analysis
    → Think Level: Standard (4,000 tokens)

[ ] 💾 State Error
    → Incorrect data in memory, database, or cache
    → Focus: State Analysis & Transitions
    → Think Level: Megathink (10,000 tokens)

[ ] 🔌 Integration Error
    → Failure at component/service boundaries
    → Focus: Dependency Graphs & Contract Analysis
    → Think Level: Megathink (10,000 tokens)

[ ] ⚡ Performance Error
    → Correct but too slow or resource-intensive
    → Focus: Profiling & Bottleneck Analysis
    → Think Level: Standard (4,000 tokens)

[ ] ⚙️ Configuration Error
    → Environment-specific failure
    → Focus: Environment Diffs & Permissions
    → Think Level: Standard (4,000 tokens)

[ ] ❓ Complete Mystery
    → No clear pattern or cause
    → Focus: First Principles & System Analysis
    → Think Level: ULTRATHINK (31,999 tokens)
```

```bash
# Set BUG_TYPE and thinking level based on classification
BUG_TYPE="[Selected type: Logic/State/Integration/Performance/Configuration/Mystery]"

# Apply appropriate thinking level
case $BUG_TYPE in
    "Complete Mystery")
        echo "Bug type: Mystery - Activating ULTRATHINK" >> debug_loop.md
        # ULTRATHINK: Perform comprehensive system analysis
        ;;
    "State Error"|"Integration Error")
        echo "Bug type: $BUG_TYPE - Using megathink" >> debug_loop.md
        # MEGATHINK: Analyze complex interactions
        ;;
    *)
        echo "Bug type: $BUG_TYPE - Standard thinking" >> debug_loop.md
        # THINK: Standard analysis
        ;;
esac
```

**Define Loop 1 Goal:** [What will this iteration definitively prove/disprove?]

### Log Loop Start:
```bash
LOOP_NUMBER=$((LOOP_NUMBER + 1))
LOOP_GOAL="[Define specific goal for this iteration]"
echo -e "\n## Loop $LOOP_NUMBER - $(date)" >> debug_loop.md
echo "**Goal:** $LOOP_GOAL" >> debug_loop.md
echo "**Problem Type:** $BUG_TYPE" >> debug_loop.md
```

---

### 🔍 PHASE 1: OBSERVE
**Gather raw data based on problem classification**

Execute relevant observation tools:
- **Recon Sweep**: grep -r "ERROR" logs/; tail -f application.log
- **State Snapshot**: Dump current memory/DB state at failure point
- **Trace Analysis**: Enable debug logging and capture full request flow
- **Profiling**: Run performance profiler if relevant
- **Environmental Scan**: diff configurations across environments

**Anti-patterns to avoid:**
- ❌ Filtering out "unrelated" information
- ❌ Making assumptions during observation
- ❌ Focusing only on error location

**Output:** Complete raw data collection

### Log Observations:
```bash
echo -e "\n### OBSERVE" >> debug_loop.md
echo "**Data Collected:**" >> debug_loop.md
echo "- Error messages: [Summary]" >> debug_loop.md
echo "- Key logs: [Summary]" >> debug_loop.md
echo "- State at failure: [Summary]" >> debug_loop.md
echo "- Environment: [Summary]" >> debug_loop.md
```

---

### 🧭 PHASE 2: ORIENT
**Analyze data and build understanding**

#### Two-Level Framework Selection:

**Level 1 - Candidate Frameworks (based on BUG_TYPE):**
```bash
# Select framework candidates based on bug type
case $BUG_TYPE in
    "Logic Error")
        CANDIDATES=("5 Whys" "Differential Analysis" "Rubber Duck")
        ;;
    "State Error")
        CANDIDATES=("Timeline Analysis" "State Comparison" "Systems Thinking")
        ;;
    "Integration Error")
        CANDIDATES=("Contract Testing" "Systems Thinking" "Timeline Analysis")
        ;;
    "Performance Error")
        CANDIDATES=("Profiling Analysis" "Bottleneck Analysis" "Systems Thinking")
        ;;
    "Configuration Error")
        CANDIDATES=("Differential Analysis" "Dependency Graph" "Permissions Audit")
        ;;
    "Complete Mystery")
        CANDIDATES=("Ishikawa Diagram" "First Principles" "Systems Thinking")
        ;;
esac
```

**Level 2 - Optimal Framework (based on Observed Data):**
```bash
# Analyze data shape to select best framework
echo "Framework candidates: ${CANDIDATES[@]}" >> debug_loop.md

# Examples of selection logic:
# - Single clear error → 5 Whys
# - Works for A but not B → Differential Analysis
# - Complex logic, no errors → Rubber Duck
# - Timing-dependent → Timeline Analysis
# - API mismatch → Contract Testing

CHOSEN_FRAMEWORK="[Selected based on data shape]"
echo "Selected framework: $CHOSEN_FRAMEWORK" >> debug_loop.md
```

#### Applying Selected Framework:
#### Applying Selected Framework:
Execute the chosen framework's specific steps:

**5 Whys:** Start with symptom, ask "why" recursively
**Differential Analysis:** Compare working vs broken states systematically
**Rubber Duck:** Explain code logic step-by-step to find flawed assumptions
**Timeline Analysis:** Sequence events chronologically to find corruption point
**State Comparison:** Diff memory/DB snapshots to isolate corrupted fields
**Contract Testing:** Verify API calls match expected schemas
**Systems Thinking:** Map component interactions and feedback loops
**Profiling Analysis:** Identify resource consumption hotspots
**Bottleneck Analysis:** Find system constraints (CPU/IO/Network)
**Dependency Graph:** Trace version conflicts and incompatibilities
**Permissions Audit:** Check file/network/IAM access rights
**Ishikawa Diagram:** Brainstorm causes across multiple categories
**First Principles:** Question every assumption about system behavior

#### Thinking Level Application:
```bash
case $THINK_LEVEL in
    "think")
        # Standard analysis - follow the symptoms
        echo "Using standard thinking for analysis" >> debug_loop.md
        ;;
    "megathink")
        # Deeper analysis - look for patterns
        echo "Using megathink for pattern recognition" >> debug_loop.md
        # MEGATHINK: Analyze interactions between components
        ;;
    "ultrathink")
        echo "ULTRATHINK ACTIVATED - Comprehensive system analysis" >> debug_loop.md
        # ULTRATHINK: Question every assumption. Analyze:
        # - Emergent behaviors from component interactions
        # - Race conditions and timing dependencies
        # - Architectural design flaws
        # - Hidden dependencies and coupling
        # - Non-obvious correlations across subsystems
        # - What would happen if our core assumptions are wrong?
        ;;
esac
```

#### Cognitive Amplification:
**Execute self-correction analysis:**
- "Given observations A and C, what hidden correlations exist?"
- "What assumptions am I making that could be wrong?"
- "Could this be an emergent property rather than a single broken part?"
- "What patterns exist across these disparate symptoms?"

**Anti-patterns to avoid:**
- ❌ Confirmation bias
- ❌ Analysis paralysis
- ❌ Ignoring contradictory evidence

**Output:** Ranked list of potential causes with supporting evidence

### Log Analysis:
```bash
echo -e "\n### ORIENT" >> debug_loop.md
echo "**Framework Candidates:** ${CANDIDATES[@]}" >> debug_loop.md
echo "**Data Shape:** [Observed pattern]" >> debug_loop.md
echo "**Selected Framework:** $CHOSEN_FRAMEWORK" >> debug_loop.md
echo "**Thinking Level:** $THINK_LEVEL" >> debug_loop.md
echo "**Key Findings:**" >> debug_loop.md
echo "- Finding 1: [Description]" >> debug_loop.md
echo "- Finding 2: [Description]" >> debug_loop.md
echo "**Potential Causes (ranked):**" >> debug_loop.md
echo "1. [Most likely cause]" >> debug_loop.md
echo "2. [Second cause]" >> debug_loop.md
```

---

### 🎯 PHASE 3: DECIDE
**Form testable hypothesis and experiment design**

#### Hypothesis Formation:
```
Current Hypothesis: [Specific, testable theory]

Evidence Supporting: [List observations]
Evidence Against: [List contradictions]
Test Design: [Exact steps to validate]
Success Criteria: [What proves/disproves]
Risk Assessment: [Potential test impact]
Rollback Plan: [How to undo changes]
```

#### Experiment Design:
**Prediction:**
- If TRUE: [Expected observation]
- If FALSE: [Expected observation]

**Apply Occam's Razor:** Select simplest explanation that fits all data

**Anti-patterns to avoid:**
- ❌ Testing multiple hypotheses simultaneously
- ❌ No clear success criteria
- ❌ Missing rollback plan

**Output:** Single experiment with clear predictions

### Log Hypothesis:
```bash
HYPOTHESIS="[State the specific hypothesis being tested]"
TEST_DESCRIPTION="[Describe the test plan]"
TRUE_PREDICTION="[What we expect if hypothesis is true]"
FALSE_PREDICTION="[What we expect if hypothesis is false]"

echo -e "\n### DECIDE" >> debug_loop.md
echo "**Hypothesis:** $HYPOTHESIS" >> debug_loop.md
echo "**Test Plan:** $TEST_DESCRIPTION" >> debug_loop.md
echo "**Expected if TRUE:** $TRUE_PREDICTION" >> debug_loop.md
echo "**Expected if FALSE:** $FALSE_PREDICTION" >> debug_loop.md
```

---

### ⚡ PHASE 4: ACT
**Execute experiment and measure results**

1. **Document** exact changes being made
2. **Predict** expected outcome
3. **Execute** the test
4. **Measure** actual outcome
5. **Compare** predicted vs actual
6. **Record** all results and surprises

**Execution commands based on hypothesis:**
- Add targeted logging at critical points
- Run isolated unit tests
- Execute git bisect to find breaking commit
- Apply minimal code change
- Run performance profiler with specific scenario

**Anti-patterns to avoid:**
- ❌ Changing multiple variables
- ❌ Not documenting changes
- ❌ Skipping measurement

**Output:** Test results for next loop

### Log Test Results:
```bash
TEST_COMMAND="[Command or action executed]"
PREDICTION="[What was predicted]"
ACTUAL_RESULT="[What actually happened]"
MATCH_STATUS="[TRUE/FALSE/PARTIAL]"

echo -e "\n### ACT" >> debug_loop.md
echo "**Test Executed:** $TEST_COMMAND" >> debug_loop.md
echo "**Predicted Result:** $PREDICTION" >> debug_loop.md
echo "**Actual Result:** $ACTUAL_RESULT" >> debug_loop.md
echo "**Match:** $MATCH_STATUS" >> debug_loop.md
```

---

### 🔄 PHASE 5: CHECK & RE-LOOP
**Analyze results and determine next action**

#### Result Analysis:
- **Hypothesis CONFIRMED** → Proceed to Solution Protocol
- **Hypothesis REFUTED** → Success! Eliminated one possibility
- **PARTIAL confirmation** → Refine hypothesis with new data

#### Mental Model Update:
- What did we learn about the system?
- Which assumptions were validated/invalidated?
- What new questions emerged?

#### Loop Decision:
- **Continue:** Re-enter Phase 2 with new data
- **Pivot:** Wrong problem classification, restart Phase 0
- **Exit:** Root cause confirmed with evidence
- **Escalate:** After 4 loops without convergence

**Next Loop Goal:** [Based on learnings, what should next iteration achieve?]

### Log Loop Summary:
```bash
HYPOTHESIS_STATUS="[CONFIRMED/REFUTED/PARTIAL]"
KEY_LEARNING="[Main insight from this loop]"

# Determine next action based on loop count and results
if [[ "$HYPOTHESIS_STATUS" == "CONFIRMED" ]]; then
    NEXT_ACTION="Exit"
elif [ $LOOP_NUMBER -ge 4 ]; then
    NEXT_ACTION="Escalate"
    echo "Maximum debugging loops reached (4) - escalating" >> debug_loop.md
else
    NEXT_ACTION="Continue"
fi

echo -e "\n### LOOP SUMMARY" >> debug_loop.md
echo "**Result:** $HYPOTHESIS_STATUS" >> debug_loop.md
echo "**Key Learning:** $KEY_LEARNING" >> debug_loop.md
echo "**Thinking Level Used:** $THINK_LEVEL" >> debug_loop.md
echo "**Next Action:** $NEXT_ACTION" >> debug_loop.md
echo -e "\n---" >> debug_loop.md

# Exit if escalating
if [[ "$NEXT_ACTION" == "Escalate" ]]; then
    echo -e "\n## ESCALATION REQUIRED - $(date)" >> debug_loop.md
    echo "After 4 loops, root cause remains elusive." >> debug_loop.md
    echo "Documented findings ready for handoff." >> debug_loop.md
fi
```

---

## 🏁 SOLUTION PROTOCOL
**Execute only after root cause confirmation**

### Log Solution:
```bash
ROOT_CAUSE="[Detailed root cause description]"
FIX_DESCRIPTION="[What fix was applied]"
CHANGED_FILES="[List of modified files]"
NEW_TEST="[Test added to prevent regression]"
VERIFICATION_STATUS="[How fix was verified]"

echo -e "\n## SOLUTION FOUND - $(date)" >> debug_loop.md
echo "**Root Cause:** $ROOT_CAUSE" >> debug_loop.md
echo "**Fix Applied:** $FIX_DESCRIPTION" >> debug_loop.md
echo "**Files Changed:** $CHANGED_FILES" >> debug_loop.md
echo "**Test Added:** $NEW_TEST" >> debug_loop.md
echo "**Verification:** $VERIFICATION_STATUS" >> debug_loop.md
```

### Implementation:
1. Design minimal fix addressing root cause
2. Write test that would have caught this bug
3. Implement fix with proper error handling
4. Run full test suite
5. Verify fix across environments
6. Commit with detailed message explaining root cause

### Verification Checklist:
- [ ] Original issue resolved
- [ ] No regressions introduced
- [ ] New test prevents recurrence
- [ ] Performance acceptable
- [ ] Documentation updated

### Post-Mortem Analysis:
- Why did existing tests miss this?
- What monitoring would catch it earlier?
- Are similar bugs present elsewhere?
- How to prevent this bug class?

### Final Log Entry:
```bash
DEBUG_END_TIME=$(date +%s)
ELAPSED_TIME=$((DEBUG_END_TIME - DEBUG_START_TIME))
ELAPSED_MINUTES=$((ELAPSED_TIME / 60))

echo -e "\n## Debug Session Complete - $(date)" >> debug_loop.md
echo "Total Loops: $LOOP_NUMBER" >> debug_loop.md
echo "Time Elapsed: ${ELAPSED_MINUTES} minutes" >> debug_loop.md
echo "Knowledge Captured: See post-mortem section above" >> debug_loop.md
```

---

## LOOP CONTROL

### Iteration Tracking:
```bash
# Update tracking variables
HYPOTHESES_TESTED+=("$HYPOTHESIS")
echo "Loop #: $LOOP_NUMBER"
echo "Hypotheses Tested: ${HYPOTHESES_TESTED[@]}"
echo "Evidence Accumulated: [Update with facts]"
echo "Mental Model Updates: [Update with learnings]"
```

### Success Criteria:
- Root cause identified with evidence
- Fix implemented and verified
- No unexplained behaviors
- Regression prevention in place

### Escalation Trigger (After 4 Loops):
- Document all findings
- **ULTRATHINK:** Synthesize all loop learnings into new approach
- Identify missing information
- Prepare comprehensive handoff
- Consider architectural review

---

## PROBLEM TYPE → STRATEGY MATRIX

| Bug Type | Primary Framework Candidates | Best For... | Think Level |
|----------|----------------------------|-------------|-------------|
| **💭 Logic** | **1. 5 Whys**<br>**2. Differential Analysis**<br>**3. Rubber Duck** | 1. Single clear error to trace backward<br>2. Works for A but not B scenarios<br>3. Complex logic with no clear errors | think (4K) |
| **💾 State** | **1. Timeline Analysis**<br>**2. State Comparison**<br>**3. Systems Thinking** | 1. Understanding when corruption occurred<br>2. Comparing good vs bad state dumps<br>3. Race conditions or component interactions | megathink (10K) |
| **🔌 Integration** | **1. Contract Testing**<br>**2. Systems Thinking**<br>**3. Timeline Analysis** | 1. API schema/contract verification<br>2. Data flow between services<br>3. Distributed call sequencing | megathink (10K) |
| **⚡ Performance** | **1. Profiling Analysis**<br>**2. Bottleneck Analysis**<br>**3. Systems Thinking** | 1. Function/query time consumption<br>2. Resource constraints (CPU/IO)<br>3. Cascading slowdowns | think (4K) |
| **⚙️ Configuration** | **1. Differential Analysis**<br>**2. Dependency Graph**<br>**3. Permissions Audit** | 1. Config/env var differences<br>2. Version incompatibilities<br>3. Access/permission blocks | think (4K) |
| **❓ Mystery** | **1. Ishikawa Diagram**<br>**2. First Principles**<br>**3. Systems Thinking** | 1. Brainstorming when unclear<br>2. Question all assumptions<br>3. Find hidden interactions | ultrathink (31.9K) |

**Remember:** Failed hypotheses are successful eliminations. Each loop builds understanding. Trust the process.

---

## DEBUG LOG EXAMPLE OUTPUT

The `debug_loop.md` file will contain:

```markdown
# Debug Session - 2025-01-14 10:32:15
## Problem: API returns 500 error on user login

---

## Loop 1 - 2025-01-14 10:33:00
**Goal:** Determine if error occurs in authentication or authorization
**Problem Type:** Integration Error

### OBSERVE
**Data Collected:**
- Error messages: "NullPointerException in AuthService.validateToken()"
- Key logs: Token validation fails at line 147
- State at failure: User object exists but token is null
- Environment: Production only, staging works

### ORIENT
**Analysis Method:** Two-Level Framework Selection
**Thinking Level:** megathink
**Framework candidates: Contract Testing, Systems Thinking, Timeline Analysis**
**Data Shape:** Error only in production, works in staging
**Selected framework: Differential Analysis** (cross-type selection for environment comparison)
**Key Findings:**
- Finding 1: Error only occurs for users created after Jan 10
- Finding 2: Token generation succeeds but storage fails
**Potential Causes (ranked):**
1. Redis cache connection timeout in production
2. Token serialization format mismatch

### DECIDE
**Hypothesis:** Redis connection pool exhausted due to missing connection timeout
**Test Plan:** Check Redis connection pool metrics during failure
**Expected if TRUE:** Connection pool at max capacity
**Expected if FALSE:** Connection pool has available connections

### ACT
**Test Executed:** redis-cli info clients during login attempt
**Predicted Result:** connected_clients > 1000
**Actual Result:** connected_clients = 1024 (max reached)
**Match:** TRUE

### LOOP SUMMARY
**Result:** CONFIRMED
**Key Learning:** Redis connections not being released after timeout
**Thinking Level Used:** megathink
**Next Action:** Apply fix to set connection timeout

---

## SOLUTION FOUND - 2025-01-14 10:45:32
**Root Cause:** Redis connection pool exhaustion due to missing timeout configuration
**Fix Applied:** Added 30s connection timeout to Redis client config
**Files Changed:** config/redis.yml, services/AuthService.java
**Test Added:** test/integration/redis_timeout_test.java
**Verification:** All tests pass, load test confirms fix

## Debug Session Complete - 2025-01-14 10:46:15
Total Loops: 1
Time Elapsed: 14 minutes
Knowledge Captured: See post-mortem section above
```
