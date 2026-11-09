# he110w0r1-links

A static link-in-bio site for **@he110w0r1.oi** (a coding diary: Claude Code, scrapers, 3D, automation),
plus the policy pages and OAuth return page used by the owner's personal publishing tools.

Plain HTML + one CSS file. No build step, no JavaScript framework, no analytics.

## Pages

| File | What it is |
|---|---|
| `index.html` | Link-in-bio page: avatar, bio, the K-Data Lab scraper store on Apify, GitHub, four featured scrapers, Instagram |
| `privacy.html` | Privacy policy for the he110w0r1.oi publishing tools (Instagram, Threads, YouTube, TikTok) |
| `terms.html` | Terms of service for the same tools |
| `deletion.html` | Data-deletion instructions (how to revoke app access, and token deletion on request) |
| `oauth/index.html` | OAuth redirect target. Shows "연결 완료 · Connected"; if the URL has `?error=…`, it shows `error` and `error_description` |
| `assets/style.css` | Shared styles (link cards, `.doc` layout for the policy pages) |
| `assets/avatar.jpg` | Avatar and favicon |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are, with no Jekyll processing |

The site covers only he110w0r1.oi. The separate `3am/` page and its `assets/3am.jpg` image were removed on 2026-11-02.

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000/
```

You can also open `index.html` directly in a browser. All links are relative, so the site works from any sub-path.

## Deploy

Push to the branch your static host serves from (the `.nojekyll` file is there for GitHub Pages). Nothing has to be built.
There is no config and there are no environment variables.

## Editing

- **Add a link:** copy an `<a class="link">…</a>` block in `index.html`. Add the `primary` class for the highlighted card.
  Each card has an `.ico` (emoji or inline SVG) and a `.t` block with a `<b>` title and a `<span>` subtitle.
- **Sections:** use `<h2>` headings (for example `인기 스크래퍼` and `채널`).
- `<!--YT_HE110-->` in `index.html` marks where a YouTube link card goes, just before the footer.
- **Policy pages:** these use `<main class="doc">`. If you change one, update its "Last updated" date.
