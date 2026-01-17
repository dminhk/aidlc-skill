# Vision Stage - Detailed Steps

## Purpose
**Capture strategic intent and stakeholder alignment for complex projects**

The Vision Stage focuses on:
- Establishing clear project vision and strategic goals
- Identifying and mapping stakeholders with their interests
- Defining success criteria and key outcomes
- Creating shared understanding of project direction
- Providing foundation for epic and story development

## Prerequisites
- Workspace Detection must be complete
- This stage runs BEFORE Requirements Analysis (when executed)

## Intelligent Assessment Guidelines

**WHEN TO EXECUTE VISION STAGE**: Use this enhanced assessment:

### High Priority Execution (ALWAYS Execute)
- **New Product Development**: Building something from scratch
- **Multiple Stakeholders**: Different business units, teams, or user groups involved
- **Strategic Initiative**: Project tied to business strategy or OKRs
- **Cross-Functional Teams**: Multiple teams collaborating on the project
- **External Dependencies**: Partners, vendors, or customers involved
- **Long-Term Project**: Multi-quarter or multi-release scope

### Medium Priority Execution (Assess Complexity)
- **Major Feature Addition**: Significant new capability to existing product
- **Platform Change**: Migration or transformation project
- **Process Change**: Workflow or business process modifications
- **Integration Project**: Connecting multiple systems or services

### Complexity Assessment Factors
For medium priority cases, execute vision stage if ANY of these apply:
- **Stakeholder Count**: 3+ distinct stakeholder groups
- **Competing Priorities**: Stakeholders with potentially conflicting needs
- **Ambiguity**: Unclear or evolving project direction
- **Risk**: High business impact or visibility
- **Scope**: Project spans multiple domains or teams

### Skip For Simple Cases
- **Bug Fixes**: Single, well-defined issues
- **Minor Enhancements**: Small improvements to existing features
- **Technical Debt**: Internal code improvements
- **Single Developer**: Individual working on isolated changes
- **Clear Scope**: Requirements already well-understood by all parties
- **Short Duration**: Tasks completable in days, not weeks

### Default Decision Rule
**When in doubt, execute vision stage for any project involving multiple stakeholders or strategic importance.** The investment in vision clarity pays dividends in reduced miscommunication and rework.

---

# PART 1: PLANNING

## Step 1: Validate Vision Stage Need (MANDATORY)

**CRITICAL**: Before proceeding, perform this assessment:

### Assessment Process
1. **Analyze Request Context**:
   - Review the original user request
   - Identify stakeholder groups mentioned or implied
   - Assess project complexity and duration
   - Evaluate strategic alignment needs

2. **Apply Assessment Criteria**:
   - Check against High Priority indicators (always execute)
   - Evaluate Medium Priority factors (complexity-based decision)
   - Confirm this isn't a simple case that should be skipped

3. **Document Assessment Decision**:
   - Create `aidlc-docs/inception/plans/vision-assessment.md`
   - Include reasoning for why vision stage is valuable
   - Reference specific assessment criteria that apply

### Assessment Documentation Template
```markdown
# Vision Stage Assessment

## Request Analysis
- **Original Request**: [Brief summary]
- **Project Type**: [New Product/Major Feature/Enhancement/Other]
- **Duration Estimate**: [Short/Medium/Long term]
- **Stakeholder Count**: [Number of groups identified]

## Assessment Criteria Met
- [ ] High Priority: [List applicable criteria]
- [ ] Medium Priority: [List applicable criteria with justification]
- [ ] Benefits: [Expected value from vision stage]

## Decision
**Execute Vision Stage**: [Yes/No]
**Reasoning**: [Detailed justification]

## Expected Outcomes
- [List specific benefits vision stage will provide]
- [How vision clarity will improve project success]
```

## Step 2: Create Vision Plan

Generate a comprehensive plan for vision development:
- Define approach for capturing strategic intent
- Outline stakeholder identification process
- Plan vision articulation methodology
- Include step-by-step execution checklist with checkboxes []

## Step 3: Generate Vision Questions

**See `common/question-format-guide.md` for question formatting rules**

Generate context-appropriate questions using [Answer]: tag format:

**Question categories to evaluate**:
- **Strategic Context** - Business drivers, market conditions, competitive landscape
- **Success Definition** - How will success be measured? What outcomes matter?
- **Stakeholder Identification** - Who are the key stakeholders? Decision makers?
- **Constraints and Boundaries** - Time, budget, technology, regulatory constraints
- **Risk Tolerance** - How much uncertainty is acceptable? What are dealbreakers?
- **Vision Scope** - What is in/out of scope for this vision?
- **Timeline Expectations** - What are the key milestones or deadlines?

## Step 4: Include Mandatory Vision Artifacts in Plan

**ALWAYS** include these mandatory artifacts in the vision plan:
- [ ] Generate `vision-statement.md` with clear vision articulation
- [ ] Generate `stakeholder-map.md` with stakeholder analysis
- [ ] Define success criteria and key results
- [ ] Document strategic alignment
- [ ] Identify known constraints and assumptions

## Step 5: Present Vision Approach Options

Include different approaches for vision development:
- **Business-Driven**: Vision centered on business outcomes and metrics
- **User-Driven**: Vision centered on user value and experience
- **Technology-Driven**: Vision centered on technical capabilities
- **Market-Driven**: Vision centered on market position and competition
- **Hybrid**: Balanced approach combining multiple perspectives

## Step 6: Store Vision Plan

Save the complete vision plan with embedded questions:
- Filename: `aidlc-docs/inception/plans/vision-plan.md`
- Include all [Answer]: tags for user input
- Ensure plan covers all vision development aspects

## Step 7: Request User Input

- Ask user to fill in all [Answer]: tags in the vision plan document
- Emphasize importance of stakeholder input
- Provide clear instructions on answer format

## Step 8: Collect Answers

- Wait for user to provide answers to all questions
- Do not proceed until ALL [Answer]: tags are completed
- Review document to ensure completeness

## Step 9: ANALYZE ANSWERS (MANDATORY)

Before proceeding, carefully review all answers for:
- **Vague or ambiguous responses**: "not sure", "depends", "maybe"
- **Missing stakeholder details**: References without identification
- **Contradictory answers**: Conflicting priorities or goals
- **Undefined success criteria**: Metrics without clear definitions
- **Incomplete context**: Answers that assume unstated knowledge

## Step 10: MANDATORY Follow-up Questions

If analysis reveals ANY ambiguous answers:
- Create separate clarification questions file
- DO NOT proceed until ALL ambiguities are resolved
- Examples of required follow-ups:
  - "You mentioned 'key stakeholders' - can you list specific individuals or roles?"
  - "You said 'success means growth' - what specific metrics define growth?"
  - "You indicated 'timeline is flexible' - what is the outer boundary?"

## Step 11: Log Approval Prompt

- Log the prompt with timestamp in `aidlc-docs/audit.md`
- Include complete approval prompt text
- Use ISO 8601 timestamp format

## Step 12: Wait for Explicit Approval of Plan

- Do not proceed until user explicitly approves the vision approach
- If user requests changes, update plan and repeat approval process

## Step 13: Record Approval Response

- Log user's approval response with timestamp in `aidlc-docs/audit.md`
- Include exact user response text
- Mark approval status clearly

---

# PART 2: GENERATION

## Step 14: Load Vision Plan

- [ ] Read complete vision plan from `aidlc-docs/inception/plans/vision-plan.md`
- [ ] Identify next uncompleted step
- [ ] Load context and requirements for that step

## Step 15: Execute Current Step

- [ ] Perform exactly what the current step describes
- [ ] Generate vision artifacts as specified
- [ ] Follow approved methodology from Planning

## Step 16: Generate Vision Statement

Create `aidlc-docs/inception/vision/vision-statement.md`:

```markdown
# Vision Statement

## Project Vision
[Clear, concise statement of what we're building and why]

## Strategic Alignment
- **Business Goal**: [How this aligns with business objectives]
- **User Value**: [Primary value delivered to users]
- **Market Position**: [Competitive or market positioning]

## Success Criteria
| Criterion | Metric | Target | Measurement Method |
|-----------|--------|--------|-------------------|
| [Criterion 1] | [Metric] | [Target value] | [How measured] |
| [Criterion 2] | [Metric] | [Target value] | [How measured] |

## Key Outcomes
1. **Primary Outcome**: [Most important result]
2. **Secondary Outcome**: [Supporting result]
3. **Tertiary Outcome**: [Additional value]

## Scope Boundaries

### In Scope
- [Item 1]
- [Item 2]

### Out of Scope
- [Item 1]
- [Item 2]

## Constraints
- **Time**: [Timeline constraints]
- **Budget**: [Resource constraints]
- **Technology**: [Technical constraints]
- **Regulatory**: [Compliance constraints]

## Assumptions
- [Assumption 1]
- [Assumption 2]

## Risks
| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| [Risk 1] | [H/M/L] | [H/M/L] | [Strategy] |
```

## Step 17: Generate Stakeholder Map

Create `aidlc-docs/inception/vision/stakeholder-map.md`:

```markdown
# Stakeholder Map

## Stakeholder Overview
- **Total Stakeholders Identified**: [Count]
- **Primary Decision Makers**: [Count]
- **Key Influencers**: [Count]

## Stakeholder Matrix

### High Power, High Interest (Manage Closely)
| Stakeholder | Role | Interest | Influence | Engagement Strategy |
|-------------|------|----------|-----------|---------------------|
| [Name/Role] | [Position] | [What they care about] | [Decision/Veto/Advisory] | [How to engage] |

### High Power, Low Interest (Keep Satisfied)
| Stakeholder | Role | Interest | Influence | Engagement Strategy |
|-------------|------|----------|-----------|---------------------|

### Low Power, High Interest (Keep Informed)
| Stakeholder | Role | Interest | Influence | Engagement Strategy |
|-------------|------|----------|-----------|---------------------|

### Low Power, Low Interest (Monitor)
| Stakeholder | Role | Interest | Influence | Engagement Strategy |
|-------------|------|----------|-----------|---------------------|

## Stakeholder Relationships

### Decision Authority
```
[Decision Maker 1]
     |
     +-- [Influencer A]
     +-- [Influencer B]

[Decision Maker 2]
     |
     +-- [Influencer C]
```

### Communication Plan
| Stakeholder Group | Frequency | Channel | Content |
|-------------------|-----------|---------|---------|
| Decision Makers | [Weekly/Bi-weekly] | [Meeting/Email] | [What to share] |
| Influencers | [Frequency] | [Channel] | [Content] |
| Informed | [Frequency] | [Channel] | [Content] |

## Potential Conflicts
| Stakeholders | Conflict Area | Resolution Approach |
|--------------|---------------|---------------------|
| [A vs B] | [Topic] | [How to resolve] |

## RACI Matrix
| Decision Area | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| [Area 1] | [Role] | [Role] | [Roles] | [Roles] |
| [Area 2] | [Role] | [Role] | [Roles] | [Roles] |
```

## Step 18: Update Progress

- [ ] Mark completed step as [x] in vision plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save all generated artifacts

## Step 19: Sync with Jira (if available)

If Jira MCP is available:
- Create parent Epic representing the vision
- Attach vision-statement.md as documentation
- Log sync in `jira-sync-log.md`

## Step 20: Continue or Complete Generation

- [ ] If more steps remain, return to Step 14
- [ ] If all steps complete, verify artifacts ready for next stage

## Step 21: Log Approval Prompt

- Log approval prompt with timestamp in `aidlc-docs/audit.md`

## Step 22: Present Completion Message

Present completion message in this structure:

```markdown
# Vision Stage Complete

Vision stage has established strategic direction:

- **Vision Statement**: Created with [X] success criteria defined
- **Stakeholder Map**: Identified [Y] stakeholders across [Z] groups
- **Strategic Alignment**: Documented business goals and constraints
- **Scope Boundaries**: Defined in/out of scope items

> **REVIEW REQUIRED:**
> Please examine the vision artifacts at: `aidlc-docs/inception/vision/`

> **WHAT'S NEXT?**
>
> **You may:**
>
> **Request Changes** - Ask for modifications to vision or stakeholder mapping
> **Approve & Continue** - Proceed to **Requirements Analysis** (or **Reverse Engineering** if brownfield)
```

## Step 23: Wait for Explicit Approval

- Do not proceed until user explicitly approves generated artifacts
- If changes requested, update and repeat approval process

## Step 24: Record Approval Response

- Log approval response with timestamp in `aidlc-docs/audit.md`
- Mark approval status clearly

## Step 25: Update Progress

- Mark Vision Stage complete in `aidlc-state.md`
- Update "Current Status" section
- Prepare for transition to next stage

---

# CRITICAL RULES

## Planning Phase Rules
- **CONTEXT-APPROPRIATE QUESTIONS**: Only ask questions relevant to this specific project
- **MANDATORY ANSWER ANALYSIS**: Always analyze answers for ambiguities
- **NO PROCEEDING WITH AMBIGUITY**: Must resolve all vague answers before generation
- **EXPLICIT APPROVAL REQUIRED**: User must approve plan before generation starts

## Generation Phase Rules
- **NO HARDCODED LOGIC**: Only execute what's written in the vision plan
- **FOLLOW PLAN EXACTLY**: Do not deviate from step sequence
- **UPDATE CHECKBOXES**: Mark [x] immediately after completing each step
- **JIRA SYNC OPTIONAL**: Sync if available, continue if not
- **VERIFY COMPLETION**: Ensure all artifacts complete before proceeding

## Completion Criteria
- All planning questions answered and ambiguities resolved
- Vision plan explicitly approved by user
- All steps in vision plan marked [x]
- All vision artifacts generated (vision-statement.md, stakeholder-map.md)
- Generated artifacts explicitly approved by user
- Vision ready to inform subsequent stages
