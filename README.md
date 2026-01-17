# AI-DLC (AI-Driven Development Life Cycle)

A structured, adaptive workflow for AI-assisted software development.

> **Based on**: [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) by AWS Labs

## Skill Variants

| Skill | Description | Use When |
|-------|-------------|----------|
| **aidlc** | Base workflow | General software development tasks |
| **aidlc-agile** | Agile variant with Vision, Epic, Backlog, Jira | Multi-stakeholder projects, agile practices |

## Supported Platforms

| Platform | Type | Installation |
|----------|------|--------------|
| [Claude Code](https://claude.ai/claude-code) | CLI | Skill (`/aidlc` or `/aidlc-agile`) |
| [Kiro IDE](https://kiro.dev) | IDE | Steering files |
| [Kiro CLI](https://kiro.dev/docs/cli) | CLI | Steering files |

## Overview

AI-DLC guides you through a complete software development lifecycle with three phases:

```
┌─────────────────────────────────────────────────────────────┐
│                      INCEPTION                              │
│                  Planning & Architecture                    │
├─────────────────────────────────────────────────────────────┤
│  Workspace Detection → Requirements → User Stories →        │
│  Workflow Planning → Application Design → Units Generation  │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                     CONSTRUCTION                            │
│               Design, Implementation & Test                 │
├─────────────────────────────────────────────────────────────┤
│  Per-Unit: Functional Design → NFR Requirements →           │
│  NFR Design → Infrastructure Design → Code Generation       │
│  Then: Build and Test                                       │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                      OPERATIONS                             │
│                 (Future: Deployment)                        │
└─────────────────────────────────────────────────────────────┘
```

## Features

- **Adaptive Workflow**: Automatically adjusts depth based on project complexity
- **Greenfield & Brownfield Support**: Works with new projects or existing codebases
- **Comprehensive Documentation**: Generates requirements, designs, and audit trails
- **Progress Tracking**: Maintains state across sessions with `aidlc-state.md`
- **Quality Focused**: Includes NFR (non-functional requirements) analysis
- **Full Audit Trail**: Logs all decisions and user inputs

---

## Installation

### Claude Code

#### Option 1: Plugin Marketplace (Recommended)

**Base workflow:**
```
/plugin marketplace add https://github.com/dminhk/aidlc-skill.git
/plugin install aidlc@aidlc-skill
```

**Agile variant (includes Vision, Epic, Backlog, Jira integration):**
```
/plugin marketplace add https://github.com/dminhk/aidlc-skill.git
/plugin install aidlc-agile@aidlc-skill
```

Restart Claude Code after installation to load the skill.

#### Option 2: Clone Repository

```bash
git clone https://github.com/dminhk/aidlc-skill.git

# Global installation (all projects)
cp -r aidlc-skill/aidlc ~/.claude/skills/
cp -r aidlc-skill/aidlc-agile ~/.claude/skills/  # Optional: Agile variant

# Or project-specific (shared via version control)
cp -r aidlc-skill/aidlc .claude/skills/
cp -r aidlc-skill/aidlc-agile .claude/skills/  # Optional: Agile variant
```

#### Verify Installation

```
What skills are available?
```

You should see "aidlc" and/or "aidlc-agile" listed with their descriptions.

#### Plugin Configuration

The `.claude-plugin/marketplace.json` file defines the available plugins:

```json
{
  "name": "aidlc-skill",
  "plugins": [
    {
      "name": "aidlc",
      "skills": ["./aidlc"]
    },
    {
      "name": "aidlc-agile",
      "skills": ["./aidlc-agile"]
    }
  ]
}
```

Each plugin maps to a skill directory containing a `SKILL.md` that defines the skill's name, description, and workflow rules.

---

### Kiro IDE / Kiro CLI

#### Option 1: Clone Repository

**Base workflow:**
```bash
git clone https://github.com/dminhk/aidlc-skill.git

# Project-specific installation
cp -r aidlc-skill/kiro/aidlc-rules <your-project>/.kiro/steering/
cp -r aidlc-skill/kiro/aidlc-rule-details <your-project>/.kiro/

# Or global installation (all projects)
cp -r aidlc-skill/kiro/aidlc-rules ~/.kiro/steering/
cp -r aidlc-skill/kiro/aidlc-rule-details ~/.kiro/
```

**Agile variant (includes Vision, Epic, Backlog, Jira integration):**
```bash
git clone https://github.com/dminhk/aidlc-skill.git

# Project-specific installation
cp -r aidlc-skill/kiro/aidlc-agile-rules <your-project>/.kiro/steering/
cp -r aidlc-skill/kiro/aidlc-agile-rule-details <your-project>/.kiro/

# Or global installation (all projects)
cp -r aidlc-skill/kiro/aidlc-agile-rules ~/.kiro/steering/
cp -r aidlc-skill/kiro/aidlc-agile-rule-details ~/.kiro/
```

#### Resulting Structure

**Base workflow:**
```
<your-project>/
└── .kiro/
    ├── steering/
    │   └── aidlc-rules/
    │       └── core-workflow.md
    └── aidlc-rule-details/
        ├── common/
        ├── inception/
        ├── construction/
        └── operations/
```

**Agile variant:**
```
<your-project>/
└── .kiro/
    ├── steering/
    │   └── aidlc-agile-rules/
    │       └── core-workflow.md
    └── aidlc-agile-rule-details/
        ├── common/
        ├── inception/
        │   ├── vision-stage.md
        │   ├── epic-stage.md
        │   └── backlog-management.md
        ├── integrations/
        │   └── jira-integration.md
        ├── construction/
        └── operations/
```

#### Verify Installation

In Kiro CLI:

```
/context show
```

Look for entries under `.kiro/steering/aidlc-rules/` or `.kiro/steering/aidlc-agile-rules/`.

---

## Usage

### Claude Code

Simply describe what you want to build:

```
"Build a REST API for user management"
"Create a React dashboard with authentication"
"Add a payment processing feature to my app"
```

Or use the explicit command:

```
/aidlc
```

For agile workflows with Vision, Epic, and Backlog management:

```
/aidlc-agile
```

### Kiro IDE / Kiro CLI

Start your prompt with **"Using AI-DLC, ..."**:

```
Using AI-DLC, build a REST API for user management
Using AI-DLC, create a React dashboard with authentication
Using AI-DLC, add a payment processing feature to my app
```

---

## How It Works

The workflow will automatically:
1. Detect your workspace (new or existing project)
2. Gather requirements through structured questions
3. Plan the implementation workflow
4. Guide you through design and code generation
5. Produce build and test instructions

---

## Commands (Claude Code)

### Basic Commands

| Command | Description |
|---------|-------------|
| `/aidlc` | Start or resume workflow |
| `/aidlc continue` | Resume from current state |
| `/aidlc status` | Show current progress |

### Phase Commands

```
/aidlc run inception              # Run/re-run inception phase
/aidlc run construction           # Run/re-run construction phase
/aidlc run construction with full documentation  # Force all docs
```

### Individual Stage Commands

**Inception Phase:**

```
/aidlc run workspace detection
/aidlc run reverse engineering
/aidlc run requirements analysis
/aidlc run user stories
/aidlc run workflow planning
/aidlc run application design
/aidlc run units generation
```

**Construction Phase:**

```
/aidlc run functional design [for unit X]
/aidlc run nfr requirements [for unit X]
/aidlc run nfr design [for unit X]
/aidlc run infrastructure design [for unit X]
/aidlc run code generation [for unit X]
/aidlc run build and test
```

### Documentation Commands

```
/aidlc generate missing documentation
/aidlc create construction docs
/aidlc create build-and-test summary
```

### Control Commands

| Command | Description |
|---------|-------------|
| `/aidlc skip [stage name]` | Skip a specific stage |
| `/aidlc include [stage name]` | Force include a stage |
| `/aidlc reset [phase]` | Reset phase status in state file |

---

## Commands (Claude Code - Agile Variant)

### Basic Commands

| Command | Description |
|---------|-------------|
| `/aidlc-agile` | Start or resume agile workflow |
| `/aidlc-agile continue` | Resume from current state |
| `/aidlc-agile status` | Show current progress |

### Agile-Specific Stage Commands

```
/aidlc-agile run vision stage
/aidlc-agile run epic stage
/aidlc-agile backlog status
/aidlc-agile backlog refine
/aidlc-agile sync jira
```

### Jira Integration Commands

| Command | Description |
|---------|-------------|
| `/aidlc-agile sync jira` | Force sync all artifacts to Jira |
| `/aidlc-agile jira status` | Show Jira connection status |
| `/aidlc-agile export to jira` | Export local artifacts to Jira |

---

## Generated Documentation Structure

Both Claude Code and Kiro generate the same documentation structure:

```
your-project/
├── [your application code]
│
└── aidlc-docs/
    ├── aidlc-state.md              # Progress tracking
    ├── audit.md                     # Complete audit trail
    ├── inception/
    │   ├── plans/
    │   ├── reverse-engineering/     # (brownfield only)
    │   ├── requirements/
    │   ├── user-stories/
    │   └── application-design/
    ├── construction/
    │   ├── plans/
    │   ├── {unit-name}/
    │   │   ├── functional-design/
    │   │   ├── nfr-requirements/
    │   │   ├── nfr-design/
    │   │   └── infrastructure-design/
    │   └── build-and-test/
    └── operations/
```

---

## Workflow Stages

### Inception Phase

| Stage | When Executed | Purpose |
|-------|---------------|---------|
| Workspace Detection | Always | Detect greenfield/brownfield, resume state |
| Vision Stage | Conditional (Agile) | Strategic intent and stakeholder alignment |
| Reverse Engineering | Brownfield only | Document existing codebase |
| Requirements Analysis | Always | Gather and clarify requirements |
| User Stories | Conditional | Define user-facing features |
| Epic Stage | Conditional (Agile) | Group stories into epics |
| Workflow Planning | Always | Plan which stages to execute |
| Backlog Init | Living (Agile) | Initialize product backlog |
| Application Design | Conditional | Define components and services |
| Units Generation | Conditional | Decompose into work units |

### Construction Phase

| Stage | When Executed | Purpose |
|-------|---------------|---------|
| Functional Design | Conditional | Business logic and domain models |
| NFR Requirements | Conditional | Performance, security, scalability |
| NFR Design | Conditional | Technical patterns for NFRs |
| Infrastructure Design | Conditional | Deployment architecture |
| Code Generation | Always | Generate application code |
| Build and Test | Always | Build instructions and tests |

### Agile-Specific Features (aidlc-agile only)

| Feature | Type | Purpose |
|---------|------|---------|
| Vision Stage | Conditional | Capture strategic intent for complex projects |
| Epic Stage | Conditional | Group 5+ stories into logical epics |
| Product Backlog | Living Artifact | Track all work items, updated at every gate |
| Jira Integration | Optional | Sync with Jira via MCP (graceful degradation) |

---

## Key Principles

1. **Adaptive Execution** - Only runs stages that add value
2. **Transparent Planning** - Shows execution plan before starting
3. **User Control** - You can include/exclude stages
4. **Progress Tracking** - Resumes where you left off
5. **Complete Audit Trail** - Logs all inputs and decisions

---

## License

This project is licensed under the **MIT-0 License** - See [LICENSE](LICENSE) for details.

This skill is based on [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) by AWS Labs, also licensed under MIT-0.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

If you encounter issues or have questions:
- Open an [Issue](https://github.com/dminhk/aidlc-skill/issues)
- Check existing discussions for solutions
