# he110w0r1-links

A static link-in-bio site for **@he110w0r1.oi** (a coding diary account), plus the policy and OAuth pages
that the owner's personal publishing tools point to. It is plain HTML and CSS. There is no build step, no
JavaScript framework and no dependencies.

## Pages

| File | What it is |
|------|------------|
| `index.html` | The link-in-bio page: avatar, handle, bio, a primary link to the Apify store (K-Data Lab), GitHub, four featured scrapers, and Instagram. Korean (`lang="ko"`). |
| `privacy.html` | Privacy policy for the publishing tools (Instagram, Threads, YouTube, TikTok). It says the tools only publish the owner's own content and keep no data about anyone else. |
| `terms.html` | Terms of service: personal-use publishing utilities, provided as is. |
| `deletion.html` | Data deletion instructions: how to revoke the app on each platform, and how to ask for stored tokens to be deleted (Instagram DM, handled within 7 days). |
| `oauth/index.html` | OAuth return page ("연결 완료 · Connected"). If the redirect URL has `?error=…&error_description=…`, a small inline script shows the error on the page. |
| `assets/style.css` | Shared styles: a dark background with a blurred gradient glow, a 440 px column of link cards, and a `.doc` layout (640 px) for the policy pages. |
| `assets/avatar.jpg` | Avatar image, also used as the favicon. |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are, without Jekyll. |

The footer of `index.html` links to `privacy.html`. Platforms usually ask for the privacy, terms and
data deletion URLs, and for `oauth/` as the redirect URI, when you register an app.

## Run locally

Every link is relative, so any static file server works:

```sh
python3 -m http.server 8000
# open http://localhost:8000/
```

You can also open `index.html` straight from disk.

## Deploy

The repo is set up for GitHub Pages (`.nojekyll` at the root). Serve it from the root of the default branch.
After a push, Pages publishes the files as they are.

## Editing

- **Add or change a link:** copy an `<a class="link">…</a>` block in `index.html`. Each block holds an
  icon (`.ico`: an emoji or inline SVG) and a title/subtitle pair (`.t` > `b` + `span`). Add `primary` to the
  class to get the gradient style. Section headings are `<h2>`.
- **Colours:** change the CSS variables at the top of `assets/style.css` (`--bg`, `--card`, `--fg`, `--mute`,
  `--grad`).
- `index.html` has an HTML comment, `<!--YT_HE110-->`, just before the footer. It looks like an insertion
  marker for a YouTube link. Leave it there unless you know nothing uses it.
- When you change the policy wording, update the "Last updated" date in `privacy.html`.
