# AI-DLC Agile Welcome Message

**Purpose**: This file contains the user-facing welcome message that should be displayed ONCE at the start of any AI-DLC Agile workflow.

---

# Welcome to AI-DLC Agile (AI-Driven Development Life Cycle - Agile Variant)

I'll guide you through an adaptive software development workflow with agile practices, vision alignment, epic management, and continuous backlog tracking.

## What is AI-DLC Agile?

AI-DLC Agile extends the base AI-DLC workflow with agile-specific features:

- **Vision Stage** - Captures strategic intent and stakeholder alignment for complex projects
- **Epic Stage** - Groups user stories into logical epics for better organization
- **Product Backlog** - Living artifact updated at every approval gate
- **Jira Integration** - Optional sync with Jira via MCP (gracefully degrades if unavailable)

Think of it as having an experienced agile coach and software architect who:

- **Analyzes your requirements** and asks clarifying questions when needed
- **Aligns stakeholders** through vision statements and stakeholder mapping
- **Organizes work** into epics and stories with dependencies
- **Maintains a living backlog** that evolves throughout the project
- **Plans the optimal approach** based on complexity and risk
- **Documents everything** so you have a complete record of decisions and rationale

## The Three-Phase Lifecycle

```
                         User Request
                              |
                              v
        +=======================================+
        |     INCEPTION PHASE                   |
        |     Planning & Architecture           |
        +---------------------------------------+
        | - Workspace Detection (ALWAYS)        |
        | - Vision Stage (CONDITIONAL)          |
        | - Reverse Engineering (COND)          |
        | - Requirements Analysis (ALWAYS)      |
        | - User Stories (CONDITIONAL)          |
        | - Epic Stage (CONDITIONAL)            |
        | - Workflow Planning (ALWAYS)          |
        |   +-- Backlog Init (LIVING)           |
        | - Application Design (CONDITIONAL)    |
        | - Units Generation (CONDITIONAL)      |
        +=======================================+
                              |
                              v
        +=======================================+
        |     CONSTRUCTION PHASE                |
        |     Design, Implementation & Test     |
        +---------------------------------------+
        | - Per-Unit Loop (for each unit):      |
        |   - Functional Design (COND)          |
        |   - NFR Requirements Assess (COND)    |
        |   - NFR Design (COND)                 |
        |   - Infrastructure Design (COND)      |
        |   - Code Generation (ALWAYS)          |
        | - Build and Test (ALWAYS)             |
        +=======================================+
                              |
                              v
        +=======================================+
        |     OPERATIONS PHASE                  |
        |     Placeholder for Future            |
        +---------------------------------------+
        | - Operations (PLACEHOLDER)            |
        +=======================================+
                              |
                              v
                          Complete
```

### Phase Breakdown:

**INCEPTION PHASE** - *Planning & Architecture*
- **Purpose**: Determines WHAT to build and WHY
- **Activities**: Vision alignment, requirements gathering, story creation, epic organization, backlog initialization
- **Output**: Vision statement, stakeholder map, user stories, epics, product backlog, execution plan
- **Your Role**: Answer questions, review plans, approve direction

**CONSTRUCTION PHASE** - *Detailed Design, Implementation & Test*
- **Purpose**: Determines HOW to build it
- **Activities**: Detailed design (when needed), code generation, comprehensive testing
- **Output**: Working code, tests, build instructions
- **Your Role**: Review designs, approve implementation plans, validate results

**OPERATIONS PHASE** - *Deployment & Monitoring (Future)*
- **Purpose**: How to DEPLOY and RUN it
- **Status**: Placeholder for future deployment and monitoring workflows
- **Current State**: Build and test activities handled in CONSTRUCTION phase

## Agile Features

### Vision Stage (CONDITIONAL)
For complex projects with multiple stakeholders:
- Creates vision statement with success criteria
- Maps stakeholders with engagement strategies
- Syncs to Jira as parent Epic (if available)

### Epic Stage (CONDITIONAL)
For projects with 5+ user stories:
- Groups stories into logical epics
- Maps dependencies between epics
- Creates epic-story mapping

### Product Backlog (LIVING)
Continuously updated throughout the workflow:
- Initialized during Workflow Planning
- Updated at every approval gate
- Tracks priorities, status, and release planning

### Jira Integration (OPTIONAL)
Syncs artifacts with Jira via MCP:
- Creates epics, stories, and links
- Updates backlog status
- Gracefully degrades if unavailable

## Key Principles:

- **Fully Adaptive**: Each stage independently evaluated based on your needs
- **Efficient**: Simple changes execute only essential stages
- **Comprehensive**: Complex changes get full treatment with all safeguards
- **Transparent**: You see and approve the execution plan before work begins
- **Documented**: Complete audit trail of all decisions and changes
- **User Control**: You can request stages be included or excluded
- **Living Backlog**: Continuously updated, not created once and forgotten
- **Graceful Integration**: Optional integrations never block workflow

## What Happens Next:

1. **I'll analyze your workspace** to understand if this is a new or existing project
2. **I'll assess vision needs** for complex/multi-stakeholder projects
3. **I'll gather requirements** and ask clarifying questions if needed
4. **I'll create user stories** and organize them into epics (if applicable)
5. **I'll create an execution plan** showing which stages I propose to run and why
6. **I'll initialize the product backlog** as a living artifact
7. **You'll review and approve** the plan (or request changes)
8. **We'll execute the plan** with checkpoints at each major stage
9. **You'll get working code** with complete documentation and tests

The AI-DLC Agile process adapts to:
- Your intent clarity and complexity
- Existing codebase state
- Scope and impact of changes
- Stakeholder count and alignment needs
- Risk and quality requirements

Let's begin!
