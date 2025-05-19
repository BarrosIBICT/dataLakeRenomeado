
# Contribuindo para Este Projeto Python

Obrigado por considerar contribuir com este projeto! Todas as contribuições são bem-vindas, incluindo relatórios de bugs, solicitações de novas funcionalidades, melhorias na documentação e contribuições de código.

## Tabela de Conteúdos

- [Primeiros Passos](#primeiros-passos)
- [Código de Conduta](#código-de-conduta)
- [Como Contribuir](#como-contribuir)
- [Diretrizes de Desenvolvimento](#diretrizes-de-desenvolvimento)
- [Estratégia de Branches](#estratégia-de-branches)
- [Padrões de Mensagens de Commit](#padrões-de-mensagens-de-commit)
- [Processo de Pull Request](#processo-de-pull-request)
- [Padrões de Codificação](#padrões-de-codificação)
- [Testes](#testes)
- [CI/CD com GitHub Actions](#cicd-com-github-actions)

---

## Primeiros Passos

1. Faça um fork do repositório e clone-o em sua máquina local.
2. Configure um ambiente virtual:

```bash
python -m venv venv
source venv/bin/activate  # No Windows use `venv\Scripts\activate`
```

3. Instale as dependências:

```bash
pip install -r requirements.txt
```

## Código de Conduta

Leia e siga nosso [Código de Conduta](CODE_OF_CONDUCT.md) para manter a comunidade respeitosa e inclusiva.

## Como Contribuir

- **Relatórios de Bugs:** Use o GitHub Issues para reportar problemas. Inclua passos para reproduzir, comportamento esperado e comportamento observado.
- **Solicitações de Funcionalidades:** Abra uma Issue ou Discussão no GitHub para propor novas funcionalidades.
- **Contribuições de Código:** Siga o processo descrito abaixo para enviar um pull request.

## Diretrizes de Desenvolvimento

- Siga o padrão [PEP8](https://pep8.org/) usando `flake8`.
- Use o `black` para formatar o código automaticamente.
- Todo novo código deve incluir testes unitários.
- Escreva docstrings seguindo o [PEP 257](https://www.python.org/dev/peps/pep-0257/).
- Evite commits diretamente na branch `main`.

## Estratégia de Branches

- `main`: Código estável e pronto para produção.
- `dev`: Branch de desenvolvimento para novas funcionalidades e correções.
- `feature/<nome>`: Branches de funcionalidades, derivadas de `dev`.
- `bugfix/<nome>`: Branches de correções de bugs, derivadas de `dev`.

## Padrões de Mensagens de Commit

Siga o padrão [Conventional Commits](https://www.conventionalcommits.org/):

Exemplos:
- `feat: adicionar novo módulo de processamento`
- `fix: corrigir erro de divisão por zero`
- `docs: atualizar README com instruções de instalação`

## Processo de Pull Request

1. Faça um fork e clone o repositório.
2. Crie uma nova branch (`feature/minha-funcionalidade`).
3. Faça suas alterações e commits.
4. Envie para seu fork e crie um Pull Request para a branch `dev`.
5. Preencha o template de PR e certifique-se de que:
   - Todos os testes e verificações passaram.
   - O código está documentado.
   - Você adicionou ou atualizou os testes.

## Padrões de Codificação

- Use `black` para formatar o código: `black .`
- Verifique com `flake8`: `flake8 .`
- Checagem de tipos com `mypy`: `mypy .`
- Variáveis de ambiente devem ser gerenciadas via `.env` e `python-dotenv`.

## Testes

Usamos `pytest` para testes. Para rodar:

```bash
pytest
```

Certifique-se de que:
- Toda nova funcionalidade tem cobertura de testes.
- Use mocks e fixtures quando necessário.

## CI/CD com GitHub Actions

Nosso fluxo inclui:

- Linting com `flake8`
- Testes com `pytest`
- Checagem de tipos com `mypy`
- Formatação automática com `black`
- Scripts de deploy (se aplicável)

Todos os pull requests passam por essas verificações. Por favor, certifique-se de que estão passando antes de pedir uma revisão.

---

Obrigado por ajudar a melhorar este projeto!
