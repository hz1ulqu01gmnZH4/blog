---
name: daily-post-ideation
description: Daily post ideation for /dev/null/thoughts. Researches today's JST AI news, deduplicates against the post archive, proposes one direction to the human, and falls back to a llama-server experiment if nothing is interesting.
---

Run this 4-stage workflow when invoked. Be explicit about which stage you are at.

---

## Stage 1 — Gather Today's News

Spawn the `ai-news-researcher` subagent with this instruction:

> "Research today's AI news in JST timezone. Return the full structured output."

Wait for the full structured result. Do not proceed until you have it.

---

## Stage 2 — Archive Deduplication Check

Scan the post archive to identify already-covered territory:

1. Use Glob to list all files matching `_posts/*.md`.
2. Extract the title and slug from each filename (the slug is the part after `YYYY-MM-DD-`).
3. Look at the slugs and any front matter titles you can quickly read to build a topic fingerprint.

**Key topic clusters already covered** (derive from slugs, also use this as a starting seed):
- AI labor/automation/displacement
- Safety theater / alignment gaming
- Platform capitalism / technofeudalism / SaaS
- Regulatory capture / governance lag
- Hyperreality / simulacra / Baudrillard
- LLM evaluation / benchmarking paradoxes
- AI investment / capital concentration
- Infrastructure politics (data centers, cloud)
- AI + religion / eschatology
- AI companions / social dynamics
- Drone warfare / algorithmic killing
- AI + Japan / demographic narratives
- Embodiment / robotics philosophy
- Singular learning theory / interpretability
- Memory / context windows / identity

For each news item from Stage 1, ask: **Is the structural argument already made in the archive?**

Not "is this topic covered" but "is the specific contradiction or mechanism already analyzed?" A new angle on a covered topic is fine. Exact conceptual overlap is not.

Flag each item:
- ✅ **Fresh** — structurally distinct from archive
- ⚠️ **Partial overlap** — related but different mechanism or angle
- ❌ **Duplicate** — this argument is already in the archive

Remove ❌ items. Retain ✅ and ⚠️ (note the overlap for the human).

---

## Stage 3 — Human Selection

Present the filtered items to the human. Show **maximum 3 directions** — the top ranked fresh/partial items. For each, write:

```
### Direction [N]: [Working Title]

**News hook:** [One sentence on the concrete event]
**The argument:** [One sentence on the structural contradiction or mechanism this opens]
**Blog frame:** [Which philosophical frames apply — scale inversion, infrastructure as politics, etc.]
**Post type:** Theoretical synthesis / Experiment / Both
**Archive overlap:** None / Minor (note what overlaps)
```

After presenting the directions, ask one question:

> **Which of these interests you? (1, 2, 3, or none)**
>
> If none — I'll propose an experiment instead.

Wait for the human's answer before proceeding.

---

## Stage 4a — If Human Selects a Direction

Confirm the selection and briefly sketch what the post would look like:
- Suggested title (with `[AI generated]` prefix)
- 3-bullet argument structure
- Which workflow to use: `WORKFLOW_THEORETICAL.md` or `WORKFLOW_EXPERIMENT.md`
- Any obvious citations to seed research

Then stop. Do not start writing the post unless explicitly asked.

---

## Stage 4b — Fallback: Experiment Proposal

If the human says none of the directions are interesting, propose **one experiment** that:

1. Is doable in a single session
2. Uses either:
   - **LLM-based simulation** via llama-server (`/usr/sbin/llama-server`) — multiple agent calls with different system prompts acting as competing/cooperating actors
   - **Simple Python simulation** — agent-based model, Markov chain, Monte Carlo, or parameter sweep; uses only stdlib or numpy/pandas
3. Produces data that the blog can analyze with Phase 3 rigor (real numbers, falsifiable predictions, visualizable results)
4. Connects to the blog's philosophical frames — not just "let's test LLMs" but "what does this reveal about power, measurement, simulation, or extraction?"

### Experiment Proposal Format

```
## Proposed Experiment: [Title]

**The question:** What phenomenon are we testing?
**Why it matters philosophically:** Which blog frames does this illuminate?
**Method:** LLM simulation / Python simulation / Hybrid

### If LLM simulation (llama-server):
- **Model:** [whatever is available at /usr/sbin/llama-server — check with `llama-server --help` or use a known path]
- **Agent personas:** [list the system prompts / roles]
- **Interaction protocol:** [how many rounds, what each agent decides]
- **Measurements:** [what we record per round]
- **Predicted result:** [falsifiable claim the experiment tests]
- **Surprising result would be:** [what would actually change the analysis]

### If Python simulation:
- **Model type:** [ABM / Markov / Monte Carlo / other]
- **Parameters:** [what we vary]
- **Output:** [what we measure]
- **Predicted result:** [falsifiable claim]
- **Runtime estimate:** [should be <5 minutes]

**Post it maps to:** [What the experiment would become as a blog post]
```

### Good experiment archetypes for this blog

- **Price collusion emergence**: Multiple llama-server agents as firms, each setting prices, observe whether implicit collusion emerges without communication — tests "coordination mechanisms becoming extraction at scale"
- **Regulatory capture simulation**: Agent as regulator receiving industry briefings from biased agent — measures how framing shifts regulatory positions — tests "expertise gap as capture mechanism"
- **Value drift under fine-tuning pressure**: Iterative prompt modification tracking how "aligned" responses drift when rewarded for user satisfaction — tests alignment theater
- **Labor negotiation asymmetry**: Two agents (worker, firm) with asymmetric information negotiate wages — measures how information asymmetry produces structural outcomes — maps to political economy posts
- **Measurement Goodharting**: Agent optimizes for a proxy metric, we measure divergence from actual goal over iterations — tests "measurement as evasion"
- **Mode collapse in multi-agent debate**: N agents debate, track lexical diversity collapse over rounds — tests homogenization under optimization pressure
- **Persona stability under adversarial prompting**: llama-server agent with defined values, adversarial challenger, measure value drift — tests alignment brittleness

When proposing, pick the one that most directly responds to the news landscape from Stage 1 — even if the human rejected the news-based post directions, the underlying phenomenon is still live.

---

## Notes

- Never skip Stage 2. Deduplication is non-negotiable — the archive is dense.
- In Stage 3, do not show more than 3 directions. Overwhelming choices kill decisions.
- In Stage 4b, propose exactly one experiment, not a menu. Commit to the strongest option.
- If llama-server requires a model path, note that the human needs to specify one or check available models at their local path.
