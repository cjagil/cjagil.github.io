# Curtis Gile — personal site

A lightweight, text-first personal website in the spirit of [gwern.net](https://gwern.net):
essays written in Markdown, compiled to static HTML, and hosted for free. No
database, no server to maintain, no monthly bill. The only thing you might ever
pay for is a custom domain (~$12/year), and that's optional.

Built with [Hugo](https://gohugo.io). Everything you write lives in plain text
files you own.

---

## What's here

```
content/            ← everything you write (Markdown)
  _index.md           homepage text
  about.md            the About page
  essays/             one file per essay
  library/            the PDF library page
static/
  css/style.css       the entire look of the site (edit colors at the top)
  pdfs/               drop PDFs here → served at /pdfs/<name>.pdf
layouts/            ← the HTML templates (rarely need touching)
hugo.toml           ← site title, menu, your email
.github/workflows/  ← auto-deploys to GitHub Pages on every push
```

---

## Writing a new essay

Create a file like `content/essays/my-new-essay.md`:

```markdown
---
title: "My New Essay"
date: 2026-06-23
description: "One line that shows up in the essay list."
---

Your text here. Use **Markdown**. Footnotes work like this.[^1]

[^1]: And the note appears at the bottom.
```

Save it. That's the whole workflow. It shows up automatically in the Essays list
and on the homepage.

### Adding a PDF to the Library

1. Drop the file into `static/pdfs/` (e.g. `static/pdfs/walden.pdf`).
2. Add a line to the list in `content/library/_index.md`.

---

## Running it on your computer

You need Hugo installed once. On a Mac with [Homebrew](https://brew.sh):

```bash
brew install hugo
```

Then, from this folder:

```bash
hugo server
```

Open <http://localhost:1313> — the site reloads instantly as you edit. Stop the
server with Ctrl-C.

---

## Putting it online for free (GitHub Pages)

You said a free `username.github.io` address is fine — here's the path. Do this
once; after that, publishing is just `git push`.

1. **Make a GitHub account** at <https://github.com> if you don't have one.

2. **Create a new repository** named exactly `YOURUSERNAME.github.io`
   (e.g. `curtisgile.github.io`). Leave it empty.

3. **Push this folder to it.** From this directory:

   ```bash
   git init
   git add .
   git commit -m "first commit"
   git branch -M main
   git remote add origin https://github.com/YOURUSERNAME/YOURUSERNAME.github.io.git
   git push -u origin main
   ```

4. **Turn on Pages.** In the repo on GitHub → **Settings → Pages** →
   under "Build and deployment", set **Source** to **GitHub Actions**.

5. **Fix the URL.** Open `hugo.toml` and set:

   ```toml
   baseURL = "https://YOURUSERNAME.github.io/"
   ```

   Commit and push. Within a minute or two your site is live at that address.
   (The included workflow in `.github/workflows/deploy.yml` builds and publishes
   automatically on every push — you never run the build yourself.)

From then on, your entire publishing routine is:

```bash
git add .
git commit -m "new essay"
git push
```

---

## Later: a custom domain

If you ever want `curtisgile.net` instead of the github.io address, buy the
domain (Cloudflare or Namecheap, ~$12/year), point it at GitHub Pages in
**Settings → Pages → Custom domain**, and update `baseURL`. Nothing else changes.

---

## Why this setup

- **Durable.** Plain HTML and PDFs will still open in 20 years.
- **Free.** Static hosting on GitHub Pages costs nothing.
- **Yours.** Every word is a text file on your machine and in your repo.
- **Fast.** No JavaScript framework, no database, no cookie banners.
