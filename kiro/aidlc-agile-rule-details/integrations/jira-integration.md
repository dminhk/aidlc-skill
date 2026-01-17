# Jira MCP Integration

**Purpose**: Provide optional Jira integration for syncing AI-DLC artifacts with Jira projects via MCP (Model Context Protocol).

**Type**: OPTIONAL - Never blocks workflow execution

---

## Integration Principle

**Check MCP -> Log -> Continue**

The Jira integration follows a non-blocking pattern:
1. Check if Jira MCP server is available
2. If available, sync artifacts
3. If unavailable, log and continue without interruption
4. Never fail or block workflow due to Jira connectivity issues

---

## MCP Server Detection

### Step 1: Check for Jira MCP Availability

At workflow start, check for Jira MCP server:

```markdown
## Jira MCP Detection

**Check**: Look for Jira MCP server in available tools
**Result**: [Available/Unavailable]
**Action**: [Will sync/Will skip Jira sync]
```

### Step 2: Log Detection Result

Create or update `aidlc-docs/integrations/jira-config.md`:

```markdown
# Jira Integration Configuration

## MCP Status
- **Detection Time**: [ISO timestamp]
- **Status**: [Available/Unavailable]
- **Server**: [MCP server name if available]

## Project Configuration
- **Jira Project Key**: [Key if configured]
- **Board Type**: [Scrum/Kanban if applicable]
- **Sync Enabled**: [Yes/No]

## Capabilities Detected
- [ ] Create Issues
- [ ] Update Issues
- [ ] Create Epics
- [ ] Link Issues
- [ ] Transition Status
- [ ] Add Comments
```

---

## Graceful Degradation

### When Jira MCP is UNAVAILABLE

1. **Log the Status**: Record in sync log
2. **Continue Workflow**: Proceed without Jira sync
3. **Local Artifacts**: All artifacts created locally in `aidlc-docs/`
4. **Manual Sync Option**: User can manually export later

### Degradation Message Template

```markdown
## Jira Integration Status

**Status**: Jira MCP not available

**Impact**:
- All AI-DLC artifacts will be created locally
- No automatic Jira synchronization
- Stories, epics, and backlog managed in markdown files

**To Enable Jira Integration**:
1. Configure Jira MCP server in your MCP settings
2. Restart the AI-DLC workflow
3. Integration will be detected automatically

**Manual Export Available**: Run `/aidlc-agile export to jira` when Jira is configured
```

---

## Sync Patterns

### Vision Stage Sync

**When**: After Vision Stage completion and approval

**Creates in Jira**:
- Parent Epic representing the vision
- Links to stakeholder documentation (as attachments or wiki links)

**Sync Mapping**:
| AI-DLC Artifact | Jira Entity |
|-----------------|-------------|
| `vision-statement.md` | Epic Description |
| `stakeholder-map.md` | Epic Attachment |
| Vision goals | Epic labels |

### Epic Stage Sync

**When**: After Epic Stage completion and approval

**Creates in Jira**:
- Epic issues for each defined epic
- Links between epics (if dependency exists)

**Sync Mapping**:
| AI-DLC Artifact | Jira Entity |
|-----------------|-------------|
| `epics.md` entries | Epic Issues |
| `epic-dependency.md` | Epic Links (blocks/blocked by) |
| Epic descriptions | Epic Description field |

### User Story Sync

**When**: After User Stories completion and approval

**Creates in Jira**:
- Story issues for each user story
- Links stories to parent epics
- Acceptance criteria as subtasks or checklist

**Sync Mapping**:
| AI-DLC Artifact | Jira Entity |
|-----------------|-------------|
| `stories.md` entries | Story Issues |
| Acceptance criteria | Story subtasks or checklist |
| `epic-story-map.md` | Epic-Story links |
| Story points (if defined) | Story Points field |

### Backlog Sync

**When**: At every approval gate (if backlog changed)

**Updates in Jira**:
- Backlog ranking/priority
- Story status transitions
- Sprint assignments (if applicable)

**Sync Mapping**:
| AI-DLC Artifact | Jira Action |
|-----------------|-------------|
| `product-backlog.md` priority | Issue rank |
| `release-plan.md` assignments | Fix Version |
| Item status changes | Issue transitions |

---

## Sync Log

Maintain sync history in `aidlc-docs/integrations/jira-sync-log.md`:

```markdown
# Jira Sync Log

## Sync History

### [ISO timestamp] - Vision Stage Sync
- **Status**: [Success/Failed/Skipped]
- **Items Created**: [List of Jira issue keys]
- **Items Updated**: [List of updated items]
- **Errors**: [Any errors encountered]

### [ISO timestamp] - Epic Stage Sync
- **Status**: [Success/Failed/Skipped]
- **Epics Created**: [List of epic keys]
- **Links Created**: [List of link types]
- **Errors**: [Any errors encountered]

### [ISO timestamp] - Story Sync
- **Status**: [Success/Failed/Skipped]
- **Stories Created**: [Count and keys]
- **Stories Linked**: [Count]
- **Errors**: [Any errors encountered]

### [ISO timestamp] - Backlog Update
- **Status**: [Success/Failed/Skipped]
- **Items Reordered**: [Count]
- **Status Transitions**: [Count]
- **Errors**: [Any errors encountered]
```

---

## Error Handling

### Transient Errors (Retry)
- Network timeout
- Rate limiting
- Server unavailable

**Action**: Log error, retry once, continue if still failing

### Permanent Errors (Skip)
- Authentication failure
- Project not found
- Permission denied

**Action**: Log error, disable sync for session, continue workflow

### Conflict Errors (Manual)
- Issue already exists with different data
- Version conflict

**Action**: Log conflict, flag for manual resolution, continue workflow

---

## Configuration Options

### User-Configurable Settings

These can be specified in initial questions or configuration:

```markdown
## Jira Configuration Questions

**Q1: Jira Project Key**
What is your Jira project key?
[Answer]:

**Q2: Default Issue Type for Stories**
What issue type should be used for user stories?
- A) Story
- B) Task
- C) User Story (custom)
- D) Other: [specify]
[Answer]:

**Q3: Epic Link Field**
How are epics linked in your Jira instance?
- A) Epic Link field (classic)
- B) Parent field (next-gen)
- C) Custom field: [specify]
[Answer]:

**Q4: Sync Frequency**
When should Jira sync occur?
- A) After each stage approval
- B) Only at phase completion
- C) Manual only
[Answer]:
```

---

## Commands

### Available Jira Commands

| Command | Description |
|---------|-------------|
| `/aidlc-agile sync jira` | Force sync all artifacts to Jira |
| `/aidlc-agile jira status` | Show Jira connection status |
| `/aidlc-agile export to jira` | Export local artifacts to Jira |
| `/aidlc-agile import from jira` | Import existing Jira items |

---

## Critical Rules

1. **NEVER BLOCK**: Jira issues never stop AI-DLC workflow
2. **ALWAYS LOG**: All sync attempts recorded in sync log
3. **LOCAL FIRST**: Artifacts always created locally, then synced
4. **IDEMPOTENT**: Re-running sync doesn't create duplicates
5. **GRACEFUL**: Missing Jira = continue with local artifacts only
