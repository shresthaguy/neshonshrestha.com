---
title: "Hugo — Static Site Generator"
date: 2026-08-02
lastmod: 2026-08-02
description: "How this site is built. Hugo basics, project structure, and deployment to GitHub Pages."
category: "Web Development"
tags: ["hugo", "static-sites", "github-pages", "web"]
---

## What is Hugo?

A fast static site generator written in Go. You write content in Markdown, Hugo converts it to a full website. No database, no server — just HTML/CSS/JS files.

## Why Hugo?

- Blog/KB posts are just markdown files — easy to write and version control
- Builds in milliseconds
- Free hosting on GitHub Pages
- SEO-friendly out of the box (sitemaps, RSS, meta tags)

## Project Structure

```
my-site/
├── content/         # Your pages and posts (markdown)
│   └── kb/          # Knowledge base articles
├── themes/          # Site theme (layouts + styles)
├── static/          # Images and other static files
├── hugo.toml        # Site configuration
└── .github/
    └── workflows/   # Auto-deploy on push
```

## Common Commands

```bash
hugo server --buildDrafts    # Local dev server with live reload
hugo new content kb/my-topic.md   # Create new article
hugo                         # Build site to ./public/
```

## Deployment

Push to GitHub → GitHub Actions builds the site → deployed to GitHub Pages → served at your custom domain. Zero-cost hosting.
