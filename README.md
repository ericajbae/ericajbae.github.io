# jihye-website

Personal academic website for Jihye "Erica" Bae — migrated from Google Sites
(`sites.google.com/view/jihyeericabae`) to GitHub Pages.

Plain static HTML + CSS. No build step, no dependencies, no JavaScript.

```
index.html              Home
research.html           Ongoing / completed projects + publications
cv.html                 Full CV (also downloadable as PDF)
assets/css/style.css    All styling
assets/img/             Logo + project illustrations
assets/files/           CV PDF
.nojekyll               Tells GitHub Pages to serve files as-is
```

## Local preview

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

Or just double-click `index.html` — every path is relative, so it works
straight off the filesystem too.

---

## Publishing to GitHub Pages

### Pick the repository name first — it decides the URL

| Repository name | Published at |
| --- | --- |
| `<username>.github.io` | `https://<username>.github.io/` |
| anything else, e.g. `ericajbae-website` | `https://<username>.github.io/ericajbae-website/` |

Only **one** `<username>.github.io` repo is allowed per account; project repos
are unlimited. The repository must be **public** on a free plan.

### Steps

This repo pushes to `ericajbae/ericajbae-website`, so the site publishes at
**https://ericajbae.github.io/ericajbae-website/**

1. **Make the repo public** — Settings → General → Danger Zone → *Change
   repository visibility* → Public. GitHub Pages only serves private repos on
   paid plans, so this step is required on a free account.

2. **Push:**

   ```sh
   cd /Users/kyoungho/workspace/personal/jihye-website
   git push -u origin main
   ```

3. **Turn on Pages** — repo → **Settings** → **Pages** →
   *Build and deployment* → Source: **Deploy from a branch**,
   Branch: **main**, Folder: **/ (root)** → **Save**.

4. Wait 1–2 minutes (first publish can take up to ~10). The live URL appears at
   the top of that same Settings → Pages screen. Check the **Actions** tab if
   it hasn't appeared — a red run there means the deploy failed.

### Updating later

```sh
git add -A && git commit -m "Update publications" && git push
```

Pages redeploys automatically on every push to `main`.

### Optional: a custom domain

Buy a domain, then Settings → Pages → *Custom domain* → enter e.g.
`jihyebae.com` → Save, and add these records at your registrar:

| Type | Name | Value |
| --- | --- | --- |
| `A` | `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `CNAME` | `www` | `<username>.github.io` |

Then tick **Enforce HTTPS** once the certificate is issued (can take an hour).

---

## Editing the content

Everything is hand-written HTML — open the file and edit the text.

- **Add a publication** → copy an existing `<li>` inside `<ol class="biblio">`
  in `research.html` and `cv.html`.
- **Add a CV entry** → copy a `<div class="entry">` block; the left column is
  `entry__when` (the date), the right is `entry__what`.
- **Replace the CV PDF** → overwrite `assets/files/CV_Jihye_Erica_Bae.pdf`.
- **Change colours/fonts** → the `:root` block at the top of
  `assets/css/style.css` holds every token.

### The portrait photo

`assets/img/portrait.jpg` is a square crop of the original Google Sites photo.
To swap it, overwrite that file with another square image — the frame uses
`object-fit: cover`, so any square crop drops in cleanly. Its displayed size is
`.portrait { max-width }` in the stylesheet.

### Before going live

- Consider leaving a short "This site has moved to …" note on the Google Sites
  page so old links still lead somewhere.
