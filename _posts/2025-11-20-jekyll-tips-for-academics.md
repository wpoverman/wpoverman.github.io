---
layout: v2-post
title: "Jekyll tips for academic sites"
subtitle: "Lessons from rebuilding my personal site"
category: Technical
permalink: /v2/notes/jekyll-tips-for-academics/
---

A sample technical post. Replace with real content.

If you're an academic building a personal site with Jekyll, here are a few patterns I've found useful.

## Use data files for publications

Rather than hardcoding your publication list in HTML, keep it in `_data/publications.yml`:

```yaml
- title: "My Great Paper"
  authors: "Me, Myself, I"
  venue: "NeurIPS 2025"
  year: 2025
  tags: [AI Safety]
```

Then loop over it in your template with Liquid. This makes it trivial to add new papers and reuse the data across pages.

## SCSS variables for your color system

Define your palette once in `_sass/colors.scss` and reference variables everywhere. When you inevitably want to tweak the accent color, it's a one-line change.
