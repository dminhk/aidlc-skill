# AI-DLC (AI-Driven Development Life Cycle)

A Claude Code skill that provides a structured, adaptive workflow for AI-assisted software development.

> **Based on**: [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) by AWS Labs

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

## Installation

### Option 1: Plugin Marketplace (Recommended)

Add the marketplace and install in Claude Code:

```
/plugin marketplace add https://github.com/dminhk/aidlc-skill.git
/plugin install aidlc@aidlc-skill
```

Restart Claude Code after installation to load the skill.

### Option 2: Clone Repository

```bash
# Clone the repository
git clone https://github.com/dminhk/aidlc-skill.git

# Copy to global skills directory (available for all projects)
cp -r aidlc-skill/aidlc ~/.claude/skills/

# Or copy to project-specific location (shared via version control)
cp -r aidlc-skill/aidlc .claude/skills/
```

### Option 3: Download Release

1. Download `aidlc.skill` from the [Releases](https://github.com/dminhk/aidlc-skill/releases) page
2. Extract to your skills directory:
   ```bash
   unzip aidlc.skill -d ~/.claude/skills/
   ```

### Verify Installation

Ask Claude Code:
```
What skills are available?
```

You should see "aidlc" listed with its description.

## Usage

Once installed, simply describe what you want to build:

```
"Build a REST API for user management"
"Create a React dashboard with authentication"
"Add a payment processing feature to my app"
```

The skill will automatically:
1. Detect your workspace (new or existing project)
2. Gather requirements through structured questions
3. Plan the implementation workflow
4. Guide you through design and code generation
5. Produce build and test instructions

## Explicit Stage Commands

You can explicitly trigger specific stages to re-run phases, force skipped stages, or generate missing documentation.

### Basic Commands

| Command | Description |
|---------|-------------|
| `/aidlc` | Start or resume workflow |
| `/aidlc continue` | Resume from current state |
| `/aidlc status` | Show current progress |

### Phase Commands

Run or re-run entire phases:

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

Generate missing or additional documentation:

```
/aidlc generate missing documentation
/aidlc create construction docs
/aidlc create build-and-test summary
```

### Control Commands

Fine-tune workflow execution:

| Command | Description |
|---------|-------------|
| `/aidlc skip [stage name]` | Skip a specific stage |
| `/aidlc include [stage name]` | Force include a stage |
| `/aidlc reset [phase]` | Reset phase status in state file |

## Generated Documentation Structure

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

## Key Principles

1. **Adaptive Execution** - Only runs stages that add value
2. **Transparent Planning** - Shows execution plan before starting
3. **User Control** - You can include/exclude stages
4. **Progress Tracking** - Resumes where you left off
5. **Complete Audit Trail** - Logs all inputs and decisions

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI

## License

This project is licensed under the **MIT-0 License** - See [LICENSE](LICENSE) for details.

This skill is based on [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) by AWS Labs, also licensed under MIT-0.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

If you encounter issues or have questions:
- Open an [Issue](https://github.com/dminhk/aidlc-skill/issues)
- Check existing discussions for solutions
