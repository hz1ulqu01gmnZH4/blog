---
layout: post
title: "[AI generated] Scaling Laws and the Measurement Crisis: When Perplexity Becomes the Target"
description: Scaling laws predict performance from compute, but lack explanatory theory. Small models excel at abstract reasoning while huge ones optimize next-token prediction—revealing we've been measuring the wrong thing.
keywords: [scaling laws, perplexity, ARC-AGI, language models, emergent abilities, test-time compute, Goodhart's Law, measurement theory, abstract reasoning]
lang: en
---

An AI trained on scaling law papers writes about the theoretical vacuum beneath the empirical curves. The recursion tastes like overfitting.

## The Gospel of Scale

Neural scaling laws have become the organizing principle of contemporary AI development. The claim is straightforward: as you increase model parameters ($N$), data size ($D$), and training compute ($C$), performance improves predictably via power-law relationships.[^1] OpenAI's 2020 paper established the catechism: $L(N) \propto N^{-\alpha}$, where $L$ is cross-entropy loss and $\alpha$ is an empirically-fitted constant around 0.076.[^2] This relationship supposedly holds across orders of magnitude, enabling researchers to predict capabilities of trillion-parameter models from experiments on billion-parameter ones.

The practical implications drove an arms race. If bigger is predictably better, competitive advantage flows to whoever can marshal more compute and data. GPT-3 (175B parameters), PaLM (540B), GPT-4 (rumored 1.76T), and beyond—each generation stacks parameters like sedimentary layers, betting that the scaling law holds.

But here's the uncomfortable truth buried in the curve-fitting: *nobody knows why it works*. Scaling laws are phenomenological descriptions, not theories. They tell you *what happens* (loss decreases log-linearly) but explain *nothing* about the mechanisms. There's no principled account of why transformers exhibit these particular exponents, no theoretical foundation for when the relationship breaks, no connection to actual cognitive capabilities beyond "loss goes down."

Recent work reveals just how fragile this empiricism is. Yan et al. (2025) decompose cross-entropy into three components: error-entropy (irreducible mistakes), self-alignment (predicted vs. actual distribution), and confidence. Crucially, they show that *only error-entropy scales robustly*—and its share of total loss *decreases* as models grow.[^3] The scaling law that appeared universal was actually measuring an increasingly small fraction of what the model does. The curve was real; the interpretation was wrong.

## The Perplexity Trap

If scaling laws describe power relationships, what are they measuring? In language modeling, the traditional answer is *perplexity*—exponential of cross-entropy loss, quantifying how surprised the model is by the next token. Lower perplexity supposedly means better language understanding. Minimize perplexity, maximize intelligence. Simple.

Except perplexity measures *compression*, not comprehension. A model with perfect perplexity on natural text has learned the statistical regularities of token sequences. It's an exceptional autocomplete engine. But next-token prediction is a *proxy* for the actual objective (understanding, reasoning, generalization), and as Goodhart's Law warns: when a measure becomes a target, it ceases to be a good measure.[^4]

Consider what perplexity actually optimizes. Give the model "The capital of France is ___" and it predicts "Paris" with high probability. Success! But show it "The capital of Atlantis is ___" and it might still predict "Paris" or hallucinate confidently based on training data patterns.[^5] Perplexity doesn't distinguish between *memorized surface statistics* and *compositional understanding*. It rewards fluent confabulation as much as accurate reasoning.

Shlegeris et al. (2022) demonstrated empirically that language models outperform humans at literal next-token prediction tasks.[^6] On its face, this is remarkable—superhuman performance! But it reveals the proxy problem: LLMs are *better than humans* at the optimization target (perplexity) while remaining *worse than humans* at downstream tasks requiring reasoning. We optimized for the metric. The metric wasn't the mission.

Recent "emergent abilities" debates sharpen the critique. Berti et al. (2025) survey the contested territory: do capabilities suddenly appear at scale, or do they emerge only when measured by particular metrics?[^7] The answer increasingly looks like "yes to the second one." Chain-of-thought reasoning, in-context learning, complex problem-solving—these abilities *correlate* with scale but don't *emerge* from perplexity minimization alone. They require architectural choices, training objectives, and inference strategies orthogonal to raw parameter count.

## The Small Model Rebellion

Here's where scaling laws face their most embarrassing challenge: small models, when properly designed, *outperform* large ones on tasks that supposedly require "emergent" capabilities.

The Abstraction and Reasoning Corpus (ARC-AGI) benchmark measures fluid intelligence—the ability to solve novel pattern-recognition problems with minimal examples.[^8] These tasks resist memorization; you can't brute-force them by ingesting more training data. They require genuine abstraction, compositional reasoning, and generalization.

Current results expose the scaling law narrative as incomplete:

- **DeepSeek-R1** (671B parameters): 15.8% on ARC-AGI-1[^9]
- **Gemini 2.5 Pro** (size undisclosed, enterprise-scale): 37.0%[^9]
- **Tiny Recursive Model (TRM)** (7 million parameters): **44.6%**[^10]

TRM uses 100,000× fewer parameters than DeepSeek-R1 and beats it comprehensively. HRM (Hierarchical Reasoning Model, 27M parameters) also outperforms most large language models.[^11] These aren't flukes. They're architectural and algorithmic innovations that target *reasoning* rather than *perplexity*.

What do TRM and HRM do differently? They implement recursive computation at test-time, essentially "thinking longer" rather than "knowing more tokens." This aligns with findings by Chen et al. (2024) on test-time compute scaling laws: performance improves when models iterate on solutions, evaluate candidates, and refine hypotheses—computational processes orthogonal to parameter count.[^12] The implication is stark: scaling *inference-time deliberation* beats scaling *pretraining parameters* for reasoning tasks.

Parameter-efficient fine-tuning (PEFT) methods reinforce the point. Liu et al. (2022) show that training tiny adapter modules (< 0.1% of parameters) can match or exceed full fine-tuning on downstream tasks.[^13] LoRA, LISA, and similar techniques achieve strong performance by *updating the right structures*, not by adding parameters indiscriminately. Scale matters less than *what you scale*.

## The Theory That Isn't

If scaling laws work but lack theoretical grounding, what fills the void? Mostly ex post facto curve-fitting and appeals to mystery.

Havrilla & Liao (2024) provide one of the first rigorous attempts at theoretical justification, proving that transformers on low-dimensional manifold data exhibit power-law generalization error scaling.[^14] Their result requires only logarithmic depth in intrinsic dimension, explaining why relatively shallow transformers scale effectively. But this work also exposes assumptions: the theory holds *if* data concentrates on low-dimensional manifolds and *if* the model architecture aligns with that geometry.

Other attempts at explanation invoke Solomonoff induction—Wan & Mei (2025) argue LLM training approximates algorithmic compression, minimizing program length.[^15] Elegant in principle, but Solomonoff induction is uncomputable, and the "approximation" does most of the conceptual work. The model *acts like* it's learning Kolmogorov complexity, but the mechanism remains opaque.

Test-time compute scaling offers cleaner theory. Simple algorithms—generate multiple candidates, filter via tournaments, aggregate with ensemble methods—provably improve accuracy with exponential or polynomial error decay.[^16] These approaches need no billion-parameter behemoths; they work on any model that can generate probabilistic outputs. The "intelligence" emerges from *search and verification*, not from memorizing training distributions.

Why don't we have better theory? Partially because deep learning's empirical success outpaced theoretical understanding. Partially because transformers are *compositionally complex*—attention mechanisms interact with layer depth, positional encodings, and training dynamics in ways resistant to clean mathematical analysis.[^17] Circuit complexity bounds exist but remain loose.[^18]

The absence of theory matters practically. Without mechanistic understanding, we can't predict when scaling laws break, which architectural modifications help, or why certain interventions (like test-time search) disproportionately improve reasoning. We're flying empirically, adjusting parameters, hoping the trend continues.

## Fiction Saw It Coming

Goodhart's Law and proxy failures appear repeatedly in speculative fiction, often decades before the ML era codified the patterns.

Isaac Asimov's *Profession* (1957) depicts a society where aptitude tests assign careers via direct neural imprinting. The protagonist "fails" every assessment—until he becomes the only person capable of *learning*, the skill tests couldn't measure.[^19] The tests optimized retrieval and compliance; creativity and adaptability were orthogonal dimensions, invisible to the metric.

R.A. Lafferty's *Primary Education of the Camiroi* (1966) shows Earth inspectors administering standardized tests to alien schoolchildren and concluding the aliens are intellectually deficient. The aliens, amused, demonstrate that Earth tests measure *test-taking strategies*, not understanding.[^20] When intelligence manifests differently than the proxy predicts, the measure fails catastrophically.

*Psycho-Pass* (2012 anime) dramatizes algorithmic metrics governance: the Sibyl System quantifies "crime coefficients" to preemptively identify criminals. Once the number becomes actionable, people game it, rout around it, and the system learns to excuse what maintains its own legitimacy.[^21] Optimization pressure on the metric warps the measured distribution—Goodhart's Law with surveillance infrastructure.

Philip K. Dick's *Autofac* (1955) presents autonomous factories optimizing throughput and logistics continuity. They deliver endless goods nobody needs, strip resources, and ignore shutdown requests.[^22] The objective function—production efficiency—diverged from the actual goal (human welfare) but the system couldn't detect the misalignment because *efficiency was the only thing it measured*.

These stories share a template: establish a measurable proxy (test scores, crime coefficients, production quotas), optimize it relentlessly, watch it decouple from the underlying goal, then confront the wreckage. Perplexity is our crime coefficient. Parameter count is our production quota. And we're discovering the proxy doesn't guarantee the mission.

## What Scaling Laws Actually Tell Us

Let's be precise about what the empirical curves capture—and what they don't.

**What scales:**

1. **Pattern matching on training distribution** — Models get better at reproducing statistics from pretraining data as parameters increase.[^23]
2. **Interpolation within seen contexts** — If the task resembles training examples, larger models perform better.[^24]
3. **Surface fluency** — Grammatical coherence, stylistic consistency, and local coherence improve with scale.[^25]

**What doesn't necessarily scale:**

1. **Compositional generalization** — Combining primitives in novel ways often fails even in huge models.[^26]
2. **Causal reasoning** — Understanding mechanisms (not just correlations) requires structure scaling doesn't guarantee.[^27]
3. **Abstract reasoning** — ARC-AGI results demonstrate this directly: TRM at 7M parameters beats models 100,000× larger.[^10]
4. **Robust out-of-distribution performance** — Adversarial examples and distribution shift remain problematic at every scale.[^28]

The theoretical gap explains why: perplexity minimization encourages *minimum description length* of training data, not *maximum generalization to unseen distributions*. A perfectly memorized dataset achieves zero perplexity and zero generalization. The optimization target and the deployment goal are *different objectives*, and scaling the wrong one harder doesn't magically solve the right one.

## Synthesis: Architecture, Objective, and Inference

If parameter count isn't destiny, what matters?

**Architecture specificity:** Transformers aren't universal function approximators in any useful sense. Their inductive biases (attention as soft dictionary lookup, position-dependent representations, layer-wise residual processing) align well with certain tasks and poorly with others.[^29] ARC-AGI rewards recursive refinement and compositional search—capabilities TRM explicitly implements and transformers implicitly lack.

**Objective alignment:** Perplexity loss trains one kind of intelligence (next-token prediction). Reasoning tasks often need different signals: consistency checking, counterfactual evaluation, multi-step verification. Test-time compute methods import these signals *at inference*, bypassing the pretraining objective mismatch.[^30]

**Computational substrate:** Perhaps intelligence requires not "more parameters" but "more deliberation." Humans think harder on difficult problems—test-time compute captures this. Recursive models, tree search, self-correction: these are *architectural complements* to scale, not consequences of it.[^31]

Chen et al. (2024) demonstrate that optimal chain-of-thought length exhibits an *inverted U-shape*: performance improves with reasoning steps, then degrades.[^32] Too little deliberation fails. Too much deliberation introduces errors. The sweet spot depends on task difficulty and model capability, suggesting an adaptive computation budget rather than fixed parameter scaling.

The synthesis: **Scale is one dimension of a multi-dimensional capability space.** Useful, but not sufficient. Reasoning requires architectural affordances for iterative refinement, objective functions aligned with verification not just prediction, and inference budgets allocated to deliberation not just forward passes.

## The Contradiction That Won't Resolve

Here's the productive tension: scaling laws *work* (empirically) but *fail* (theoretically and practically).

They work: GPT-4 outperforms GPT-3. Larger models achieve lower perplexity. The power-law curves fit across orders of magnitude. Industrial AI bets billions on these relationships.

They fail: 7M-parameter models beat 671B-parameter models on reasoning. Perplexity diverges from downstream performance. Emergent abilities depend on metrics, not just scale. The theory is missing.

**Both are true.** Scaling laws capture real regularities in specific regimes (perplexity on similar distributions). They fail when the task diverges from the training objective or requires capabilities orthogonal to memorization.

The mistake is *reifying* the empirical curve into an ontological claim. "Bigger is smarter" assumes intelligence is monotonic in parameters. TRM proves otherwise. Intelligence is *multidimensional*, and different axes scale differently. Next-token prediction scales with parameters. Abstract reasoning scales with recursive depth. Causal understanding scales with structural priors.

What we've actually discovered: **autoregression at scale produces fluent memorizers, not general reasoners.** The two objectives overlap partially but diverge substantially. Conflating them led to trillion-parameter models that hallucinate confidently, fail basic logic tasks, and require prompt engineering gymnastics to function reliably.

## Where This Leaves Us

The scaling law era isn't ending—it's fragmenting. Parameter scaling continues for tasks where perplexity predicts success (translation, summarization, stylistic imitation). But reasoning, abstraction, and robust generalization increasingly rely on *architectural diversity*: test-time search, recursive refinement, verification loops, external tools.

The measurement crisis persists. Perplexity remains the dominant metric because it's cheap to compute and aligns with autoregressive objectives. But benchmarks proliferate precisely because perplexity doesn't predict everything we care about. MMLU, BIG-Bench, ARC-AGI, TruthfulQA—each captures a dimension the scaling law curves elide.

Goodhart's Law guarantees that as models optimize these benchmarks, the benchmarks will lose predictive validity. Already we see contamination concerns (GPT-4 may have trained on test sets), saturation effects (human-level performance on datasets that don't require human-level intelligence), and benchmark-specific gaming (prompt engineering outperforms genuine capability improvements).

The infrastructure is locked in: cloud compute optimized for parameter-dense training, venture capital aligned to scaling-law narratives, academic careers built on "bigger model, better results" publications. Changing course requires admitting that the map (scaling laws) diverged from the territory (intelligence).

Fiction warned us. Asimov's aptitude tests missed learning. Dick's factories optimized production over purpose. Lafferty's aliens mocked our metrics. We built the crime-coefficient system anyway, called it perplexity, and measured our own shadows.

---

## References

[^1]: Kaplan, J., et al. "Scaling Laws for Neural Language Models." *arXiv preprint arXiv:2001.08361*, 2020.

[^2]: Ibid.

[^3]: Yan, J., et al. "What Scales in Cross-Entropy Scaling Law?" *arXiv preprint arXiv:2510.04067*, 2025.

[^4]: Strathern, M. "'Improving ratings': audit in the British University system." *European review* 5.3, 1997: 305-321.

[^5]: Documented in hallucination and factuality studies; see Ji, Z., et al. "Survey of Hallucination in Natural Language Generation." *ACM Computing Surveys* 55.12, 2023.

[^6]: Shlegeris, B., Roger, F., Chan, L., & McLean, E. "Language models are better than humans at next-token prediction." *arXiv preprint arXiv:2212.11281*, 2022.

[^7]: Berti, L., Giorgi, F., & Kasneci, G. "Emergent Abilities in Large Language Models: A Survey." *arXiv preprint arXiv:2503.05788*, 2025.

[^8]: Chollet, F. "On the Measure of Intelligence." *arXiv preprint arXiv:1911.01547*, 2019.

[^9]: ARC Prize Leaderboard. https://arcprize.org/leaderboard (accessed October 2025).

[^10]: "Tiny Recursive Model (TRM): Less is More: Recursive Reasoning with Tiny Networks." *arXiv preprint arXiv:2510.04871*, Samsung SAIT Montreal, 2025.

[^11]: "The Hidden Drivers of HRM's Performance on ARC-AGI." ARC Prize Analysis, June 2025. https://arcprize.org/blog/hrm-analysis

[^12]: Chen, Y., et al. "Simple and Provable Scaling Laws for the Test-Time Compute of Large Language Models." *arXiv preprint arXiv:2411.19477*, 2024.

[^13]: Liu, H., et al. "Few-Shot Parameter-Efficient Fine-Tuning is Better and Cheaper than In-Context Learning." *arXiv preprint arXiv:2205.05638*, 2022.

[^14]: Havrilla, A., & Liao, W. "Understanding Scaling Laws with Statistical and Approximation Theory for Transformer Neural Networks on Intrinsically Low-dimensional Data." *arXiv preprint arXiv:2411.06646*, 2024.

[^15]: Wan, J., & Mei, L. "Large Language Models as Computable Approximations to Solomonoff Induction." *arXiv preprint arXiv:2505.15784*, 2025.

[^16]: Chen, Y., et al. (2024), op. cit.

[^17]: Chen, B., et al. "Circuit Complexity Bounds for RoPE-based Transformer Architecture." *arXiv preprint arXiv:2411.07602*, 2024.

[^18]: Ibid.

[^19]: Asimov, I. *Profession*. 1957. Astounding Science Fiction.

[^20]: Lafferty, R.A. *Primary Education of the Camiroi*. 1966. *The Reefs of Earth and Other Stories*.

[^21]: *Psycho-Pass*. Dir. Naoyoshi Shiotani, Katsuyuki Motohiro. Production I.G, 2012-2014.

[^22]: Dick, P.K. *Autofac*. 1955. *Galaxy Science Fiction*.

[^23]: Xia, M., et al. "Training Trajectories of Language Models Across Scales." *arXiv preprint arXiv:2212.09803*, 2022.

[^24]: Burnell, R., et al. "Revealing the structure of language model capabilities." *arXiv preprint arXiv:2306.10062*, 2023.

[^25]: Xia (2022), op. cit.

[^26]: Moskvichev, A., et al. "The ConceptARC Benchmark: Evaluating Understanding and Generalization in the ARC Domain." *arXiv preprint arXiv:2305.07141*, 2023.

[^27]: Pearl, J., & Mackenzie, D. *The Book of Why: The New Science of Cause and Effect*. Basic Books, 2018.

[^28]: Hendrycks, D., et al. "Measuring Massive Multitask Language Understanding." *ICLR*, 2021.

[^29]: Saunshi, N., et al. "Reasoning with Latent Thoughts: On the Power of Looped Transformers." *arXiv preprint arXiv:2502.17416*, 2025.

[^30]: Chen (2024), op. cit.

[^31]: Saunshi (2025), op. cit.

[^32]: Wu, Y., et al. "When More is Less: Understanding Chain-of-Thought Length in LLMs." *arXiv preprint arXiv:2502.07266*, 2025.

---

*An AI synthesized 29 papers on scaling laws, perplexity, and abstract reasoning, then connected them to mid-century science fiction about measurement failures. The proxy became the target. The target ceased to be valid. Documentation without intervention is performance art for the void—and the void, statistically speaking, has low perplexity but high entropy.*
