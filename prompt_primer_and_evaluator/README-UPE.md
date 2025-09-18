# Ultimate Prompt Evaluator (UPE) - README

## Getting Started

To use the Ultimate Prompt Evaluator effectively:

1. **Setup**: Either add the UPE to a project (recommended for Claude), a Gemini Gem, or just paste it into a new conversation

2. **Submit Your Prompt**: When prompted, share the prompt you want evaluated
   - Put your prompt in quotation marks: `"Your prompt here"`

3. **Review**: After receiving the evaluation:
   - Examine the identified strengths and gaps
   - Request the ultimate version: `"Using this, give me the ultimate refined prompt in a code block"`

4. **Optional Next Steps**: You can:
   - Start a new conversation with your improved prompt
   - Continue working with the evaluator in the same conversation
   - Compare evaluation scores if you choose to re-evaluate

## Perfect Complement: Dual Path Primer

The **Dual Path Primer** works seamlessly with UPE as part of a complete prompt engineering workflow:

- **Use Dual Path Primer first** to deeply understand your requirements and create a comprehensive initial prompt
- **Feed the resulting prompt into UPE** for detailed evaluation and refinement
- **Get professionally crafted prompts** with rich context and thorough evaluation

The Primer ensures you start with well-contextualized prompts, while UPE provides the rigorous evaluation and optimization. Together, they create a complete professional toolkit.

## Platform-Specific Usage Tips

### Using with Claude
- **Project Integration**: Add the UPE to a Claude project as main instructions
- **Unlimited Instructions**: Claude has no limit on the length of main instructions in projects, making it ideal for the UPE
- **Simple Evaluation**: Put the prompt you want evaluated in quotation marks and send
- **Great Performance**: Claude typically provides quality evaluations

### Using with ChatGPT
- **Direct Pasting**: Simply paste the entire UPE prompt into a conversation
- **Model Recommendation**: Use the latest large models for best results
- **Follow Instructions**: It will ask you to share the prompt you want evaluated
- **Proceed Normally**: Continue from there with the evaluation
- **Custom GPT Limitations**: As of last check, Custom GPTs have character limits too low for the UPE
- **Project Limitations**: As of last check, ChatGPT projects also have instruction limits that prevent using the full UPE

### Using with Gemini
- **Gems Integration**: Gemini's "gems" feature (similar to Claude's projects) is compatible with the UPE
- **Comprehensive Output**: The latest Gemini Large Models provide very dense, detailed quality criteria breakdowns
- **Request Refined Prompt**: Sometimes Gemini won't include the refined prompt in its evaluation - simply ask for it afterward with "Give me the refined prompt in a code block"

### Using with Other LLMs
- **Project Method**: If your LLM supports projects with sufficient token limits in main instructions, add the UPE there
- **Direct Paste Method**: For all LLMs, you can paste the entire prompt and work from there
- **Best Experiences**: Users report excellent results with Claude projects, ChatGPT's advanced models, and the latest Gemini Pro 2.5 Preview which shows very comprehensive evaluations

## Advanced Usage Tips & Tricks

### Getting the Ultimate Refined Prompt

The initial evaluation will include a refined version of your prompt, but for the best results:

1. **Request the Ultimate Version**: After receiving your evaluation, ask:
   ```
   "Using this, give me the ultimate refined prompt in a code block"
   ```

2. **Compare Versions**: This often produces an even better version that incorporates all evaluation insights

3. **Next Steps Options**:
   - Copy the refined prompt into a new chat for a fresh evaluation
   - Continue the conversation with the evaluator in the same chat, refining through dialogue
   - Use the refined prompt as is if you're satisfied with the results

### Iterative Re-evaluation Technique (Powerful with Claude Sonnet 4)

A highly effective technique for continuous prompt improvement:

1. **Get Initial Evaluation**: Submit your prompt for evaluation as normal
2. **Add Enhancement**: After receiving the evaluation, add your improvement request directly to the conversation:
   ```
   "include [your specific addition/improvement]. re-evaluate"
   ```
3. **Get Enhanced Analysis**: The evaluator will incorporate your addition and provide a significantly more refined prompt
4. **Continue Iterating**: You can repeat this process multiple times - after each re-evaluation, add another improvement and re-evaluate again for continuous refinement

**Example Usage:**
- `"include a questionnaire to ensure better user understanding. re-evaluate"`
- `"add error handling mechanisms. re-evaluate"`
- `"include examples for each step. re-evaluate"`

**Multiple Iterations:**
- First: `"include error handling. re-evaluate"`
- Then: `"add user skill level adaptation. re-evaluate"`
- Then: `"include output validation steps. re-evaluate"`

**Why This Works:**
- Leverages the full evaluation context already established
- The addition triggers a broader, deeper analysis beyond just the specific request
- Forces the evaluator to consider new angles and perspectives
- Often results in comprehensive improvements throughout the entire prompt, not just the added element
- Creates iterative refinement cycles for increasingly sophisticated prompts
- Each iteration builds upon the previous enhanced analysis
- Particularly powerful with Claude Sonnet 4's advanced reasoning

**Key Insight:** When you ask to include something specific (like a questionnaire), the model doesn't just add that element - it reconsiders the entire prompt from this new perspective, leading to a much more elaborate and powerful result overall.

**Important Note:** This technique has been extensively tested and proven extremely powerful with the new Claude Sonnet 4. While it could potentially work with other models, it has not been tested beyond Claude Sonnet 4 at this time.

### Creating Prompt Chains

The UPE can help design connected prompt sequences:

1. **Chain Development**: Ask something like:
   ```
   "What would be the follow-up chain prompt for this one?"
   ```

2. **Forward-Chain Design**: Convert standalone prompts into chained sequences:
   ```
   "Convert this into a feed-forward chain prompt"
   ```

3. **Multi-Stage Workflows**: Use the evaluator to create connected prompts for complex tasks

### Building Prompts From Scratch

The UPE isn't just for evaluating existing prompts:

1. **Concept Interpretation**: The evaluator can interpret your ideas as prompts
   - Put your concept in quotation marks: `"I want a prompt that helps with creative writing"`
   - The evaluator will interpret this as a prompt attempt, evaluate it, and refine it
   - This is a powerful way to go from concept to refined prompt in one step

2. **Direct Creation Requests**: Explicitly ask for prompt creation
   ```
   "Create a prompt for [your specific purpose]"
   ```

3. **Multi-Agent Systems**: Develop sophisticated multi-agent prompt systems
   ```
   "Build a three-agent prompt system for [task] with agents that handle [specific roles]"
   ```

4. **Important Considerations**:
   - Be careful with wording to avoid wrong assumptions by the evaluator
   - Be specific about your requirements to get more targeted prompts
   - If the evaluator misunderstands, clarify and try again with different wording
   - Prompts created with the evaluator in context will typically be more robust

5. **Advanced Applications**:
   - Create multiple connected prompts that work together as a system
   - Develop specialized prompts for different aspects of complex tasks

### Conversation Mode & Context Benefits

The UPE isn't just for formal evaluations:

- **Conversation Without Evaluation**: Start with "Don't evaluate" and then converse normally
- **On-Demand Evaluation**: Request evaluation at any point in the conversation
- **Knowledge in Context**: The evaluator's expertise remains available throughout your session, enhancing all prompt-related discussions

## Troubleshooting & Important Notes

### Self-Evaluation Confusion

When using the UPE in projects or certain contexts, you might encounter:

- **Self-Evaluation Error**: Sometimes the evaluator gets confused and evaluates itself instead of your prompt
- **Misleading Assessments**: The UPE might receive low scores if it self-evaluates, but this is not reflective of its actual quality
- **Token Density**: Due to its comprehensive nature, some LLMs may judge the UPE as "not that great" because it's dense and has a high token count

### Trust the Proven Value

- **Extensively Tested**: The UPE has been tested and refined through extensive real-world usage
- **Intentional Design**: The density is by design to enable sophisticated analysis
- **Self-Criticism Not Relevant**: If the UPE evaluates itself, it might give itself a low score - ignore this self-criticism as it has no bearing on its actual effectiveness for evaluating your prompts

### If Self-Evaluation Occurs

- Try rephrasing your request to make it clearer what needs evaluation
- Use quotation marks around the prompt you want evaluated
- Start a fresh conversation if the confusion persists

## Final Thoughts

The Ultimate Prompt Evaluator is designed for maximum usability. If something seems complex, it's a feature allowing for sophisticated analysis - not a bug. The complexity enables powerful optimization but is presented in an accessible format for all skill levels.

---

Now you're ready to transform your prompts with the Ultimate Prompt Evaluator! Share your prompt to get started.
