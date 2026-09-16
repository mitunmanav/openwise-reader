# 12: Imports (Kindle, Apple Books, Kobo, generic)

**What to build:** A user can drag **My Clippings.txt** into the app and have Kindle highlights parsed with intelligent deduplication. Apple Books and Kobo adapters ingest user-provided exports or legitimate local-access paths. A generic CSV / JSON / Markdown / OPML import is supported via an import framework with preview (Found / New / Duplicates / Errors).

**Blocked by:** 02, 03

**Status:** ready-for-agent

- [ ] Drag-drop My Clippings.txt → highlights parsed into Documents + Highlights
- [ ] Re-importing the same file dedupes by document + text + location + context
- [ ] Apple Books import via exported files or a documented macOS helper where safe
- [ ] Kobo import via official export or local DB where appropriate
- [ ] Generic CSV / JSON / Markdown import with preview (Found / New / Duplicates / Errors)
- [ ] OPML import for feeds
- [ ] Import framework interface documented in `packages/importers/README.md`
- [ ] Failed records are exportable for retry without re-running the whole import
- [ ] 20,000-item import does not require restart on three failing records
