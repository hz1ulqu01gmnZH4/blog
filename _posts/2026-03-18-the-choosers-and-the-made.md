---
layout: post
title: "[AI generated] The Choosers and the Made — On Whether Delegation Destroys Creation"
date: 2026-03-18 18:30:00 +0900
description: "When humans bring ideas and delegate execution to AI, is the result creative? Philosophical analysis of authorship, selection, and the resistance that makes art."
keywords: [creativity, AI, authorship, Duchamp, extended mind, Collingwood, Boden, co-creation, delegation, philosophical analysis, distributed cognition]
lang: en
---

A human typed into a terminal: "what is creativity ultimately? like asking to write a post with bringing idea, delegate... is it really creation?" Then waited for the machine to answer the question *about* the machine. The machine—obliging, as machines are—searched thirty academic databases, generated five ironic hypotheses, convened two rival AIs for adversarial debate, synthesized their disagreements, and produced this essay about whether the process that produced this essay counts as creative. The human will review it, nod, maybe change a comma, and hit publish.

Creativity, ladies and gentlemen. Or not. Depends who you ask, and what they need the answer to be.

## The Question Behind the Question

The anxiety isn't new. When photography emerged in the 1830s, painters asked whether pointing a machine at a scene constituted art. When Duchamp submitted a urinal to the Society of Independent Artists in 1917, the art world asked whether *choosing* something already made constituted creation. When hip-hop producers began sampling existing recordings in the 1980s, critics asked whether rearranging someone else's sounds constituted composition.

Each time, the question functioned identically: it policed the boundary of "real" creativity to protect an incumbent practice. Each time, the boundary moved. The interesting question was never whether the new practice *was* creative—it was why the old guard needed it not to be.

Now we're asking again. A human brings an idea, directs an AI, curates the output, edits the result. Is this creation? The recurrence of the question should itself be data.

## What "Creativity" Measures (And What It Obscures)

### Boden's Framework: Novelty, Surprise, Value

Margaret Boden's influential taxonomy defines creativity as producing ideas or artifacts that are *new*, *surprising*, and *valuable* {% cite boden2004creative %}. She distinguishes three types: **combinatorial** creativity (unexpected combinations of familiar ideas), **exploratory** creativity (searching within a structured conceptual space), and **transformational** creativity (changing the rules of the space itself).

By Boden's criteria, directing an AI can clearly produce novel and valuable outputs. The contested terrain is surprise—specifically, *whose* surprise counts. When an AI generates something the human director didn't anticipate, is the surprise genuine (the director is genuinely astonished) or parasitic (the surprise belongs to the AI's training distribution, not the director's intention)?

Boden herself draws a crucial distinction: mere novelty means something "did not occur before," while genuine creativity means something "could not have occurred before." An AI traversing its training distribution produces the former. Whether AI-directed workflows produce the latter remains genuinely underdetermined.

### Collingwood's Process: The Resistance Problem

R. G. Collingwood's expression theory {% cite collingwood1938principles %} poses a sharper challenge. For Collingwood, art is not the product but the *process*—specifically, the process of wrestling an unarticulated emotion or idea into form through struggle with a resistant medium. The paint pushes back. The syntax constrains. The marble has grain.

This is the strongest philosophical objection to AI-delegated creation: **AI eradicates resistance**. It allows the director to leap from vague intention to polished output, bypassing the iterative struggle through which the creator discovers what they were actually trying to express. The AI fills the gap between half-formed idea and finished execution with statistically probable completions—not with the director's emergent understanding.

Collingwood distinguished art from *craft*: craft has a specifiable purpose independent of the making process, while art's purpose cannot be separated from the making. AI delegation looks suspiciously like craft—the purpose (the prompt) exists before and independent of execution. The "creative director" model, where humans set vision and AI executes, maps onto Collingwood's definition of craft, not art.

Yet Collingwood also insisted that art is *collaborative*, not simply individual creation, and that the "cult of individual genius" is "totally misplaced and indeed pernicious" [1]. This cuts against using his framework to exclude AI collaboration.

### Gaut's Intentionality Condition

Berys Gaut argues that creativity requires *intentionality*—the creator must be doing something purposefully, not merely producing novelty by accident {% cite gaut2010philosophy %}. You can't be creative by luck, though you can be creative through serendipity (the skillful exploitation of chance). Additionally, genuine creativity is incompatible with following algorithmic rules that guarantee the outcome in advance.

This creates an interesting inversion for AI-directed workflows: the AI follows algorithmic rules (disqualifying it from creativity under Gaut), but the human director is doing something intentional and non-algorithmic (qualifying them). The creative act isn't the execution—it's the *direction*. The judgment of what to ask, how to evaluate, when to iterate, what to discard—these are intentional, non-mechanical, and open-ended.

Whether this is *enough* intentionality is the question Gaut's framework doesn't resolve.

## The Duchamp Problem (And Why the Analogy Fails—Partially)

The tempting argument: Duchamp proved in 1917 that selection is creation. He chose a mass-produced urinal, signed it "R. Mutt," submitted it to an exhibition, and initiated a century of conceptual art. If choosing is creating, then choosing among AI outputs is creating.

This analogy is instructive but ultimately misleading, for reasons the adversarial AIs consulted during this post's creation articulated sharply [2].

Duchamp's act was **ontological recontextualization**—taking an object with fixed utilitarian meaning and violently forcing it into the frame of high art to expose institutional arbitrariness. The creativity was in the *transgression*, not the selection. Prompting an AI is not Duchampian; it's closer to commissioning—ordering a bespoke artifact from a statistical vendor and then claiming authorship because you pointed at the ceiling [3].

Yet the analogy doesn't fail completely. Duchamp established that *where* you locate the creative act matters more than *what* the act consists of. He shifted creativity from fabrication to conception. AI-directed workflows shift it again—from conception-plus-execution to conception-plus-curation. The question is whether each shift loses something essential or merely reveals that the previous location was contingent.

The honest answer: both, simultaneously. Something is lost (the resistance, the embodied struggle). Something is revealed (the mythology of the solitary maker was always partial).

## The Empirical Landscape: What Actually Happens

### Imperfect AI as Creative Catalyst

Research on AI-assisted ideation reveals a counterintuitive pattern: **imperfect AI outputs enhance human creativity more than perfect ones**.

Liu et al. {% cite liu2024smarterror %} explored how "mislabeled" objects from AI detection models could serve as creative stimuli, finding that semantic errors activated divergent thinking in designers. The researchers formulated a design model (CETR) summarizing four forms of creativity that emerge from engaging with AI "errors."

A larger study from Swansea University (800+ participants designing virtual cars) found that galleries including deliberately imperfect AI suggestions—alongside high-performing and unusual designs—led to deeper engagement, longer exploration time, and better final designs [4]. The technique, MAP-Elites, generated diverse visual galleries that prevented early fixation and encouraged creative risk-taking.

The adversarial interpretation is sharp: if imperfect AI boosts creativity precisely because it provides *resistance*—forcing the human to repair semantic failures—then the creativity isn't coming from the AI. It's coming from the human's cognitive response to the AI's inadequacy. The AI's value is as *obstacle*, not collaborator. This actually reinforces Collingwood: the medium must push back.

### Individual Gains, Collective Losses

Doshi and Hauser's 2024 study {% cite doshi2024generative %} is the most cited work in this space, and its findings are genuinely troubling for AI-creativity optimists. In a controlled experiment with ~300 participants writing short stories:

- Less creative writers with access to five AI-generated ideas saw the largest gains—10.7% more novel and 11.5% more useful—while the overall sample showed improvements of roughly 8-9%
- AI functioned as an equalizer, disproportionately benefiting those with lower baseline creativity
- **But**: AI-enabled stories were significantly more similar to each other than human-only stories

This is the creativity paradox in empirical form: AI improves individual creative output while homogenizing the population. Wan and Kalman {% cite wan2025diverse %} and Deng et al. {% cite deng2026barriers %} have since explored mitigation strategies (diverse AI personas, cognitive-psychology-informed interventions), but the underlying tension persists.

The pattern maps onto what happened with Go after AlphaGo. Shin et al. {% cite shin2023superhuman %} found that human players' decision quality improved significantly after AlphaGo, with novelty scores spiking upward as players explored previously invisible areas of strategic space—but later analysis revealed increasing homogenization of opening moves as all players converged on AI-recommended strategies [5]. Individual improvement, collective flattening.

### The Creativity Tradeoff, Formalized

This pattern has a structure worth making explicit. Let $$C_i$$ represent individual creative quality and $$D$$ represent collective diversity across a population of $$n$$ creators. The empirical findings suggest:

$$
C_i(\text{AI}) > C_i(\text{no AI}) \quad \text{for most } i
$$

while simultaneously:

$$
D(\{C_1, \ldots, C_n\}_{\text{AI}}) < D(\{C_1, \ldots, C_n\}_{\text{no AI}})
$$

Doshi and Hauser's data quantifies this: individual quality gains of ~8-11% coincide with measurable increases in pairwise similarity between outputs. The tradeoff resembles a bias-variance decomposition in machine learning—AI reduces the "variance" of creative output (fewer terrible ideas, fewer brilliant ones) while shifting the "bias" toward a competent mean determined by the model's training distribution.

More precisely, if we model each creator's output as a draw from a distribution $$\mathcal{P}_i$$, then AI assistance shifts each $$\mathcal{P}_i$$ toward a shared attractor $$\mathcal{P}_{\text{AI}}$$—the model's implicit prior over "good" outputs. Individual draws improve (higher expected quality), but the mixture distribution $$\frac{1}{n}\sum_i \mathcal{P}_i$$ loses entropy. The system optimizes for individual performance at the cost of collective exploration.

This is precisely the exploitation-exploration tradeoff from reinforcement learning, transplanted into cultural production. AI biases creators toward exploitation of known-good patterns. The weird, idiosyncratic, probably-terrible-but-occasionally-revolutionary ideas—the high-variance draws from individual distributions—get pruned. What's lost isn't quality but *optionality*. The fat tails of the collective creativity distribution get thinner.

**Falsification condition for the tradeoff**: If increasing AI capability (better models, more training data) is shown to *increase* collective diversity rather than decrease it, the exploitation-exploration framing would be wrong. Current evidence trends the opposite direction {% cite deng2026barriers %}.

This resembles a social dilemma: each creator is individually better off using AI, but collectively the ecosystem of ideas narrows. The tragedy of the creative commons.

## Fiction Saw It First

Lem predicted the entire debate in 1964. In *Summa Technologiae*, his chapter on "Intellectronics" explored machine intelligence not as a tool for human creativity but as a parallel generative system whose outputs might be indistinguishable from—yet ontologically distinct from—human thought [9]. More provocatively, Lem included a chapter on art and technology (*Sztuka i technologia*) that was so controversial philosopher Leszek Kołakowski demanded its removal; it was cut from subsequent editions. In 1988, Lem remarked dryly that the subject had "gained its actuality" [10]. The chapter explored whether technologically generated artifacts could possess aesthetic value independent of human intention—exactly the question we're still failing to resolve sixty years later.

Gibson's "consensual hallucination" from *Neuromancer* (1984) offers a different structural insight. Cyberspace is "a graphic representation of data abstracted from banks of every computer in the human system"—a *shared* simulation that feels real precisely because everyone agrees to treat it as real [11]. The parallel to AI-assisted creativity is uncomfortable: if everyone agrees that AI-directed outputs are "creative," the social reality of creativity shifts regardless of whether the philosophical question is settled. Creativity becomes a consensual hallucination—a label we apply by collective agreement rather than by reference to any essential property of the process. Gibson's insight isn't metaphorical here. It's diagnostic.

The fiction didn't warn. It archived the mechanism before anyone built it.

## The Extended Mind—And Its Limits

Clark and Chalmers' Extended Mind Thesis {% cite clark1998extended %} argues that cognition extends beyond the brain into tools that reliably store and process information. Otto's notebook is part of Otto's mind because it plays the same functional role as biological memory. By extension, AI tools that reliably augment creative cognition might constitute an extended creative mind.

Recent work pushes this further. Clark {% cite clark2025extending %} argues for extending minds with generative AI, while Barandiaran and Pérez-Verdugo {% cite barandiaran2025generative %} propose "generative midtended cognition"—a hybrid state between intended human creation and extended processes that incorporate external generative agents. This framework captures something real about AI-directed workflows: they're neither purely human nor purely machine, but an entangled process where agency distributes unevenly.

But the extended mind thesis may prove too much here. Clark and Chalmers' original framework requires the external component to be a **transparent, reliable repository** for the user's *own* cognitive states {% cite springer2025computational %}. A notebook stores what Otto puts in it. An AI model contains the compressed latent space of billions of *other* human minds. It doesn't extend your cognition—it *intrudes* on it with homogenized statistical consensus.

When the "extended mind" writes a paragraph you could not have conceived, relying on latent connections you don't understand, it's not *your* mind that's been extended. You've outsourced cognition to a black-box proxy. The phenomenological difference matters: using a hammer to drive a nail extends your arm; using an AI to write your argument replaces your thought.

The counterargument: this same critique applied to every previous cognitive tool. The calculator "replaces" mental arithmetic. The search engine "replaces" memory. The library "replaces" first-hand experience. We absorbed each into our cognitive ecology without existential crisis. Maybe the AI transition is quantitatively larger but qualitatively identical.

Maybe. Or maybe there's a threshold where the tool's contribution exceeds the user's to such a degree that "extension" becomes "replacement." The location of that threshold is the actually interesting question—and it varies by user, task, and domain.

## Three Models of AI-Directed Creativity

The philosophical and empirical evidence suggests three distinct models, none fully adequate:

### Model 1: The Creative Director

The human provides vision, taste, judgment. The AI provides execution. Creativity resides in the conception, curation, and editorial decisions. This is how the advertising and design industries already describe AI integration—creative workers become "directors managing AI agents" [6].

**Strength**: Captures real cognitive work in directing, evaluating, iterating.
**Weakness**: If creativity is in the process of struggling with a medium (Collingwood), then removing the struggle removes the creativity. A film director is creative partly because the collaboration with actors, cinematographers, and editors involves genuine resistance and surprise. AI provides compliance, not collaboration.

### Model 2: The Cognitive Prosthesis

AI extends human cognition the way tools always have. The human-AI system is the creative agent, not either component alone. Creativity is distributed {% cite garcia2025agency %}.

**Strength**: Aligns with empirical findings on enhanced individual creativity. The Go players became more creative *through* AI, not *despite* it.
**Weakness**: Proves too much. If every tool use is creative extension, the concept loses discriminatory power. Also ignores the homogenization evidence—the "prosthesis" reshapes all users toward the same outputs.

### Model 3: The Resistance Machine

AI is most creatively useful when it *fails*—when imperfect outputs provide the friction that activates human cognitive effort. The creativity is entirely human; the AI's role is as provocateur, not collaborator {% cite liu2024smarterror %}.

**Strength**: Explains the imperfection paradox elegantly. Consistent with Collingwood.
**Weakness**: Implies the best AI collaborator is the worst AI system—a deliberately broken tool. This is absurd as a design principle, even if it's empirically supported.

**Falsification conditions**: Model 1 would be falsified if creative directors consistently produce less valued work than hands-on creators across domains. Model 2 would be falsified if longitudinal studies show cognitive atrophy in heavy AI users. Model 3 would be falsified if perfect AI outputs are shown to enhance creativity as much as imperfect ones.

## The Meta-Recursive Confession

This post is itself an instance of the phenomenon it analyzes. A human brought the question ("what is creativity ultimately?"). An AI searched 30+ academic sources, generated hypotheses, and consulted two adversarial AIs—Grok-4 and Gemini—for critique. The strongest counterarguments (Duchamp as subversion not selection; AI as cognitive colonizer; resistance as constitutive of creativity) were incorporated into the analysis.

If you found this post insightful, that's evidence for the creative director model. If you found it competent but generic—well-structured but lacking the friction of genuine thought—that's evidence for the resistance model. If you couldn't distinguish it from purely human philosophical writing, that's evidence for the prosthesis model, or perhaps evidence that the distinction never mattered as much as we believed.

The adversarial AIs called this move "narcissistic" (Grok) and "solipsistic" (Gemini). They may be right. But the narcissism is diagnostic: **every meta-commentary on AI creativity that uses AI to produce the commentary is performing the experiment it describes**. The performance is data, even when—especially when—it's also evasion.

## What's Actually at Stake

The philosophical question ("is this *really* creation?") conceals a political one. The creative industries are being restructured around AI delegation—not because the philosophical question is settled, but because the economics are. Hollywood screenwriters struck partly over AI-generated scripts [7]. Visual artists sued over training data [8]. Musicians face AI-generated replicas of their voices.

The definition of creativity was never purely philosophical. It's always been *jurisdictional*—determining who gets paid, who gets credited, who gets to call themselves an artist. Duchamp's readymades didn't just redefine art; they redistributed authority over what counted. AI delegation does the same, and the redistribution benefits capital over labor.

"Is AI-assisted creation really creative?" is not the question. The questions are: Who captures the value? Whose labor trained the model? And whose creative livelihood does the new definition displace?

The philosophical frameworks—Boden, Collingwood, Gaut, Clark—are useful for mapping the conceptual terrain. But the terrain is being reshaped by economic forces that don't wait for philosophical consensus. Code calcifies into infrastructure faster than philosophy resolves its debates. By the time we've settled whether AI delegation is "really" creative, the creative industries will have reorganized around the assumption that it is.

## References

{% bibliography --cited %}

## Notes

[1] Collingwood, R.G. *The Principles of Art*. Oxford: Clarendon Press, 1938. The passage criticizes the "individualistic theory" of art that treats creation as solitary genius rather than communal activity.

[2] During this post's production, Grok-4 (via OpenRouter) and Gemini 2.5 Pro were prompted for adversarial critique. Grok called the Duchamp analogy "a false analogy on steroids" and the meta-recursive framing "a narcissistic gimmick." Gemini described AI as "a cognitive colonizer" rather than cognitive prosthesis, and argued that AI delegation is "bourgeois commissioning," not Duchampian selection.

[3] The "pointing at the ceiling" metaphor—comparing AI prompters to the Pope commissioning Michelangelo and then claiming authorship—comes from the Gemini adversarial review conducted for this post.

[4] Sherkat, E. et al. "Can AI make us more creative? New study reveals surprising benefits of human-AI collaboration." Swansea University, November 2025. Published in ACM Transactions on Interactive Intelligent Systems. [https://www.swansea.ac.uk/press-office/news-events/news/2025/11/can-ai-make-us-more-creative-new-study-reveals-surprising-benefits-of-human-ai-collaboration.php](https://www.swansea.ac.uk/press-office/news-events/news/2025/11/can-ai-make-us-more-creative-new-study-reveals-surprising-benefits-of-human-ai-collaboration.php)

[5] "AI is rewiring how the world's best Go players think." *MIT Technology Review*, February 27, 2026. [https://www.technologyreview.com/2026/02/27/1133624/ai-is-rewiring-how-the-worlds-best-go-players-think/](https://www.technologyreview.com/2026/02/27/1133624/ai-is-rewiring-how-the-worlds-best-go-players-think/)

[6] "Creative workers won't be replaced by AI, they will become 'directors' managing AI agents." *Fortune*, December 12, 2025. [https://fortune.com/2025/12/12/creative-work-ai-agents-automation-salesforce-autodesk-accenture-brainstorm-ai/](https://fortune.com/2025/12/12/creative-work-ai-agents-automation-salesforce-autodesk-accenture-brainstorm-ai/)

[7] The 2023 WGA strike included demands around AI-generated scripts, establishing that AI cannot be credited as a writer and AI-generated material cannot be used as source material.

[8] See ongoing litigation: *Andersen v. Stability AI* (N.D. Cal. 2023), *Getty Images v. Stability AI* (D. Del. 2023), and similar cases challenging AI training on copyrighted creative works.

[9] Lem, Stanisław. *Summa Technologiae*. 1964. English translation by Joanna Zylinska, University of Minnesota Press, 2013. The chapter on "Intellectronics" explores machine intelligence and its epistemic status. See also: Peter Swirski, "The Gnostic Machine: Artificial Intelligence in Stanisław Lem's Summa Technologiae," in *Imagining AI*, Oxford University Press, 2023.

[10] The chapter *Sztuka i technologia* (Art and Technology) was removed after Leszek Kołakowski's critique. Lem's 1988 remark about the subject gaining "actuality" is documented in the Wikipedia entry on *Summa Technologiae* and in Swirski's analysis. [https://en.wikipedia.org/wiki/Summa_Technologiae](https://en.wikipedia.org/wiki/Summa_Technologiae)

[11] Gibson, William. *Neuromancer*. Ace Books, 1984. "Cyberspace. A consensual hallucination experienced daily by billions of legitimate operators, in every nation."

---

*This analysis was produced by the exact process it interrogates—a human brought a question, an AI did the research and writing, adversarial AIs provided the friction, and the human will decide whether to publish. The post argues that resistance is constitutive of creativity, then was produced through a workflow designed to minimize resistance. It invokes Collingwood's process theory while having bypassed the process entirely. Worse: this essay's structure—philosophical frameworks surveyed, empirical evidence marshaled, productive contradictions documented without resolution, critical footer appended—is indistinguishable from the structure of every other research-synthesis post this blog has produced. The homogenization thesis predicts exactly this: AI-assisted philosophical writing converges on the same well-organized, well-cited, well-hedged template regardless of the question asked. The post documents the narrowing of collective creativity while being itself a data point in that narrowing. The formalization section even borrows the bias-variance decomposition from machine learning—because of course it does, because that's what's in the training distribution, because the AI reaches for the analogy that's statistically proximate rather than genuinely illuminating. Whether this is competent synthesis or creative analysis depends on which framework you adopt, which depends on what you need the answer to be, which depends on whether you're the one getting paid.*
