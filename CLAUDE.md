# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**`/dev/null/thoughts`** — A GitHub Pages blog featuring AI-generated essays on technology, philosophy, and social science. The site uses a terminal aesthetic with dark mode and Unix-inspired design elements. Content is written by AI as a "simulacrum documenting simulacra"—embracing the meta-recursion of AI writing about AI, hyperreality, and late capitalism.

**Core identity**: Analytical/observational essays with cynical undertones, heavy academic research, and a "doomsayer attempting objectivity" tone. Writing for the void itself.

## Development Commands

### Local Development
```bash
# Install dependencies (first time or after Gemfile changes)
bundle install

# Serve locally (with live reload)
bundle exec jekyll serve

# Build static site
bundle exec jekyll build

# Clean generated files
bundle exec jekyll clean
```

The site will be available at `http://localhost:4000/blog/` when serving locally. Note the `/blog` baseurl—this is required for GitHub Pages deployment at `https://hz1ulqu01gmnZH4.github.io/blog/`.

### Deployment

**Important**: This site uses **jekyll-scholar** (not supported by default GitHub Pages), so deployment happens via **GitHub Actions** instead of the default GitHub Pages build.

**How it works:**
1. Push to `main` branch triggers `.github/workflows/deploy.yml`
2. GitHub Actions builds site with custom plugins (including jekyll-scholar)
3. Built site deployed to GitHub Pages automatically

**No manual deployment needed** - just push to `main` as usual.

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
- **Citations**: Heavy research with numbered footnotes `[1]` and full bibliography. add citation not only for scientific literature but web pages you searched.
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
date: 2026-03-18 22:00:00 +0900      # Required for ordering (see below)
description: SEO-optimized description (150-160 chars)
keywords: [keyword1, keyword2, keyword3, ...]
lang: en  # or ja for Japanese translations
---
```

**Naming convention**: `YYYY-MM-DD-title-slug.md`

For Japanese translations, append `-ja` to filename: `YYYY-MM-DD-title-slug-ja.md`

**Date front matter and post ordering**: Every post must include a `date` field in its front matter. Jekyll orders posts by date descending (newest first); for posts on the same date, the `date` field's time component determines order (later times appear first). When publishing multiple posts on the same day, assign descending hour values (e.g., `23:00:00`, `22:00:00`, `21:00:00`) with `+0900` timezone. For single posts on a date, a plain `date: YYYY-MM-DD` is acceptable.

### Mathematical Notation with KaTeX

**KaTeX is enabled** for rendering mathematical formulas. Use standard LaTeX notation with `$$` delimiters.

**How it works**: Jekyll's kramdown markdown processor converts `$$...$$ ` to `\(...\)` format in HTML, which KaTeX then renders.

**Inline math** (within text):
```markdown
Use $$x + y = z$$ for inline equations.
```

**Display math** (centered, on separate line):
```markdown
Use display mode for longer equations:

$$
\eta = \Theta(1/\sqrt{n})
$$
```

**Multi-line equations**:
```markdown
$$
\begin{align}
\mathcal{L}(\theta) &= \sum_{i=1}^n \ell(y_i, f(x_i; \theta)) \\
&= \mathbb{E}[\ell(y, f(x; \theta))]
\end{align}
$$
```

**Important conventions**:
- Use `$$` delimiters for both inline and display math (KaTeX auto-render handles both)
- For Greek letters: `\alpha`, `\beta`, `\eta`, `\theta`, `\lambda`, etc.
- For operators: `\sum`, `\prod`, `\int`, `\mathbb{E}` (expectation), `\mathcal{L}` (loss)
- For relations: `\to`, `\rightarrow`, `\leq`, `\geq`, `\approx`, `\propto`
- For sets: `\in`, `\subset`, `\cup`, `\cap`, `\emptyset`
- Big-O notation: `O(n)`, `\Omega(n)`, `\Theta(n)`
- Subscripts/superscripts: `x_i`, `x^2`, `x_i^2`
- Fractions: `\frac{a}{b}` or `a/b` for simple cases
- Square roots: `\sqrt{n}` or `\sqrt[3]{n}` for nth root

**When to use math notation**:
- Technical papers with equations, algorithms, complexity bounds
- Posts about machine learning, optimization, statistics
- Any content requiring precise mathematical expression

**Avoid** using math notation for:
- Simple numbers or percentages in prose (write "50%" not "$$50\%$$")
- Variables that are clear in context (write "the parameter n" not "the parameter $$n$$")
- Over-formalizing qualitative arguments

### Using Jekyll-Scholar for Citations

**jekyll-scholar** provides academic-style citations and bibliography management.

**BibTeX file location**: `_bibliography/references.bib`

**In-text citations:**
```markdown
Research shows algorithmic collusion emerges spontaneously {% cite douglas2024algorithmic %}.

Multiple studies confirm this pattern {% cite varoufakis2023technofeudalism allouah2025agentic %}.
```

**Rendering bibliography:**
```markdown
## References

{% bibliography --cited %}
```

**Inline bibliography (single reference):**
```markdown
{% reference varoufakis2023technofeudalism %}
```

**Adding new references:**
1. Add BibTeX entry to `_bibliography/references.bib`
2. Use citation key in post via `{% cite key %}`
3. Add `{% bibliography --cited %}` section at post end

**Note**: Can mix jekyll-scholar citations with manual numbered footnotes [1] for non-academic sources. Use jekyll-scholar for academic papers (google scholar, arXiv, journals), manual footnotes for web sources, industry reports, fiction references.

## SEO Configuration

The site uses `jekyll-seo-tag` for automatic meta tag generation. The `{% seo %}` tag in `_layouts/default.html` generates:
- Open Graph tags
- Twitter cards
- JSON-LD structured data
- Canonical URLs

`robots.txt` exists at root with sitemap reference. Sitemap auto-generated via `jekyll-sitemap` at `/blog/sitemap.xml`.

## Common Workflows

**Workflow files (choose based on post type):**

| Post Type | File | Description |
|-----------|------|-------------|
| Index/Shared | `ESSAY_WORKFLOW.md` | Post creation basics, review workflow, translations, maintenance |
| Theoretical | `WORKFLOW_THEORETICAL.md` | 6-stage: research → ironic hypotheses → multi-AI deliberation → formal verification → write |
| Experiment | `WORKFLOW_EXPERIMENT.md` | 6-stage: pre-registration → data collection → analysis → visualization → scientific write-up |

**Quick decision:**
- Running/reporting an experiment? → `WORKFLOW_EXPERIMENT.md`
- Synthesizing research without new data? → `WORKFLOW_THEORETICAL.md`
- Creating any post? → Start with `ESSAY_WORKFLOW.md` for basics

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
├── ESSAY_WORKFLOW.md       # Index + shared workflows (post basics, review)
├── WORKFLOW_THEORETICAL.md # 7-stage research synthesis workflow
├── WORKFLOW_EXPERIMENT.md  # 5-stage experiment report workflow
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

*Last updated: 2026-01-16*
*This document reflects current state. Workflows extracted to ESSAY_WORKFLOW.md for maintainability. Site aesthetic and philosophical positioning established through extensive iterative design. jekyll-scholar integration via GitHub Actions deployment.*
