# 08: Newsletter Ingestion (inbound email)

**What to build:** A user has a unique inbound email address. Forwarding a newsletter to that address creates a Library document with sender, subject, date, clean reader mode, and original HTML fallback. List-Unsubscribe metadata is shown when present and one-click usable. Inbound processing is idempotent (same Message-ID is never duplicated).

**Blocked by:** 02

**Status:** ready-for-agent

- [ ] Each user has a unique inbound email address visible in settings
- [ ] SMTP / inbound processing service can be configured by self-hosters
- [ ] Forwarding a newsletter to that address ingests it
- [ ] Ingested newsletter appears in the Library as a Document
- [ ] Sender, subject, and date are preserved on the Document
- [ ] Reader mode renders cleanly with images and links
- [ ] Original HTML fallback is accessible
- [ ] List-Unsubscribe header, when present, is shown and one-click usable
- [ ] Inbound email processor is idempotent (same Message-ID is not duplicated)
- [ ] Sender recognition: repeated senders can be auto-archived, muted, or labeled
