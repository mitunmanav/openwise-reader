# OpenWise Reader — Spec

Status: ready-for-agent

> Source spec authored by the user. Sections 1–91 of the originating product
> brief are the canonical reference. This document adds: (a) the problem/solution
> framing, (b) explicit user stories, (c) the binding implementation decisions,
> (d) the testing strategy, and (e) out-of-scope clarifications.

## Problem Statement

People who read seriously — across web articles, PDFs, books, newsletters, RSS,
and video — end up with their attention, highlights, and notes scattered across
five or six different products. Most of those products are paid, locked to a
single vendor, and own the user's data. None of them treat "read", "highlight",
"remember", and "find again later" as one coherent experience; instead the
reader and the highlight library live behind separate mental models and separate
price tags.

The user wants **one open-source application** that does the whole loop — save,
read, highlight, remember, find, export — without subscription lock-in, without
data hostage, and without splitting the experience into a "reader app" and a
"highlights app". The product should feel simple to a normal person on day one
and remain useful to a serious reader, researcher, student, writer, lawyer,
analyst, developer, or knowledge worker for years.

## Solution

**OpenWise Reader** is a single, unified, open-source product that holds
everything the user wants to read, everything they highlighted, and everything
worth remembering — in one library they control. The whole product reduces to
four actions: **Save**, **Read**, **Highlight**, **Remember**.

- One application, one library, one mental model. A document can contain
  highlights; a highlight always knows its source.
- One global search over every document, highlight, note, tag, OCR text, and
  transcript.
- One daily review surface for resurfacing highlights, decoupled from any
  proprietary algorithm.
- Open data: full export, no platform lock-in, self-hostable.
- AI is opt-in, BYO provider, and never required for the core loop.
- Offline-capable clients with deterministic sync.

## User Stories

The numbered list below is exhaustive for the scope of this spec. It is the
binding contract for what `/implement` will build. Each ticket produced by
`/to-tickets` will reference a contiguous range of these stories.

### Onboarding

1. As a new visitor on the web app, I want to sign up with email and password, so that I can start using OpenWise without external accounts.
2. As a new visitor on the web app, I want to sign up with a passkey, so that I don't have to manage a password.
3. As a new visitor, I want to skip the sign-up wizard and reach the app in one minute, so that I can decide later whether to commit.
4. As a new user on first run, I want to be asked one screen about what I want to read (articles, books/PDFs, newsletters/RSS, everything), so that the empty states are relevant without forcing a choice.
5. As a new user, I want to bring in one item immediately (URL, PDF/EPUB, Kindle import, or skip), so that I see the product working on real content.
6. As a new user reading my first item, I want to be taught highlighting through doing, not through a tutorial, so that I learn by using.
7. As a new user, I want to be told once that highlights will come back in a daily review, so that I understand the loop.

### Saving

8. As a reader, I want to paste a URL into a global **+ Add** field and have it saved in one step, so that I can capture without organizing.
9. As a reader, I want to drag a PDF, EPUB, or image file anywhere sensible on the page and have it ingested, so that capture is gesture-driven.
10. As a reader, I want to drop a folder of files and have each one ingested, so that bulk import is one action.
11. As a reader, I want to paste plain text or Markdown into **+ Add**, so that I can save quotes and excerpts without a source URL.
12. As a reader, I want to add an RSS/Atom feed URL, so that new items from that site arrive automatically.
13. As a reader, I want to import my existing read-later / highlights library (CSV, JSON, Markdown, OPML, Instapaper export, browser bookmarks), so that I don't lose history.
14. As a reader, I want an import preview showing found / new / duplicates / errors before commit, so that I don't silently create hundreds of duplicates.
15. As a reader, I want to add a document manually (title + author + body), so that I can capture book passages, lecture notes, and other non-URL sources.
16. As a mobile user, I want to use the OS share sheet to save URLs, files, and selected text, so that I can capture from any app.
17. As a desktop user, I want a system-wide "save to OpenWise" action, so that capture is one keystroke from any app.

### Web capture (browser extension)

18. As a browser user, I want to click one button in the extension popup to save the current page, so that capture takes one click.
19. As a browser user, I want a keyboard shortcut to save the current page, so that capture is muscle-memory.
20. As a browser user, I want the extension to show whether the current page is already saved, so that I don't create duplicates.
21. As a browser user, I want to highlight directly on the open web and have the highlight land in OpenWise with a source reference, so that I don't need to save first and re-find the page.
22. As a browser user, I want to attach a note to the highlight from the same gesture, so that capture is one continuous action.
23. As a browser user, I want a "Save to Later" button that bypasses the Inbox, so that I can triage by gesture.
24. As a browser user, I want the extension to fall back to capturing the rendered DOM when public HTTP extraction fails (login-walled content, JS-rendered pages), so that I can save pages I am authorized to see.
25. As a browser user, I want the extension to never upload unrelated browsing data, never capture passwords, and never read form fields I didn't touch, so that my privacy is preserved.
26. As a browser user on Firefox, I want the extension to install and behave identically, so that I'm not pushed to a browser.
27. As a browser user on Safari, I want the extension to install with appropriate limitations clearly explained, so that I know what works.

### Reading — general

28. As a reader, I want to open any document in a calm reader that is visually quieter than the source website, so that I can focus.
29. As a reader, I want to choose font family, font size, line height, margin width, and theme (light / warm / dark), so that I can read comfortably.
30. As a reader, I want the reader to follow my system theme by default, so that I don't flip manually.
31. As a reader, I want a focus mode that hides toolbars until I move the cursor, so that the chrome disappears.
32. As a reader, I want a reading progress indicator and an estimated remaining time, so that I can decide whether to start now.
33. As a reader, I want to click a position in the table of contents and jump there, so that navigation is direct.
34. As a reader, I want to close the app mid-sentence and reopen at the exact same position, so that I never search for where I stopped.
35. As a reader, I want reading progress to sync across all my devices within seconds, so that I can switch devices seamlessly.
36. As a reader, I want to read fully offline on any device that has the document cached, so that a plane doesn't stop me.

### Reading — web articles

37. As a reader, I want saved web articles to render in a clean reader view with the original images preserved, so that the article reads well.
38. As a reader, I want the original article HTML to be snapshotted where allowed, so that I have a fallback if the canonical page changes.
39. As a reader, I want publication metadata (title, author, publication, publish date, hero image, favicon, canonical URL) preserved on the document, so that I can cite it later.
40. As a reader, I want extraction failures to surface honestly ("we saved the URL but couldn't extract a clean article; retry or open original") instead of pretending success, so that I know what I'm working with.
41. As a reader, I want paywalled and login-walled pages to be capturable only through my own browser session via the extension, never through bypassing access controls, so that the product stays legal and ethical.

### Reading — PDF

42. As a reader, I want to upload a PDF and have it open in an in-app reader with page navigation and thumbnails, so that I don't need an external PDF viewer.
43. As a reader, I want native text PDFs to be searchable, so that I can find passages.
44. As a reader, I want scanned PDFs to be OCR'd on demand or automatically per preference, so that I can search and highlight them.
45. As a reader, I want a clean text view of a PDF alongside the rendered view, so that I can read long passages without page chrome.
46. As a reader, I want the original PDF download link preserved on the document, so that I can take the file elsewhere.
47. As a reader, I want table of contents extracted from PDF outline where present, so that I can navigate chapters.

### Reading — EPUB

48. As a reader, I want to upload an EPUB and have it open with its cover, author, metadata, and chapter structure, so that the book feels like a book.
49. As a reader, I want EPUB-native location identifiers to anchor my position, so that re-opening is exact even across devices.
50. As a reader, I want the same typography and theme controls as for web articles, so that I read consistently.
51. As a reader, I want bookmarks, highlights, and notes to persist inside the EPUB reading experience, so that the book is annotated.
52. As a reader, I want TTS to read from the current position in EPUB, so that I can listen while commuting.

### Reading — Markdown, plain text

53. As a reader, I want Markdown to render with proper formatting (headings, lists, code, blockquotes, tables), so that the source reads well.
54. As a reader, I want the original Markdown source preserved alongside the rendered view, so that I can copy it cleanly.
55. As a reader, I want plain text to render in a comfortable monospace-aware view, so that notes and clippings are readable.

### Reading — email newsletters

56. As a reader, I want a unique inbound email address per account, so that I can forward newsletters there.
57. As a reader, I want forwarded newsletters to land in my library as documents with sender, subject, and date preserved, so that I can read them in the app instead of my inbox.
58. As a reader, I want a clean reader mode for newsletters and a fallback HTML view, so that I see what was actually sent.
59. As a reader, I want unsubscribe metadata shown when present, so that I can opt out from the app.
60. As a reader, I want my newsletter email address to be discoverable but not guessable, so that I control who sends to it.

### Reading — RSS / feeds

61. As a reader, I want to subscribe to an RSS or Atom feed by URL, so that new entries arrive automatically.
62. As a reader, I want to discover feeds from a website when I paste a non-feed URL, so that subscribing is one click when possible.
63. As a reader, I want to organize feeds into folders or groups, so that my subscriptions are browsable.
64. As a reader, I want a feed to be muted without being deleted, so that I can pause it temporarily.
65. As a reader, I want unread/seen state per feed item, so that I don't re-read what I've seen.
66. As a reader, I want RSS excerpts to be replaced with full article content where the source provides it, so that I read the actual article, not a teaser.
67. As a reader, I want a feed item to be one-click savable into the permanent Library, so that feed browsing doesn't pollute the library.
68. As a reader, I want OPML import and export, so that I can move between readers.

### Reading — video

69. As a reader, I want to paste a YouTube URL and have the video open with its transcript beside it, so that I can read along while watching.
70. As a reader, I want clicking a paragraph in the transcript to seek the video to that moment, so that search is two-way.
71. As a reader, I want highlighting a transcript line to record the timestamp and store the highlight, so that I can find the moment later.
72. As a reader, I want available transcript languages to be selectable, so that I can read in the language I prefer.
73. As a reader, I want the video's official transcript used when the platform provides it, so that I'm not depending on unauthorized extraction.

### Reading — audio and images

74. As a reader, I want to upload an audio file and have it transcribed when I ask, so that I can search and highlight the content.
75. As a reader, I want to upload an image and have OCR run on it on demand or automatically per preference, so that I can search and highlight the text.
76. As a reader, I want mobile camera capture to OCR a page from a physical book, so that I can highlight without retyping.

### Highlights — general

77. As a reader, I want selecting text to instantly create a highlight with the smallest possible gesture, so that capture feels free.
78. As a reader on a touch device, I want to highlight with a long-press then tap, so that the gesture is natural.
79. As a reader on a tablet with a stylus, I want natural freehand-style highlighting where the platform permits.
80. As a reader, I want every highlight to record its source (document, URL, page or timestamp, surrounding context) so that I can always return to it.
81. As a reader, I want a highlight's text to never be silently rewritten or lost when the source page changes, so that my notes are durable.
82. As a reader, I want a highlight whose anchoring has been lost to appear in the document notebook with an "unresolved" marker rather than disappearing, so that I can repair or re-anchor by hand.

### Highlights — per content type

83. As a reader of web articles, I want highlights to survive small page changes (banner inserted, paragraph wrapped) because the system re-anchors using quote + context, so that my library is robust.
84. As a reader of PDFs, I want highlights to record page number, text, and PDF coordinates, so that I can return to the exact region.
85. As a reader of EPUBs, I want highlights to use EPUB CFI when possible, so that re-opening is exact.
86. As a reader of video transcripts, I want highlights to record start and end timestamps, so that I can seek back to the moment.

### Notes

87. As a reader, I want to attach a note to a specific highlight, so that I can annotate the exact passage.
88. As a reader, I want to attach a note to a whole document, so that I can record my overall reaction.
89. As a reader, I want to add a note while in the daily review, so that I can capture reactions in context.
90. As a reader, I want notes to be Markdown-compatible, so that I can use lists, links, and emphasis.

### Tags

91. As a reader, I want to add a tag to a document, so that I can organize without folders.
92. As a reader, I want to add a tag to a highlight, so that I can group ideas across documents.
93. As a reader, I want typing a tag to search existing tags first and let me create a new one inline, so that I don't pollute the vocabulary.
94. As a reader, I want to rename and merge tags, so that I can keep the vocabulary clean over time.

### Document notebook

95. As a reader, I want every document to have a Notebook panel showing its highlights, notes, headings, and tags, so that I have one place to see the document's annotations.
96. As a reader, I want to click a highlight in the notebook and jump to its position in the document, so that I can revisit context.
97. As a reader, I want to edit, copy, or delete a highlight from the notebook, so that I can manage annotations without losing source context.
98. As a reader, I want to export a single document's highlights and notes, so that I can share or archive.

### Library lifecycle

99. As a reader, I want every saved document to start in Inbox, so that I have an explicit "unprocessed" queue.
100. As a reader, I want to move a document from Inbox to Later (I want to read it) or to Archive (keep it, no longer needs attention), so that the library reflects my intent.
101. As a reader, I want to delete a document as a separate action from archiving, so that delete is irreversible and obvious.
102. As a reader who hates inbox triage, I want to collapse the default model to just Later → Archive, so that the system matches how I work.

### Feed lifecycle

103. As a reader, I want feed items to start as Unseen and become Seen when I open them, so that feed state is clean.
104. As a reader, I want a deliberate "Save to Library" action to promote a feed item, so that my permanent library is not auto-polluted by every RSS subscription.

### Saved views and filtering

105. As a reader, I want a visual filter builder over type, tag, author, source, date saved, date published, state, reading progress, has highlights, has notes, and unread, so that I can build views without learning syntax.
106. As a reader, I want to save a filter as a View and pin it, so that I can return to it.
107. As a power reader, I want an advanced textual query syntax underneath the visual builder, so that I can be expressive.
108. As a reader, I want common views pre-suggested (PDFs, Unread books, Research, Articles with highlights, Saved this week, From a specific publication), so that I can use them without building them.

### Search

109. As a reader, I want one global search box that searches titles, authors, source, document body, highlights, notes, tags, OCR text, and transcripts, so that I have one place to find anything.
110. As a reader, I want search to rank exact title matches first, then title + author, then highlights, then notes, then body, so that what I want surfaces quickly.
111. As a reader, I want typo-tolerant search where reasonable, so that near-misses still find things.
112. As a reader, I want search filters for type, date, author, tag, source, location/state, has highlights, and has notes, so that I can narrow.
113. As a reader, I want to be able to disable semantic search entirely, so that core search works with zero AI.
114. As a reader, I want optional semantic search via embeddings when I configure a provider, so that I can ask natural-language questions.

### Highlight library

115. As a reader, I want a dedicated view over all my highlights independent of documents, so that I can browse what I've learned.
116. As a reader, I want that view to filter by Books / Articles / PDFs / Videos / Newsletters / Manual highlights / Tags / Author / Source / Date, so that I can browse by category.
117. As a reader, I want clicking a highlight to show the highlight, its note, the source title and author, the location in the source, and surrounding context, so that I have what I need to remember it.
118. As a reader, I want a "View in Source" button that returns me to the exact source position when technically possible, so that I can re-read context.

### Daily review

119. As a reader, I want **Today's Review** to show me roughly five highlights one at a time, so that review is sustainable.
120. As a reader, I want the review to surface highlights that are worth revisiting, considering time since last review, my preferences, source frequency, manual pinning, novelty, past dismissal, and mastery state, so that the loop stays useful.
121. As a reader, I want each review item to support: Next, Save note, Tag, See context, Open source, See related, Remember this, More often, Less often, Never show again, so that I can act without friction.
122. As a reader, I want the review algorithm to be transparent and documented, so that I trust the loop.

### Review frequency

123. As a reader, I want to set review frequency globally, per document, per tag, and per highlight, so that I can tune the loop.
124. As a reader, I want friendly frequency choices (More often, Normal, Less often, Never), so that I don't have to learn scheduling.

### Mastery / active recall

125. As a reader, I want to mark a highlight as something I want to actively remember (a "Learn" or "Remember" action), so that it becomes part of my spaced practice.
126. As a reader, I want to create a cloze card that hides part of a highlight, so that I can practice recall.
127. As a reader, I want to create a question/answer card from a highlight, so that I can define my own prompts.
128. As a reader, I want an AI-generated card option that I can accept, edit, or reject, so that I can save time when I want to.
129. As a reader doing a recall session, I want Again / Hard / Good / Easy feedback that the system uses to schedule the next review, so that the loop adapts.

### Themed reviews

130. As a reader, I want to define custom review streams (e.g. "Writing", "Product Management", "Exam Revision"), so that I can study thematically.
131. As a reader, I want themed reviews to be configured by documents, authors, tags, types, or saved filters, so that the source is precise.
132. As a reader, I want themed review schedules (per-day, per-weekday, monthly), so that the cadence matches my study plan.

### Imports — Kindle

133. As a Kindle reader, I want to drag my `My Clippings.txt` into the app and have highlights parsed, so that I can preserve my Kindle library.
134. As a Kindle reader, I want Kindle imports to dedupe intelligently across runs, so that re-importing doesn't duplicate.
135. As a Kindle reader with the extension, I want to import highlights visible in my authenticated Kindle notebook without sharing my Amazon password with OpenWise, so that my credentials stay safe.

### Imports — Apple Books, Kobo, others

136. As an Apple Books user, I want to import highlights through legitimate means (exported files, email, or a local macOS helper where safe), so that I can consolidate.
137. As a Kobo user, I want to import highlights through official exports or my local device database where appropriate, so that I can consolidate.
138. As a reader with any other highlight source, I want an import framework that converts external data into the common Document / Highlight / Note / Tag / Location model, so that future importers are cheap.

### Physical books

139. As a reader of physical books, I want to take a photo with my phone, OCR the page, select a passage, and save the highlight, so that I capture without retyping.
140. As a reader of physical books, I want to record title, author, page, and a note, so that the source is reproducible.
141. As a reader of physical books, I want to search existing book entries before creating a duplicate, so that the library stays clean.

### Dedup

142. As a reader, I want documents arriving from different sources (extension, RSS, email, manual, import) to be deduplicated by canonical URL, normalized URL, title/domain/content hashes, and redirect history, so that the library is one entry per thing.
143. As a reader, I want highlights to be deduplicated by document identity, normalized text, location, and context, so that re-imports don't multiply.
144. As a reader, I want imports to be idempotent when possible, so that re-running an import is safe.

### Exports

145. As a reader, I want one-click complete export of my library and annotations, so that I can leave the product with my data.
146. As a reader, I want exports in JSON, Markdown, CSV, and OPML (where relevant), so that I can pick the format my destination accepts.
147. As a reader, I want original uploaded files preserved in the export, so that I take the binaries with me.
148. As a reader, I want each export to include metadata, so that the destination can interpret the data correctly.

### Obsidian integration

149. As an Obsidian user, I want one Markdown file per source written into a vault, so that the import is direct.
150. As an Obsidian user, I want a configurable template (Title, Author, Source URL, Metadata, Document note, Highlights, Highlight notes, Tags), so that the structure matches my vault.
151. As an Obsidian user, I want incremental append/update without overwriting my unrelated edits, so that I control my vault.
152. As an Obsidian user, I want an official plugin for safer sync where that improves the experience.

### Notion / Logseq / Roam

153. As a Notion user, I want an OAuth-connected workspace/page/database where documents, highlights, notes, and tags sync, so that I can use my existing knowledge base.
154. As a Notion user, I want to choose one-way vs two-way sync with the safety behavior clearly explained, so that I can pick what I trust.
155. As a Logseq / Roam / generic Markdown user, I want portable text exports with documented templates, so that my destination isn't locked out.

### Public API

156. As a developer, I want a REST API with API tokens, scopes, rate limiting, clear versioning, and an OpenAPI schema, so that I can integrate without scraping.
157. As a developer, I want endpoints for documents, highlights, notes, tags, feeds, reviews, search, and imports, so that the whole library is scriptable.

### MCP server

158. As an AI agent operator, I want an MCP server exposing read tools (`search_library`, `search_highlights`, `get_document`, `get_document_content`, `get_highlights`, `get_recent_documents`, `get_daily_review`, `find_related_highlights`), so that my agent can search the user's library safely.
159. As an AI agent operator, I want write tools (`save_url`, `create_note`, `create_highlight`, `add_tag`, `move_document`, `archive_document`) with explicit confirmation for destructive bulk actions, so that I can capture from the agent.
160. As an AI agent operator, I want MCP responses to include stable IDs and source references, so that the agent can cite.

### AI — optional and BYO

161. As a privacy-conscious reader, I want AI to be fully off by default, so that nothing leaves my device unless I enable a provider.
162. As a reader with a local model, I want to point OpenWise at an Ollama-compatible endpoint, so that I can use local AI.
163. As a reader with a cloud account, I want to provide an OpenAI-compatible API key through a settings page, so that I can use a hosted provider.
164. As a reader, I want the system to refuse to hard-code a single AI vendor, so that I can change providers without code changes.

### AI — document actions

165. As a reader, I want optional AI actions on a document: Summarize, Explain selection, Simplify selection, Define word, Translate, Expand concept, Extract key ideas, Extract action items, Generate questions, Generate flashcard, Ask document, so that I can deepen understanding.
166. As a reader, I want every AI answer to be grounded in the actual document text, with the ability to jump to the supporting passage, so that I trust the output.

### AI — chat with highlights

167. As a reader, I want to ask my library "what did I highlight about pricing?" and get an answer drawn from my real highlights, with each highlight exposed, so that I trust the answer.
168. As a reader, I want the AI to never pretend a highlight came from my library when it did not, so that I trust the loop.
169. As a reader, I want a "Chat with document" mode that scopes answers to the current document unless I explicitly expand scope, so that I don't get cross-document drift by accident.

### Custom AI prompts

170. As a power reader, I want to define reusable AI prompts scoped to word / selection / document / highlights / library, so that I can encode my own workflows.
171. As a power reader, I want prompt variables (document title, author, content, selection, highlights, notes, tags, user query) so that my prompts can be parameterized.

### Automatic AI

172. As a reader, I want optional auto-summary and auto-tag actions, off by default, so that I can enable them when I trust the provider.
173. As a reader, I want to see which provider/model an automatic action will use and (where possible) the actual usage, so that I control cost and trust.

### Related highlights

174. As a reader, I want a "Related" action on any highlight that surfaces conceptually or lexically related highlights, so that I can connect ideas across the library.
175. As a reader without embeddings enabled, I want related-highlights to fall back to strong full-text retrieval, so that the feature works without AI.

### Text-to-speech

176. As a reader, I want TTS to play / pause / seek / change speed / change voice on the current document, so that I can listen while commuting.
177. As a reader, I want TTS to start from the current reading position and synchronize highlighting of the spoken paragraph where practical, so that I can follow along.
178. As a reader, I want TTS to use system voices by default, with optional local or cloud voices through a provider, so that I don't pay for a vendor-locked TTS.

### Offline & sync

179. As a mobile reader on a plane, I want to open any document I previously downloaded, read it, highlight, add notes, tag, and update reading progress without connectivity.
180. As a multi-device reader, I want offline changes to synchronize when I reconnect, without losing any data.
181. As a multi-device reader, I want conflict resolution that is deterministic: notes preserve both sides if automatic reconciliation would lose data; tags merge; reading progress keeps the most recent meaningful value; highlights never disappear just because one device hasn't seen them yet.
182. As a power reader, I want airplane-mode editing to be tested aggressively, so that the loop is reliable.

### Mobile experience

183. As a mobile reader, I want bottom navigation (Home, Library, Review, Search) and a prominent Add action, so that capture is one thumb away.
184. As a mobile reader, I want reading to consume nearly the full screen, so that I can focus.
185. As a mobile reader, I want the OS share sheet to send URLs, files, and selected text into OpenWise.
186. As a mobile reader, I want camera-based OCR for physical books.
187. As a mobile reader, I want full offline reading, highlighting, notes, review, and search.

### Desktop experience

188. As a desktop reader on Windows, I want a first-class desktop app, not a tab in a browser.
189. As a desktop reader on macOS, I want a first-class desktop app.
190. As a desktop reader on Linux, I want an officially supported app.
191. As a desktop reader, I want drag-and-drop import, full keyboard navigation, a command palette, and local-file access, so that capture is fast.

### Keyboard and command palette

192. As a keyboard-first reader, I want shortcuts for Search, Add, Archive, Later, Highlight, Note, Tag, Open source, and the command palette, so that I don't touch the mouse.
193. As a keyboard reader, I want every shortcut to be optional — I can still do everything with the mouse / touch.

### Accessibility

194. As a reader using a screen reader, I want the entire UI to be navigable and announced correctly.
195. As a reader who needs large text, I want the reader to remain usable at large text sizes without horizontal scroll.
196. As a reader who needs reduced motion, I want the UI to respect that preference.
197. As a reader with motor impairment, I want all interactive elements to have visible focus, sufficient contrast, and reachable touch targets.

### Empty states, errors, progressive disclosure

198. As a new reader, I want every empty screen to tell me what it is, why I'd use it, and what I can do now (e.g. "Nothing to review yet. Highlight something while you read. Useful ideas will come back here later.").
199. As a reader, I want errors to be honest and specific, e.g. "We saved the page but couldn't extract a clean article. You can retry extraction or open the saved original."
200. As a normal reader, I want advanced features (filtered views, custom prompts, review tuning, API, MCP, custom exports, semantic search, self-host configuration) hidden until I want them, so that the app doesn't overwhelm me on day one.

### Platform integrity

201. As a reader, I want the system to never circumvent DRM, never acquire pirated ebooks, never bypass paywalls, and never capture content my browser session isn't authorized to see, so that the product stays legal and ethical.
202. As a reader, I want the platform integrations (Kindle, Apple Books, Kobo, YouTube, RSS, newsletters) to use official APIs, user exports, or browser data I'm authorized to access, so that the product stays reliable.

### Self-hosting and ownership

203. As a self-hoster, I want one command (`docker compose up -d`) to bring up the product, so that self-hosting isn't punishment.
204. As a self-hoster, I want a documented list of ports, volumes, database, storage, SMTP/email options, AI providers, backup, restore, and upgrade, so that I can deploy predictably.
205. As a reader, I want my data backed up and restorable, with backup that includes database, uploaded files, content snapshots, annotations, and configuration, so that I'm not hostage.
206. As a reader, I want one-click full export at any time, so that I can leave.

### Performance and scale

207. As a power reader with a 100,000-document / 1,000,000-highlight library, I want the app to remain responsive, so that scale doesn't ruin the product.
208. As a reader with a large library, I want pagination / cursors / virtualized lists / incremental indexing, so that the UI never blocks on data load.

## Implementation Decisions

These decisions are binding for the implementation. Any deviation must be justified in an ADR.

### Repository layout (monorepo)

```
openwise-reader/
├── apps/
│   ├── web/                 React + Vite + PWA
│   ├── desktop/             Tauri shell hosting the web build
│   ├── mobile/              Expo (React Native)
│   ├── extension/           WebExtension (MV3 for Chromium, WebExtension for Firefox)
│   └── server/              Node + TypeScript API + workers
├── packages/
│   ├── core/                Shared domain types and logic (no I/O)
│   ├── database/            Server-side PostgreSQL schema, migrations, query helpers
│   ├── api-client/          Typed REST + MCP client used by every client
│   ├── reader/              Reader UI primitives and per-type renderers (web / PDF / EPUB / video / email / text)
│   ├── ui/                  Shared React UI primitives (theme, command palette, dialog, list virtualization)
│   ├── importers/           One adapter per import source (Kindle, Apple Books, Kobo, Instapaper, generic CSV/JSON/MD/OPML)
│   ├── exporters/           One adapter per export target (JSON, Markdown, CSV, OPML, Obsidian, Notion, Logseq, Roam)
│   ├── sync/                Cursor-based delta sync protocol and conflict resolution
│   └── mcp/                 MCP server + tool definitions
├── docs/
│   ├── agents/              (already created)
│   ├── adr/                 Architecture decision records (created lazily)
│   └── architecture/        Diagrams and protocol docs
├── .scratch/                Specs + tickets (local tracker)
├── AGENTS.md
├── README.md
├── LICENSE                  AGPL-3.0
├── SECURITY.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── docker-compose.yml
```

Rationale: the apps-vs-packages split keeps deployable surfaces (apps) separate
from reusable libraries (packages). Per section 60 of the originating brief.

### Stack picks

| Surface | Stack | Reason |
|---|---|---|
| Server runtime | Node 22 LTS, TypeScript strict | Best ecosystem for the integrations required (MCP, RSS, AI SDKs). |
| HTTP framework | Hono | Lightweight, fast, edge-friendly, first-class OpenAPI via `@hono/zod-openapi`. |
| Validation | Zod | Shared schemas between server, clients, and MCP. |
| Database | PostgreSQL 16 | Required by section 47 ("boring infrastructure"). |
| Full-text search | PostgreSQL `tsvector` | Built-in; no Elasticsearch. |
| Embeddings (optional) | `pgvector` | When enabled; otherwise disabled. |
| Background jobs | `pg-boss` (database-backed) | Avoids Redis; survives server restarts. |
| Object storage | Filesystem adapter (default) + S3-compatible adapter | Section 49: self-host without buying a service. |
| Content extraction | `@mozilla/readability` (primary) + Playwright worker (fallback) + extension DOM capture (login-walled) | Section 7 layered pipeline. |
| PDF | `pdf.js` for render; `tesseract.js` for OCR | Mature, offline-capable. |
| EPUB | `epub.js` | De-facto in-browser EPUB renderer. |
| Markdown | `unified` + `remark` + `rehype` | Extensible; same parser across surfaces. |
| TTS (web) | Web Speech API (default), optional cloud/local provider | No vendor lock. |
| TTS (mobile / desktop) | Native platform APIs | Per-platform quality. |
| MCP | `@modelcontextprotocol/sdk` (official TypeScript SDK) | First-class. |
| Auth | Sessions via `better-auth` (self-host-friendly) + optional passkeys (SimpleWebAuthn) + optional OAuth | Section 56. |
| Sync | Cursor-based delta sync using `updated_at` + monotonic server cursors; tombstones for soft-delete | Section 45. |
| Local DB (clients) | SQLite via `op-sqlite` (mobile) / `better-sqlite3` (desktop) / `sql.js` (web) | Section 46. |
| Local FTS | SQLite FTS5 | Section 48. |
| WebExtension | MV3 (Chromium) + WebExtension API (Firefox); shared core via the browser action | Section 8. |
| Desktop | Tauri 2 | Lighter than Electron; Rust core. |
| Mobile | Expo (React Native) | Cross-platform, share code with web. |

Justified deviations from "vanilla" picks are recorded as ADRs in `docs/adr/`.

### Domain model (server-side, relational)

The canonical entities below are persisted as tables. JSON is used only for
genuinely source-specific metadata (e.g. raw extension capture payload).

```
User
Device
Document
DocumentVersion        (snapshots of source HTML / extracted content)
DocumentContent        (current canonical content for the reader)
DocumentFile           (binary: PDF, EPUB, image, audio, snapshot)
Source                 (URL or file path or email-message-id)
Author
Feed
FeedSubscription
FeedItem
Highlight
HighlightAnchor        (per-type selector: web/PDF/EPUB/transcript)
Note                   (scope: highlight | document | review)
Tag
DocumentTag
HighlightTag
ReadingProgress        (per device, per document)
ReviewSchedule         (per highlight, plus aggregate settings)
ReviewEvent            (log of past reviews)
MasteryCard            (cloze or QA card referencing a highlight)
ImportJob              (status, counts, error report)
ExportJob              (status, output)
Integration            (Obsidian vault path, Notion OAuth, etc.)
ApiToken               (hashed)
SyncMutation           (idempotent log for delta sync)
AIConfiguration        (provider, model, per-feature toggle)
EmailAddress           (per-user inbound newsletter address)
```

Schema lives in `packages/database/migrations/` and is migrated via a checked-in
CLI; migrations are forward-only and reversible only via a paired "down" migration
that the CI refuses if data would be lost without an explicit override.

### Sync protocol

- Every mutable entity carries `id`, `created_at`, `updated_at`,
  `version` (monotonic per-row counter), and `deleted_at` (tombstone).
- Each device maintains a local mutation queue.
- Server exposes:
  - `POST /sync/changes?since=<cursor>` — server delta since cursor
  - `POST /sync/push` — accept idempotent mutations from the device
- Conflicts:
  - Notes: keep both versions if reconciliation would lose content.
  - Tags: set-merge.
  - Reading progress: most recent meaningful value wins.
  - Highlights: never delete one side because another client hasn't seen it.
- Test harness: two simulated devices with offline → online → divergent
  edits → reconnect.

### Ingestion pipeline (server-side)

Single conceptual pipeline used by every entry path (URL, file, email, RSS,
import). Each step is independently observable and retryable.

```
SOURCE
  → fetch / receive
  → identify type
  → parse (per-type adapter)
  → normalize
  → extract metadata
  → extract text
  → optional OCR / transcription
  → dedupe (canonical URL, content hash, redirect history)
  → index (PostgreSQL FTS)
  → store (Document, DocumentContent, DocumentFile)
  → ready
```

Failures are isolated: a failed OCR doesn't block reading; a failed AI
summary doesn't block ingest; a failed extraction is reported honestly.

### Job system

Backed by `pg-boss`. Each job has:

- Stable ID
- Status (`pending`, `running`, `succeeded`, `failed`, `dead`)
- Attempt count
- Last error (structured)
- Timestamps
- Retry policy (exponential backoff, max attempts)

UI surfaces job state as `Processing` / `Ready` / `Failed — Retry`.

### Content extraction (seam)

The extraction layer is a server-side module behind a single interface:

```ts
interface ContentExtractor {
  extract(input: ExtractInput): Promise<ExtractResult>;
}

type ExtractInput =
  | { kind: 'url'; url: string; userId: UserId; viaExtensionDom?: ExtensionDom }
  | { kind: 'file'; fileId: FileId }
  | { kind: 'email'; messageId: string }
  | { kind: 'feed-item'; feedItemId: string };

type ExtractResult =
  | { ok: true; document: DocumentDraft }
  | { ok: false; reason: 'no-content' | 'paywall' | 'unauthorized' | 'unsupported' };
```

Implementations:
1. `ReadabilityExtractor` — `@mozilla/readability` for normal pages.
2. `RenderedBrowserExtractor` — Playwright worker for JS-heavy pages.
3. `ExtensionDomExtractor` — for content captured by the user's authenticated browser.
4. `FileExtractor` — for PDFs (pdf.js + optional Tesseract), EPUBs, MD, text.
5. `EmailExtractor` — for forwarded newsletters.

### Reader (client-side)

The reader is a single React component that selects a renderer based on
`Document.kind`:

```ts
type Renderer =
  | WebRenderer          // article HTML
  | PdfRenderer          // pdf.js
  | EpubRenderer         // epub.js
  | MarkdownRenderer     // unified/remark
  | PlainTextRenderer
  | EmailRenderer        // raw + clean reader mode
  | VideoRenderer        // <video> + transcript with seek-on-click
  | AudioRenderer
  | ImageRenderer        // <img> + optional OCR overlay
```

Themes (light / warm / dark / system) are tokenized and shared across web,
desktop, mobile, and extension where applicable.

### Highlighting & anchoring

Anchor strategy is per content type but uniformly exposed through:

```ts
type HighlightAnchor =
  | WebAnchor            // quote, prefix, suffix, xpath, character offsets
  | PdfAnchor            // page, text, quads
  | EpubAnchor           // CFI + quote fallback
  | TranscriptAnchor     // text, start_ms, end_ms
  | TextAnchor;          // character offsets
```

Anchoring is re-validated when a document is reopened. Failed re-anchors
move the highlight to an `unresolved` state rather than deleting it.

### Search

- Server: PostgreSQL `tsvector` indexes on Document, Highlight, Note, OCR text,
  Transcript. Ranking: title > title+author > highlight > note > body.
- Client (offline): SQLite FTS5 over the locally cached subset.
- Optional semantic: embeddings stored via `pgvector` (server) or
  `sqlite-vss` (client). Disabled by default. Core search works with AI off.

### AI

- Provider abstraction (Vercel AI SDK) with these backends:
  - Disabled
  - Ollama-compatible
  - OpenAI-compatible (BYO key)
  - User-defined HTTP endpoint
- No automatic AI without explicit user toggle per feature.
- AI provider configuration is per user; never global.
- AI responses for document chat must cite the supporting passage via anchor.
- AI chat with highlights must show the highlights used.

### MCP server

Exposed tools (read):
- `search_library(query, filters?)`
- `search_highlights(query, filters?)`
- `get_document(id)`
- `get_document_content(id)`
- `get_highlights(documentId?)`
- `get_recent_documents(limit?)`
- `get_daily_review()`
- `find_related_highlights(highlightId)`

Exposed tools (write):
- `save_url(url)`
- `create_note(target, body)`
- `create_highlight(documentId, anchor, note?)`
- `add_tag(target, tag)`
- `move_document(documentId, state)`
- `archive_document(documentId)`

All destructive bulk actions require explicit confirmation.

### Storage

- Server binaries live outside PostgreSQL rows in object storage (filesystem
  default, S3 adapter optional).
- Checksums (SHA-256) stored per file.
- Self-hosters can point the storage adapter at S3-compatible endpoints.

### Auth

- Self-host: local email + password (bcrypt or argon2), passkeys via SimpleWebAuthn.
- Hosted: same, plus optional OAuth (Google, Apple, GitHub) — never required.
- Sessions are server-issued, HTTP-only, secure, SameSite=Lax.
- CSRF tokens on state-changing routes.
- API tokens are scoped (read:library, write:library, admin:*) and revocable.

### Privacy

- Documents and highlights never sent to AI providers unless the user
  explicitly enables that provider and the relevant feature.
- Logs never contain document bodies or highlights.
- API tokens stored hashed.
- The AI settings page shows exactly what leaves the device per feature.

### Security

- Server-Side Request Forgery protection on URL fetches (deny private IP ranges,
  deny localhost unless explicitly opted in for self-hosted testing).
- HTML sanitization on all incoming article content (DOMPurify server-side).
- File uploads: content-type sniffing + size limits + checksum + safe storage path.
- Rendered-browser extraction workers run in sandboxed subprocesses with no
  filesystem access to the rest of the server.
- Scoped API tokens with rate limits.
- Safe archive extraction (zip slip, symlink checks) for EPUBs and imports.

### Observability

- Structured JSON logs.
- Per-job state surfaced in UI.
- `/healthz` (liveness), `/readyz` (readiness), `/metrics` (basic Prometheus).
- Self-host diagnostics page listing recent ingest / sync / feed / OCR failures.

### Frontend architecture

- React + Vite for web; React Native via Expo for mobile; Tauri shell for desktop.
- Reader UI primitives live in `packages/reader`.
- Shared UI primitives in `packages/ui` (theme, dialog, command palette,
  virtualized list).
- Server state is fetched via `api-client`; client-side state via TanStack Query.
- Optimistic UI for highlight creation (does not block on network).

### Open-source posture

- License: AGPL-3.0 (per the originating brief).
- Trademarks/branding kept distinct from third parties.
- Repository MUST contain: README, LICENSE, SECURITY.md, CONTRIBUTING.md,
  CODE_OF_CONDUCT.md, architecture docs, self-host docs, developer setup,
  backup/restore docs, API docs.
- Public OpenAPI schema published.

## Testing Decisions

Test pyramid, ordered highest-seam-first:

### End-to-end (Playwright)

Tests run against the highest seam — the full HTTP API + the web app — driving
the acceptance test in section 90 of the originating brief verbatim, plus the
specific journeys below. Each test creates a fresh server with seeded fixtures
and asserts visible user-facing outcomes.

- Save URL → read → highlight → note → reopen → position preserved → search
  finds highlight → review surfaces it.
- Upload PDF → OCR if scanned → highlight → reopen → highlight restored.
- Upload EPUB → highlight → reopen → position restored via CFI.
- Subscribe RSS → feed item appears Unseen → Save to Library.
- Forward newsletter → document appears in Inbox.
- Import `My Clippings.txt` → duplicates detected → report shown.
- Export → JSON readable; Obsidian Markdown matches template.
- Offline edit → reconnect → no data lost.
- MCP tool call → returns highlights with stable IDs and source refs.
- Disable AI → core flow still works.

### Integration

- HTTP API contract (Hono + OpenAPI + generated client, round-trip).
- Sync: two simulated devices, divergent edits, deterministic reconciliation.
- Extraction: golden fixtures covering blogs, news, documentation, paywall
  stubs, broken HTML, lazy-loaded content, code blocks, tables, multiple
  languages, embedded media.
- PDF extraction: native text PDF + scanned PDF + OCR.
- EPUB extraction: chapters, metadata, CFI generation.
- Email ingestion: forwarded-message parsing.
- Feed ingestion: RSS, Atom, OPML import/export.
- Storage adapter: filesystem + S3 round-trip with checksum.
- AI provider adapter: mock provider asserting the same input produces the
  same tool call shape across providers.

### Unit

- URL normalization, canonicalization, redirect resolution.
- Dedupe hashing and ranking.
- Highlight anchor re-anchoring on DOM mutations.
- Review scheduling (transparent algorithm; documented tests).
- Sync conflict resolution.
- Markdown / HTML / EPUB CFI parsing.
- Tag rename / merge.
- Permissions and scoped API tokens.

### Definition of done per capability

A feature is **done** when:

1. The user-facing path works end-to-end.
2. Expected failure states work and surface honestly.
3. Tests pass (unit + integration + relevant e2e).
4. Data survives restart.
5. Sync behavior is checked where relevant.
6. Accessibility basics work (keyboard, screen reader, focus, contrast, zoom).
7. Docs are updated.
8. No known critical bug remains.

### Test corpus

A `packages/extractors/__fixtures__/` directory holds:

- Diverse HTML pages (blog, news, docs, long essays, code, tables, images).
- Lazy-loaded pages.
- Paywall/login stubs (only used to assert behavior when the page IS the
  user's authorized browser via extension capture).
- Broken HTML.
- Multiple languages.
- PDFs (native text, scanned, multi-column).
- EPUBs (with and without CFI-friendly metadata).
- OPML files.
- `My Clippings.txt` examples.
- Email newsletter samples.

Golden expected outputs are stored as JSON in the same directory and asserted
against. Extraction regressions are product regressions.

### Anchoring tests (specific)

DOM mutation fixtures:

- Element moved in tree.
- Paragraph wrapped differently.
- Extra banner inserted.
- Minor text edit.
- Article re-rendered.
- CSS classes randomized.
- Same quote appearing twice.

The system must use context to recover the correct occurrence. If
uncertain, the highlight moves to `unresolved` rather than attaching to the
wrong passage.

### Sync tests (specific)

- Device A offline; Device B online; both edit a note; A reconnects → both
  versions preserved.
- A adds a highlight; B archives the document; A reconnects → highlight and
  archive preserved.
- Same import executed twice → idempotent.
- Network dies halfway through an upload → no user data lost.

## Out of Scope

The following are explicitly **not** part of this spec, either because the
originating brief rules them out or because they are misaligned with the
product principle.

- **DRM circumvention** of any kind (ebooks, video, PDFs).
- **Pirated ebook acquisition** or "free book" sources of dubious provenance.
- **Paywall bypass** of any kind.
- **Credential theft** — no logging in with a user's third-party password.
- **Unauthorized private-content scraping** — only user-authorized browser
  capture is permitted for login-walled content.
- **Collaboration / team wiki / shared libraries** — single-user per account.
- **Public follower / social network features.**
- **Kanban / project management / database-as-pages** — Notion-clone features.
- **Generic document editor** beyond reader needs.
- **Graph view by default** — discoverable later, not first-class.
- **Public API write scopes that can mass-delete** without explicit
  confirmation.
- **Hosted-only features** — anything in the spec must work on a self-hosted
  single-user install unless explicitly flagged otherwise.
- **Vendor lock-in** — no integration may require a specific commercial
  product (other than user-provided API keys).

## Further Notes

### License

AGPL-3.0. Trademarks and branding distinct from any third party.

### Acceptance test

Section 90 of the originating brief is the **binding definition of done** for
the whole product. `/to-tickets` will produce vertical-slice tickets that, in
aggregate, complete that acceptance test.

### Vertical-slice ordering

Tickets are produced to maximize that every slice ends in working software
(originating brief, section 87). The implicit ordering below is the default
unless an ADR justifies a change. Each slice is a complete user path:

1. **Foundation**: monorepo, schemas, server skeleton, web skeleton, FTS,
   local store stub.
2. **Save a URL → read → highlight → persist → search** (web article end-to-end).
3. **Tags, notebook, library states** (Inbox / Later / Archive).
4. **Daily review** (lexical selection only; no embeddings yet).
5. **PDF end-to-end** (upload, OCR for scanned, highlight, search).
6. **EPUB end-to-end** (upload, CFI anchoring, resume).
7. **RSS → Library** (subscribe, unseen → seen, save-to-library).
8. **Newsletter ingestion** (inbound email).
9. **Browser extension save + highlight** (extension on top of slice 2).
10. **Offline + sync** (local store, delta sync, conflict tests).
11. **Mastery cards + themed reviews** (transparent FSRS-style scheduler).
12. **Imports** (Kindle `My Clippings.txt`, then Apple Books / Kobo adapters).
13. **Exports** (JSON, Markdown, CSV, OPML, Obsidian).
14. **Notion / Logseq / Roam** integrations.
15. **MCP server** + public REST API.
16. **AI** (provider abstraction, document AI, chat with highlights, custom
    prompts; all opt-in).
17. **TTS**.
18. **Desktop (Tauri)** shell + mobile (Expo) shell around the same web build.
19. **Self-host packaging** (Docker Compose, backup/restore).
20. **Hardening pass** (security review, performance to scale targets,
    accessibility audit, fixture corpus expansion).

### Risk register

- **Content extraction regressions** are the highest-risk single failure mode.
  Mitigation: golden fixtures + per-PR extraction diffs.
- **Sync conflicts** can silently lose user data. Mitigation: aggressive
  airplane-mode tests; preservation-over-resolution defaults.
- **AI cost** can run away. Mitigation: explicit user toggles, usage surfacing.
- **Self-host complexity** can erode trust. Mitigation: `docker compose up -d`
  as the canonical entry point; documented backup/restore.
- **Anchor drift** in long-lived web highlights. Mitigation: quote + context
  re-anchoring, unresolved state, never silent deletion.

### Open questions

None at this time. The spec is binding; deviations are recorded as ADRs.
