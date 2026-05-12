# Road's Log

A personal website built with [Jekyll](https://jekyllrb.com) and the [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) theme, hosted on [GitHub Pages](https://pages.github.com).

**Live site**: [https://road1228.github.io](https://road1228.github.io)

## Site Structure

```
.
├── _config.yml          # Main site configuration
├── _data/               # Locale files, contact info, share settings
├── _posts/              # Public blog posts (visible on homepage)
├── _tabs/               # Sidebar pages (About, Notes, Tags, etc.)
├── _guides/             # Internal tutorials & how-to guides
├── _profile/            # Internal personal info (CV, publications)
├── _thoughts/           # Internal personal reflections
├── assets/
│   ├── img/
│   │   ├── avatar.png   # Sidebar profile photo
│   │   └── favicons/    # Browser tab icons
│   └── pdf/             # PDF files
├── .github/workflows/   # CI/CD (auto build & deploy)
└── index.html           # Homepage
```

## Content Types

| Directory | Visibility | URL Pattern |
|-----------|-----------|-------------|
| `_posts/` | Public (homepage) | `/posts/<title>/` |
| `_tabs/` | Sidebar navigation | `/<title>/` |
| `_guides/` | Internal (link only) | `/posts/internal/guides/<title>/` |
| `_profile/` | Internal (link only) | `/posts/internal/profile/<title>/` |
| `_thoughts/` | Internal (link only) | `/posts/internal/thoughts/<title>/` |

## Quick Start

### Write a new post

```bash
code _posts/2026-05-12-my-note.md
git add _posts/2026-05-12-my-note.md
git commit -m "Add note: My Note"
git push origin main
```

### Write an internal page

```bash
code _guides/my-tutorial.md
git add _guides/my-tutorial.md
git commit -m "Add guide: My Tutorial"
git push origin main
```

### Local preview (requires Ruby)

```bash
bundle install
bundle exec jekyll serve
# Open http://127.0.0.1:4000
```

## Tech Stack

- **Static Site Generator**: Jekyll 4.x
- **Theme**: jekyll-theme-chirpy 7.5
- **Hosting**: GitHub Pages (free)
- **CI/CD**: GitHub Actions
- **Language**: English UI, content can be in any language

## License

This work is published under [MIT](LICENSE) License.
