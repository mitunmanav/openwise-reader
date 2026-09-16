# 09: Browser Extension (Chromium + Firefox)

**What to build:** A Chromium (MV3) and Firefox (WebExtension) extension that saves the current page in one click, highlights directly on the open web, attaches notes, detects already-saved URLs, and supports a keyboard shortcut. Falls back to DOM capture for login-walled content using the user's authorized browser session. Never uploads unrelated browsing data.

**Blocked by:** 02

**Status:** ready-for-agent

- [ ] Extension installs on Chrome and Firefox
- [ ] Click "Save" in the popup → current page saved (one click)
- [ ] Keyboard shortcut saves the current page (configurable)
- [ ] Extension popup shows whether the page is already saved (with link to the document)
- [ ] Highlighting directly on the open web creates a highlight on the saved document
- [ ] Attaching a note to a highlight from the same gesture works
- [ ] "Save to Later" button bypasses Inbox
- [ ] Fallback to DOM capture when public HTTP extraction fails (login-walled)
- [ ] No upload of unrelated browsing data; no form fields read; no page DOM exfiltrated beyond the user's saved selection
- [ ] Permissions declared in the manifest are minimal and documented
