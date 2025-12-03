# Simple Path Journey

**THE COMMISSION**: {{COMMISSION_NAME}}

{{COMMISSION_DESCRIPTION}}

**Started**: {{START_TIMESTAMP}}
**Complexity**: SIMPLE (< 2 days, 1-5 files, clear requirements)
**Estimated Duration**: {{DURATION_ESTIMATE}}

---

## Commission Analysis

**Ethical Checkpoint:** ✅ PASS

**Classification:**
- **Type**: {{TYPE}}
- **Complexity**: SIMPLE
- **Duration Estimate**: {{DURATION_ESTIMATE}}

**Quality Targets:**
- Coverage: ≥80% line, ≥70% branch
- Tests: Unit tests
- Documentation: Minimal README

**Risk Analysis:**

| Risk | Impact | Prob | Score | Mitigation |
|------|--------|------|-------|------------|
| {{RISK_1}} | {{IMPACT_1}} | {{PROB_1}} | {{SCORE_1}} | {{MITIGATION_1}} |

**Selected Playbook:** {{PLAYBOOK}}
- **Why:** {{PLAYBOOK_REASON}}

**Frameworks Applied:**
- TDD (mandatory)
- Clean Code
- {{ADDITIONAL_FRAMEWORKS}}

**Frameworks Pruned:**
- {{PRUNED_FRAMEWORKS}}

**Success Criteria (SMART):**
- **S**pecific: {{SPECIFIC}}
- **M**easurable: {{MEASURABLE}}
- **A**chievable: {{ACHIEVABLE}}
- **R**elevant: {{RELEVANT}}
- **T**ime-bound: {{TIMEBOUND}}

---

## Simple Path - 6 Steps

### Step 1: Confirm Scope ✅
**Duration**: 2 min

- [ ] Commission understood
- [ ] Scope is truly SIMPLE (< 2 days, 1-5 files)
- [ ] No hidden complexity

**Confirmed**: {{STEP_1_TIMESTAMP}}

---

### Step 2: Setup Structure
**Duration**: 5 min

- [ ] Directory created
- [ ] File structure planned

```
{{DIRECTORY_STRUCTURE}}
```

**Completed**: {{STEP_2_TIMESTAMP}}

---

### Step 3: Tests First (TDD Red)
**Duration**: ~20 min

- [ ] Test file created
- [ ] All test cases written
- [ ] Tests run and FAIL (expected)

**Test File**: `{{TEST_FILE_PATH}}`

**Tests Written**:
1. {{TEST_1}}
2. {{TEST_2}}
3. {{TEST_3}}

**Test Results**:
```bash
$ {{TEST_COMMAND}}
{{TEST_COUNT}} tests FAILED (expected - TDD Red phase)
```

**Completed**: {{STEP_3_TIMESTAMP}}

---

### Step 4: Implement (TDD Green/Refactor)
**Duration**: ~25 min

- [ ] Implementation written
- [ ] All tests passing
- [ ] Code refactored if needed

**Implementation File**: `{{IMPL_FILE_PATH}}`

**Test Results**:
```bash
$ {{TEST_COMMAND}}
{{TEST_COUNT}}/{{TEST_COUNT}} tests PASSED ✅
```

**Completed**: {{STEP_4_TIMESTAMP}}

---

### Step 5: Minimal README
**Duration**: ~10 min

- [ ] README created
- [ ] Usage documented
- [ ] Examples provided

**README Location**: `{{README_PATH}}`

**Completed**: {{STEP_5_TIMESTAMP}}

---

### Step 6: Verify
**Duration**: ~5 min

- [ ] All tests pass
- [ ] Build succeeds
- [ ] Documentation complete
- [ ] Commission requirements met

**Final Test Results**:
```bash
$ {{TEST_COMMAND}}
{{TEST_COUNT}}/{{TEST_COUNT}} tests PASSED ✅
Coverage: {{COVERAGE}}%
```

**Completed**: {{STEP_6_TIMESTAMP}}

---

## ✅ COMMISSION COMPLETE

**Status**: DELIVERED
**Date**: {{COMPLETION_TIMESTAMP}}
**Duration**: {{TOTAL_DURATION}} (estimated {{DURATION_ESTIMATE}})

**Files Created**:
- `{{FILE_1}}` ({{FILE_1_LINES}} lines)
- `{{FILE_2}}` ({{FILE_2_LINES}} lines)

**Test Results**:
- Tests: {{TEST_COUNT}}/{{TEST_COUNT}} passing
- Coverage: {{COVERAGE}}%

**Success Criteria Met**:
- ✅ {{CRITERIA_1}}
- ✅ {{CRITERIA_2}}
- ✅ {{CRITERIA_3}}

---

**Simple. Clean. Done.**
