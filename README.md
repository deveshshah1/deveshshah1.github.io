# deveshshah1.github.io

Personal site for Devesh Shah, built with Jekyll and the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) remote theme. Pushing to `master` deploys to <https://deveshshah1.github.io> via GitHub Pages.

## Where things live

| Page | File |
| --- | --- |
| About (home) | `index.md` |
| Experience | `_pages/experience.md` |
| Publications | `_data/publications.yml` (content), `_pages/publications.md` (layout) |
| Projects | `_data/projects.yml` (content), `_pages/projects.md` (card layout) |
| Resume | `_pages/resume.md` (PDF at `assets/files/Devesh_Shah_Resume.pdf`) |

- Sidebar photo, title lines, and social links: `_config.yml` → `author` (markup in `_includes/author-profile.html`)
- Top nav: `_data/navigation.yml`
- Fonts and styles (modeled on [Sharon Li's page](https://pages.cs.wisc.edu/~sharonli/)): `_includes/head/custom.html`, `assets/css/main.scss`
- To add a publication or project, copy an existing entry in its `_data/*.yml` file (each file's header explains the fields)
- Images: headshot `assets/images/bio-photo.jpg`, paper thumbnails `assets/images/papers/`, project cards `assets/images/projects/` (1200×750)

## Local preview

```bash
bundle config set --local path vendor/bundle
bundle install
LANG=en_US.UTF-8 bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>. `LANG` must be UTF-8, or Sass fails on the theme's non-ASCII characters.
