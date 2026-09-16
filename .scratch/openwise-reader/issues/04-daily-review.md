# 04: Daily Review (lexical selection, no embeddings)

**What to build:** Home → **Today's Review** shows roughly five highlights one at a time. Selection considers time since last review, user frequency preference, source frequency, manual pinning, novelty, past dismissal, and mastery state. Each item exposes Next, Save note, Tag, See context, Open source, See related, Remember this, More often, Less often, Never show again. The algorithm is documented and unit-tested.

**Blocked by:** 02, 03

**Status:** ready-for-agent

- [ ] Home shows a **Today's Review** card
- [ ] Tapping Today's Review opens a one-at-a-time review surface
- [ ] ~5 highlights per session (configurable in settings)
- [ ] Each item shows the highlight, source title, and author
- [ ] Next advances; Open source returns to the exact source position
- [ ] Save note, Tag, See context, Remember this, More/Less often, Never show again all work
- [ ] Highlights marked "Never show again" never reappear
- [ ] Per-highlight "More/Less often" affects future selection
- [ ] Selection algorithm is documented in `docs/review/algorithm.md` and unit-tested
- [ ] Manual pinning exists (a way to surface a specific highlight in the next review)
