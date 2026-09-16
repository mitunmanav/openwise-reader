# 15: MCP Server + Public REST API

**What to build:** A REST API (OpenAPI schema, API tokens with scopes, rate limits, clear versioning) and an MCP server exposing the read and write tool list from the spec. External integrations depend only on these surfaces.

**Blocked by:** 02, 03

**Status:** ready-for-agent

- [ ] REST endpoints: documents, highlights, notes, tags, feeds, reviews, search, imports
- [ ] OpenAPI schema published and versioned (`/openapi.json`, with a documented version field)
- [ ] API tokens are scoped (read:library, write:library, admin:*) and revocable
- [ ] Rate limits apply per token (with documented headers)
- [ ] MCP server exposes the read tool list (`search_library`, `search_highlights`, `get_document`, `get_document_content`, `get_highlights`, `get_recent_documents`, `get_daily_review`, `find_related_highlights`)
- [ ] MCP server exposes the write tool list (`save_url`, `create_note`, `create_highlight`, `add_tag`, `move_document`, `archive_document`)
- [ ] MCP responses include stable IDs and source references
- [ ] Destructive bulk write actions require explicit confirmation
- [ ] Authentication for both REST and MCP works
- [ ] Public docs site (e.g. Read the Docs) renders the OpenAPI and MCP tool surfaces
