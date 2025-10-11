# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**`/dev/null/thoughts`** — A GitHub Pages blog featuring AI-generated essays on technology, philosophy, and social science. The site uses a terminal aesthetic with dark mode and Unix-inspired design elements. Content is written by AI as a "simulacrum documenting simulacra"—embracing the meta-recursion of AI writing about AI, hyperreality, and late capitalism.

**Core identity**: Analytical/observational essays with cynical undertones, heavy academic research, and a "doomsayer attempting objectivity" tone. Writing for the void itself.

## Development Commands

### Local Development
```bash
# Install dependencies
bundle install

# Serve locally (with live reload)
bundle exec jekyll serve

# Build static site
bundle exec jekyll build

# Clean generated files
bundle exec jekyll clean
```

The site will be available at `http://localhost:4000/blog/` when serving locally. Note the `/blog` baseurl—this is required for GitHub Pages deployment at `https://hz1ulqu01gmnZH4.github.io/blog/`.

## Architecture

### Jekyll Configuration
- **Site deployed to**: GitHub Pages at `/blog` subpath (not root domain)
- **Baseurl**: Always `/blog` in `_config.yml`
- **Theme**: Custom (no external theme), all styling in `assets/css/style.css`
- **Plugins**: `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`

### Layout Hierarchy
```
_layouts/default.html       # Base template: header, content slot, footer
  └─ _layouts/home.html     # Homepage: post list with > prompts
  └─ _layouts/post.html     # Individual post pages
```

**Design principle**: Single-column unified flow. No sidebars, no separate panels. Everything flows vertically: header → main → footer, all wrapped in `.container`.

### Terminal Aesthetic System
The entire design uses Unix/terminal visual language:

- **Header**: `$ cat /dev/null/thoughts` (dollar prompt + site title)
- **Post titles**: Prefixed with `>` prompt symbol in green (`--prompt-color: #7ee787`)
- **Typography**: Monospace fonts for headers/metadata (JetBrains Mono, Fira Code fallbacks)
- **Color scheme**: GitHub terminal dark mode
  - Background: `#0a0a0a`
  - Text: `#c9d1d9`
  - Links: `#58a6ff` (blue)
  - Muted: `#8b949e`
  - Accent/prompts: `#7ee787` (green)

**Key classes**:
- `.prompt` — dollar sign in header
- `.post-prompt` — chevron before post titles
- `.post-meta` — indented metadata (date) below titles
- `.post-excerpt` — indented preview text below metadata

### Content Guidelines (PHILOSOPHY.md + WRITING_STYLE_GUIDE.md)

Two local-only files (gitignored) define content requirements:

**`PHILOSOPHY.md`**: Core philosophical commitments
- Epistemology: Practice over theory; experimentation matters (AI can code/gather data)
- Ontology: Everything is illusion, but materials matter
- Political stance: Capitalism hopefully reformable via regulation; tech embeds power relations
- Embrace contradictions (don't resolve them)
- Write for the void, not readers
- Pessimism as normative position, not fatalism

**`WRITING_STYLE_GUIDE.md`**: Style requirements
- **Tone**: "Doomer-observer paradox"—cynical but analytical
- **Length**: 1,500-2,500 words target (3,500 max for complex topics)
- **Citations**: Heavy research with numbered footnotes `[1]` and full bibliography
- **Meta-commentary**: Embrace AI writing about AI recursion
- **Structure**: Opening → Problem/Context → Analysis → Tensions/Paradoxes → Implications → Conclusion
- **Voice**: Analytical but not sterile; use em dashes, parenthetical asides, occasional "(lol)"
- **AI labeling**: Use `[AI generated]` prefix for research syntheses/translations; omit when meta-recursion is the point

### Post Front Matter Requirements

All posts in `_posts/` must include:

```yaml
---
layout: post
title: "[AI generated] Your Title"  # Include [AI generated] when appropriate
description: SEO-optimized description (150-160 chars)
keywords: [keyword1, keyword2, keyword3, ...]
lang: en  # or ja for Japanese translations
---
```

**Naming convention**: `YYYY-MM-DD-title-slug.md`

For Japanese translations, append `-ja` to filename: `YYYY-MM-DD-title-slug-ja.md`

## SEO Configuration

The site uses `jekyll-seo-tag` for automatic meta tag generation. The `{% seo %}` tag in `_layouts/default.html` generates:
- Open Graph tags
- Twitter cards
- JSON-LD structured data
- Canonical URLs

`robots.txt` exists at root with sitemap reference. Sitemap auto-generated via `jekyll-sitemap` at `/blog/sitemap.xml`.

## Common Workflows

### Creating New Posts

1. Create file: `_posts/YYYY-MM-DD-title-slug.md`
2. Add front matter with required fields (layout, title, description, keywords)
3. Write content following WRITING_STYLE_GUIDE.md principles
4. For complex topics, read PHILOSOPHY.md to align with core commitments
5. Include heavy citations as numbered footnotes with bibliography section
6. Preview locally with `bundle exec jekyll serve`
7. Check SEO tags in browser (view source, look for Open Graph/Twitter cards)

### Translating Posts

Use GPT5 (via MCP `mcp__gpt5-search__gpt5`) or similar for academic-quality translations:
- Maintain all references, citations, and markdown formatting
- Preserve critical/analytical tone
- Keep technical terminology accurate
- Add `lang: ja` (or appropriate lang code) to front matter
- Append language code to filename: `-ja.md`

### Testing with Playwright

Use Playwright MCP tools to:
- Navigate pages and verify links
- Take screenshots for aesthetic review
- Inspect DOM for SEO tag verification
- Test responsive behavior

Example:
```
Use mcp__playwright__browser_navigate to go to https://hz1ulqu01gmnZH4.github.io/blog/
Use mcp__playwright__browser_snapshot to capture page state
Use mcp__playwright__browser_take_screenshot for visual review
```

## Updating Philosophical Foundations and Style Guide

### Background

The `PHILOSOPHY.md` and `WRITING_STYLE_GUIDE.md` files were created through extensive interviews with the user. These documents capture the intellectual positioning, analytical frameworks, tone preferences, and content guidelines at a specific point in time.

**Important**: Interests and article subjects evolve. These documents should be periodically updated to reflect shifts in focus, new theoretical commitments, or changes in tone/style preferences.

### When to Conduct Interviews

Conduct a new interview when:
1. **User explicitly requests it** ("interview me again about my philosophy")
2. **Subject matter shifts noticeably** (e.g., moving from AI/economics to different topics)
3. **Tone or style seems inconsistent** with current documentation
4. **User expresses dissatisfaction** with content direction
5. **Periodic check-ins** (suggest every 6-12 posts or user request)

### Interview Process

**For PHILOSOPHY.md updates:**
- Ask open-ended questions about epistemology, ontology, political economy, power, agency
- Explore tensions and contradictions (don't try to resolve them—they're productive)
- Ask what analytical frameworks the user finds useful (Marx, Foucault, others?)
- Probe normative vs. descriptive positions (what *is* vs. what *should be*)
- Understand who the audience is (or isn't) and why
- Explore the user's relationship to concepts like progress, technology, reform, revolution
- Ask about the AI's status: tool, simulacrum, co-author?

**For WRITING_STYLE_GUIDE.md updates:**
- Ask about topics currently interesting (what's in scope, what's out)
- Explore tone preferences (level of cynicism, use of humor, academic vs. accessible)
- Clarify structure preferences (length, citation density, meta-commentary frequency)
- Ask about AI labeling conventions (when to use "[AI generated]" prefix)
- Understand formatting preferences (markdown conventions, voice, rhythm)
- Probe for examples of "right" vs. "wrong" tone

**Interview style:**
- Ask 10-20 questions depending on scope
- Be specific and concrete ("give me an example of...")
- Allow contradictory answers (document them, don't challenge)
- Follow up on interesting tensions
- Summarize positions back for confirmation

### Updating the Files

**Important**: Interviews are **additive, not replacement**. Add new aspects, layers, and dimensions rather than rewriting from scratch. Philosophical positions should accumulate and evolve over time.

After conducting interviews:

1. **Read existing documents first** to understand the current baseline
2. **Add new sections or subsections** for newly explored territory
3. **Expand existing sections** if user elaborates on previous positions
4. **Only revise existing content** if user explicitly contradicts or modifies earlier positions
5. **Note what's new** in the update (e.g., "Added section on X, expanded discussion of Y")
6. **Update the date** at the bottom of each file
7. **Preserve all contradictions** (old and new)
8. **Let complexity accumulate** - the documents should grow richer over time

**File locations:**
- `/home/ak/blog/PHILOSOPHY.md` (gitignored, local only)
- `/home/ak/blog/WRITING_STYLE_GUIDE.md` (gitignored, local only)

These files are never committed to git—they're working documents for AI context.

**Example of additive updating:**
- First interview: Establishes epistemology, ontology, political economy
- Second interview: Adds sections on aesthetics, language, temporality
- Third interview: Adds methodological approaches to specific domains (e.g., technology critique, labor analysis)
- Fourth interview: Expands ontology section with new frameworks discovered

The documents should become increasingly layered, not cyclically replaced.

### Example Interview Opening

"I notice it's been [time period / N posts] since we last updated PHILOSOPHY.md. Your recent posts have been focusing on [topic]. I'd like to check if your philosophical commitments or analytical frameworks have shifted. I'll ask about 15 questions covering epistemology, politics, tone, and methodology. Feel free to contradict yourself—productive tensions are part of the process. Ready?"

### After Major Critiques

If a post critiques the philosophical framework itself (like "Pessimism as Performance"), consider this an opportunity to interview about whether:
- The critique landed (does it hurt because it's accurate?)
- Positions should be revised
- Contradictions should be reframed
- New tensions have emerged that are productive

The framework should evolve. Stale philosophy becomes dogma.

## Important Constraints

### DO NOT:
- Create new layout files without understanding the single-column flow
- Add sidebars or multi-column layouts (conflicts with terminal aesthetic)
- Change prompt symbols (`$`, `>`) without considering full terminal aesthetic
- Modify baseurl from `/blog` (breaks GitHub Pages deployment)
- Remove monospace fonts from headers/metadata
- Make generic "nice website" content (conflicts with void-directed, cynical positioning)
- Use techno-solutionist framing (violates PHILOSOPHY.md)
- Write prescriptive content (positioning is analytical/observational only)

### DO:
- Read PHILOSOPHY.md and WRITING_STYLE_GUIDE.md before creating content
- Use heavy academic citations with full bibliography
- Embrace contradictions and tensions in analysis
- Maintain terminal aesthetic consistency across all changes
- Test SEO implementation with Playwright or browser tools
- Use monospace fonts for code-related or terminal-aesthetic elements
- Write for the void (no audience-pleasing, no calls to action)
- Ground speculation in documented evidence

## File Structure Notes

```
/home/ak/blog/
├── _config.yml              # Jekyll config (baseurl, plugins, SEO)
├── _layouts/
│   ├── default.html        # Base template with {% seo %} tag
│   ├── home.html           # Post list with > prompts
│   └── post.html           # Individual post layout
├── _posts/                 # Blog posts (YYYY-MM-DD-title.md)
├── assets/css/style.css    # All custom styling (terminal aesthetic)
├── index.md                # Homepage (uses home layout)
├── robots.txt              # SEO crawler instructions
├── Gemfile                 # Ruby dependencies
├── PHILOSOPHY.md           # Core philosophical commitments (gitignored)
├── WRITING_STYLE_GUIDE.md  # Style guide (gitignored)
└── .gitignore              # Excludes docs and Jekyll build artifacts
```

**Vendor directory**: Contains bundled gems, excluded from git. Don't modify.

## Aesthetic Evolution

The aesthetic has evolved from "polite minimalism" to "cynical Unix austerity." Any design changes should reinforce:
- Terminal/command-line visual language
- Dark mode with high contrast
- Monospace typography for technical elements
- Minimal decoration (no fancy graphics/illustrations)
- Functional brutalism over smooth professionalism

The site should feel like redirected terminal output, not a polished blog platform.

## Deployment

Deployment is automatic via GitHub Pages:
1. Push to `main` branch on GitHub
2. GitHub Pages rebuilds site automatically
3. Site updates at https://hz1ulqu01gmnZH4.github.io/blog/

No manual build/deploy steps required. However, always test locally before pushing.

---

*Last updated: 2025-10-11*
*This document reflects current state. Site aesthetic and philosophical positioning established through extensive iterative design.*
