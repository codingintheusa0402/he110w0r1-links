# he110w0r1-links

Static link-in-bio site for **@he110w0r1.oi** (a Korean "coding diary" account), plus the policy and OAuth return pages
the owner's personal publishing tools point to. Plain HTML and one CSS file: no build step, no JavaScript framework, no
dependencies.

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Link-in-bio page (Korean): avatar, handle, bio, a highlighted link to the Apify Store scraper page (K-Data Lab), GitHub, a "인기 스크래퍼" section with four scraper links, and a "채널" section with Instagram. Footer links to the privacy policy. |
| `privacy.html` | Privacy policy for the owner-only publishing tools (Instagram, Threads, YouTube, TikTok uploads). |
| `terms.html` | Terms of service for the same tools. |
| `deletion.html` | Data-deletion instructions: how to revoke the app per platform, and how to ask for stored tokens to be deleted. |
| `oauth/index.html` | OAuth redirect page. Shows "연결 완료 · Connected"; if the URL has an `error` query parameter it also shows `error` and `error_description`. |
| `assets/style.css` | Shared dark theme (black background, gradient avatar ring and primary button, frosted link cards). Pages with `<main class="doc">` use the narrower text layout. |
| `assets/avatar.jpg` | Avatar, also used as the favicon. |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are, without Jekyll processing. |

## Run locally

Open `index.html` in a browser, or serve the folder so relative links behave like they do when hosted:

```sh
python3 -m http.server 8000
# then open http://localhost:8000/
```

## Deploy

The site is meant for GitHub Pages: serve the repository root from the `main` branch. All links between pages are relative
(`assets/…`, `../assets/…` from `oauth/`), so it works under a project-page path as well as on a custom domain.

## Editing

- **Add a link** to `index.html`: copy an existing `<a class="link" …>` block. Inside it, `.ico` holds an emoji or an
  inline SVG, `<b>` is the title, `<span>` is the subtitle (one line, cut off with an ellipsis). Add `primary` to the class
  for the gradient button.
- **Section headings** are `<h2>` elements between links.
- `index.html` has a `<!--YT_HE110-->` comment just before the footer. It marks where a YouTube channel link goes; it
  renders nothing.
- When you change the privacy policy, update its "Last updated" date.
- The OAuth app settings on each platform must use these pages as their privacy policy, terms, data-deletion and redirect
  URLs. If you move or rename a file, update those settings too.
