# Padroes e Restricoes de Commit Conventions

Este documento define os padroes gerais que devem ser seguidos em todas as mensagens de commit.

## Restricoes Gerais

- **Nunca commite secrets**: Arquivos como `.env`, `credentials.json`, chaves de API
- **Verifique .gitignore**: Antes do primeiro commit, garanta que existe um `.gitignore` adequado
- **Primeiro commit padrao**: O primeiro commit deve ser `chore: initial commit`
- **Foco no "why"**: A mensagem explica o motivo, o diff mostra o que mudou
- **Sem emojis**: A menos que seja padrao estabelecido do projeto

## Formato da Mensagem

### Estrutura Completa

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Componentes

| Componente | Obrigatorio | Descricao                              |
| ---------- | ----------- | -------------------------------------- |
| type       | Sim         | Categoria semantica da mudanca         |
| scope      | Nao         | Area do codigo afetada                 |
| subject    | Sim         | Descricao concisa no imperativo        |
| body       | Nao         | Contexto adicional e justificativa     |
| footer     | Nao         | Breaking changes, referencias a issues |

## Tipos de Commit

| Tipo     | Quando Usar                              | Exemplo                                   |
| -------- | ---------------------------------------- | ----------------------------------------- |
| feat     | Nova funcionalidade                      | `feat(auth): add OAuth2 login`            |
| fix      | Correcao de bug                          | `fix(api): handle null response`          |
| docs     | Apenas documentacao                      | `docs(readme): add setup instructions`    |
| style    | Formatacao, sem mudanca de logica        | `style: apply prettier formatting`        |
| refactor | Refatoracao sem mudanca de comportamento | `refactor(utils): simplify date parsing`  |
| perf     | Melhoria de performance                  | `perf(query): add database index`         |
| test     | Adicao ou correcao de testes             | `test(auth): add login unit tests`        |
| build    | Mudancas no build ou dependencias        | `build: upgrade webpack to v5`            |
| ci       | Configuracao de CI/CD                    | `ci: add GitHub Actions workflow`         |
| chore    | Tarefas de manutencao                    | `chore: update dependencies`              |
| revert   | Reverter commit anterior                 | `revert: revert "feat(auth): add OAuth2"` |

## Regras do Subject

- Use modo imperativo: "add" nao "added" ou "adds"
- Primeira letra minuscula
- Sem ponto final
- Maximo 50 caracteres (recomendado)
- Seja especifico mas conciso

### Bons Exemplos

- `feat(cart): add quantity validation`
- `fix(auth): prevent session timeout on refresh`
- `docs(api): document rate limiting headers`

### Maus Exemplos

- `feat: stuff` (vago demais)
- `Fixed the bug.` (passado, com ponto)
- `FEAT(AUTH): ADD LOGIN` (maiusculas)

## Regras do Body

- Separe do subject com linha em branco
- Explique o "porque" da mudanca
- Maximo 72 caracteres por linha
- Use para contexto que nao cabe no subject

### Exemplo com Body

```
fix(payment): handle currency conversion edge case

The previous implementation failed when converting between currencies
with more than 2 decimal places. This affected JPY and KRW transactions.

Added rounding logic to handle arbitrary decimal precision.
```

## Regras do Footer

### Breaking Changes

Mudancas que quebram compatibilidade devem incluir `BREAKING CHANGE:` no footer:

```
feat(api): change authentication endpoint

BREAKING CHANGE: The /auth/login endpoint now requires a JSON body
instead of form data. All clients must update their requests.
```

### Referencias a Issues

Use `Closes`, `Fixes`, ou `Resolves` para fechar issues automaticamente:

```
fix(upload): handle large file timeout

Closes #123
```

## Escopo (Scope)

O escopo e opcional mas recomendado para projetos maiores:

- Use nomes curtos e consistentes
- Represente modulos, componentes ou areas do codigo
- Mantenha uma lista de escopos validos no projeto

### Exemplos de Escopos

- `auth`, `api`, `ui`, `db`, `config`
- `cart`, `checkout`, `payment`, `user`
- `core`, `utils`, `tests`, `docs`

## Anti-patterns a Evitar

- **Commits gigantes**: Quebre em commits atomicos
- **Mensagens vagas**: "fix stuff", "update code", "wip"
- **Misturar tipos**: Um commit com feat + fix + refactor
- **Commits de merge desnecessarios**: Use rebase quando apropriado
- **Historico sujo**: Commits de "fix typo" repetidos

## Validacao

Considere usar ferramentas de validacao:

- **commitlint**: Valida formato das mensagens
- **husky**: Git hooks para validacao pre-commit
- **conventional-changelog**: Gera changelog automaticamente
