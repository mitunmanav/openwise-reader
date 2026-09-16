# 01: Foundation

**What to build:** A runnable monorepo with apps/server (Hono + Postgres), apps/web (React + Vite PWA), packages/database (migrations), packages/core (domain types), packages/api-client (typed client), packages/reader (placeholder), and the storage adapter interface. Server boots, web shell renders, full-text search round-trips against a smoke-test document, Docker Compose brings up Postgres for development, CI runs unit tests.

**Blocked by:** None (can start immediately)

**Status:** ready-for-agent

- [ ] `pnpm install` succeeds at the repo root
- [ ] `docker compose up -d` brings up Postgres + the server
- [ ] `pnpm dev` boots the server (port 4000) and the web (port 5173)
- [ ] A smoke-test user can be created via the API
- [ ] The web shell renders "OpenWise Reader" with theme support
- [ ] `pnpm test` runs unit tests green
- [ ] `packages/core` defines Document, Highlight, Note, Tag, User, Source, ReadingProgress types
- [ ] Postgres FTS works against a smoke-test document (round-trip)
- [ ] Storage adapter interface exists with filesystem + S3 implementations
- [ ] README, LICENSE (AGPL-3.0), SECURITY.md, CONTRIBUTING.md, CODE_OF_CONDUCT.md exist
