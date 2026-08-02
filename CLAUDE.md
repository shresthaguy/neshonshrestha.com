# neshonshrestha.com

Personal website and knowledge base built with Hugo. Hosted on GitHub Pages with custom domain.

## Structure
- `content/kb/` — Knowledge base articles as markdown files
- `themes/neshon/` — Custom theme (layouts, CSS, JS)
- `hugo.toml` — Site configuration
- `.github/workflows/deploy.yml` — Auto-deploys on push to main

## Commands
- `hugo server --buildDrafts` — Local dev server at localhost:1313
- `hugo new content kb/my-topic.md` — Create new KB article
- `hugo` — Build static site to ./public/

## Conventions
- KB articles go in `content/kb/` with frontmatter: title, date, lastmod, description, category, tags
- Categories group articles on the KB page (e.g., "AWS", "AI Tools", "Web Development")
- Tags should be lowercase kebab-case
- Update `lastmod` when revising an article
- Dark/light theme with toggle, mobile-responsive
- SEO: every article needs description and tags in frontmatter
