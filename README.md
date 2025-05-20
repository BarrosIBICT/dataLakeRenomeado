# 🐍 Guia de Commits com Conventional Commits para Projetos Python

## 🎯 Objetivo
Este guia define um padrão de mensagens de commit para melhorar a clareza, automatizar changelogs e facilitar a integração contínua com GitHub Actions em projetos Python.

---

## 📌 Formato Padrão
```
<tipo>[escopo opcional]: <descrição>
```

### ✅ Exemplo de mensagens boas para projetos Python:
```
feat(api): adicionar endpoint para listagem de usuários
fix(auth): corrigir bug de autenticação com token expirado
docs(readme): adicionar instruções de instalação do projeto
style(pep8): corrigir identação para seguir padrão PEP8
refactor(models): renomear classe User para AppUser
test(utils): adicionar testes para função de validação de CPF
chore: atualizar dependências no requirements.txt
ci(github-actions): adicionar passo de lint no workflow
```

---

## 🔠 Tipos mais comuns

| Tipo      | Descrição                                      |
|-----------|-----------------------------------------------|
| `feat`    | Nova funcionalidade                            |
| `fix`     | Correção de bugs                               |
| `docs`    | Alterações apenas em documentação              |
| `style`   | Formatação, sem alteração de lógica de código  |
| `refactor`| Refatoração sem correção ou nova funcionalidade|
| `test`    | Adição ou alteração de testes                  |
| `chore`   | Tarefas auxiliares (build, config, etc.)       |
| `ci`      | Mudanças no processo de integração contínua    |
| `build`   | Mudanças no sistema de build (ex: setup.py)    |

---

## 🚫 Más práticas a evitar
- Commits genéricos: `update`, `ajustes`, `teste`
- Commits sem contexto: `final`, `corrigido`
- Commits com muitas mudanças não relacionadas
- Mensagens vagas ou muito longas no título

---

## 🔧 Integração com GitHub Workflow

### 1. Validação com `commitlint`
Instalar dependências:
```
npm install --save-dev @commitlint/{config-conventional,cli}
```

Criar arquivo `commitlint.config.js`:
```js
module.exports = { extends: ['@commitlint/config-conventional'] };
```

### 2. Usar Husky para hooks Git:
```
npm install --save-dev husky
npx husky install
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit $1'
```

Adicionar no `package.json`:
```json
"scripts": {
  "prepare": "husky install"
}
```

---

## 🚀 Publicação automática com `semantic-release`

### 1. Instalar:
```
npm install --save-dev semantic-release
```

### 2. Criar `.releaserc.json`:
```json
{
  "branches": ["main"],
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    "@semantic-release/github"
  ]
}
```

### 3. Workflow GitHub `.github/workflows/release.yml`:
```yaml
name: Release

on:
  push:
    branches:
      - main

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Use Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npx semantic-release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

---

## 📄 Dica: Adicione este guia ao seu repositório

Recomenda-se adicionar este conteúdo em `COMMIT_CONVENTIONS.md` ou no `CONTRIBUTING.md` do projeto Python.

---

## 📈 Benefícios
- Histórico limpo e compreensível
- Geração automática de changelog
- Versionamento semântico padronizado
- CI/CD mais confiável
- Mais facilidade em revisões e auditoria
