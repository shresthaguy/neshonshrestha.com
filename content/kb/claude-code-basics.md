---
title: "Claude Code — Getting Started"
date: 2026-08-02
lastmod: 2026-08-02
description: "What Claude Code is, how to set it up, and key concepts for effective use."
category: "AI Tools"
tags: ["claude-code", "AI", "developer-tools"]
---

## What is Claude Code?

Claude Code is Anthropic's CLI tool for AI-assisted development. It runs in your terminal, reads your project files, and helps you build, debug, and understand code through conversation.

## Key Concepts

### CLAUDE.md
A file at the root of your project that gives Claude context about your project — conventions, structure, how to run things. Think of it as onboarding docs for your AI pair programmer.

### Context Window
Claude can only "see" so much at once. Long conversations degrade quality. Start fresh sessions for new topics. Use `/compact` when things get slow.

### Prompting Effectively
Specificity beats length:
- Bad: "fix the bug"
- Good: "The search function returns empty results when the query contains spaces — I think the split logic in search.py line 23 is wrong"

## Useful Commands

| Command | What it does |
|---------|-------------|
| `/plan` | Plan before implementing a complex change |
| `/review` | Review a pull request |
| `/init` | Generate a CLAUDE.md for your project |
| `/compact` | Compress conversation to save context |

## Things I've Learned

- Claude reads your project files — better organization = better responses
- Start broad (explain/explore), then narrow (change/fix)
- One clear ask per prompt produces better results than dumping everything at once
- Trust but verify — always run the code and read the diff
