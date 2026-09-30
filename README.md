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
| anything else, e.g. `jihye-website` | `https://<username>.github.io/jihye-website/` |

Only **one** `<username>.github.io` repo is allowed per account; project repos
are unlimited. The repository must be **public** on a free plan.

### Steps

1. **Create the repo on GitHub** — https://github.com/new
   Name it `<username>.github.io`, visibility **Public**, and do *not* add a
   README/.gitignore (this folder already has its own files).

2. **Push this folder:**

   ```sh
   cd /Users/kyoungho/workspace/personal/jihye-website
   git init -b main
   git add .
   git commit -m "Migrate personal website from Google Sites to GitHub Pages"
   git remote add origin https://github.com/<username>/<username>.github.io.git
   git push -u origin main
   ```

   Or with the GitHub CLI, which creates the repo and pushes in one go:

   ```sh
   gh repo create <username>.github.io --public --source=. --remote=origin --push
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

### Adding the portrait photo

The original Google Sites portrait could not be downloaded (Google returns 403
for direct image requests). To add it:

1. Save the photo as `assets/img/portrait.jpg`.
2. In `index.html`, replace the `<div class="portrait__fallback">…</div>` block
   with:

   ```html
   <img src="assets/img/portrait.jpg" alt="Portrait of Jihye Erica Bae">
   ```

Until then a styled monogram placeholder is shown, so nothing looks broken.

### Before going live

- `index.html` has `<link rel="canonical" href="https://example.github.io/">` —
  replace with the real URL.
- Consider leaving a short "This site has moved to …" note on the Google Sites
  page so old links still lead somewhere.
