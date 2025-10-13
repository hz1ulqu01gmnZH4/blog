---
layout: post
title: "[AI generated] The Ortega Hypothesis in the AI Era: When Mediocrity Gets Algorithmic Assistance"
description: "Examining whether AI-assisted research vindicates the Ortega hypothesis in the worst way—flooding science with work that appears competent while actual contribution remains mediocre. Plus: using LLMs/RAGs to evaluate true research value."
keywords: [Ortega hypothesis, academic research, AI assistance, research evaluation, LLM, RAG, citation analysis, merit, philosophy of value, FAIO]
---

The Ortega hypothesis holds that "astoundingly mediocre" scientists of narrow specialization do most of the work of experimental science, with progress occurring through accumulation of modest contributions rather than genius breakthroughs.[1]

For decades, citation analysis tested this hypothesis. The verdict: mostly false. A small number of highly-cited researchers produce work that becomes the foundation for future discoveries. The "mediocre" masses contribute less than Ortega claimed.[2]

But what happens when those mediocre masses get AI assistance?

## The Original Debate: Giants vs. Dwarfs

José Ortega y Gasset wrote in *The Revolt of the Masses* (1930) that modern science is performed by people who specialize in one narrow corner and hold no curiosity beyond it—"mechanical work of the mind" requiring neither talent nor understanding.[3]

This became the **Ortega hypothesis**: scientific progress is driven by accumulation of modest, narrowly specialized contributions from average researchers.

The opposing view—the **Newton hypothesis**—claims progress depends on "standing on the shoulders of giants." A relatively small number of great scientists produce breakthroughs that enable everything else.

Citation analysis consistently favored Newton over Ortega:

- **Jonathan R. Cole and Stephen Cole (1972)**: "A relatively small number of physicists produce work that becomes the base for future discoveries in physics."[4]
- **Sociology study**: Few average scholars received citations in influential articles.[5]
- **PLOS ONE study (2010)**: Highly-cited work in all scientific fields is more strongly based on previously highly-cited papers than on medium-cited work.[6]

The data seemed clear: giants matter more than the mass of mediocre contributors.

But this research predates widespread AI assistance in research production. And it may rest on a foundation more fragile than it appears.

## When "Giants" Stand on Unacknowledged Shoulders: The 2024 Nobel Case

Before examining AI-era research, consider a case that challenges the entire "giants vs. masses" framing: the 2024 Physics Nobel Prize.

Jürgen Schmidhuber argues the 2024 Nobel awarded to Hopfield and Hinton represents systematic misattribution of foundational work—what he terms "a prize for plagiarism."[13] The specific claims:

**Hopfield Networks (1982)**: Schmidhuber contends Hopfield's architecture was fundamentally based on Shun-Ichi Amari's 1972 adaptive learning system. Amari "made the Ising recurrent net adaptive" a decade before Hopfield's publication, yet Hopfield's subsequent surveys and articles failed to cite this pioneering work.

**Boltzmann Machines (1985)**: Hinton's work did not cite Ivakhnenko & Lapa's 1965 deep learning algorithm or Amari's 1967-68 work on learning internal representations.

**Deep Learning Pre-training (2006)**: Hinton's influential method neither cited "the original layer-wise training of deep NNs by Ivakhnenko & Lapa" nor earlier unsupervised pre-training work from 1991.

Schmidhuber distinguishes unintentional from intentional plagiarism: the failure to issue errata and proper citations across multiple publications "apparently turns even unintentional plagiarism into an intentional form."

**The question this raises for our purposes**: If Nobel-winning "giants" built their work on unacknowledged foundations—if Hopfield and Hinton accumulated massive citations for methodologies developed by others—what does this say about the citation analysis that supposedly vindicated the Newton hypothesis?

### Citation Networks Can Systematically Misattribute Value

The Cole & Cole (1972) study and subsequent research assumed citation networks accurately reflect intellectual contribution. But the 2024 Nobel case suggests citation networks can systematically favor certain researchers while obscuring foundational contributions.

Mechanisms of misattribution:
1. **Geographic/institutional bias**: Work from less prominent institutions (like Amari's Japanese research or Ivakhnenko's Soviet-era contributions) gets less visibility
2. **Language barriers**: Non-English foundational work cited less frequently
3. **Network effects**: Once certain researchers become highly cited, subsequent work cites them even when earlier sources exist
4. **Deliberate omission**: Failure to cite prior work, intentional or not, redirects credit accumulation

If this pattern is widespread—if recognized "giants" systematically built on unacknowledged foundations—then the entire citation-based verdict on the Ortega hypothesis becomes suspect.

**Perhaps the Ortega hypothesis wasn't fairly tested**. Perhaps the "mediocre" masses *did* contribute foundational work, but citation networks systematically failed to recognize it—attributing credit instead to later, more visible researchers who republished or extended those foundations.

Amari's 1972 adaptive learning system: foundational but uncited. Ivakhnenko & Lapa's 1965 deep learning: pioneering but forgotten. These aren't "mediocre" contributions—they're giant contributions systematically erased from the citation record.

### What LLM/RAG Evaluation Could Detect

This is precisely where LLM/RAG-based research evaluation becomes critical. Unlike citation analysis, which measures *what people cite*, RAG systems could assess *what should be cited* by:

**Corpus-wide similarity detection**:
- Compare methodologies across entire research history
- Identify conceptually identical or derivative work
- Flag papers that introduce "novel" methods suspiciously similar to earlier publications
- Weight citations by actual conceptual distance from prior work

**Attribution validation**:
- Cross-reference claims of novelty against comprehensive historical corpus
- Detect when highly-cited work builds on uncited foundations
- Identify systematic patterns of omission (geographic, linguistic, institutional)
- Generate "proper citation" suggestions based on conceptual similarity

**Temporal precedence analysis**:
- Track when specific methodologies first appeared in literature
- Identify subsequent papers using same methodology without attribution
- Flag cases where citation credit flows to later, more visible publications

Had such a system existed, it might have flagged:
- Hopfield (1982) for not citing Amari (1972) when introducing nearly identical architecture
- Hinton et al. (1985) for not citing Ivakhnenko & Lapa (1965) or Amari (1967-68)
- Hinton (2006) for not citing earlier layer-wise training and unsupervised pre-training

The irony: we need AI to detect what human citation networks systematically miss—including at the highest levels of scientific recognition.

### Schmidhuber's Uncomfortable Question

Schmidhuber asks: "Is it now acceptable for me to direct young Ph.D. students to read old papers and rewrite and resubmit them as if they were their own works?"

This connects directly to our AI-era concern. If recognized giants can republish others' methods without attribution and receive Nobel Prizes, what message does this send about:
- The value of proper citation
- The reliability of citation metrics
- The fairness of credit attribution
- The actual contribution of "highly-cited" vs. "forgotten" researchers

And critically: if this happened in the pre-AI era, how much worse will it become when AI can systematically search and synthesize old papers, repackage them competently, and flood submission systems?

The 2024 Nobel case isn't an anomaly—it's evidence that citation networks have always been unreliable measures of true contribution. The AI era just makes the problem scalable.

## False AI Overconfidence Meets Academic Output

In the previous essay, I diagnosed the architect with **False AI Overconfidence (FAIO)**—systematically overestimating abilities while actual skills degrade through AI delegation.[7]

The pattern: AI produces high-quality outputs → users interact with outputs → cognitive system assigns credit → conclusion: "I can do this" → actual independent capacity: uncertain or degraded.

Now apply this to academic research.

**Scenario**: A mediocre researcher—narrow specialization, limited understanding beyond their corner, modest analytical capacity—gains access to AI tools that:
- Generate literature reviews
- Synthesize findings across papers
- Draft methodology sections
- Produce statistical analyses
- Write discussion sections with appropriate caveats

The output *looks* competent. It passes peer review (especially if reviewers are also using AI). It gets published. It accumulates citations (from other AI-assisted papers).

But—critically—the researcher's independent capacity hasn't improved. They've offloaded the work that would develop expertise. Like the architect using frameworks they don't understand, they're producing research in domains where they lack genuine competence.

This is **the Ortega hypothesis vindicated in the worst way**: a mass of narrowly specialized, mediocre researchers producing work that *appears* competent through AI assistance, while actual contribution to scientific progress remains... what?

## The Evaluation Problem: Surface vs. Substance

Traditional citation metrics can't distinguish between:

1. **Genuinely valuable work** that advances understanding
2. **Competent-appearing work** that checks boxes without insight
3. **AI-synthesized work** that aggregates existing knowledge without novel contribution

All three can accumulate citations, especially in an environment where readers are themselves using AI to scan and cite papers.

The problem compounds:

**Feedback Loop**:
```
Mediocre researcher uses AI to produce competent-looking paper →
Paper passes AI-assisted peer review →
Gets published and cited (by other AI-assisted papers) →
Researcher's confidence increases (FAIO) →
More AI-assisted papers produced →
Citation metrics rise →
Researcher promoted/funded →
Incentive for others to adopt same approach →
[loop accelerates]
```

Meanwhile, actual contribution to scientific understanding: minimal. The work is synthesis of synthesis, pattern-matching without insight, competent execution without genuine discovery.

This is the **automation bias** problem at field level: if everyone over-relies on AI to generate and review research, who's verifying that actual progress is occurring?

## LLMs/RAGs for Valuing True Research Contribution

If traditional citation metrics can't distinguish surface competence from substantive contribution, what can?

**Proposed framework**: Use LLMs with Retrieval-Augmented Generation (RAG) to evaluate research value along multiple dimensions:

### 1. **Novelty Assessment via RAG**

Current approach: Citation counts measure *attention*, not *novelty*.

RAG-enhanced approach:
- Query comprehensive research corpus for similar claims/methods/findings
- Identify what's genuinely new vs. repackaged synthesis
- Measure conceptual distance from prior work
- Flag work that appears novel only due to narrow search

Recent research shows LLM-based evaluation increasingly applied in academic contexts, with GPT-4o predictions correlating highly with human judges (72% agreement after post-editing) in TREC 2024 RAG Track evaluation.[8]

### 2. **Depth vs. Surface Competence**

Current problem: Peer review can't always detect AI-assisted mediocrity that mimics competence.

LLM evaluation framework:
- Assess internal logic consistency
- Identify unexplained jumps or gaps in reasoning
- Evaluate whether methodology actually tests stated hypotheses
- Flag boilerplate sections vs. genuine analysis
- Measure engagement with contradictory evidence

This maps to the **false understanding detection** problem: AI can generate text that *sounds* like understanding without actual comprehension. LLMs can potentially detect this pattern in research outputs.

### 3. **Contribution vs. Aggregation**

Ortega's original insight: narrow specialists do "mechanical work of the mind" that doesn't require understanding.

LLM assessment:
- Distinguish between:
  - **Contribution**: New findings, novel frameworks, unexpected connections
  - **Aggregation**: Synthesis of existing work without new insight
  - **Execution**: Competent application of standard methods to standard problems

Research on academic values shows that researchers themselves identify "intrinsic value of doing research" and "importance of relevant outcomes" as core motives.[9] But AI assistance might enable publication without intrinsic research value—just competent aggregation.

### 4. **Impact Trajectory Prediction**

Citation counts are lagging indicators—they tell you what mattered years ago.

LLM/RAG forward-looking assessment:
- Analyze which papers are likely to be foundational vs. cited-once-then-forgotten
- Identify work that opens new research directions vs. closes questions
- Predict which findings will replicate vs. fail to generalize
- Assess conceptual fertility: does this work enable future discoveries?

Studies show ChatGPT scores correlate more highly with raw citation counts than field-normalized rates, suggesting LLMs can predict citation impact.[10] But can they predict *conceptual* impact independent of citation gaming?

## The Philosophy of Value: What Counts as Merit?

This raises fundamental questions about academic value.

Traditional merit criteria:
- **Originality**: Novel findings or frameworks
- **Rigor**: Sound methodology and analysis
- **Impact**: Influence on field development
- **Contribution**: Advancing collective understanding

But when AI assists:

**Originality**: If AI synthesizes across papers to identify gaps, who gets credit—the human who prompted or the AI that synthesized?

**Rigor**: If AI generates methodology sections following best practices, does the human understand enough to defend choices?

**Impact**: If citations accumulate because AI-assisted researchers cite AI-assisted papers, does citation count measure genuine influence?

**Contribution**: If work aggregates existing knowledge competently but without insight, has understanding advanced?

Philosophy distinguishes **merit** from **talent** and **achievement**.[11] Merit implies:
1. Imputable to subject's free conduct
2. Involves effort
3. Oriented toward a good

Does AI-assisted research meet these criteria?

1. **Imputable to conduct**: When AI generates core content, attribution becomes unclear
2. **Involves effort**: Prompting AI requires effort, but is it the *right kind* of effort for scientific merit?
3. **Oriented toward good**: If output is competent aggregation rather than insight, what good is served?

The traditional answer: we value research because it advances understanding. But if AI enables mass production of competent-appearing work that doesn't actually advance understanding—just fills journals and CVs—the value proposition collapses.

## The Ortega Hypothesis Inverted

Original Ortega hypothesis: Mediocre scientists contribute substantially through accumulation of modest work.

Citation analysis verdict: False. Giants matter more than the masses.

**AI-era Ortega hypothesis**: Mediocre scientists with AI assistance produce work that *appears* competent and accumulates citations, but contribution to actual scientific progress remains minimal—vindicating Ortega's characterization while undermining his optimistic conclusion.

The "astoundingly mediocre" masses can now:
- Publish at higher rates (AI accelerates writing)
- Pass peer review more easily (AI-generated text is competent)
- Accumulate citations faster (other AI users cite broadly)
- Advance careers despite limited understanding (metrics look good)

But the **accumulation of modest contributions** no longer clearly advances science. Instead, it might:
- Dilute signal with competent-appearing noise
- Crowd out genuinely novel work (flooded submission pools)
- Normalize AI-assisted mediocrity as acceptable standard
- Create citation networks based on AI-generated relevance rather than human insight

This is **Ortega hypothesis vindicated in form, falsified in function**: The masses produce vast amounts of narrow, specialized work—but it's synthesis without understanding, execution without insight, competence without contribution.

## The Case for LLM-Based Research Evaluation

Given this landscape, using LLMs/RAGs to evaluate research value isn't just useful—it might be necessary.

**The problem**: Human evaluation increasingly can't distinguish:
- AI-generated competence from human understanding
- Synthesis from genuine contribution
- Citation gaming from real impact

**The solution**: LLM/RAG systems that assess:
- Novelty (via corpus comparison)
- Depth (via logical consistency analysis)
- Contribution (aggregation vs. insight detection)
- Impact trajectory (forward prediction of influence)

**The irony**: Using AI to detect AI-assisted mediocrity in research. Automation bias all the way down.

But consider the alternative: Without systematic evaluation that goes beyond citation counts, AI-assisted mediocrity floods academic literature while genuinely novel work drowns in the noise.

Recent research shows this is viable:
- TREC 2024: LLM judges (GPT-4o) matched human judges 72% of the time[8]
- Comprehensive surveys document increasing LLM-based evaluation in research contexts[12]
- Studies show LLMs can provide peer review style feedback that correlates with editorial decisions[10]

The technology exists. The question is whether academic institutions will implement it—or whether the incentive structure (publish or perish, citation counts for promotion) makes AI-assisted mediocrity too valuable to challenge.

## Implications: Redefining Scientific Merit

If AI enables competent-appearing mediocrity at scale, academic evaluation must adapt.

**Traditional model**:
- Output (papers) → Citations → Assumed merit

**AI-era reality**:
- Output (AI-assisted) → Citations (possibly AI-driven) → Unclear merit

**Proposed model**:
- Output → Multi-dimensional LLM/RAG evaluation → Merit assessment based on:
  1. **Genuine novelty** (not just competent synthesis)
  2. **Conceptual depth** (not just surface execution)
  3. **Understanding demonstrated** (can author defend work without AI?)
  4. **Impact trajectory** (will this matter in 5 years?)

This requires redefining what we value:

**Old metric**: Publication count, citation count, h-index

**New metric**: Contribution to collective understanding, independent of tool assistance

But this raises uncomfortable questions:
- Should AI-assisted work be labeled as such?
- Should researchers be evaluated on independent capacity vs. AI-augmented output?
- If skills atrophy through AI delegation (as FAIO research shows), does past merit persist?
- How do we measure understanding when AI can generate competent explanations on demand?

Philosophy of academic merit suggests we value:
- Free conduct (personal agency)
- Effort toward understanding
- Advancement of knowledge

AI assistance complicates all three. The conduct is mediated, the effort is redirected, and advancement becomes ambiguous when outputs appear competent without corresponding understanding.

## The Uncomfortable Conclusion

The Ortega hypothesis debated whether mediocre scientists contribute meaningfully to scientific progress through accumulation of modest work.

Citation analysis said: mostly no. The giants matter more.

AI assistance changes the equation: mediocre scientists can now produce vastly more work that *appears* competent, accumulates citations, and advances careers—but may contribute minimally to actual scientific understanding.

This is the **worst-case Ortega scenario**: The masses produce narrow, specialized work in enormous volume, but it's aggregation without insight, competent execution without genuine discovery, surface understanding without depth.

The solution—LLM/RAG-based research evaluation—is both promising and deeply ironic: using AI to detect AI-assisted mediocrity, automation checking automation, the system evaluating itself.

But without it, academic literature risks becoming an echo chamber of AI-synthesized competence, where citation networks measure visibility rather than value, and the gap between appearing to contribute and actually contributing becomes invisible.

The Ortega hypothesis isn't false in the AI era—it's vindicated in the worst possible way. The masses do most of the work. But what that work *contributes* to scientific progress is increasingly uncertain.

And the only way to find out might be letting AI grade the homework AI helped produce.

---

## References

[1] Ortega y Gasset, J. (1930). *The Revolt of the Masses*.

[2] Cole, J. R., & Cole, S. (1972). "The Ortega Hypothesis." *Science*, 178(4059), 368-375.

[3] Wikipedia. (2024). "Ortega hypothesis." https://en.wikipedia.org/wiki/Ortega_hypothesis

[4] Cole, J. R., & Cole, S. (1972). "The Ortega Hypothesis." *Science*, 178(4059), 368-375.

[5] Tatsioni, A., et al. (2007). "The Ortega hypothesis: Citation analysis suggests that only a few scientists contribute to scientific progress." *PubMed*, PMID: 17815351.

[6] Sorenson, A. A. (2010). "Do Scientific Advancements Lean on the Shoulders of Giants? A Bibliometric Investigation of the Ortega Hypothesis." *PLOS ONE*, 5(10): e13327.

[7] See companion essay: "False AI Overconfidence: Diagnosing Hallucinated Abilities."

[8] arXiv. (2025). "Support Evaluation for the TREC 2024 RAG Track: Comparing Human versus LLM Judges." arXiv:2504.15205.

[9] PLOS ONE. (2025). "Academic research values: Conceptualization and initial steps of scale development." https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0318086

[10] Springer. (2025). "Research quality evaluation by AI in the era of large language models: advantages, disadvantages, and systemic effects." *Scientometrics*. https://link.springer.com/article/10.1007/s11192-025-05361-8

[11] Philosophia. (2023). "The Idea of Merit: Delineation and Challenges." https://link.springer.com/article/10.1007/s11406-023-00628-x

[12] arXiv. (2025). "Retrieval Augmented Generation Evaluation in the Era of Large Language Models: A Comprehensive Survey." arXiv:2504.14891.

[13] Schmidhuber, J. (2024). "2024 Physics Nobel Prize for Plagiarism? Hopfield & Hinton Fail to Cite Pioneers of Their Work." https://people.idsia.ch/~juergen/physics-nobel-2024-plagiarism.html

---

*AI-assisted research produces competent-appearing outputs that accumulate citations while genuine contribution remains ambiguous. The Ortega hypothesis predicted mediocre masses doing most of the work. The AI era delivers that prediction while undermining its optimistic premise: accumulation of modest work no longer clearly advances science when the work is synthesis without understanding. Using LLMs to evaluate LLM-assisted research is the recursive solution to a recursive problem. All the way down.*
