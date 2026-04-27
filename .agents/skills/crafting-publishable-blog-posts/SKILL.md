---
name: crafting-publishable-blog-posts
description: Use when a topic, summary, or rough notes should become a publishable first-person technical blog post, especially when drafts sound generic, lack a central argument, or need a more natural review tone.
---

# Crafting Publishable Blog Posts

## Overview

Turn sparse material into a publishable Hugo article that reads like a real first-person technical review, not a generic explainer.

**Core principle:** lead with one judgment, then organize evidence, tradeoffs, and Q&A around it.

## When to Use

- A topic, summary, or rough notes should become a public blog post
- The draft sounds smooth but generic
- The material should read like a real review for self-review and employer reading
- The writing needs a clearer point of view, stronger structure, or less AI-shaped phrasing

**Do not use for:**
- release notes
- neutral product docs
- posts that require original reporting, data collection, or fact-finding beyond the source material

## Output Contract

Return **publishable Hugo Markdown only**:

```md
---
title: 标题
date: YYYY-MM-DD
---

正文
```

Do not prepend writing notes, options, or meta commentary.
Unless the request says otherwise, write the article in natural Chinese.

## Reality Lock

Before writing, classify the source material:

- **built**: already implemented or used
- **tried**: partially tested or briefly explored
- **planned**: an intended direction
- **inferred**: structure added only to make the article readable

Rules:

- Never present `planned` material as `built`
- Never invent benchmarks, logs, screenshots, user feedback, traffic, production incidents, or architecture details
- If the input is still an idea, write an idea-stage reflection, not a fake retrospective
- If the source only supports a short note, write a short note instead of padding

## Input Triage

| Input | Primary move | Guardrail |
| --- | --- | --- |
| Topic only | Find the narrow angle worth writing and build a short honest argument | Do not fabricate implementation detail |
| Summary | Extract the thesis and supporting contrasts | Preserve the author’s judgment |
| Rough notes | De-duplicate, cluster, and order notes into an argument | Avoid product-pitch language unless the notes themselves clearly ask for it |

## Default Structure

1. Opening context and thesis
2. Core explanation or main argument
3. Tradeoffs / limits / mistakes / constraints
4. 常见问题 / 踩坑问答
5. Short closing paragraph

Every section must serve the same central judgment. If a section does not strengthen the argument, cut it.

## Writing Rules

- State the main judgment early
- Prefer “why I chose this” and “why I did not choose the other path”
- Use first-person when the judgment comes from experience or direct reasoning
- Turn the most confusing point into an explicit Q&A item
- Keep uncertainty visible when the material is still exploratory
- Let concrete limits do the work instead of abstract praise

## Anti-AI Filters

Cut or rewrite lines that sound like:

- “随着技术的发展……”
- “本文将带你……”
- “总的来说……”
- “值得一提的是……”
- “不难发现……”

Also remove:

- symmetrical three-part rhetoric that sounds pre-polished
- empty praise such as “高效”“强大”“优雅” when no evidence follows
- endings that merely restate the title in cleaner words

## Q&A Rules

Q&A is the default closing section unless the source material is too small to support it.

Good Q&A prompts:

- Why did this confuse me at first?
- What gets mixed together most easily?
- Where does this approach stop being a good fit?
- Why this path instead of the obvious alternative?

Bad Q&A:

- headings rewritten as questions
- filler questions added only to make the article look complete

## Common Mistakes

| Mistake | Fix |
| --- | --- |
| Topic-only input becomes fake implementation detail | Downgrade to idea-stage language and focus on motivation, scope, and judgment |
| Notes turn into a product pitch | Re-center on what was learned, doubted, or narrowed |
| Article explains everything but argues nothing | Write the central judgment first, then rebuild the outline |
| Q&A just repeats the body | Use Q&A for confusion, tradeoffs, and edge cases |
| The post sounds too polished | Replace abstract transitions with problem-driven ones |

## Quick Reference

| Need | Move |
| --- | --- |
| Material is thin | Shorten the post, do not pad |
| Material is scattered | Group by decision, not by note order |
| Material is too neutral | Pull out one sentence of judgment and let it lead |
| Material sounds too certain | Mark what is planned, assumed, or still unresolved |

## Final Check

- One clear judgment appears in the opening
- No invented facts or fake certainty
- At least one real tradeoff or limit is visible
- Q&A exposes confusion or pitfalls rather than padding
- Output is Hugo-ready Markdown only
