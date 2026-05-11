---
title: Getting Started with Jekyll and Chirpy
author: Road
date: 2026-05-11 14:30:00 +0800
categories: [Tutorial, Jekyll]
tags: [jekyll, chirpy, webdev]
math: true
---

## Introduction

This site is built with [Jekyll](https://jekyllrb.com) and the [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) theme. In this post, I'll walk through the key features and how to get started.

---

## Why Jekyll + Chirpy?

- **Static Site Generator** — Fast, secure, and free hosting on GitHub Pages
- **Markdown-based** — Write content in Markdown with powerful extensions
- **Academic-friendly** — Math rendering, code highlighting, clean design
- **Responsive** — Looks great on all devices
- **Customizable** — Easy to modify and extend

---

## Key Features

### Math Support

Inline math: $\nabla \cdot \mathbf{E} = \frac{\rho}{\varepsilon_0}$

Block math:

$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$

### Code Blocks

```javascript
// A simple async function
async function fetchData(url) {
  try {
    const response = await fetch(url);
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}
```

### Tip Boxes

> This is an informational note about the site.
{: .prompt-info }

> Here's a useful tip for writing posts.
{: .prompt-tip }

---

## Writing Posts

Posts are stored in the `_posts/` directory with the naming format `YYYY-MM-DD-title.md`. Each post requires front matter:

```yaml
---
title: Your Post Title
author: Your Name
date: YYYY-MM-DD HH:MM:SS +0800
categories: [Category1, Category2]
tags: [tag1, tag2, tag3]
---
```

---

## Next Steps

1. Customize the `_config.yml` with your information
2. Add your profile photo to `assets/img/avatar.png`
3. Start writing posts in `_posts/`
4. Push to GitHub and enable GitHub Pages

Happy writing!
