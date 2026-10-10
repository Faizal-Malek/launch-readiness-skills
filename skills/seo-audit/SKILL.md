---
name: seo-audit
description: >-
  Run a 20-point SEO / discoverability audit for vibecoded or shipped websites
  (sitemap, robots, meta, headings, schema, CWV, OG, Search Console, llms.txt).
  Use before launch, after marketing site changes, or when organic search /
  social previews matter—not for AppSec or de-AI visual restyles.
---

# SEO Audit — 20 checks for a vibecoded website

Audit the site (code, routes, and public HTML) against this checklist. Detect stack (Next, Vite, Astro, etc.) and point to the files that should own each fix. Detect-only by default; apply fixes when the user asks.

Not for: security hardening ([production-readiness](../production-readiness/SKILL.md)), or UI taste / de-AI ([ux-audit](../ux-audit/SKILL.md) / Taste skills).

Reference: Project media `seo-20-checks.jpg` (“20 SEO checks… give this checklist to Claude”).

---

## The 20 checks

### Crawl & indexability
1. **Build `sitemap.xml`** — Present, linked, covers public routes; regenerate on deploy.
2. **Add `robots.txt`** — Allows intended crawl paths; does not block CSS/JS needed for rendering; points to sitemap.
3. **Remove `noindex` tags** — Public pages must not ship `noindex` (meta or header) by accident.
4. **Add canonical tags** — One preferred URL per page; avoid duplicate `/` vs non-`/`, query variants, preview hosts.

### Metadata & semantics
5. **Add meta titles** — Unique, descriptive `<title>` per page (~50–60 chars intent).
6. **Meta descriptions** — Unique summaries for SERP snippets (~150–160 chars); no boilerplate duplicates.
7. **One H1 per page** — Single primary heading matching the page job.
8. **Fix heading order** — Logical H1 → H2 → H3; no skipped levels for style.
9. **Add alt text** — Meaningful `alt` on content images; empty `alt=""` only for pure decoration.
10. **Add schema markup** — Relevant JSON-LD (Organization, WebSite, Article, Product, FAQ, etc.).

### Structure & content graph
11. **Add internal links** — Important pages reachable from nav/body; no orphan marketing routes.
12. **Fix broken links** — No 404s in nav, footer, or body; check redirects.

### Performance & UX (SEO-facing)
13. **Compress images** — Modern formats (WebP/AVIF), sensible dimensions, lazy-load below fold.
14. **Core Web Vitals** — LCP, INP/FID, CLS within good thresholds; flag layout shift and huge heroes.
15. **Fix mobile layout** — Usable viewport, tap targets, no horizontal scroll; matches mobile-first indexing reality.
16. **Enforce HTTPS** — TLS everywhere; HTTP → HTTPS; no mixed content.

### URLs & sharing
17. **Clean up URL slugs** — Readable paths (`/about-us`), not opaque IDs for public pages.
18. **Add an `og:image`** — Open Graph (+ Twitter) image, title, description for shares.

### Search & AI discovery
19. **Verify Search Console** — Ownership/setup noted or checklist item for the operator (cannot fully automate login).
20. **Add `llms.txt`** — Site-level guidance for LLMs (what the product is, key URLs, what to cite); keep accurate and short.

---

## Process

1. Identify public routes and how metadata is produced (file-based, `generateMetadata`, `react-helmet`, etc.).
2. Walk all 20 checks; mark each **PASS / WARN / FAIL / N/A**.
3. Cite evidence (file path, route, or missing artifact).
4. Prioritize: index blockers (1–4, 16) → metadata/semantics (5–10) → structure (11–12) → CWV/mobile/images (13–15) → sharing/AI (17–20).
5. Hand off CWV/image/HTTPS depth to [production-readiness](../production-readiness/SKILL.md) when the issue is infra/perf engineering; hand off heading/alt/mobile craft clashes with “AI look” to UX skills when relevant.

## Output format

```markdown
# SEO audit: <site or route set>

## Verdict
Pass | Warn | Fail — <one line>

## Scorecard (20)
| # | Check | Status | Evidence | Fix |
| --- | --- | --- | --- | --- |
| 1 | sitemap.xml | | | |
| … | … | | | |
| 20 | llms.txt | | | |

## Priority fixes
- P0: …
- P1: …
- P2: …

## Notes
- Search Console / DNS items the human must complete
```

## What NOT to do

- Don’t invent rankings promises or keyword stuffing.
- Don’t add fake schema that doesn’t match page content.
- Don’t block the whole site in `robots.txt` “to be safe.”
- Don’t treat private app shells (logged-in dashboards) as must-index unless they are marketing surfaces.
