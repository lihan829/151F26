# Slides

[Slidev](https://sli.dev/) decks for lecture slides.

- `Lecture_02_Variables_Git.md` — Week 2: Python Basics & Git (exported PDF alongside it, linked from the [course schedule](../index.md))
- `public/images/` — Slidev's [public directory](https://sli.dev/guide/assets#public-directory); referenced with a leading `/` (e.g. `/images/L1_intro.jpg`)

## Usage

```sh
cd slides
npm install
npm run dev      # start dev server at http://localhost:3030
npm run build    # build for production
npm run export   # export to PDF
```

This directory is excluded from the Jekyll build (see `exclude:` in `../_config.yml`) so its `.md` files aren't treated as site pages.
