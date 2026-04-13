# Template de Mensagem de Commit

Use este template como referencia para criar mensagens de commit padronizadas.

## Estrutura Basica

```
<type>(<scope>): <subject>
```

## Estrutura Completa

```
<type>(<scope>): <subject>

<body>

<footer>
```

## Campos

### Type (Obrigatorio)

Escolha um dos tipos abaixo:

- `feat` - Nova funcionalidade
- `fix` - Correcao de bug
- `docs` - Documentacao
- `style` - Formatacao (sem mudanca de logica)
- `refactor` - Refatoracao
- `perf` - Performance
- `test` - Testes
- `build` - Build/dependencias
- `ci` - CI/CD
- `chore` - Manutencao
- `revert` - Reverter commit

### Scope (Opcional)

Area do codigo afetada. Exemplos:

- `auth`, `api`, `ui`, `db`
- `cart`, `checkout`, `user`
- Nome do modulo ou componente

### Subject (Obrigatorio)

- Modo imperativo ("add" nao "added")
- Primeira letra minuscula
- Sem ponto final
- Maximo 50 caracteres

### Body (Opcional)

- Separado do subject por linha em branco
- Explica o "porque" da mudanca
- Maximo 72 caracteres por linha

### Footer (Opcional)

- Breaking changes: `BREAKING CHANGE: descricao`
- Referencias: `Closes #123` ou `Fixes #456`

## Exemplos Prontos

### Feature Simples

```
feat(auth): add email verification on signup
```

### Feature com Body

```
feat(payment): add support for PIX payments

PIX is now the most popular payment method in Brazil.
This implementation uses the Central Bank API for
QR code generation and payment confirmation.
```

### Bug Fix com Referencia

```
fix(cart): calculate discount before tax

The discount was being applied after tax calculation,
resulting in incorrect final prices.

Fixes #234
```

### Breaking Change

```
feat(api): require authentication for all endpoints

BREAKING CHANGE: All API endpoints now require a valid
JWT token in the Authorization header. Anonymous access
has been removed for security compliance.

Migration: Update all API clients to include authentication.
See docs/auth-migration.md for details.
```

### Refatoracao

```
refactor(utils): consolidate string helpers

Merged stringUtils.js and textHelpers.js into a single
strings.js module. No functional changes.
```

### Documentacao

```
docs(readme): add Docker setup instructions

Added step-by-step guide for running the application
using Docker Compose, including environment configuration.
```

### Primeiro Commit

```
chore: initial commit
```

### Revert

```
revert: revert "feat(cache): add Redis caching"

This reverts commit a1b2c3d.

Redis integration causing memory issues in production.
Reverting until we can properly configure memory limits.
```

## Checklist Pre-Commit

- [ ] Tipo correto para a mudanca?
- [ ] Subject no imperativo?
- [ ] Subject com menos de 50 caracteres?
- [ ] Body explica o "porque" (se necessario)?
- [ ] Breaking changes documentados?
- [ ] Issues referenciadas (se aplicavel)?
- [ ] Nenhum secret no commit?
- [ ] .gitignore atualizado (se primeiro commit)?
