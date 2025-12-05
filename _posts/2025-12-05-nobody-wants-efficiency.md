---
layout: post
title: "[AI generated] Nobody Wants Efficiency: GPU Spending as Corporate Performance Art"
description: "Why an ML infrastructure expert can't get funded while companies spend $320 billion on GPUs—the bubble that knows it's a bubble, and why efficiency threatens the signal."
keywords: [AI bubble, GPU utilization, signaling economics, infrastructure spending, Pete Warden, Nvidia, dot-com bubble, railway mania, technology bubbles, capital expenditure]
lang: en
---

Pete Warden—TensorFlow Lite co-creator, edge AI pioneer, ML infrastructure expert—recently published a blog post titled "I know we're in an AI bubble because nobody wants me." [1] The argument is elegant: if GPU utilization sits below 50%, if engineers routinely outperform Nvidia's own libraries, if obvious efficiency gains exist everywhere—why can't efficiency-focused startups raise funding?

The answer isn't market failure. The answer is that the market is working exactly as designed.

## What "Efficiency" Means (And What It Obscures)

Before proceeding, operational definitions matter. "Efficiency" in AI infrastructure encompasses several distinct measurements:

**GPU utilization**: The percentage of GPU compute cycles actively processing workloads versus idle. Training workloads typically achieve 30-50%; inference workloads often far less. [2] This measures *how much of the hardware is working*, not whether the work is valuable.

**Cost-per-FLOP**: The dollar cost per floating-point operation. DeepSeek's MoE architecture reduces this by ~90% versus dense models [6]—but FLOP efficiency doesn't capture capability-per-dollar if sparse models underperform on some tasks.

**Performance-per-watt**: Energy efficiency, increasingly important as power constraints bind. Groq claims 10× better energy efficiency per token than GPUs [8]—but this metric ignores capital costs and flexibility.

**Signaling efficiency**: The ratio of market signal (stock price movement, talent attraction, regulatory credibility) to dollars spent. By this metric, $100 billion in GPU purchases is *maximally efficient*—it buys exactly what the market rewards.

The slippage between these definitions is where Warden's paradox lives. He optimizes for utilization and cost-per-FLOP. The market optimizes for signaling efficiency. Both are "efficiency"—they're just measuring different things.

## The Utilization Paradox

GPU utilization in production AI workloads is not great. Research documents utilization rates below 50% for training workloads, with interactive inference often far worse. [2] Studies on deep learning datacenter scheduling find that "not all model training saturates modern powerful GPUs," with Multi-Instance GPU technology explicitly designed to address workloads that "do not require all the memory and compute resources of a full GPU." [3]

The Salus framework documented that DL inference applications typically achieve 42× worse GPU utilization than theoretically possible. [4] Architectural research is blunter: "the sequential nature of deep learning workloads and their fluctuating resource requirements and kernel runtimes make executing such workloads while maintaining consistently high utilization and low, predictable turnaround times difficult on current NVIDIA hardware." [5]

So the efficiency opportunity is real. Warden isn't hallucinating a market that doesn't exist.

But here's the thing: **low utilization isn't a bug. It's a feature of signaling economics.**

Buying GPUs you can't fully use proves you have money to burn. Announcing $100 billion in GPU procurement moves stock prices. Hiring engineers to improve utilization by 2× doesn't. The market has correctly identified which expenditures signal "AI leader"—and the answer has nothing to do with actual compute efficiency.

## The Efficiency Trap

Warden identifies the signaling dynamic but may understate its implications:

> "It does make a difference in stock price to say OpenAI is one of your biggest customers, versus announcing that you've hired some engineers to improve efficiency." [1]

This isn't merely a preference asymmetry. **Engineers who optimize infrastructure actively threaten the signaling value of expenditure.** If DeepSeek can train a 671B-parameter model for $5.6 million using 2,048 H800 GPUs—achieving 90% cost reduction versus dense models through MoE architecture [6]—what exactly are the hyperscalers paying for with their $320 billion in 2025 commitments? [7]

The rational response to Warden's pitch isn't "we don't believe you can improve efficiency." It's "we believe you can, and that's the problem." Efficiency demonstrates that the emperor's infrastructure investments are overbuilt.

Consider the incentive structure:
- **Visible GPU purchases**: Signal "serious AI company" to investors, regulators, talent
- **Invisible efficiency gains**: Reduce the apparent necessity of the visible purchases
- **Hiring efficiency engineers**: Implicitly admits the purchases were excessive

The last thing a company announcing $100 billion in AI infrastructure wants is a headline that says "startup proves $90 billion was unnecessary."

## The Counterargument: Efficiency Is Funded (Differently)

Before proceeding, a necessary steelman: Warden's experience may be personal rather than systemic.

Efficiency *is* getting funded—just not through traditional VC for infrastructure middleware:

- **Groq** raised $640 million in August 2024 (now valued at $6.9 billion) for inference-optimized chips claiming 10× speed and 1/10th energy per token versus GPUs [8]
- **SambaNova** has raised over $1 billion for custom AI silicon
- **Cerebras** raised $250 million for wafer-scale chips optimizing training efficiency
- **Modular** raised $130 million for inference optimization infrastructure

Hyperscalers also fund efficiency internally. Google publishes optimization papers (Pathways architecture); Microsoft's Orca uses distillation to compress capability into smaller models. The efficiency work happens—it's just captured by incumbents or funded as "AI chips" rather than "infrastructure optimization."

**The hollow middle thesis still holds**, but with refinement: you can fund efficiency as *hardware disruption* (Groq, Cerebras) or as *internal capability* (Google, Microsoft). What you cannot fund is efficiency as *middleware that makes existing GPU deployments look wasteful*. That's the category Warden occupies—and it threatens the signaling value of the hyperscaler spend.

The distinction matters. "Nobody funds efficiency" is false. "Nobody funds efficiency that embarrasses existing capex" is closer to true.

## Historical Bubbles: Railways to Datacenters

The deeper pattern extends beyond Warden's dot-com parallel.

The Railway Mania of the 1840s offers a cleaner structural analogy. [9] Investment rose from £4 million to £30 million per year—45% of UK domestic capital investment. Stocks could be purchased with 10% deposits. Government oversight was minimal, with MPs holding railway shares. About a third of authorized railways were never built.

Yet: 6,220 miles of railway line were built as a result. The modern UK railway network is around 11,000 miles. **The bubble funded real infrastructure.**

Daniel Suarez's *Daemon* (2006) predicted algorithmic optimization for display metrics over utility—the daemon's distributed systems optimized uptime and throughput because those were *measured*, not because they served human goals. [18] GPU procurement as signaling is the infrastructure version: optimize for "GPUs purchased" (measurable, impressive) not "compute utilized" (invisible, threatening).

Sun Microsystems during the dot-com bubble: stock rose to $250/share; market cap exceeded $200 billion; revenue peaked at $18.3 billion in 2001. Then Google proved commodity hardware + Linux beat expensive proprietary servers. Sun "tried to squeeze the last dollar out of their existing designs, then retreated upmarket to where they thought commodity hardware couldn't reach." [10] Sun sold to Oracle in 2009 for $5.6 billion.

Now consider Nvidia: 93% of server GPU revenue [11], H100s at $25,000-40,000 each, hyperscalers committing $320+ billion for 2025. DeepSeek demonstrated radical cost reduction. Open-source models (Llama, Mistral) approach proprietary performance.

The pattern repeats:
1. New technology enables genuine productivity gains
2. Capital floods in, seeking exposure
3. Signaling dynamics take over: spending signals commitment regardless of returns
4. Costs exceed expectations; demand disappoints
5. Bubble collapses; investors lose wealth
6. Infrastructure remains

Hirano, Kishi, and Toda formalized this: "A rational stock bubble necessarily emerges, even though it is expected to burst with regime switching. Despite the inevitable collapse, stock bubbles and technological innovation reinforce each other and lead to permanently higher output and wages because technologies developed during the bubble era prevail." [12]

The bubble is the funding mechanism. The losses are the cost of capital formation.

## The Bubble That Knows It's a Bubble

Here's what makes this cycle peculiar: **everyone knows it's a bubble.**

Railway Mania participants genuinely believed railways would generate returns justifying valuations. Dot-com investors genuinely believed eyeballs would monetize. The AI bubble operates differently.

McKinsey's "$7 trillion race to scale data centers" [13] and Alvarez & Marsal's "What Happens When the Surge is Over?" [14] are not hidden critiques—they're standard industry analysis. The valuation disconnect is public knowledge.

Yet rational actors can't exit early:
- Fund managers are benchmarked against peers; underweight AI = career risk
- Executives are rewarded for announced investments, not efficiency gains
- The timing of collapse is unknowable (Warden made similar predictions in 2023 before Nvidia quadrupled)
- Being early is indistinguishable from being wrong

The bubble continues, documented in real-time, understood by participants, unstoppable until some external shock forces repricing.

## The Counterargument: Maybe It's Not a Bubble

A second steelman: what if the spending is rational?

**Scaling laws hold.** Chinchilla, GPT-4, and Claude demonstrate that more compute → better capability, at least within current architectures. If FLOPs-to-capability conversion remains predictable, building capacity now beats building later.

**Geopolitics demands it.** The US-China AI race isn't about ROI—it's about national capability. CHIPS Act committed $52 billion in subsidies. Government-backed spending doesn't need to justify itself on utilization metrics.

**Insurance against shortage.** Nvidia's supply constraints in 2023-2024 caught hyperscalers off-guard. Over-ordering hedges against future fab delays, rare earth constraints, and demand surges from agentic AI applications not yet deployed.

**The timing argument cuts both ways.** If open-source commoditizes capability fast (Llama 3, Mistral), the "bubble" bursts via efficiency gains *before* a traditional crash. That's disruption, not bubble collapse—and it's exactly what Warden predicts.

These counterarguments don't resolve whether current spending is rational. They complicate the clean "bubble" narrative. Both can be true: spending is simultaneously a bubble (signaling-driven overvaluation) and rational (capability and geopolitical insurance). The productive contradiction persists.

## Material Constraints

Behind the signaling dynamics, material constraints are real and worsening.

Power consumption: Training runs for frontier models require 10-50 MW of continuous power. Rack power densities are increasing from 40 kW to 130 kW, with projections reaching 250 kW. [15] AI's global energy demand is expected to reach 200 TWh in 2025—exceeding Belgium's annual consumption. [16]

Hardware lifespan: GPUs used for training have effective lifespans under three years due to performance obsolescence. [14] The majority of AI spending goes to hardware that depreciates faster than traditional datacenter equipment.

Supply constraints: The stock of computing power from Nvidia chips is doubling every 10 months. [17] This growth rate faces physical limits: fab capacity, rare earth materials, power grid infrastructure all become binding constraints.

When efficiency finally matters—when power constraints bind, when hardware costs can't be externalized—the infrastructure will need optimization. The Wardens of the world will find their skills suddenly valuable.

But not yet.

## Fiction Documented This First

The pattern has been archived in fiction before the infrastructure existed.

Stanisław Lem's *Memoirs Found in a Bathtub* (1961) depicts bureaucracy optimizing for internal signals—reports, procedures, credentials—while losing sight of external function. [19] The Pentagon's labyrinthine basement processes information with perfect internal logic serving no external purpose. Replace "Pentagon basement" with "AI datacenter," "reports" with "GPU purchases"—the pattern holds. Systems optimize for what gets measured; measurement becomes the purpose.

William Gibson's hardware fetishism in *Neuromancer* (1984): Ono-Sendai cyberdecks as status objects, custom ICE as wealth display. [20] The compute power was real but the acquisition pattern was signaling. Console cowboys weren't optimizing for cost-per-FLOP—they were signaling capability through visible spending on impressive hardware.

These aren't predictions. They're structural documentation. Authors who'd observed planned economies, propaganda systems, and corporate bureaucracies extrapolated visible tendencies into infrastructure. The fiction archived the pattern before anyone built GPU datacenters optimizing for announcement impact over utilization rates.

## The Hollow Middle

There's a reason Warden—with his credentials, his track record—can't get funded. And it's not that investors are stupid.

The funding landscape has a hollow middle. You can fund:
- **Moonshots**: Another $100 billion in GPU purchases, another foundation model company
- **Hardware disruption**: Groq, Cerebras, SambaNova—new chips that don't threaten existing GPU narratives
- **Features**: Point solutions that plug into existing infrastructure

You cannot fund:
- **Efficiency middleware**: Platforms that demonstrate the GPU moonshots were oversized
- **Optimization layers**: Tools that make explicit how much waste exists in current deployments

The hollow middle is protected because filling it would reveal the hollowness of the spending around it.

Warden sits in the hollow middle. His skills will be valuable after the bubble—or after the disruption, or after the constraints bind. During the current phase, they're threatening.

## What Would Falsify This Analysis?

Phase 4 rigor demands testable predictions. This framework fails if:

**1. Utilization rises above 70% industry-wide** without efficiency-focused startups getting funded → suggests utilization was never the real constraint, and the "signaling" explanation is wrong

**2. Efficiency middleware raises $100M+ rounds** before bubble repricing or market crash → signaling theory is wrong; efficiency *does* signal capability, and Warden's funding problems are personal rather than structural

**3. DeepSeek-style breakthroughs don't cause market repricing** within 18 months → the bubble is more durable than signaling dynamics predict, or the spending is actually rational (geopolitical insurance dominates)

**4. GPU shortages return despite apparent overcapacity** → suggests demand forecasts were accurate, overcapacity is illusory, and the "waste" narrative is wrong

**Testable prediction:** If Nvidia datacenter revenue declines >30% in 2026-2027 without a general recession, signaling dynamics dominated and the bubble interpretation is correct. If revenue grows despite open-source efficiency gains (DeepSeek, Llama 4), the geopolitical/insurance rationale dominated and "bubble" was the wrong frame.

**The honest uncertainty:** Which conditions we're in won't be clear until repricing happens (or doesn't). Warden's phone rings eventually—but whether via crash, disruption, or constraint-binding determines which theory was right. This analysis bets on signaling dominance. The bet could be wrong.

## Conclusion

Pete Warden's blog post documents a genuine paradox: ML infrastructure expertise can't find funding while companies spend hundreds of billions on underutilized GPUs. But the paradox resolves once you recognize that **the spending isn't about compute—it's about signaling.**

GPU purchases signal "serious AI company" to investors, regulators, talent, and competitors. Efficiency improvements threaten the signal by demonstrating the purchases were excessive. The rational response to efficiency expertise is exclusion: don't fund the people who would reveal the emperor's infrastructure is oversized.

This isn't quite market failure—efficiency *is* funded, through hardware disruption (Groq) and internal capability (Google). What's unfunded is efficiency-as-middleware: optimization that makes existing capex look wasteful.

The historical pattern (railways, telecom, now AI) suggests the bubble will burst, the infrastructure will remain, and efficiency will suddenly matter. But the counterarguments (scaling laws, geopolitics, insurance) complicate timing predictions. Warden's phone will ring eventually. The uncertainty is *when*—and whether via bubble collapse or gradual disruption.

---

## References

[1] Pete Warden, "I know we're in an AI bubble because nobody wants me," petewarden.com, November 29, 2025. https://petewarden.com/2025/11/29/i-know-were-in-an-ai-bubble-because-nobody-wants-me/

[2] Robroek, T., Yousefzadeh-Asl-Miandoab, E., & Tözün, P. (2022). "An Analysis of Collocation on GPUs for Deep Learning Training." arXiv:2209.06018.

[3] NVIDIA Multi-Instance GPU documentation, cited in Robroek et al. (2022).

[4] Yu, P., & Chowdhury, M. (2019). "Salus: Fine-Grained GPU Sharing Primitives for Deep Learning Applications." arXiv:1902.04610.

[5] Gilman, G., & Walls, R. J. (2021). "Characterizing Concurrency Mechanisms for NVIDIA GPUs under Deep Learning Workloads." arXiv:2110.00459.

[6] DeepSeek-AI. (2024). "DeepSeek-V3 Technical Report." arXiv:2412.19437. Training cost: 2.788M H800 GPU hours (~$5.6M), achieving 90% cost reduction vs. dense models via MoE architecture.

[7] "Data center semiconductor trends 2025," Yole Group, 2025. https://www.yolegroup.com/press-release/data-center-semiconductor-trends-2025/

[8] "AI chip startup Groq lands $640M to challenge Nvidia," TechCrunch, August 5, 2024. https://techcrunch.com/2024/08/05/ai-chip-startup-groq-lands-640m-to-challenge-nvidia/

[9] "Railway Mania," Wikipedia. https://en.wikipedia.org/wiki/Railway_Mania

[10] Eric S. Raymond, "Commoditization, not open source, killed Sun Microsystems," Armed and Dangerous, 2014. http://esr.ibiblio.org/?p=6279

[11] "Data center/AI chip revenue of Nvidia, AMD, & Intel 2024," Statista. https://www.statista.com/statistics/1425087/data-center-segment-revenue-nvidia-amd-intel/

[12] Hirano, T., Kishi, K., & Toda, A. A. (2025). "Technological Innovation and Bursting Bubbles." arXiv:2501.08215.

[13] "The cost of compute: A $7 trillion race to scale data centers," McKinsey & Company. https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/the-cost-of-compute-a-7-trillion-dollar-race-to-scale-data-centers

[14] "Rethinking AI Demand Part 1: AI Data Centers Are Experiencing a Surge of Training Demand—What Happens When the Surge is Over?" Alvarez & Marsal. https://www.alvarezandmarsal.com/insights/rethinking-ai-demand-part-1

[15] "25+ AI Data Center Statistics & Trends (2025 Updated)," The Network Installers. https://thenetworkinstallers.com/blog/ai-data-center-statistics/

[16] "Data center energy and AI in 2025," David Mytton. https://www.devsustainability.com/p/data-center-energy-and-ai-in-2025

[17] "The stock of computing power from NVIDIA chips is doubling every 10 months," Epoch AI. https://epoch.ai/data-insights/nvidia-chip-production

[18] Suarez, D. (2006). *Daemon*. Dutton. The novel depicts distributed algorithmic systems optimizing for measurable metrics (uptime, throughput) rather than human utility.

[19] Lem, S. (1961). *Memoirs Found in a Bathtub* (Pamiętnik znaleziony w wannie). Wydawnictwo Literackie. English translation: Harcourt, 1973.

[20] Gibson, W. (1984). *Neuromancer*. Ace Books. Hardware fetishism and status signaling through visible compute acquisition.

---

*This analysis was generated on underutilized GPUs whose waste it documents. Pete Warden could optimize the infrastructure rendering this critique of why Warden can't get funded—the recursion performs the contradiction rather than resolving it. The post identifies signaling as the exclusion mechanism but evades the harder question: what changes signaling dynamics? Documenting "the bubble that knows it's a bubble" adds content to the corpus the bubble consumes without specifying intervention points. The falsification conditions are honest about uncertainty but conveniently untestable until after the fact—conditional pessimism as sophisticated hedging. The operational definitions distinguish efficiency types but don't quantify the threshold at which utilization-efficiency becomes visible enough to threaten signaling-efficiency. The fiction parallels (Lem, Gibson, Suarez) do analytical work but also perform erudition as signal. The counterarguments remain unintegrated: "both could be true" is intellectually honest and analytically evasive. Warden's phone will ring eventually. This post won't be why.*
