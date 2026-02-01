# Guia de Conventional Commits

Este guia detalha como aplicar a especificacao Conventional Commits em diferentes cenarios.

## Visao Geral

Conventional Commits e uma convencao para mensagens de commit que facilita:

- Geracao automatica de changelogs
- Determinacao semantica de versao (SemVer)
- Comunicacao clara da natureza das mudancas
- Facilitar contribuicoes de novos membros

## Fluxo de Decisao

### 1. Identifique o Tipo

Pergunte-se: "O que essa mudanca faz?"

```
Nova funcionalidade?           → feat
Corrige um bug?                → fix
Apenas documentacao?           → docs
Formatacao/estilo?             → style
Refatoracao sem mudar comportamento? → refactor
Melhoria de performance?       → perf
Adiciona/corrige testes?       → test
Build/dependencias?            → build
CI/CD?                         → ci
Manutencao geral?              → chore
Reverte commit anterior?       → revert
```

### 2. Defina o Escopo (Opcional)

Pergunte-se: "Qual area do codigo foi afetada?"

- Se afeta um modulo especifico: use o nome do modulo
- Se afeta multiplas areas: considere quebrar em commits menores
- Se e uma mudanca geral: omita o escopo

### 3. Escreva o Subject

Pergunte-se: "Como eu completaria a frase 'This commit will...'?"

- "This commit will **add user authentication**" → `add user authentication`
- "This commit will **fix login timeout issue**" → `fix login timeout issue`

### 4. Adicione Body se Necessario

Pergunte-se: "O subject explica tudo? Ha contexto importante?"

Adicione body quando:

- A mudanca e complexa
- Ha decisoes de design a documentar
- O "porque" nao e obvio

### 5. Adicione Footer se Necessario

Pergunte-se: "Ha breaking changes? Referencias a issues?"

## Cenarios Comuns

### Primeiro Commit do Repositorio

```
chore: initial commit
```

Ou com mais contexto:

```
chore: initial commit

Set up project structure with:
- Package.json configuration
- Basic directory structure
- Initial .gitignore
```

### Nova Feature

```
feat(auth): add password reset functionality

Users can now request a password reset email from the login page.
The reset link expires after 24 hours for security.

Closes #45
```

### Bug Fix

```
fix(cart): prevent negative quantities

Added validation to ensure quantity cannot go below 1.
Previously, users could set negative quantities which
caused incorrect totals.

Fixes #123
```

### Refatoracao

```
refactor(utils): extract date formatting to separate module

Moved date formatting functions from helpers.js to dates.js
for better organization and reusability.

No functional changes.
```

### Breaking Change

```
feat(api): migrate to v2 authentication

BREAKING CHANGE: The authentication endpoint has changed from
/api/auth to /api/v2/auth. All API clients must update their
base URL configuration.

Migration guide: https://docs.example.com/auth-migration
```

### Multiplas Issues Relacionadas

```
fix(validation): improve form error handling

- Add field-level error messages
- Highlight invalid fields
- Scroll to first error on submit

Closes #101, #102, #103
```

### Revert

```
revert: revert "feat(auth): add OAuth2 login"

This reverts commit abc1234.

OAuth2 integration causing issues in production.
Will re-implement after fixing the callback URL handling.
```

## Commits Atomicos

### Principio

Cada commit deve representar uma unica mudanca logica que:

- Pode ser entendida isoladamente
- Pode ser revertida sem afetar outras mudancas
- Compila e passa nos testes

### Exemplo: Quebrando um Commit Grande

**Ruim** - Um commit gigante:

```
feat: add user management system
```

**Bom** - Commits atomicos:

```
feat(db): add user table migration
feat(models): create User model with validation
feat(api): add user CRUD endpoints
feat(ui): create user management page
test(user): add unit tests for User model
docs(api): document user endpoints
```

## Integracao com Versionamento

Conventional Commits mapeia diretamente para SemVer:

| Tipo de Commit  | Versao SemVer | Exemplo       |
| --------------- | ------------- | ------------- |
| fix             | PATCH         | 1.0.0 → 1.0.1 |
| feat            | MINOR         | 1.0.0 → 1.1.0 |
| BREAKING CHANGE | MAJOR         | 1.0.0 → 2.0.0 |

## Dicas Praticas

### Use Templates

Configure um template de commit no git:

```bash
git config commit.template .gitmessage
```

### Revise Antes de Commitar

```bash
git diff --staged  # Veja o que sera commitado
git commit -v      # Mostra diff durante edicao da mensagem
```

### Corrija Commits Recentes

Se errou a mensagem do ultimo commit (nao pushado):

```bash
git commit --amend
```

### Squash Commits de WIP

Antes de fazer merge, combine commits de trabalho em progresso:

```bash
git rebase -i HEAD~3  # Interativo para ultimos 3 commits
```

## Referencias

- [Conventional Commits Specification](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [Angular Commit Guidelines](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#commit)
