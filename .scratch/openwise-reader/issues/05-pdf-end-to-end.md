# 05: PDF End-to-End

**What to build:** A user can upload a PDF (drag-drop or +Add). It opens in the in-app reader with page navigation, thumbnails, table-of-contents (where present), text search, highlights (with page number + PDF coordinates), reading position, and zoom. Scanned PDFs run OCR (Tesseract) on first open or per user preference. Original PDF remains downloadable.

**Blocked by:** 02

**Status:** ready-for-agent

- [ ] Upload PDF via drag-drop or +Add
- [ ] Document opens in pdf.js-based reader with page navigation and thumbnails
- [ ] Native-text PDF is full-text searchable across pages
- [ ] Scanned PDF runs Tesseract OCR on first open (or per user preference); OCR text is searchable
- [ ] Highlights record page number, text, and PDF coordinates
- [ ] Highlights restore on reopen at the exact page
- [ ] Original PDF is downloadable from the document
- [ ] Reading position (page + scroll) is preserved across sessions
- [ ] Zoom and rotation controls work
- [ ] OCR job failure does not block reading (PDF still opens with original view)
