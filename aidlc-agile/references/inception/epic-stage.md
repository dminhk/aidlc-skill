# Epic Stage - Detailed Steps

## Purpose
**Group user stories into epics for better organization and release planning**

The Epic Stage focuses on:
- Organizing user stories into logical epic groupings
- Defining epic boundaries and scope
- Establishing epic dependencies and sequencing
- Creating story-to-epic mappings
- Enabling release and sprint planning

## Prerequisites
- User Stories stage must be complete
- `stories.md` and `personas.md` must exist
- This stage runs AFTER User Stories (when executed)

## Intelligent Assessment Guidelines

**WHEN TO EXECUTE EPIC STAGE**: Use this enhanced assessment:

### High Priority Execution (ALWAYS Execute)
- **5+ User Stories**: Sufficient stories to warrant grouping
- **Natural Groupings**: Stories cluster around distinct themes or features
- **Multi-Release Project**: Work spans multiple releases or sprints
- **Large Team**: Multiple developers or teams working in parallel
- **Complex Dependencies**: Stories have interdependencies
- **Portfolio Alignment**: Epics needed for portfolio-level tracking

### Medium Priority Execution (Assess Complexity)
- **3-5 User Stories**: May benefit from grouping
- **Thematic Clusters**: Some stories share common themes
- **Jira Integration**: Epics needed for Jira structure
- **Stakeholder Reporting**: Epics simplify status communication

### Complexity Assessment Factors
For medium priority cases, execute epic stage if ANY of these apply:
- **Story Count**: 5+ stories created
- **Feature Clusters**: 2+ distinct feature areas identified
- **Release Planning**: Need to assign stories to releases
- **Team Organization**: Stories will be worked on by different teams
- **Dependency Chains**: Stories have execution order dependencies

### Skip For Simple Cases
- **Less than 5 Stories**: Too few stories to warrant epic structure
- **Linear Implementation**: All stories in single execution sequence
- **Single Feature**: All stories for one cohesive feature
- **Short Project**: Single sprint or iteration scope
- **No Grouping Benefit**: Flat backlog is clearer

### Default Decision Rule
**When in doubt, execute epic stage if there are 5+ stories or natural groupings exist.** Epic organization pays dividends in clarity and planning.

---

# PART 1: PLANNING

## Step 1: Validate Epic Stage Need (MANDATORY)

**CRITICAL**: Before proceeding, perform this assessment:

### Assessment Process
1. **Load User Stories**:
   - Read `aidlc-docs/inception/user-stories/stories.md`
   - Count total number of stories
   - Identify potential groupings

2. **Analyze Story Relationships**:
   - Look for common themes
   - Identify shared personas
   - Find feature clusters
   - Detect dependency chains

3. **Apply Assessment Criteria**:
   - Check against High Priority indicators
   - Evaluate Medium Priority factors
   - Confirm this isn't a simple case to skip

4. **Document Assessment Decision**:
   - Create `aidlc-docs/inception/plans/epic-assessment.md`
   - Include story count and grouping analysis
   - Reference criteria that apply

### Assessment Documentation Template
```markdown
# Epic Stage Assessment

## Story Analysis
- **Total Stories**: [Count]
- **Potential Epic Groups**: [List identified themes]
- **Cross-Cutting Stories**: [Stories that span multiple themes]

## Assessment Criteria Met
- [ ] High Priority: [List applicable criteria]
- [ ] Medium Priority: [List applicable criteria]
- [ ] Benefits: [Expected value from epic organization]

## Decision
**Execute Epic Stage**: [Yes/No]
**Reasoning**: [Detailed justification]

## Proposed Epic Structure
[If executing, outline initial epic grouping thoughts]
```

## Step 2: Create Epic Plan

Generate a comprehensive plan for epic development:
- Define epic identification methodology
- Outline dependency analysis approach
- Plan story mapping process
- Include step-by-step execution checklist with checkboxes []

## Step 3: Generate Epic Questions

**See `common/question-format-guide.md` for question formatting rules**

Generate context-appropriate questions using [Answer]: tag format:

**Question categories to evaluate**:
- **Grouping Criteria** - What defines an epic boundary? Feature, persona, domain?
- **Epic Granularity** - How large should epics be? Stories per epic?
- **Dependency Handling** - How to manage cross-epic dependencies?
- **Release Alignment** - Should epics align with releases?
- **Naming Convention** - How should epics be named?
- **Priority Inheritance** - Do stories inherit epic priority?

## Step 4: Include Mandatory Epic Artifacts in Plan

**ALWAYS** include these mandatory artifacts in the epic plan:
- [ ] Generate `epics.md` with epic definitions
- [ ] Generate `epic-dependency.md` with dependency relationships
- [ ] Generate `epic-story-map.md` linking stories to epics
- [ ] Document epic acceptance criteria
- [ ] Define epic completion criteria

## Step 5: Present Epic Organization Options

Include different approaches for epic organization:
- **Feature-Based**: Epics represent distinct features
- **Persona-Based**: Epics organized by user persona
- **Domain-Based**: Epics align with business domains
- **Journey-Based**: Epics follow user journeys
- **Release-Based**: Epics map to release targets
- **Hybrid**: Combination based on context

## Step 6: Store Epic Plan

Save the complete epic plan with embedded questions:
- Filename: `aidlc-docs/inception/plans/epic-plan.md`
- Include all [Answer]: tags for user input

## Step 7: Request User Input

- Ask user to fill in all [Answer]: tags in the epic plan document
- Provide clear instructions on answer format

## Step 8: Collect Answers

- Wait for user to provide answers to all questions
- Do not proceed until ALL [Answer]: tags are completed

## Step 9: ANALYZE ANSWERS (MANDATORY)

Before proceeding, carefully review all answers for:
- **Vague grouping criteria**: "group by theme" without defining themes
- **Conflicting organization**: Wanting both persona and feature grouping
- **Unclear boundaries**: Stories that could fit multiple epics
- **Missing priorities**: No indication of epic ordering

## Step 10: MANDATORY Follow-up Questions

If analysis reveals ANY ambiguous answers:
- Create separate clarification questions file
- DO NOT proceed until ALL ambiguities are resolved
- Examples:
  - "You mentioned 'group by feature' - what defines a feature boundary?"
  - "Stories X, Y, Z could fit multiple epics - which takes precedence?"
  - "You want persona-based epics - how do cross-persona stories get assigned?"

## Step 11: Log Approval Prompt

- Log the prompt with timestamp in `aidlc-docs/audit.md`

## Step 12: Wait for Explicit Approval of Plan

- Do not proceed until user explicitly approves the epic approach
- If user requests changes, update plan and repeat

## Step 13: Record Approval Response

- Log user's approval response with timestamp in `aidlc-docs/audit.md`

---

# PART 2: GENERATION

## Step 14: Load Epic Plan

- [ ] Read complete epic plan from `aidlc-docs/inception/plans/epic-plan.md`
- [ ] Load user stories from `aidlc-docs/inception/user-stories/stories.md`
- [ ] Identify next uncompleted step

## Step 15: Execute Current Step

- [ ] Perform exactly what the current step describes
- [ ] Generate epic artifacts as specified
- [ ] Follow approved methodology from Planning

## Step 16: Generate Epics Document

Create `aidlc-docs/inception/epics/epics.md`:

```markdown
# Epics

## Epic Overview
- **Total Epics**: [Count]
- **Total Stories Mapped**: [Count]
- **Organization Method**: [Feature/Persona/Domain/etc.]

## Epic Summary

| Epic ID | Name | Stories | Priority | Status |
|---------|------|---------|----------|--------|
| E1 | [Name] | [Count] | [P1-P4] | [New/Ready/In Progress/Done] |
| E2 | [Name] | [Count] | [P1-P4] | [Status] |

---

## Epic Details

### E1: [Epic Name]

**Description**: [What this epic delivers]

**Business Value**: [Why this epic matters]

**Acceptance Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]

**Completion Criteria**:
- All stories in Done status
- [Additional criteria]

**Stories Included**:
| Story ID | Title | Priority | Status |
|----------|-------|----------|--------|
| S1 | [Title] | [Priority] | [Status] |
| S2 | [Title] | [Priority] | [Status] |

**Dependencies**:
- Depends On: [List epic IDs]
- Blocks: [List epic IDs]

**Estimated Effort**: [Story points or t-shirt size]

---

### E2: [Epic Name]

[Same structure as E1]

---

## Unassigned Stories

Stories not yet assigned to an epic:

| Story ID | Title | Reason |
|----------|-------|--------|
| [If any] | | |

## Cross-Cutting Stories

Stories that span multiple epics:

| Story ID | Title | Primary Epic | Related Epics |
|----------|-------|--------------|---------------|
| [If any] | | | |
```

## Step 17: Generate Epic Dependency Document

Create `aidlc-docs/inception/epics/epic-dependency.md`:

```markdown
# Epic Dependencies

## Dependency Overview

Total dependency relationships: [Count]

## Dependency Matrix

|          | E1 | E2 | E3 | E4 |
|----------|----|----|----|----|
| **E1**   | -  | B  |    |    |
| **E2**   | D  | -  | B  |    |
| **E3**   |    | D  | -  | B  |
| **E4**   |    |    | D  | -  |

**Legend**: D = Depends On, B = Blocks, - = Self

## Dependency Details

### E1: [Epic Name]
- **Depends On**: None (can start immediately)
- **Blocks**: E2 (must complete before E2 starts)

### E2: [Epic Name]
- **Depends On**: E1 (requires E1 completion)
- **Blocks**: E3

### E3: [Epic Name]
- **Depends On**: E2
- **Blocks**: E4

### E4: [Epic Name]
- **Depends On**: E3
- **Blocks**: None

## Critical Path

```
E1 --> E2 --> E3 --> E4
```

**Critical Path Duration**: [Total of critical path epic estimates]

## Parallel Execution Opportunities

Epics that can be worked on simultaneously:

| Group | Epics | Constraint |
|-------|-------|------------|
| [If any parallel groups] | | |

## Dependency Risks

| Risk | Epics Affected | Mitigation |
|------|----------------|------------|
| [Dependency risk 1] | [Epics] | [How to mitigate] |
```

## Step 18: Generate Epic-Story Map

Create `aidlc-docs/inception/epics/epic-story-map.md`:

```markdown
# Epic-Story Map

## Visual Map

```
+-------------------+     +-------------------+
|    E1: [Name]     |     |    E2: [Name]     |
+-------------------+     +-------------------+
| S1: [Story]       |     | S4: [Story]       |
| S2: [Story]       |     | S5: [Story]       |
| S3: [Story]       |     | S6: [Story]       |
+-------------------+     +-------------------+
         |                         |
         v                         v
+-------------------+     +-------------------+
|    E3: [Name]     |     |    E4: [Name]     |
+-------------------+     +-------------------+
| S7: [Story]       |     | S10: [Story]      |
| S8: [Story]       |     | S11: [Story]      |
| S9: [Story]       |     | S12: [Story]      |
+-------------------+     +-------------------+
```

## Mapping Table

| Epic | Story ID | Story Title | Priority | Points |
|------|----------|-------------|----------|--------|
| E1 | S1 | [Title] | P1 | [Points] |
| E1 | S2 | [Title] | P2 | [Points] |
| E2 | S4 | [Title] | P1 | [Points] |

## Summary by Epic

| Epic | Story Count | Total Points | Priority Distribution |
|------|-------------|--------------|----------------------|
| E1 | [Count] | [Points] | P1:[X], P2:[Y], P3:[Z] |
| E2 | [Count] | [Points] | P1:[X], P2:[Y], P3:[Z] |

## Persona Coverage

| Persona | Epics | Story Count |
|---------|-------|-------------|
| [Persona 1] | E1, E2 | [Count] |
| [Persona 2] | E2, E3 | [Count] |

## Coverage Analysis

### Epics by Size
- **Large (10+ stories)**: [List]
- **Medium (5-9 stories)**: [List]
- **Small (<5 stories)**: [List]

### Recommendations
- [Any recommendations for epic rebalancing]
```

## Step 19: Update Progress

- [ ] Mark completed step as [x] in epic plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save all generated artifacts

## Step 20: Sync with Jira (if available)

If Jira MCP is available:
- Create Epic issues for each epic
- Create links between epics (blocks/blocked by)
- Link stories to parent epics
- Log sync in `jira-sync-log.md`

## Step 21: Continue or Complete Generation

- [ ] If more steps remain, return to Step 14
- [ ] If all steps complete, verify artifacts ready for next stage

## Step 22: Log Approval Prompt

- Log approval prompt with timestamp in `aidlc-docs/audit.md`

## Step 23: Present Completion Message

Present completion message in this structure:

```markdown
# Epic Stage Complete

Epic stage has organized stories into epics:

- **Epics Created**: [X] epics defined
- **Stories Mapped**: [Y] stories assigned to epics
- **Dependencies**: [Z] epic dependencies identified
- **Organization**: [Method used] approach applied

> **REVIEW REQUIRED:**
> Please examine the epic artifacts at: `aidlc-docs/inception/epics/`

> **WHAT'S NEXT?**
>
> **You may:**
>
> **Request Changes** - Ask for modifications to epic structure or mappings
> **Approve & Continue** - Proceed to **Workflow Planning**
```

## Step 24: Wait for Explicit Approval

- Do not proceed until user explicitly approves generated artifacts
- If changes requested, update and repeat approval process

## Step 25: Record Approval Response

- Log approval response with timestamp in `aidlc-docs/audit.md`

## Step 26: Update Progress

- Mark Epic Stage complete in `aidlc-state.md`
- Update "Current Status" section
- Prepare for transition to Workflow Planning

---

# CRITICAL RULES

## Planning Phase Rules
- **CONTEXT-APPROPRIATE QUESTIONS**: Only ask questions relevant to this project
- **MANDATORY ANSWER ANALYSIS**: Always analyze answers for ambiguities
- **NO PROCEEDING WITH AMBIGUITY**: Must resolve all vague answers
- **EXPLICIT APPROVAL REQUIRED**: User must approve plan before generation

## Generation Phase Rules
- **LOAD STORIES FIRST**: Always load existing stories before epic work
- **NO HARDCODED LOGIC**: Only execute what's written in the epic plan
- **FOLLOW PLAN EXACTLY**: Do not deviate from step sequence
- **UPDATE CHECKBOXES**: Mark [x] immediately after completing each step
- **JIRA SYNC OPTIONAL**: Sync if available, continue if not
- **VERIFY MAPPINGS**: Ensure all stories are mapped (or explicitly unassigned)

## Completion Criteria
- All planning questions answered and ambiguities resolved
- Epic plan explicitly approved by user
- All steps in epic plan marked [x]
- All epic artifacts generated (epics.md, epic-dependency.md, epic-story-map.md)
- All stories mapped to epics (or documented as unassigned)
- Generated artifacts explicitly approved by user
- Epics ready to inform Workflow Planning and backlog
