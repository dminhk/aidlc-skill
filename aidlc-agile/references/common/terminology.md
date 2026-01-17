# AI-DLC Agile Terminology Glossary

## Core Terminology

### Phase vs Stage

**Phase**: One of the three high-level lifecycle phases in AI-DLC
- 🔵 **INCEPTION PHASE** - Planning & Architecture (WHAT and WHY)
- 🟢 **CONSTRUCTION PHASE** - Design, Implementation & Test (HOW)
- 🟡 **OPERATIONS PHASE** - Deployment & Monitoring (future expansion)

**Stage**: An individual workflow activity within a phase
- Examples: Context Assessment stage, Requirements Assessment stage, Code Planning stage
- Each stage has specific prerequisites, steps, and outputs
- Stages can be ALWAYS-EXECUTE or CONDITIONAL

**Usage Examples**:
- ✅ "The CONSTRUCTION phase contains 7 stages"
- ✅ "The Code Planning stage is always executed"
- ✅ "We're in the INCEPTION phase, executing the Requirements Assessment stage"
- ❌ "The Requirements Assessment phase" (should be "stage")
- ❌ "The CONSTRUCTION stage" (should be "phase")

## Three-Phase Lifecycle

### INCEPTION PHASE
**Purpose**: Planning and architectural decisions  
**Focus**: Determine WHAT to build and WHY  
**Location**: `inception/` directory

**Stages**:
- Workspace Detection (ALWAYS)
- Vision Stage (CONDITIONAL - Multi-stakeholder/strategic projects)
- Reverse Engineering (CONDITIONAL - Brownfield only)
- Requirements Analysis (ALWAYS - Adaptive depth)
- User Stories (CONDITIONAL)
- Epic Stage (CONDITIONAL - 5+ stories)
- Workflow Planning (ALWAYS)
- Backlog Init (LIVING - Updated at every approval gate)
- Application Design (CONDITIONAL)
- Design - Units Planning/Generation (CONDITIONAL)

**Outputs**: Requirements, vision statement, stakeholder map, user stories, epics, product backlog, architectural decisions, unit definitions

### CONSTRUCTION PHASE
**Purpose**: Detailed design and implementation  
**Focus**: Determine HOW to build it  
**Location**: `construction/` directory

**Stages**:
- Functional Design (CONDITIONAL, per-unit)
- NFR Requirements (CONDITIONAL, per-unit)
- NFR Design (CONDITIONAL, per-unit)
- Infrastructure Design (CONDITIONAL, per-unit)
- Code Planning (ALWAYS)
- Code Generation (ALWAYS)
- Build and Test (ALWAYS)

**Outputs**: Design artifacts, NFR implementations, code, tests

### OPERATIONS PHASE
**Purpose**: Deployment and operational readiness  
**Focus**: How to DEPLOY and RUN it  
**Location**: `operations/` directory

**Stages**:
- Operations (PLACEHOLDER)

**Outputs**: Build instructions, deployment guides, monitoring setup, verification procedures

---

## Workflow Stages

### Always-Execute Stages
- **Workspace Detection**: Initial analysis of workspace state and project type
- **Requirements Analysis**: Gathering requirements (depth varies based on complexity)
- **Workflow Planning**: Creating execution plan for which phases to run
- **Code Planning**: Creating detailed implementation plans for code generation
- **Code Generation**: Generating actual code based on plans and prior artifacts
- **Build and Test**: Building all units and executing comprehensive testing

### Conditional Stages
- **Vision Stage**: Capturing strategic intent and stakeholder alignment (multi-stakeholder/strategic projects)
- **Reverse Engineering**: Analyzing existing codebase (brownfield projects only)
- **User Stories**: Creating user stories and personas (includes Story Planning and Story Generation)
- **Epic Stage**: Grouping stories into epics with dependencies (5+ stories)
- **Application Design**: Designing application components, methods, business rules, and services
- **Design**: Designing system components (includes Units Planning, Units Generation, per-unit design)
- **Functional Design**: Technology-agnostic business logic design (per-unit)
- **NFR Requirements**: Determining NFRs and selecting tech stack (per-unit)
- **NFR Design**: Incorporating NFR patterns and logical components (per-unit)
- **Infrastructure Design**: Mapping to actual infrastructure services (per-unit)

### Living Artifacts
- **Product Backlog**: Continuously updated artifact tracking all work items, priorities, and status
- **Backlog Init**: Initialization during Workflow Planning, then updated at every approval gate

## Application Design Terms

- **Component**: A functional unit with specific responsibilities
- **Method**: A function or operation within a component with defined business rules
- **Business Rule**: Logic that governs method behavior and validation
- **Service**: Orchestration layer that coordinates business logic across components
- **Component Dependency**: Relationship and communication pattern between components

## Architecture Terms (Infrastructure)

### Unit of Work
A logical grouping of user stories for development purposes. The term used during planning and decomposition.

**Usage**: "We need to decompose the system into units of work"

### Service
An independently deployable component in a microservices architecture. Each service is a separate unit of work.

**Usage**: "The Payment Service handles all payment processing"

### Module
A logical grouping of functionality within a single service or monolith. Modules are not independently deployable.

**Usage**: "The authentication module within the User Service"

### Component
A reusable building block within a service or module. Components are classes, functions, or packages that provide specific functionality.

**Usage**: "The EmailValidator component validates email addresses"

## Terminology Guidelines

### When to Use Each Term

**Unit of Work**:
- During Units Planning and Units Generation phases
- When discussing system decomposition
- In planning documents and discussions
- Example: "How should we decompose this into units of work?"

**Service**:
- When referring to independently deployable components
- In microservices architecture contexts
- In deployment and infrastructure discussions
- Example: "The Order Service will be deployed to ECS"

**Module**:
- When referring to logical groupings within a service
- In monolith architecture contexts
- When discussing internal organization
- Example: "The reporting module generates all reports"

**Component**:
- When referring to specific classes, functions, or packages
- In design and implementation discussions
- When discussing reusable building blocks
- Example: "The DatabaseConnection component manages connections"

## Stage Terminology

### Planning vs Generation
- **Planning**: Creating a plan with questions and checkboxes for execution
- **Generation**: Executing the plan to create artifacts

Examples:
- Story Planning → Story Generation
- Units Planning → Units Generation
- Unit Design Planning → Unit Design Generation
- NFR Planning → NFR Generation
- Code Planning → Code Generation

### Depth Levels
- **Minimal**: Quick, focused execution for simple changes
- **Standard**: Normal depth with standard artifacts for typical projects
- **Comprehensive**: Full depth with all artifacts for complex/high-risk projects

## Artifact Types

### Plans
Documents with checkboxes and questions that guide execution.
- Located in `aidlc-docs/plans/`
- Examples: `story-generation-plan.md`, `unit-of-work-plan.md`

### Artifacts
Generated outputs from executing plans.
- Located in various `aidlc-docs/` subdirectories
- Examples: `requirements.md`, `stories.md`, `design.md`

### State Files
Files tracking workflow progress and status.
- `aidlc-state.md`: Overall workflow state
- `audit.md`: Complete audit trail of all interactions

## Agile-Specific Terminology

### Vision Stage
The optional stage that captures strategic intent and stakeholder alignment for complex projects. Produces `vision-statement.md` and `stakeholder-map.md`.

**Execute IF**: Complex project, multiple stakeholders, strategic initiative, new product development
**Skip IF**: Bug fix, single developer, clear scope, short duration

### Epic
A large body of work that can be broken down into user stories. Epics group related stories for better organization and release planning.

**Usage**: "The Authentication Epic contains 8 user stories"

### Product Backlog
A living artifact that contains all work items (epics, stories, tasks) with priorities and status. Initialized during Workflow Planning and updated at every approval gate.

**Key Characteristics**:
- Living: Continuously updated throughout the workflow
- Prioritized: Items ordered by value/effort
- Visible: Single source of truth for all work

### Living Artifact
An artifact that is not created once and forgotten, but continuously updated throughout the workflow lifecycle. The Product Backlog is the primary living artifact in AI-DLC Agile.

**Contrast with**: Static artifacts like requirements.md that are created once and only modified on request

### Stakeholder Map
A document identifying all project stakeholders, their interests, influence, and engagement strategies. Created during Vision Stage.

### Epic-Story Map
A mapping document showing which user stories belong to which epics, along with dependencies between epics.

### Jira MCP
Model Context Protocol integration with Jira for syncing AI-DLC artifacts with Jira projects. Optional feature that gracefully degrades if unavailable.

**Key Principle**: Check MCP -> Log -> Continue (never blocks workflow)

### Approval Gate
A checkpoint in the workflow where user approval is required before proceeding. At each approval gate:
1. Artifacts are presented for review
2. User can request changes or approve
3. Product Backlog is updated (if applicable)
4. Jira sync occurs (if available)

## Common Abbreviations

- **AI-DLC**: AI-Driven Development Life Cycle
- **NFR**: Non-Functional Requirements
- **UOW**: Unit of Work
- **API**: Application Programming Interface
- **CDK**: Cloud Development Kit (AWS)
- **MCP**: Model Context Protocol (for integrations like Jira)
