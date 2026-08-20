## Entrega II — Organizador de Tarefas (Containerização + CI)

Este repositório contém a segunda entrega do projeto Organizador de Tarefas, com foco em containerização com Docker Compose e integração contínua com GitHub Actions.

A base do projeto é a extensão do Chrome desenvolvida na Entrega I, agora empacotada, testada automaticamente e executada em ambiente conteinerizado.

## Tecnologias Utilizadas

- Node.js 20
- Docker e Docker Compose
- Playwright (Chromium)
- GitHub Actions (CI/CD)

## Estrutura do Projeto

- `Dockerfile` → Cria o ambiente de build e teste da extensão

- `docker-compose.yml` → Orquestra o container de testes

- `scripts/build-extension.mjs` → Gera a pasta `dist/` e o arquivo `dist/extension.zip`

- `tests/` → Contém os testes automatizados (Playwright)

- `.github/workflows/ci.yml` → Pipeline de integração contínua

- `manifest.json`, `src/`, `icons/` → Arquivos da extensão do Chrome

## Como Executar o Projeto Localmente
## 1. Instalar dependências locais (opcional)

- Caso queira testar fora do container:

npm ci
npx playwright install --with-deps chromium
npm run build
npm run test:e2e

## 2. Rodar via Docker Compose (recomendado)

- Este método simula o ambiente usado no CI do GitHub.

docker compose build
docker compose run --rm tests


- Após os testes, o relatório HTML do Playwright será gerado automaticamente na pasta:

`playwright-report/`

## Como Entregar no GitHub

- Crie um repositório público com o nome do projeto (ex: Organizador-de-Tarefas).

- Envie todos os arquivos do diretório da entrega.

- Verifique se o workflow está dentro da pasta `.github/workflows/ci.yml`.

- Faça o commit e push para a branch main.

- Acesse a aba Actions no GitHub e verifique se o workflow foi executado com sucesso.

- O relatório de testes e o .zip da extensão serão gerados como artefatos do CI.

## Observações Finais

Os testes em `tests/extension.spec.ts` verificam se a interface do popup da extensão é carregada corretamente.

O pacote final da extensão é gerado em `dist/extension.zip`.

Caso precise ajustar seletores ou elementos do teste, é possível personalizar os arquivos em `tests/`.

O projeto foi desenvolvido de acordo com os requisitos da Entrega II do Bootcamp, contemplando containerização e integração contínua.

## Autor

Feito por Gustavo Barbosa para o Bootcamp II.
Meu GitHub: https://github.com/gustavob63
