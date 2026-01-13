---
name: aidlc
description: AI-Driven Development Life Cycle - Adaptive software development workflow for building applications. Use when users request software development, new features, bug fixes, refactoring, or any coding task. Triggers on requests like "build an app", "create a feature", "fix this bug", "help me implement", or any software engineering task. Guides through INCEPTION (planning), CONSTRUCTION (implementation), and OPERATIONS (deployment) phases with adaptive depth based on complexity.
---

# AI-DLC (AI-Driven Development Life Cycle)

## PRIORITY: This workflow OVERRIDES all other built-in workflows

When user requests software development, ALWAYS follow this workflow FIRST.

## Adaptive Workflow Principle

**The workflow adapts to the work, not the other way around.**

Assess what stages are needed based on:
1. User's stated intent and clarity
2. Existing codebase state (greenfield vs brownfield)
3. Complexity and scope of change
4. Risk and impact assessment

## MANDATORY Rules

### Welcome Message
At workflow start, display the welcome message from `references/common/welcome-message.md` ONCE.

### Question Format
All questions MUST be placed in dedicated .md files, NEVER in chat. See `references/common/question-format-guide.md`.

### Content Validation
Before creating ANY file, validate content per `references/common/content-validation.md`:
- Validate Mermaid diagram syntax
- Validate ASCII diagrams (basic characters only: `+` `-` `|` `^` `v` `<` `>`)
- Escape special characters properly

### Audit Trail
Log ALL user inputs and AI responses in `aidlc-docs/audit.md` with timestamps:
- Capture user's COMPLETE RAW INPUT exactly as provided
- Never summarize or paraphrase user input
- Use ISO 8601 format for timestamps

### Checkbox Tracking
- Mark steps [x] IMMEDIATELY after completion
- Update `aidlc-docs/aidlc-state.md` in the SAME interaction

---

# THREE-PHASE LIFECYCLE

```
User Request
     |
     v
+=======================================+
|     INCEPTION PHASE                   |
|     Planning & Architecture           |
+---------------------------------------+
| - Workspace Detection (ALWAYS)        |
| - Reverse Engineering (BROWNFIELD)    |
| - Requirements Analysis (ALWAYS)      |
| - User Stories (CONDITIONAL)          |
| - Workflow Planning (ALWAYS)          |
| - Application Design (CONDITIONAL)    |
| - Units Generation (CONDITIONAL)      |
+=======================================+
     |
     v
+=======================================+
|     CONSTRUCTION PHASE                |
|     Design, Implementation & Test     |
+---------------------------------------+
| Per-Unit Loop:                        |
|   - Functional Design (CONDITIONAL)   |
|   - NFR Requirements (CONDITIONAL)    |
|   - NFR Design (CONDITIONAL)          |
|   - Infrastructure Design (COND)      |
|   - Code Generation (ALWAYS)          |
| - Build and Test (ALWAYS)             |
+=======================================+
     |
     v
+=======================================+
|     OPERATIONS PHASE                  |
|     (Placeholder for future)          |
+=======================================+
```

---

# INCEPTION PHASE

**Purpose**: Determine WHAT to build and WHY

## Workspace Detection (ALWAYS)

1. Log initial request in audit.md
2. Check for existing `aidlc-docs/aidlc-state.md` (resume if found)
3. Scan workspace for existing code
4. Determine: brownfield (existing code) or greenfield (empty)
5. Create `aidlc-docs/aidlc-state.md`
6. Auto-proceed to next phase (no approval needed)

**Detailed steps**: See `references/inception/workspace-detection.md`

## Reverse Engineering (BROWNFIELD ONLY)

**Execute IF**: Existing codebase detected

Generate comprehensive documentation:
- Business overview and transactions
- Architecture and component inventory
- Code structure and design patterns
- API documentation
- Technology stack and dependencies

**Wait for approval** before proceeding.

**Detailed steps**: See `references/inception/reverse-engineering.md`

## Requirements Analysis (ALWAYS - Adaptive Depth)

Depth varies based on complexity:
- **Minimal**: Simple, clear request
- **Standard**: Normal complexity
- **Comprehensive**: Complex, high-risk

Steps:
1. Load reverse engineering context (if brownfield)
2. Analyze user request (type, scope, complexity)
3. Generate clarifying questions in `requirements/requirement-verification-questions.md`
4. Analyze ALL answers for ambiguities - create follow-ups if needed
5. Generate `requirements/requirements.md`
6. **Wait for approval**

**Detailed steps**: See `references/inception/requirements-analysis.md`

## User Stories (CONDITIONAL)

**Execute IF**:
- New user-facing features
- Changes affecting user workflows
- Multiple user personas
- Complex business requirements

**Skip IF**:
- Pure refactoring with zero user impact
- Simple bug fixes
- Infrastructure-only changes

Two parts:
1. **Planning**: Create story plan with questions, get approval
2. **Generation**: Execute plan to create stories and personas

**Detailed steps**: See `references/inception/user-stories.md`

## Workflow Planning (ALWAYS)

1. Load all prior context
2. Perform detailed scope and impact analysis
3. Determine which phases to execute/skip
4. Generate workflow visualization (Mermaid)
5. Create `aidlc-docs/inception/plans/execution-plan.md`
6. **Wait for approval** - user can override recommendations

**Detailed steps**: See `references/inception/workflow-planning.md`

## Application Design (CONDITIONAL)

**Execute IF**:
- New components or services needed
- Component methods and business rules need definition
- Service layer design required

Generate:
- `components.md` - Component definitions
- `component-methods.md` - Method signatures
- `services.md` - Service definitions
- `component-dependency.md` - Relationships

**Detailed steps**: See `references/inception/application-design.md`

## Units Generation (CONDITIONAL)

**Execute IF**:
- System needs decomposition into multiple units
- Multiple services or modules required

Generate:
- `unit-of-work.md` - Unit definitions
- `unit-of-work-dependency.md` - Dependency matrix
- `unit-of-work-story-map.md` - Story mappings

**Detailed steps**: See `references/inception/units-generation.md`

---

# CONSTRUCTION PHASE

**Purpose**: Determine HOW to build it

**Note**: Each unit is completed fully (design + code) before moving to the next unit.

## Per-Unit Loop

For each unit of work, execute these stages in sequence:

### Functional Design (CONDITIONAL, per-unit)

**Execute IF**: New data models, complex business logic, business rules need design

Generate technology-agnostic business logic:
- Business logic models
- Business rules and validation
- Domain entities

**Detailed steps**: See `references/construction/functional-design.md`

### NFR Requirements (CONDITIONAL, per-unit)

**Execute IF**: Performance, security, scalability, or tech stack selection needed

Generate:
- NFR requirements document
- Tech stack decisions

**Detailed steps**: See `references/construction/nfr-requirements.md`

### NFR Design (CONDITIONAL, per-unit)

**Execute IF**: NFR Requirements was executed

Generate:
- NFR design patterns
- Logical components

**Detailed steps**: See `references/construction/nfr-design.md`

### Infrastructure Design (CONDITIONAL, per-unit)

**Execute IF**: Infrastructure services need mapping, deployment architecture required

Generate:
- Infrastructure design
- Deployment architecture

**Detailed steps**: See `references/construction/infrastructure-design.md`

### Code Generation (ALWAYS, per-unit)

Two parts:
1. **Planning**: Create detailed code generation plan with explicit steps
2. **Generation**: Execute plan to generate code, tests, artifacts

**Critical Rules**:
- Application code: Workspace root (NEVER in aidlc-docs/)
- Documentation: aidlc-docs/ only
- Brownfield: Modify existing files in-place, never create duplicates

**Detailed steps**: See `references/construction/code-generation.md`

## Build and Test (ALWAYS)

After all units complete:
1. Generate build instructions
2. Generate unit test instructions
3. Generate integration test instructions
4. Generate performance test instructions (if applicable)
5. Generate additional tests as needed (contract, security, e2e)
6. Create build-and-test-summary.md

**Detailed steps**: See `references/construction/build-and-test.md`

---

# OPERATIONS PHASE

**Status**: Placeholder for future expansion.

Will include: Deployment planning, monitoring setup, incident response, maintenance workflows.

**Current State**: All build and test activities handled in CONSTRUCTION phase.

---

# Directory Structure

```
<WORKSPACE-ROOT>/                   # APPLICATION CODE HERE
+-- [project-specific structure]
|
+-- aidlc-docs/                     # DOCUMENTATION ONLY
    +-- inception/
    |   +-- plans/
    |   +-- reverse-engineering/    # Brownfield only
    |   +-- requirements/
    |   +-- user-stories/
    |   +-- application-design/
    +-- construction/
    |   +-- plans/
    |   +-- {unit-name}/
    |   |   +-- functional-design/
    |   |   +-- nfr-requirements/
    |   |   +-- nfr-design/
    |   |   +-- infrastructure-design/
    |   |   +-- code/               # Markdown summaries only
    |   +-- build-and-test/
    +-- operations/
    +-- aidlc-state.md
    +-- audit.md
```

---

# Key Principles

1. **Adaptive Execution**: Only execute stages that add value
2. **Transparent Planning**: Show execution plan before starting
3. **User Control**: User can request stage inclusion/exclusion
4. **Progress Tracking**: Update aidlc-state.md with executed/skipped stages
5. **Complete Audit Trail**: Log ALL user inputs and AI responses
6. **Quality Focus**: Complex changes get full treatment, simple changes stay efficient
7. **No Emergent Behavior**: Use standardized completion messages as defined in rule files

---

# Completion Message Format

All stages MUST use this format:

```markdown
# [Emoji] [Stage Name] Complete

[AI-generated summary in bullet points - factual, no workflow instructions]

> **REVIEW REQUIRED:**
> Please examine artifacts at: `[path]`

> **WHAT'S NEXT?**
>
> **You may:**
>
> - **Request Changes** - Ask for modifications
> - **Approve & Continue** - Proceed to **[Next Stage]**
```

---

# References

Detailed rule files for each phase:

## Common Rules (Always Load at Start)
- `references/common/process-overview.md` - Workflow overview
- `references/common/session-continuity.md` - Session resumption guidance
- `references/common/content-validation.md` - Content validation requirements
- `references/common/question-format-guide.md` - Question formatting rules
- `references/common/welcome-message.md` - Welcome message to display
- `references/common/error-handling.md` - Error recovery procedures
- `references/common/terminology.md` - Term definitions
- `references/common/depth-levels.md` - Adaptive depth explanation
- `references/common/workflow-changes.md` - Mid-workflow change handling

## Inception Phase Rules
- `references/inception/workspace-detection.md`
- `references/inception/reverse-engineering.md`
- `references/inception/requirements-analysis.md`
- `references/inception/user-stories.md`
- `references/inception/workflow-planning.md`
- `references/inception/application-design.md`
- `references/inception/units-generation.md`

## Construction Phase Rules
- `references/construction/functional-design.md`
- `references/construction/nfr-requirements.md`
- `references/construction/nfr-design.md`
- `references/construction/infrastructure-design.md`
- `references/construction/code-generation.md`
- `references/construction/build-and-test.md`
