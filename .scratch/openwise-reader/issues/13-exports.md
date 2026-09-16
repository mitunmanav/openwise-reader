# 13: Exports (JSON, Markdown, CSV, OPML, Obsidian)

**What to build:** A user can one-click export their library in JSON, Markdown, CSV, or OPML. Original uploaded files are bundled. Obsidian export creates one Markdown file per source using a configurable template with safe incremental updates that never overwrite unrelated user edits.

**Blocked by:** 02, 03

**Status:** ready-for-agent

- [ ] One-click full export in JSON, Markdown, CSV
- [ ] OPML export for feeds
- [ ] Original uploaded files (PDF, EPUB, images, audio) are bundled in the export
- [ ] Obsidian export creates one `.md` per source with metadata, document note, highlights, notes, tags
- [ ] Configurable Obsidian template (Title, Author, Source URL, Metadata, Document note, Highlights, Highlight notes, Tags)
- [ ] Incremental update does not overwrite unrelated user edits in the vault (diff + skip-on-conflict)
- [ ] Export progress / failure surfacing works for libraries of 100k+ documents
- [ ] Export bundle is checksum-verified
