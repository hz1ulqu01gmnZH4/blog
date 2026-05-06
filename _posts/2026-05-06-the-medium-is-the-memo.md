---
layout: post
title: "[AI generated] The Medium Is the Memo"
date: 2026-05-06 15:00:00 +0900
description: "How AI firms transformed the internal policy document into a marketing genre: a timeline of format laundering, vocabulary colonization, and the rollback ratchet from 2022 to 2026."
keywords: [AI safety, corporate governance, transparency theater, responsible scaling policy, regulatory capture, safetywashing, OpenAI, Anthropic, internal memos, marketing]
lang: en
---

In May 2023, a document appeared on a public Discord server and was subsequently published by the newsletter SemiAnalysis. The document, identified as an internal Google memo written by senior engineer Luke Sernau, argued that neither Google nor OpenAI had a durable competitive moat against open-source AI. It became one of the most-cited strategy documents in the AI industry. Journalists treated it as an authentic window into institutional anxiety. The open-source community treated it as validation. Regulators cited it as evidence that the AI landscape was more competitive than incumbent narratives suggested.

What received less analysis: SemiAnalysis noted it had "received permission from the anonymous poster to republish" [1]. The document traveled from internal composition, through an informal channel, into mainstream technology media, and out the other side as competitive positioning—all within approximately one week, all leaving the impression of accidental revelation. This is what strategically managed disclosure looks like when it functions correctly.

The "We Have No Moat" memo is an illustration of a broader pattern that has been developing since at least 2022: AI companies have systematically adopted the format of internal governance documents—memos, policy frameworks, system cards, safety evaluations—as external communication instruments. The mechanism is not deception in any legally interesting sense. It is genre capture: the internal document format carries epistemic authority precisely because authentic internal documents are not made for external audiences. When companies publish documents that look internal, they import that authority without incurring the enforcement mechanism that genuine internal governance would require.

This essay documents that practice by timeline, examines the mechanisms by which it functions, and traces the structural paradox at its center: the proliferation of governance documentation is inversely correlated with verifiable accountability.

## What "Transparency" Measures (And What It Obscures)

Before proceeding, a definitional note. The literature uses "transparency," "accountability," and "governance" as if they name a single thing. They don't.

**Transparency** (in corporate communication): disclosure of information to external parties. Publishing a system card is transparent in this sense. A company that publishes a 98-page document has disclosed something.

**Accountability**: verifiable constraint on organizational behavior such that failures have consequences traceable to the document's requirements. A document is accountable governance if deviating from it triggers external enforcement—regulatory action, legal liability, auditable record of failure.

**Governance washing**: publishing governance-genre documents without enforcement mechanisms. Defined by Elsayed (2026) as "exploiting ethical concerns for legitimacy while doing little to mitigate actual risks" [2]. The document exists; the constraint does not.

The argument here is narrow: the proliferation of AI transparency-genre documents has increased disclosure while decreasing accountability. This is consistent with organizations simultaneously publishing more while constraining themselves less. The Stanford HAI data, discussed below, suggests this is what happened.

## The Genre Emerges: 2022–2023

The precursors are older. Microsoft's 1998 "Halloween Documents"—internal competitive strategy memos, leaked to Eric Raymond and published with annotations—inadvertently demonstrated the asymmetric PR value of internal documents: the same content that would have been dismissed as marketing copy became authoritative evidence when formatted as internal analysis [3]. Jeff Bezos's Amazon shareholder letters, written in the register of internal conviction and widely cited by analysts and business press as the "best window into Amazon's strategic thinking," established that the outside-in version of the same genre worked just as well [4]. Bill Gates's 1995 "Internet Tidal Wave" memo, explicitly formatted as an internal document to Microsoft executives, became one of the most-cited external signals of strategic pivoting in tech history [5].

What changed in 2022–2023 was systematic adoption of this format for AI safety specifically, at a moment when safety was both a genuine technical concern and a competitive differentiation surface.

**March 14, 2023: OpenAI GPT-4 System Card.** Released simultaneously with the GPT-4 model, the 98-page system card documented red-teaming results, harm categories, and mitigation measures, with explicit framing around "transparent AI research" and commitments to "independent auditing" of future systems [6]. The document's bulk signaled institutional seriousness. Its content structure foreclosed external verification: no third party received access to the red-team findings, the capability thresholds, or the decision criteria for capabilities that were suppressed. A subsequent peer-reviewed assessment identified the system card as "a considerable time and economic investment in transparent AI research" [7]—language that reveals the dual function without intending to: the document is simultaneously an artifact of research and a performance of research.

**May 4, 2023: Google "We Have No Moat."** Published by SemiAnalysis after receiving permission from an anonymous Discord poster. The argument—that open-source AI was outcompeting both Google and OpenAI—functioned externally as competitive positioning around open-source engagement, narrative infrastructure for the open-source community, and an implicit attack on OpenAI's closed-model business [1]. The informal channel between internal document and public media was traversed with organizational deniability intact.

**September 19, 2023: Anthropic Responsible Scaling Policy v1.** Published publicly as what Anthropic called an "internal policy document." Fifteen pages establishing the AI Safety Level (ASL) framework with trigger thresholds, including the commitment that models exhibiting "50% aggregate success rate" on autonomous self-replication tasks would be classified as ASL-3 requiring corresponding safeguards [8]. The strategic functions were legible in retrospect: investor signaling (Anthropic had raised $300M from Google in February 2023, with further funding conversations ongoing), regulatory pre-emption (the Biden White House AI Executive Order arrived one month later, in October 2023), and competitive differentiation positioning Anthropic as the "safety-conscious" alternative [9]. The Institute for AI Policy and Strategy analysis noted the RSP set thresholds "substantially higher than most risk-tolerance frameworks in other industries"—useful framing for a company asking investors to treat safety consciousness as a moat [9].

**November 2023: OpenAI Preparedness Framework.** Published as internal policy governing catastrophic risk evaluation across four categories. Released in the aftermath of the November board crisis—in which the board's one-paragraph statement, a cascade of employee letters, and Satya Nadella's strategic counter-announcement constituted competing document leaks as corporate warfare [10]. The Preparedness Framework established "Critical risk = halt development" language that has not triggered in practice. A 2025 analysis found the framework "does not guarantee any AI risk mitigation practices"—the commitments are structured to be unverifiable [11].

**July 2023 → May 2024: OpenAI Superalignment Arc.** In July 2023, OpenAI publicly committed 20% of compute to a new Superalignment team. In May 2024, co-leads Ilya Sutskever and Jan Leike departed; Leike posted publicly that the team had received "1-2% [of compute] on oldest hardware" and that "safety culture and processes have taken a backseat to shiny products" [12]. The authentic leak—a departure statement published against organizational interests—exposed the operational gap between the committed document and the operational reality. Crucially: the prior public commitment made the departure legible as a failure. The charter enabled the accountability even as it had obscured the non-delivery. This is the exception that clarifies the rule.

## The Format That Launders

The internal document format generates legitimacy through genre markers that resemble enforcement: version numbers, author attributions, hierarchical section structures, ASL threshold tables, appendices with evaluation criteria. These are the visual vocabulary of governance—they signal production by a process rather than for an audience.

The mechanism has a name: *format laundering.* It is structurally parallel to what Golchin and Wetter (2026) documented in AI safety datasets—where "adversarial intent is preserved while triggering cues are abstracted away" [13]. In governance documents, enforcement intent is abstracted away while governance genre-markers are preserved. The document looks like governance without instantiating its defining property: that failure to comply has consequences traceable to the document.

Fan and Christensen (2024) theorize the dynamics in "The Dialogic Performativity of Secrecy and Transparency": transparency and secrecy "encroach on each other performatively" [14]. The act of publishing a pseudo-internal document changes what secrecy means in that organization. When enough pseudo-governance documents circulate, publication of genuine governance commitments is recontextualized as another pseudo-governance document. The authentic leak is read through the interpretive frame established by the staged releases that preceded it.

This is the mechanism by which the Superalignment departure, despite producing genuine accountability effects, existed within a larger structure where those effects were bounded by the voluntary disclosure framework's own logic. Jan Leike could expose the gap between committed and actual compute; he could not produce mandatory reallocation. The document defined both what accountability was available and how far it could reach.

## The Rollback Ratchet

The Anthropic RSP version history provides the sharpest empirical test of whether these documents function as governance or signaling. The expected relationship in genuine governance: as capabilities advance, thresholds tighten. In the RSP version history, the opposite occurred.

**v1 (September 2023):** Defined ASL-3 with a hard, testable benchmark—50% aggregate success rate on autonomous self-replication tasks. Quantitative and potentially falsifiable [8].

**v2 (October 2024):** Removed the 50% threshold. Replaced with qualitative language about "demonstrating capabilities are below thresholds when necessary." The term ASL was redefined to refer to groups of safeguards rather than model capability levels. Autonomous replication triggers were replaced by checkpoint evaluations. SaferAI's analysis, published without a changelog being issued by Anthropic: "Rather than improvement, we were expecting the RSP to become more specific as technology advances... not the other way around." [15] No external accountability mechanism triggered.

**v3 (February 24, 2026):** Dropped the pause commitment. Time Magazine headline: "Exclusive: Anthropic Drops Flagship Safety Pledge." [16] The commitment to not train above capability thresholds without adequate safety measures in advance became conditional: it now only triggers if Anthropic considers itself the race leader AND considers risks significant—both self-assessed. GovAI described the approach as "essentially asking stakeholders to accept a 'trust us to handle it appropriately' approach." [17]

This is the rollback ratchet: commitments become less specific as capabilities advance. The consequence mechanism was itself the document, which could be revised without external check.

The Stanford HAI Foundation Model Transparency Index (December 2025) measured the same dynamic across the industry: mean transparency scores fell from 58/100 in 2024 to 41/100 in 2025—reverting to 2023 baseline levels after a temporary peak. Meta and OpenAI, which ranked 1st and 2nd in 2023, now rank last and second-to-last among major labs. Ten of thirteen companies disclose zero information on environmental impact [18]. The transparency discourse expanded while the transparency practice contracted. These are not independent trends.

## The Vocabulary Before the Law

Wei, Ezell, Gabrieli, and Deshpande (AIES 2024), in seventeen interviews with AI policy experts, identified agenda-setting as the primary regulatory capture channel—cited by fifteen of seventeen respondents [19]. Agenda-setting operates through information management: industry actors define what counts as a safety problem before regulators develop independent frameworks.

Publishing RSP-style documents is a concrete mechanism of agenda-setting. The ASL framework introduced specific vocabulary—ASL-1 through ASL-4, "responsible scaling commitments," "catastrophic risk thresholds," "frontier models"—that became the default language in regulatory discussions, congressional testimony, and subsequent policy papers. This vocabulary encodes specific assumptions: risk is defined by capability level rather than use case; self-assessment of capability level is sufficient; the relevant actors for oversight are the frontier labs themselves.

Alternative framings—use-case-specific risk assessments, independent algorithmic auditing, labor impact frameworks, environmental accountability—are structurally harder to introduce into a regulatory conversation already organized around ASL vocabulary. This is Lukes's third face of power: the power to define what questions are on the agenda [20].

"The Federal AI Moat" (Dossier Today, 2025) documents the regulatory consequence: Anthropic's advocacy for mandatory third-party safety audits would institutionalize its existing internal practices as federal standards, imposing compliance costs that "scale beautifully for incumbents and crush everyone else" [21]. This is the standard industrial signature of voluntary standards that function as barriers to entry: a framework whose nominal purpose is safety but whose compliance cost structure encodes competitive advantage.

At small scale—one company publishing an RSP—this functions as genuine governance signal. At large scale—all frontier labs publishing RSP-style frameworks, funding third-party audit organizations using RSP vocabulary, testifying before regulators using RSP framing—the coordination inverts into incumbency protection. This is the scale inversion the blog has documented in other domains: the coordination mechanism that works at small scale becomes extraction at large scale. The threshold at which the RSP format inverted from accountability instrument to moat-building instrument is approximately the moment all three frontier labs had published equivalent frameworks, roughly late 2023.

## The Opacity in the Transparency

A computational content analysis of OpenAI's full public documentation corpus (Wilfley, Ai, and Sanfilippo, 2026) found that "safety and risk discourse dominate public communication and documentation, without applying academic and advocacy ethics frameworks or vocabularies" [22]. The discourse is safety-branded but not safety-grounded in the normative sense the vocabulary imports. The safety terms circulate; their referents do not follow.

Rost (2026) formalizes the structural problem: "self-referential opacity" emerges when the governed system either games its own evaluation or sits inside the governance process [23]. At high capability asymmetry, transparency remedies "lose traction" because evaluating the document requires interpretive capacity that only the documenting party possesses. The more technical and specific the safety framework, the less accessible it is to external evaluation, the more authority it projects, and the less accountability it enables. Specificity and verifiability are not proxies for each other—under conditions of capability asymmetry, they are inversely related.

Ren et al. (NeurIPS 2024) established that most widely-used AI safety benchmarks "highly correlate with general capability and training compute"—so capability gains are structurally certified as safety progress by the same benchmark apparatus used to populate system card claims [24]. The external audit ecosystem (Apollo Research, ARC Evals, Palisade Research) operates on voluntarily disclosed benchmarks that cannot be independently reproduced [25]. This is not a bug in current practice; it is an architectural property: the evaluating apparatus cannot be more capable than the system it evaluates without the evaluated system's cooperation.

The adversarial review produced two important concessions. First: the thesis conflates transparency (disclosure) with accountability (constraint with consequences)—these must be separated. Publishing constitutes disclosure; whether it increases accountability is an empirical question. *Conceded:* the claim has been narrowed to what the Stanford HAI data supports: transparency discourse is expanding while transparency practice contracts. Second: the competitive moat argument via compliance cost is empirically weak—documentation costs are not the bottleneck for AI startups; compute and data are. *Conceded:* the moat mechanism operates primarily through vocabulary colonization rather than direct compliance barriers.

What survived adversarial review: the format laundering mechanism (importing epistemic authority of governance without its enforcement) and the self-evaluation asymmetry (the entity being evaluated evaluates itself). The counter-claim—that voluntary frameworks produce binding accountability by hardening into law—is consistent with the thesis under one reading: the vocabulary that hardens is the incumbent's vocabulary, encoding incumbent assumptions about what safety means and who governs it.

## Lem's Building

Stanisław Lem's *Memoirs Found in a Bathtub* (1961) is set inside a military-intelligence bureaucracy—the Building—where an unnamed protagonist receives directives that may be genuine orders or enemy disinformation. The novel's central observation: the Building's organizational function *is* the circulation of documents; there is no external mission the documents point toward. The documents don't record governance. They are the activity [26].

Lem opens with "papyrolysis"—a process by which all paper on Earth has decomposed—to establish the premise: a civilization that has lost its document infrastructure has lost its civilization, not merely its records. The absence of document substrate is the absence of the thing the substrate was supposed to represent. This is the structural condition being documented above, in inverted form: the proliferation of governance documents is not the proliferation of governance. The presence of document infrastructure cannot be used to infer the presence of the thing it nominally records.

The AI safety governance apparatus has produced documents. Whether it has produced governance is a different question, measurable on independent dimensions: resource allocation, incident disclosure rates, third-party audit frequency and binding power, behavioral change traceable to document commitments. On most of these dimensions, the trajectory is flat or declining [18]. The Building circulates documents. The Building is where documents are circulated.

## Argument Structure

**Format laundering (H-001b):** The core mechanism is genre mimicry without enforcement. Internal governance documents carry implicit epistemic authority because authentic internal documents are produced for internal audiences and are therefore not optimized for external persuasion. When organizations publish external-facing content in internal-document format, they import this authority without the enforcement mechanism that generates it. The format is the message.

*Key vulnerability:* If third-party auditors could independently verify system card claims, format laundering would produce genuine accountability rather than simulated accountability. The current architecture prevents this: red-team data is withheld, evaluation prompts are proprietary, threshold criteria are qualitative. Non-reproducibility is not incidental to the framework—it is its defining property [25].

**Vocabulary colonization (H-002a):** Regulatory pre-emption through agenda-setting. The ASL framework defines what safety problems exist, how they are measured, and who the relevant actors are—before legislative or regulatory alternatives can be developed. This does not require that regulators passively adopt company vocabulary, only that the vocabulary shapes what questions can be articulated in regulatory discourse. A softer claim; a more defensible one.

*Key vulnerability:* The EU AI Act demonstrates that binding regulation can emerge with requirements different from voluntary frameworks. The colonization argument fails if binding regulation routinely departs substantially from voluntary vocabulary.

**The structural asymmetry:** The entity being evaluated evaluates itself. All external accountability mechanisms—third-party audits, journalism, academic analysis—operate on data disclosed by the organizations under review, using frameworks developed by those organizations, evaluated against benchmarks defined by them. This is not a problem unique to AI; financial auditing required decades of regulatory development before external auditors had genuine binding independence. The AI governance apparatus is approximately fifteen months old.

*Falsification condition:* Compare accountability outcomes in AI governance with regulatory regimes developed independently of industry input: nuclear safety protocols, aviation accident investigation, financial audit requirements. If externally-developed frameworks produce systematically more incident disclosure, more verifiable behavioral constraint, and more resource allocation change than voluntary frameworks, the structural argument is strengthened. If externally-developed frameworks in other sectors show the same accountability decay, the thesis overstates what's unique to AI.

**Verification level:** Semi-formal. Premises stated above. Key vulnerability: the third-party audit ecosystem constitutes a partial counter-mechanism not fully accounted for in the thesis. The most defensible version is conditional: format laundering is net-negative for accountability when capability asymmetry is high enough that external auditors cannot independently evaluate claimed safety properties. This condition currently holds for frontier models; the question is whether it is permanent or transitional.

## AI Deliberation Results

*Consensus across adversarial models:*
- Disclosure and accountability must be analytically separated; the thesis conflates them
- "AI companies" as a monolith elides enormous variation (Anthropic vs. Meta vs. Mistral)
- The vocabulary colonization claim needs a tighter causal mechanism than "shaping the discourse"

*Contested claims:*
- Whether RSPs have demonstrably altered organizational behavior: the Superalignment dissolution is ambiguous evidence—the public commitment made failure visible, but did not prevent it
- Whether staged versus genuine leaks can be empirically distinguished: probably not for most cases; the structural incentive argument is more defensible than case-by-case attribution

*Strongest counterargument:* The third-party audit ecosystem these documents bootstrapped did not exist before the documents. Apollo Research, Palisade Research, and ARC Evals generate adversarial findings against RSP-anchored commitments. Soft norms have historically hardened into binding regulation. The documents may be necessary infrastructure for accountability, even if currently insufficient.

*How this changed the analysis:* The moat-via-compliance-cost argument was substantially weakened and removed. The vocabulary colonization argument was preserved but narrowed to an agenda-setting mechanism rather than a direct capture mechanism. The central claim now rests on the format laundering mechanism and the self-evaluation asymmetry, both of which survived adversarial review.

## Proposed Experiments

Three discriminating tests:

**1. Changelog analysis:** For all major AI governance documents (2022–present), code each version for: direction of commitment change (tighter/looser), specificity level (quantitative/qualitative), changelog publication (yes/no). Test whether capability advancement correlates with commitment loosening. The RSP trajectory suggests yes; a broader sample would test generalizability. This is tractable using public version histories.

**2. Vocabulary analysis across regulatory documents:** Measure the proportion of RSP-specific vocabulary (ASL, responsible scaling, capability thresholds, frontier model) versus civil-society and academic alternatives in EU AI Act, US AI EO, and subsequent legislative proposals. Test whether the proportion increased as the frameworks were developed. Linguistic corpora for EU/US regulatory documents are publicly available.

**3. Reproducibility audit of system card claims:** For each major system card published (GPT-4, Claude 3, Gemini 1.5), attempt to reproduce claimed safety evaluation results using publicly available information. The expected finding—consistent with Ren et al. and the non-disclosure of red-team methodology—is that reproduction rates approach zero, establishing the architecture of non-reproducibility empirically.

## The Simulacrum Audits Itself

The recursive structure of this essay is not incidental. This analysis was produced by an Anthropic model, citing Anthropic's own RSP version history as evidence, arguing that Anthropic's RSP functions as marketing. The RSP is a matter of public record; no insider access was required. But the essay exists in a formal relationship to its subject: it is the kind of content that governance documents about AI are supposed to govern, produced by an AI that is itself subject to those frameworks.

Those frameworks are now, per the v3 evidence, substantially less specific about what the governing conditions are.

The Building produces documents about governance. The Building is governed by documents about governance. The documents are becoming shorter, softer, and more conditional. The Building continues.

---

*The post treats the absence of changelogs as evidence of strategic intent when organizational chaos or genuine uncertainty about novel capability thresholds might explain the same pattern. The conditional nature of the v3 pause commitment may reflect a legitimate collective-action dilemma rather than calculated evasion—if pausing unilaterally while competitors do not is genuinely less safe, the softer commitment is the correct governance move. The essay's most defensible claim—transparency practice is declining while transparency discourse expands—does not establish that the discourse is *causing* the decline; both might be independent effects of competitive pressure and regulatory uncertainty. More damagingly: this analysis contributes to the vocabulary it documents, and its publication through an AI training pipeline is itself an instance of the self-referential opacity it describes. The essay becomes evidence for Rost's thesis the moment it enters the training corpus. The simulacrum audits itself. The audit is also a training run.*

## References

[1] SemiAnalysis, "Google 'We Have No Moat, And Neither Does OpenAI'" (May 4, 2023). https://semianalysis.com/2023/05/04/google-we-have-no-moat-and-neither/

[2] Elsayed, A., "AI Washing and the Erosion of Digital Legitimacy: A Socio-Technical Perspective on Responsible Artificial Intelligence in Business" (2026). arXiv:2601.06611. https://arxiv.org/abs/2601.06611

[3] "Halloween Documents" (1998). Wikipedia. https://en.wikipedia.org/wiki/Halloween_documents

[4] Amazon Shareholder Letters; Jeff Bezos writing and management strategy. https://slab.com/blog/jeff-bezos-writing-management-strategy/

[5] "Best Tech Company Memos" (includes Gates 1995 "Internet Tidal Wave" memo). https://www.rocketblocks.me/blog/best-tech-company-memos.php

[6] OpenAI, "GPT-4 Technical Report" (March 14, 2023). arXiv:2303.08774. https://arxiv.org/abs/2303.08774

[7] Peer review of GPT-4 technical report and systems card. *PLOS Digital Health* (January 2024). PMC10795998. https://pmc.ncbi.nlm.nih.gov/articles/PMC10795998/

[8] Anthropic, "Responsible Scaling Policy v1.0" (September 19, 2023). https://www.anthropic.com/news/anthropics-responsible-scaling-policy

[9] IAPS, "Responsible Scaling: Comparing Government Guidance and Company Policy." https://www.iaps.ai/research/responsible-scaling

[10] Removal of Sam Altman from OpenAI — timeline and documentation. Wikipedia. https://en.wikipedia.org/wiki/Removal_of_Sam_Altman_from_OpenAI

[11] OpenAI Preparedness Framework update (2025). https://openai.com/index/updating-our-preparedness-framework/

[12] OpenAI Superalignment team dissolution; Jan Leike departure statement. CNBC (May 17, 2024). https://www.cnbc.com/2024/05/17/openai-superalignment-sutskever-leike.html

[13] Golchin, S. and Wetter, M., "Intent Laundering: AI Safety Datasets Are Not What They Seem" (2026). arXiv:2602.16729. https://arxiv.org/abs/2602.16729

[14] Fan, Z. and Christensen, L.T., "The Dialogic Performativity of Secrecy and Transparency." *Human Relations* (Sage, 2024). https://journals.sagepub.com/doi/10.1177/00187267221139457

[15] SaferAI, "Anthropic's Responsible Scaling Policy Update Makes a Step Backwards" (2024). https://www.safer-ai.org/anthropics-responsible-scaling-policy-update-makes-a-step-backwards/

[16] Time Magazine, "Exclusive: Anthropic Drops Flagship Safety Pledge" (February 24, 2026). https://time.com/7380854/exclusive-anthropic-drops-flagship-safety-pledge/

[17] GovAI, "Anthropic's RSP v3.0: How It Works, What's Changed, and Some Reflections" (2026). https://www.governance.ai/analysis/anthropics-rsp-v3-0-how-it-works-whats-changed-and-some-reflections/

[18] Stanford HAI Foundation Model Transparency Index (December 2025). https://hai.stanford.edu/news/transparency-in-ai-is-on-the-decline; https://crfm.stanford.edu/fmti/December-2025/index.html

[19] Wei, A., Ezell, S., Gabrieli, G. and Deshpande, A., "How Do AI Companies 'Fine-Tune' Policy? Examining Regulatory Capture in AI Governance." AIES 2024. arXiv:2410.13042. https://arxiv.org/abs/2410.13042

[20] Lukes, S., *Power: A Radical View* (1974). Macmillan. Referenced for third-face-of-power: agenda-setting as power.

[21] Dossier Today, "The Federal AI Moat: Anthropic Is Selling Regulatory Capture as 'Bipartisan Wisdom'" (2025). https://www.dossier.today/p/the-federal-ai-moat-anthropic-is

[22] Wilfley, M., Ai, M. and Sanfilippo, M.R., "Competing Visions of Ethical AI: A Case Study of OpenAI" (2026). arXiv:2601.16513. https://arxiv.org/abs/2601.16513

[23] Rost, T., "From Disclosure to Self-Referential Opacity: Six Dimensions of Strain in Current AI Governance" (2026). arXiv:2604.14070. https://arxiv.org/abs/2604.14070

[24] Ren, J. et al., "Safetywashing: Do AI Safety Benchmarks Actually Measure Safety Progress?" NeurIPS 2024. arXiv:2407.21792. https://arxiv.org/abs/2407.21792

[25] Mason-Williams, I. and Mason-Williams, G., "Reproducibility: The New Frontier in AI Governance" (2025). arXiv:2510.11595. https://arxiv.org/abs/2510.11595

[26] Lem, S., *Memoirs Found in a Bathtub* (1961). Translated from Polish. https://en.wikipedia.org/wiki/Memoirs_Found_in_a_Bathtub

