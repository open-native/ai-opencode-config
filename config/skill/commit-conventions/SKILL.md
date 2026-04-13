---
name: commit-conventions
description: Create commits based on conventional-commits specs. It should be always loaded before commiting and should be always used.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: version-control
---

## What I do

- Criar mensagens de commit claras e padronizadas
- Aplicar Conventional Commits corretamente
- Escolher o tipo de commit adequado (feat, fix, docs, etc.)
- Estruturar body e footer quando necessario
- Garantir consistencia no historico de commits

## When to use me

Use this skill when you need to create or review commit messages. This is especially helpful when:

- Creating commits for new features, bug fixes, or refactoring
- Writing the first commit of a repository
- Adding breaking changes that need documentation
- Referencing issues or pull requests in commits
- Reviewing commit message quality

## How I work

I follow Conventional Commits specification:

1. **Formato padrao**: `<type>(scope): <subject>`
2. **Tipos semanticos**: feat, fix, docs, style, refactor, perf, test, build, ci, chore, revert
3. **Escopo opcional**: Identifica a area afetada
4. **Mensagem imperativa**: Descreve o "porque", nao o "o que"

## Restrictions

- Nunca commitar arquivos com secrets (.env, credentials, etc.)
- Sempre verificar se existe .gitignore antes do primeiro commit
- O primeiro commit deve ser `chore: initial commit`
- Mensagens devem focar no "why", o diff mostra o "what"
- Nao usar emojis a menos que seja padrao do projeto

## Available Resources

When you need specific guidance, load these files:

### Standards and Guidelines

- `skills/commit-conventions/references/standards.md` - Padroes e restricoes gerais

### Instructions by Task Type

- `skills/commit-conventions/references/conventional-commits.md` - Guia completo de Conventional Commits

### Templates

- `skills/commit-conventions/references/commit-message.md` - Template de mensagem de commit

Use the Read tool to load the appropriate file based on the task at hand.
