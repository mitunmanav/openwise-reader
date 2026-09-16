# 07: RSS → Library

**What to build:** A user can subscribe to RSS/Atom feeds by URL, browse feed items as Unseen → Seen, and one-click save a feed item to the permanent Library. OPML import/export works. Feed items are stored separately from Library documents so RSS subscriptions do not pollute the permanent library.

**Blocked by:** 02, 03

**Status:** ready-for-agent

- [ ] Subscribe to RSS/Atom by URL (or discover from a website URL when possible)
- [ ] Feed items auto-poll on a configurable cadence (default every 30 minutes)
- [ ] Feed items appear as Unseen in the Feed view
- [ ] Opening a feed item marks it Seen
- [ ] "Save to Library" promotes a feed item to a Document in Inbox
- [ ] Feed folders / groups can be created
- [ ] Mute / unsubscribe work
- [ ] OPML import and export round-trip cleanly
- [ ] Full article content replaces excerpts where the source provides it
- [ ] Feed items are stored separately from Library Documents and don't pollute search by default (toggle in settings)
