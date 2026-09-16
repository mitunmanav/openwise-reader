# OpenWise Reader — Tickets

21 vertical slices. Worked frontier-first: any ticket whose blockers are all
done can start.

## Frontier at a glance

| # | Ticket | Blocked by |
|---|---|---|
| 01 | Foundation | — |
| 02 | Save URL → read → highlight → persist → search | 01 |
| 03 | Tags, notebook, library states | 02 |
| 04 | Daily review | 02, 03 |
| 05 | PDF end-to-end | 02 |
| 06 | EPUB end-to-end | 02 |
| 07 | RSS → Library | 02, 03 |
| 08 | Newsletter ingestion | 02 |
| 09 | Browser extension | 02 |
| 10 | Offline + sync | 02, 03 |
| 11 | Mastery cards + themed reviews | 04 |
| 12 | Imports (Kindle, Apple Books, Kobo) | 02, 03 |
| 13 | Exports (JSON, Markdown, CSV, OPML, Obsidian) | 02, 03 |
| 14 | Notion / Logseq / Roam | 13 |
| 15 | MCP server + public REST API | 02, 03 |
| 16 | AI (provider abstraction, document AI, chat with highlights, custom prompts) | 02, 03, 15 |
| 17 | TTS | 02 |
| 18 | Desktop shell (Tauri) | 02, 10 |
| 19 | Mobile shell (Expo) | 02, 10 |
| 20 | Self-host packaging (Docker Compose, backup/restore) | 18, 19 |
| 21 | Hardening pass | 20 |

## Parallelization after 01 + 02 land

The most parallelized window: once 02 (the central tracer bullet) is done,
~12 other tickets unlock at once and can be worked in parallel.

```
                ┌→ 03 (Tags, notebook, library states)
                │     ├→ 04 (Daily review)        ─→ 11 (Mastery)
                │     └→ 10 (Offline + sync)      ─→ 18 / 19 (Shells)
02 (Save→Read→  ├→ 05 (PDF)                              ─→ 18 / 19
  Highlight→    ├→ 06 (EPUB)                             ─→ 18 / 19
  Persist→      ├→ 07 (RSS → Library)                    ─→ 14 (Notion)
  Search)       ├→ 08 (Newsletter)                       ─→ 18 / 19
                ├→ 09 (Browser extension)                ─→ 18 / 19
                ├→ 12 (Imports)                          ─→ 18 / 19
                ├→ 13 (Exports)            ─→ 14 (Notion / Logseq / Roam)
                ├→ 15 (MCP + REST API) ─→ 16 (AI)
                └→ 17 (TTS)                              ─→ 18 / 19
```

## Working order

1. `/implement` ticket 01 (Foundation) — gets the monorepo, schema, server, web shell, FTS, CI green.
2. `/implement` ticket 02 (Save URL → read → highlight → persist → search) — the central tracer bullet.
3. Once 02 is green, work the frontier: any ticket with all blockers `Status: resolved` is grabbable.
4. Pick up dependent chains: 03 → 04 → 11; 03 → 13 → 14; 03 → 15 → 16; 10 → 18 → 20; 18 + 19 → 20; 20 → 21.
