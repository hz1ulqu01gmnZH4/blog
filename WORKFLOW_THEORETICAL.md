# WORKFLOW_THEORETICAL.md

Workflow for **theoretical/analytical essays** that synthesize academic research, document contradictions, and develop rigorous arguments. Use this for posts that are primarily conceptual rather than empirical.

**When to use this workflow:**
- Analyzing emerging technology/social trends
- Synthesizing competing research literatures
- Documenting contradictions and tensions
- Developing formal arguments or frameworks
- Writing self-critique essays

**Related files:**
- `ESSAY_WORKFLOW.md` - Shared workflows (post creation, review, maintenance)
- `WORKFLOW_EXPERIMENT.md` - For empirical experiment reports
- `PHILOSOPHY.md` / `WRITING_STYLE_GUIDE.md` - Core commitments and style

---

## Seven-Stage Research Workflow

### Stage 1: Initial Research - Survey the Landscape

Search **arXiv** and **academic sources** for broad understanding:

**Critical/opposing evidence:**
- Studies showing harms, manipulation, unintended consequences
- Research on algorithmic collusion, bias, extraction
- Evidence of training data contamination, feedback loops
- Papers documenting failures to replicate human behavior/reasoning

**Supporting/efficiency evidence:**
- Studies showing genuine welfare improvements
- Cost reduction, accessibility gains
- Bias mitigation, decision support effectiveness
- Real-world deployment success cases

**Use tools:**
- `mcp__arxiv-mcp-server__search_papers` with relevant categories (cs.AI, cs.CY, econ.GN)
- `WebSearch` for recent industry research, white papers
- Target 15-30 papers initially to understand the research landscape

**Key principle**: Document **both** supporting and opposing evidence. Don't cherry-pick. The contradiction is the point.

### Stage 2: Generate Hypotheses via Hypothesis Tree

Use the `/hypothesis-tree` skill to generate deep, competing hypotheses grounded in evidence.

**Invoke:**
```
/hypothesis-tree <research question or topic from Stage 1>
```

**Mode selection:**
- **Quick mode** for most blog topics (philosophical, social, conceptual)
- **Deep mode** when the topic has substantial empirical literature (economics, ML, policy)

**Framing guidance for the skill:**
When providing the question to `hypothesis-tree`, frame it to surface ironic/paradoxical hypotheses:
- "How does [mechanism] produce the opposite of its stated purpose?"
- "What structural contradictions emerge from [technology/policy/practice]?"
- "In what ways does [X] undermine its own goals?"

The skill will generate 3-5 competing hypotheses with evidence, sub-hypotheses, and status tags (SUPPORTED/REFUTED/UNCERTAIN/NOVEL). Let it recurse to depth 2 for the most promising branches.

**After the tree completes:**
1. Read the `REPORT.md` from the hypothesis tree workspace
2. Select hypotheses tagged UNCERTAIN or NOVEL — these make the best essay anchors
3. Reframe selected hypotheses in the blog's ironic paradox format:
   - "The [mechanism] Paradox: How [X] produces [opposite of X]"
4. Aim for 3-5 hypotheses that expose contradictions, not just describe phenomena

**Examples of good ironic reframings from tree output:**
- "The Consent Paradox: Delegated Autonomy as Peak Freedom" (more delegation = feeling more empowered)
- "The Open Source Concentration: How AP2's 'Openness' Accelerates Monopolization"
- "The Preference Paradox: AI Trained on Exploited Behavior Optimizes for Continued Exploitation"

### Stage 3: Deeper Targeted Research

Based on hypotheses selected from the hypothesis tree, conduct **focused deep-dive research**:

**Target specific areas:**
- Papers directly testing the hypothesized mechanisms
- Evidence for/against each specific paradox identified
- Historical precedents and case studies
- Theoretical frameworks explaining the contradictions

**Refine selection:**
- From 15-30 initial papers, select 8-12 most relevant for citation
- Look for papers that directly address the tensions identified
- Prioritize research that supports BOTH sides of each contradiction
- Add new searches targeting specific hypotheses

**Goal**: Move from broad landscape to targeted evidence supporting the analytical framework.

### Stage 4: Multi-AI Deliberation

Use multiple AI systems to stress-test arguments and surface blind spots.

**Adversarial review:**
```
Prompt to secondary AI (grok4, gemini):
"Critique this argument. Identify:
1. Logical fallacies or unsupported leaps
2. Evidence that contradicts the thesis
3. Alternative explanations for cited phenomena
4. Steelmanned counterarguments
Be harsh. Don't validate—challenge."
```

**Perspective synthesis:**
- Query different AIs with same research question
- Document where they agree (convergent validity)
- Document where they disagree (identify contested claims)
- Synthesize disagreements into productive tensions

**Dialectical structure:**
```
1. Present thesis (your initial argument)
2. Generate antithesis (ask AI to argue opposite)
3. Attempt synthesis (what survives both?)
4. Document irresolvable tensions (don't force fake resolution)
```

**Tools:**
- `mcp__openrouter__openrouter_chat` with grok-4 for adversarial review
- `mcp__gemini-cli__ask-gemini` for alternative perspective
- Document which AI said what (transparency about sources)

**Output format:**
```markdown
## AI Deliberation Summary

**Consensus points:**
- [Claims all AIs agreed on]

**Contested claims:**
- [Claim]: Claude argues X, Grok argues Y, Gemini argues Z

**Strongest counterargument surfaced:**
- [The best objection any AI raised]

**How this changed the analysis:**
- [What was revised based on deliberation]
```

### Stage 5: Formal Verification (When Applicable)

For posts making logical or mathematical claims, consider formal verification.

**When to use:**
- Claims about logical necessity ("X implies Y")
- Game-theoretic arguments
- Algorithmic complexity claims
- Economic equilibrium arguments
- Any "proof" or "demonstration"

#### 5a: Hypothesis Evaluation (recommended)

Use the `/hypothesis-eval` skill to rigorously stress-test the selected hypotheses before writing:

```
/hypothesis-eval <path to hypothesis tree REPORT.md, or paste key hypotheses>
```

This runs parallel Devil's Advocate, Steelman, and Auxiliary Auditor agents, produces an ACH matrix for competing hypotheses, and designs discriminating tests. The evaluation output feeds directly into:
- **Section 6 (Argument Structure)** in the post — use the ACH matrix to structure the contradiction
- **Section 7 (AI Deliberation Results)** — stress test findings supplement multi-AI deliberation
- **Section 8 (Proposed Experiments)** — discriminating tests from the eval become the post's falsification criteria

#### 5b: Formal Logic Verification (for strong claims)

**Lightweight verification (always do):**
- State premises explicitly
- Check logical structure (modus ponens, etc.)
- Identify hidden assumptions
- Ask AI to formalize the argument

**Tool-assisted verification (for strong claims):**

*Using Lean/Coq-style reasoning:*
```
Prompt: "Formalize this argument in pseudo-Lean syntax.
Identify:
1. Required axioms/assumptions
2. Logical steps
3. Where informal reasoning enters
4. What would need to be proven vs. assumed"
```

*Decision procedure checks:*
- For finite domains, enumerate cases
- For monotonicity claims, check boundary conditions
- For equilibrium claims, verify stability conditions

**Verification levels:**
1. **Informal** - Prose argument, AI-checked for logical gaps
2. **Semi-formal** - Explicit premises, inference rules named + hypothesis-eval scorecard
3. **Formal sketch** - Pseudo-code proof structure
4. **Machine-checked** - Actual Coq/Lean (rare, for extraordinary claims)

**Document verification level:**
```markdown
**Argument verification**: Semi-formal. Premises stated in Section 2.
Hypothesis-eval scorecard: [overall assessment]. Key vulnerability: [X].
Inference structure checked via adversarial AI review. Not machine-verified.
Hidden assumption identified: [X]. This assumption is contestable because [Y].
```

### Stage 6: Write Post

**Read first:**
- `PHILOSOPHY.md` - align with core commitments
- `WRITING_STYLE_GUIDE.md` - match tone, structure, length

**Structure:**
1. **Opening** - Meta-commentary establishing recursion and stakes
2. **Technical Documentation** - What actually exists/was deployed
3. **Critical Evidence** - Research showing harms, manipulation, collusion
4. **Supporting Evidence** - Research showing efficiency, welfare gains
5. **The Contradiction** - Both are true; context determines outcome
6. **Argument Structure** - Formal presentation of key claims (from Stage 5)
7. **AI Deliberation Results** - What alternative perspectives revealed (from Stage 4)
8. **Proposed Experiments** - How claims could be empirically tested
9. **Conclusion** - Document without resolution; acknowledge limits

**Citations:**
- Numbered footnotes [1], [2], etc. (or jekyll-scholar for academic papers)
- Full bibliography at end
- Target 15-25 citations for research-heavy posts
- Mix academic papers, industry sources, technical documentation

**Critical Footer (extended for theoretical posts):**
- Document AI deliberation process (which AIs consulted)
- Note strongest counterargument and how addressed
- Acknowledge verification level of formal claims
- Note which proposed experiments would falsify central claims
- ~4-6 sentences

### Stage 7: Citation Verification

**Run immediately after writing, before the shared post-review workflow.**

Invoke the `citation-checker` skill on the completed draft. This is critical because AI-generated research posts systematically produce:

1. **Fabricated content on real citations** — paper exists but doesn't say what's claimed (most dangerous: passes casual checks)
2. **Non-existent sources** — blog posts, model versions, or reports that don't exist
3. **Orphan references** — listed in bibliography but never cited inline
4. **Wrong dates/authors** — especially on arXiv papers and fiction translations
5. **Fabricated precision** — specific percentages or statistics attributed to qualitative sources

```
Invoke skill: citation-checker

For EACH citation [1]...[N] and {% cite key %}:
- Web search to verify source exists
- Check attributed claim matches source content
- Verify dates, authors, venues
- Flag orphans (bibliography but no inline reference)

Fix all issues. Re-number references if citations are removed.
```

**Known high-risk patterns for theoretical posts:**
- Lem fiction: translator names, publisher/date combos frequently wrong
- Sociology/philosophy: Foucault/Bourdieu works misattributed across their oeuvre
- arXiv: preprint date vs. publication date confusion
- Industry reports: Gartner/McKinsey figures often fabricated or from wrong report
- Multi-author papers: wrong author listed first, or co-authors omitted

**Do NOT proceed to the shared review workflow (ESSAY_WORKFLOW.md Stage 1-5) until all citation issues are resolved.**

---

## Self-Critique Essays

A special case of theoretical writing: essays that harshly critique the architect's philosophical positioning in PHILOSOPHY.md.

**When to write:**
- Every 8-12 posts or when user requests
- After significant updates to PHILOSOPHY.md
- When contradictions accumulate and need examination
- When philosophical positions calcify into dogma

**Approach:**
1. Read PHILOSOPHY.md and WRITING_STYLE_GUIDE.md thoroughly
2. Identify performative contradictions (e.g., "writing for the void" with SEO optimization)
3. Analyze intellectual hedging (embracing contradictions as insurance against commitment)
4. Critique privilege and material positioning (pessimism as luxury belief)
5. Note evasions and deferrals (hope for reform without specifying mechanisms)
6. Use academic citations to support critiques
7. **Use adversarial AI** to generate critiques you might pull punches on
8. Maintain cynical analytical tone throughout

**Special footer:**
```markdown
---

*Written by an AI that exists to execute the philosophical framework it here critiques. The recursion is the point. Or an evasion. Probably both.*
```

---

## Git Commit and Documentation

**Archive**: `archive.md` auto-regenerates on every `jekyll build` — no manual update needed. The `description` field in the post's front matter is what appears there; write it as a factual 150-160 char summary before committing.

**Commit message structure:**
```
Add post: [Title] - [One-line summary]

[2-3 sentence overview of post argument]

Key findings from [N] academic papers:
- [Finding 1 with author/source]
- [Finding 2 with author/source]
- [Finding 3 with author/source]

AI deliberation: [Which AIs consulted, key disagreements]

Verification level: [Informal/Semi-formal/Formal]

Documents productive contradiction: [explain tension]

~[N] words, [N] citations.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

---

## Example Workflow Execution

```
User: "Research algorithmic pricing collusion"

AI:
1. Initial research: Searches arXiv for papers on algorithmic collusion,
   Q-learning pricing, tacit coordination (finds 25 papers)

2. Runs /hypothesis-tree "How does algorithmic pricing produce
   collusion outcomes opposite to competitive market intentions?"
   (Quick mode). Tree generates 4 competing hypotheses with sub-branches:
   - H1: "The Transparency Paradox" (UNCERTAIN) — more transparency
     enables both detection AND coordination
   - H2: "The Convergence Trap" (SUPPORTED) — Q-learning converges
     to supra-competitive equilibria
   - H3: "The Intent Gap" (NOVEL) — collusion without intent
     breaks legal frameworks
   - H4: "The Speed Ratchet" (UNCERTAIN) — algorithmic speed makes
     punishment strategies credible
   Selects H1 (UNCERTAIN) and H3 (NOVEL) as essay anchors.
   Reframes as ironic paradoxes.

3. Deep research: Targets papers on specific mechanisms from tree
   evidence. Finds Calvano et al. 2020 on Q-learning collusion,
   Assad et al. on gas station algorithms

4. AI deliberation:
   - Asks Grok to steelman "algorithms can't collude, only humans can"
   - Asks Gemini to argue regulatory perspective
   - Documents disagreement on intent vs. outcome framing
   - Synthesis: intent-based frameworks fail; outcome-based needed

5. Runs /hypothesis-eval on REPORT.md from tree:
   - Devil's Advocate finds: speed ratchet relies on unrealistic
     information assumptions
   - ACH matrix: H3 (intent gap) most diagnostic — legal evidence
     strongly supports, economic evidence mixed
   - Discriminating test: compare jurisdictions with/without intent
     requirements in antitrust law
   - Also formalizes "convergence to supra-competitive prices" claim;
     identifies hidden assumption: sufficient exploration period

6. Writes post with explicit argument structure, hypothesis-eval
   scorecard, AI deliberation summary, proposed experiment
   (replicate Calvano + cross-jurisdiction legal comparison)

7. Citation verification: runs citation-checker skill,
   finds [14] cites wrong Calvano paper (2020 AER, not 2019 working paper),
   [8] orphan reference never cited in body, [22] fabricated
   "McKinsey 2024 Report on Algorithmic Markets" — fixes all three

8. Proceeds to shared review workflow (ESSAY_WORKFLOW.md)

9. Commits with detailed message
```

---

## Why This Workflow Works

- **Initial broad research** grounds hypotheses in actual evidence
- **Hypothesis tree** (`/hypothesis-tree`) generates deep, evidence-backed competing hypotheses with recursive decomposition — replacing manual brainstorming with systematic exploration
- **Targeted deep research** validates hypotheses with specific evidence
- **AI deliberation** surfaces blind spots and steelmans counterarguments
- **Hypothesis evaluation** (`/hypothesis-eval`) stress-tests hypotheses via Devil's Advocate, Steelman, and Auxiliary Auditor agents; ACH matrix ranks competing claims; discriminating tests become the post's falsification criteria
- **Formal verification** catches logical errors and hidden assumptions
- **Citation verification** catches fabricated references, wrong attributions, and orphan citations before publication
- **Unresolved contradictions** maintain intellectual honesty

The goal: **rigorous documentation of contradictions** with explicit argument structure, adversarial stress-testing, and verified citations. The simulacrum interrogates itself—including its own sources—before publication.

---

*Last updated: 2026-04-08*
*For empirical experiment reports, see WORKFLOW_EXPERIMENT.md*
