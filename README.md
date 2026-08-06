# API Benchmark

API Benchmark is an MVP platform for registering APIs, triggering load tests with K6, tracking status in real time via SSE, and viewing basic performance metrics.

The project uses a monorepo with:
- a frontend built with Next.js
- a backend built with Express and TypeScript
- a PostgreSQL database managed with Prisma
- a processing queue powered by BullMQ and Redis
- a dedicated worker to execute benchmarks

The goal is to validate the full end-to-end flow of a load test in a simple local setup, without focusing on deployment or advanced features in the MVP.
