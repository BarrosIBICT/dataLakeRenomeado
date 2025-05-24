# Guia de Commits com Conventional Commits

## 🎯 Objetivo
Este guia define um padrão de mensagens de commit para melhorar a clareza, automatizar changelogs e facilitar a integração contínua no projeto ServiçosPI.

---

## 📌 Formato Padrão
```
<tipo>[escopo opcional]: <descrição>
```

### ✅ Exemplo de mensagens para commit:
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

## 🚫 Evite
- Commits genéricos: `update`, `ajustes`, `teste`
- Commits sem contexto: `final`, `corrigido`
- Commits com muitas mudanças não relacionadas
- Mensagens vagas ou muito longas no título

---



## 📈 Benefícios
- Histórico limpo e compreensível
- Geração automática de changelog
- Versionamento semântico padronizado
- CI/CD mais confiável
- Mais facilidade em revisões e auditoria
