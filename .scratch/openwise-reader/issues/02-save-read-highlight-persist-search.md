# 02: Save URL → Read → Highlight → Persist → Search (web article end-to-end)

**What to build:** A web user can paste a URL into the global **+ Add** button; the URL is fetched and extracted into a clean article; the article opens in the in-app reader; the user can select text to create a highlight in one gesture; the highlight persists server-side; searching the article's full text returns the document and the highlight; reading position is restored on reopen.

**Blocked by:** 01

**Status:** ready-for-agent

- [ ] +Add button accepts a URL
- [ ] Article is fetched and extracted via Readability (Playwright worker fallback) into a Document
- [ ] Reader renders the article in a clean theme with table-of-contents and progress
- [ ] Selecting text creates a highlight in one gesture; highlight appears immediately
- [ ] Highlight persists server-side and re-appears on reopen at the exact location
- [ ] Global search returns the document and the highlight when a phrase from the article is searched
- [ ] Reading position is restored on reopen (approximate same place)
- [ ] Extraction failure surfaces honestly (no false success; "saved URL but couldn't extract clean article" pattern)
- [ ] At least one extraction golden-fixture test passes against `packages/extractors/__fixtures__/`
- [ ] Canonical URL is stored; redirect history is recorded
- [ ] Original HTML snapshot is preserved where the source allows
