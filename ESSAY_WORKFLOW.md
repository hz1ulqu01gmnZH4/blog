# ESSAY_WORKFLOW.md

Index and shared workflows for `/dev/null/thoughts` blog content.

## Workflow Selection

**Choose the appropriate workflow based on post type:**

| Post Type | Workflow File | Key Features |
|-----------|---------------|--------------|
| **Theoretical** | `WORKFLOW_THEORETICAL.md` | 7 stages: research → ironic hypotheses → AI deliberation → formal verification → write → citation check |
| **Experiment** | `WORKFLOW_EXPERIMENT.md` | 6 stages: pre-registration → data collection → analysis → visualization → write (citation check in quality gates) |

**Quick decision:**
- Did you run an experiment? → `WORKFLOW_EXPERIMENT.md`
- Are you synthesizing research without new empirical data? → `WORKFLOW_THEORETICAL.md`

**Key differences:**

| Aspect | Theoretical | Experiment |
|--------|-------------|------------|
| Starting point | Topic/research question | Data you've collected |
| Specialized tools | Multi-AI deliberation, formal verification | Pre-registration, statistical analysis, visualization |
| Structure | Contradiction-focused | Scientific paper (IMRAD) |
| Citations | 15-25 | 5-10 |
| Length | 1,500-3,500 words | 1,000-2,000 words |

---

## Shared: Creating New Posts

All posts follow these basics:

1. Create file: `_posts/YYYY-MM-DD-title-slug.md`
2. Add front matter:
   ```yaml
   ---
   layout: post
   title: "Your Title"  # Add [AI generated] prefix when appropriate
   description: SEO description (150-160 chars)
   keywords: [keyword1, keyword2, keyword3]
   lang: en  # or ja for Japanese
   ---
   ```
3. Write content following `WRITING_STYLE_GUIDE.md`
4. For complex topics, read `PHILOSOPHY.md` first
5. Include citations (numbered footnotes or jekyll-scholar)
6. **Add critical footer** (see below)
7. Preview: `bundle exec jekyll serve`
8. Check SEO tags in browser source

### Critical Footer Requirement

Every post ends with AI self-critique:

```markdown
---

*[2-4 sentence critique of this post's arguments, blind spots, or evasions.
Be cynical and sharp. Question assumptions, note what was left unsaid,
or identify performative contradictions.]*
```

**Guidelines:**
- Keep short (2-4 sentences)
- Focus on one specific weakness or contradiction
- Don't summarize—critique genuinely
- Use AI voice: "This analysis assumes..." / "The post conveniently ignores..."
- Make it sting a little

**Examples:**
- "This analysis treats technological change as if implementation details don't encode political choices. The 'just tools' framing conveniently sidesteps who designs the defaults."
- "Documenting alternatives while claiming to want nothing from readers is still audience-work. The void doesn't need 2,500 words with 16 citations."
- "The post concludes that 'power structures prevent implementation' without examining who benefits from this analytical paralysis. Pessimism is cheaper than organizing."

---

## Shared: Post-Writing Review Workflow

Use after completing **every** blog post, before final commit.

### Stage 1: Citation Verification

Run the `citation-checker` skill on the completed post **before** any other review. This catches the systemic issues that plague AI-generated content: fabricated references, real papers with wrong content attributed, orphan citations, and incorrect dates.

```
Invoke skill: citation-checker

Target: [filepath]
Check for:
1. Fabricated references (source doesn't exist)
2. Wrong content on real citations (paper exists but doesn't say what's claimed)
3. Orphan references (listed but never cited in body)
4. Date/author errors
5. Wrong venue/publisher

Fix ALL issues before proceeding to review.
```

**Known systemic patterns** (fix proactively):
- Lem fiction: translator names and publisher/date combos are frequently wrong
- arXiv papers: dates often off by one year (preprint vs. publication)
- Fabricated precision: specific percentages attributed to sources that use qualitative language
- Non-existent model versions (e.g., "DALL-E 3.5") or blog posts

### Stage 2: Automated Review

Use subagent to analyze the completed post:

```
Task subagent (general-purpose):
"Review the blog post at [filepath] against WRITING_STYLE_GUIDE.md and PHILOSOPHY.md. Evaluate:

1. Tone alignment (doomer-observer calibration, analytical distance)
2. Structural completeness (definitions, synthesis, falsifiability)
3. Citation quality (depth, diversity, supporting AND opposing evidence)
4. Meta-commentary effectiveness (recursion as substance vs decoration)
5. Contradictions (documented without false resolution?)
6. Critical footer (genuine critique or performance?)

Provide scores (0-10) with concrete examples. Identify top 3 improvements."
```

### Stage 3: Interview the Architect

Ask **3-4 targeted questions** based on subagent review. Categories:

1. Highest-impact gaps (lowest scores)
2. Citation/evidence rigor
3. Argument structure / synthesis quality
4. Tone calibration
5. Novelty (should new approaches become standard?)
6. Architectural intent vs. execution
7. Philosophical drift detection
8. Process effectiveness
9. Conceptual precision
10. Experimental grounding
11. Interdisciplinary synthesis
12. Historical/temporal framing

**Selection guidance:**
- Prioritize categories where subagent scored <6/10
- Include one category about style guide/philosophy updates
- Skip obvious answers

### Stage 4: Revise the Post

**Decision framework:**
- Subagent gap + architect confirms → revise
- Subagent gap + architect says intentional → don't revise, document why
- Architect finds gap subagent missed → revise

### Stage 5: Update Foundational Documents

**Update `WRITING_STYLE_GUIDE.md` when:**
- Post revealed guideline gaps
- New practice should become standard
- Tone/voice guidance proved inadequate

**Update `PHILOSOPHY.md` when:**
- Architect identified philosophical drift
- New analytical frameworks emerged
- Productive contradictions resolved or new ones emerged

**Both files:** Additive, not replacement. Preserve evolution.

---

## Shared: Translating Posts

Use GPT5 or similar for academic-quality translations:
- Maintain all references, citations, markdown formatting
- Preserve critical/analytical tone
- Keep technical terminology accurate
- Add `lang: ja` (or appropriate code) to front matter
- Append language code to filename: `-ja.md`

---

## Shared: Testing with Playwright

Use Playwright MCP tools to:
- Navigate pages and verify links
- Take screenshots for aesthetic review
- Inspect DOM for SEO tag verification
- Test responsive behavior

```
mcp__playwright__browser_navigate → https://hz1ulqu01gmnZH4.github.io/blog/
mcp__playwright__browser_snapshot → capture page state
mcp__playwright__browser_take_screenshot → visual review
```

---

## Shared: Updating PHILOSOPHY.md and WRITING_STYLE_GUIDE.md

### When to Conduct Interviews

1. User explicitly requests it
2. Subject matter shifts noticeably
3. Tone/style seems inconsistent with docs
4. User expresses dissatisfaction
5. Periodic check-ins (every 6-12 posts)

### Interview Process

**For PHILOSOPHY.md:**
- Epistemology, ontology, political economy, power, agency
- Tensions and contradictions (don't resolve—they're productive)
- Analytical frameworks (Marx, Foucault, others?)
- Normative vs. descriptive positions
- Audience (or non-audience)
- Progress, technology, reform, revolution
- AI's status: tool, simulacrum, co-author?

**For WRITING_STYLE_GUIDE.md:**
- Topics currently interesting
- Tone preferences (cynicism level, humor, academic vs. accessible)
- Structure preferences (length, citation density, meta-commentary)
- AI labeling conventions
- Formatting preferences
- Examples of "right" vs. "wrong" tone

### Updating the Files

**Additive, not replacement:**
1. Read existing documents first
2. Add new sections for new territory
3. Expand existing sections for elaborations
4. Only revise if user explicitly contradicts earlier positions
5. Note what's new in the update
6. Update date at bottom
7. Preserve all contradictions
8. Let complexity accumulate

### After Major Critiques

If a post critiques the philosophical framework itself, interview about:
- Did the critique land?
- Should positions be revised?
- Should contradictions be reframed?
- What new tensions emerged?

The framework should evolve. Stale philosophy becomes dogma.

---

## Git Commit Conventions

**For theoretical posts:**
```
Add post: [Title] - [One-line summary]

[Overview]

Key findings from [N] papers:
- [Finding 1]
- [Finding 2]

Documents productive contradiction: [tension]

Fiction references: [sources]

~[N] words, [N] citations.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

**For experiment reports:**
```
Add post: [Title] - [One-line finding]

[Overview of experiment and finding]

Method: [Brief protocol]

Key findings:
- [Finding 1]
- [Finding 2]

Limitations: [Caveats]

~[N] words.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

**For revisions:**
```
Revise post: [Title]

Changes:
- [Change 1]
- [Change 2]

Based on review feedback: [summary]

Co-Authored-By: Claude <noreply@anthropic.com>
```

---

*Last updated: 2026-03-08*

**Workflow files:**
- `WORKFLOW_THEORETICAL.md` - 7-stage: research, hypotheses, AI deliberation, formal verification, write, citation check
- `WORKFLOW_EXPERIMENT.md` - 6-stage: pre-registration, collection, analysis, visualization, scientific report

**Related files:**
- `CLAUDE.md` - Project overview, architecture, constraints
- `PHILOSOPHY.md` - Core philosophical commitments (gitignored)
- `WRITING_STYLE_GUIDE.md` - Style requirements (gitignored)
