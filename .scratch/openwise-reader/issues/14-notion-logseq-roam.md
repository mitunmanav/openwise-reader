# 14: Notion / Logseq / Roam Integrations

**What to build:** A user can OAuth-connect to Notion and sync documents, highlights, notes, and tags to a chosen workspace / page / database with one-way or two-way options. Logseq and Roam integrations use portable text with documented templates.

**Blocked by:** 13

**Status:** ready-for-agent

- [ ] Notion OAuth flow works
- [ ] User selects workspace / page / database
- [ ] Sync documents, highlights, notes, tags to Notion
- [ ] One-way vs two-way sync toggle with safety default (one-way by default)
- [ ] Duplicate detection prevents re-creating existing Notion pages
- [ ] Logseq integration: documented template + sync mechanism (outliner blocks)
- [ ] Roam integration: documented template + sync mechanism (block-level)
- [ ] Disconnection cleanly stops syncing without losing previously synced data
- [ ] Sync conflicts surface in the UI; no silent overwrites
