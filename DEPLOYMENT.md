# Closer Blog - Deployment Guide

## Overview

The Closer blog is built with [Hugo](https://gohugo.io/) using the PaperMod theme and deployed to GitHub Pages via GitHub Actions.

- **Repository**: https://github.com/MarwanNakhaleh/closer-blog
- **Live Site**: https://marwannakhaleh.github.io/closer-blog/
- **Theme**: PaperMod

---

## Directory Structure

```
content/landing-pages/blog/
├── .github/workflows/hugo.yml   # GitHub Actions deployment workflow
├── content/
│   ├── posts/                   # Blog posts (Hugo format)
│   ├── search.md
│   └── archives.md
├── themes/PaperMod/             # Theme (git submodule)
├── hugo.yaml                    # Site configuration
└── DEPLOYMENT.md                # This file
```

---

## Adding New Blog Posts

### 1. Post Location

All blog posts go in: `content/landing-pages/blog/content/posts/`

### 2. Post Format (Hugo Front Matter)

Each post must have YAML front matter at the top:

```markdown
---
title: "Your Post Title Here"
date: YYYY-MM-DD
draft: false
categories:
  - Communication, Clarity & Connection   # OR
  - Data-Driven Intimacy                  # OR
  - Intentional Sexual Growth
tags:
  - Actionable      # OR Analytical, Aspirational, Anthropological
  - other-tags
summary: "A brief 1-2 sentence summary for the post list."
---

Your post content here...
```

### 3. Category Reference (Buckets)

| Category | Description |
|----------|-------------|
| Communication, Clarity & Connection | Dispelling confusion and breaking the silence around sex |
| Data-Driven Intimacy | Using tracking/feedback to improve satisfaction |
| Intentional Sexual Growth | Moving from autopilot to actively improving together |

### 4. Tag Reference (4A Framework)

| Tag | Content Type |
|-----|--------------|
| Actionable | Tips, hacks, how-to guides |
| Analytical | Data, research, breakdowns |
| Aspirational | Stories, lessons, reflections |
| Anthropological | Truths, myths, human nature |

---

## Deployment Process

### Automatic Deployment (Recommended)

1. **Commit changes** to the `main` branch
2. **Push to GitHub**: `git push origin main`
3. **GitHub Actions** automatically builds and deploys
4. **Site updates** within ~1-2 minutes

### Manual Deployment Commands

From the blog directory (`content/landing-pages/blog/`):

```bash
# Stage all changes
git add -A

# Commit with descriptive message
git commit -m "Add new blog post: [Post Title]

Co-Authored-By: Claude Opus 4.5 <noreply@anthropic.com>"

# Push to deploy
git push origin main
```

### Check Deployment Status

```bash
# View recent workflow runs
gh run list --repo MarwanNakhaleh/closer-blog --limit 3

# View specific run details
gh run view [RUN_ID] --repo MarwanNakhaleh/closer-blog

# View failed run logs
gh run view [RUN_ID] --repo MarwanNakhaleh/closer-blog --log-failed
```

---

## Local Development

### Start Dev Server

```bash
cd content/landing-pages/blog
hugo server
```

Site available at: http://localhost:1313/closer-blog/

### Build Static Site

```bash
hugo --gc --minify
```

Output in `public/` directory.

---

## Deployed Posts Tracking

| Date | Filename | Deployed |
|------|----------|----------|
| 2026-02-01 | spark-dies-waiting-doesnt-work.md | Yes |

**Next deployment date**: 2026-02-02

---

## Claude Workflow Integration

When the user requests "generate N more blog posts":

1. **Check this file** for the last deployed date
2. **Generate posts** starting from the next date
3. **Write posts** to `content/landing-pages/blog/content/posts/`
4. **Update the tracking table** above
5. **Commit and push** to deploy
6. **Verify deployment** succeeded

### Quick Deploy Command Sequence

```bash
cd /Users/marwan/Documents/BransonSolutions/Closer-Content/content/landing-pages/blog
git add -A
git commit -m "Add blog post: [TITLE]

Co-Authored-By: Claude Opus 4.5 <noreply@anthropic.com>"
git push origin main
```
