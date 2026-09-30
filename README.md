# ericajbae.github.io

Personal academic website for Jihye "Erica" Bae.

Plain static HTML + CSS. No build step, no dependencies, no JavaScript.

```
index.html              Home
research.html           Ongoing / completed projects
publications.html       Publication list
cv.html                 CV — embeds the live Google Doc "CV_Bae"
assets/css/style.css    All styling
assets/img/             Logo + project illustrations
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

## Publishing

The site is live at **https://ericajbae.github.io/**, served by GitHub Pages
from the `main` branch (root folder) of `ericajbae/ericajbae.github.io`.
Because the repository is named `<username>.github.io`, it publishes at the
root of the domain. It must stay **public** for Pages to work on a free plan.

### Updating

Edit a file on github.com and commit, or edit locally and push:

```sh
git pull
git add -A && git commit -m "Update publications" && git push
```

Pages redeploys automatically on every push to `main`, usually within 1–2
minutes. Check the **Actions** tab if a change hasn't appeared — a red run
there means the deploy failed.

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
  in `publications.html`.
- **Update the CV** → just edit the Google Doc "CV_Bae". The CV page embeds it
  and the "CV (PDF)" / "Download PDF" links export it fresh, so nothing here
  needs to change. Keep the doc shared as "anyone with the link can view".
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
