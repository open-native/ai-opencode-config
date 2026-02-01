# AGENTS.md

Single source of truth for AI coding agents (Claude, Gemini, Copilot, Cursor).

## Repository Overview

This is a custom OpenCode configuration. Customize agents, skills, and commands to fit your workflow.

## Build/Lint/Test Commands

```bash
# Add your project-specific commands here
```

## Code Style Guidelines

Add your code style guidelines here.

## File Structure

```
/
├── agent/                    # Agent definitions (.md files)
├── skill/                    # Skill definitions
├── command/                  # Custom slash commands
├── instructions/             # Shared instructions
├── policies/rules/           # Policy documents
└── opencode.jsonc            # Main OpenCode configuration
```

## Commit Conventions

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(scope): <subject>

Types: feat, fix, docs, style, refactor, perf, test, build, ci, chore, revert
```

## Agent Development Guidelines

### Creating Agents

1. Place agent file in `agent/<name>.md`
2. Use YAML frontmatter for metadata:
   ```yaml
   ---
   name: my-agent
   description: Brief description
   mode: subagent
   temperature: 0.1
   tools:
     write: true
     edit: true
     bash: true
   ---
   ```

### Creating Skills

1. Create directory `skill/<skill-name>/`
2. Add `SKILL.md` with frontmatter:
   ```yaml
   ---
   name: skill-name
   description: What the skill does (max 1024 chars)
   ---
   ```

### Creating Commands

1. Create directory `command/<command-name>/`
2. Add `COMMAND.md` with slash command definition

## Operational Rules

- **Never commit** unless explicitly requested
- **Never push** unless explicitly requested
- **Use plan tool** for multi-step tasks
- **Validate changes** with tests before completing
- **Avoid destructive commands** without approval

## Security

- Never commit secrets, tokens, or credentials
- Use environment variables for sensitive config
- Check `.gitignore` exists before first commit
