# Backlog Management - Living Artifact

**Purpose**: Maintain a living product backlog that tracks all work items, priorities, and release planning across the AI-DLC workflow.

**Type**: LIVING ARTIFACT - Initialized during Workflow Planning, updated at every approval gate

---

## Living Artifact Principle

Unlike sequential stages, the Product Backlog is a **cross-cutting concern**:

1. **Initialized**: During Workflow Planning stage
2. **Updated**: At every approval gate throughout the lifecycle
3. **Never Closed**: Remains active until project completion
4. **Always Current**: Reflects latest priorities and status

```
Workflow Planning     Approval Gates      Completion
      |                   |   |   |           |
      v                   v   v   v           v
  [Initialize] ----> [Update] [Update] ---> [Archive]
      |                   |   |   |           |
      +-------------------+---+---+-----------+
                    LIVING BACKLOG
```

---

## Backlog Initialization

### When: During Workflow Planning Stage

After execution plan is created, initialize the backlog:

### Step 1: Create Backlog Directory

```
aidlc-docs/inception/backlog/
+-- product-backlog.md       # Main backlog artifact
+-- release-plan.md          # Release/sprint planning
+-- backlog-history.md       # Change history log
```

### Step 2: Generate Initial Product Backlog

Create `aidlc-docs/inception/backlog/product-backlog.md`:

```markdown
# Product Backlog

## Backlog Metadata
- **Created**: [ISO timestamp]
- **Last Updated**: [ISO timestamp]
- **Total Items**: [Count]
- **Prioritization Method**: [MoSCoW/Value-Effort/Custom]

## Priority Legend
- **P1 - Must Have**: Critical for release, non-negotiable
- **P2 - Should Have**: Important, expected in release
- **P3 - Could Have**: Desirable, include if time permits
- **P4 - Won't Have**: Out of scope for current release

## Status Legend
- **New**: Not yet started
- **Ready**: Refined and ready for development
- **In Progress**: Currently being developed
- **Review**: In review or testing
- **Done**: Completed and accepted
- **Blocked**: Waiting on dependency

---

## Backlog Items

### P1 - Must Have

| ID | Type | Title | Epic | Status | Story Points |
|----|------|-------|------|--------|--------------|
| [ID] | [Story/Task/Bug] | [Title] | [Epic Name] | [Status] | [Points] |

### P2 - Should Have

| ID | Type | Title | Epic | Status | Story Points |
|----|------|-------|------|--------|--------------|

### P3 - Could Have

| ID | Type | Title | Epic | Status | Story Points |
|----|------|-------|------|--------|--------------|

### P4 - Won't Have (This Release)

| ID | Type | Title | Epic | Reason |
|----|------|-------|------|--------|

---

## Backlog Summary

### By Status
- **New**: [Count]
- **Ready**: [Count]
- **In Progress**: [Count]
- **Review**: [Count]
- **Done**: [Count]
- **Blocked**: [Count]

### By Epic
| Epic | Total | Done | Remaining |
|------|-------|------|-----------|

### By Priority
| Priority | Total | Done | Remaining |
|----------|-------|------|-----------|
```

### Step 3: Generate Release Plan

Create `aidlc-docs/inception/backlog/release-plan.md`:

```markdown
# Release Plan

## Release Overview
- **Release Name**: [Name/Version]
- **Target Date**: [Date if known]
- **Release Goal**: [Brief statement]

## Release Scope

### Included Epics
| Epic | Stories | Points | Priority |
|------|---------|--------|----------|

### Excluded from Release
| Item | Reason | Target Release |
|------|--------|----------------|

---

## Iteration/Sprint Plan (if applicable)

### Iteration 1
- **Goal**: [Sprint goal]
- **Capacity**: [Story points or items]
- **Items**:
  - [ ] [Item ID]: [Title]
  - [ ] [Item ID]: [Title]

### Iteration 2
- **Goal**: [Sprint goal]
- **Capacity**: [Story points or items]
- **Items**:
  - [ ] [Item ID]: [Title]

---

## Dependencies

### External Dependencies
| Dependency | Owner | Status | Impact |
|------------|-------|--------|--------|

### Internal Dependencies
| Blocked Item | Blocked By | Expected Resolution |
|--------------|------------|---------------------|

---

## Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
```

---

## Backlog Updates at Approval Gates

### When to Update

The backlog MUST be updated at these approval gates:

1. **Vision Stage Approval**: Add vision-level items, create parent backlog structure
2. **Epic Stage Approval**: Add epics to backlog, establish epic hierarchy
3. **User Stories Approval**: Add all stories to backlog with initial priorities
4. **Workflow Planning Approval**: Finalize initial backlog state
5. **Application Design Approval**: Add technical tasks if identified
6. **Unit Completion**: Mark related items as done
7. **Phase Completion**: Archive completed items, update release status

### Update Process

#### Step 1: Load Current Backlog
- Read `product-backlog.md`
- Read `release-plan.md`

#### Step 2: Apply Updates
Based on the approval gate:

**After Vision Approval**:
- Add vision goals as high-level backlog themes
- Create placeholder for epics

**After Epic Approval**:
- Add each epic as a backlog item (type: Epic)
- Link epics to vision themes
- Set initial epic priorities

**After Stories Approval**:
- Add all stories to backlog
- Link stories to parent epics
- Set story priorities based on epic priority
- Add acceptance criteria reference

**After Unit Work Completion**:
- Mark related stories as Done
- Update epic progress
- Adjust remaining items if scope changed

#### Step 3: Record History

Append to `aidlc-docs/inception/backlog/backlog-history.md`:

```markdown
## [ISO timestamp] - [Trigger Event]

### Changes Made
- **Items Added**: [List]
- **Items Updated**: [List with before/after]
- **Items Removed**: [List with reason]

### Backlog State
- **Total Items**: [Count]
- **Done**: [Count]
- **Remaining**: [Count]

### Context
[Brief description of why changes were made]
```

#### Step 4: Sync with Jira (if available)

If Jira MCP is available:
- Sync new items to Jira
- Update existing Jira items
- Log sync in `jira-sync-log.md`

---

## Backlog Refinement

### Refinement Activities

These can be triggered by user request or during workflow:

1. **Prioritization**: Reorder items based on value/effort
2. **Estimation**: Add or update story points
3. **Decomposition**: Break large items into smaller ones
4. **Clarification**: Add detail to item descriptions
5. **Grooming**: Remove obsolete or duplicate items

### Refinement Questions Template

When refinement is needed, create `backlog-refinement-questions.md`:

```markdown
# Backlog Refinement Questions

## Items Requiring Attention

### [Item ID]: [Title]

**Current State**:
- Priority: [Current]
- Story Points: [Current or unestimated]
- Status: [Current]

**Questions**:

**Q1: Priority Assessment**
Is the current priority ([Current]) still accurate?
- A) Yes, keep current priority
- B) Increase priority to [Higher]
- C) Decrease priority to [Lower]
- D) Other: [Specify]
[Answer]:

**Q2: Estimation** (if unestimated)
What is the relative size of this item?
- A) Small (1-2 points)
- B) Medium (3-5 points)
- C) Large (8-13 points)
- D) Too large, needs decomposition
[Answer]:

**Q3: Readiness**
Is this item ready for development?
- A) Yes, all details are clear
- B) No, needs [specific clarification]
- C) Blocked by [dependency]
[Answer]:
```

---

## Backlog Metrics

### Velocity Tracking (if applicable)

Track velocity in `product-backlog.md`:

```markdown
## Velocity History

| Iteration | Committed | Completed | Velocity |
|-----------|-----------|-----------|----------|
| 1         | [Points]  | [Points]  | [Points] |
| 2         | [Points]  | [Points]  | [Points] |

**Average Velocity**: [Points per iteration]
**Remaining Work**: [Total remaining points]
**Estimated Iterations**: [Calculated]
```

### Burndown/Burnup Data

```markdown
## Progress Tracking

| Date | Total | Done | Remaining | Added |
|------|-------|------|-----------|-------|
```

---

## Commands

### Available Backlog Commands

| Command | Description |
|---------|-------------|
| `/aidlc-agile backlog status` | Show backlog summary |
| `/aidlc-agile backlog refine` | Start refinement session |
| `/aidlc-agile backlog prioritize` | Re-prioritize items |
| `/aidlc-agile backlog add [item]` | Add new backlog item |
| `/aidlc-agile backlog update [id]` | Update specific item |
| `/aidlc-agile release plan` | Show/update release plan |

---

## Critical Rules

1. **ALWAYS INITIALIZE**: Backlog must be created during Workflow Planning
2. **ALWAYS UPDATE**: Every approval gate triggers backlog update
3. **NEVER SKIP**: Even minimal projects maintain a simple backlog
4. **HISTORY PRESERVED**: All changes logged in backlog-history.md
5. **SINGLE SOURCE**: product-backlog.md is the authoritative backlog
6. **SYNC OPTIONAL**: Jira sync enhances but doesn't replace local backlog
