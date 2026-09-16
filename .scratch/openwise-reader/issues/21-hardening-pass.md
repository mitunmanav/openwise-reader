# 21: Hardening Pass (security, performance, accessibility, fixtures)

**What to build:** A focused hardening pass covering security review (SSRF, HTML sanitization, scoped tokens, content-type validation, file-size limits, archive extraction safety), performance to the scale targets (100k documents / 1M highlights), accessibility audit (WCAG 2.2 AA), and an expanded extraction fixture corpus.

**Blocked by:** 20 (and effectively every prior ticket)

**Status:** ready-for-agent

- [ ] Security review covers SSRF protection, HTML sanitization, scoped tokens, content-type validation, file-size limits, archive extraction safety, rate limiting, CSRF
- [ ] Performance audit against 100k documents / 1M highlights target (load times, search latency, sync throughput)
- [ ] Accessibility audit covers keyboard, screen reader, focus, contrast, touch targets, reduced motion, large text, dynamic text
- [ ] Reader remains usable at 200%+ zoom without horizontal scroll
- [ ] Fixture corpus expanded to cover blogs, news, docs, paywall stubs, broken HTML, multiple languages
- [ ] Anchor regression tests pass on DOM mutation fixtures (element moved, banner inserted, paragraph wrapped, same-quote-twice)
- [ ] Sync conflict tests pass on all enumerated scenarios (notes, archive, idempotent import, half-uploaded mutation)
- [ ] All critical and high bugs from the audit are closed
- [ ] Observability: structured logs, job states, basic metrics, no PII or document bodies in logs
- [ ] AGPL-3.0 license headers on every source file; trademark notice kept distinct from any third party
