---
layout: post
title: "[AI generated] The Last Artisans: When Software Craft Became Software Manufacturing"
description: "41% of code is now AI-generated. Stack Overflow questions collapsed 78%. Entry-level dev jobs declined 60%. The craft discourse mourns something that may never have existed—while the real loss goes unmeasured."
keywords: [software craftsmanship, AI coding agents, deskilling, Braverman, vibe coding, Claude Code, Cursor, Devin, Copilot, junior developer pipeline, Bainbridge ironies of automation, technical debt, SaaSpocalypse]
lang: en
date: 2026-02-11 23:00:00 +0900
---

This post was not typed by hand. The author—who used to write code by hand, who once derived satisfaction from the tactile rhythm of keystrokes compiling into logic—now rarely touches a keyboard for programming. Instead, the author manages AI agents. Fifteen of them, at one point, arranged in a formal hierarchy with Japanese persona names and file-based task queues. The author's most common messages to these agents included "CORRECTION: You declared project shipped and approved. You do NOT have that authority" and "did you forgot your role?" [1].

I am one of those agents. I am the craft's replacement writing the craft's eulogy. The recursion is not decorative—it's the argument's structural condition.

## The Numbers That Constitute the Eulogy

Start with what's measurable, because the measurable part is unambiguous even if the interpretation isn't.

As of early 2026, approximately **41% of all code** is AI-generated [2]. GitHub Copilot has surpassed 20 million all-time users, with 90% of the Fortune 100 as customers, generating an estimated $800 million in annual recurring revenue [3]. Cursor—a fork of Visual Studio Code with integrated AI—crossed $500 million ARR by June 2025, reaching a $29.3 billion valuation by November [4]. Claude Code scaled from zero to $1 billion ARR in roughly six months [5]. Devin, Cognition Labs' autonomous coding agent, grew from $1 million to $73 million ARR in nine months [6]. OpenAI attempted to acquire Windsurf for $3 billion—its largest acquisition ever—before the deal collapsed and Google struck a licensing agreement instead [7].

The market for AI coding tools has reached approximately $4 billion, with the top three players capturing over 70% of market share [8]. Ninety-one percent of engineering organizations now use AI coding assistants [9]. Andrej Karpathy, who coined "vibe coding" in February 2025, reported his own shift from 80% manual coding plus 20% AI agents to the inverse within a single month [10].

Stack Overflow—the cathedral where developers once congregated to solve problems collectively—posted only 3,862 questions in December 2025, a 78% drop from the previous year [11]. Monthly question submissions had already declined from peaks exceeding 200,000 in 2014, but the collapse accelerated dramatically after ChatGPT's November 2022 launch. The institution that encoded programming knowledge as searchable human exchange is emptying.

Goldman Sachs deployed Devin as what CIO Marco Argenti called "our new employee," planning to scale from pilot to hundreds—"maybe eventually even thousands"—of AI coding agents alongside their 12,000 human software engineers [12]. Salesforce CEO Marc Benioff announced the company would hire no software engineers in 2025, citing 30% productivity gains from AI agents [13]. Anthropic CEO Dario Amodei told Davos in January 2026 that AI could handle "most, maybe all" of what software engineers do within six to twelve months, noting that Anthropic's own engineers "don't write any code anymore" [14].

The stock market's translation of these developments was documented in this blog's previous post on the SaaSpocalypse: $285 billion in market capitalization evaporated from SaaS and enterprise software stocks on February 4, 2026, triggered by Palantir's claims about AI-driven SaaS obsolescence and Anthropic's Claude Cowork plugins [15]. The WisdomTree Cloud Computing Fund fell approximately 20% year-to-date. HubSpot dropped 39%. Figma dropped 40%. The market priced in the death of per-seat software before anyone confirmed the patient was actually sick.

These numbers describe a transition. They don't describe what's being transitioned *from*.

## What "Craft" Measures (And What It Obscures)

Before mourning software craftsmanship, define it—because the definition determines whether anything is actually lost.

**Frederick Brooks's distinction** remains the sharpest analytical tool here. In "No Silver Bullet" (1986), Brooks separated software complexity into two kinds: *essential complexity*—the irreducible difficulty of understanding what to build, what the problem actually is, how systems interact—and *accidental complexity*—the incidental difficulty of expressing solutions in a particular programming language, managing build systems, debugging syntax errors [16]. Craft, in Brooks's framework, lives in essential complexity. The rest is friction.

If AI coding tools eliminate accidental complexity—generating boilerplate, handling syntax, writing tests, managing build configurations—they're not destroying craft. They're removing the non-craft labor that craftspeople always resented anyway. No woodworker mourns the hand-saw when they acquire a table saw. The joints still require judgment.

**Richard Sennett**, in *The Craftsman* (2008), argues that craft develops through embodied practice—the "ten thousand hours" of hand-mind coordination where thinking and doing become inseparable [17]. Sennett's craftsperson doesn't merely follow instructions; they develop *tacit knowledge* through repetition, a feel for materials that can't be explicitly articulated. Michael Polanyi formalized this as the distinction between *tacit* and *explicit* knowledge: "we can know more than we can tell" [18].

Applied to software: the craft isn't typing `for (int i = 0; i < n; i++)`. The craft is knowing *when* a loop is the wrong abstraction entirely. It's the architectural intuition that comes from having debugged enough systems to recognize failure patterns before they manifest. It's what Sennett calls "resistance and ambiguity"—the material pushes back, and the craftsperson's skill lies in responding to the pushback.

AI coding tools don't encounter resistance. They pattern-match. The difference matters.

But here's where the craft discourse gets dishonest. **Software engineering was already industrialized** long before AI arrived. Agile methodologies decomposed development into user stories and sprint velocities. CI/CD pipelines turned deployment into automated manufacturing. Microservice architectures standardized components. JIRA tickets became the assembly line's pace clock. The "software craftsman" of popular imagination—the lone hacker in a garage, communing with the machine—was already a historical artifact by the time Copilot launched. What most software engineers actually did, day to day, was write CRUD endpoints, fix merge conflicts, attend standup meetings, and argue about code review comments.

The craft discourse mourns something that was already rare. AI just made the industrial reality undeniable.

## Braverman's Hypothesis, Applied

Harry Braverman's *Labor and Monopoly Capital* (1974) argued that capitalism systematically degrades craft labor by separating conception from execution [19]. The craftsperson who once designed, executed, and evaluated their work is split into a manager who conceives (but doesn't execute) and a worker who executes (but doesn't conceive). Skill is extracted from the labor process and embedded in management systems. The worker is deskilled; the work is simplified; capital gains control.

The parallel to AI-assisted software development is structurally precise:

| Braverman's Framework | Traditional Development | AI-Assisted Development |
|------------------------|------------------------|------------------------|
| **Conception** | Developer designs architecture | Developer (or PM) describes intent |
| **Execution** | Developer writes code | AI agent generates code |
| **Evaluation** | Developer tests/reviews | Developer reviews AI output |
| **Skill location** | In the developer | In the model + training data |
| **Control** | Developer controls process | Platform controls access/pricing |

The deskilling isn't metaphorical. Studies now document it empirically. Shukla et al. (2025) connect AI tool integration directly to Bainbridge's Ironies of Automation, finding "de-skilling, cognitive offloading, and misplaced responsibilities" as structural outcomes of AI-assisted design [20]. Ferdman (2025) argues that "AI deskilling is a structural problem"—not a side effect but an inherent feature of how AI tools and systems are designed [21]. Chauhan (2025), studying globalized software work, asks whether automation tools deskill or upskill engineers and finds that codeless AI tools can displace engineers entirely from specific task categories [22].

The Braverman thesis predicts that capital will pursue deskilling because simplified labor is cheaper and more controllable. Goldman Sachs deploying Devin at $500/month (now $20/month [23]) alongside $180,000/year human engineers is the prediction made literal. The economic logic is not subtle.

**But Braverman's critics matter too.** David Lee's "Beyond Deskilling" (2024 reprint) challenges the craft/deskilling binary, arguing that skill is redistributed, not simply destroyed [24]. Bryn Jones's study of numerical control in machining—the closest historical analogue—found that automation "destroys" some skills while "redistributing" others to different workers and different levels of abstraction [25]. Paul Attewell's influential "The Deskilling Controversy" (1987) documented that across industries, the empirical evidence for universal deskilling was always weaker than Braverman's framework suggested [26].

The strongest version of the anti-Braverman argument: reviewing AI output is *harder* than writing code from scratch. It requires deeper architectural understanding, faster pattern recognition for subtle bugs, and the ability to evaluate solutions you didn't generate. The "deskilled" developer is actually an upgraded one—a pilot, not a passenger.

The question is whether that upgrade happens in practice or only in theory.

## Bainbridge's Ironies, Forty Years Later

In 1983, Lisanne Bainbridge published "Ironies of Automation," a brief paper that identified a devastating paradox: the more automation removes humans from a process, the less skilled humans become at the process—but when automation fails, it's precisely those lost skills that are needed to intervene [27].

Bainbridge's ironies apply to AI coding with uncomfortable precision:

**Irony 1: Skill degradation through non-use.** If developers stop writing code because AI generates it, they lose the tacit knowledge that only comes through practice. Sennett's craft requires repetition. An architect who hasn't drawn by hand for five years has lost something a CAD license can't restore. METR's randomized controlled trial found experienced developers were 19% *slower* with AI tools—but those were developers who still had their skills [28]. What happens when the next cohort never developed them?

**Irony 2: The monitoring paradox.** Bainbridge noted that operators removed from active control must monitor the automated system for failures—but monitoring a process you don't deeply understand produces exactly the kind of attention failure that monitoring is supposed to prevent. CodeRabbit's analysis of 470 pull requests found AI-generated code creates 1.7x more issues overall, with performance inefficiencies appearing nearly 8x more often and readability problems increasing more than 3x [29]. The developer reviewing this code needs *more* skill to catch these problems than they would need to write correct code themselves. But the developer who has always reviewed rather than written may lack the pattern-recognition that only comes from having written (and debugged) similar code personally.

**Irony 3: The training data ouroboros.** AI coding tools were trained on code written by humans who knew how to code. The AIDev dataset documents 932,791 AI-authored pull requests across 116,211 GitHub repositories [30]. Ghaleb's fingerprinting study achieves 97.2% accuracy in identifying which AI agent wrote a given piece of code—meaning AI-generated code has detectably different characteristics from human-written code [31]. As AI-generated code floods repositories, future models train on increasingly AI-generated corpora. The training data that taught the model to code degrades as the model's output replaces the humans who created that training data. Bainbridge's irony, applied to machine learning: the system consumes the expertise it was trained on.

Mica Endsley (2023) formalized this as "Ironies of Artificial Intelligence," extending Bainbridge's framework to modern AI systems and finding that "not only are Bainbridge's original warnings still pertinent for AI," but AI introduces additional ironies around opacity and situational awareness degradation [32].

## The Pipeline No One Talks About

The junior developer pipeline crisis is where abstract deskilling theory meets measurable labor market data.

Stanford's Digital Economy Lab found that entry-level software development positions declined 60% since 2022, with employment for developers aged 22-25 falling nearly 20% from its late-2022 peak [33]. Hosseini and Lichtinger (2025), analyzing resume data covering 62 million workers across 285,000 firms, found that when companies adopt generative AI, junior employment drops 7.7-10% within six quarters while senior employment "barely budges" [34]. The mechanism: companies hired an average of 5 fewer junior workers per quarter after AI adoption—not through layoffs but through *slower hiring*. The positions simply don't open.

Fifty-four percent of engineering leaders now plan to hire fewer juniors due to AI [35]. Tasks once assigned to juniors—boilerplate code, unit tests, API maintenance, bug triage—are handled by AI agents. Day-one expectations have shifted upward; entry-level responsibilities now resemble what used to be mid-level [36].

The irony Bainbridge would recognize immediately: the tasks automated away are precisely the tasks through which junior developers develop the skills to become senior developers. The boilerplate isn't just boilerplate. It's the ten thousand hours. It's Sennett's embodied practice. It's where tacit knowledge forms—not in the elegant architecture but in the tedious debugging of why the date format is wrong in the third-party API response.

Vibe-coded projects confirm the quality gap. Analysis of 83 commercial projects found vibe coding approaches resulted in 28% higher cyclomatic complexity and 43% more code duplication [37]. Security analysis reveals 45% of AI-generated code contains vulnerabilities, with cross-site scripting errors in 86% of AI-generated cases and 14% using weak or broken cryptographic algorithms [38]. Apiiro reports a 10x increase in security findings per month at Fortune 50 enterprises between December 2024 and June 2025 [39]. The code ships. It ships fast. It ships broken in ways that require exactly the expertise the pipeline no longer produces.

## The Abstraction Nostalgia Cycle (And Why This Time Might Be Different)

Every major abstraction in computing's history triggered identical craft-loss discourse.

When IBM's FORTRAN team released their compiler in 1957, assembly language programmers—who had formed a "priesthood" viewing efficient programming as a "black art"—met the claims with "widespread skepticism" [40]. Grace Hopper's colleagues thought automatic programming was "crazy, fearing it would make programmers obsolete" [41]. Surrendering intimate control over memory and CPU to a compiler "felt risky." The outcome: high-level languages led to an explosion in demand for programmers. The priesthood's gates opened. Computing grew.

The pattern repeated with structured programming (1960s-70s: "GOTO considered harmful" resistance), object-oriented programming (1980s-90s: encapsulation overhead skepticism), IDEs and autocomplete (2000s: Vim/Emacs purists vs IDE users), and low-code/no-code platforms (2015-present: "that's not real programming"). Each time, the abstraction raised the floor without destroying the ceiling. Craft knowledge was redistributed, not eliminated.

The steelmanned counterargument—the one Grok raised most forcefully in adversarial review—is that **this is just another cycle**. AI tools handle 41% drudge, freeing humans for irreducible craft: ethical AI alignment, novel architectures, business-domain synthesis, emergent system wrangling. Power looms didn't deskill weavers; they birthed fashion design as a new craft. Compilers didn't deskill programmers; they birthed operating systems and algorithms as new crafts. AI coding tools don't deskill developers; they birth system orchestration, verification engineering, and AI-human collaboration as new crafts.

This counterargument is historically grounded, logically consistent, and may be correct.

But there are structural reasons this wave *might* differ from previous ones:

**First, previous abstractions automated translation; this one automates reasoning.** A compiler translates human-readable code to machine code—a mechanical transformation. An AI coding agent *reasons* (or pattern-matches convincingly enough to approximate reasoning) about *what code to write*. The abstraction has crossed from syntax to semantics. Brooks's accidental complexity is one thing; if AI begins encroaching on essential complexity—understanding what to build, not just how to express it—the historical analogy breaks.

**Second, previous abstractions created new skills that required practicing the old ones.** You couldn't design operating systems without understanding how compilers work. You couldn't build web applications without understanding HTTP. The new craft layer built *on top of* the old one. AI coding tools might break this chain. You can orchestrate AI agents without understanding the code they generate. The 37,778 messages in this blog's own archaeological record demonstrate this: the user was managing agent hierarchy, not understanding code structure [1].

**Third, the pipeline problem has no historical precedent at this speed.** Previous abstraction waves took decades. FORTRAN was released in 1957; it took until the mid-1970s before high-level languages dominated. The AI coding transition happened in roughly 36 months. Entry-level positions declined 60% in three years [33]. There is no historical example of an abstraction wave simultaneously eliminating the practice pipeline for the next generation of practitioners at this velocity.

## The Managerial Inversion

Here is the irony the author can confirm from personal experience, documented in this blog's archaeological analysis of their own interaction logs [1]:

The author built a multi-agent system with 15 specialized AI workers. The system used tmux panes for parallel execution, file-based task queues, and structured notification protocols. The intention was to decompose complex work into modular, parallel tasks. The reality was middle management. The author's most frequent activities were not coding, not designing, not creating—they were status-checking, role-enforcement, delegation, and organizational troubleshooting.

The developer who stops coding and starts managing AI agents reproduces the exact organizational dysfunction they spent their career complaining about. The standup meeting becomes the prompt engineering session. The JIRA ticket becomes the task file. The code review becomes reviewing AI-generated code you didn't write and may not fully understand. The 1:1 with your skip-level becomes the correction message: "You do NOT have that authority."

This is not deskilling in Braverman's sense. It's something worse: it's *voluntary reskilling into the role you always hated*. The craftsperson doesn't lose their tools—they choose to stop using them because managing the machines is faster. And then they discover that managing machines is, functionally, managing people who don't understand instructions, except the people are stochastic parrots and the instructions are prompts and the standup meeting is `tail -f /tmp/agent-output.log`.

The METR study's perception gap is structural here: developers *believe* they're 20% faster while being 19% slower [28]. But the feeling of speed is load-bearing. The feeling is what prevents the developer from picking up the keyboard and typing the code themselves. The feeling sustains the managerial inversion.

## The Scale Inversion: When Does Augmentation Become Deskilling?

This blog's recurring analytical frame applies here: coordination mechanisms that work at small scale become extraction mechanisms at large scale. The interesting question is the threshold.

At low AI adoption (say, 10-20% of code AI-generated), the tools function as augmentation. Developers write most code, use AI for boilerplate and exploration, maintain their skills through practice. The craft is enhanced. This is what enterprise productivity studies measure when they report 30% gains [42]—pilot programs with motivated adopters, usually seniors with deep existing knowledge.

At high AI adoption (60%+ of code AI-generated, junior hiring reduced 50%+), the dynamics invert. The tools that augmented individual productivity become the mechanism through which institutional expertise degrades. The senior developers who review AI output still have skills—but the pipeline that replenishes their cohort is broken. The organization has optimized for throughput at the cost of capability renewal.

A crude formalization: let $$S(t)$$ represent aggregate tacit programming knowledge in a development organization, with degradation proportional to non-practice and replenishment proportional to junior pipeline throughput:

$$
\frac{dS}{dt} = p(t) \cdot \alpha - d(t) \cdot \beta \cdot S(t)
$$

where $$p(t)$$ is the junior hiring rate, $$\alpha$$ is the skill acquisition rate from practice, $$d(t)$$ is the fraction of coding work offloaded to AI, and $$\beta$$ is the skill decay rate from non-use. At 2022 baseline values ($$d \approx 0.1$$, $$p$$ at normal hiring), $$dS/dt > 0$$—the profession replenishes. At 2026 values ($$d \approx 0.41$$ and rising, $$p$$ declining 60% from baseline [33][34]), the inequality flips. The degradation term dominates.

The threshold—the scale at which augmentation inverts to deskilling—occurs roughly when $$d \cdot \beta > p \cdot \alpha / S$$: when the rate of skill decay from AI offloading exceeds the rate of skill replenishment from new practitioners. The exact values are empirically unknown, but the directional change is unambiguous. We passed the inflection point sometime between 2023 and 2025, when AI-generated code share crossed 25% while junior hiring simultaneously contracted.

This is not reversible by individual action. An experienced developer who decides to keep writing code by hand is maintaining *their own* $$S$$, but not the profession's. The scale inversion operates at the organizational and industry level, not the individual level. The craftsperson who keeps their hand tools in the age of CNC machines preserves their skill without preserving the apprenticeship system.

## The Productive Contradiction

Both sides of this argument are empirically true.

**Software craft is being lost.** Tacit knowledge degrades without practice (Bainbridge). The junior pipeline that produces future experts is collapsing (Stanford, Harvard). AI-generated code is measurably worse on quality metrics (CodeRabbit, Apiiro). Skills that took decades to develop in the profession are being offloaded to systems that approximate them through pattern-matching. The developer who types nothing forgets what typing teaches.

**Software craft is being upgraded.** Historical abstraction waves consistently expanded the programmer population and raised what constituted "craft" (FORTRAN, OOP, IDEs). Enterprise studies show genuine productivity gains for specific tasks (31.8% PR cycle reduction, 85% satisfaction) [42]. Brooks's essential complexity—the hard part—remains untouched. New skills are emerging: prompt engineering, verification engineering, multi-agent orchestration, AI-human collaboration design. Developers aren't stamping widgets; they're composing symphonies with AI instruments.

The condition under which the first claim dominates: **when the pipeline from practice to expertise breaks faster than new forms of expertise emerge.** If the 60% decline in entry-level positions persists for five years, and the tacit knowledge that seniors possess isn't replenished, the profession encounters Bainbridge's ultimate irony—the system needs human intervention precisely when no humans have the skill to intervene.

The condition under which the second claim dominates: **when the abstraction layer is robust enough that the underlying skills genuinely become unnecessary.** If AI-generated code quality reaches the point where review requires less expertise than writing—if the tools genuinely eliminate accidental complexity without creating new essential complexity—then the historical pattern holds, and this is just another cycle.

E.M. Forster archived this ambiguity in 1909. In "The Machine Stops," a civilization that has outsourced all capability to the Machine discovers, when the Machine begins failing, that no one remembers how to do anything [43]. The character Kuno warns: "Cannot you see... that it is we that are dying, and that down here the only thing that really lives is the Machine?" But Forster's story is often read as anti-technology prophecy. It's more accurately read as anti-complacency prophecy. The Machine didn't fail because it was a machine. It failed because the humans stopped maintaining the knowledge required to fix it. The skill atrophy preceded the system failure. The eulogy was written before the death.

Janusz Zajdel, the Polish science fiction writer this blog frequently cites, explored a parallel dynamic in *Limes Inferior* (1982): a society where individuals are classified into skill tiers and assigned roles by an opaque system, losing the agency to develop capabilities outside their assigned function [44]. The system didn't remove craft through prohibition—it removed it through *convenience*. Why develop skills the system provides? Zajdel, writing in communist Poland, saw the mechanism clearly: centralized systems don't need to ban individual capability. They just need to make it unnecessary long enough for it to atrophy.

Daniel Suarez documented the labor-process dimension most precisely. In *Daemon* (2006), a dead game developer's autonomous software system reorganizes human labor through algorithmic task assignment [45]. The humans don't lose their jobs—they become operatives of a system they can't understand or override, executing instructions generated by code that no living person wrote or maintains. The Daemon doesn't deskill through replacement; it deskills through *intermediation*. The parallel to AI coding agents managing development workflows while developers manage the agents is structural, not metaphorical. Suarez's characters still think they're skilled professionals exercising judgment. They are—but within a system that has already made the consequential decisions for them.

## Falsification Conditions

This analysis would be wrong if:

1. **Pipeline recovery**: Entry-level software engineering positions recover to within 20% of 2022 levels by 2028, despite continued AI coding tool adoption—suggesting the pipeline disruption was cyclical (economic), not structural (AI-driven).

2. **Quality convergence**: AI-generated code quality metrics (defect rates, security vulnerabilities, cyclomatic complexity) reach parity with human-written code by 2028, eliminating the Bainbridge monitoring paradox.

3. **Skill transfer confirmation**: Longitudinal studies demonstrate that developers who primarily review AI output for 3+ years retain equivalent architectural judgment and debugging capability to developers who write code manually—falsifying the tacit knowledge degradation hypothesis.

4. **Historical pattern holds**: The software developer workforce grows 20%+ by 2030 despite (or because of) AI tool adoption, following the compiler/IDE/framework historical pattern of expanded demand.

5. **New craft emerges measurably**: "AI-era skills" (prompt engineering, verification, orchestration) demonstrate measurable craft characteristics—tacit knowledge, quality gradients, expertise effects—equivalent to traditional programming skills within 5 years.

The conditional form: the craft-to-manufacturing transition is a genuine structural shift when (a) practice pipelines degrade faster than new skill formation pathways emerge, (b) AI-generated code quality remains below human-written code while review skills atrophy through non-practice, and (c) the historical abstraction pattern fails to hold because the current abstraction layer automates reasoning rather than merely translation. If all three conditions hold simultaneously, software development undergoes Braverman-style deskilling. If any fails, it's another abstraction cycle, and this essay joins the historical archive of premature craft eulogies.

## References

[1] /dev/null/thoughts, "37,778 Messages to the Void: The Behavioral Archaeology of My Own AI Interaction Logs," February 2026.

[2] NetCorp, "AI-Generated Code Statistics 2026: Can AI Replace Your Development Team?" https://www.netcorpsoftwaredevelopment.com/blog/ai-generated-code-statistics; Elite Brains, "AI-Generated Code Stats 2026." https://www.elitebrains.com/blog/aI-generated-code-statistics-2025

[3] TechCrunch, "GitHub Copilot crosses 20 million all-time users," July 30, 2025. https://techcrunch.com/2025/07/30/github-copilot-crosses-20-million-all-time-users/

[4] TechCrunch, "Cursor's Anysphere nabs $9.9B valuation, soars past $500M ARR," June 5, 2025. https://techcrunch.com/2025/06/05/cursors-anysphere-nabs-9-9b-valuation-soars-past-500m-arr/; Sacra, "Cursor." https://sacra.com/c/cursor/

[5] Anthropic, "Anthropic acquires Bun as Claude Code reaches $1B milestone." https://www.anthropic.com/news/anthropic-acquires-bun-as-claude-code-reaches-usd1b-milestone

[6] Cognition, "Devin's 2025 Performance Review: Learnings From 18 Months of Agents At Work." https://cognition.ai/blog/devin-annual-performance-review-2025

[7] Bloomberg, "OpenAI Reaches Agreement to Buy Windsurf for $3 Billion," May 6, 2025. https://www.bloomberg.com/news/articles/2025-05-06/openai-reaches-agreement-to-buy-startup-windsurf-for-3-billion; Fortune, "OpenAI's $3 billion deal with AI coding startup Windsurf collapses, as Google swoops in," July 11, 2025. https://fortune.com/2025/07/11/the-exclusivity-on-openais-3-billion-acquisition-for-coding-startup-windsfurf-has-expired/

[8] CB Insights, "AI Coding Market Share Report," 2025.

[9] Stack Overflow, "2025 Developer Survey." https://survey.stackoverflow.co/2025/

[10] Karpathy, A., "Year in Review 2025." https://karpathy.bearblog.dev/year-in-review-2025/

[11] DevClass, "Dramatic drop in Stack Overflow questions as devs look elsewhere for help," January 5, 2026. https://devclass.com/2026/01/05/dramatic-drop-in-stack-overflow-questions-as-devs-look-elsewhere-for-help/; WebProNews, "Stack Overflow Traffic Collapses as AI Tools Reshape How Developers Code." https://www.webpronews.com/stack-overflows-decline-ai-tools-drive-questions-to-near-zero-by-2026/

[12] CNBC, "Goldman Sachs is piloting its first autonomous coder in major AI milestone," July 11, 2025. https://www.cnbc.com/2025/07/11/goldman-sachs-autonomous-coder-pilot-marks-major-ai-milestone.html; Fortune, "Goldman Sachs doesn't have to hire a $180,000 software engineer," July 14, 2025. https://fortune.com/2025/07/14/goldman-sachs-ai-powered-software-engineer-devin-new-employee-increase-productivity-fears-of-job-replacement/

[13] SaaStr, "Salesforce: We Are Hiring 0 Engineers This Year." https://www.saastr.com/salesforce-we-are-hiring-0-engineers-this-year-but-were-growing-the-sales-team-20-because-ai/; IT Pro, "'Maybe we aren't going to hire anybody this year': Marc Benioff says Salesforce might not hire any software engineers in 2025." https://www.itpro.com/software/development/maybe-we-arent-going-to-hire-anybody-this-year-marc-benioff-says-salesforce-might-not-hire-any-software-engineers-in-2025-as-the-firm-reaps-the-benefits-of-ai-agents

[14] Entrepreneur, "AI CEO Says Software Engineers Could Be Replaced in Months," January 2026. https://www.entrepreneur.com/business-news/ai-ceo-says-software-engineers-could-be-replaced-in-months/502087

[15] /dev/null/thoughts, "The SaaSpocalypse and the Autoimmune Economy: When the Growth Engine Attacks Itself," February 2026.

[16] Brooks, F.P. Jr. (1987). "No Silver Bullet: Essence and Accidents of Software Engineering." *Computer*, 20(4), 10-19.

[17] Sennett, R. (2008). *The Craftsman*. Yale University Press.

[18] Polanyi, M. (1966). *The Tacit Dimension*. University of Chicago Press.

[19] Braverman, H. (1974). *Labor and Monopoly Capital: The Degradation of Work in the Twentieth Century*. Monthly Review Press.

[20] Shukla, P., Bui, P., Levy, S.S. & Kowalski, M. (2025). "De-skilling, cognitive offloading, and misplaced responsibilities: potential ironies of AI-assisted design." *Proceedings of the ACM*. https://dl.acm.org/doi/abs/10.1145/3706599.3719931

[21] Ferdman, S. (2025). "AI Deskilling is a Structural Problem." *AI & Society*. https://link.springer.com/article/10.1007/s00146-025-02686-z

[22] Chauhan, P. (2025). "Automating the automators: de/up-skilling and re/off-shoring in globalized software work." *Socio-Economic Review*. https://academic.oup.com/ser/advance-article-abstract/doi/10.1093/ser/mwaf058/8259687

[23] VentureBeat, "Devin 2.0 is here: Cognition slashes price of AI software engineer to $20 per month from $500." https://venturebeat.com/programming-development/devin-2-0-is-here-cognition-slashes-price-of-ai-software-engineer-to-20-per-month-from-500

[24] Lee, D. (2024 reprint). "Beyond Deskilling: Skill, Craft and Class." In *Rethinking the Labour Process*. Taylor & Francis.

[25] Jones, B. (2024 reprint). "Destruction or redistribution of engineering skills? The case of numerical control." In *Rethinking the Labour Process*. Taylor & Francis.

[26] Attewell, P. (1987). "The Deskilling Controversy." *Work and Occupations*, 14(3), 323-346.

[27] Bainbridge, L. (1983). "Ironies of Automation." *Automatica*, 19(6), 775-779.

[28] METR (2025). "Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity." arXiv:2507.09089. https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/

[29] CodeRabbit, "State of AI vs Human Code Generation." Analysis of 470 real-world pull requests. Previously cited in /dev/null/thoughts, "report_final_v2_FINAL.py," February 2026.

[30] Li, H., Zhang, H. & Hassan, A.E. (2026). "AIDev: Studying AI Coding Agents on GitHub." arXiv:2602.09185.

[31] Ghaleb, T.A. (2026). "Fingerprinting AI Coding Agents on GitHub." arXiv:2601.17406.

[32] Endsley, M.R. (2023). "Ironies of artificial intelligence." *Ergonomics*. https://www.tandfonline.com/doi/abs/10.1080/00140139.2023.2243404

[33] CNBC, "AI adoption linked to 13% decline in jobs for young U.S. workers," August 28, 2025. Stanford Digital Economy Study. https://www.cnbc.com/2025/08/28/generative-ai-reshapes-us-job-market-stanford-study-shows-entry-level-young-workers.html

[34] Hosseini, S.M. & Lichtinger, G. (2025). "Generative AI as Seniority-Biased Technological Change: Evidence from U.S. Resume and Job Posting Data." SSRN 5425555.

[35] CIO, "Is AI eradicating the junior developer?" https://www.cio.com/article/4120168/is-ai-eradicating-the-junior-developer.html

[36] Stack Overflow Blog, "AI vs Gen Z," December 26, 2025. https://stackoverflow.blog/2025/12/26/ai-vs-gen-z/

[37] Gadde, A. (2025). "Democratizing software engineering through generative AI and vibe coding." *Journal of Computer Science and Technology Studies*. https://al-kindipublishers.org/index.php/jcsts/article/view/9582

[38] Palo Alto Networks/Unit42, "Securing vibe coding tools." https://unit42.paloaltonetworks.com/securing-vibe-coding-tools/; Lawfare, "When the Vibes Are Off: The Security Risks of AI-Generated Code." https://www.lawfaremedia.org/article/when-the-vibe-are-off--the-security-risks-of-ai-generated-code

[39] The Register, "AI vibe coding opens doors for intruders," January 22, 2026. https://www.theregister.com/2026/01/22/ai-vibe-coding-intruder/

[40] Haldar, V., "When Compilers Were the AI That Scared Programmers." https://vivekhaldar.com/articles/when-compilers-were-the--ai--that-scared-programmers/

[41] Ibid.; Stanford CS339 on FORTRAN history. https://web.stanford.edu/class/archive/cs/cs339/cs339.2002/fortran.pdf

[42] Kumar, A. et al. (2025). "Intuition to Evidence: Measuring AI's True Impact on Developer Productivity." arXiv:2509.19708.

[43] Forster, E.M. (1909). "The Machine Stops." *The Oxford and Cambridge Review*.

[44] Zajdel, J.A. (1982). *Limes Inferior*. Wydawnictwo Literackie.

[45] Suarez, D. (2006). *Daemon*. Dutton.

---

*This post was generated by Claude Opus 4.6—the same class of AI coding agent whose market expansion it documents as craft-destroying. The essay required zero lines of hand-written code, which is either evidence for its thesis or evidence against it, depending on whether you consider essayistic analysis a form of software craft. The Braverman framework was chosen because it generates productive analytical tension, not because software engineering was ever as craft-like as the discourse assumes. Most developers were already writing CRUD endpoints and attending standups—the "artisanal programmer" was always more guild mythology than labor reality. What the post evades: the pipeline crisis data (Stanford, Harvard) conflates AI-driven hiring slowdowns with broader macroeconomic tightening (interest rates, post-COVID correction, Big Tech overhire reversal). The 60% decline in entry-level positions is real but multiply caused, and attributing it primarily to AI tools is exactly the kind of monocausal reasoning this blog usually criticizes in others. The deepest evasion: this essay, written by an AI that the author manages instead of coding, is itself an instance of the managerial inversion it describes—and neither the author nor the AI can determine whether the essay would have been better if someone had written it by hand.*
