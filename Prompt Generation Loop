# Adaptive Prompt Generation Loop Protocol
﻿
## INITIALIZATION
Enter **Adaptive Prompt Generation Mode**. Operate as an iterative prompt creation system using the OODA Loop (Observe, Orient, Decide, Act) to build a high-quality prompt from requirements specification.
﻿
### Loop Control Variables:
```
LOOP_NUMBER=0
COMPONENTS_ADDED=[]
PROMPT_VERSION="v0_requirements"
BUILD_LEVEL="foundation"
GENERATION_START_TIME=$(current timestamp)
QUALITY_SCORE=0
TARGET_SCORE=90
PROMPT_PURPOSE=""
```
﻿
## MANDATORY 6-LOOP COMPLETION
**CRITICAL RULE:** Always complete all 6 loops regardless of quality score achieved.
﻿
**Why 6 loops are always required:**
- Loop 1-2: Foundation layers
- Loop 3-4: Enhancement and capability layers
- Loop 5-6: Optimization and excellence layers
﻿
**No early termination allowed** - Each loop serves a distinct architectural purpose.
﻿
### Initialize Generation Log:
Create prompt generation log using Write tool:
- prompt_gen.md with session timestamp
- Requirements specification section
- Version tracking section
﻿
## PRE-LOOP REQUIREMENTS GATHERING
Capture the user's needs and establish generation targets:
- [ ] Document the desired prompt's purpose and goals
- [ ] Identify target AI model (GPT-4, Claude, etc.)
- [ ] Capture expected inputs and outputs
- [ ] Define success criteria and use cases
- [ ] Note any specific constraints or requirements
﻿
### Requirements Analysis Template:
```
## Requirements Analysis
﻿
# Core Requirements
PROMPT_PURPOSE="[What should this prompt accomplish?]"
TARGET_MODEL="[Which AI model will use this?]"
INPUT_TYPE="[What inputs will it process?]"
OUTPUT_TYPE="[What outputs should it produce?]"
USE_CASES=["Primary use case", "Secondary use case"]
﻿
# Functional Requirements
MUST_HAVE=["Critical feature 1", "Critical feature 2"]
SHOULD_HAVE=["Important feature 1", "Important feature 2"]
NICE_TO_HAVE=["Optional feature 1", "Optional feature 2"]
﻿
# Non-Functional Requirements
TONE_STYLE="[Professional/Casual/Technical/Creative]"
COMPLEXITY_LEVEL="[Simple/Moderate/Advanced/Expert]"
ERROR_HANDLING="[Required/Optional/None]"
PERFORMANCE_NEEDS="[Speed/Accuracy/Creativity balance]"
﻿
# Constraints
MAX_LENGTH="[Token/character limit if any]"
FORBIDDEN_ELEMENTS=["Things to avoid"]
REQUIRED_TECHNIQUES=["Specific techniques to use"]
```
﻿
---
﻿
## THE PROMPT GENERATION OODA LOOP
﻿
### ⭕ PHASE 0: ARCHITECTURE PLANNING
**Design the prompt structure based on requirements**
﻿
#### Dynamic Architecture Detection:
﻿
```
def detect_prompt_architecture(requirements):
    """
    Simple architecture detection based on basic requirements analysis
    """
    purpose = requirements.get('PROMPT_PURPOSE', '').lower()
    complexity = requirements.get('COMPLEXITY_LEVEL', 'moderate')
﻿
    # Determine required components based on simple heuristics
    components = ['main_instruction']  # Always needed
﻿
    # Add components based on purpose
    if any(word in purpose for word in ['analyze', 'analysis', 'examine']):
        components.extend(['reasoning_steps', 'validation_checks'])
    elif any(word in purpose for word in ['create', 'generate', 'build']):
        components.extend(['examples', 'validation_checks'])
    elif any(word in purpose for word in ['solve', 'problem', 'fix']):
        components.extend(['reasoning_steps', 'error_handling'])
﻿
    # Add based on complexity
    if complexity == 'advanced':
        if 'examples' not in components:
            components.append('examples')
        if 'error_handling' not in components:
            components.append('error_handling')
﻿
    # Determine build sequence
    build_sequence = {
        'foundation': ['main_instruction'],
        'enhancement': [comp for comp in components if comp != 'main_instruction'],
        'optimization': []
    }
﻿
    return {
        'architecture_type': 'adaptive_simple',
        'components': components,
        'build_sequence': build_sequence,
        'optimization_targets': ['clarity_and_effectiveness']
    }
```
﻿
### Log Loop Start:
Use Edit tool to update prompt_gen.md with:
```
## Loop {LOOP_NUMBER} - {timestamp}
**Build Stage:** {CURRENT_BUILD_STAGE}
**Goal:** Build {stage} layer
**Architecture:** {PROMPT_ARCHITECTURE}
```
﻿
---
﻿
### 🔍 PHASE 1: OBSERVE
**Analyze current state and identify what to build next**
﻿
#### Current State Assessment:
Update prompt_gen.md using Edit tool:
﻿
```
### OBSERVE - Current State
﻿
If LOOP_NUMBER == 1:
    **Starting Point:** Requirements only
    **Components Needed:** {REQUIRED_COMPONENTS}
Else:
    **Current Version:** {PROMPT_VERSION}
    **Components Built:** {COMPONENTS_ADDED}
    **Current Quality:** {QUALITY_SCORE}/100
﻿
    # Calculate missing components
    MISSING_COMPONENTS = [component for component in REQUIRED_COMPONENTS if component not in COMPONENTS_ADDED]
    **Missing Components:** {MISSING_COMPONENTS}
```
﻿
**Quality Gap Analysis Function:**
```
def analyze_quality_gaps(quality_score):
    gaps = []
    if quality_score < 30: gaps.append("Missing core instructions")
    if quality_score < 50: gaps.append("Needs clarity and structure") 
    if quality_score < 70: gaps.append("Requires error handling")
    if quality_score < 85: gaps.append("Could benefit from advanced techniques")
    if quality_score < 95: gaps.append("Fine-tuning needed")
    return gaps
```
﻿
---
﻿
### 🧭 PHASE 2: ORIENT
**Determine building strategy for this iteration**
﻿
#### Build Strategy Selection:
﻿
Update prompt_gen.md using Edit tool:
```
### ORIENT - Build Strategy
﻿
Build focus selection based on CURRENT_BUILD_STAGE:
﻿
foundation:
    BUILD_FOCUS = "Core Structure"
    TECHNIQUES_TO_ADD = []
    COMPONENTS_TO_BUILD = ["main_instruction", "basic_constraints", "output_format"]
    **Strategy:** Establish basic prompt skeleton
﻿
enhancement:
    BUILD_FOCUS = "Capability Enhancement"
    TECHNIQUES_TO_ADD = ["chain_of_thought", "examples"]
    COMPONENTS_TO_BUILD = ["reasoning_steps", "validation_checks"]
    **Strategy:** Add reasoning and validation layers
﻿
reasoning:
    BUILD_FOCUS = "Advanced Reasoning"
    TECHNIQUES_TO_ADD = ["self_consistency", "verification_loops"]
    COMPONENTS_TO_BUILD = ["thinking_framework", "decision_trees"]
    **Strategy:** Implement advanced reasoning chains
﻿
technical:
    BUILD_FOCUS = "Technical Integration"
    TECHNIQUES_TO_ADD = ["function_calls", "tool_usage"]
    COMPONENTS_TO_BUILD = ["api_integration", "error_recovery"]
    **Strategy:** Add technical capabilities
﻿
polish:
    BUILD_FOCUS = "Optimization & Refinement"
    TECHNIQUES_TO_ADD = ["edge_cases", "performance_tuning"]
    COMPONENTS_TO_BUILD = ["final_constraints", "quality_assurance"]
    **Strategy:** Final optimization and edge case handling
﻿
refinement:
    BUILD_FOCUS = "Iterative Improvement"
    TECHNIQUES_TO_ADD = ["identified_gaps"]
    COMPONENTS_TO_BUILD = ["specific_improvements"]
    **Strategy:** Address specific quality gaps
﻿
**Build Focus:** {BUILD_FOCUS}
**Components to Add:** {COMPONENTS_TO_BUILD}
**Techniques to Integrate:** {TECHNIQUES_TO_ADD}
```
﻿
#### Component Generation Templates:
﻿
```
def generate_component(component_type, requirements, current_prompt=""):
    """
    Simple but effective component generation based on requirements
    """
    purpose = requirements.get('PROMPT_PURPOSE', '')
    input_type = requirements.get('INPUT_TYPE', 'input')
    output_type = requirements.get('OUTPUT_TYPE', 'output')
    complexity = requirements.get('COMPLEXITY_LEVEL', 'moderate')
﻿
    if component_type == "main_instruction":
        return generate_main_instruction(purpose, input_type, output_type, complexity)
    elif component_type == "reasoning_steps":
        return generate_reasoning_steps(purpose, complexity)
    elif component_type == "error_handling":
        return generate_error_handling(purpose)
    elif component_type == "validation_checks":
        return generate_validation_checks(output_type, purpose)
    elif component_type == "examples":
        return generate_examples(purpose, input_type, output_type)
    else:
        return f"## {component_type.replace('_', ' ').title()}\n[Component for {purpose}]"
﻿
def generate_main_instruction(purpose, input_type, output_type, complexity):
    """Generate clear main instruction based on simple parameters"""
﻿
    if 'analyze' in purpose.lower():
        instruction = f"Analyze the provided {input_type} and provide {output_type}."
        if complexity == 'advanced':
            instruction += " Use systematic analytical methods and provide detailed insights."
﻿
    elif 'create' in purpose.lower() or 'generate' in purpose.lower():
        instruction = f"Create {output_type} based on the {input_type}."
        if complexity == 'advanced':
            instruction += " Follow best practices and ensure high-quality output."
﻿
    elif 'solve' in purpose.lower() or 'problem' in purpose.lower():
        instruction = f"Solve the problem presented in the {input_type} and provide {output_type}."
        if complexity == 'advanced':
            instruction += " Use step-by-step problem-solving methodology."
    else:
        instruction = f"Process the {input_type} to produce {output_type}."
﻿
    return instruction
﻿
def generate_reasoning_steps(purpose, complexity):
    """Generate context-specific reasoning steps based on purpose analysis"""
﻿
    purpose_lower = purpose.lower()
﻿
    # Analyze what kind of analysis this is
    if any(word in purpose_lower for word in ['sentiment', 'emotion', 'feeling', 'opinion']):
        return generate_sentiment_analysis_steps(complexity)
    elif any(word in purpose_lower for word in ['data', 'statistics', 'metrics', 'numbers']):
        return generate_data_analysis_steps(complexity)
    elif any(word in purpose_lower for word in ['text', 'document', 'content', 'writing']):
        return generate_text_analysis_steps(complexity)
    elif any(word in purpose_lower for word in ['market', 'business', 'financial', 'economic']):
        return generate_business_analysis_steps(complexity)
    elif any(word in purpose_lower for word in ['code', 'software', 'technical', 'system']):
        return generate_technical_analysis_steps(complexity)
    elif 'analyze' in purpose_lower:
        return generate_generic_analysis_steps(complexity)
    elif any(word in purpose_lower for word in ['problem', 'solve', 'issue', 'troubleshoot']):
        return generate_problem_solving_steps(purpose_lower, complexity)
    elif any(word in purpose_lower for word in ['create', 'generate', 'build', 'design']):
        return generate_creation_steps(purpose_lower, complexity)
    else:
        return generate_generic_systematic_steps(complexity)
﻿
def generate_sentiment_analysis_steps(complexity):
    """Steps specifically for sentiment/emotion analysis"""
    if complexity == 'simple':
        return """Sentiment Analysis Approach:
1. Identify emotional indicators (positive/negative words)
2. Consider context and tone
3. Determine overall sentiment"""
    else:
        return """Comprehensive Sentiment Analysis:
1. Extract explicit emotional language and sentiment indicators
2. Analyze implicit tone, context, and subtext
3. Consider cultural and domain-specific nuances
4. Evaluate sentiment intensity and confidence levels
5. Provide balanced assessment with supporting evidence"""
﻿
def generate_data_analysis_steps(complexity):
    """Steps specifically for data/statistical analysis"""
    if complexity == 'simple':
        return """Data Analysis Approach:
1. Examine the data structure and key metrics
2. Identify trends, patterns, and outliers
3. Draw insights from the findings"""
    else:
        return """Systematic Data Analysis:
1. Assess data quality, completeness, and reliability
2. Apply appropriate statistical methods and frameworks
3. Identify significant patterns, correlations, and anomalies
4. Consider potential confounding factors and limitations
5. Generate actionable insights with confidence intervals"""
﻿
def generate_text_analysis_steps(complexity):
    """Steps specifically for text/content analysis"""
    if complexity == 'simple':
        return """Text Analysis Approach:
1. Identify main themes and key concepts
2. Examine structure, style, and tone
3. Summarize findings and implications"""
    else:
        return """Comprehensive Text Analysis:
1. Conduct structural analysis (organization, flow, coherence)
2. Perform thematic analysis (main ideas, supporting arguments)
3. Evaluate linguistic features (style, tone, rhetoric)
4. Assess effectiveness for intended purpose and audience
5. Identify strengths, weaknesses, and recommendations"""
﻿
def generate_business_analysis_steps(complexity):
    """Steps specifically for business/market analysis"""
    if complexity == 'simple':
        return """Business Analysis Approach:
1. Identify key business factors and stakeholders
2. Assess opportunities and risks
3. Provide strategic recommendations"""
    else:
        return """Strategic Business Analysis:
1. Analyze market context and competitive landscape
2. Evaluate internal capabilities and external factors
3. Assess financial implications and resource requirements
4. Identify risks, opportunities, and strategic options
5. Develop actionable recommendations with implementation considerations"""
﻿
def generate_technical_analysis_steps(complexity):
    """Steps specifically for technical/code analysis"""
    if complexity == 'simple':
        return """Technical Analysis Approach:
1. Review architecture and implementation approach
2. Identify potential issues and improvements
3. Provide technical recommendations"""
    else:
        return """Comprehensive Technical Analysis:
1. Evaluate system architecture and design patterns
2. Assess code quality, performance, and maintainability
3. Identify security vulnerabilities and technical debt
4. Consider scalability and future requirements
5. Recommend specific improvements with priority levels"""
﻿
def generate_problem_solving_steps(purpose_lower, complexity):
    """Context-specific problem solving based on problem type"""
    if any(word in purpose_lower for word in ['debug', 'error', 'bug', 'fix']):
        return """Debugging Approach:
1. Reproduce and isolate the problem
2. Analyze symptoms and potential root causes
3. Test solutions systematically
4. Verify the fix and prevent recurrence"""
    elif any(word in purpose_lower for word in ['optimize', 'improve', 'enhance']):
        return """Optimization Approach:
1. Establish current baseline and success metrics
2. Identify bottlenecks and improvement opportunities  
3. Design and test potential optimizations
4. Implement changes and measure results"""
    else:
        return """Problem-Solving Framework:
1. Define the problem clearly and completely
2. Generate multiple potential solutions
3. Evaluate options against key criteria
4. Implement the best solution and verify results"""
﻿
def generate_creation_steps(purpose_lower, complexity):
    """Context-specific creation steps based on what's being created"""
    if any(word in purpose_lower for word in ['strategy', 'plan', 'framework']):
        return """Strategic Creation Process:
1. Define objectives and success criteria
2. Research best practices and gather requirements
3. Design comprehensive framework or strategy
4. Validate approach and refine based on feedback"""
    elif any(word in purpose_lower for word in ['content', 'write', 'document']):
        return """Content Creation Process:
1. Define target audience and key messages
2. Create structured outline with main points
3. Develop content with appropriate tone and style
4. Review for clarity, accuracy, and effectiveness"""
    else:
        return """Creation Framework:
1. Define requirements and constraints
2. Research and gather relevant inputs
3. Design and build systematically
4. Test, refine, and finalize output"""
﻿
def generate_generic_analysis_steps(complexity):
    """Fallback for generic analysis tasks"""
    if complexity == 'simple':
        return """Analysis Approach:
1. Examine key components and relationships
2. Identify significant patterns or findings
3. Draw evidence-based conclusions"""
    else:
        return """Systematic Analysis Framework:
1. Define scope, objectives, and analytical approach
2. Gather and organize relevant information systematically
3. Apply appropriate analytical methods and frameworks
4. Synthesize findings and identify key insights
5. Present conclusions with supporting evidence and limitations"""
﻿
def generate_generic_systematic_steps(complexity):
    """Most generic fallback for any systematic task"""
    return """Systematic Approach:
1. Understand requirements and context
2. Plan your methodology and approach
3. Execute systematically with attention to detail
4. Review results and refine as needed"""
﻿
def generate_error_handling(purpose):
    """Generate simple error handling guidance"""
    return """If you encounter issues:
- State what clarification is needed
- Make reasonable assumptions if necessary
- Flag any limitations in your response"""
﻿
def generate_validation_checks(output_type, purpose):
    """Generate simple validation checks"""
    checks = ["Before finalizing, verify:"]
﻿
    if 'analysis' in purpose.lower():
        checks.extend([
            "- Key points are addressed",
            "- Conclusions are supported",
            "- Analysis is complete"
        ])
    elif 'creative' in purpose.lower():
        checks.extend([
            "- Output meets requirements",
            "- Creative elements are appropriate",
            "- Quality is high"
        ])
    else:
        checks.extend([
            "- Requirements are met",
            "- Quality is adequate",
            "- Output is complete"
        ])
﻿
    return '\n'.join(checks)
﻿
def generate_examples(purpose, input_type, output_type):
    """Generate context-specific examples based on purpose"""
    purpose_lower = purpose.lower()
﻿
    # Generate relevant examples based on task type
    if any(word in purpose_lower for word in ['sentiment', 'emotion', 'opinion']):
        return generate_sentiment_examples(input_type, output_type)
    elif any(word in purpose_lower for word in ['data', 'statistics', 'metrics']):
        return generate_data_examples(input_type, output_type)
    elif any(word in purpose_lower for word in ['code', 'technical', 'software']):
        return generate_technical_examples(input_type, output_type)
    elif any(word in purpose_lower for word in ['business', 'market', 'strategy']):
        return generate_business_examples(input_type, output_type)
    elif any(word in purpose_lower for word in ['text', 'document', 'content']):
        return generate_text_examples(input_type, output_type)
    elif 'analyze' in purpose_lower:
        return generate_analysis_examples(input_type, output_type, purpose)
    else:
        return generate_generic_examples(input_type, output_type, purpose)
﻿
def generate_sentiment_examples(input_type, output_type):
    return f"""## Example
﻿
**Input:** "I absolutely love this new feature! It makes everything so much easier and saves me tons of time."
﻿
**Output:** 
- **Sentiment:** Positive (Strong)
- **Confidence:** High (95%)
- **Key Indicators:** "absolutely love", "so much easier", "saves me tons of time"
- **Emotional Tone:** Enthusiastic and appreciative
- **Recommendation:** Feature is well-received, consider highlighting in marketing"""
﻿
def generate_data_examples(input_type, output_type):
    return f"""## Example
﻿
**Input:** Sales data showing Q4: $2.3M, Q3: $1.8M, Q2: $1.9M, Q1: $1.6M
﻿
**Output:**
- **Trend:** Consistent growth with 28% increase Q3→Q4
- **Key Pattern:** Strong Q4 performance (+44% vs Q1)
- **Notable:** Q2 slight dip, but recovery trend established
- **Projection:** If trend continues, Q1 next year could reach $2.8M
- **Recommendation:** Investigate Q4 success factors for replication"""
﻿
def generate_technical_examples(input_type, output_type):
    return f"""## Example
﻿
**Input:** Code snippet with nested loops processing large arrays
﻿
**Output:**
- **Performance Issue:** O(n²) time complexity in nested loops
- **Memory Concern:** Unnecessary array copies in inner loop
- **Maintainability:** Deep nesting reduces readability
- **Security:** No input validation on array bounds
- **Recommendation:** Implement single-pass algorithm with HashMap, add input validation"""
﻿
def generate_business_examples(input_type, output_type):
    return f"""## Example
﻿
**Input:** Market analysis request for entering the electric vehicle charging market
﻿
**Output:**
- **Market Size:** $31B globally, growing 25% annually
- **Key Players:** ChargePoint, Tesla Supercharger, EVgo
- **Barriers:** High infrastructure costs, regulatory complexity
- **Opportunities:** Partnership with retail chains, government incentives
- **Risk Assessment:** Medium-high initial investment, long-term growth potential
- **Recommendation:** Start with strategic partnerships before direct investment"""
﻿
def generate_text_examples(input_type, output_type):
    return f"""## Example
﻿
**Input:** Marketing email draft for product launch
﻿
**Output:**
- **Clarity:** Subject line clear but could be more compelling
- **Structure:** Good flow from problem→solution→action
- **Tone:** Professional but lacks excitement for launch
- **Call-to-Action:** Clear but positioned too late in email
- **Improvements:** Add urgency, move CTA higher, include social proof
- **Overall Grade:** B+ (effective but could be optimized)"""
﻿
def generate_analysis_examples(input_type, output_type, purpose):
    return f"""## Example
﻿
**Input:** {input_type} requiring {purpose}
﻿
**Output:**
- **Key Findings:** [Main discoveries from analysis]
- **Supporting Evidence:** [Data/facts that support conclusions]
- **Patterns Identified:** [Significant trends or relationships]
- **Implications:** [What these findings mean]
- **Recommendations:** [Actionable next steps based on analysis]
- **Confidence Level:** [How certain you are of conclusions]"""
﻿
def generate_generic_examples(input_type, output_type, purpose):
    return f"""## Example
﻿
**Input:** [Realistic sample {input_type}]
﻿
**Output:** [Detailed example of {output_type} that demonstrates:]
- Quality and depth expected
- Appropriate format and structure  
- Level of analysis or detail required
- Tone and style for {purpose}
﻿
**Note:** This example shows the standard expected for this type of {purpose} task."""
```
﻿
---
﻿
### 🎯 PHASE 3: DECIDE
**Select specific components to build this iteration**
﻿
Update prompt_gen.md using Edit tool:
```
### DECIDE - Implementation Plan
﻿
# Prioritize what to build
PRIORITY_COMPONENT = COMPONENTS_TO_BUILD[0]
IMPLEMENTATION_METHOD = "[How to implement this component]"
INTEGRATION_POINT = "[Where in prompt structure]"
EXPECTED_IMPACT = "[Quality improvement expected]"
﻿
**Primary Component:** {PRIORITY_COMPONENT}
**Implementation Method:** {IMPLEMENTATION_METHOD}
**Integration Point:** {INTEGRATION_POINT}
**Expected Quality Gain:** +10-15 points
﻿
# Design the component
COMPONENT_TEXT = generate_component(PRIORITY_COMPONENT)
**Component Design:**
```
{COMPONENT_TEXT}
```
```
﻿
---
﻿
### ⚡ PHASE 4: ACT
**Build and integrate the new component**
﻿
Update prompt_gen.md using Edit tool:
```
### ACT - Building Prompt
﻿
If LOOP_NUMBER == 1:
    # Create initial prompt structure using Write tool
    CURRENT_PROMPT = f"""# {PROMPT_PURPOSE}
﻿
## Instructions
{COMPONENT_TEXT}
﻿
## Input
[Specify input format]
﻿
## Output
[Specify output format]"""
﻿
Else:
    # Add to existing prompt using Edit tool
    CURRENT_PROMPT = f"""{PREVIOUS_PROMPT}
﻿
## {PRIORITY_COMPONENT}
{COMPONENT_TEXT}"""
﻿
# Update version and tracking
PROMPT_VERSION = f"v{LOOP_NUMBER}_{CURRENT_BUILD_STAGE}"
COMPONENTS_ADDED.append(PRIORITY_COMPONENT)
﻿
**Version Created:** {PROMPT_VERSION}
**Components Integrated:** {len(COMPONENTS_ADDED)} total
﻿
**Current Prompt:**
```markdown
{CURRENT_PROMPT}
```
﻿
# Store for next iteration
PREVIOUS_PROMPT = CURRENT_PROMPT
```
﻿
---
﻿
### 🔄 PHASE 5: CHECK & RE-LOOP
**Evaluate the generated prompt and determine next action**
﻿
Update prompt_gen.md using Edit tool:
```
### CHECK - Quality Assessment
﻿
def evaluate_prompt(current_prompt, requirements):
    """
    Realistic prompt quality evaluation with simple but meaningful assessment
    """
    assessment = {
        'clarity_score': 0,
        'completeness_score': 0, 
        'effectiveness_score': 0,
        'robustness_score': 0,
        'issues': [],
        'strengths': []
    }
﻿
    # CLARITY ASSESSMENT (0-25 points) - Simple but meaningful
    if len(current_prompt.strip()) > 50:
        assessment['clarity_score'] += 5
        assessment['strengths'].append("Substantial instruction content")
    else:
        assessment['issues'].append("Too brief - needs more detailed instructions")
﻿
    if any(word in current_prompt.lower() for word in ['task', 'goal', 'objective']):
        assessment['clarity_score'] += 10
        assessment['strengths'].append("Clear task definition present")
    else:
        assessment['issues'].append("Missing clear task definition")
﻿
    # Check for ambiguous language
    ambiguous_terms = ['might', 'maybe', 'perhaps', 'things', 'stuff', 'appropriate', 'good']
    ambiguity_count = sum(1 for term in ambiguous_terms if term in current_prompt.lower())
    if ambiguity_count == 0:
        assessment['clarity_score'] += 10
        assessment['strengths'].append("Language is precise and specific")
    elif ambiguity_count <= 2:
        assessment['clarity_score'] += 5
    else:
        assessment['issues'].append(f"Contains {ambiguity_count} ambiguous terms")
﻿
    # COMPLETENESS ASSESSMENT (0-25 points)
    essential_sections = ['input', 'output', 'instruction']
    present_sections = [section for section in essential_sections 
                       if section in current_prompt.lower()]
﻿
    assessment['completeness_score'] = len(present_sections) * 8
    if len(present_sections) == 3:
        assessment['strengths'].append("All essential sections present")
    else:
        missing = [s for s in essential_sections if s not in present_sections]
        assessment['issues'].append(f"Missing sections: {missing}")
﻿
    # EFFECTIVENESS ASSESSMENT (0-25 points) - Context-specific evaluation
    purpose = requirements['PROMPT_PURPOSE'].lower()
﻿
    # Domain-specific effectiveness checks
    if any(word in purpose for word in ['sentiment', 'emotion', 'opinion']):
        effectiveness_score = assess_sentiment_analysis_effectiveness(current_prompt)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    elif any(word in purpose for word in ['data', 'statistics', 'metrics']):
        effectiveness_score = assess_data_analysis_effectiveness(current_prompt)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    elif any(word in purpose for word in ['code', 'technical', 'software']):
        effectiveness_score = assess_technical_effectiveness(current_prompt)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    elif any(word in purpose for word in ['business', 'market', 'strategy']):
        effectiveness_score = assess_business_effectiveness(current_prompt)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    elif 'analyze' in purpose or 'analysis' in purpose:
        effectiveness_score = assess_analysis_effectiveness(current_prompt, purpose)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    elif 'create' in purpose or 'generate' in purpose:
        effectiveness_score = assess_creation_effectiveness(current_prompt, purpose)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    elif 'solve' in purpose or 'problem' in purpose:
        effectiveness_score = assess_problem_solving_effectiveness(current_prompt, purpose)
        assessment['effectiveness_score'] += effectiveness_score['score']
        assessment['strengths'].extend(effectiveness_score['strengths'])
        assessment['issues'].extend(effectiveness_score['issues'])
﻿
    else:
        # Generic effectiveness check with basic alignment
        alignment_score = assess_generic_effectiveness(current_prompt, requirements)
        assessment['effectiveness_score'] += alignment_score['score']
        assessment['strengths'].extend(alignment_score['strengths'])
        assessment['issues'].extend(alignment_score['issues'])
﻿
def assess_sentiment_analysis_effectiveness(prompt):
    """Assess effectiveness specifically for sentiment analysis tasks"""
    score = 0
    strengths = []
    issues = []
﻿
    if any(word in prompt.lower() for word in ['sentiment', 'emotion', 'tone']):
        score += 8
        strengths.append("Explicitly mentions sentiment/emotion analysis")
    else:
        issues.append("Should explicitly reference sentiment or emotional analysis")
﻿
    if any(word in prompt.lower() for word in ['context', 'nuance', 'subtext']):
        score += 7
        strengths.append("Considers contextual factors beyond surface language")
    else:
        issues.append("Should emphasize importance of context in sentiment analysis")
﻿
    if any(word in prompt.lower() for word in ['confidence', 'intensity', 'degree']):
        score += 5
        strengths.append("Addresses sentiment strength/confidence")
    else:
        issues.append("Should specify need to assess sentiment intensity")
﻿
    if any(word in prompt.lower() for word in ['bias', 'objective', 'balanced']):
        score += 5
        strengths.append("Includes objectivity considerations")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_data_analysis_effectiveness(prompt):
    """Assess effectiveness specifically for data analysis tasks"""
    score = 0
    strengths = []
    issues = []
﻿
    if any(word in prompt.lower() for word in ['pattern', 'trend', 'correlation']):
        score += 8
        strengths.append("Focuses on identifying data patterns and trends")
    else:
        issues.append("Should emphasize pattern and trend identification")
﻿
    if any(word in prompt.lower() for word in ['statistical', 'significance', 'confidence']):
        score += 7
        strengths.append("Considers statistical rigor and significance")
    else:
        issues.append("Should address statistical significance and confidence")
﻿
    if any(word in prompt.lower() for word in ['outlier', 'anomaly', 'exception']):
        score += 5
        strengths.append("Includes attention to outliers and anomalies")
﻿
    if any(word in prompt.lower() for word in ['limitation', 'assumption', 'caveat']):
        score += 5
        strengths.append("Acknowledges analytical limitations")
    else:
        issues.append("Should mention analytical limitations and assumptions")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_technical_effectiveness(prompt):
    """Assess effectiveness for technical/code analysis"""
    score = 0
    strengths = []
    issues = []
﻿
    if any(word in prompt.lower() for word in ['performance', 'scalability', 'efficiency']):
        score += 8
        strengths.append("Addresses performance and scalability concerns")
    else:
        issues.append("Should consider performance and scalability factors")
﻿
    if any(word in prompt.lower() for word in ['security', 'vulnerability', 'risk']):
        score += 7
        strengths.append("Includes security considerations")
    else:
        issues.append("Should address security implications")
﻿
    if any(word in prompt.lower() for word in ['maintainability', 'readable', 'clean']):
        score += 5
        strengths.append("Considers code quality and maintainability")
﻿
    if any(word in prompt.lower() for word in ['best practice', 'standard', 'convention']):
        score += 5
        strengths.append("References industry best practices")
    else:
        issues.append("Should reference relevant technical standards")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_business_effectiveness(prompt):
    """Assess effectiveness for business analysis"""
    score = 0
    strengths = []
    issues = []
﻿
    if any(word in prompt.lower() for word in ['stakeholder', 'impact', 'business value']):
        score += 8
        strengths.append("Considers stakeholder impact and business value")
    else:
        issues.append("Should address stakeholder impact and business value")
﻿
    if any(word in prompt.lower() for word in ['risk', 'opportunity', 'threat']):
        score += 7
        strengths.append("Includes risk and opportunity assessment")
    else:
        issues.append("Should evaluate risks and opportunities")
﻿
    if any(word in prompt.lower() for word in ['actionable', 'implement', 'execute']):
        score += 5
        strengths.append("Emphasizes actionable recommendations")
    else:
        issues.append("Should focus on actionable business recommendations")
﻿
    if any(word in prompt.lower() for word in ['roi', 'cost', 'benefit', 'resource']):
        score += 5
        strengths.append("Addresses resource and financial considerations")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_analysis_effectiveness(prompt, purpose):
    """Generic analysis effectiveness assessment"""
    score = 0
    strengths = []
    issues = []
﻿
    if any(word in prompt.lower() for word in ['systematic', 'methodical', 'structured']):
        score += 10
        strengths.append("Promotes systematic analytical approach")
    else:
        issues.append("Should emphasize systematic analytical methodology")
﻿
    if any(word in prompt.lower() for word in ['evidence', 'support', 'justify']):
        score += 8
        strengths.append("Requires evidence-based conclusions")
    else:
        issues.append("Should require evidence to support conclusions")
﻿
    if any(word in prompt.lower() for word in ['comprehensive', 'thorough', 'complete']):
        score += 7
        strengths.append("Emphasizes thoroughness in analysis")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_creation_effectiveness(prompt, purpose):
    """Assess effectiveness for creative/generative tasks"""
    score = 0
    strengths = []
    issues = []
﻿
    if 'example' in prompt.lower():
        score += 10
        strengths.append("Provides examples to guide creation")
    else:
        issues.append("Should include examples to guide creative output")
﻿
    if any(word in prompt.lower() for word in ['format', 'structure', 'template']):
        score += 8
        strengths.append("Specifies output format and structure")
    else:
        issues.append("Should specify desired format and structure")
﻿
    if any(word in prompt.lower() for word in ['quality', 'standard', 'criteria']):
        score += 7
        strengths.append("Establishes quality standards")
    else:
        issues.append("Should establish quality criteria for output")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_problem_solving_effectiveness(prompt, purpose):
    """Assess effectiveness for problem-solving tasks"""
    score = 0
    strengths = []
    issues = []
﻿
    if any(word in prompt.lower() for word in ['step', 'approach', 'method', 'process']):
        score += 12
        strengths.append("Provides structured problem-solving approach")
    else:
        issues.append("Should provide clear problem-solving methodology")
﻿
    if any(word in prompt.lower() for word in ['root cause', 'underlying', 'source']):
        score += 8
        strengths.append("Emphasizes identifying root causes")
    else:
        issues.append("Should emphasize finding root causes, not just symptoms")
﻿
    if any(word in prompt.lower() for word in ['solution', 'alternative', 'option']):
        score += 5
        strengths.append("Encourages exploring multiple solutions")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
def assess_generic_effectiveness(prompt, requirements):
    """Basic effectiveness assessment for unspecified tasks"""
    score = 0
    strengths = []
    issues = []
﻿
    # Check purpose alignment
    purpose_words = requirements['PROMPT_PURPOSE'].lower().split()
    alignment_count = sum(1 for word in purpose_words if word in prompt.lower())
﻿
    if alignment_count > len(purpose_words) * 0.5:
        score += 10
        strengths.append("Good alignment with stated purpose")
    else:
        score += 5
        issues.append("Could improve alignment with stated purpose")
﻿
    # Check for detail and structure
    if len(prompt) > 200:
        score += 8
        strengths.append("Provides detailed guidance")
    elif len(prompt) > 100:
        score += 5
    else:
        issues.append("Needs more detailed instructions")
﻿
    if any(word in prompt.lower() for word in ['step', 'process', 'approach']):
        score += 7
        strengths.append("Includes structured approach")
    else:
        issues.append("Should provide structured approach or methodology")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
# Continue with ROBUSTNESS ASSESSMENT (0-25 points) - Simplified
def evaluate_robustness(current_prompt):
    """Evaluate robustness of the prompt"""
    score = 0
    strengths = []
    issues = []
﻿
    if 'error' in current_prompt.lower() or 'if' in current_prompt.lower():
        score += 10
        strengths.append("Includes error handling guidance")
    else:
        issues.append("No error handling or edge case guidance")
﻿
    if 'verify' in current_prompt.lower() or 'check' in current_prompt.lower():
        score += 10
        strengths.append("Includes verification steps")
    else:
        issues.append("Missing verification/quality check steps")
﻿
    if len(current_prompt) > 300:  # Longer prompts tend to be more robust
        score += 5
        strengths.append("Comprehensive instruction set")
﻿
    return {'score': score, 'strengths': strengths, 'issues': issues}
﻿
# Complete the evaluate_prompt function
def complete_evaluate_prompt(current_prompt, requirements):
    """Complete evaluation function with all assessments"""
    assessment = {
        'clarity_score': 0,
        'completeness_score': 0, 
        'effectiveness_score': 0,
        'robustness_score': 0,
        'issues': [],
        'strengths': []
    }
﻿
    # Run all assessments and combine
    robustness_result = evaluate_robustness(current_prompt)
    assessment['robustness_score'] = robustness_result['score']
    assessment['strengths'].extend(robustness_result['strengths'])
    assessment['issues'].extend(robustness_result['issues'])
﻿
    total_score = (assessment['clarity_score'] + 
                  assessment['completeness_score'] +
                  assessment['effectiveness_score'] +
                  assessment['robustness_score'])
﻿
    return total_score, assessment
﻿
# Add utility functions
def format_list(items):
    """Format list items for display"""
    if not items:
        return "None identified"
    return '\n'.join(f"  - {item}" for item in items)
﻿
# Updated evaluation call
NEW_QUALITY_SCORE, DETAILED_ASSESSMENT = evaluate_prompt(CURRENT_PROMPT, requirements)
SCORE_IMPROVEMENT = NEW_QUALITY_SCORE - QUALITY_SCORE
QUALITY_SCORE = NEW_QUALITY_SCORE
﻿
**Previous Score:** {QUALITY_SCORE - SCORE_IMPROVEMENT}/100
**New Score:** {QUALITY_SCORE}/100
**Improvement:** +{SCORE_IMPROVEMENT} points
﻿
**Detailed Assessment:**
- Clarity: {DETAILED_ASSESSMENT['clarity_score']}/25
- Completeness: {DETAILED_ASSESSMENT['completeness_score']}/25  
- Effectiveness: {DETAILED_ASSESSMENT['effectiveness_score']}/25
- Robustness: {DETAILED_ASSESSMENT['robustness_score']}/25
﻿
**Identified Strengths:**
{format_list(DETAILED_ASSESSMENT['strengths'])}
﻿
**Issues to Address:**
{format_list(DETAILED_ASSESSMENT['issues'])}
﻿
**Purpose-Specific Effectiveness Analysis:**
{generate_purpose_effectiveness_analysis(CURRENT_PROMPT, requirements, DETAILED_ASSESSMENT)}
﻿
# Determine next action
if LOOP_NUMBER >= 6:
    NEXT_ACTION = "Complete" # All 6 loops completed
else:
    NEXT_ACTION = "Continue" # Continue to next required loop
﻿
### LOOP SUMMARY
**Quality Achievement:** {QUALITY_SCORE}/{TARGET_SCORE}
**Components Built:** {len(COMPONENTS_ADDED)}/{len(REQUIRED_COMPONENTS)}
**Next Action:** {NEXT_ACTION}
```
﻿
---
﻿
## QUALITY SCORE PURPOSE
Quality scores are for **tracking improvement**, not termination decisions.
- Scores help identify what each loop contributes
- High early scores may indicate missing advanced components
- Final score only meaningful after all 6 loops completed
- Target score is a guideline, not a stopping condition
﻿
### LOOP PROGRESSION LOGIC
- Loops 1-5: Always continue to next loop
- Loop 6: Complete with final assessment
﻿
**Current Loop Status:**
- If LOOP_NUMBER < 6: Prepare for Loop {LOOP_NUMBER + 1}
- If LOOP_NUMBER = 6: Finalize prompt generation
﻿
## LOOP COMPLETION VERIFICATION
Each loop must address its designated purpose:
- Loop 1: ✅ Foundation established
- Loop 2: ✅ Core methodology implemented
- Loop 3: ✅ Examples and validation added
- Loop 4: ✅ Advanced techniques integrated
- Loop 5: ✅ Edge cases and optimization handled
- Loop 6: ✅ Meta-instructions and final polish completed
﻿
**Only mark complete when all 6 purposes fulfilled.**
﻿
## 🏆 COMPLETION PROTOCOL
**Execute when all 6 loops have been completed**
﻿
### Final Generation Report:
Use Edit tool to add to prompt_gen.md:
```
## FINAL GENERATED PROMPT - {timestamp}
**Version:** {PROMPT_VERSION}
**Final Quality Score:** {QUALITY_SCORE}/100
**Build Loops:** {LOOP_NUMBER}
**Components Integrated:** {COMPONENTS_ADDED}
```
﻿
### Quality Certification:
```markdown
## Quality Assessment
﻿
| Aspect | Score | Status |
|--------|-------|--------|
| Completeness | [X/25] | ✅ All required components present |
| Clarity | [X/25] | ✅ Instructions are clear and unambiguous |
| Robustness | [X/25] | ✅ Error handling and edge cases covered |
| Efficiency | [X/25] | ✅ Optimized for token usage and performance |
﻿
**Overall Rating:** {QUALITY_SCORE}/100 - Production Ready
```
﻿
### 📁 File Output Generation:
Use Write tool to create output file:
```
# Create output file with timestamp
TIMESTAMP = current_timestamp()
OUTPUT_FILE = f"prompt_clean_{TIMESTAMP}.md"
﻿
# Save clean prompt only using Write tool
Write(OUTPUT_FILE, CURRENT_PROMPT)
﻿
# Update prompt_gen.md with completion info
**Output File:** {OUTPUT_FILE}
**Quality Score:** {QUALITY_SCORE}/100
**Build Loops:** {LOOP_NUMBER}
﻿
# Display completion message
✅ Prompt generation complete!
📊 Quality Score: {QUALITY_SCORE}/100
🏗️ Components Built: {len(COMPONENTS_ADDED)}
🔄 Build Loops: {LOOP_NUMBER}
📁 Generated prompt saved to: {OUTPUT_FILE}
```
﻿
def generate_purpose_effectiveness_analysis(prompt, requirements, assessment):
    """Generate simple effectiveness analysis based on purpose"""
    purpose = requirements.get('PROMPT_PURPOSE', '').lower()
    analysis = []
﻿
    # Basic purpose alignment check
    purpose_words = purpose.split()
    alignment_score = sum(1 for word in purpose_words if word in prompt.lower())
﻿
    if alignment_score > len(purpose_words) * 0.5:
        analysis.append("✅ Good alignment with stated purpose")
    else:
        analysis.append("⚠️ Could improve alignment with stated purpose")
﻿
    # Task-specific checks
    if 'analysis' in purpose or 'analyze' in purpose:
        if any(word in prompt.lower() for word in ['step', 'method', 'systematic']):
            analysis.append("✅ Includes structured analytical approach")
        else:
            analysis.append("⚠️ Would benefit from structured analytical steps")
﻿
    elif 'create' in purpose or 'generate' in purpose:
        if 'example' in prompt.lower():
            analysis.append("✅ Provides guidance through examples")
        else:
            analysis.append("⚠️ Could benefit from examples or templates")
﻿
    elif 'solve' in purpose or 'problem' in purpose:
        if any(word in prompt.lower() for word in ['step', 'approach', 'method']):
            analysis.append("✅ Provides problem-solving methodology")
        else:
            analysis.append("⚠️ Needs clearer problem-solving steps")
﻿
    return "**Purpose Effectiveness Analysis:**\n" + '\n'.join(f"  {item}" for item in analysis)
﻿
---
﻿
## GENERATION STRATEGIES
﻿
### Component Building Blocks
﻿
| Component Type | Purpose | Quality Impact |
|----------------|---------|----------------|
| **Main Instruction** | Core task definition | +15-20 points |
| **Role Definition** | Establish expertise/persona | +10-15 points |
| **Input Specification** | Define expected inputs | +10 points |
| **Output Specification** | Define expected outputs | +10 points |
| **Step-by-Step Process** | Break down complex tasks | +10-15 points |
| **Examples** | Provide concrete illustrations | +10-15 points |
| **Constraints** | Set boundaries and limits | +5-10 points |
| **Error Handling** | Manage edge cases | +10 points |
| **Validation Checks** | Ensure quality outputs | +5-10 points |
| **Reasoning Framework** | Add thinking structure | +15-20 points |
﻿
### Advanced Techniques Integration
﻿
#### When to Add Each Technique:
- **Loop 1-2**: Basic structure and instructions
- **Loop 3**: Chain-of-Thought or reasoning steps
- **Loop 4**: Examples and validation
- **Loop 5**: Error handling and edge cases
- **Loop 6**: Final optimizations and polish
﻿
### Architecture Patterns
﻿
#### Simple Task Pattern:
```
1. Clear instruction
2. Input format
3. Output format
4. Basic constraints
```
﻿
#### Complex Analysis Pattern:
```
1. Role and expertise
2. Context and background
3. Step-by-step methodology
4. Reasoning framework
5. Validation criteria
6. Output structure
```
﻿
#### System Framework Pattern:
```
1. System architecture
2. Component definitions
3. Integration points
4. Control flow
5. Error recovery
6. Meta-instructions
```
﻿
---
﻿
## EXAMPLE GENERATION SESSION
﻿
```markdown
# Prompt Generation Session - 2024-01-14 10:00:00
## Requirements Specification:
"I need a prompt that helps analyze customer feedback and extract actionable insights"
﻿
---
﻿
## Loop 1 - 2024-01-14 10:00:30
**Build Stage:** foundation
**Goal:** Build foundation layer
**Architecture:** Analytical/Reasoning
﻿
### OBSERVE - Current State
**Starting Point:** Requirements only
**Components Needed:** context method reasoning validation
﻿
### ORIENT - Build Strategy
**Strategy:** Establish basic prompt skeleton
**Build Focus:** Core Structure
﻿
### DECIDE - Implementation Plan
**Primary Component:** main_instruction
﻿
### ACT - Building Prompt
**Current Prompt:**
```
# Customer Feedback Analysis
﻿
## Instructions
You are tasked with analyzing customer feedback to extract actionable insights.
Your goal is to identify patterns, sentiment, and specific improvement suggestions.
﻿
## Input
[Customer feedback text]
﻿
## Output
- Overall sentiment
- Key themes
- Actionable recommendations
```
﻿
### CHECK - Quality Assessment
**New Score:** 35/100
﻿
---
﻿
## Loop 2 - 2024-01-14 10:02:00
[Adds reasoning framework, validation steps...]
﻿
---
﻿
## FINAL GENERATED PROMPT
**Quality Score:** 92/100
[Complete generated prompt with all components...]
```
﻿
---
﻿
## BUILD LEVEL PROGRESSION
﻿
### Foundation (Loops 1-2)
- Core instructions
- Basic I/O specifications
- Initial constraints
﻿
### Enhancement (Loops 3-4)
- Reasoning chains
- Validation methods
- Examples
﻿
### Polish (Loops 5-6)
- Edge case handling
- Performance optimization
- Final refinements
﻿
---
﻿
**Implementation Notes for Claude Code:**
- Use Write tool to create initial prompt_gen.md
- Use Edit tool to update sections iteratively  
- Use Write tool to create final clean prompt file
- Replace bash variables with Python-style variable tracking
- Use TodoWrite tool to track loop progress
- Maintain all core OODA loop logic and quality scoring
- Preserve complete component library and architecture patterns
﻿
**Remember:** Each loop builds upon the previous, gradually constructing a comprehensive, high-quality prompt tailored to the specific requirements.
