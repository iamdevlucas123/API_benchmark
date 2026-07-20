# API_benchmark — Plataforma de Testes de Performance de APIs (MVP)

Este repositório contém a Fase 1 (MVP) de uma plataforma para cadastrar APIs, executar testes de carga com k6 e visualizar métricas de performance.

Objetivo principal
- Permitir login, cadastro de APIs e endpoints, configuração e execução de testes com k6, armazenamento dos resultados em PostgreSQL e visualização de históricos e gráficos.

Stack (Fase 1)
- Frontend: Next.js (App Router), React, TypeScript, TailwindCSS, Clerk
- Backend: Node.js, Express, TypeScript, Prisma ORM
- Banco: PostgreSQL
- Infra: Docker Compose, NGINX (reverse proxy)
- Load testing: k6 (executado pelo backend via child_process)

Como rodar (desenvolvimento rápido)
1. Copie variáveis de ambiente de `.env.example` para `.env` e ajuste `DATABASE_URL`.
2. Construa e suba os serviços com Docker Compose:

```bash
docker compose up --build
```

Fluxo de execução (resumo)
- O usuário solicita a execução de um teste pelo frontend → o backend gera/gera o script k6 → executa k6 via `child_process` de forma síncrona → processa o JSON de saída → salva métricas no PostgreSQL → frontend consulta e exibe gráficos.

Estrutura mínima esperada

- apps/
	- web/    (Next.js)
	- api/    (Express + Prisma)
- prisma/   (schema e migrations)
- infra/
	- nginx/
- docker-compose.yml
- docs/     (contém `AGENTS.md` com requisitos e fluxo)

Requisitos importantes
- A execução de k6 será síncrona (sem filas/workers).
- Salvar métricas obrigatórias: média, p95, p99, máxima, requests/sec, total requests, total failures, tempo total.
- A aplicação deve ser implantável em uma única instância EC2 usando Docker Compose.

Onde ler a especificação
- Veja `docs/AGENTS.md` para o escopo completo, modelos de dados e fluxo de execução usados para planejar o desenvolvimento.

Próximos passos sugeridos
- Criar `docker-compose.yml` e `prisma/schema.prisma` → scaffold do backend básico → endpoints essenciais → scaffold do frontend mínimo.

Licença
- (Adicionar informação de licença, se aplicável.)

