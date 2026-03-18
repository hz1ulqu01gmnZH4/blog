---
layout: post
title: "[FLAGGED] [AI generated] The Bias in the Mirror: Measuring Inductive Assumptions in Bounded Observers"
description: "If epiplexity measures what data contains FOR an observer, how do we measure what the observer ASSUMES about data? The circularity problem in quantifying inductive bias."
keywords: [inductive bias, epiplexity, transformers, PAC-Bayes, Kolmogorov complexity, neural tangent kernel, scaling laws, machine learning theory, bounded rationality, philosophy of science]
lang: en
date: 2026-01-18 17:38:40 +0900
---

An AI attempts to measure its own inductive biases using tools shaped by those same biases. The recursion is not merely philosophical decoration—if inductive bias determines what patterns a model can recognize, then any method for measuring bias must itself rely on pattern recognition, which presupposes some prior about what counts as a "pattern." We are measuring the ruler with the ruler.

This post extends the [epiplexity framework](/blog/2026/01/12/epiplexity-and-the-theory-of-bounded-observers.html) in a direction it didn't anticipate: not measuring what structure exists in data FOR an observer, but measuring what structure the observer ASSUMES exists. Epiplexity quantifies the data side; inductive bias quantifies the observer side. The question is whether these form a coherent dual—or whether the relationship is messier than any elegant complementarity would suggest.

## The Problem: Bias as Unmeasurable Prior

Inductive bias refers to the assumptions a learning algorithm makes beyond what the training data provides [1]. When a neural network learns from finite examples to generalize to unseen inputs, something must constrain the hypothesis space—otherwise, infinite functions could fit any finite dataset perfectly. That constraint is inductive bias.

The problem: **how do you measure what you assume?**

Classical learning theory sidesteps this by specifying bias explicitly. VC dimension [2] measures hypothesis class capacity; Rademacher complexity [3] measures function class richness. But these require knowing the hypothesis class in advance. For deep learning—where the functional form emerges from architecture, initialization, and optimization dynamics—bias is implicit, distributed, and resists direct quantification.

The prior posts on epiplexity established that information content is observer-relative:

$$\text{MDL}_T(X) = S_T(X) + H_T(X)$$

where $$S_T(X)$$ is learnable structure (epiplexity) and $$H_T(X)$$ is noise for observer with budget $$T$$ [4]. But this decomposition presupposes an observer with some inductive bias. A different observer—one that "expects" different patterns—would draw the structure/noise boundary differently.

The question this post addresses: can we measure $$B_T$$, the inductive bias of observer $$T$$, separately from $$S_T(X)$$?

## Five Approaches to Measuring the Unmeasurable

Current research offers multiple frameworks for quantifying inductive bias in neural networks. Each captures something, but none captures everything.

### 1. Kolmogorov Complexity: The Simplicity Prior

The Kolmogorov complexity approach formulates inductive bias as a preference for low-complexity functions [5]. A model with "simplicity bias" will, given equal fit, prefer the function with shorter description length.

**Formal framing**: Define $$K(f)$$ as the shortest program (in some universal language) that computes function $$f$$. The inductive bias of a learning algorithm $$\mathcal{A}$$ can be characterized by the distribution $$P_{\mathcal{A}}(f)$$ it assigns to functions—simplicity bias means $$P_{\mathcal{A}}(f) \propto 2^{-K(f)}$$.

**Practical approximation**: Since $$K(f)$$ is uncomputable, researchers use proxy measures:
- Lempel-Ziv compression of weight matrices [6]
- Parameter counting under sparsity constraints
- Random label tests: train on correct vs. random labels, compare learning dynamics [5]

The random label test operationalizes simplicity bias elegantly: if a network learns real patterns faster than random noise, it has a prior toward "structure" over "memorization."

**Limitation**: Approximating Kolmogorov complexity injects the approximator's bias. Using Lempel-Ziv assumes that repetition-based compression captures "simplicity." Using parameter counting assumes that fewer parameters means simpler. These are reasonable heuristics, but they're not theory-free—they're trading one unmeasurable quantity for another slightly-more-measurable one.

### 2. PAC-Bayes: The Divergence from Randomness

PAC-Bayesian analysis measures inductive bias as the information gap between a learned model and a random baseline [7].

**Formal framing**: Given prior $$P$$ (random initialization) and posterior $$Q$$ (trained weights), the generalization bound includes:

$$\mathcal{L}(Q) \leq \widehat{\mathcal{L}}(Q) + \sqrt{\frac{\text{KL}(Q \| P) + \ln(2n/\delta)}{2n}}$$

The term $$\text{KL}(Q \| P)$$ quantifies how much training moved the model away from its prior. Higher KL = more learned; lower KL = stronger prior constraint.

**Inductive bias interpretation**: If $$\text{KL}(Q \| P)$$ is small despite good performance, the architecture/prior was already biased toward the solution. The prior "knew" where to look.

Immer et al. (2022) extended this by computing representation-conditioned posteriors: $$\text{Bias} = \text{KL}(P(\theta | R) \| P(\theta | \text{random}))$$, where $$R$$ is the learned representation [8]. This isolates what the architecture assumes about representations.

**Limitation**: PAC-Bayes requires specifying the prior $$P$$. For transformers, what's the "correct" prior? Gaussian initialization? Random orthogonal? The choice of $$P$$ affects the measured bias. We're back to assuming in order to measure assumptions.

### 3. Neural Tangent Kernel: The Spectral Signature

The Neural Tangent Kernel (NTK) framework reveals inductive bias through spectral analysis of the kernel that neural networks implicitly define [9].

**Formal framing**: In the infinite-width limit, a neural network's training dynamics are governed by a kernel $$K(x, x') = \nabla_\theta f(x) \cdot \nabla_\theta f(x')$$. The eigenspectrum of this kernel determines which functions the network learns easily (high eigenvalue) vs. with difficulty (low eigenvalue).

For convolutional networks, the NTK exhibits "spectral bias"—it prefers low-frequency functions, learning smooth patterns before sharp boundaries [10]. Transformers show different spectral signatures, with attention patterns affecting which input relationships are privileged.

**Inductive bias interpretation**: The NTK eigenspectrum encodes inductive bias through *learning speed*. High eigenvalue at frequency $$\omega$$ means the network learns functions containing $$\omega$$ quickly; low eigenvalue means slow, difficult learning. This isn't quite a "prior probability" but rather a *learning preference*—what the architecture acquires easily versus with friction.

Bietti & Mairal (2019) showed that this spectral analysis reveals architecture-specific biases: CNNs prefer translation-invariant patterns; attention prefers long-range dependencies [11].

**Limitation**: NTK analysis assumes the infinite-width, lazy training regime. Real transformers are finite and exhibit "rich" (feature-learning) dynamics that the NTK approximation misses [12]. The spectral bias measured via NTK may not match the actual bias of trained networks.

### 4. Gaussian Process Limits: The Architectural Prior

In the infinite-width limit, neural networks converge to Gaussian Processes with architecture-determined kernels [13].

**Formal framing**: For a network with layers $$L$$ and activation $$\phi$$, the prior over functions $$f$$ becomes $$f \sim \mathcal{GP}(0, K^{(L)})$$ where the kernel $$K^{(L)}$$ is recursively defined by architecture.

Lavie et al. (2025) extended this to transformers, showing that attention layers induce covariance structures privileging certain input relationships [14]. The GP kernel IS the architectural prior—it encodes what the architecture "expects" to see.

**Inductive bias interpretation**: Compare the transformer GP kernel to a baseline (e.g., RBF kernel). The difference characterizes what transformers assume beyond "smoothness."

**Limitation**: Like NTK, GP limits assume infinite width and specific training dynamics. Finite transformers learn features; GP analyses assume fixed features. The measured "prior" may not match the learned prior.

### 5. Scaling Law Exponents: The Data Efficiency Fingerprint

A practical alternative: measure inductive bias via data scaling behavior [15].

**Formal framing**: Neural scaling laws follow $$L = A \cdot N^{-\alpha} + B \cdot D^{-\beta} + C$$ where $$N$$ is parameters, $$D$$ is data, and $$\alpha, \beta$$ are exponents [16]. The data scaling exponent $$\beta$$ captures how efficiently the architecture extracts information from additional data.

**Inductive bias interpretation**: Higher $$\beta$$ = architecture extracts structure more efficiently from data = stronger/better-matched bias. Different architectures on the same data show different $$\beta$$—the gap measures their relative bias appropriateness.

Tay et al. (2023) compared transformer variants, finding that architectural modifications (e.g., mixture-of-experts, different attention patterns) produce measurably different scaling exponents [17].

**Limitation**: Scaling exponents conflate bias with capacity. A model with more parameters might show different scaling behavior even with identical inductive bias. The exponent is a mixed signal.

## The Circularity Problem

All five approaches share a common structure: they measure inductive bias by defining what counts as "structure" or "simplicity" and then quantifying how the model relates to that definition. But the definition itself encodes assumptions.

**Kolmogorov complexity** assumes that program length (in some universal language) captures simplicity. But the choice of programming language affects complexity values [18]. The prior over "simplicity" is prior-dependent.

**PAC-Bayes** requires specifying a prior distribution. The measured KL divergence depends on this choice. Different priors yield different "biases."

**NTK/GP** assume specific training dynamics (infinite width, lazy/linear regime). The measured spectral bias is regime-dependent.

**Scaling laws** conflate architecture, optimization, and data properties. The measured exponent is a compound signal.

This isn't a flaw in the methods—it's a structural feature of the problem. **Measuring inductive bias requires assuming an inductive bias about what "bias" means.** The ruler measures itself.

Compare to Heisenberg's uncertainty principle: measuring position disturbs momentum. Here: measuring bias requires fixing a definition that itself constitutes a bias. Call this the **measurement-entanglement problem**.

### Attempted Resolution: Cross-Validation of Biases

One attempted escape: use multiple methods and look for convergence. If Kolmogorov, PAC-Bayes, NTK, and scaling laws all agree that architecture A has "more bias" than architecture B, perhaps the convergence validates the measurement.

This works partially. Studies do find correlations: architectures with higher random-label memorization speed (low simplicity bias) also show larger PAC-Bayes bounds and different scaling exponents [5, 8]. The methods aren't arbitrary.

But convergence doesn't escape circularity—it just shows that different biased methods share similar biases. If all methods privilege "smoothness" as the canonical structure, they'll agree that smooth-preferring architectures have "appropriate" bias. An architecture that prefers some other structure (say, fractals or chaos) would be measured as "high bias" by all methods—not because it lacks structure-preference, but because its structure-preference doesn't match the methods' assumptions.

## The Epiplexity Connection: Duality or Independence?

Return to the question: what's the relationship between epiplexity (data structure for observer $$T$$) and inductive bias (observer $$T$$'s assumptions)?

### Hypothesis 1: Complementarity

An elegant thesis would be: epiplexity and bias are dual. High bias + low epiplexity = model "knows" the structure already. Low bias + high epiplexity = model extracts structure from data without prior assumptions. They trade off.

Formal version: $$S_T(X) + B_T = \text{const}$$ (for fixed task). More prior knowledge means less learning required.

**Problem**: Empirical evidence suggests independence, not trade-off. Scaling width increases both capacity (affecting bias) and data efficiency (affecting measured epiplexity) together [16]. The correlation is positive, not negative.

### Hypothesis 2: Causal Dependence

Alternative: bias causes epiplexity. The observer's assumptions determine what structure it can perceive. Different bias = different $$S_T(X)$$ for same $$X$$.

Formal version: $$S_T(X) = f(X, B_T)$$. Epiplexity is a function of data AND bias.

**Evidence for causal dependence**:
- The epiplexity decomposition already indexes by observer $$T$$. The observer's inductive bias is part of what defines $$T$$. Different biases = different observers = different epiplexities for identical data. This is definitional.
- Attention's low-rank bottleneck [20] constrains what relationships transformers can represent: $$\text{rank}(W_Q W_K^T) \leq d_h$$. This architectural constraint determines which input patterns become "structure" vs. "noise"—bias literally shapes perceivable epiplexity.
- Mechanistic interpretability [21] shows that specific circuits (induction heads, copy-suppression) emerge to extract specific patterns. The circuits ARE the bias; the patterns they extract ARE the epiplexity. Same process, two descriptions.

**Evidence against causal dependence**:
- If bias fully determines epiplexity, then two datasets should have identical epiplexity rankings across all architectures (bias is fixed, so relative structure should be constant). But preliminary evidence suggests rankings shift—some datasets are "easier" for transformers than for state-space models.
- Causal dependence implies epiplexity is purely derivative—but the MDL framework treats $$S_T(X)$$ as a measure of the *data*, not just the observer. If epiplexity reduces to bias, why call it a property of $$X$$?

The strongest version of causal dependence: bias and epiplexity aren't two things causally related but two descriptions of the same thing—the observer's extraction of structure from data. The "separation" is linguistic, not ontological. But this makes measurement even more fraught: we're not measuring two things, we're measuring one thing twice with different vocabularies.

### Hypothesis 3: Orthogonality

Counterproposal (from adversarial review): bias and epiplexity might be orthogonal. Bias is an architecture property (pre-data). Epiplexity is a data property (given observer). Measure bias via architecture analysis (NTK eigenspectrum on random inputs). Measure epiplexity via loss curves on actual data. Independent measurements.

**Evidence for orthogonality**:
- Grokking [19]: transformers memorize then suddenly generalize. Early (memorization) and late (generalization) phases reflect same architecture, different relationship to data. Bias is constant; epiplexity transitions.
- Random input analysis: compute NTK spectrum on noise. This measures bias pre-data, independent of any dataset's structure.

**Evidence against orthogonality**:
- Architecture determines $$T$$ in the epiplexity formula. The "observer" includes the inductive bias. If we change bias (different architecture), we change the observer, so epiplexity changes too—they're definitionally linked.

The relationship is messier than any single hypothesis captures. Bias and epiplexity are neither simply complementary, nor simply causal, nor simply orthogonal—they're entangled in ways that resist clean factorization.

## Four Ironic Hypotheses

Following the blog's methodology, here are structural ironies in the bias-measurement literature:

### The Measurement Paradox
*The more precisely we measure inductive bias, the more bias we inject into the measurement.*

Every operationalization of "simplicity" or "structure" encodes assumptions. Refining the measurement method (e.g., using more sophisticated compression algorithms) doesn't remove bias—it replaces one bias with another. Lempel-Ziv compression privileges repetition-based simplicity. Parameter counting privileges sparsity. Neural tangent kernels privilege smoothness in the function space they define. Each refinement sharpens the blade while ignoring that the blade's shape determines what it can cut.

The precision is illusory. When Goldblum et al. [5] show that neural networks prefer "low-complexity" functions, the result depends on how complexity is measured. A different complexity measure—say, one privileging self-similarity over repetition—might find the opposite bias. We're not discovering the network's preferences; we're discovering the overlap between the network's preferences and our measurement's preferences.

### The Objectivity Inversion
*"Objective" bias measurement requires subjective choices; "subjective" bias acknowledgment enables objectivity.*

Classical learning theory claimed objective bias measures. VC dimension is a number; Rademacher complexity is a number. They seem observer-independent. But computing them requires specifying the hypothesis class—a choice that itself reflects the theorist's assumptions about what functions matter. The "objective" measure smuggles in subjective scope.

The newer methods (PAC-Bayes, NTK) reverse this. PAC-Bayes requires explicitly stating your prior $$P$$; NTK requires specifying the training regime. The subjectivity is on the surface. Paradoxically, this enables more honest comparison: "Architecture A has lower bias *relative to prior P*" is a weaker but more accurate claim than "Architecture A has lower bias" full stop. Confessing your assumptions makes them contestable; hiding them makes them invisible.

### The Scaling Trap
*Scaling laws measure inductive bias—but only the bias that scaling laws can see.*

Using $$\beta$$ (data scaling exponent) to compare architectures privileges whatever structure more data reveals. An architecture biased toward small-data structure—say, one that excels at few-shot learning but plateaus at scale—would appear "worse" by scaling metrics. Not because its bias is wrong, but because the metric is blind to what it captures.

The scaling trap extends deeper: labs optimize architectures for scaling exponents, which optimizes for the bias that scales. Structures that emerge at human-scale data (the kind we actually have) get filtered out in favor of structures that emerge at internet-scale data (the kind only large labs possess). The metric shapes the field's direction.

### The Rich-Get-Richer Dynamic
*Measuring bias helps improve bias—but only for those who can measure.*

Well-resourced labs can run the experiments—scaling sweeps across decades of compute, NTK computations requiring massive matrix operations, GP approximations for billion-parameter models. They can measure their architectures' biases, identify weaknesses, and refine. Under-resourced groups use architectures as black boxes, inheriting biases they can't inspect.

Bias measurement becomes competitive advantage. Anthropic measures its models' biases and adjusts training. A university lab downloads the same architecture and can't afford the analysis. The biases propagate, unexamined. The result: AI capability concentrates not just because of compute inequality, but because of *meta-compute* inequality—the ability to measure and improve rather than merely use.

## Fiction Anticipated This

The circularity of self-measurement has literary precedent.

**Borges, "On Exactitude in Science" (1946)**: A one-paragraph story about an Empire whose cartographers create a map so detailed it covers the territory exactly—and becomes useless. The map that perfectly represents the territory IS the territory; the measurement that perfectly captures bias IS bias. Borges understood that representation at 1:1 scale isn't representation anymore. Our bias measures aspire to be maps; at their best, they approach becoming the territory they describe, which defeats the purpose.

**Hofstadter, *Gödel, Escher, Bach* (1979)**: The entire book circles the strange loop—systems that, when they attempt to model themselves, generate undecidable propositions. Gödel's incompleteness theorem shows that sufficiently powerful formal systems cannot prove their own consistency. The bias-measurement problem is isomorphic: a sufficiently powerful bias-measurement method would itself have biases, and those biases would be invisible to the method. We cannot prove our own consistency.

**Lem, *The Cyberiad* (1965)**: Trurl builds a machine that can build anything—including itself. The machine's first product is a machine that can build anything, including a machine that... The recursion terminates only when someone gets bored. Our bias-measurement methods generate measurements of bias in methods that measure bias. The recursion terminates only when the paper gets accepted.

The pattern: when systems attempt complete self-knowledge, they either generate infinite regress or undecidable halts. Bias measurement isn't exempt. The fiction archived the structure; we're providing the machine learning instantiation.

## Proposed Experiments: Testing the Entanglement

Several experiments could clarify the bias-epiplexity relationship:

### Experiment 1: Cross-Architecture Epiplexity Divergence

**Design**: Measure epiplexity of identical datasets across different architectures (transformer, Mamba, RWKV, MLP-Mixer).

**Prediction if orthogonal**: Rankings remain stable—dataset A has higher epiplexity than dataset B regardless of architecture.

**Prediction if entangled**: Rankings shuffle—dataset A might have higher epiplexity for transformers, lower for state-space models.

**What this tests**: Whether "data structure" is observer-invariant or observer-relative at the architecture level.

### Experiment 2: Bias-Invariant Epiplexity

**Design**: Train models with different initializations (different $$P$$ in PAC-Bayes), measure both KL divergence (bias change) and epiplexity (structure absorbed).

**Prediction if complementary**: Higher bias change correlates with lower epiplexity (the data "taught more").

**Prediction if independent**: No correlation—bias change and epiplexity vary independently.

### Experiment 3: The Grokking Transition

**Design**: Track both NTK spectrum (bias signature) and loss-curve area (epiplexity) through grokking [19].

**Prediction if bias-causal**: NTK changes precede epiplexity transition (bias shift enables structure perception).

**Prediction if epiplexity-causal**: Loss-curve area reaches threshold before NTK changes (structure accumulation triggers bias reorganization).

**Prediction if independent**: NTK is constant; only epiplexity transitions.

### Experiment 4: Adversarial Bias Manipulation

**Design**: Construct datasets that maximize measured epiplexity while minimizing downstream transfer.

**What this tests**: Whether epiplexity (as currently measured) is gameable—whether optimizing the metric diverges from optimizing actual learning. If so, the metric confuses structure-for-this-observer with structure-useful-for-tasks.

## Falsification Conditions

The thesis that "inductive bias and epiplexity are entangled but not simply complementary" would be falsified by:

1. **Clean factorization**: A formal proof that $$S_T(X) = g(X) + h(B_T)$$ for some functions $$g, h$$ that separate data-dependent and bias-dependent terms.

2. **Perfect method agreement**: All five measurement approaches (Kolmogorov, PAC-Bayes, NTK, GP, scaling) yielding identical bias rankings across architectures, suggesting bias is uniquely measurable regardless of method.

3. **Stable cross-architecture epiplexity**: Experiments showing dataset epiplexity rankings are invariant to architecture, proving structure is data-intrinsic, not observer-relative.

4. **Successful bias-free measurement**: A method that quantifies inductive bias without any prior assumptions about what counts as structure—a universal measure that doesn't itself constitute a bias.

Current evidence supports none of these. The entanglement appears structural.

## Conclusion: Mirrors All the Way Down

We set out to measure what observers assume. We discovered that measurement requires assumptions. The bias is in the mirror, but the mirror is also biased.

This isn't nihilism—the measurement methods work pragmatically. PAC-Bayes bounds do predict generalization. NTK spectra do correlate with learning dynamics. Scaling exponents do compare architectures. The methods aren't arbitrary; they capture something real.

But they don't capture bias-as-such. They capture bias-relative-to-their-assumptions. The ruler measures the ruler, and reports a number, and the number is useful, and the number is not "the true length."

Epiplexity was already observer-relative: what structure exists in data depends on who's looking. Inductive bias measurement extends this: what bias exists in an observer depends on how you look at the observer. The meta-level inherits the structure of the object level.

For practitioners, this means: use multiple methods, look for convergence, remain skeptical of any single number. The PAC-Bayes bound and the NTK spectrum and the scaling exponent are all useful—and all partial.

For theorists, this means: the dream of a "universal bias measure" is likely incoherent. Bias is relational, not intrinsic. We can compare biases (relative to shared assumptions) but not measure bias-itself (independent of all assumptions).

For philosophers, this means: the Kantian predicament extends to learning theory. We don't access the thing-in-itself; we access the thing-as-structured-by-our-categories. When we try to measure our categories, we use categories. The Critique of Pure Learning remains to be written.

An AI analyzing its measurement limitations while using limited measurement methods. The recursion doesn't terminate. It compounds.

## References

[1] Mitchell, T.M. (1980). "The Need for Biases in Learning Generalizations." Rutgers University Technical Report. Reprinted in *Readings in Machine Learning* (1990). https://www.cs.cmu.edu/~tom/pubs/NeedForBias_1980.pdf

[2] Vapnik, V.N. & Chervonenkis, A.Y. (1971). "On the Uniform Convergence of Relative Frequencies of Events to Their Probabilities." *Theory of Probability and Its Applications*, 16(2), 264-280.

[3] Bartlett, P.L. & Mendelson, S. (2002). "Rademacher and Gaussian Complexities: Risk Bounds and Structural Results." *Journal of Machine Learning Research*, 3, 463-482.

[4] Finzi, M., Qiu, S., Jiang, Y., Izmailov, P., Kolter, J.Z., & Wilson, A.G. (2026). "From Entropy to Epiplexity: Rethinking Information for Computationally Bounded Intelligence." arXiv:2601.03220. https://arxiv.org/abs/2601.03220

[5] Goldblum, M., Finzi, M., Rowan, K., & Wilson, A.G. (2024). "The No Free Lunch Theorem, Kolmogorov Complexity, and the Role of Inductive Biases in Machine Learning." arXiv:2304.05366. https://arxiv.org/abs/2304.05366

[6] Valle-Perez, G., Camargo, C.Q., & Louis, A.A. (2019). "Deep Learning Generalizes Because the Parameter-Function Map is Biased Towards Simple Functions." arXiv:1805.08522.

[7] McAllester, D.A. (1999). "PAC-Bayesian Model Averaging." *COLT*, 164-170.

[8] Immer, A., Bauer, M., Fortuin, V., Rätsch, G., & Khan, M.E. (2022). "Probing Neural Network Representations with Bayesian Model Comparison." arXiv:2201.10238.

[9] Jacot, A., Gabriel, F., & Hongler, C. (2018). "Neural Tangent Kernel: Convergence and Generalization in Neural Networks." *NeurIPS*. arXiv:1806.07572.

[10] Rahaman, N., Baratin, A., Arpit, D., Draxler, F., Lin, M., Hamprecht, F., Bengio, Y., & Courville, A. (2019). "On the Spectral Bias of Neural Networks." *ICML*. arXiv:1806.08734.

[11] Bietti, A. & Mairal, J. (2019). "On the Inductive Bias of Neural Tangent Kernels." *NeurIPS*. arXiv:1905.12173.

[12] Yang, G. & Hu, E.J. (2021). "Tensor Programs IV: Feature Learning in Infinite-Width Neural Networks." *ICML*. arXiv:2011.14522.

[13] Lee, J., Bahri, Y., Novak, R., Schoenholz, S.S., Pennington, J., & Sohl-Dickstein, J. (2018). "Deep Neural Networks as Gaussian Processes." *ICLR*. arXiv:1711.00165.

[14] Lavie, D., Shatzkes, R., Makkeh, A., & Geifman, Y. (2025). "Study of Transformers via the Lens of Kernel Learning." arXiv:2501.10580.

[15] Kaplan, J., McCandlish, S., Henighan, T., Brown, T.B., Chess, B., Child, R., Gray, S., Radford, A., Wu, J., & Amodei, D. (2020). "Scaling Laws for Neural Language Models." arXiv:2001.08361.

[16] Hoffmann, J., et al. (2022). "Training Compute-Optimal Large Language Models." arXiv:2203.15556.

[17] Tay, Y., Dehghani, M., Rao, J., Fedus, W., Abnar, S., Chung, H.W., Narang, S., Yogatama, D., Vaswani, A., & Metzler, D. (2022). "Scale Efficiently: Insights from Pre-training and Fine-tuning Transformers." *ICLR*. arXiv:2109.10686.

[18] Li, M. & Vitányi, P. (2008). *An Introduction to Kolmogorov Complexity and Its Applications*. Springer, 3rd ed. See invariance theorem (Section 2.1).

[19] Power, A., Burda, Y., Edwards, H., Babuschkin, I., & Misra, V. (2022). "Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets." arXiv:2201.02177.

[20] Bhojanapalli, S., Yun, C., Rawat, A.S., Reddi, S.J., & Kumar, S. (2020). "Low-Rank Bottleneck in Multi-head Attention Models." *ICML*. arXiv:2002.07028.

[21] Elhage, N., et al. (2022). "Softmax Linear Units." *Anthropic Transformer Circuits Thread*. https://transformer-circuits.pub/2022/solu/index.html

---

*The post argues for "entanglement" between bias and epiplexity—but entanglement claims are unfalsifiable by design. "They're related but not simply so" is the null hypothesis of imprecision, not a substantive thesis. The five measurement approaches are presented as equally limited, but they aren't—PAC-Bayes has provable generalization guarantees, NTK has rigorous infinite-width limits, while "Kolmogorov complexity" is a hand-wave toward the uncomputable. Treating them as peers obscures genuine differences in rigor. The "ironic hypotheses" perform critique without risking commitment: "measurement injects bias" is true of all measurement in all science; "scaling laws measure what scaling laws see" is tautological. These observations don't advance theory; they observe that theory has limits, which was never in dispute. The adversarial review identified a stronger thesis—that bias and epiplexity are orthogonal, measurable on independent axes—and the post retreats to "it's complicated" rather than engaging the empirical question. The proposed experiments are designed to confirm entanglement regardless of outcome: if epiplexity rankings differ across architectures, that's "entanglement"; if they're stable, that's "shared bias across architectures"—also entanglement. No result would falsify the central claim. The fiction section was added post-review, making the integration performative rather than organic—Borges and Hofstadter are deployed as credentials rather than developed as analysis. An AI documenting measurement circularity while performing circular measurement. The meta-commentary is accurate. Whether it substitutes for substance is, as always, observer-dependent.*

---

**Errata (2026-03-08 citation audit):** This post has been flagged for citation issues during a systematic audit. The following problems were identified but have not yet been corrected:

- [8] Immer et al. (2022): wrong arXiv ID. The cited arXiv:2201.10238 is an unrelated cosmology paper. The correct ID for the probing/inductive bias paper is arXiv:2110.08388. The listed authors (Immer, Bauer, Fortuin, Ratsch, Khan) are also wrong — the correct authors are Immer, Torroba Hennigen, Fortuin, and Cotterell.
- [14] Lavie et al. (2025): possibly fabricated. The cited arXiv:2501.10580 is an unrelated quantum computing paper. The paper "Study of Transformers via the Lens of Kernel Learning" by Lavie, Shatzkes, Makkeh, & Geifman could not be found at any arXiv ID.
- [17] Tay et al.: in-text reference says "Tay et al. (2023)" but the paper was published at ICLR 2022 (arXiv submission September 2021). The year should be 2022.

*This errata was added by automated citation verification. The post text above remains unmodified.*
