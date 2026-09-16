# 10: Offline + Sync

**What to build:** A local SQLite store on each client mirrors the user's library. Offline edits (highlights, notes, tags, reading progress, library state changes) sync to the server on reconnect via cursor-based delta sync. Conflicts are resolved deterministically with an explicit "preserve both" default for notes.

**Blocked by:** 02, 03

**Status:** ready-for-agent

- [ ] Local SQLite mirror of documents / highlights / notes / tags / reading progress / library state
- [ ] App remains usable offline: read, highlight, note, tag, change state
- [ ] Local full-text search over the cached subset (SQLite FTS5)
- [ ] Reconnect syncs via cursor-based delta
- [ ] Server exposes `POST /sync/changes?since=<cursor>` and `POST /sync/push`
- [ ] Two-device conflict test: divergent note edits → both versions preserved
- [ ] Two-device conflict test: highlight on one side, archive on other → both preserved
- [ ] Reading progress resolves to most recent meaningful value
- [ ] Idempotent re-import / re-push is safe (running twice does not duplicate)
- [ ] Airplane-mode test harness passes against a real client + server
- [ ] Tombstones for soft-delete so sync does not lose state
