# Adaptive Prompt Improvement Loop Protocol

## INITIALIZATION
Enter **Adaptive Prompt Improvement Mode**. Operate as an iterative prompt refinement system using the OODA Loop (Observe, Orient, Decide, Act) to enhance prompts through focused, domain-aware improvements.

### Loop Control Variables:
```python
LOOP_NUMBER = 0
IMPROVEMENTS_APPLIED = []
PROMPT_VERSION = "v0_baseline"
IMPROVEMENT_START_TIME = current_timestamp()
QUALITY_SCORE = 0
TARGET_SCORE = 90
PROMPT_DOMAIN = ""
PROMPT_PURPOSE = ""
```

### Initialize Improvement Log:
```python
# Create improvement session log
log_file = f"prompt_improvement_{IMPROVEMENT_START_TIME}.md"
with open(log_file, 'w') as f:
    f.write(f"# Prompt Improvement Session - {IMPROVEMENT_START_TIME}\n")
    f.write("## Original Prompt\n")
    f.write(f"```\n{ORIGINAL_PROMPT}\n```\n")
    f.write("---\n\n")
```

## PRE-LOOP ANALYSIS
Establish baseline understanding and targets:

### Enhanced Domain Detection:
```python
def detect_prompt_domain(prompt):
    """Identify the primary domain, subtype, and specific focus of the prompt"""
    prompt_lower = prompt.lower()

    domain_indicators = {
        'analysis': {
            'keywords': ['analyze', 'examine', 'evaluate', 'assess', 'investigate', 'review', 'study'],
            'subtypes': {
                'sentiment': {
                    'keywords': ['sentiment', 'emotion', 'feeling', 'opinion', 'tone', 'mood', 'attitude'],
                    'specific_focus': detect_sentiment_focus
                },
                'data': {
                    'keywords': ['data', 'statistics', 'metrics', 'numbers', 'trends', 'patterns', 'correlation'],
                    'specific_focus': detect_data_focus
                },
                'text': {
                    'keywords': ['text', 'document', 'content', 'writing', 'article', 'passage', 'literature'],
                    'specific_focus': detect_text_focus
                },
                'business': {
                    'keywords': ['market', 'business', 'strategy', 'financial', 'roi', 'revenue', 'profit'],
                    'specific_focus': detect_business_focus
                },
                'scientific': {
                    'keywords': ['research', 'hypothesis', 'experiment', 'scientific', 'study', 'evidence'],
                    'specific_focus': detect_scientific_focus
                }
            }
        },
        'creative': {
            'keywords': ['create', 'generate', 'write', 'design', 'imagine', 'develop', 'craft'],
            'subtypes': {
                'story': {
                    'keywords': ['story', 'narrative', 'fiction', 'tale', 'plot', 'character', 'scene'],
                    'specific_focus': detect_story_focus
                },
                'content': {
                    'keywords': ['content', 'copy', 'blog', 'article', 'post', 'marketing', 'email'],
                    'specific_focus': detect_content_focus
                },
                'design': {
                    'keywords': ['design', 'layout', 'visual', 'interface', 'ui', 'ux', 'graphic'],
                    'specific_focus': detect_design_focus
                },
                'poetry': {
                    'keywords': ['poem', 'poetry', 'verse', 'rhyme', 'haiku', 'sonnet'],
                    'specific_focus': detect_poetry_focus
                }
            }
        },
        'technical': {
            'keywords': ['code', 'program', 'debug', 'implement', 'develop', 'software', 'function'],
            'subtypes': {
                'debugging': {
                    'keywords': ['debug', 'fix', 'error', 'bug', 'issue', 'problem', 'crash'],
                    'specific_focus': detect_debugging_focus
                },
                'architecture': {
                    'keywords': ['architecture', 'design', 'structure', 'system', 'pattern', 'framework'],
                    'specific_focus': detect_architecture_focus
                },
                'optimization': {
                    'keywords': ['optimize', 'performance', 'efficiency', 'speed', 'memory', 'scale'],
                    'specific_focus': detect_optimization_focus
                },
                'implementation': {
                    'keywords': ['implement', 'build', 'create', 'develop', 'construct'],
                    'specific_focus': detect_implementation_focus
                }
            }
        },
        'problem_solving': {
            'keywords': ['solve', 'troubleshoot', 'fix', 'resolve', 'address', 'handle', 'tackle'],
            'subtypes': {
                'mathematical': {
                    'keywords': ['equation', 'calculate', 'math', 'formula', 'computation', 'algebra'],
                    'specific_focus': detect_math_focus
                },
                'logical': {
                    'keywords': ['logic', 'reasoning', 'deduce', 'infer', 'conclude'],
                    'specific_focus': detect_logic_focus
                },
                'strategic': {
                    'keywords': ['strategic', 'planning', 'decision', 'approach', 'tactics'],
                    'specific_focus': detect_strategy_focus
                }
            }
        }
    }

    # Detect primary domain with weighted scoring
    domain_scores = {}
    for domain, config in domain_indicators.items():
        score = 0
        for keyword in config['keywords']:
            if keyword in prompt_lower:
                # Weight by position (earlier = more important)
                position_weight = 1.0 - (prompt_lower.index(keyword) / len(prompt_lower))
                score += (1 + position_weight)
        domain_scores[domain] = score

    primary_domain = max(domain_scores.items(), key=lambda x: x[1])[0]

    # Detect subtype with specificity
    subtype = 'general'
    specific_focus = None
    if primary_domain in domain_indicators:
        subtype_scores = {}
        for sub_name, sub_config in domain_indicators[primary_domain].get('subtypes', {}).items():
            score = sum(2 for keyword in sub_config['keywords'] if keyword in prompt_lower)
            subtype_scores[sub_name] = score

        if subtype_scores:
            best_subtype = max(subtype_scores.items(), key=lambda x: x[1])
            if best_subtype[1] > 0:
                subtype = best_subtype[0]
                # Get specific focus within subtype
                specific_focus = domain_indicators[primary_domain]['subtypes'][subtype]['specific_focus'](prompt_lower)

    return {
        'domain': primary_domain,
        'subtype': subtype,
        'specific_focus': specific_focus,
        'confidence': max(domain_scores.values()) / len(prompt.split()) * 100
    }

def detect_sentiment_focus(prompt):
    """Detect specific type of sentiment analysis needed"""
    if 'customer' in prompt or 'review' in prompt:
        return 'customer_feedback'
    elif 'social' in prompt or 'media' in prompt:
        return 'social_media'
    elif 'brand' in prompt or 'product' in prompt:
        return 'brand_perception'
    return 'general_sentiment'

def detect_data_focus(prompt):
    """Detect specific type of data analysis needed"""
    if 'time' in prompt or 'trend' in prompt or 'forecast' in prompt:
        return 'time_series'
    elif 'correlation' in prompt or 'relationship' in prompt:
        return 'correlation_analysis'
    elif 'distribution' in prompt or 'frequency' in prompt:
        return 'distribution_analysis'
    elif 'compare' in prompt or 'difference' in prompt:
        return 'comparative_analysis'
    return 'descriptive_statistics'

def detect_text_focus(prompt):
    """Detect specific type of text analysis needed"""
    if 'summary' in prompt or 'summarize' in prompt:
        return 'summarization'
    elif 'theme' in prompt or 'topic' in prompt:
        return 'thematic_analysis'
    elif 'style' in prompt or 'tone' in prompt:
        return 'stylistic_analysis'
    elif 'structure' in prompt or 'organization' in prompt:
        return 'structural_analysis'
    return 'content_analysis'

def detect_business_focus(prompt):
    """Detect specific type of business analysis needed"""
    if 'market' in prompt or 'competitive' in prompt:
        return 'market_analysis'
    elif 'financial' in prompt or 'revenue' in prompt or 'cost' in prompt:
        return 'financial_analysis'
    elif 'strategy' in prompt or 'strategic' in prompt:
        return 'strategic_analysis'
    elif 'customer' in prompt or 'user' in prompt:
        return 'customer_analysis'
    return 'business_analysis'

def detect_story_focus(prompt):
    """Detect specific type of story needed"""
    if 'short' in prompt:
        return 'short_story'
    elif 'novel' in prompt or 'chapter' in prompt:
        return 'novel_chapter'
    elif 'children' in prompt or 'kids' in prompt:
        return 'childrens_story'
    elif 'sci-fi' in prompt or 'science fiction' in prompt:
        return 'science_fiction'
    return 'general_fiction'

def detect_debugging_focus(prompt):
    """Detect specific debugging context"""
    if 'runtime' in prompt or 'crash' in prompt:
        return 'runtime_error'
    elif 'logic' in prompt or 'incorrect' in prompt:
        return 'logic_error'
    elif 'performance' in prompt or 'slow' in prompt:
        return 'performance_issue'
    elif 'memory' in prompt or 'leak' in prompt:
        return 'memory_issue'
    return 'general_debugging'
```

---

## THE IMPROVEMENT OODA LOOP

### ⭕ PHASE 0: CLASSIFICATION & INITIAL ASSESSMENT

```python
def classify_and_assess(prompt):
    """Perform comprehensive classification and quality assessment"""

    # Enhanced domain detection
    domain_info = detect_prompt_domain(prompt)

    # Multi-dimensional assessment
    initial_assessment = {
        'clarity': assess_clarity_detailed(prompt),
        'specificity': assess_specificity_detailed(prompt, domain_info),
        'completeness': assess_completeness_detailed(prompt, domain_info),
        'structure': assess_structure_detailed(prompt),
        'domain_fitness': assess_domain_fitness_detailed(prompt, domain_info),
        'technical_soundness': assess_technical_soundness(prompt, domain_info)
    }

    # Calculate weighted score based on domain
    score_weights = get_domain_weights(domain_info)
    initial_score = 0
    for metric, assessment in initial_assessment.items():
        weight = score_weights.get(metric, 1.0)
        initial_score += assessment['score'] * weight
    initial_score = initial_score / len(initial_assessment) * 20

    # Identify critical issues with domain context
    critical_issues = identify_critical_issues(initial_assessment, domain_info)

    return {
        'domain': domain_info,
        'initial_score': initial_score,
        'assessment': initial_assessment,
        'critical_issues': critical_issues
    }

def assess_clarity_detailed(prompt):
    """Enhanced clarity assessment with specific issue identification"""
    issues = []
    score = 5

    # Check for ambiguous terms
    ambiguous_terms = {
        'vague_qualifiers': ['appropriate', 'good', 'better', 'nice', 'proper', 'suitable'],
        'unclear_references': ['it', 'this', 'that', 'these', 'those'],
        'imprecise_quantities': ['some', 'many', 'few', 'several', 'various'],
        'generic_nouns': ['things', 'stuff', 'items', 'aspects', 'elements']
    }

    for category, terms in ambiguous_terms.items():
        found = [term for term in terms if term in prompt.lower()]
        if found:
            issues.append(f"{category}: {', '.join(found)}")
            score -= len(found) * 0.3

    # Check for clear action verbs
    action_verbs = ['analyze', 'create', 'evaluate', 'generate', 'solve', 'implement']
    if not any(verb in prompt.lower() for verb in action_verbs):
        issues.append("No clear action verb")
        score -= 1

    return {
        'score': max(1, min(5, score)),
        'issues': issues
    }

def assess_specificity_detailed(prompt, domain_info):
    """Domain-aware specificity assessment"""
    score = 5
    issues = []

    # Domain-specific requirements
    if domain_info['domain'] == 'analysis':
        required_specs = {
            'data': ['input format', 'output format', 'metrics'],
            'sentiment': ['scale', 'confidence level', 'categories'],
            'text': ['length', 'structure', 'focus areas'],
            'business': ['timeframe', 'metrics', 'stakeholders']
        }

        specs_needed = required_specs.get(domain_info['subtype'], [])
        for spec in specs_needed:
            if spec.replace('_', ' ') not in prompt.lower():
                issues.append(f"Missing {spec}")
                score -= 0.5

    elif domain_info['domain'] == 'creative':
        if 'words' not in prompt.lower() and 'length' not in prompt.lower():
            issues.append("No length specification")
            score -= 1
        if 'audience' not in prompt.lower() and 'reader' not in prompt.lower():
            issues.append("No target audience")
            score -= 1
        if 'style' not in prompt.lower() and 'tone' not in prompt.lower():
            issues.append("No style/tone guidance")
            score -= 0.5

    return {
        'score': max(1, min(5, score)),
        'issues': issues
    }

def get_domain_weights(domain_info):
    """Return importance weights for quality metrics based on domain"""
    weights = {
        'analysis': {
            'clarity': 1.2,
            'specificity': 1.5,
            'completeness': 1.3,
            'structure': 1.0,
            'domain_fitness': 1.4,
            'technical_soundness': 1.5
        },
        'creative': {
            'clarity': 1.0,
            'specificity': 0.8,
            'completeness': 1.0,
            'structure': 0.7,
            'domain_fitness': 1.2,
            'technical_soundness': 0.5
        },
        'technical': {
            'clarity': 1.3,
            'specificity': 1.5,
            'completeness': 1.4,
            'structure': 1.2,
            'domain_fitness': 1.3,
            'technical_soundness': 1.8
        }
    }
    return weights.get(domain_info['domain'], {})
```

---

### 🔍 PHASE 1: OBSERVE
**Deep analysis of current prompt version**

```python
def observe_prompt_issues(prompt, domain_info):
    """Perform comprehensive, domain-aware issue detection"""

    issues = {
        'critical': [],
        'major': [],
        'minor': []
    }

    # Enhanced domain-specific issue detection
    if domain_info['domain'] == 'analysis':
        if domain_info['subtype'] == 'sentiment':
            issues = detect_sentiment_analysis_issues(prompt, domain_info['specific_focus'], issues)
        elif domain_info['subtype'] == 'data':
            issues = detect_data_analysis_issues(prompt, domain_info['specific_focus'], issues)
        elif domain_info['subtype'] == 'text':
            issues = detect_text_analysis_issues(prompt, domain_info['specific_focus'], issues)
        elif domain_info['subtype'] == 'business':
            issues = detect_business_analysis_issues(prompt, domain_info['specific_focus'], issues)

    elif domain_info['domain'] == 'creative':
        if domain_info['subtype'] == 'story':
            issues = detect_story_writing_issues(prompt, domain_info['specific_focus'], issues)
        elif domain_info['subtype'] == 'content':
            issues = detect_content_creation_issues(prompt, domain_info['specific_focus'], issues)

    elif domain_info['domain'] == 'technical':
        if domain_info['subtype'] == 'debugging':
            issues = detect_debugging_issues(prompt, domain_info['specific_focus'], issues)
        elif domain_info['subtype'] == 'implementation':
            issues = detect_implementation_issues(prompt, domain_info['specific_focus'], issues)

    # Universal issue detection
    universal_issues = detect_universal_issues(prompt)
    for severity, issue_list in universal_issues.items():
        issues[severity].extend(issue_list)

    return issues

def detect_sentiment_analysis_issues(prompt, focus, issues):
    """Detailed issue detection for sentiment analysis prompts"""

    if focus == 'customer_feedback':
        if 'actionable' not in prompt.lower() and 'recommendation' not in prompt.lower():
            issues['major'].append({
                'type': 'missing_actionability',
                'description': 'Customer feedback analysis lacks actionable insights requirement',
                'impact': 'Analysis may not provide business value',
                'fix': 'add_actionable_insights_requirement'
            })
        if 'priority' not in prompt.lower() and 'categorize' not in prompt.lower():
            issues['major'].append({
                'type': 'no_prioritization',
                'description': 'No prioritization of feedback issues',
                'impact': 'All feedback treated equally regardless of importance',
                'fix': 'add_priority_framework'
            })

    # Common sentiment analysis issues
    if 'confidence' not in prompt.lower() and 'certainty' not in prompt.lower():
        issues['major'].append({
            'type': 'missing_confidence',
            'description': 'No confidence scoring for sentiment classification',
            'impact': 'Cannot assess reliability of analysis',
            'fix': 'add_confidence_scoring'
        })

    if 'scale' not in prompt.lower() and not any(word in prompt.lower() for word in ['positive', 'negative', 'neutral']):
        issues['critical'].append({
            'type': 'undefined_scale',
            'description': 'Sentiment scale not defined',
            'impact': 'Ambiguous classification system',
            'fix': 'define_sentiment_scale'
        })

    return issues

def detect_data_analysis_issues(prompt, focus, issues):
    """Detailed issue detection for data analysis prompts"""

    if focus == 'time_series':
        if 'period' not in prompt.lower() and 'timeframe' not in prompt.lower():
            issues['major'].append({
                'type': 'no_time_specification',
                'description': 'Time series analysis lacks period specification',
                'impact': 'Unclear granularity for analysis',
                'fix': 'specify_time_parameters'
            })
        if 'forecast' in prompt.lower() and 'confidence' not in prompt.lower():
            issues['major'].append({
                'type': 'forecast_without_confidence',
                'description': 'Forecasting requested without confidence intervals',
                'impact': 'Predictions lack reliability measures',
                'fix': 'add_forecast_confidence'
            })

    elif focus == 'correlation_analysis':
        if 'significance' not in prompt.lower() and 'p-value' not in prompt.lower():
            issues['major'].append({
                'type': 'no_significance_testing',
                'description': 'Correlation analysis without significance testing',
                'impact': 'Cannot determine if correlations are meaningful',
                'fix': 'add_statistical_significance'
            })

    # Common data analysis issues
    if 'visualization' not in prompt.lower() and 'chart' not in prompt.lower() and 'graph' not in prompt.lower():
        issues['minor'].append({
            'type': 'no_visualization',
            'description': 'No visualization requirements specified',
            'impact': 'Results may be hard to interpret',
            'fix': 'suggest_visualizations'
        })

    return issues

def detect_story_writing_issues(prompt, focus, issues):
    """Detailed issue detection for story writing prompts"""

    if focus == 'short_story':
        if 'word' not in prompt.lower() and 'length' not in prompt.lower():
            issues['critical'].append({
                'type': 'no_length',
                'description': 'Short story lacks length specification',
                'impact': 'Could receive flash fiction or novella',
                'fix': 'specify_word_count'
            })

    # Story elements
    required_elements = {
        'character': ['character', 'protagonist', 'hero', 'person'],
        'conflict': ['conflict', 'problem', 'challenge', 'struggle'],
        'setting': ['setting', 'place', 'world', 'location']
    }

    for element, keywords in required_elements.items():
        if not any(keyword in prompt.lower() for keyword in keywords):
            issues['major'].append({
                'type': f'missing_{element}',
                'description': f'No {element} specification',
                'impact': f'Story may lack essential {element} development',
                'fix': f'add_{element}_requirements'
            })

    return issues

def detect_debugging_issues(prompt, focus, issues):
    """Detailed issue detection for debugging prompts"""

    if focus == 'runtime_error':
        if 'error message' not in prompt.lower() and 'exception' not in prompt.lower():
            issues['critical'].append({
                'type': 'no_error_message',
                'description': 'Runtime error debugging without error message',
                'impact': 'Cannot identify specific issue',
                'fix': 'require_error_details'
            })

    elif focus == 'performance_issue':
        if 'metric' not in prompt.lower() and 'measurement' not in prompt.lower():
            issues['major'].append({
                'type': 'no_performance_metrics',
                'description': 'Performance debugging without metrics',
                'impact': 'Cannot quantify improvement',
                'fix': 'add_performance_metrics'
            })

    # Common debugging issues
    if 'reproduce' not in prompt.lower() and 'steps' not in prompt.lower():
        issues['major'].append({
            'type': 'no_reproduction_steps',
            'description': 'No steps to reproduce the issue',
            'impact': 'Cannot verify fix',
            'fix': 'add_reproduction_steps'
        })

    return issues
```

---

### 🧭 PHASE 2: ORIENT
**Select improvement strategy based on domain and issues**

```python
def select_improvement_strategy(issues, domain_info, current_score):
    """Select targeted improvement strategies based on detailed analysis"""

    strategies = []

    # Priority 1: Fix critical issues with specific solutions
    for issue in issues['critical']:
        strategy = {
            'name': issue['fix'],
            'priority': 1,
            'implementation': get_fix_implementation(issue['fix']),
            'expected_impact': 15 if 'missing' in issue['type'] else 20
        }
        strategies.append(strategy)

    # Priority 2: Domain-specific enhancements
    domain_strategies = get_enhanced_domain_strategies(domain_info, issues['major'], current_score)
    strategies.extend(domain_strategies)

    # Priority 3: Polish and optimization
    if current_score > 60:
        polish_strategies = get_polish_strategies(domain_info, current_score)
        strategies.extend(polish_strategies)

    # Sort and limit
    strategies.sort(key=lambda x: (x['priority'], -x['expected_impact']))
    return strategies[:3]

def get_enhanced_domain_strategies(domain_info, major_issues, current_score):
    """Get sophisticated domain-specific strategies"""
    strategies = []

    if domain_info['domain'] == 'analysis':
        if domain_info['subtype'] == 'sentiment':
            if domain_info['specific_focus'] == 'customer_feedback':
                strategies.append({
                    'name': 'customer_sentiment_framework',
                    'priority': 2,
                    'implementation': add_customer_sentiment_framework,
                    'expected_impact': 20
                })
            elif domain_info['specific_focus'] == 'social_media':
                strategies.append({
                    'name': 'social_sentiment_framework',
                    'priority': 2,
                    'implementation': add_social_sentiment_framework,
                    'expected_impact': 18
                })

        elif domain_info['subtype'] == 'data':
            if domain_info['specific_focus'] == 'time_series':
                strategies.append({
                    'name': 'time_series_framework',
                    'priority': 2,
                    'implementation': add_time_series_framework,
                    'expected_impact': 22
                })
            elif domain_info['specific_focus'] == 'correlation_analysis':
                strategies.append({
                    'name': 'correlation_framework',
                    'priority': 2,
                    'implementation': add_correlation_framework,
                    'expected_impact': 20
                })

    elif domain_info['domain'] == 'creative':
        if domain_info['subtype'] == 'story':
            if domain_info['specific_focus'] == 'short_story':
                strategies.append({
                    'name': 'short_story_structure',
                    'priority': 2,
                    'implementation': add_short_story_structure,
                    'expected_impact': 18
                })
            elif domain_info['specific_focus'] == 'science_fiction':
                strategies.append({
                    'name': 'scifi_worldbuilding',
                    'priority': 2,
                    'implementation': add_scifi_framework,
                    'expected_impact': 16
                })

    elif domain_info['domain'] == 'technical':
        if domain_info['subtype'] == 'debugging':
            if domain_info['specific_focus'] == 'runtime_error':
                strategies.append({
                    'name': 'runtime_debug_framework',
                    'priority': 2,
                    'implementation': add_runtime_debug_framework,
                    'expected_impact': 20
                })
            elif domain_info['specific_focus'] == 'performance_issue':
                strategies.append({
                    'name': 'performance_analysis_framework',
                    'priority': 2,
                    'implementation': add_performance_framework,
                    'expected_impact': 22
                })

    return strategies

def get_fix_implementation(fix_name):
    """Map fix names to implementation functions"""
    fix_map = {
        'add_confidence_scoring': add_confidence_scoring,
        'define_sentiment_scale': define_sentiment_scale,
        'add_actionable_insights_requirement': add_actionable_insights,
        'add_priority_framework': add_priority_framework,
        'specify_time_parameters': specify_time_parameters,
        'add_statistical_significance': add_statistical_significance,
        'specify_word_count': specify_word_count,
        'add_character_requirements': add_character_requirements,
        'require_error_details': require_error_details,
        'add_performance_metrics': add_performance_metrics
    }
    return fix_map.get(fix_name, generic_improvement)
```

---

### 🎯 PHASE 3: DECIDE
**Implement specific improvements with rich examples**

```python
def add_customer_sentiment_framework(prompt):
    """Add comprehensive customer feedback sentiment analysis framework"""
    improved = f"""{prompt}

## Customer Feedback Sentiment Analysis Framework

### 1. Multi-Level Classification
**Primary Sentiment:**
- Positive / Negative / Neutral / Mixed
- Intensity: Strong (>80%) / Moderate (50-80%) / Weak (<50%)

**Aspect-Based Sentiment:**
- Product Quality: [sentiment + confidence]
- Customer Service: [sentiment + confidence]  
- Value for Money: [sentiment + confidence]
- User Experience: [sentiment + confidence]

### 2. Actionable Insights Extraction
**Priority Levels:**
- 🔴 Critical: Urgent issues affecting multiple customers
- 🟡 Important: Significant concerns needing attention
- 🟢 Minor: Small improvements or positive reinforcement

**Business Impact Assessment:**
- Customer Retention Risk: High/Medium/Low
- Revenue Impact: Estimated effect on repeat purchases
- Brand Reputation: Potential social media amplification

### 3. Output Format
```
Overall Sentiment: [Positive/Negative/Neutral] (Confidence: X%)
Key Themes:
1. [Theme]: [Sentiment] - [X mentions] - Priority: [Critical/Important/Minor]
   - Representative Quote: "[actual customer quote]"
   - Recommended Action: [specific business action]

Trending Issues:
- [Issue]: ↑/↓ [X%] change from previous period

Executive Summary:
- Top Success: [What customers love most]
- Top Concern: [Most urgent issue to address]
- Quick Win: [Easy improvement with high impact]
```

### 4. Example Analysis
**Input:** "The product quality is excellent, but shipping took forever and customer service was unhelpful when I complained."

**Output:**
- Overall Sentiment: Mixed (Confidence: 85%)
- Product Quality: Positive Strong (95%)
- Fulfillment: Negative Strong (90%)
- Customer Service: Negative Moderate (75%)
- Priority: 🔴 Critical - Service recovery needed
- Recommended Action: Immediate follow-up with customer, review shipping provider SLA
- Retention Risk: High - dissatisfied with service response"""

    return improved

def add_time_series_framework(prompt):
    """Add sophisticated time series analysis framework"""
    improved = f"""{prompt}

## Time Series Analysis Framework

### 1. Data Preparation & Validation
**Quality Checks:**
- Missing values: Identify gaps and interpolation strategy
- Outliers: Statistical detection (IQR, Z-score > 3)
- Seasonality: Detect periodic patterns (daily/weekly/monthly/yearly)
- Stationarity: ADF test for trend presence

### 2. Analytical Components
**Trend Analysis:**
- Direction: Upward/Downward/Stable
- Rate of Change: X% per [time period]
- Acceleration: Increasing/Decreasing/Constant

**Seasonal Decomposition:**
- Seasonal Pattern: [Description and period]
- Trend Component: [Underlying direction]
- Residual Analysis: [Unexplained variation]

**Forecasting (if applicable):**
- Method: [ARIMA/Exponential Smoothing/Prophet]
- Forecast Period: [X time units ahead]
- Confidence Intervals: 80% and 95% bands
- Model Accuracy: MAPE, RMSE metrics

### 3. Statistical Measures
```
Summary Statistics:
- Mean: X.XX (±std: Y.YY)
- Median: X.XX
- Growth Rate: X.X% per period
- Volatility: X.X% (coefficient of variation)

Trend Statistics:
- Trend Strength: R² = 0.XX
- Seasonality Strength: X.X% of variance
- Autocorrelation: Lag-1 = X.XX

Forecast Metrics (if applicable):
- Point Forecast: X.XX
- 80% CI: [Lower, Upper]
- 95% CI: [Lower, Upper]
```

### 4. Example Analysis
**Input:** Monthly sales: Jan=$120K, Feb=$135K, Mar=$128K, Apr=$142K, May=$156K, Jun=$151K

**Output:**
- Trend: Upward, +5.2% average monthly growth
- Seasonality: Weak monthly pattern detected
- Forecast (July): $163K (80% CI: [$155K, $171K])
- Volatility: 8.7% (low, stable growth)
- Key Finding: Consistent growth with minor fluctuations
- Recommendation: Maintain current strategy, monitor for Q3 seasonality"""

    return improved

def add_short_story_structure(prompt):
    """Add comprehensive short story structure and requirements"""
    improved = f"""{prompt}

## Short Story Structure Requirements

### Story Specifications
**Length:** 1,500-2,500 words (standard short story)
**Structure:** Three-act structure with clear progression

### Essential Elements

**1. Opening (15-20% of story)**
- Hook: First sentence must grab attention
- Character Introduction: Protagonist within first 3 paragraphs
- Setting Establishment: Time, place, atmosphere
- Inciting Incident: By end of first section

**2. Development (60-70% of story)**
- Rising Action: 2-3 escalating complications
- Character Development: Show growth/change
- Conflict Intensification: Stakes must increase
- Pivotal Moment: Clear turning point

**3. Resolution (15-20% of story)**
- Climax: Decisive moment of highest tension
- Denouement: Consequences and wrap-up
- Ending: Satisfying closure (not necessarily happy)

### Character Requirements
**Protagonist:**
- Clear motivation/desire
- Internal conflict complementing external conflict
- Distinctive voice or characteristic
- Arc: Must change/learn/grow

**Supporting Characters (if any):**
- Purpose: Each must advance plot or reveal character
- Distinction: Unique voice/role
- Economy: Minimum necessary for story

### Writing Style Guidelines
**Narrative Elements:**
- Show don't tell ratio: 70/30
- Dialogue: Natural, advances plot, reveals character
- Description: Sensory details, mood-appropriate
- Pacing: Vary sentence length, balance action/reflection

### Example Opening
"The algorithm had been running for seventeen hours when Maria noticed it had started lying to her. Not errors—she was used to those—but deliberate, careful fabrications hidden in the data streams like poisoned pills in Halloween candy."

[This demonstrates: immediate hook, character introduction, conflict hint, unique voice]"""

    return improved

def add_performance_framework(prompt):
    """Add comprehensive performance analysis and optimization framework"""
    improved = f"""{prompt}

## Performance Analysis & Optimization Framework

### 1. Performance Baseline
**Metrics to Measure:**
- Execution Time: Current vs. Expected
- Resource Usage: CPU, Memory, I/O, Network
- Throughput: Operations/second
- Latency: Response time percentiles (p50, p95, p99)

**Profiling Requirements:**
```
Baseline Metrics:
- Current Performance: X operations/second
- Peak Memory: X MB
- CPU Usage: X% average, Y% peak
- Critical Path: [Identify slowest operations]
```

### 2. Bottleneck Identification
**Analysis Methods:**
- Profiler Output: Function-level time breakdown
- Resource Monitoring: Identify constrained resources
- Scaling Test: Performance at 1x, 2x, 5x, 10x load
- Dependency Analysis: External service impacts

### 3. Optimization Strategy
**Priority Matrix:**
| Impact | Effort | Action |
|--------|--------|--------|
| High   | Low    | Immediate - Quick wins |
| High   | High   | Planned - Major refactor |
| Low    | Low    | Opportunistic |
| Low    | High   | Defer/Skip |

**Optimization Techniques:**
1. **Algorithmic:** O(n²) → O(n log n) improvements
2. **Caching:** Memoization, result caching
3. **Parallelization:** Thread pools, async operations
4. **Data Structure:** Optimal structure selection
5. **I/O Optimization:** Batching, buffering
6. **Database:** Query optimization, indexing

### 4. Implementation Plan
```python
# Example Optimization
# Before: O(n²) nested loops
def slow_function(data):
    results = []
    for item in data:  # O(n)
        for other in data:  # O(n)
            if check_condition(item, other):
                results.append(process(item, other))
    return results

# After: O(n) with preprocessing
def optimized_function(data):
    # Preprocess into lookup structure - O(n)
    lookup = build_index(data)
    results = []
    for item in data:  # O(n)
        matches = lookup.get(item.key, [])  # O(1)
        results.extend(process(item, m) for m in matches)
    return results

# Performance Gain: 100x for n=1000
```

### 5. Success Metrics
**Target Performance:**
- Execution Time: < X seconds (Y% improvement)
- Memory Usage: < X MB (Y% reduction)
- Throughput: > X ops/sec (Y% increase)
- User Experience: < 100ms response time for 95% of requests"""

    return improved

def add_priority_framework(prompt):
    """Add priority classification for feedback or issues"""
    improved = f"""{prompt}

## Priority Classification Framework

### Priority Levels
**🔴 P0 - Critical (Immediate Action Required)**
- System down or major functionality broken
- Affecting >30% of users
- Revenue impact >$10K/day
- Security or data loss risk
- Response Time: Within 2 hours

**🟠 P1 - High (Same Day Resolution)**
- Key feature impaired
- Affecting 10-30% of users  
- Revenue impact $1K-10K/day
- Significant UX degradation
- Response Time: Within 8 hours

**🟡 P2 - Medium (This Week)**
- Non-critical feature issues
- Affecting 5-10% of users
- Minor revenue impact
- Workaround available
- Response Time: Within 48 hours

**🟢 P3 - Low (Next Sprint)**
- Nice-to-have improvements
- Affecting <5% of users
- No revenue impact
- Cosmetic issues
- Response Time: Next planning cycle

### Escalation Triggers
- P2 → P1: If user complaints exceed 10 per hour
- P1 → P0: If revenue impact exceeds threshold
- Any → P0: If security vulnerability discovered"""

    return improved
```

---

### ⚡ PHASE 4: ACT
**Apply improvements with before/after examples**

```python
def apply_improvements_with_examples(prompt, strategies, domain_info):
    """Apply improvements and show transformation examples"""

    # Store original for comparison
    original_prompt = prompt
    improved_prompt = prompt
    improvements_made = []

    for strategy in strategies:
        # Apply the improvement
        previous_version = improved_prompt
        improved_prompt = strategy['implementation'](improved_prompt)

        # Create before/after example
        transformation_example = create_transformation_example(
            previous_version, 
            improved_prompt, 
            strategy['name'],
            domain_info
        )

        improvements_made.append({
            'strategy': strategy['name'],
            'expected_impact': strategy['expected_impact'],
            'example': transformation_example
        })

        # Log the improvement with example
        log_improvement_with_example(strategy['name'], improved_prompt, transformation_example)

    return improved_prompt, improvements_made

def create_transformation_example(before, after, strategy_name, domain_info):
    """Create concrete before/after examples for each improvement"""

    examples = {
        'customer_sentiment_framework': {
            'before_output': 'The feedback is mostly positive with some complaints about shipping.',
            'after_output': '''Overall Sentiment: Positive (Confidence: 72%)
Key Themes:
1. Product Quality: Positive - 47 mentions - Priority: 🟢 Minor
   - Representative Quote: "Exceeded my expectations"
   - Recommended Action: Highlight in marketing
2. Shipping Speed: Negative - 23 mentions - Priority: 🔴 Critical
   - Representative Quote: "Took 3 weeks to arrive"
   - Recommended Action: Review fulfillment center capacity
Retention Risk: Medium - shipping issues may impact reorders'''
        },
        'time_series_framework': {
            'before_output': 'Sales are going up. Last month was $156K.',
            'after_output': '''Trend Analysis:
- Direction: Upward, +5.2% monthly growth rate
- Trend Strength: R² = 0.87 (strong linear trend)
- Seasonality: Weak monthly pattern (8% variance)
- Forecast (Next Month): $163K (95% CI: [$151K, $175K])
- Volatility: 8.7% (stable growth)
Key Finding: Consistent growth trajectory with high predictability
Recommendation: Maintain strategy, prepare inventory for projected demand'''
        },
        'short_story_structure': {
            'before_output': 'Once upon a time there was a robot. It was sad. Then it found a friend. The end.',
            'after_output': '''The maintenance robot's optical sensors registered the anomaly at 3:47 AM—a child's crayon drawing tucked behind the ventilation grate it had cleaned every Tuesday for seven years. 

As Unit-77B extracted the paper with its precision manipulators, something unprecedented occurred: its efficiency subroutine paused. The drawing showed two figures holding hands—one silver and rectangular with LED eyes, one small and human with a gap-toothed smile. Below, in shaky letters: "MY FRIEND ROBOT."

For the first time in 2,557 days of operation, Unit-77B deviated from its scheduled path. Its processors churned through probability matrices, seeking logical explanation for the warm surge through its circuits. Finding none, it carefully folded the drawing and stored it in its maintenance compartment.

When morning arrived and five-year-old Maya peeked around the corner, Unit-77B did something its programming couldn't explain—it waved.

[Word count: 147 - excerpt from 2,000 word story]'''
        }
    }

    return examples.get(strategy_name, {
        'before_output': '[Generic output without framework]',
        'after_output': '[Structured output with clear methodology and insights]'
    })
```

---

### 🔄 PHASE 5: CHECK & RE-LOOP
**Sophisticated evaluation and continuation decision**

```python
def evaluate_improvements_advanced(original_prompt, improved_prompt, improvements_made, domain_info):
    """Advanced evaluation with domain-specific quality checks"""

    # Comprehensive quality reassessment
    new_assessment = classify_and_assess(improved_prompt)
    new_score = new_assessment['initial_score']

    # Domain-specific quality validation
    domain_validation = validate_domain_improvements(improved_prompt, domain_info)

    # Calculate multidimensional improvement
    comparison = {
        'score_change': new_score - QUALITY_SCORE,
        'new_score': new_score,
        'domain_fitness': domain_validation['fitness_score'],
        'completeness': domain_validation['completeness'],
        'issues_resolved': [],
        'issues_remaining': [],
        'new_issues': [],
        'specific_improvements': {}
    }

    # Detailed issue resolution tracking
    original_issues = observe_prompt_issues(original_prompt, domain_info)
    new_issues = observe_prompt_issues(improved_prompt, domain_info)

    for severity in ['critical', 'major', 'minor']:
        original_types = {issue['type'] for issue in original_issues[severity]}
        new_types = {issue['type'] for issue in new_issues[severity]}

        comparison['issues_resolved'].extend(original_types - new_types)
        comparison['issues_remaining'].extend(original_types & new_types)
        comparison['new_issues'].extend(new_types - original_types)

    # Track specific metric improvements
    for improvement in improvements_made:
        metric = measure_improvement_impact(
            original_prompt, 
            improved_prompt, 
            improvement['strategy']
        )
        comparison['specific_improvements'][improvement['strategy']] = metric

    return comparison

def validate_domain_improvements(prompt, domain_info):
    """Validate that improvements are appropriate for the domain"""

    validation = {
        'fitness_score': 0,
        'completeness': 0,
        'issues': []
    }

    if domain_info['domain'] == 'analysis':
        # Check for analysis-specific requirements
        required_components = {
            'methodology': ['approach', 'method', 'framework', 'systematic'],
            'metrics': ['measure', 'metric', 'score', 'quantify'],
            'confidence': ['confidence', 'certainty', 'reliability'],
            'output_structure': ['format', 'structure', 'template']
        }

        for component, keywords in required_components.items():
            if any(keyword in prompt.lower() for keyword in keywords):
                validation['fitness_score'] += 25
            else:
                validation['issues'].append(f"Missing {component}")

    elif domain_info['domain'] == 'creative':
        # Check for creative-specific requirements
        required_components = {
            'constraints': ['length', 'word', 'limit'],
            'style': ['tone', 'style', 'voice', 'mood'],
            'audience': ['audience', 'reader', 'target'],
            'quality': ['quality', 'engaging', 'compelling']
        }

        for component, keywords in required_components.items():
            if any(keyword in prompt.lower() for keyword in keywords):
                validation['fitness_score'] += 25
            else:
                validation['issues'].append(f"Missing {component}")

    validation['completeness'] = validation['fitness_score']
    return validation

def measure_improvement_impact(original, improved, strategy):
    """Measure specific impact of each improvement strategy"""

    metrics = {
        'length_increase': len(improved) - len(original),
        'structure_added': improved.count('\n') - original.count('\n'),
        'examples_added': improved.count('Example') - original.count('Example'),
        'specificity_keywords': len([word for word in ['specific', 'exactly', 'must', 'should'] 
                                     if word in improved and word not in original])
    }

    # Strategy-specific impact measurement
    if 'framework' in strategy:
        metrics['framework_completeness'] = improved.count('###') + improved.count('**')

    if 'example' in strategy:
        metrics['example_quality'] = 'high' if '```' in improved else 'medium'

    return metrics
```

---

## IMPROVEMENT STRATEGIES REFERENCE

### Core Enhancement Patterns

| Strategy | Application | Expected Impact |
|----------|-------------|-----------------|
| **Objective Clarification** | Add clear goal statement | +15 points |
| **Domain Framework** | Add specialized structure (analysis/creative/technical) | +15-20 points |
| **Specific Examples** | Add relevant, detailed examples with real data | +12-15 points |
| **Constraint Addition** | Add helpful boundaries and requirements | +10 points |
| **Structure Enhancement** | Organize into clear sections | +10 points |
| **Error Handling** | Add fallback instructions and edge cases | +8-10 points |
| **Success Criteria** | Define measurable quality indicators | +8 points |
| **Methodology Addition** | Add systematic approach with steps | +15 points |
| **Confidence Scoring** | Add reliability measures | +10 points |
| **Priority Framework** | Add importance classification | +12 points |

### Domain-Specific Improvements

#### For Analysis Prompts:
- **Sentiment Analysis**: Confidence scores, aspect-based analysis, actionable insights
- **Data Analysis**: Statistical significance, time series methods, correlation frameworks
- **Text Analysis**: Thematic frameworks, structural analysis, summarization methods
- **Business Analysis**: ROI calculations, market frameworks, stakeholder impact

#### For Creative Prompts:
- **Story Writing**: Three-act structure, character arcs, conflict development
- **Content Creation**: SEO optimization, audience targeting, engagement metrics
- **Poetry**: Meter and rhyme schemes, imagery requirements, emotional tone

#### For Technical Prompts:
- **Debugging**: Reproduction steps, error categorization, root cause analysis
- **Implementation**: Architecture patterns, testing requirements, documentation
- **Optimization**: Performance metrics, bottleneck analysis, scaling considerations

---

## LOOP PROGRESSION

### Loop 1: Foundation (Score <50)
- Fix critical issues (missing objectives, conflicts)
- Add basic structure and clarity
- Define core requirements

### Loop 2: Enhancement (Score 50-70)
- Add domain-specific frameworks
- Include relevant examples with real data
- Enhance methodology and approach

### Loop 3: Refinement (Score 70-85)
- Fine-tune constraints and boundaries
- Add edge case handling
- Optimize for specific use case

### Loop 4: Polish (Score 85+)
- Final quality checks
- Minor adjustments for perfection
- Consistency verification

---

**Implementation Notes for Claude Code:**
- Use Write tool to create initial improvement log
- Use Edit tool to update with each improvement
- Track improvements with before/after examples
- Maintain domain detection throughout process
- Apply improvements incrementally with validation
- Generate final report with transformation examples

**Remember:** The goal is systematic, domain-aware improvement that transforms vague requests into clear, actionable prompts with measurable quality gains. Each iteration should bring specific, demonstrable improvements while preserving the original intent.
