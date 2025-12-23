# UNAGAGORY Architecture

## System Overview

UNAGAGORY is a multi-agent orchestration system that coordinates AI agents to build complete software solutions.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              USER INTERFACE                                  │
│                    (CLI / IDE / API / Chat Interface)                       │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          MASTER ORCHESTRATOR                                 │
│                    (Tier 10 - Supreme Coordination)                         │
├─────────────────────────────────────────────────────────────────────────────┤
│  • Spawn/terminate agents    • Manage workflows    • Handle escalations     │
│  • Resource allocation       • Checkpoint/recovery  • Cross-agent comms     │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
              ┌───────────────────────┼───────────────────────┐
              │                       │                       │
              ▼                       ▼                       ▼
┌─────────────────────┐ ┌─────────────────────┐ ┌─────────────────────┐
│   MEMORY MANAGER    │ │ PERMISSION MANAGER  │ │  BUDGET ANALYST     │
│      (Tier 9)       │ │      (Tier 9)       │ │     (Tier 6)        │
├─────────────────────┤ ├─────────────────────┤ ├─────────────────────┤
│ • Memory shaders    │ │ • Permission levels │ │ • Token tracking    │
│ • Cross-session     │ │ • Escalation        │ │ • Cost optimization │
│ • Context indexing  │ │ • Audit logging     │ │ • Budget alerts     │
└─────────────────────┘ └─────────────────────┘ └─────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            AGENT SWARM                                       │
├─────────────┬─────────────┬─────────────┬─────────────┬─────────────────────┤
│ ARCHITECTS  │  BUILDERS   │  REVIEWERS  │   TESTERS   │    SPECIALISTS      │
├─────────────┼─────────────┼─────────────┼─────────────┼─────────────────────┤
│ System      │ Code        │ Code        │ Unit        │ Documentation       │
│ Frontend    │ Generator   │ Reviewer    │ Integration │ License Manager     │
│ Backend     │             │ Quality     │ E2E         │ OpenSource Finder   │
│ Database    │             │ Controller  │             │ Budget Analyst      │
└─────────────┴─────────────┴─────────────┴─────────────┴─────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          SECURITY SENTINEL                                   │
│                         (Tier 8 - Always Active)                            │
├─────────────────────────────────────────────────────────────────────────────┤
│  • Vulnerability scanning   • Secret detection    • Security reviews        │
│  • OWASP compliance        • Dependency audit    • Action blocking         │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                           LLM INTERFACE SDK                                  │
│                    (Provider Abstraction Layer)                              │
├─────────────┬─────────────┬─────────────┬───────────────────────────────────┤
│   Claude    │   OpenAI    │   Ollama    │          Other Providers          │
└─────────────┴─────────────┴─────────────┴───────────────────────────────────┘
```

## Component Details

### Master Orchestrator

The supreme coordinator of the entire system.

**Responsibilities:**
- Spawn and terminate agents based on workflow needs
- Manage parallel and sequential task execution
- Handle escalations from lower-tier agents
- Maintain system checkpoints for recovery
- Coordinate communication between agents

**Key Decisions:**
- Which agents to spawn for a task
- When to parallelize vs serialize
- Resource allocation across agents
- Escalation handling

### Memory System

Four-layer memory architecture for context persistence.

```
┌─────────────────────────────────────────────────────────────────┐
│                        MEMORY LAYERS                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│   L1 (HOT)     │ Current context, active operations            │
│   ─────────────┼────────────────────────────────────────────── │
│   L2 (WARM)    │ Session state, recent conversation            │
│   ─────────────┼────────────────────────────────────────────── │
│   L3 (COLD)    │ Project context, architecture decisions       │
│   ─────────────┼────────────────────────────────────────────── │
│   L4 (ARCHIVE) │ Completed projects, historical patterns       │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

**Memory Shaders:**
- `session_state.yaml` - Current session tracking
- `project_context.yaml` - Project-wide persistent context
- `token_budget.yaml` - Resource usage tracking
- `codebase_index.yaml` - Searchable code index

### Permission System

Hierarchical permission model with escalation.

| Level | Name | Capabilities |
|-------|------|--------------|
| 0 | Read | Read files only |
| 1 | Suggest | Analyze and suggest changes |
| 2 | Create | Create new files |
| 3 | Modify | Edit existing files |
| 4 | Execute | Run commands |
| 5 | Deploy | Network and deployment |
| 6 | Delete | Remove files |
| 7 | Admin | System-level access |

### Agent Tiers

Agents are organized into tiers based on their role in the hierarchy.

| Tier | Name | Role | Examples |
|------|------|------|----------|
| 0 | Foundation | Infrastructure | LLM Interface |
| 1 | Interpreters | Input processing | PromptInterpreter |
| 2 | Planners | Scope definition | ScopeAnalyzer |
| 3 | Designers | Architecture | SystemArchitect |
| 4 | Implementers | Code generation | CodeGenerator |
| 5 | Specialists | Domain expertise | DocumentationWriter |
| 6 | Quality | Testing/Review | UnitTester, CodeReviewer |
| 7 | Operations | DevOps | CICDDesigner |
| 8 | Security | Protection | SecuritySentinel |
| 9 | Management | Resource control | MemoryManager |
| 10 | Orchestration | Coordination | MasterOrchestrator |

### Workflow System

Workflows define the sequence of agent activities.

```yaml
workflow: new_project
phases:
  - discovery     # Understand requirements
  - architecture  # Design system
  - setup         # Create project structure
  - implementation # Write code
  - testing       # Verify quality
  - review        # Final checks
  - documentation # Create docs
  - deployment    # Deploy to staging
```

Each phase can:
- Run steps sequentially or in parallel
- Have quality gates requiring approval
- Trigger agent spawning
- Create checkpoints for recovery

## Data Flow

### Request Processing

```
User Request
     │
     ▼
┌────────────────────┐
│  PromptInterpreter │ ──► Extract requirements
└────────────────────┘
     │
     ▼
┌────────────────────┐
│ MasterOrchestrator │ ──► Select workflow, spawn agents
└────────────────────┘
     │
     ▼
┌────────────────────┐
│  Architect Agents  │ ──► Design solution
└────────────────────┘
     │
     ▼
┌────────────────────┐
│  Builder Agents    │ ──► Generate code
└────────────────────┘
     │
     ▼
┌────────────────────┐
│  Reviewer Agents   │ ──► Verify quality
└────────────────────┘
     │
     ▼
Completed Deliverable
```

### Memory Flow

```
Agent Operation
     │
     ├──► L1: Store in hot memory (immediate access)
     │
     ├──► L2: Update session state
     │
     ├──► L3: Record decisions, update project context
     │
     └──► L4: Archive on completion (compressed)
```

## Security Architecture

### Defense in Depth

```
┌─────────────────────────────────────────────────────────────────┐
│                    SECURITY LAYERS                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│   USER INPUT      │ Prompt injection protection                 │
│   ────────────────┼────────────────────────────────────────────│
│   PERMISSIONS     │ Level-based access control                  │
│   ────────────────┼────────────────────────────────────────────│
│   GUARDRAILS      │ Hard/soft limits on actions                 │
│   ────────────────┼────────────────────────────────────────────│
│   CODE SCANNING   │ SAST, dependency audit, secret detection    │
│   ────────────────┼────────────────────────────────────────────│
│   AUDIT LOGGING   │ All actions tracked and logged              │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Security Sentinel

Always-active security monitoring:
- Scans all generated code
- Detects exposed secrets
- Checks for OWASP Top 10 vulnerabilities
- Audits dependencies
- Can block unsafe actions

## Extensibility

### Adding New Agents

1. Create agent definition in `agents/{category}/{agent_name}.yaml`
2. Define:
   - Agent ID, name, tier
   - System prompt
   - Capabilities
   - Tools
   - Triggers
   - Permissions
3. Register in `agents/AGENT_INDEX.yaml`

### Adding New Workflows

1. Create workflow in `orchestration/workflows/{workflow_name}.yaml`
2. Define:
   - Phases and steps
   - Agent assignments
   - Quality gates
   - Success criteria

### Adding Memory Shaders

1. Create shader in `memory/shaders/{shader_name}.yaml`
2. Define:
   - Schema for stored data
   - Operations
   - Storage configuration
   - Lifecycle rules

## Performance Considerations

### Token Efficiency
- Memory summarization to reduce context
- Focused prompts for specific tasks
- Caching of common patterns
- Budget tracking and alerts

### Parallelization
- Independent tasks run concurrently
- Agent pools for scalability
- Async operations where possible

### Recovery
- Checkpoints after each phase
- State persistence in memory shaders
- Graceful degradation on errors

---

*UNAGAGORY Architecture Document v1.0.0*
