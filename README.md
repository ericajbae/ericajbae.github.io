# ericajbae.github.io

Personal academic website for Jihye "Erica" Bae.

Plain static HTML + CSS. No build step, no dependencies. The only script is
the GoatCounter visitor counter (stats at https://khan0425.goatcounter.com/).

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

---

## Editing the content

Everything is hand-written HTML — open the file and edit the text.

- **Add a publication** → copy an existing `<li>` inside `<ol class="biblio">`
  in `publications.html`.
- **Update the CV** → just edit the Google Doc "CV_Bae". The CV page embeds it
  and its "Download PDF" button exports it fresh, so nothing here
  needs to change. Keep the doc shared as "anyone with the link can view".
- **Change colours/fonts** → the `:root` block at the top of
  `assets/css/style.css` holds every token.

### The portrait photo

`assets/img/portrait.jpg` is a square photo.
To swap it, overwrite that file with another square image — the frame uses
`object-fit: cover`, so any square crop drops in cleanly. Its displayed size is
`.portrait { max-width }` in the stylesheet.
