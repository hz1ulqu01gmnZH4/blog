# WORKFLOW_EXPERIMENT.md

Workflow for **experiment reports** following scientific writing conventions. Use this when you've conducted an empirical investigation and want to document findings rigorously.

**When to use this workflow:**
- Reporting results from scraping/API experiments
- Documenting AI agent behavior tests
- Writing up small-n behavioral studies
- Sharing code analysis findings
- Reporting replication attempts (successes AND failures)

**When NOT to use this workflow:**
- Pure research synthesis → use `WORKFLOW_THEORETICAL.md`
- Proposing experiments without running them → use `WORKFLOW_THEORETICAL.md`
- Conceptual analysis without empirical component → use `WORKFLOW_THEORETICAL.md`

**Related files:**
- `ESSAY_WORKFLOW.md` - Shared workflows (post creation, review, maintenance)
- `WORKFLOW_THEORETICAL.md` - For research synthesis posts
- `PHILOSOPHY.md` / `WRITING_STYLE_GUIDE.md` - Core commitments and style

---

## Scientific Report Structure

Follow standard scientific paper structure adapted for blog format:

```
1. Abstract (optional, for longer reports)
2. Introduction
3. Methods
4. Results
5. Analysis & Discussion
6. Limitations
7. Conclusion
8. Data Availability
9. References
```

---

## Six-Stage Experiment Report Workflow

### Stage 1: Pre-Registration (Before Running)

Document your experimental design **before** collecting data to prevent p-hacking.

**Pre-registration template:**
```markdown
## Pre-Registration

**Date**: [YYYY-MM-DD]
**Research question**: [What are we testing?]

**Hypothesis**: [Specific, falsifiable prediction]
- H₀ (null): [What we expect if effect doesn't exist]
- H₁ (alternative): [What we expect if effect exists]

**Method**: [Protocol in enough detail to replicate]

**Primary outcome measure**: [What variable determines success/failure]

**Sample size justification**: [Why this n? Power analysis if applicable]

**Analysis plan**:
- Statistical test(s) to use: [t-test, chi-square, etc.]
- Significance threshold: [α = 0.05 or other]
- Multiple comparison correction: [Bonferroni, FDR, or none]

**Stopping rule**: [When do we stop collecting data?]

**Exploratory analyses**: [Anything beyond primary hypothesis—labeled as exploratory]
```

**For informal experiments:**
Even for small-n or self-experiments, document:
- What you expect to find
- What would confirm vs. falsify
- When you'll stop

### Stage 2: Data Collection

Execute protocol with rigorous documentation.

**During collection:**
- Timestamp all observations
- Store raw data before any processing
- Log errors, anomalies, edge cases
- Note any deviations from pre-registered protocol
- Version control scripts (git commit data collection code)

**Data organization:**
```
experiment_name/
├── pre_registration.md
├── raw_data/
│   ├── [timestamped data files]
│   └── collection_log.md
├── processed_data/
│   └── [cleaned datasets]
├── scripts/
│   ├── collect.py
│   ├── process.py
│   └── analyze.py
└── figures/
    └── [generated visualizations]
```

**Deviation documentation:**
```markdown
## Protocol Deviations

| Deviation | Reason | Impact |
|-----------|--------|--------|
| [What changed] | [Why] | [How this affects interpretation] |
```

### Stage 3: Analysis

Analyze data following pre-registered plan, then conduct exploratory analyses.

**Confirmatory analysis (pre-registered):**
- Execute exactly what was pre-registered
- Report results regardless of outcome
- Calculate effect sizes, not just p-values
- Report confidence intervals

**Exploratory analysis (post-hoc):**
- Clearly label as exploratory
- Document what patterns emerged from data
- Generate hypotheses for future confirmation
- **Do not treat as confirmatory evidence**

**Statistical reporting checklist:**
- [ ] Sample size (n)
- [ ] Descriptive statistics (mean, SD, median, IQR as appropriate)
- [ ] Test statistic and degrees of freedom
- [ ] P-value (exact, not just < 0.05)
- [ ] Effect size (Cohen's d, r, η², etc.)
- [ ] Confidence intervals
- [ ] Multiple comparison corrections applied

**For non-statistical experiments:**
- Quantify what can be quantified
- Use descriptive statistics even without inference
- Report distributions, not just central tendency
- Document qualitative observations systematically

### Stage 4: Visualization

Create clear, honest visualizations following best practices.

**Visualization principles:**
- Show the data, not just summaries
- Don't hide variation (show error bars, distributions)
- Use appropriate chart types (see below)
- Consistent styling across figures
- Accessible colors (colorblind-friendly palettes)

**Chart type selection:**

| Data Type | Recommended Chart | Avoid |
|-----------|-------------------|-------|
| Distribution (1 variable) | Histogram, density plot, box plot | Pie chart |
| Comparison (categorical) | Bar chart with error bars, dot plot | 3D bars |
| Relationship (2 continuous) | Scatter plot | Line plot (unless time series) |
| Time series | Line plot with confidence band | Bar chart |
| Part-to-whole | Stacked bar, treemap | Pie chart (for >5 categories) |
| Small multiples | Faceted plots | Single cluttered plot |

**Required elements for each figure:**
- Descriptive title
- Axis labels with units
- Legend (if multiple series)
- Error bars or uncertainty indication
- Sample size annotation
- Caption explaining what to see

**Figure generation tools:**
```python
# Python (matplotlib/seaborn)
import matplotlib.pyplot as plt
import seaborn as sns
sns.set_style("whitegrid")
plt.figure(figsize=(8, 5))
# ... plot code ...
plt.savefig("figures/fig1_results.png", dpi=150, bbox_inches="tight")
```

**Include in post:**
- PNG/SVG at appropriate resolution (150+ dpi)
- Alt text for accessibility
- Reference in text before figure appears

### Stage 5: Write Report

Follow scientific structure with blog adaptations.

**1. Abstract** (optional, for reports >1500 words)
```markdown
**Abstract**: [2-3 sentences summarizing question, method, key finding]
```

**2. Introduction**
- Research question in plain language
- Why this matters (motivation)
- Brief theoretical context (link to prior theoretical post if applicable)
- Specific hypothesis being tested

**3. Methods**
- Protocol summary (detailed version in appendix if long)
- Tools, APIs, scripts used (with versions)
- Sample size and selection criteria
- Timeline of data collection
- Link to code repository if public

**4. Results**
- Report findings without interpretation
- Present in order of pre-registered analyses first
- Include all results (not just significant ones)
- Reference figures/tables by number
- Use consistent significant figures

**Results reporting template:**
```markdown
### Primary Outcome

[Descriptive statistics]: The mean X was M (SD = S, n = N).

[Statistical test]: A [test name] revealed [significant/no significant]
difference between conditions, t(df) = X.XX, p = .XXX, 95% CI [L, U],
d = X.XX.

[Figure reference]: Figure 1 shows the distribution of X across conditions.
```

**5. Analysis & Discussion**
- Interpret results in context of hypothesis
- Compare to prior work / theoretical predictions
- Explain unexpected findings
- Consider alternative explanations
- Connect to broader theoretical implications

**6. Limitations**
Be comprehensive and honest:
- Sample size constraints
- Selection biases
- Temporal specificity (may not hold later)
- Platform/API-specific findings
- Researcher degrees of freedom exercised
- What this study cannot tell us

**7. Conclusion**
- Direct answer to research question
- Confidence level (strong evidence, suggestive, inconclusive)
- Implications for theory or practice
- Future directions

**8. Data Availability**
```markdown
## Data Availability

**Code**: [GitHub link or "available on request"]
**Raw data**: [Link or "available on request" or "not shared due to X"]
**Pre-registration**: [Link to pre-reg document]
```

### Stage 6: Quality Checks Before Publication

**6a. Citation Verification**

Run the `citation-checker` skill on the completed report. Even experiment posts cite prior work, methods papers, and comparison studies — these are subject to the same fabrication risks as theoretical posts.

```
Invoke skill: citation-checker

For EACH citation:
- Verify source exists (web search)
- Check claim matches source content
- Verify dates, authors, venues
- Flag orphan references
```

**Experiment-specific citation risks:**
- Method citations: wrong version of a tool/library cited
- Comparison studies: effect sizes or sample sizes misquoted
- Background literature: prior work exists but doesn't make the claimed finding
- Software versions: citing a specific release that doesn't exist

Fix all citation issues before proceeding to remaining quality checks.

**6b. Reproducibility checklist:**
- [ ] Could someone replicate from methods section alone?
- [ ] Are all statistical tests justified and correctly applied?
- [ ] Do figures accurately represent the data?
- [ ] Are limitations honestly assessed?
- [ ] Is exploratory vs. confirmatory clearly distinguished?

**Common errors to check:**
- Confusing correlation with causation
- Over-interpreting small samples
- Selective reporting of results
- Inappropriate statistical tests
- Missing uncertainty quantification
- Figures that distort data (truncated axes, etc.)

**Critical footer for experiment reports:**
- Acknowledge what the experiment doesn't prove
- Note gap between small-n findings and general claims
- Specify what would overturn the finding
- ~2-4 sentences

**Footer examples:**
```markdown
---

*n=14 over two weeks proves nothing except that effects can exist under
these conditions. The confidence interval includes effects from trivial
to substantial. Replication with larger n and longer duration needed
before any strong claims.*
```

```markdown
---

*Scraping three platforms for one week doesn't establish systematic
patterns. But it establishes that the claimed invariant (no price
discrimination) is empirically false in at least these cases. The
platforms may have changed behavior since data collection.*
```

---

## Experiment Types: Specific Guidance

### Scraping/API Experiments

**Pre-registration additions:**
- Endpoints/URLs to query
- Rate limiting approach
- Data retention policy
- Ethical considerations (ToS compliance)

**Analysis focus:**
- Distribution of responses
- Temporal patterns
- Cross-condition comparisons
- Anomaly detection

**Visualization:**
- Time series of collected metrics
- Histograms of response distributions
- Heatmaps for multi-dimensional patterns

### Prompt/Interaction Experiments

**Pre-registration additions:**
- Exact prompts (verbatim)
- Model versions and parameters
- Number of trials per condition
- Coding scheme for responses

**Analysis focus:**
- Response categorization
- Inter-condition differences
- Failure mode taxonomy
- Consistency across trials

**Visualization:**
- Category frequency charts
- Example response comparisons (tables)
- Consistency metrics across trials

### Small-n Behavioral Studies

**Pre-registration additions:**
- Participant recruitment (even if n=1)
- Measurement schedule
- Blinding (if possible)
- Confound controls

**Analysis focus:**
- Individual trajectories (not just aggregates)
- Within-subject variation
- Before/after comparisons
- Qualitative observations

**Visualization:**
- Individual time series
- Before/after comparisons
- Spaghetti plots for multiple subjects

### Code Analysis Experiments

**Pre-registration additions:**
- Target codebase version (commit hash)
- Analysis methodology (static, dynamic, etc.)
- Specific claims being tested

**Analysis focus:**
- Code behavior vs. documentation
- Data flow tracing
- Security/privacy findings
- Undocumented behaviors

**Visualization:**
- Data flow diagrams
- Code excerpt annotations
- Comparison tables (claimed vs. actual)

### Replication Attempts

**Pre-registration additions:**
- Original study citation
- Methodology differences (intentional and unintentional)
- Success criteria

**Analysis focus:**
- Side-by-side with original results
- Effect size comparison
- Possible reasons for discrepancy

**Visualization:**
- Forest plot comparing effect sizes
- Overlay of original vs. replication distributions
- Comparison tables

---

## Git Commit and Documentation

**Commit message structure:**
```
Add post: [Experiment Title] - [One-line finding]

[2-3 sentence overview of experiment and key finding]

Method: [Brief protocol description]
Sample: n = [N], collected [dates]

Key findings:
- [Finding 1 with effect size]
- [Finding 2 with effect size]

Limitations: [Major caveats]

Data: [Link to repository or "available on request"]

Relates to: [Link to theoretical post if applicable]

~[N] words.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

---

## Example Workflow Execution

```
User: "I ran the Q-learning collusion replication. Here's the data."

AI:
1. Reviews pre-registration document
   - Confirms hypothesis: agents converge to supra-competitive prices
   - Confirms analysis plan: compare final prices to competitive equilibrium

2. Processes data
   - Imports price trajectories from 50 simulation runs
   - Calculates descriptive statistics
   - Runs pre-registered statistical tests

3. Analyzes results
   - Confirmatory: t-test on final prices vs. competitive benchmark
   - Reports: t(49) = 4.23, p < .001, d = 0.60, 95% CI [0.31, 0.89]
   - Exploratory: examines convergence speed patterns

4. Creates visualizations
   - Figure 1: Price trajectories over time (spaghetti plot)
   - Figure 2: Final price distribution vs. competitive benchmark
   - Figure 3: Convergence speed by parameter settings (exploratory)

5. Writes report
   - Introduction links to theoretical algorithmic collusion post
   - Methods describe simulation parameters
   - Results present confirmatory then exploratory findings
   - Discussion compares to Calvano et al. original
   - Limitations: simplified environment, no regulatory response

6. Quality checks
   - Citation verification: runs citation-checker, finds Calvano
     cited as 2019 (correct: 2020 AER), fixes
   - Reproducibility checklist: passes
   - Proceeds to shared review workflow (ESSAY_WORKFLOW.md)

7. Commits with detailed message including effect sizes
```

---

## Why Scientific Structure Matters

From PHILOSOPHY.md: **Practice over theory**.

Scientific structure serves epistemics:
- **Pre-registration** prevents motivated reasoning
- **Explicit methods** enable replication
- **Honest statistics** quantify uncertainty
- **Visualization** reveals patterns prose hides
- **Citation verification** catches fabricated or misattributed sources before publication
- **Limitations** demonstrate intellectual honesty

The void doesn't need more armchair speculation. It needs someone to actually check whether the thing happens—and report what they found, not what they hoped to find.

---

*Last updated: 2026-03-08*
*For theoretical/research synthesis posts, see WORKFLOW_THEORETICAL.md*
