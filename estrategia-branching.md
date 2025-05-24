
# 📘 Estratégia de Branching para Projetos com Python + Docker usando GitHub Flow

Este guia apresenta as melhores práticas para gerenciar branches em um projeto que utiliza Python, Docker e segue o modelo GitHub Flow.

---

## 🔀 Visão Geral do GitHub Flow

O GitHub Flow é um fluxo de trabalho leve baseado em branches que apoia a entrega contínua. Princípios principais:

1. A branch `main` está sempre pronta para produção.
2. Todo novo trabalho é feito em branches criadas a partir da `main`.
3. Crie um pull request (PR) para propor e discutir mudanças.
4. Obtenha revisões e aprovações de outros desenvolvedores.
5. Faça o merge da branch na `main` quando estiver pronta.
6. Faça o deploy imediatamente após o merge (ou via CI/CD).

---

## 🌿 Tipos de Branch

| Padrão de Nome da Branch | Propósito |
|--------------------------|-----------|
| `main`                   | Código pronto para produção (sempre estável e implantável) |
| `feature/<nome>`         | Novas funcionalidades ou melhorias |
| `bugfix/<nome>`          | Correções de bugs ou defeitos |
| `hotfix/<nome>`          | Correções urgentes diretamente na `main` |
| `refactor/<nome>`        | Melhorias ou limpezas no código (sem novas funcionalidades) |
| `test/<nome>`            | Testes ou experimentos |

---

## 🚀 Criando uma Nova Branch

Sempre crie a branch a partir da `main`:

```bash
git checkout main
git pull origin main
git checkout -b feature/nome-da-funcionalidade
```

---

## ✅ Checklist para Pull Request

Antes de abrir um PR:

- [ ] O código compila e roda corretamente (Python e Docker)
- [ ] Lint e formatação aplicados (ex: `black`, `flake8`)
- [ ] Testes unitários adicionados/atualizados
- [ ] Todos os testes passam localmente (`pytest`, `tox`, etc.)
- [ ] Docker build concluído com sucesso (`docker build .`)
- [ ] Descrição clara e objetiva do PR
- [ ] Relacionado a uma issue (se aplicável)

---

## 🔄 Mantendo sua Branch Atualizada

Mantenha sua branch sincronizada com a `main` para evitar conflitos:

```bash
git checkout main
git pull origin main
git checkout feature/nome-da-funcionalidade
git merge main
```

Ou utilize rebase, se preferir:

```bash
git fetch origin
git rebase origin/main
```

---

## 🧪 Testando com Docker Localmente

Garanta que sua branch está funcionando corretamente no Docker:

```bash
docker build -t minhaapp:dev .
docker run -it minhaapp:dev
```

---

## 🚨 Quando Usar `hotfix/`

Use branches `hotfix/` apenas para corrigir problemas urgentes em produção:

```bash
git checkout main
git pull origin main
git checkout -b hotfix/correção-urgente
```

Após corrigir e testar:

```bash
git checkout main
git merge hotfix/correção-urgente
git push origin main
```

Depois, crie um PR para merge nas demais branches se necessário.

---

## 📁 Exemplos de Nomes de Branch

- `feature/api-login`
- `bugfix/variaveis-ambiente`
- `refactor/limpeza-docker-compose`
- `hotfix/ajuste-seguranca-2025-05`

---

## 🧹 Deletando Branches Mescladas

Após o merge de uma branch, exclua-a para manter o repositório limpo:

```bash
# Localmente
git branch -d feature/nome-da-funcionalidade

# Remotamente
git push origin --delete feature/nome-da-funcionalidade
```

---

## 👥 Dicas de Colaboração

- Use PRs como rascunho para obter feedback inicial.
- Marque colegas no PR (`@usuario`).
- Mantenha os PRs pequenos e objetivos.
- Escreva mensagens de commit claras.
- Documente mudanças no `CHANGELOG.md`, se aplicável.

---

## 🛠 Ferramentas e CI Recomendados

- **Linters**: `flake8`, `pylint`, `black`
- **Testes**: `pytest`, `tox`
- **Docker**: `Dockerfile`, `docker-compose.yml`
- **CI/CD**: GitHub Actions ou outra ferramenta para build/test/deploy

---

## 🔚 Resumo

| Tarefa                   | Boa Prática                                  |
|--------------------------|-----------------------------------------------|
| Criar nova branch        | A partir da `main` com nome claro (`feature/...`) |
| Manter branch atualizada | Merge ou rebase com `main` regularmente       |
| Antes do PR              | Testar Python e Docker, seguir checklist      |
| Estratégia de merge      | Usar PRs e squash se necessário               |
| Após merge               | Deletar a branch                              |

---

Boas práticas e bons commits! 🐍🐳🚀
