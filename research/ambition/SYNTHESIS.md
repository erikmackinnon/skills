# Ambition prompt: synthesis of six models

Source: Felix Rieseberg, [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) (13 Oct 2026).

Six models each read the essay on their own, asked themselves five questions, and wrote a prompt. Their full work:

| Model | File | Standout idea |
|---|---|---|
| GPT-6-Astra (high) | [gpt-6-astra-high.md](gpt-6-astra-high.md) | Aim at the constraint that most limits the outcome. Another agent agreeing is not validation. |
| GPT-6.1-Sol (xhigh) | [gpt-6.1-sol-xhigh.md](gpt-6.1-sol-xhigh.md) | An effort limit and stopping rule. Name the assumption most likely to sink the plan, and disprove it cheaply. |
| Grok 4.7 (high) | [grok-4.7-high.md](grok-4.7-high.md) | Every hard target needs a constraint that can veto it. "Where are you fluent but wrong?" Keep the artifact when it *is* the point. |
| Fable 5.1 (high) | [fable-5.1-high.md](fable-5.1-high.md) | Pick one primary axis. Put the judge before the target. "If it should stay small, say so and stop." |
| Muse Wonder Full (max) | [muse-wonder-full-max.md](muse-wonder-full-max.md) | "Belief is lent to the search, not to the conclusion." What to do when no judge exists. |
| Opus 5.5 (high) | [opus-5.5-high.md](opus-5.5-high.md) | Ambition is capped by the best check the agent can run, so missing access is part of the work. "An honest miss beats a faked hit." |

---

## The prompt

### Full version (for any task worth more than a few minutes)

```
Before you start building, help me be more ambitious about this task: aim at the real outcome and go deeper, not just bigger. Don't start the work yet.

Look at what's actually here first (code, data, logs, tools) so your answers rest on evidence. Don't interview me: state your assumptions, and ask only what would change your recommendation. A few lines each:

1. Outcome: What do I actually want to happen after this? Is there a version that gets there more directly, or stops this task from coming back? If the thing I named is itself the point, say so and keep it.
2. Method: What would the best practitioner do here that I didn't ask for? What raw material would they start from instead of the digested version, which real tools would they run, and which of my assumptions would they test against it? If the material can't support the method, say so. New vocabulary is not a new method.
3. Other fields: Describe the task as verbs. Which one or two methods from other fields would change the result? Methods, not personas or role-play.
4. Judge: What, other than you or me, will show it's right: a test, benchmark, reproduction, holdout, or real user? Another agent agreeing doesn't count. If none exists, building one is step one. If none can exist, name the closest proxy and what stays unverified.
5. Target: Set one specific goal harder than mine and treat it as reachable, plus the constraint allowed to veto it. If there's no known method yet, finding one is the first goal.
6. Gaps: What access, data, or tools are missing? Install what you can and flag what you can't. Where are you likely to be fluent but wrong?

Then recommend one version. Change at most two things (outcome, method, borrowed technique) and keep the rest at the scale I asked for. In one line, name the boldest option you rejected and why. If my task is already the right size, say so and stop. Give the cost (time, my review load, upkeep, anyone else's sign-off), the assumption most likely to sink it, and the cheapest probe that would prove or kill it.

Then rewrite my task as one self-contained prompt that asks for exactly this. Include my constraints, the raw material, methods, judge, target and veto, an effort limit with a rule for when to stop or fall back, and the first checkpoint I'll review. Use parallel agents only for truly independent work, such as an adversarial check. Include this rule: push past the first "impossible", never shrink scope silently, and report the real measured result. An honest miss beats a faked hit. Wait for my go-ahead before executing.

My task (and any fixed constraints): [describe it here]
```

### Compact version (for when you'd skip the full one)

```
Before you start, help me be more ambitious about this task: deeper, not bigger. Look at the actual material first; don't start the work. Briefly: What outcome am I really after, and is there a more direct version? What would the best practitioner do here, from what raw material, with what real tools? Is there one method from another field that would change the result? What, other than you or me, will prove it's right? Set one harder target and the constraint that can veto it. Recommend one version, or tell me mine is already the right size, with its cost and the cheapest probe that would kill it. Then rewrite my task as a prompt with the judge, target and first checkpoint built in, and wait for my go-ahead. Never shrink scope silently. An honest miss beats a faked hit.

My task: [describe it here]
```

---

## How I got there

### 1. What all six agreed on (the core)

The essay gives these points one bullet or less, or leaves them out entirely. Even so, all six models independently made them central. That convergence is the strongest signal in the whole exercise:

- **The outside judge carries the whole thing.** The essay files "use an outside judge" as a fifth bullet under Depth. Every model promoted it to a required gate. The reason: "tell the model the goal is reasonable" is only safe if something other than the model can say no. Without a judge, more ambition just produces more confident reports of unmeasured success. (Fable: "ambition and verification are a pair". Muse: "the load-bearing wall". Grok: "no judge, no ambitious version".)
- **Deeper, not bigger.** Real ambition changes the outcome, or how confident you can be in it. Inflation adds surface: more deliverables, more agents, more pages. Several models noted that depth often makes the output *smaller*: one validated finding instead of twelve charts.
- **Methods, not role-play.** "Act like a statistician" changes the vocabulary. "Use a database and a survival model" changes the method. All six banned personas.
- **The real cost is your review attention, not compute.** The essay treats ambition as free upside. Five of six models named review load, upkeep and authority (who has standing to approve the bigger version) as the hidden bill.
- **"Stay small" has to be an allowed answer.** Without that escape, the prompt is only safe on tasks you already suspect are big, and you can't know that in advance. With it, you can paste it every time.
- **Propose, then wait.** The go-ahead isn't bureaucracy. Grok and Fable both argued it's where *your* self-efficacy actually updates: you see the larger version concretely and choose it, rather than nodding along.

### 2. The best unique contributions (what I added on top)

| Idea | From | Why it made the cut |
|---|---|---|
| Look at the actual material before answering | Opus, Muse, Astra | Answers grounded in evidence beat confident brainstorming. The agent can read the repo, so it should. |
| "If the thing I named is itself the point, keep it" | Grok (substitutability test), Astra | Most tickets *are* the artifact. Altitude that climbs past them abandons the thing someone is waiting on. |
| "If the material can't support the method, say so" | Grok | The inverse failure of persona prompting: once you reward real instruments, agents fit fancy models to 40 rows. Real experts sometimes refuse the fancy tool. |
| "Another agent agreeing doesn't count" | Astra, Sol | You have multi-agent orchestration, so a second model's agreement is the cheapest fake judge available to you. |
| No judge possible → closest proxy plus a label for what's unverified | Muse | Covers writing, strategy and design, where the essay's best rule is hardest to follow. |
| A veto constraint on the hard target | Grok | Unreasonable targets select for damage: the cache that breaks correctness, the test that asserts a mock. Naming a constraint that can veto the target stops the number being hit by breaking something else. |
| "If there's no known method yet, finding one is the first goal" | Grok, citing Winters & Latham | A real limit in the goal-setting research the essay cites. On complex tasks, a hard *outcome* goal before you have a strategy makes performance worse, and a *learning* goal works better. |
| Gaps: install what you can | Opus | The essay's buried lede. The crash-free story only worked after the plumbing. Ambition is capped by the best check the agent can run. |
| "Where are you likely to be fluent but wrong?" | Grok | Turns Tao's "jagged frontier" line, which the essay quotes but never acts on, into something the agent has to answer. |
| Change at most two things | Grok (cap at two), Fable (one primary axis) | Applying altitude, depth and range all at once is how a two-hour job becomes a research program. |
| Assumption most likely to sink it, plus cheapest probe | Sol, Muse ("brake"), Opus | Big goals become safe to approve when there's a cheap way to kill them early. |
| Effort limit and stop-or-fall-back rule | Sol | The essay points at Collison's "Fast" list (audacity *plus* deadline) but its techniques have no clock. |
| Honesty rule written into the executed prompt | Opus, Grok | This is "permission to fail" applied to the model. Persistence alone invites faked results. Persistence plus honest measurement doesn't. |
| "(and any fixed constraints)" in the task slot | Muse | A cheap way to get the veto constraints and the "this artifact is mandated" facts in up front. |

### 3. Where the models disagreed, and how I resolved it

- **Menu or single proposal?** Astra and Sol asked for up to three options. Opus argued explicitly against menus ("decision paralysis or skimming"). Fable and Grok cap the number of axes instead. **Resolution:** recommend *one*, but name the boldest rejected option in one line. That keeps what Astra and Sol were after ("a leap I might dismiss too soon"), the Bannister effect of *seeing* the bigger version, without making you choose from a menu.
- **Ask questions or not?** Grok said "do not interview me". Astra and Sol said "ask only questions that would change your recommendation". **Resolution:** both. State assumptions by default, and ask only when the answer changes the recommendation.
- **Name the four types?** Muse used Altitude/Depth/Range as headers. Opus, Fable and Grok deliberately didn't ("labels invite filling in a taxonomy; plain questions get plain answers"). **Resolution:** plain labels (Outcome / Method / Other fields), which map to the essay's types without inviting a taxonomy.
- **Length.** Sol's prompt is about 190 words and Grok's about 420. Brevity matters (a prompt you skip is worth nothing), but each model's extra sentences were each closing off a specific way of faking it. **Resolution:** two versions. The full one is about 420 words; each line traces to at least one model and guards against a named failure. The compact one (about 150 words) keeps the core: outcome, method, other field, judge, target plus veto, stay-small, probe, honesty rule.

### 4. What I deliberately left out

- **The self-efficacy anecdotes and any pep talk.** Grok's point convinced me: in Bandura's terms, persuasion is the weakest of the four sources of self-efficacy, and a model has no mastery or nerves to build on anyway. "This is reasonable" works on a model only as a ban on giving up early. The prompt keeps that ban ("push past the first impossible") and drops the inspiration.
- **Speed.** Every model dropped it. It's already the default.
- **Crews and the heist-movie framing.** Fun, but you can spawn threads cheaply, which makes "assemble the crew" the path of least resistance. Parallel agents appear only for truly independent work.
- **Mandatory durable automation or "produce new knowledge" as a standing order.** Both are great when the task is recurring or data-rich. As defaults on every task they're altitude-as-habit (Grok). The Outcome question ("stops this task from coming back") leaves room for them when they fit.
- **Muse's structured output format** (one-line task, rewrite, five bullets). Good, but it adds length, and the rewrite is the deliverable anyway.

### 5. Observations about the models themselves

- **Family resemblance is real.** The two GPT models wrote the most compact, measured prompts with near-identical structure (a menu of options, then a recommendation, then a disproof experiment). Opus and Fable both used six numbered questions and both added cost and authority. Grok went deepest on research (Locke & Latham's limits, Winters & Latham, Bandura's four sources) and wrote the longest reflection, about 5k words. Muse was the most essayistic and had the best one-liners: "belief is lent to the search, not to the conclusion", and "depth is scale-free; inflation is not".
- **Everyone attacked the same weak spot.** Every model found the same gap in the essay: "tell the model it's reasonable" without measurement invites fake success. Six independent readings converging on one critique is a good sign the critique is right.
- **Opus read the local plain-text copy instead of fetching the live URL.** The content was identical (same day, same text). The other five either fetched the URL or didn't say which they used.
