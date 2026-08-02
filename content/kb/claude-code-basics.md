---
title: "Claude Code — Getting Started"
date: 2026-08-02
lastmod: 2026-08-02
description: "What Claude Code is, how to set it up, and key concepts for effective use."
category: "AI Tools"
tags: ["claude-code", "AI", "developer-tools"]
type: "note"
---

## What It Is

Claude Code is Anthropic's CLI tool for AI-assisted development. It runs in your terminal, reads your project files, and helps you build, debug, and understand code through conversation. It's available as a CLI, desktop app, web app, and IDE extension.

## Key Concepts

**CLAUDE.md** — A file at the root of your project that gives Claude context about your project. Conventions, structure, how to run things. Think of it as onboarding docs for your AI pair programmer. This is your biggest leverage multiplier.

**Context Window** — Claude can only "see" so much at once. Long conversations degrade quality. Start fresh sessions for new topics. Use `/compact` when things get slow.

**Specificity > Length** — The quality of output depends on the quality of context you provide:
- Bad: "fix the bug"
- Good: "The search function returns empty results when the query contains spaces — I think the split logic in search.py line 23 is wrong"

**Two Modes of Working:**
- Exploring/Planning: back-and-forth, short prompts, refining ideas
- Building/Executing: specific detailed prompts, one clear ask with enough context

## How to Use It

| Command | What it does |
|---------|-------------|
| `/plan` | Plan before implementing a complex change |
| `/review` | Review a pull request |
| `/init` | Generate a CLAUDE.md for your project |
| `/compact` | Compress conversation to save context |
| `/help` | See all available commands |

**Starting a project:**
```bash
mkdir my-project && cd my-project
git init
claude
```

Claude Code uses whatever directory you launch it from as the project root.

## Things I Learned

- Claude reads your project files — better organization = better responses
- Start broad (explain/explore), then narrow (change/fix)
- One clear ask per prompt produces better results than dumping everything at once
- Trust but verify — always run the code and read the diff
- CLAUDE.md is worth the upfront investment — every session starts smarter
- No git needed for non-coding projects — just a folder and your files
- It's a conversation partner, not a command terminal — context matters more than syntax
