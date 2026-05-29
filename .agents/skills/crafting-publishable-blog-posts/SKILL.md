---
name: crafting-publishable-blog-posts
description: Use when a topic, summary, or rough notes should become a publishable first-person technical blog post, especially when drafts sound generic, run too long, repeat themselves, lack a central argument, or need a more natural review tone.
---

# Crafting Publishable Blog Posts

## Overview

Turn sparse material into a publishable Hugo article that reads like a real first-person technical review, not a generic explainer.

**Core principle:** start with the most direct reason for using the thing, then spend the rest of the article on the details, differences, and Q&A that make that reason believable.

## When to Use

- A topic, summary, or rough notes should become a public blog post
- The draft sounds smooth but generic
- The draft is readable but too long for the amount of source material
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
Default to the shortest article that still makes the judgment clearly.
Do not confuse "short" with "thin" — keep the useful details and cut the repeated setup.

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
- If two paragraphs make the same point, keep the sharper one

## Input Triage

| Input | Primary move | Guardrail |
| --- | --- | --- |
| Topic only | Find the narrow angle worth writing and build a short honest argument | Do not fabricate implementation detail; prefer a short note over a full essay |
| Summary | Extract the thesis and supporting contrasts | Preserve the author’s judgment and remove repeated setup |
| Rough notes | De-duplicate, cluster, and order notes into an argument | Avoid product-pitch language unless the notes themselves clearly ask for it |

## Default Structure

1. Opening paragraph: the direct reason, trigger, goal, or pain point
2. Main details: what the tool / theme / solution is doing
3. Differences and tradeoffs: how it differs from nearby options or older approaches
4. Optional specifics: example, config, or implementation detail if the source supports it
5. Final Q&A section

Every section must serve the same central judgment. If a section does not strengthen the argument, cut it.
If the material is straightforward, merge sections instead of expanding them just to fill the structure.
The opening should usually be a single strong paragraph. The detail sections should carry most of the article weight.

## Reference Pattern

Use this article shape by default:

1. **First paragraph:** why I used it, what problem pushed me to it, or what direct goal I had
2. **Middle sections:** the actual mechanics, details, distinctions, and why it differs from alternatives
3. **Final section:** Q&A / pitfalls / practical follow-ups

If the draft is short but skips the middle details, it is incomplete.  
If the draft has details but repeats the opening motivation in every section, it is bloated.

## Compression Rules

- Prefer 3-5 short sections, not a long staircase of headings
- Prefer 1 compact paragraph over 2 similar paragraphs
- Do not restate the thesis in every section
- Keep bullet lists only when they compress meaning; if the next paragraph repeats the list, cut one
- Default Q&A to 2-3 questions; only go longer when the source clearly supports it
- End as soon as the reason, the key details, the main differences, and the Q&A are clear
- Compress repeated motivation first; do not compress away the mechanism or the comparison

## Writing Rules

- State the main judgment early
- Make the first paragraph answer: "Why did I use this?"
- The first paragraph should sound like a natural opening, not a meta announcement about writing
- Prefer "背景 + 主角 + 直接价值" in one paragraph over openings like "我开始用 X，原因很直接" or "我对 X 的判断是"
- Prefer “why I chose this” and “why I did not choose the other path”
- After the first paragraph, spend most of the space on details and differences
- Use first-person when the judgment comes from experience or direct reasoning
- Turn the most confusing point into an explicit Q&A item
- Keep uncertainty visible when the material is still exploratory
- Let concrete limits do the work instead of abstract praise
- Prefer direct sentences over layered setup
- Treat deletion as writing, not loss

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
- one idea stretched across multiple short paragraphs
- openings that talk about the act of choosing before they establish the real scene

## Q&A Rules

Q&A is the default closing section unless the source material is too small to support it.
Keep it short and use it to answer only the highest-value confusion points.

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
| The post is clear but too long | Merge overlapping paragraphs, cut repeated setup, and stop earlier |
| The post is short but too empty | Restore the detail section: explain the mechanics, the distinctions, or the tradeoffs after the opening |
| The opening feels stiff or self-conscious | Rewrite the first paragraph as scene + tool/theme + direct payoff, without meta phrasing |

## Quick Reference

| Need | Move |
| --- | --- |
| Material is thin | Shorten the post, do not pad |
| Material is scattered | Group by decision, not by note order |
| Material is too neutral | Pull out one sentence of judgment and let it lead |
| Material sounds too certain | Mark what is planned, assumed, or still unresolved |
| Material already makes the point | Stop instead of adding another explanatory section |
| Material has a clear reason but weak middle | Add details and differences before Q&A |

## Final Check

- One clear judgment appears in the opening
- No invented facts or fake certainty
- At least one real tradeoff or limit is visible
- The opening paragraph states the direct reason, goal, or pain point
- The middle explains details and differences instead of repeating the opening
- Q&A exposes confusion or pitfalls rather than padding
- The draft does not repeat the same point in multiple sections
- Output is Hugo-ready Markdown only
