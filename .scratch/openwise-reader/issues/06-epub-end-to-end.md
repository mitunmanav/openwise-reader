# 06: EPUB End-to-End

**What to build:** A user can upload an EPUB. It opens with cover, author, metadata, chapter structure, themes, typography controls, highlights (anchored by EPUB CFI where possible), bookmarks, notes, and exact position restoration via CFI.

**Blocked by:** 02

**Status:** ready-for-agent

- [ ] Upload EPUB via drag-drop or +Add
- [ ] Document opens with cover, author, metadata, and table of contents
- [ ] Theme controls (font family, size, line height, light/warm/dark) work
- [ ] Highlights use EPUB CFI for durable anchoring when the book supports it
- [ ] Highlights restore on reopen at the exact position
- [ ] Bookmarks persist and are visible from the notebook
- [ ] Notes persist and are visible in the notebook
- [ ] Reading progress is preserved across sessions and devices
- [ ] EPUB without CFI-friendly metadata falls back to quote + context anchoring
- [ ] Safe archive extraction (zip slip, symlink checks) is enforced on upload
