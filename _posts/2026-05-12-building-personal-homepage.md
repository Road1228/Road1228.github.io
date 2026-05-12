---
title: How to Build a Personal Academic Homepage from Scratch
author: Road
date: 2026-05-12 13:45:00 +0800
categories: [Tutorial, Web Development]
tags: [jekyll, chirpy, github pages, tutorial]
pin: true
---

## Introduction

Want a free, fast, and professional personal academic website? This guide walks you through building one from zero using **Jekyll** + **Chirpy** theme + **GitHub Pages**. No web development experience required.

**What you'll get:**
- A personal website at `https://<your-username>.github.io`
- Clean academic-style design
- Markdown-based writing
- Math formula support (LaTeX)
- Code syntax highlighting
- Auto-deployment via GitHub Actions
- All for **free**

---

## Prerequisites

Before starting, make sure you have:

1. **A GitHub account** — Sign up at [github.com](https://github.com)
2. **Git** installed on your computer — [git-scm.com](https://git-scm.com)
3. **A code editor** — [VS Code](https://code.visualstudio.com) recommended
4. **Ruby** (optional, only needed for local preview) — [ruby-lang.org](https://www.ruby-lang.org)

---

## Step 1: Create the Repository

### 1.1 Create a new repository on GitHub

Go to [github.com/new](https://github.com/new) and create a repository:

- **Repository name**: `<your-username>.github.io` (e.g., `Road1228.github.io`)
- **Visibility**: Public
- **Do NOT** initialize with README, .gitignore, or license

> The repository name must follow the `<username>.github.io` pattern. This is what enables GitHub Pages to serve your site at that URL.
{: .prompt-tip }

### 1.2 Clone the repository to your computer

```bash
git clone git@github.com:<your-username>/<your-username>.github.io.git
cd <your-username>.github.io
```

---

## Step 2: Set Up the Chirpy Theme

The easiest way is to use the Chirpy starter template.

### 2.1 Option A: Use the Chirpy Starter (Recommended)

1. Go to [github.com/cotes2020/chirpy-starter](https://github.com/cotes2020/chirpy-starter)
2. Click **"Use this template"** → **"Create a new repository"**
3. Name it `<your-username>.github.io`
4. Clone your new repository:

```bash
git clone git@github.com:<your-username>/<your-username>.github.io.git
cd <your-username>.github.io
```

### 2.2 Option B: Manual Setup

If you prefer to set up manually, create these files:

**Gemfile:**

```ruby
source "https://rubygems.org"

gem "jekyll-theme-chirpy", "~> 7.5"
gem "html-proofer", "~> 5.0", group: :test
```

**index.html:**

```html
---
layout: home
---
```

**_config.yml** (see Step 3 for full content)

Then run:

```bash
bundle install
```

---

## Step 3: Configure Your Site

Edit `_config.yml` — this is the most important file. Here's what to customize:

```yaml
# Language and timezone
lang: en
timezone: Asia/Shanghai

# Site identity
title: Your Name's Academic Page
tagline: Academic Notes & Research
description: >-
  A personal academic website for sharing research notes and publications.

# Your site URL (no trailing slash)
url: "https://<your-username>.github.io"

# Your social profiles
github:
  username: <your-username>

social:
  name: Your Name
  links:
    - https://github.com/<your-username>

# Profile photo (sidebar avatar)
avatar: /assets/img/avatar.png

# Enable table of contents in posts
toc: true

# Posts per page
paginate: 10
```

---

## Step 4: Create Your Pages

Pages are stored in the `_tabs/` directory. Each page is a Markdown file with front matter.

### 4.1 About Page (`_tabs/about.md`)

```yaml
---
icon: fas fa-info-circle
order: 4
---

## About Me

> A learner and researcher passionate about knowledge.

### Education

| Period | University | Major | Degree |
|--------|-----------|-------|--------|
| 20XX – Present | XX University | XX Major | Ph.D. |

### Research Interests

- Machine Learning & Deep Learning
- Natural Language Processing

### Contact

- **GitHub**: [your-username](https://github.com/<your-username>)
- **Email**: your.email@example.com
```

### 4.2 CV Page (`_tabs/cv.md`)

```yaml
---
icon: fas fa-address-card
order: 6
layout: page
title: CV
---

## Curriculum Vitae

### Education

**XX University — XX Major (Ph.D.)**
*20XX.09 – Present*

### Publications

1. **Your Name**, Co-author. (20XX). "Paper Title." *Journal Name*.
```

### 4.3 Other Useful Pages

You can also create:
- `_tabs/archives.md` — Post timeline
- `_tabs/categories.md` — Category listing
- `_tabs/tags.md` — Tag listing
- `_tabs/publications.md` — Publication list
- `_tabs/resources.md` — Useful links

> The `icon` field uses [Font Awesome](https://fontawesome.com/icons) class names. The `order` field controls the sidebar sequence.
{: .prompt-tip }

---

## Step 5: Add Your Profile Photo

### 5.1 Sidebar Avatar

Place your photo at `assets/img/avatar.png` and set it in `_config.yml`:

```yaml
avatar: /assets/img/avatar.png
```

> The avatar displays in a circle. Use a **square** photo for best results.
{: .prompt-warning }

### 5.2 Browser Tab Icon (Favicon)

Create a `assets/img/favicons/` directory with these files generated from your photo:

```
assets/img/favicons/
├── favicon.ico                 # Browser tab icon
├── favicon-16x16.png          # 16x16 icon
├── favicon-32x32.png          # 32x32 icon
├── apple-touch-icon.png       # iOS home screen (180x180)
├── android-chrome-192x192.png # Android icon
├── android-chrome-512x512.png # Android splash
└── site.webmanifest           # PWA config
```

You can generate these at [realfavicongenerator.net](https://realfavicongenerator.net) by uploading your photo.

---

## Step 6: Set Up Auto-Deployment

Create `.github/workflows/pages-deploy.yml` so GitHub automatically builds and deploys your site on every push:

```yaml
name: "Build and Deploy"
on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: true

      - uses: actions/configure-pages@v5

      - uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.4
          bundler-cache: true

      - run: bundle exec jekyll b -d "_site"
        env:
          JEKYLL_ENV: "production"

      - run: |
          bundle exec htmlproofer _site \
            --disable-external \
            --ignore-urls "/^http:\/\/127.0.0.1/,/^http:\/\/0.0.0.0/"

      - uses: actions/upload-pages-artifact@v4

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
    steps:
      - uses: actions/deploy-pages@v4
```

### 6.1 Enable GitHub Pages

1. Go to your repository on GitHub
2. **Settings** → **Pages**
3. Under "Build and deployment", set **Source** to **GitHub Actions**

---

## Step 7: Push and Go Live

```bash
git add .
git commit -m "Initial setup: Jekyll + Chirpy academic site"
git push origin main
```

GitHub Actions will start building automatically. Check progress at:
`https://github.com/<your-username>/<your-username>.github.io/actions`

Once complete, your site is live at: **`https://<your-username>.github.io`**

---

## Step 8: Troubleshooting Common Issues

### Build Fails: "Test site" Step

This is usually caused by **broken internal links** — you referenced a file that doesn't exist.

**How to fix:**
1. Go to Actions → click the failed run → expand "Test site"
2. Look for errors like `linking to /path/file, which does not exist`
3. Either create the missing file or remove the broken link

### Site Not Updating

- Wait 1-2 minutes for deployment
- Force refresh: `Cmd + Shift + R` (Mac) or `Ctrl + Shift + R` (Windows)
- Try in an incognito/private window

### Avatar Not Showing

- Make sure the file path in `_config.yml` matches the actual file location
- Verify the image file is committed and pushed to GitHub

---

## How to Write and Publish Notes

### Creating a Note

Create a Markdown file in `_posts/` with the naming format `YYYY-MM-DD-title.md`:

```bash
# Example: create a new note on May 12, 2026
code _posts/2026-05-12-my-research-notes.md
```

### Writing the Content

Every note must start with front matter:

```markdown
---
title: My Research Notes
author: Road
date: 2026-05-12 14:00:00 +0800
categories: [Research Notes]
tags: [machine learning, paper review]
math: true
---

## Key Findings

The attention mechanism can be expressed as:

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V
$$

### Code Example

```python
import torch
x = torch.randn(3, 4)
print(x.shape)
```
```

### Front Matter Reference

| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Note title |
| `author` | Yes | Author name |
| `date` | Yes | Date with timezone |
| `categories` | No | 1-2 categories |
| `tags` | No | Multiple tags |
| `math: true` | No | Enable LaTeX formulas |
| `mermaid: true` | No | Enable diagrams |
| `pin: true` | No | Pin to homepage top |
| `image` | No | Social preview image |

### Publishing

```bash
# Stage the new note
git add _posts/2026-05-12-my-research-notes.md

# Commit
git commit -m "Add note: My Research Notes"

# Push to trigger auto-deployment
git push origin main
```

Your note will be online in 1-2 minutes.

### Preview Locally (Optional)

If you have Ruby installed, you can preview before pushing:

```bash
bundle install          # First time only
bundle exec jekyll serve
# Open http://127.0.0.1:4000 in your browser
```

---

## Summary

```
From zero to live website:

  1. Create GitHub repo  →  <username>.github.io
  2. Set up Chirpy theme  →  starter template or manual
  3. Edit _config.yml     →  your name, URL, avatar
  4. Create pages         →  _tabs/about.md, _tabs/cv.md, etc.
  5. Add profile photo    →  assets/img/avatar.png
  6. Set up CI/CD         →  .github/workflows/pages-deploy.yml
  7. Enable GitHub Pages  →  Settings → Pages → GitHub Actions
  8. Push to main         →  git push origin main
  9. Visit your site      →  https://<username>.github.io
  10. Write notes         →  _posts/YYYY-MM-DD-title.md → git push
```

> The full source code for this site is available at [github.com/Road1228/Road1228.github.io](https://github.com/Road1228/Road1228.github.io).
{: .prompt-info }
