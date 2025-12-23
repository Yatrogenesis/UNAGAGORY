# UNAGAGORY Quick Start Guide

Get started with UNAGAGORY in 5 minutes.

## Prerequisites

- Git installed
- An LLM with tool use capability (Claude Code recommended)
- API key for your chosen LLM provider

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Yatrogenesis/UNAGAGORY.git
cd UNAGAGORY
```

### 2. Read the Bootstrap Instructions

If you're an LLM, read `BOOTSTRAP.md` for self-initialization instructions.

If you're a human setting this up for an LLM:

```bash
cat BOOTSTRAP.md
```

## First Project

### Option A: Claude Code (Recommended)

1. Open a terminal in your project directory
2. Start Claude Code:
   ```bash
   claude
   ```
3. Tell Claude about UNAGAGORY:
   ```
   I've cloned UNAGAGORY to /path/to/UNAGAGORY. Please read the BOOTSTRAP.md
   file and initialize yourself as an UNAGAGORY orchestrator.
   ```
4. Once initialized, request your project:
   ```
   Create a new React dashboard application with user authentication,
   data visualization, and a REST API backend using Node.js.
   ```

### Option B: Other LLMs

1. Provide the LLM with the contents of:
   - `BOOTSTRAP.md` (initialization instructions)
   - `README.md` (system overview)
   - `unagagory.yaml` (configuration)
   - Relevant agent definitions from `agents/`

2. Ask the LLM to follow the bootstrap protocol.

## Example Workflows

### Create a New Project

```
User: Create a todo application with React frontend and Python FastAPI backend.

UNAGAGORY will:
1. Analyze requirements (PromptInterpreter)
2. Design architecture (SystemArchitect, FrontendArchitect, BackendArchitect)
3. Set up project structure (EnvironmentPreparer)
4. Generate code (CodeGenerator)
5. Write tests (UnitTester, IntegrationTester)
6. Review code (CodeReviewer, SecuritySentinel)
7. Create documentation (DocumentationWriter)
8. Set up CI/CD (CICDDesigner)
```

### Add Feature to Existing Project

```
User: Add dark mode support to the existing React application.

UNAGAGORY will:
1. Analyze existing codebase (codebase_index shader)
2. Design feature (FrontendArchitect)
3. Implement changes (CodeGenerator)
4. Update tests (UnitTester)
5. Review changes (CodeReviewer)
```

### Fix a Bug

```
User: The login form doesn't validate email addresses properly.

UNAGAGORY will:
1. Locate relevant code (codebase_index)
2. Analyze the issue (CodeReviewer)
3. Implement fix (CodeGenerator)
4. Add regression test (UnitTester)
5. Verify fix (IntegrationTester)
```

## Key Concepts

### Agents
Specialized AI workers with specific capabilities. Each agent has:
- A tier (0-10) indicating its role hierarchy
- Defined capabilities and tools
- Permission levels for actions

### Memory Shaders
Persistent memory layers that survive across sessions:
- **L1 (Hot)**: Current context, active tasks
- **L2 (Warm)**: Session state
- **L3 (Cold)**: Project context, decisions
- **L4 (Archive)**: Historical data

### Workflows
Predefined sequences of agent activities:
- **new_project**: Complete project creation
- **bug_fix**: Issue resolution
- **feature**: Feature development
- **refactor**: Code improvement

### Permission Levels
Actions require appropriate permissions:
- 0: Read files
- 1: Analyze/suggest
- 2: Create files
- 3: Modify files
- 4: Execute commands
- 5: Deploy/network
- 6: Delete files
- 7: Admin/system

## Configuration

Edit `unagagory.yaml` to customize:

```yaml
# LLM Settings
llm:
  primary_provider: claude
  model: claude-opus-4-5-20251101

# Permission defaults
permissions:
  default_level: 1
  auto_approve_below: 2

# Memory settings
memory:
  auto_save: true
  save_interval: 60
```

## Troubleshooting

### LLM Not Following Protocol
- Ensure BOOTSTRAP.md was fully read
- Re-initialize with explicit instructions
- Check that agent definitions are accessible

### Permission Issues
- Check current permission level
- Request escalation for higher-level actions
- Review permission_manager.yaml for rules

### Memory Not Persisting
- Verify `.unagagory/` directory is writable
- Check memory shader configuration
- Ensure save operations complete before session end

## Next Steps

1. Read the full [README.md](../README.md)
2. Explore agent definitions in `agents/`
3. Review workflow templates in `orchestration/`
4. Customize configuration in `unagagory.yaml`

## Getting Help

- Review documentation in `docs/`
- Check agent capabilities in `agents/AGENT_INDEX.yaml`
- Examine prompt templates in `prompts/`

---

*UNAGAGORY - UNified AGnostic AGent ORchestator Yatrogenesis*
