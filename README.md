# AI-DLC (AI-Driven Development Life Cycle)

A structured, adaptive workflow for AI-assisted software development.

> **Based on**: [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) by AWS Labs

## Supported Platforms

| Platform | Type | Installation |
|----------|------|--------------|
| [Claude Code](https://claude.ai/claude-code) | CLI | Skill (`/aidlc`) |
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

```
/plugin marketplace add https://github.com/dminhk/aidlc-skill.git
/plugin install aidlc@aidlc-skill
```

Restart Claude Code after installation to load the skill.

#### Option 2: Clone Repository

```bash
git clone https://github.com/dminhk/aidlc-skill.git

# Global installation (all projects)
cp -r aidlc-skill/aidlc ~/.claude/skills/

# Or project-specific (shared via version control)
cp -r aidlc-skill/aidlc .claude/skills/
```

#### Verify Installation

```
What skills are available?
```

You should see "aidlc" listed with its description.

---

### Kiro IDE / Kiro CLI

#### Option 1: Clone Repository

```bash
git clone https://github.com/dminhk/aidlc-skill.git

# Project-specific installation
cp -r aidlc-skill/kiro/aidlc-rules <your-project>/.kiro/steering/
cp -r aidlc-skill/kiro/aidlc-rule-details <your-project>/.kiro/

# Or global installation (all projects)
cp -r aidlc-skill/kiro/aidlc-rules ~/.kiro/steering/
cp -r aidlc-skill/kiro/aidlc-rule-details ~/.kiro/
```

#### Resulting Structure

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

#### Verify Installation

In Kiro CLI:

```
/context show
```

Look for entries under `.kiro/steering/aidlc-rules/`.

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
| Reverse Engineering | Brownfield only | Document existing codebase |
| Requirements Analysis | Always | Gather and clarify requirements |
| User Stories | Conditional | Define user-facing features |
| Workflow Planning | Always | Plan which stages to execute |
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
