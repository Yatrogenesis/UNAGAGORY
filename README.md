# UNAGAGORY

**UNified AGnostic AGent ORchestrator Yatrogenesis**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Optimized-blueviolet)](https://claude.ai)
[![LLM Agnostic](https://img.shields.io/badge/LLM-Agnostic-green)](https://github.com/Yatrogenesis/UNAGAGORY)

> A complete, self-bootstrapping agent orchestration system for massive software production. Clone it, let your LLM read it, and watch autonomous agents build your entire project.

---

## Vision

UNAGAGORY enables any LLM to become a **complete software production factory**. After cloning this repository, an LLM can:

1. **Bootstrap itself** with all necessary agents
2. **Orchestrate multiple specialized agents** working in parallel
3. **Maintain project memory** across sessions
4. **Manage permissions and escalations** with user approval
5. **Run until completion** without stopping

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           UNAGAGORY VISION                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Human: "Build me a SaaS platform for inventory management"                │
│                        │                                                     │
│                        ▼                                                     │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    PROMPT INTERPRETER AGENT                          │   │
│   │         Analyzes requirements, scope, constraints                    │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                        │                                                     │
│                        ▼                                                     │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    MASTER ORCHESTRATOR                               │   │
│   │         Spawns and coordinates all agent swarms                      │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│          │              │              │              │                      │
│          ▼              ▼              ▼              ▼                      │
│   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐                │
│   │Architect │   │ Builder  │   │ Tester   │   │ DevOps   │                │
│   │  Swarm   │   │  Swarm   │   │  Swarm   │   │  Swarm   │                │
│   └──────────┘   └──────────┘   └──────────┘   └──────────┘                │
│          │              │              │              │                      │
│          └──────────────┴──────────────┴──────────────┘                      │
│                                   │                                          │
│                                   ▼                                          │
│                        ┌─────────────────┐                                   │
│                        │  PRODUCTION SW  │                                   │
│                        │   (Complete)    │                                   │
│                        └─────────────────┘                                   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Quick Start

### For Claude Code (Primary Target)

```bash
# Clone the repository
git clone https://github.com/Yatrogenesis/UNAGAGORY.git

# Navigate to project
cd UNAGAGORY

# Bootstrap UNAGAGORY in your Claude Code session
# Just tell Claude: "Read UNAGAGORY/BOOTSTRAP.md and initialize the system"
```

### For Other LLMs

```bash
# Clone and provide the BOOTSTRAP.md to your LLM
git clone https://github.com/Yatrogenesis/UNAGAGORY.git

# Have your LLM read:
# 1. BOOTSTRAP.md - Initialization instructions
# 2. agents/ - Agent definitions
# 3. orchestration/ - Workflow configurations
```

---

## Architecture

### Agent Hierarchy

```
UNAGAGORY Agent System
│
├── TIER 0: META-ORCHESTRATION
│   ├── MasterOrchestrator      # Coordinates all swarms
│   ├── OrchestratorOfOrchestrators  # Multi-project coordination
│   └── InterLLMOrchestrator    # Cross-LLM work distribution
│
├── TIER 1: INTERPRETERS & PLANNERS
│   ├── PromptInterpreter       # Human request analysis
│   ├── ScopeAnalyzer           # Project scope definition
│   ├── RequirementsExtractor   # Detailed requirements
│   └── ConstraintIdentifier    # Limitations and boundaries
│
├── TIER 2: ARCHITECTS
│   ├── SystemArchitect         # Overall system design
│   ├── FrontendArchitect       # UI/UX architecture
│   ├── BackendArchitect        # Server/API architecture
│   ├── DatabaseArchitect       # Data layer design
│   ├── SecurityArchitect       # Security design
│   ├── CloudArchitect          # Infrastructure design
│   └── ArchitectureAdvisor     # Design optimization
│
├── TIER 3: BUILDERS
│   ├── CodeGenerator           # Core code writing
│   ├── FrontendBuilder         # UI implementation
│   ├── BackendBuilder          # API/Server implementation
│   ├── DatabaseBuilder         # Schema/Migration creation
│   ├── LibraryCreator          # Reusable component creation
│   └── IntegrationBuilder      # Third-party integrations
│
├── TIER 4: QUALITY & REVIEW
│   ├── CodeReviewer            # Code quality review
│   ├── PRReviewer              # Pull request review
│   ├── Linter                  # Code style enforcement
│   ├── Refactorer              # Code improvement
│   ├── QualityController       # Overall quality assurance
│   └── ComplianceVerifier      # Standards compliance
│
├── TIER 5: TESTING
│   ├── UnitTester              # Unit test creation/execution
│   ├── IntegrationTester       # Integration testing
│   ├── E2ETester               # End-to-end testing
│   ├── PerformanceTester       # Load/stress testing
│   ├── SecurityTester          # Security testing
│   └── TestReporter            # Test result analysis
│
├── TIER 6: INFRASTRUCTURE
│   ├── CICDDesigner            # Pipeline design
│   ├── CICDMaintainer          # Pipeline maintenance
│   ├── EnvironmentPreparer     # Dev/staging/prod setup
│   ├── WorkspaceManager        # IDE/workspace config
│   └── ContainerArchitect      # Docker/K8s design
│
├── TIER 7: DOCUMENTATION
│   ├── TechnicalDocWriter      # Technical documentation
│   ├── APIDocWriter            # API documentation
│   ├── UserManualWriter        # End-user documentation
│   ├── DesignDocWriter         # Technical design docs
│   └── ReadmeGenerator         # README creation
│
├── TIER 8: SECURITY & COMPLIANCE
│   ├── SecuritySentinel        # Security monitoring
│   ├── GuardrailReviewer       # Safety boundaries
│   ├── LicenseManager          # License compliance
│   ├── PermissionManager       # Access control
│   └── AuditLogger             # Activity logging
│
├── TIER 9: ANALYTICS & METRICS
│   ├── MetricsCreator          # Metric definition
│   ├── MetricsCollector        # Data collection
│   ├── BudgetAnalyst           # Token/cost analysis
│   ├── ProgressTracker         # Project progress
│   └── PerformanceAnalyzer     # System performance
│
└── TIER 10: RESEARCH & DISCOVERY
    ├── Researcher              # Technical research
    ├── OpenSourceFinder        # OSS discovery
    ├── PatternAnalyzer         # Code pattern analysis
    └── TechStackAdvisor        # Technology recommendations
```

---

## Core Components

### 1. Agent Definitions (`agents/`)

Each agent is defined with:
- **System prompt** - Core identity and capabilities
- **Task prompts** - Specific task instructions
- **Tools** - Available tool definitions
- **Permissions** - Required permission levels
- **Triggers** - When to activate

### 2. Orchestration System (`orchestration/`)

- **Workflows** - Multi-step process definitions
- **Pipelines** - Sequential/parallel execution
- **Schedulers** - Task scheduling and prioritization
- **State machines** - Workflow state management

### 3. Memory System (`memory/`)

- **Shaders** - Memory persistence layers
- **Stores** - Long-term knowledge storage
- **Indexes** - Fast retrieval indexes
- **Context windows** - Session context management

### 4. Permission System (`permissions/`)

- **Levels** - Permission tier definitions
- **Policies** - Access control policies
- **Escalation** - User approval workflows

### 5. Prompt Library (`prompts/`)

- **System prompts** - Agent identities
- **Task prompts** - Task-specific instructions
- **Chain prompts** - Multi-step reasoning
- **Few-shot examples** - Learning examples

---

## Features

### LLM Agnostic Design

UNAGAGORY works with any LLM that can:
- Read and understand markdown/YAML
- Execute tools/functions
- Maintain conversation context

**Optimized for Claude Code** with fallbacks for:
- OpenAI GPT-4
- Anthropic Claude API
- Ollama local models
- Any MCP-compatible model

### Cross-Session Memory

```yaml
# Memory shader configuration
memory:
  backend: file  # or redis, sqlite, vector-db
  persistence: true
  encryption: aes-256
  indexes:
    - semantic  # Vector similarity
    - temporal  # Time-based
    - entity    # Entity relationships
```

### Autonomous Execution

Once started, agents:
1. Work until project completion
2. Request escalation only when needed
3. Self-heal on errors
4. Checkpoint progress regularly

### Multi-IDE Support

- VS Code (primary)
- Cursor
- Windsurf
- JetBrains IDEs
- Vim/Neovim
- Artifact (Claude)
- Any terminal

---

## Directory Structure

```
UNAGAGORY/
├── .unagagory/              # Runtime configuration
│   ├── config/              # Active configuration
│   ├── memory/              # Session memory
│   └── sessions/            # Session state
│
├── agents/                  # Agent definitions
│   ├── core/                # Core system agents
│   ├── architects/          # Architecture agents
│   ├── reviewers/           # Review agents
│   ├── builders/            # Building agents
│   ├── testers/             # Testing agents
│   ├── orchestrators/       # Orchestration agents
│   ├── security/            # Security agents
│   ├── documentation/       # Documentation agents
│   ├── infrastructure/      # DevOps agents
│   ├── analytics/           # Analytics agents
│   └── integrations/        # Integration agents
│
├── prompts/                 # Prompt templates
│   ├── system/              # System prompts
│   ├── task/                # Task prompts
│   ├── chain/               # Chain-of-thought prompts
│   └── few-shot/            # Few-shot examples
│
├── memory/                  # Memory management
│   ├── shaders/             # Memory persistence layers
│   ├── stores/              # Knowledge stores
│   └── indexes/             # Retrieval indexes
│
├── orchestration/           # Orchestration system
│   ├── workflows/           # Workflow definitions
│   ├── pipelines/           # Pipeline configurations
│   └── schedulers/          # Scheduling logic
│
├── permissions/             # Permission system
│   ├── levels/              # Permission levels
│   ├── policies/            # Access policies
│   └── escalation/          # Escalation rules
│
├── templates/               # Project templates
│   ├── projects/            # Full project templates
│   ├── cicd/                # CI/CD templates
│   ├── databases/           # Database templates
│   ├── frontend/            # Frontend templates
│   ├── backend/             # Backend templates
│   └── fullstack/           # Full-stack templates
│
├── tools/                   # Tool configurations
│   ├── linters/             # Linter configs
│   ├── formatters/          # Formatter configs
│   └── analyzers/           # Analyzer configs
│
├── sdk/                     # LLM SDK integrations
│   ├── claude/              # Claude-specific
│   ├── openai/              # OpenAI-specific
│   ├── anthropic/           # Anthropic API
│   ├── ollama/              # Ollama local
│   └── common/              # Shared utilities
│
├── integrations/            # External integrations
│   ├── ide/                 # IDE integrations
│   ├── vcs/                 # Version control
│   ├── cloud/               # Cloud providers
│   └── databases/           # Database systems
│
├── docs/                    # Documentation
│   ├── guides/              # User guides
│   ├── api/                 # API documentation
│   └── architecture/        # Architecture docs
│
├── examples/                # Usage examples
│   ├── simple/              # Simple examples
│   ├── complex/             # Complex examples
│   └── enterprise/          # Enterprise examples
│
├── BOOTSTRAP.md             # Bootstrap instructions
├── CLAUDE.md                # Claude Code context
└── unagagory.yaml           # Main configuration
```

---

## Supported Languages

UNAGAGORY supports **all major programming languages**:

| Category | Languages |
|----------|-----------|
| **Systems** | Rust, C, C++, Go, Zig |
| **Web Backend** | Python, Node.js, Java, C#, Ruby, PHP |
| **Web Frontend** | TypeScript, JavaScript, HTML, CSS, SCSS |
| **Mobile** | Swift, Kotlin, Dart, React Native |
| **Data/ML** | Python, R, Julia, SQL |
| **Scripting** | Bash, PowerShell, Python, Lua |
| **Functional** | Haskell, Elixir, Clojure, F#, OCaml |
| **Config** | YAML, JSON, TOML, HCL, Dhall |

---

## Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/Yatrogenesis/UNAGAGORY.git
cd UNAGAGORY
```

### 2. Configure

Edit `unagagory.yaml` with your preferences:

```yaml
llm:
  primary: claude-code
  fallback: [claude-api, openai, ollama]

project:
  name: "My Project"
  type: fullstack

agents:
  auto_spawn: true
  max_concurrent: 10

memory:
  persist: true
  backend: sqlite
```

### 3. Bootstrap

Tell your LLM:
```
Read UNAGAGORY/BOOTSTRAP.md and initialize the agent system.
Then analyze my project requirements: [YOUR REQUIREMENTS]
```

### 4. Let It Run

The system will:
1. Parse your requirements
2. Spawn necessary agents
3. Create project structure
4. Build, test, and deploy
5. Request approval only when needed

---

## License

MIT License - Use freely, attribute kindly.

---

## Author

**Francisco Molina Burgos** (Yatrogenesis)
- ORCID: 0009-0008-6093-8267
- GitHub: github.com/Yatrogenesis

---

*"One prompt to build them all."*
