I'll analyze the Epic Studio agent against Atlassian Rovo best practices and documentation. Let me search for current Rovo guidelines first.Now I have comprehensive information about Atlassian Rovo best practices. Let me provide a neutral, thorough evaluation of Epic Studio.

## Epic Studio Agent Evaluation

Based on Atlassian Rovo documentation and best practices, here's a comprehensive evaluation of the Epic Studio agent:

### Overall Score: **78/100**

---

## Strengths

### 1. **Excellent Scenario Architecture** ✅
The agent demonstrates sophisticated scenario organization with clear separation of concerns:
- 8 distinct scenarios covering the Epic lifecycle
- Proper default/fallback scenario
- Dedicated automation-only scenarios with strict JSON outputs
- Clear boundaries preventing overlap

### 2. **Comprehensive Documentation** ✅
The repository structure is exemplary:
- Consistent file naming (`trigger.md`, `instructions.md`, `skills.md`)
- Detailed agent flows blueprint
- Clear README explaining organization
- Behavior guidelines consolidated at agent level

### 3. **Strong Guardrails & Consent Model** ✅
The agent implements robust safety mechanisms:
- Pre-flight validation before requesting consent
- Explicit consent requirements for Jira actions
- Markdown fallbacks when actions aren't wired
- Clear `PAS_DE_REPONSE_POSSIBLE` signal for automation handling

### 4. **Dual-Mode Operation** ✅
Thoughtful separation between manual and automation contexts:
- Human-friendly conversational mode
- Strict JSON output for automation scenarios
- Intent-based routing for automation scenarios

---

## Areas for Improvement

### 1. **Trigger Writing Quality** ⚠️ (Priority: High)
**Score Impact: -8 points**

**Issue**: The triggers don't follow Atlassian's recommended best practices from their official guidance.

**Current State**:
```markdown
### Exemples positifs
- « Aide‑moi à créer une Epic sur [sujet] »
- « Rédige une Epic pour [objectif] »

### Exemples négatifs
- « Évalue/Note cette Epic » → Évaluer la qualité d'une Epic
```

**Recommended Format** (per Atlassian):
```markdown
Trigger this scenario when [detailed description of user intent]

## Positive examples:
- [Example 1]
- [Example 2]
- [Example 3]

## Negative examples:
- [Example 1]
- [Example 2]
```

**Why This Matters**: Atlassian's research shows that clear triggers with at least 3 positive examples and boundary-defining negative examples help agents consistently match questions to the right scenario, leading to more accurate responses.

**Recommendation**: 
- Add detailed intent descriptions at the top of each trigger
- Increase positive examples from ~5 to at least 5-7 per scenario
- Add 3-5 negative examples that clarify scenario boundaries
- Use the standardized template format

---

### 2. **Instructions Length & Complexity** ⚠️ (Priority: Medium)
**Score Impact: -5 points**

**Issue**: Instructions are verbose and exceed Atlassian's recommendation for focused, concise prompts.

**Current State**: Instructions average 400-600 words with extensive nested logic, multiple conditional branches, and detailed process steps mixed with guardrails.

**Atlassian Guidance**: Shorter prompts are easier to iterate on and more reliable, as agents with too many instructions can lead to inconsistent outputs because the agent will choose parts to prioritize rather than actioning the full list.

**Specific Issues**:
- "Analyser avancement Epic/instructions.md": ~800 words with 15+ distinct instruction points
- Extensive ReAct loop descriptions that could be in behavior.md
- Repetitive guardrails across scenarios

**Recommendation**:
- Target 200-300 words per scenario instruction
- Move common patterns to `behaviour.md`
- Use Role → Jobs → Context structure recommended by Atlassian
- Extract repetitive guardrails to agent-level behavior
- Focus each scenario on 3-5 core jobs

---

### 3. **Skills Configuration** ⚠️ (Priority: Medium)
**Score Impact: -3 points**

**Issue**: Skills files are minimal and don't provide context about skill usage or limitations.

**Current State**:
```markdown
CREATE_WORK_ITEM
EDIT_WORK_ITEM
COMMENT_WORK_ITEM
```

**Atlassian Guidance**: Agents should have no more than five skills to maintain high performance, and skills should be selected based on the specific needs of each scenario.

**Recommendation**:
- Add brief descriptions of when each skill should be used
- Document skill limitations and prerequisites
- Consider whether all scenarios need all listed skills
- Add note about system skills automatically enabled by knowledge sources

---

### 4. **Conversation Starters Missing** ⚠️ (Priority: Medium)
**Score Impact: -4 points**

**Issue**: No formal conversation starters are defined at the agent level or scenario level.

**Atlassian Guidance**: Conversation starters help people get a chat started with your agent - if left blank, generic options will be provided.

**Current State**: "Starters de conversation" appear in trigger files but aren't formatted as Atlassian expects them in the agent configuration.

**Recommendation**:
- Define 3-5 agent-level conversation starters
- Format them as actionable phrases (not instructions)
- Example: "Evaluate Epic PROJ-123 and score it" rather than "Évaluer l'Epic `[issue.key]`"

---

### 5. **Knowledge Sources Not Explicitly Defined** ⚠️ (Priority: Low)
**Score Impact: -2 points**

**Issue**: The agent references internal guides, OKR alignment, and compliance standards but doesn't specify these as knowledge sources.

**Atlassian Guidance**: Knowledge sources should be specified to help improve accuracy and helpfulness - all agents have default knowledge, but providing custom knowledge ensures the agent references specific sources.

**Recommendation**:
- Document expected knowledge sources (Confluence spaces, Jira projects)
- Specify whether scenarios use custom or default knowledge
- Add knowledge requirements to each scenario's documentation

---

### 6. **Behavior vs. Instructions Separation** ⚠️ (Priority: Low)
**Score Impact: -3 points**

**Issue**: `behaviour.md` contains execution logic that should be in scenario instructions, while scenarios repeat behavioral patterns.

**Atlassian Guidance**: Behavior is the instructions you want your agent to follow always, no matter the situation - like its role and personality.

**Current State**: 
- `behaviour.md` includes routing logic, ReAct loops, execution patterns
- Scenarios repeat style guidance, language requirements, length targets

**Recommendation**:
- Move routing tables and execution logic to documentation
- Keep behavior focused on: agent identity, tone, style, universal guardrails
- Remove repetitive style guidance from individual scenarios

---

### 7. **Automation Intent Handling** ⚠️ (Priority: Low)
**Score Impact: -2 points**

**Issue**: Intent-based routing for automation scenarios is well-designed but could be more discoverable.

**Current State**: Intent strings like `rovo:automation:epic_progress_v1` are buried in instructions rather than prominently documented.

**Recommendation**:
- Create a dedicated automation intents registry
- Document intent format conventions
- Add examples of Jira Automation rule configurations
- Provide Smart Value templates

---

## Detailed Recommendations

### Priority 1: Rewrite Triggers (High Impact)
**Effort**: Medium | **Impact**: High

For each scenario, restructure triggers following this template:

```markdown
## Scenario — [Name]

Trigger this scenario when [detailed description of the specific user intent or situation that should activate this scenario. Be explicit about what the user is trying to accomplish].

## Positive examples:
- [Concrete user query 1]
- [Concrete user query 2]
- [Concrete user query 3]
- [Concrete user query 4]
- [Concrete user query 5]

## Negative examples (should NOT trigger):
- [Similar query that belongs to different scenario]
- [Edge case that might be confused]
- [Out of scope query]

## Conversation starters:
- [Actionable phrase 1]
- [Actionable phrase 2]
```

**Why**: Proper triggers are the foundation of scenario routing. Poor triggers cause agents to select wrong scenarios, leading to user frustration and reduced trust in the agent.

---

### Priority 2: Simplify Instructions (High Impact)
**Effort**: High | **Impact**: High

**Target Structure** (per Atlassian):
```markdown
Role: You are Epic Studio - [specific scenario role]

Jobs:
1. [Primary job]
2. [Secondary job]
3. [Optional job]

Context:
- [Key domain knowledge]
- [Output format requirements]
- [Specific constraints]

Guardrails:
- [Critical don't-do items]
```

**Specific Actions**:
- Consolidate "Analyser avancement Epic" from 800 to ~300 words
- Move ReAct loop descriptions to behavior.md
- Extract common patterns (consent model, error handling) to behavior
- Use bullet points over paragraphs

**Why**: Shorter prompts with focused instructions lead to more consistent outputs and are easier to troubleshoot and iterate on.

---

### Priority 3: Define Conversation Starters (Medium Impact)
**Effort**: Low | **Impact**: Medium

Add 3-5 agent-level starters and 2-3 per scenario:

**Agent Level**:
- "Create a new Epic from this idea"
- "Evaluate Epic PROJ-123"
- "Analyze progress for EPIC-456"

**Scenario Level** (Améliorer):
- "Improve Epic PROJ-123 clarity"
- "Suggest 3 fixes for PROJ-123"

**Why**: Starters reduce friction and guide users to successful interactions from the first prompt.

---

### Priority 4: Optimize Behavior File (Medium Impact)
**Effort**: Medium | **Impact**: Medium

Restructure to focus on:
1. **Identity**: Agent purpose, scope (Epic-only), personality
2. **Universal Style**: Response format, language, length
3. **Core Guardrails**: Consent model, pre-flight requirements
4. **Handoff Policy**: When/how to redirect

Remove: Routing tables (→ docs), execution sequences (→ scenarios), repetitive examples

---

### Priority 5: Document Knowledge & Skills (Low Impact)
**Effort**: Low | **Impact**: Low

Create supplementary files:
- `knowledge-sources.md`: List expected Confluence spaces, Jira projects, internal standards
- Enhance `skills.md` with usage notes and prerequisites
- Add automation integration examples

---

## Best Practices Already Implemented ✅

1. **Scenario Modularity**: Excellent use of scenarios to prevent agent sprawl
2. **Permission-Aware**: Properly respects user permissions
3. **No Scope Creep**: Clear boundaries with redirects to Product Backlog Studio
4. **Audit Trail**: Confirmation messages with keys/links after actions
5. **Fallback Strategy**: Markdown outputs when skills unavailable
6. **Bilingual Consideration**: French primary with clear locale handling
7. **Version Control Ready**: File structure supports GitOps workflows

---

## Comparison to Atlassian Out-of-the-Box Agents

Epic Studio compares favorably to Atlassian's own agents like "Readiness Checker" and "Work Item Planner" in complexity and scope. However, Atlassian's agents typically use:
- Shorter, more focused instructions (150-250 words)
- Standardized trigger formats with 3+ positive examples
- Explicit conversation starters
- Clear skill limitations documented

Epic Studio's architecture is actually more sophisticated than most OOTB agents due to its automation integration and dual-mode operation, but it needs to adopt the standardized formatting conventions.

---

## Final Assessment

**Score Breakdown**:
- Architecture & Structure: 9/10
- Documentation: 8/10
- Trigger Quality: 6/10 ⚠️
- Instruction Clarity: 7/10 ⚠️
- Skills Configuration: 7/10
- Behavior Design: 7/10
- Guardrails & Safety: 10/10
- Automation Integration: 9/10
- User Experience: 7/10
- Maintainability: 8/10

**Overall: 78/100** — **Good foundation with room for optimization**

Epic Studio demonstrates advanced understanding of Rovo's capabilities and has a solid architectural foundation. The main gaps are in adopting Atlassian's latest guidance on trigger formatting and instruction brevity, which were formalized in late 2024/early 2025. Implementing the recommended changes would bring this to an **88-92/100** score.

The agent is production-ready but would benefit from the refinements above to maximize reliability and user satisfaction.