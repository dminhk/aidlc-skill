# AI-DLC Agile Skill: Vision, Epic, Backlog & Jira Integration

> **Status**: Planned (not yet implemented)
> **Created**: 2026-01-16

## Summary

Create a **new skill variant** called `aidlc-agile` that extends the original `aidlc` workflow with:
1. **Vision Stage** - Strategic intent capture (CONDITIONAL)
2. **Epic Stage** - Story grouping (CONDITIONAL)
3. **Backlog Management** - Living prioritized artifact
4. **Jira MCP Integration** - Real-time sync (optional)

The original `aidlc` skill remains unchanged.

---

## Directory Structure

```
aidlc-skill/
├── aidlc/                    # UNCHANGED - Original workflow
│   ├── SKILL.md
│   └── references/
│
├── aidlc-agile/              # NEW - Extended workflow
│   ├── SKILL.md              # Updated workflow with new stages
│   └── references/
│       ├── common/           # Copy + updates
│       ├── inception/        # Copy + new stage files
│       ├── construction/     # Copy
│       └── integrations/     # NEW folder
│
└── README.md                 # Updated to document both variants
```

---

## aidlc-agile Workflow

```
INCEPTION PHASE
├── Workspace Detection (ALWAYS)
├── Vision Stage (CONDITIONAL) ←── NEW
├── Reverse Engineering (CONDITIONAL - brownfield)
├── Requirements Analysis (ALWAYS)
├── User Stories (CONDITIONAL)
├── Epic Stage (CONDITIONAL) ←── NEW
├── Backlog Management (LIVING) ←── NEW
├── Workflow Planning (ALWAYS)
├── Application Design (CONDITIONAL)
└── Units Generation (CONDITIONAL)
```

---

## Jira Mapping

| AI-DLC | Jira | Trigger |
|--------|------|---------|
| Vision | Epic | Vision Stage completion |
| Epic | Epic | Epic Stage completion |
| User Story | Story | User Stories completion |
| Unit of Work | Task | Units Generation completion |

---

## Implementation Steps

### Step 1: Create aidlc-agile folder structure
```bash
cp -r aidlc aidlc-agile
mkdir -p aidlc-agile/references/integrations
```

### Step 2: Create new reference files in aidlc-agile

#### 2a. `/aidlc-agile/references/inception/vision-stage.md`
- Two-part stage (Planning + Generation)
- Execute IF: complex project, multiple stakeholders, strategic alignment needed
- Skip IF: simple feature, bug fix, single developer
- Artifacts: `vision-statement.md`, `stakeholder-map.md`
- Jira sync: Creates parent Epic

#### 2b. `/aidlc-agile/references/inception/epic-stage.md`
- Two-part stage (Planning + Generation)
- Execute IF: 5+ user stories, natural groupings exist
- Skip IF: <5 stories, linear implementation
- Artifacts: `epics.md`, `epic-dependency.md`, `epic-story-map.md`
- Jira sync: Creates Epics, links Stories

#### 2c. `/aidlc-agile/references/inception/backlog-management.md`
- Living artifact (continuously updated)
- Initialized during Workflow Planning
- Updated at every approval gate
- Artifacts: `product-backlog.md`, `release-plan.md`
- Jira sync: Bidirectional priority/status

#### 2d. `/aidlc-agile/references/integrations/jira-integration.md`
- MCP availability check pattern
- Graceful degradation when MCP unavailable
- Sync triggers: Stage completion, Approval gates
- Artifacts: `jira-config.md`, `jira-sync-log.md`

### Step 3: Modify files in aidlc-agile only

#### 3a. `/aidlc-agile/SKILL.md`
- Update skill name/description to "aidlc-agile"
- Update workflow ASCII diagram (add 3 new stages)
- Add Vision Stage section
- Add Epic Stage section
- Add Backlog Management section
- Update directory structure
- Add new reference files to list

#### 3b. `/aidlc-agile/references/common/process-overview.md`
- Update Mermaid diagram with new stages
- Add stage descriptions for Vision, Epic, Backlog

#### 3c. `/aidlc-agile/references/inception/workflow-planning.md`
- Add Vision Stage assessment criteria
- Add Epic Stage assessment criteria
- Add Backlog initialization step
- Update execution plan template with new stages
- Add artifact loading for new stages

#### 3d. `/aidlc-agile/references/common/terminology.md`
- Add definitions: Vision Stage, Epic, Epic Stage, Product Backlog, Release Plan, Living Artifact, Jira MCP Integration

#### 3e. `/aidlc-agile/references/common/session-continuity.md`
- Add context loading for: vision artifacts, epic artifacts, backlog, jira config

#### 3f. `/aidlc-agile/references/common/welcome-message.md`
- Update ASCII diagram with new stages
- Add Jira integration section

### Step 4: Update README.md
- Document both skill variants
- Add aidlc-agile installation instructions
- Add aidlc-agile specific commands
- Add Jira Integration documentation

---

## New Directory Structure (aidlc-agile docs)

```
aidlc-docs/
├── inception/
│   ├── vision/                    # NEW
│   │   ├── vision-statement.md
│   │   └── stakeholder-map.md
│   ├── epics/                     # NEW
│   │   ├── epics.md
│   │   ├── epic-dependency.md
│   │   └── epic-story-map.md
│   ├── backlog/                   # NEW
│   │   ├── product-backlog.md
│   │   └── release-plan.md
│   └── [existing folders...]
├── integrations/                  # NEW
│   ├── jira-config.md
│   └── jira-sync-log.md
└── [existing files...]
```

---

## New Commands (aidlc-agile)

```
/aidlc-agile                      # Start agile workflow
/aidlc-agile run vision stage
/aidlc-agile run epic stage
/aidlc-agile run backlog update
/aidlc-agile jira configure
/aidlc-agile jira sync
/aidlc-agile jira status
```

---

## Jira MCP Integration Pattern

```markdown
# Before any Jira operation:
1. Check if Jira MCP tools available
2. If not available:
   - Log in audit.md: "Jira MCP not available, sync skipped"
   - Continue workflow normally
   - Note in completion message
3. If available:
   - Execute sync operation
   - Log in jira-sync-log.md
   - Update jira-config.md with mappings
```

---

## Files Summary

### New Files to Create (in aidlc-agile/)
1. `references/inception/vision-stage.md`
2. `references/inception/epic-stage.md`
3. `references/inception/backlog-management.md`
4. `references/integrations/jira-integration.md`

### Files to Modify (in aidlc-agile/ only)
5. `SKILL.md`
6. `references/common/process-overview.md`
7. `references/inception/workflow-planning.md`
8. `references/common/terminology.md`
9. `references/common/session-continuity.md`
10. `references/common/welcome-message.md`

### Root Files to Update
11. `README.md` - Document both variants

---

## Verification

1. Verify original `aidlc/` folder is unchanged
2. Verify `aidlc-agile/` has all new stages
3. Read through modified files for consistency
4. Verify workflow diagram shows correct stage order
5. Verify new reference files follow existing patterns
6. Test: `/aidlc` still works with original workflow
7. Test: `/aidlc-agile` triggers new workflow
8. Test: complex project triggers Vision Stage
9. Test: 5+ stories triggers Epic Stage
10. Verify graceful handling when Jira MCP unavailable
