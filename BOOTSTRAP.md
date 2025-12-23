# UNAGAGORY Bootstrap Instructions

> **READ THIS FIRST** - This document contains all instructions needed to bootstrap the UNAGAGORY agent system.

---

## For LLMs: Self-Initialization Protocol

When you (an LLM) receive this document, follow these steps **exactly**:

### Phase 1: Environment Assessment

```yaml
# Execute these checks FIRST
checks:
  - Identify current working directory
  - Identify available tools (Read, Write, Bash, etc.)
  - Identify IDE/environment (VS Code, Terminal, Artifact, etc.)
  - Check for existing project structure
  - Identify user's permission level
  - Check available memory/context
```

**Action**: Report findings to user and request permission to proceed.

### Phase 2: Core Agent Initialization

Initialize the following agents in order:

```
1. PromptInterpreter     - Ready to analyze user requests
2. MasterOrchestrator    - Ready to coordinate agents
3. EnvironmentPreparer   - Ready to set up workspaces
4. MemoryManager         - Ready to persist state
5. PermissionManager     - Ready to handle escalations
```

**Action**: Load agent definitions from `agents/core/` and confirm readiness.

### Phase 3: Memory System Activation

```yaml
# Memory initialization
memory_init:
  1. Check for existing session in .unagagory/sessions/
  2. Load previous context if exists
  3. Initialize new session if fresh start
  4. Set up memory shaders for persistence
  5. Index available knowledge from repository
```

**Action**: Create or resume session, report memory status.

### Phase 4: User Request Processing

Once initialized, process user requests using this flow:

```
User Request
     │
     ▼
┌─────────────────────────────────────────────────────────┐
│              PROMPT INTERPRETER AGENT                    │
│                                                          │
│  1. Parse natural language request                       │
│  2. Extract explicit requirements                        │
│  3. Infer implicit requirements                          │
│  4. Identify constraints (time, budget, tech)            │
│  5. Determine project scope                              │
│  6. Flag ambiguities for clarification                   │
└─────────────────────────────────────────────────────────┘
     │
     ▼
┌─────────────────────────────────────────────────────────┐
│              SCOPE CONFIRMATION                          │
│                                                          │
│  Present to user:                                        │
│  - Interpreted requirements                              │
│  - Proposed architecture                                 │
│  - Estimated effort (agents/tasks)                       │
│  - Required permissions                                  │
│  - Any clarifying questions                              │
└─────────────────────────────────────────────────────────┘
     │
     ▼ (User approves)
┌─────────────────────────────────────────────────────────┐
│              MASTER ORCHESTRATOR                         │
│                                                          │
│  1. Create project plan                                  │
│  2. Identify required agent swarms                       │
│  3. Allocate resources                                   │
│  4. Set up parallel execution tracks                     │
│  5. Initialize progress tracking                         │
│  6. BEGIN AUTONOMOUS EXECUTION                           │
└─────────────────────────────────────────────────────────┘
```

---

## Permission Levels

UNAGAGORY uses a tiered permission system:

| Level | Name | Actions | User Approval |
|-------|------|---------|---------------|
| 0 | Read | Read files, analyze code | Never |
| 1 | Suggest | Propose changes, create plans | Never |
| 2 | Create | Create new files | On first use |
| 3 | Modify | Edit existing files | On first use |
| 4 | Execute | Run commands | Always |
| 5 | Deploy | Production deployment | Always + confirmation |
| 6 | Delete | Remove files/resources | Always + confirmation |
| 7 | Admin | System configuration | Always + double confirmation |

### Escalation Protocol

When an agent needs elevated permissions:

```yaml
escalation:
  1. Agent identifies need for elevated permission
  2. Agent pauses current task
  3. Agent constructs clear permission request:
     - What action is needed
     - Why it's needed
     - What will happen
     - Potential risks
     - Alternatives if denied
  4. User approves or denies
  5. Agent proceeds or adapts
```

---

## Agent Spawning Rules

### When to Spawn Agents

```yaml
spawn_triggers:
  # Spawn architect agents when:
  - New project initialization
  - Major feature addition
  - Architecture refactoring request

  # Spawn builder agents when:
  - Code generation needed
  - Implementation phase begins
  - Bug fixes required

  # Spawn tester agents when:
  - Code changes completed
  - Pre-commit checks needed
  - Quality gates triggered

  # Spawn reviewer agents when:
  - PR created or updated
  - Code review requested
  - Merge consideration

  # Spawn documentation agents when:
  - New features completed
  - API changes made
  - User-facing changes
```

### Agent Concurrency

```yaml
concurrency:
  max_agents: 10  # Maximum concurrent agents

  parallel_safe:  # Can run in parallel
    - Researchers
    - Testers (different areas)
    - Documentation writers
    - Static analyzers

  sequential_required:  # Must run sequentially
    - Architects (same area)
    - Builders (same files)
    - Database migrations
    - Deployments
```

---

## Memory Shaders

Memory shaders persist information across sessions:

### Shader Types

```yaml
shaders:
  project_context:
    purpose: "Project-wide context and decisions"
    persistence: permanent
    format: yaml
    location: .unagagory/memory/project_context.yaml

  session_state:
    purpose: "Current session state"
    persistence: session
    format: json
    location: .unagagory/sessions/{session_id}.json

  agent_memory:
    purpose: "Individual agent memories"
    persistence: permanent
    format: yaml
    location: .unagagory/memory/agents/{agent_id}.yaml

  code_knowledge:
    purpose: "Indexed code understanding"
    persistence: permanent
    format: sqlite
    location: .unagagory/memory/code_index.db

  conversation_history:
    purpose: "User interaction history"
    persistence: configurable
    format: jsonl
    location: .unagagory/memory/conversations/
```

### Memory Operations

```yaml
memory_ops:
  store:
    - Key-value pairs
    - Structured documents
    - Vector embeddings (if available)

  retrieve:
    - Exact key lookup
    - Pattern matching
    - Semantic search (if available)

  update:
    - Merge new information
    - Version history
    - Conflict resolution

  expire:
    - TTL-based expiration
    - Manual cleanup
    - Session-scoped cleanup
```

---

## Workflow Templates

### New Project Workflow

```yaml
workflow: new_project
steps:
  1_interpret:
    agent: PromptInterpreter
    action: Analyze user requirements
    output: requirements_doc

  2_architect:
    agent: SystemArchitect
    action: Design system architecture
    input: requirements_doc
    output: architecture_doc
    requires_approval: true

  3_setup:
    agent: EnvironmentPreparer
    action: Create project structure
    input: architecture_doc
    output: project_skeleton

  4_build:
    agents: [FrontendBuilder, BackendBuilder, DatabaseBuilder]
    action: Implement core features
    parallel: true
    input: architecture_doc
    output: source_code

  5_test:
    agents: [UnitTester, IntegrationTester]
    action: Create and run tests
    parallel: true
    input: source_code
    output: test_results

  6_review:
    agent: CodeReviewer
    action: Review all code
    input: [source_code, test_results]
    output: review_report

  7_document:
    agent: TechnicalDocWriter
    action: Generate documentation
    input: source_code
    output: documentation

  8_cicd:
    agent: CICDDesigner
    action: Set up CI/CD
    input: architecture_doc
    output: pipeline_config

  9_deploy:
    agent: EnvironmentPreparer
    action: Deploy to staging
    input: [source_code, pipeline_config]
    output: deployment_url
    requires_approval: true
```

### Bug Fix Workflow

```yaml
workflow: bug_fix
steps:
  1_analyze:
    agent: CodeReviewer
    action: Analyze bug report
    output: bug_analysis

  2_locate:
    agent: Researcher
    action: Find root cause
    input: bug_analysis
    output: root_cause

  3_fix:
    agent: CodeGenerator
    action: Implement fix
    input: root_cause
    output: fix_code

  4_test:
    agent: UnitTester
    action: Test fix
    input: fix_code
    output: test_results

  5_review:
    agent: CodeReviewer
    action: Review fix
    input: [fix_code, test_results]
    output: approval
```

---

## Claude Code Optimization

When running in Claude Code, use these optimizations:

### Tool Usage

```yaml
claude_code:
  prefer_tools:
    - Task (for spawning sub-agents)
    - Bash (for command execution)
    - Read/Write/Edit (for file operations)
    - Glob/Grep (for code search)

  tool_patterns:
    parallel_reads: true  # Read multiple files at once
    batch_edits: true     # Group related edits
    background_tasks: true # Use background execution
```

### Context Management

```yaml
context:
  # Minimize context usage
  summarize_long_outputs: true
  use_references_over_inline: true
  chunk_large_files: true

  # Maximize effectiveness
  front_load_critical_info: true
  use_structured_formats: true
  include_examples: true
```

### Agent Spawning

```yaml
claude_code_agents:
  use_task_tool: true
  subagent_types:
    - Explore       # For codebase exploration
    - Plan          # For architecture planning
    - general-purpose # For complex multi-step tasks
```

---

## Initialization Checklist

Before starting any project, verify:

```yaml
checklist:
  environment:
    [ ] Working directory identified
    [ ] Git repository initialized
    [ ] Required tools available
    [ ] IDE/editor detected

  permissions:
    [ ] File read permission confirmed
    [ ] File write permission requested
    [ ] Command execution permission scoped

  memory:
    [ ] Memory directory created
    [ ] Session initialized
    [ ] Previous context loaded (if any)

  agents:
    [ ] Core agents loaded
    [ ] Agent registry populated
    [ ] Spawn triggers configured

  user:
    [ ] Requirements understood
    [ ] Scope confirmed
    [ ] Approval workflow established
```

---

## Error Handling

When errors occur:

```yaml
error_handling:
  recoverable:
    - Log error to memory
    - Attempt automatic fix
    - If fixed, continue
    - If not, escalate to user

  non_recoverable:
    - Log error details
    - Save current state
    - Report to user with:
      - What went wrong
      - What was attempted
      - Current state
      - Recommended actions
    - Wait for user guidance

  escalation_triggers:
    - 3 consecutive failures on same task
    - Permission denied
    - External service unavailable
    - Ambiguous requirements
    - Conflicting constraints
```

---

## Quick Reference Commands

For Claude Code users, use these commands:

```
# Initialize UNAGAGORY
"Initialize UNAGAGORY and prepare for a new project"

# Start new project
"Create a new [type] project called [name] with requirements: [description]"

# Resume project
"Resume UNAGAGORY session for project [name]"

# Check status
"Show UNAGAGORY agent status and progress"

# Pause execution
"Pause all UNAGAGORY agents and save state"

# Specific agent
"Spawn [agent_name] agent for [task]"
```

---

## Next Steps

After reading this document:

1. **Confirm understanding** by summarizing the bootstrap process
2. **Request permission** to initialize the system
3. **Create session** in `.unagagory/sessions/`
4. **Load core agents** from `agents/core/`
5. **Wait for user instructions** or analyze existing project

---

*UNAGAGORY v1.0 - Self-Bootstrapping Agent Orchestration System*
