# AGENTS.md

Single source of truth for AI coding agents (Claude, Gemini, Copilot, Cursor).

## Repository Overview

This is a custom OpenCode configuration repository. It defines agents, skills, and commands used by the OpenCode CLI.
Customize agents, skills, and commands to fit your workflow.

## Build, Lint, and Test Commands

Since this is a configuration repository, standard build artifacts are not produced. However, you should validate configuration files.

### Dependency Management
This project uses [Bun](https://bun.sh/).

```bash
# Install dependencies
bun install
```

### Validation & Linting
Ensure all JSON/JSONC and YAML files are syntactically correct.

```bash
# Check formatting (if prettier is installed)
bun x prettier --check "**/*.{json,jsonc,md,yaml}"

# Fix formatting
bun x prettier --write "**/*.{json,jsonc,md,yaml}"
```

### Testing
There is no automated test suite. Verification is manual:
1. Reload OpenCode to apply changes.
2. Test the specific Agent, Skill, or Command interactively.
3. Use the `/debug` command if available to inspect state.

To test a specific agent:
```bash
opencode run --agent <agent-name> "Test prompt"
```

## Code Style Guidelines

### File Structure & Naming
- **Directories:** Use `kebab-case` (e.g., `my-skill`, `data-processing`).
- **Files:** Use `kebab-case` matching the directory or content (e.g., `agent/my-agent.md`).
- **Extensions:**
  - Agents: `.md`
  - Skills: `.md` (inside `skills/<name>/`)
  - Config: `.jsonc` (preferred over `.json` to allow comments)

### Formatting
- **Indentation:** 2 spaces for all file types (JSON, YAML, Markdown).
- **Line Endings:** LF (Unix style).
- **Markdown:**
  - Use ATX headers (`#`, `##`).
  - Use fenced code blocks with language identifiers (e.g., \`\`\`bash).
  - Limit line length to 100 characters where possible.

### Configuration (JSONC/YAML)
- **Comments:** Use comments in `.jsonc` files to explain non-obvious configurations.
- **Keys:** Use `camelCase` for JSON keys unless a specific schema requires otherwise.
- **Strings:** Double quotes `"` for JSON.

### Imports & References
- When referencing other files (e.g., in `opencode.jsonc` instructions), use relative paths from the config root.
- Example: `"instructions": ["instructions/**/*.md"]`

## File Structure

```
/
├── agent/                    # Agent definitions (.md files)
├── skills/                   # Skill definitions (each in its own subdir)
├── command/                  # Custom slash commands (each in its own subdir)
├── instructions/             # Shared instructions/context
├── policies/rules/           # Policy documents
└── opencode.jsonc            # Main OpenCode configuration
```

## Commit Conventions

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(scope): <subject>

Types:
- feat: New agent, skill, or command
- fix: Bug fix in configuration
- docs: Documentation changes
- style: Formatting changes
- refactor: Restructuring config
- chore: Maintenance (deps, etc.)
```

Example: `feat(agent): add new data-analysis agent`

## Agent Development Guidelines

### Creating Agents
1. Place agent file in `agent/<name>.md`.
2. Use YAML frontmatter for metadata.
3. Define system prompt in the Markdown body.

```markdown
---
name: my-agent
description: specialized agent for X
mode: subagent
temperature: 0.1
tools:
  write: true
  edit: true
  bash: true
---

You are an agent specialized in...
```

### Creating Skills
Skills provide reusable capabilities or knowledge.

1. Create directory `skills/<skill-name>/`.
2. Add `SKILL.md` with frontmatter.

```markdown
---
name: skill-name
description: specific capability description (max 1024 chars)
---

# Instructions
Step-by-step guide for this skill...
```

### Creating Commands
Custom slash commands for the OpenCode CLI.

1. Create directory `command/<command-name>/`.
2. Add `COMMAND.md`.

## Operational Rules

- **Never commit** unless explicitly requested by the user.
- **Never push** unless explicitly requested.
- **Use plan tool** for multi-step tasks to ensure logical progression.
- **Validate changes**: Since there are no unit tests, verify your config changes by explaining what they do or asking the user to test.
- **Avoid destructive commands** (like `rm -rf`) without explicit approval and explanation.
- **Security:**
  - Never commit secrets, tokens, or credentials.
  - Use environment variables (e.g., `{env:MY_TOKEN}`) in configuration files.
  - Ensure `.gitignore` is properly configured.
