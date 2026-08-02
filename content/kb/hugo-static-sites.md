---
title: "Hugo — Static Site Generator"
date: 2026-08-02
lastmod: 2026-08-02
description: "How this site is built. Hugo basics, project structure, and deployment to GitHub Pages."
category: "Web Development"
tags: ["hugo", "static-sites", "github-pages", "web"]
type: "note"
---

## What It Is

Hugo is a fast static site generator written in Go. You write content in Markdown, Hugo converts it to a full website. No database, no server, no monthly hosting costs — just HTML/CSS/JS files served from GitHub Pages.

## Key Concepts

**Content as Markdown** — Every page/article is a `.md` file with frontmatter (metadata at the top) and body content. No CMS, no editor — just files in a folder.

**Archetypes** — Templates for new content. When you run `hugo new content kb/my-article.md --kind kb-solution`, it creates a file pre-filled with the solution structure.

**Themes** — Layouts + styles that define how your site looks. This site uses a custom theme (`themes/neshon/`).

**Taxonomies** — Tags and categories that auto-generate listing pages (e.g., `/tags/aws/` shows all articles tagged with AWS).

**Project Structure:**
```
my-site/
├── content/kb/      # Your articles (markdown)
├── themes/neshon/   # Site theme (layouts + styles)
├── static/images/   # Images and static files
├── hugo.toml        # Site configuration
└── .github/workflows/  # Auto-deploy on push
```

## How to Use It

```bash
# Local dev server with live reload
hugo server --buildDrafts

# Create new solution article
hugo new content kb/my-workaround.md --kind kb-solution

# Create new learning note
hugo new content kb/my-topic.md --kind kb-note

# Build site to ./public/
hugo
```

**Deployment flow:** Edit locally → `git push` → GitHub Actions builds → site updates at your domain in ~1 minute.

## Things I Learned

- `baseURL` in hugo.toml must match your actual domain — locally use `hugo server --baseURL http://localhost:1313/` to avoid redirects
- `lastmod` in frontmatter is useful for knowledge base articles that get updated over time
- GitHub Pages + GitHub Actions = free hosting with auto-deploy, no server to manage
- DNS propagation takes time (up to an hour) — don't panic if the site doesn't show immediately after connecting a domain
- Hugo builds in milliseconds — live reload during development is instant
