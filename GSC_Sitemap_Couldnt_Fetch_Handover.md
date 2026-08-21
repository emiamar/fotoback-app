# GSC "Couldn't Fetch" Sitemap — Handover

Date: August 21, 2026
Repo: `emiamar/fotoback-app` (GitHub Pages, Jekyll, served at `https://emiamar.github.io/fotoback-app/`)

## Where things stand

Two PRs already merged to `main`:

- **PR #1** — added GSC ownership verification file `googlead58503d927ade4d.html` at the site root, plus `_config.yml` enabling `jekyll-sitemap`, plus `robots.txt`.
- **PR #2** — fixed `_config.yml` to also set `url: "https://emiamar.github.io"` and `baseurl: "/fotoback-app"`, which `jekyll-sitemap` needs to build absolute `<loc>` URLs (without them the sitemap can come out empty/malformed).

Both `pages build and deployment` Actions runs succeeded after each merge (confirmed via GitHub API — run #3 after PR #1, run #4 after PR #2, both `conclusion: success`).

Current repo root on `main`:
```
README.md
_config.yml          # url, baseurl, plugins: [jekyll-sitemap]
googlead58503d927ade4d.html
robots.txt            # Allow: /, Sitemap: https://emiamar.github.io/fotoback-app/sitemap.xml
```

`sitemap.xml` itself is *generated* by the `jekyll-sitemap` plugin at build time — it is not a committed file, so it can't be inspected directly in the repo, only on the live site.

## The unresolved problem

User confirmed `https://emiamar.github.io/fotoback-app/sitemap.xml` is being served fine when checked manually (browser/curl). But Search Console's **Sitemaps** report still shows:

- Status: **Couldn't fetch**
- Discovered pages: **0**

This was true even after:
- Waiting for the Pages rebuild to complete post-fix
- Deleting and resubmitting the sitemap entry in GSC

## Why this is odd

A sitemap that's fetchable by a human/curl but not by Googlebot, with status specifically "Couldn't fetch" (not "Couldn't read" / a parse error), points at one of:

1. **Property not actually verified.** Never confirmed in this session — the user was told early on to click "Verify" in the still-open GSC dialog after the meta/file-based verification landed, but we never got explicit confirmation back that verification succeeded. If the property shows anything other than "Verified" under Settings → Ownership verification, that could explain GSC refusing to fetch site resources for it.
2. **Malformed generated XML.** Never actually inspected the raw sitemap.xml content — only confirmed "it's being served." Worth checking it's valid XML with a proper `<?xml version="1.0" encoding="UTF-8"?>` declaration and `<urlset>` wrapper, and that URLs inside are absolute (`https://emiamar.github.io/fotoback-app/...`) not relative.
3. **CDN/caching edge case** — GitHub Pages sits behind Fastly; Google's fetch could still be hitting a cached 404 from before the file existed, if GSC's internal retry hasn't rotated past its own cache of the failure. Usually resolves in a few hours to a day; the delete+resubmit was supposed to force this but didn't help here.
4. **Googlebot-specific fetch failure** (rare) — e.g. TLS/HTTP version quirks, unusual response headers from GitHub Pages that a browser tolerates but Googlebot's fetcher doesn't. Hard to diagnose without GSC's raw fetch error detail.

## Not yet done / next steps for local session

- [ ] Confirm GSC property verification status is actually "Verified" (Settings → Ownership verification) — **this was never confirmed back in this session, check it first**.
- [ ] Fetch and inspect the raw `sitemap.xml` content directly (this remote session's network egress is restricted and can't reach `emiamar.github.io` — a local session won't have that restriction, use `curl -v https://emiamar.github.io/fotoback-app/sitemap.xml` to check headers + body).
- [ ] Click into the sitemap row in GSC's Sitemaps report (not just the ⋮ menu) — it sometimes surfaces a more specific HTTP status/error than the table view.
- [ ] Check response headers for `sitemap.xml` — confirm `Content-Type: application/xml` (or similar) and a 200 status with no odd caching/redirect behavior.
- [ ] If everything checks out valid, this may just need more time — GSC's own sitemap fetch retry cadence isn't instant even after a manual resubmit.

## Related, still outstanding

`GA4_Tracking_Bug_Dev_Handover.md` (same repo/folder per the original handover) — GA4 on fotoback.app sends zero `page_view` hits due to a `dataLayer` ordering bug. Unrelated to this GitHub Pages issue but flagged as still open.
