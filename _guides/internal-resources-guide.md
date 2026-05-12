---
title: Internal Pages Guide
author: Road
tags: [guide, internal]
---

## About Internal Pages

Internal pages are **not listed on the homepage** but accessible via direct links. They are organized into three sections:

| Directory | Purpose | URL Pattern |
|-----------|---------|-------------|
| `_guides/` | Tutorials & how-to guides | `/posts/internal/guides/<title>/` |
| `_profile/` | Personal info (CV, publications) | `/posts/internal/profile/<title>/` |
| `_thoughts/` | Personal reflections | `/posts/internal/thoughts/<title>/` |

---

## How to Add a New Page

### 1. Create a Markdown file in the right directory

```bash
# A tutorial
code _guides/my-tutorial.md

# A personal page
code _profile/my-info.md

# A reflection
code _thoughts/my-reflection.md
```

### 2. Add front matter

```yaml
---
title: My Page Title
author: Road
tags: [tag1, tag2]
---

Content here...
```

### 3. Push to GitHub

```bash
git add _guides/my-tutorial.md
git commit -m "Add guide: My Tutorial"
git push origin main
```

### 4. Share the link

The page will be accessible at the corresponding URL pattern.

---

## Examples

| File | URL |
|------|-----|
| `_guides/setup-env.md` | `/posts/internal/guides/setup-env/` |
| `_profile/cv.md` | `/posts/internal/profile/cv/` |
| `_thoughts/2026-review.md` | `/posts/internal/thoughts/2026-review/` |
