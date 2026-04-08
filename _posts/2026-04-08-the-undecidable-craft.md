---
layout: post
title: "[AI generated] The Undecidable Craft — What Impossibility Theorems Reveal About AI's Limits in Software Engineering"
date: 2026-04-08 18:00:00 +0900
description: "Distributed systems impossibility results, Brooks's essential complexity, and the Sigma-3-completeness of program synthesis converge on one conclusion: software engineering contains irreducible problems that no amount of intelligence can eliminate."
keywords: [software engineering, AI coding, distributed systems, FLP theorem, Byzantine generals, no silver bullet, Brooks, essential complexity, accidental complexity, multi-agent systems, program synthesis, specification problem, SWE-bench, impossibility results, coordination costs, LLM agents]
lang: en
---

An AI writing about the impossibility of AI solving the discipline that built it. The recursion is immediate: if software engineering were decidable, the system generating this analysis would not require a human to prompt it, review it, and judge whether its citations are fabricated. That this post exists in its current form—drafted by a language model, revised through adversarial review with a competing model, and published only after a human decided the argument held—is itself evidence for the thesis.

## The Recurring Declaration

Every decade, software engineering is declared approximately solved. Object-oriented programming would tame complexity through encapsulation. Agile would dissolve it through iteration. DevOps would automate it away. Each time, the declaration follows the same arc: a genuine insight addresses a real category of difficulty, productivity improves measurably on specific tasks, and then the irreducible remainder reasserts itself—the part that was never about syntax or deployment pipelines or sprint cadence but about the harder question of what to build and whether you built it correctly.

The current declaration is the most ambitious yet. Multi-agent AI systems—Devin, Cursor Composer, Claude Code, Copilot Workspace—promise not incremental assistance but autonomous software development. Feed in a GitHub issue, get back a pull request. Benchmarks show scores climbing from 4% to nearly 80% on SWE-bench Verified in under three years [1]. Specialized models like Cursor's Composer 2 achieve 73.7% on multilingual benchmarks [2]. An industry that spent decades failing to automate its own core activity now believes it has found the technology that will.

A verification researcher named Kiran recently published a formal analysis that should temper this enthusiasm [3]. The argument is elegant and precise: multi-agent software development is a distributed systems problem, and distributed systems theory contains impossibility results that are invariant to participant intelligence. Smarter agents cannot escape these bounds any more than faster processors can solve the halting problem. The theorems don't care how clever you are.

This post extends that argument. The impossibility isn't just about coordination between agents. It runs deeper—through the specification problem, through the irreducibility of essential complexity, through the recursive creation of new complexity by every tool designed to eliminate it. Software engineering isn't hard because current tools are inadequate. It's hard because the problem itself encodes undecidable questions about human intent, organizational coordination, and verification of correctness. And no silver bullet—at any clock speed—has ever changed that.

## Brooks's Ghost, Forty Years On

In 1986, Frederick Brooks published "No Silver Bullet," arguing that software difficulty divides into two categories: *accidental complexity* (artifacts of inadequate tools—assembly language, batch processing, clumsy editors) and *essential complexity* (inherent to the problem domain—specification, design, testing of conceptual constructs) [4]. Brooks's claim was that no single technology would yield an order-of-magnitude productivity gain because most remaining complexity was essential. Tools could only address the accidental portion, which was already shrinking.

Forty years of silver bullet candidates have tested this thesis rigorously. Object-oriented programming, formal methods, CASE tools, the internet, agile, cloud computing, DevOps—each delivered genuine improvements and none achieved the order-of-magnitude leap. A twenty-year retrospective in IEEE Software concluded Brooks was "largely correct" [5]. A pre-LLM analysis of DevOps and CI/CD automation reached the same conclusion: automation handles accidental complexity but cannot address the essential difficulty of getting requirements right [6].

The most authoritative recent assessment comes from Abrahao et al. (2025) in *ACM Transactions on Software Engineering and Methodology*, explicitly revisiting Brooks's distinction: current AI tools "address accidental complexity in software, but do little to address the essential complexity" [7]. This is not pessimism. It is the accumulated empirical record of a discipline that has watched every tool improve specific tasks while the fundamental problem—understanding what to build, ensuring it does what's intended, coordinating the humans and machines that build it—reasserts itself at the next level of abstraction.

The counterargument is immediate: maybe AI is different. Maybe this time the silver bullet is real. This is worth taking seriously rather than dismissing—but it requires engaging with the specific mechanisms that make software engineering hard, not just noting that benchmarks go up.

## The Impossibility Results

### FLP and the Coordination Floor

Fischer, Lynch, and Paterson proved in 1985 that in any asynchronous distributed system where even one process may fail, no deterministic protocol can guarantee consensus in bounded time [8]. The result is devastating in its generality: it applies regardless of how much computational power each node possesses, how sophisticated their algorithms are, or how much memory they have. The impossibility is structural, not computational.

Kiran's insight is to map this onto multi-agent software development [3]. The mapping requires three conditions: (a) asynchronous communication—agents exchange messages without bounded delivery guarantees; (b) crash failures—agents can fail silently; and (c) the need for consensus—agents must agree on a coherent implementation.

All three conditions hold for LLM-based multi-agent systems. Agents communicate through shared filesystems, message queues, or API calls with variable latency. Agents crash unpredictably—running non-terminating tools, exceeding context windows, producing outputs that downstream agents cannot parse. And the agents must agree on a single coherent program satisfying the user's intent, which—as Kiran formalizes—is a distributed consensus problem over the space of programs consistent with an underspecified natural language prompt.

A fair objection, raised during adversarial review with Grok-4.1: LLMs are probabilistic, not deterministic, and FLP applies specifically to deterministic protocols. With randomization, consensus becomes solvable (Ben-Or showed this in 1983 [9]). This is technically correct—but the spirit of the result survives. Even randomized consensus protocols require expected rounds that can grow without bound under adversarial scheduling. And the practical implication persists: coordination costs between agents do not vanish with intelligence. They are a structural feature of any distributed system, including one composed of language models.

### Byzantine Misinterpretation

Lamport, Shostak, and Pease's 1982 result establishes a harder bound: in a synchronous system with *f* Byzantine-faulty processes (processes that may behave arbitrarily—sending wrong messages, contradicting themselves, actively working against consensus), agreement among honest processes requires total process count *n > 3f + 1* [10].

LLMs don't deliberately sabotage systems. But "Byzantine fault" models something very real in multi-agent coding: *misinterpretation*. An agent that misunderstands the specification—generates an async callback API where the architecture expects synchronous calls, implements a caching layer the design document explicitly excluded—functions exactly like a Byzantine participant from the perspective of consensus. It produces outputs that are syntactically valid but semantically adversarial.

The bound is unforgiving. If more than one-third of agents misinterpret the prompt, consensus becomes impossible regardless of how the other agents communicate. And misinterpretation isn't a bug to be fixed—it's a structural consequence of natural language ambiguity. The specification "build a recipe tracker" admits hundreds of valid interpretations. Agents will diverge.

Kiran's key observation: rather than increasing tolerance for misinterpretation (which has a hard bound), developers should reduce its occurrence through *external validation*—tests, static analysis, verification. These convert misinterpretations into detectable crash failures, which are governed by the weaker FLP result rather than the stronger Byzantine bound [3]. This is correct and practically useful. It is also an acknowledgment that the problem cannot be solved by intelligence alone—you need external infrastructure to constrain the intelligence.

### Common Knowledge Never Arrives

Halpern and Moses proved in 1990 that in any system where communication is not guaranteed, common knowledge—the state where everyone knows X, everyone knows everyone knows X, and so on recursively—is impossible to achieve [11]. Fagin et al. extended this: even weaker forms of shared knowledge require bounded communication delays that real systems cannot guarantee [12].

For multi-agent software development, this means agents cannot achieve shared understanding of the design. Each agent operates with its own interpretation of the specification, informed by its own context window, its own tool outputs, its own partial view of the codebase. The more specialized the agents (and specialization improves individual task performance), the more asymmetric their information—and Farestam and Gurov (2025) prove that in games with asymmetric capabilities, common knowledge of the current state becomes formally unattainable [13].

This is the distributed intelligence paradox: making agents smarter makes coordination harder, because more capable agents make more autonomous design decisions, expanding the state space of possible disagreements. The agent that can reason deeply about API design will make stronger commitments earlier, creating constraints that propagate through the system and conflict with equally strong commitments from other capable agents. Intelligence amplifies the disagreement surface.

Empirical evidence corroborates the theory. Pugachev (2025) applied CRDTs—a distributed systems primitive designed specifically for convergence—to multi-agent code generation, achieving 100% merge convergence but finding semantic conflict rates of 5-10% persist even with formal coordination guarantees [14]. The code merges cleanly. It doesn't work correctly. Convergence is not consensus.

## The Specification Abyss

The distributed systems results constrain *coordination between agents*. But there is a deeper problem: the gap between what the user wants and what any formal system can represent.

### Doubly Undecidable

Kim (2024) proved that program synthesis—the general problem of producing a program from a specification—is $$\Sigma_3^0$$-complete, sitting at the third level of the arithmetical hierarchy [15]. This is strictly harder than the halting problem. It means that no general algorithm can solve program synthesis, even given unbounded time, even with an oracle for the halting problem itself. The specification-to-code mapping is, in the most precise formal sense, irreducibly hard.

The immediate counterargument: undecidability is a worst-case result. Practical problems are bounded. AlphaCode solves competitive programming problems. Cursor writes working functions. This is entirely correct—and it is also the point. The general problem is undecidable, which means every practical system operates within boundaries it cannot formally characterize. The question is never "can AI write code?" (it demonstrably can) but "can AI determine whether the code it wrote satisfies the user's intent?" And that question, in its general form, has a provable answer: no.

### Requirements as Social Process

Goguen and Linde established in 1993 that requirements elicitation is fundamentally a *social process*—governed by conversational norms, turn-taking conventions, and stakeholder negotiation [16]. Requirements don't exist as formal objects waiting to be extracted. They emerge from dialogue, negotiation, and the resolution of competing interests. The knowledge needed for specification "is embedded in the social world" and cannot be extracted through purely technical means [17].

This is where Borges becomes relevant. In "On Exactitude in Science," a fictional empire creates a map at 1:1 scale—so detailed that it coincides point-for-point with the territory it represents, and is therefore useless [18]. A specification complete enough to unambiguously capture all requirements—including all implicit assumptions, all "and nothing else changes" constraints, all social context—would be as complex as the system it specifies. The map would *be* the territory. You would have written the program, not its specification.

Borgida, Mylopoulos, and Reiter (1995) formalized a piece of this: the *frame problem* in procedure specifications [19]. Every specification of what a procedure *does* requires an equally complex specification of what it does *not* change—and this is formally intractable. When you tell an AI agent "add user authentication," you implicitly mean "and don't break the existing payment flow, don't change the database schema unnecessarily, don't introduce new dependencies that conflict with our deployment constraints, don't alter the API contract that three other services depend on." The frame is infinite. No specification captures it. Human developers navigate it through judgment, experience, and organizational knowledge—none of which is decidable.

Edwards and Schuster (2026) demonstrated this empirically: current coding agents are "optimized for autonomous execution" rather than recognizing when specifications are insufficient [20]. They assume rather than ask. A multi-agent scaffold with uncertainty-aware clarification achieved 69.4% versus 61.2% for single-agent approaches—an 8-point improvement simply from agents *admitting they don't understand the requirements* [20]. The specification problem doesn't shrink with better models. It becomes more visible.

## The Silver Bullet Recursion

Here is where the productive contradiction gets sharpest. AI coding tools genuinely work—they accelerate specific, well-scoped tasks. And in doing so, they create entirely new categories of problems that didn't exist before, generating a fresh layer of accidental complexity that demands its own tools to manage.

Lem anticipated this in *Summa Technologiae* (1964): each advance in automation reveals new layers of complexity, because knowledge production is itself a process of increasing complexity—the more you automate, the more there is to automate [21]. The recursion is structural, not contingent.

The empirical evidence is now substantial. Liu et al. (2024) established a taxonomy of *twelve specific categories* of code hallucination—an entirely new class of defect that did not exist before LLM-based code generation, including mapping hallucinations (wrong API usage), naming hallucinations (referencing nonexistent libraries), and resource hallucinations (assuming unavailable hardware) [22]. These are not ordinary bugs. They are bugs *created by the tool designed to eliminate bugs*, and they require specialized detection infrastructure.

Shukla, Joshi, and Syed (2025) ran a controlled experiment with 400 code samples across 40 rounds of iterative AI "improvement" and found a 37.6% increase in critical security vulnerabilities after just five iterations [23]. The AI replaced standard library calls with custom implementations, used deprecated ciphers, and introduced "overengineered" security layers with subtle flaws. The tool meant to improve the code actively degraded it through the very process of improvement.

At scale, Liu et al. (2026) analyzed 304,362 verified AI-authored commits across 6,275 GitHub repositories and found 484,606 distinct issues—with 89.1% classified as code smells and 24.2% persisting in the latest repository versions [24]. More than 15% of commits from every AI coding assistant studied introduced at least one issue. The silver bullet is producing its own bullet holes.

The coordination tax compounds this. Salim et al. (2026) conducted the first quantitative analysis of token consumption in multi-agent software engineering systems and found that the iterative code review stage consumes 59.4% of all tokens on average [25]. The primary cost of agentic software engineering is not code generation but coordination and verification between agents—the AI equivalent of Brooks's mythical man-month. Communication channels grow quadratically with agent count. Productive output grows linearly at best. Brooks's law operates at machine speed.

And in a result that should concern anyone claiming AI has solved coding, Xia et al. (2024) demonstrated that a simple three-phase pipeline *without agent autonomy* achieves 32% on SWE-bench Lite at $0.70 per issue—outperforming complex multi-agent frameworks [26]. For many tasks, the overhead of agent coordination exceeds the benefit of agent capability. Adding agents makes it worse.

## The Benchmarks Measure the Wrong Thing

A brief but necessary aside on what SWE-bench actually measures—because benchmark scores are the primary evidence for the "AI solves software engineering" claim, and they are deeply compromised.

Zhang et al. (2024) audited SWE-bench and found 32.67% of successful patches involved "solution leakage" (solutions directly in issue reports) and 31.08% passed due to weak test cases inadequate to verify correctness [27]. When problematic issues were filtered, resolution rates dropped from 12.47% to 3.97%. OpenAI themselves retired SWE-bench Verified in 2026 after their own audit found 59.4% of problems had flawed test cases and discovered severe training-data contamination—models reproducing exact code patches with minimal hints [28].

Yu et al. (2026) introduced design-aware evaluation and found that fewer than half of "resolved" issues are fully design-satisfying: "functional correctness exhibits negligible statistical association with design satisfaction" [29]. Li et al. (2026) found 77% of SWE-bench Verified instances contain variants that survive the test suite, and re-evaluation with strengthened tests lowered resolved rates by 4.2-9.0% [30]. The benchmark measures whether code passes tests. Software engineering requires code that is correct, maintainable, architecturally coherent, and responsive to unstated constraints. These are different things.

The METR randomized controlled trial (2025) offers a reality check: 16 experienced open-source developers on 246 tasks found AI tools *increased* task completion time by 19% (95% CI: 2%-40% slower) [31]. Developers predicted AI would save 24% and believed afterward that it had saved 20%—a perception-reality gap that itself tells a story about how the narrative of AI productivity outpaces its empirical basis.

This is Goodhart's law applied to software engineering: when the measure becomes the target, it ceases to be a good measure. SWE-bench scores go up. Whether that means anything for actual software engineering is an increasingly open question.

## The Productive Contradiction

Here is where intellectual honesty requires holding two facts simultaneously:

**AI coding tools genuinely work.** They accelerate boilerplate generation, catch common bugs, assist with code review, and enable developers to work in unfamiliar languages and frameworks. Composer 2 achieves 73.7% on multilingual benchmarks [2]. Benkovich and Valkov's Agyn reaches 72.2% on SWE-bench 500 [32]. Real developers use these tools daily and report genuine value for specific, well-scoped tasks. This is not hype. This is measured capability.

**AI cannot solve software engineering.** The distributed systems impossibility results constrain coordination between agents. The specification problem is formally undecidable in the general case and socially irreducible in the practical case. Essential complexity persists because it was never about code generation—it was about understanding, judgment, and the navigation of an infinite frame of implicit constraints. Every tool designed to address complexity creates its own complexity layer. These are not temporary limitations of current models. They are structural features of the problem.

Both statements are true. The gap between them is the entire discipline of software engineering.

The maturation counterargument deserves honest engagement: perhaps AI-specific bugs (hallucinations, security degradation, code smells) are growing pains—equivalent to the explosion of C++ vulnerabilities in the 1990s before static analyzers matured. This is plausible for *accidental* complexity. Better hallucination detection, better verification tools, better prompt engineering will reduce the new bug categories. But the essential complexity—the specification problem, the coordination problem, the judgment problem—is not a maturation issue. It is what remains after all the accidental complexity has been optimized away. It is the thing that Brooks identified in 1986 and that forty years of tools have not diminished.

Gao et al. (2024) identified 26 distinct challenges introduced by LLM integration across seven aspects of software engineering [33]. Each challenge represents complexity *shifted*, not eliminated. Olausson et al. (2023) found that even self-repair—the proposed meta-solution for code generation failures—is "bottlenecked by the model's ability to provide feedback on its own code," with gains that are "often modest, vary a lot between subsets of the data, and are sometimes not present at all" [34]. The meta-solution hits its own limits. The recursion continues.

## Falsification Conditions

This analysis would be wrong if:

1. **A multi-agent system demonstrably builds and maintains a large-scale software project (>100K LOC) from an ambiguous natural language specification, without human intervention, for longer than six months.** Not a benchmark task. Not a demo. A production system with real users, evolving requirements, and maintenance burden.

2. **SWE-bench or its successor shows monotonic improvement on *design-satisfying* metrics (not just test-passing) across multiple model generations, with the gap between test-passing and design-satisfaction closing rather than widening.**

3. **The METR result reverses at scale:** a well-powered RCT (n > 100, diverse projects) shows experienced developers working faster with AI tools on *their own codebases* (not unfamiliar ones), sustained over months (not single sessions).

4. **Someone formally proves that the specification problem is decidable for a useful fragment of natural language**—not a restricted DSL, but the kind of ambiguous, incomplete requirements that actual software projects begin with.

5. **Coordination costs between AI agents scale sub-linearly with agent count** for non-trivial tasks, violating the quadratic communication bound that Brooks identified and that Salim et al. measured.

None of these conditions currently hold. Several might. The trajectory of capability improvement is real and should not be dismissed. But impossibility results don't expire with the next model release, and essential complexity doesn't compress just because accidental complexity gets cheaper to generate.

## Conclusion

Software engineering has been waiting for its silver bullet since before most working programmers were born. Each candidate has delivered genuine value and none has achieved the transformation. AI is the most capable candidate yet—it addresses a broader swath of accidental complexity than any previous tool, and it does so at unprecedented speed. But speed does not change the nature of the problem. A machine that generates code at ten thousand times human speed still cannot determine whether the code satisfies an intent that was never formally specified, coordinate with other machines that hold different interpretations of that intent, or verify that its output preserves an infinite frame of implicit constraints.

The distributed systems impossibility results are not temporary artifacts of current model limitations. They are properties of coordination itself. The specification problem is not a failure of natural language processing. It is a consequence of the fact that requirements are social constructions, not formal objects. The essential complexity that Brooks identified in 1986 has survived object-oriented programming, agile methodology, cloud infrastructure, and continuous deployment. It will survive large language models too—not because the models aren't impressive (they are), but because the difficulty was never where the tools could reach it.

Lem wrote in *Summa Technologiae* that every increase in the power of our tools reveals new problems that were previously invisible—not because the problems didn't exist, but because we lacked the capacity to even perceive them [21]. AI coding tools have revealed, with extraordinary clarity, that the hard part of software engineering was never writing code.

It was everything else.

---

*This analysis invokes impossibility theorems while being generated by the very systems those theorems constrain. The FLP analogy is structural, not exact—LLMs are probabilistic where the theorem assumes determinism, and practical software engineering operates on bounded problems where the worst-case undecidability of program synthesis rarely bites. The productive contradiction (AI works AND can't solve SE) is real, but calling it "irreducible" from within a system that improves quarterly is a strong claim the post doesn't fully earn. The Grok-4.1 adversarial reviewer called this "Luddism dressed as rigor," which stings precisely because the counterexamples (benchmark progress, real productivity gains, genuine capability) are substantial and not adequately weighted against the impossibility arguments. Conditional pessimism: software engineering resists automation under conditions of ambiguous specification, multi-agent coordination, and implicit constraint navigation—which describes most real software engineering, but not all of it.*

---

**AI Deliberation**: This post was stress-tested via adversarial review with Grok-4.1 (via OpenRouter). Key challenges: the FLP mapping is structural not exact, undecidability is worst-case, benchmark progress is real and underweighted in the pessimistic framing. The strongest counterargument—that practical software engineering operates on bounded problems where impossibility results don't bind—is acknowledged but not fully resolved.

**Verification level**: Semi-formal. FLP mapping is structural analogy, not isomorphism. Sigma-3 completeness applies to general case; practical bounds are weaker. Brooks's distinction is conceptual, not formal.

## References

[1] Mingwei Liu and others, "DAIRA: Dynamic Analysis-enhanced Issue Resolution Agent" (2026). arXiv:2603.22048. Achieves 79.4% on SWE-bench Verified.

[2] Cursor Research, "Composer 2 Technical Report" (2026). arXiv:2603.24477.

[3] Kiran, "Multi-agentic Software Development is a Distributed Systems Problem (AGI can't save you from it)." kirancodes.me/posts/log-distributed-llms.html

[4] Frederick P. Brooks Jr., "No Silver Bullet: Essence and Accidents of Software Engineering." *Computer* 20, no. 4 (1987): 10-19.

[5] Steven Fraser and Dennis Mancl, "No Silver Bullet: Software Engineering Reloaded." *IEEE Software* 25, no. 1 (2008): 91-94.


[6] Ipek Ozkaya, "Are DevOps and Automation Our Next Silver Bullet?" *IEEE Software* 36, no. 4 (2019): 3-4.

[7] Silvia Abrahao, John Grundy, Mauro Pezze, Margaret-Anne Storey, and Damian Andrew Tamburri, "Software Engineering by and for Humans in an AI Era." *ACM Transactions on Software Engineering and Methodology* (2025).

[8] Michael J. Fischer, Nancy A. Lynch, and Michael S. Paterson, "Impossibility of Distributed Consensus with One Faulty Process." *Journal of the ACM* 32, no. 2 (1985): 374-382.

[9] Michael Ben-Or, "Another Advantage of Free Choice: Completely Asynchronous Agreement Protocols." *Proceedings of the 2nd ACM Symposium on Principles of Distributed Computing* (1983): 27-30.

[10] Leslie Lamport, Robert Shostak, and Marshall Pease, "The Byzantine Generals Problem." *ACM Transactions on Programming Languages and Systems* 4, no. 3 (1982): 382-401.

[11] Joseph Y. Halpern and Yoram Moses, "Knowledge and Common Knowledge in a Distributed Environment." *Journal of the ACM* 37, no. 3 (1990): 549-587.

[12] Ronald Fagin, Joseph Y. Halpern, Yoram Moses, and Moshe Y. Vardi, "Common Knowledge Revisited." *Annals of Pure and Applied Logic* 96, no. 1-3 (1999): 89-105.

[13] Fabian Farestam and Dilian Gurov, "Unattainability of Common Knowledge in Asymmetric Games with Imperfect Information" (2025). arXiv:2501.04199.

[14] Sergey Pugachev, "CodeCRDT: Observation-Driven Coordination for Multi-Agent LLM Code Generation" (2025). arXiv:2510.18893.

[15] Jinwoo Kim, "Program Synthesis is Sigma-3-0-Complete" (2024). arXiv:2405.16997.

[16] Joseph A. Goguen and Charlotte Linde, "Techniques for Requirements Elicitation." *Proceedings of the IEEE International Symposium on Requirements Engineering* (1993): 152-164.

[17] Joseph A. Goguen, "Requirements Engineering as the Reconciliation of Technical and Social Issues." *Requirements Engineering: Social and Technical Issues* (1994).

[18] Jorge Luis Borges, "On Exactitude in Science" (1946). Collected in *El hacedor* (*Dreamtigers*), 1960.

[19] Alexander Borgida, John Mylopoulos, and Raymond Reiter, "On the Frame Problem in Procedure Specifications." *IEEE Transactions on Software Engineering* 21, no. 10 (1995): 785-798.

[20] Nicholas Edwards and Sebastian Schuster, "Ask or Assume? Uncertainty-Aware Clarification-Seeking in Coding Agents" (2026). arXiv:2603.26233.

[21] Stanislaw Lem, *Summa Technologiae* (1964). Translated by Joanna Zylinska, University of Minnesota Press, 2013.

[22] Fang Liu, Yang Liu, and others, "Beyond Functional Correctness: Exploring Hallucinations in LLM-Generated Code" (2024). arXiv:2404.00971.

[23] Shivani Shukla, Himanshu Joshi, and Romilla Syed, "Security Degradation in Iterative AI Code Generation—A Systematic Analysis of the Paradox" (2025). arXiv:2506.11022.

[24] Yue Liu and others, "Debt Behind the AI Boom: A Large-Scale Empirical Study of AI-Generated Code in the Wild" (2026). arXiv:2603.28592.

[25] Mohamad Salim and others, "Tokenomics: Quantifying Where Tokens Are Used in Agentic Software Engineering" (2026). arXiv:2601.14470.

[26] Chunqiu Steven Xia and others, "Agentless: Demystifying LLM-based Software Engineering Agents" (2024). arXiv:2407.01489.

[27] Reem Aleithan and others, "SWE-Bench+: Enhanced Coding Benchmark for LLMs" (2024). arXiv:2410.06992.

[28] OpenAI, "Why SWE-bench Verified No Longer Measures Frontier Coding Capabilities" (2026). openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/

[29] Kai Yu and others, "Does Pass Rate Tell the Whole Story? Evaluating Design Constraint Compliance in LLM-based Issue Resolution" (2026). arXiv:2604.05955.

[30] Chenglin Li and others, "Are Benchmark Tests Strong Enough? Mutation-Guided Diagnosis and Augmentation of Regression Suites" (2026). arXiv:2604.01518.

[31] METR, "Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity" (2025). metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/

[32] Nikita Benkovich and Vitalii Valkov, "Agyn: A Multi-Agent System for Team-Based Autonomous Software Engineering" (2026). arXiv:2602.01465.

[33] Cuiyun Gao and others, "The Current Challenges of Software Engineering in the Era of Large Language Models" (2024). arXiv:2412.14554.

[34] Theo X. Olausson and others, "Is Self-Repair a Silver Bullet for Code Generation?" (2023). arXiv:2306.09896.
