# OpenCode Configuration

This is a new OpenCode configuration. Customize it according to your needs.

## Structure

```
/
├── config/                       # Configuration directory
│   ├── agent/                   # Agent definitions (markdown files)
│   ├── skill/                   # Custom skills (directories with instructions)
│   ├── command/                 # Custom commands (markdown files)
│   ├── instructions/            # Shared instructions
│   ├── policies/rules/          # Policy documents
│   ├── opencode.jsonc           # OpenCode configuration
│   ├── AGENTS.md                # Project guidelines
│   └── .gitignore               # Git ignore patterns
└── opencode.metadata.jsonc      # Configuration metadata
```

## Getting Started

1. Edit `opencode.metadata.jsonc` to add description and metadata
2. Add agents in `config/agent/` directory
3. Add skills in `config/skill/` directory
4. Add commands in `config/command/` directory
5. Add instructions in `config/instructions/` directory
6. Customize `config/opencode.jsonc` as needed
7. Update `config/AGENTS.md` with project-specific guidelines

## Activation

```bash
opencode-config use <config-name>
source ~/.zshrc
```
