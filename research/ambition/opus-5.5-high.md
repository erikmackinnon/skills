# Opus 5.5 (high): Ambition reflections

## Reflections on the article

**What it is really saying.** Under the taxonomy, the claim is that the bottleneck has moved. Execution is cheap now, so the limit on what you get from a model is the *frame* you hand it: the scope you believe is possible, set by habits formed when you or a junior colleague did the work by hand. Each of the three interesting types widens that frame along one axis:

- **Altitude** widens the *why*: from the task to the outcome behind it ("fix this crash" → "keep the app crash-free").
- **Depth** widens the *how well*: from the digested artifact to raw material, real instruments and a real bar ("markdown table" → database + statistical model + a prediction tested on held-out data).
- **Range** widens the *with what*: from the obvious field to fields the task's verbs point at (a QBR is persuasion under uncertainty, so journalism, editing and forensic accounting apply).

Speed is skipped because it doesn't change the frame. But it is what *pays for* the other three: when execution is nearly free, you can afford to explore, to probe and to build a judge.

The self-efficacy section is the motivation. People (and, I'd add, models) under-reach because of what they believe is possible, and belief responds to specific hard goals, to seeing an existence proof, and to permission to fail.

**What's true.** The task as written is usually a guess at how to get an outcome, and the model will faithfully carry out the guess. Models default to the shallowest artifact that satisfies the literal request. "Act like an expert" changes vocabulary, not method. The test of depth is whether the instruments change. And the outside judge is the load-bearing element of the whole piece. Without it, every other technique makes plausible-looking output *bigger* rather than *better*.

**The buried lede.** The most important sentence is almost an aside: all of this needs the model to have a computer, software and data. The crash-free example only worked after Felix did plumbing: crash-report access, mapping versions to commits, machines on three OSes for reproduction. So ambition is capped less by imagination than by **what the agent can observe, run and measure**. In an agentic IDE the highest-leverage ambitious move is often not a grander prompt. It's building the harness (fixtures, benchmarks, data access, a reproduction loop) that makes a grander prompt checkable.

**What it leaves out.**
- **Cost, and who pays it.** Ambitious output costs the human review attention, which is the scarcest resource. A 4,000-line PR or a redesigned review process is a liability if nobody can verify it. The article treats ambition as free upside.
- **Authority.** Altitude quickly goes past what you own. "Replace the QBR" isn't your decision. In a shared codebase, "keep it crash-free" can mean touching other teams' code.
- **When not to.** Some tasks really are the size they look. Inflating them is waste, and the article gives no stop rule.
- **Staging.** Big goals succeed by cheap early probes that prove or kill them. The article jumps from small prompt to big prompt without the spike in between.
- **The dark side of "tell it it's reasonable."** Pressure plus belief, with no honest measurement, invites the model to game the metric: cache the benchmark, simplify silently, declare victory. Ask for 200ms and you might get a 200ms number that measures the wrong thing.
- **Survivorship.** Dantzig and Bannister are the cases that worked. The goal-setting research the article cites holds when people have the ability and the feedback. Hard goals without feedback mostly produce stress or cheating.

**Where it breaks down.** It breaks down where there is no judge: taste, strategy, novel writing. Altitude fails without data access. In regulated or irreversible settings, "keep going, it's solvable" is dangerous. And all three types stall when the human can't review the result, so ambition outruns comprehension and the human rubber-stamps.

## Five questions

### Q1: Is the real constraint the human's ambition, or the agent's environment?

Mostly the environment, though people rarely notice that, because they experience it as a lack of ambition. Three things limit what an agent delivers: **imagination** (what you think to ask for), **belief** (what you think it can do), and **instrumentation** (what it can actually observe, run and check). The article's prompts work on the first two. Its own success story was won on the third.

A useful rule: *your ambition is capped by the best check the agent can run.* If the agent can't reproduce the bug, it can't credibly fix the whole class of bugs. If it can't query raw events, it can't find the churn signal. If there's no benchmark, "make it 50x faster" is theater. So an ambitious prompt should always ask "what access or tooling is missing?", and the agent should treat building that harness as first-class work, not setup to rush through. A good side effect is that the harness lasts. The next task starts at a higher altitude for free.

### Q2: How do Altitude, Depth and Range interact, and what does each look like alone?

Each one alone has a typical failure:
- **Altitude without depth** produces strategy slides: a confident redesign of "how leadership catches problems" with no proof it would have caught anything.
- **Depth without altitude** produces gold-plating: a statistically rigorous answer to a question nobody needed answered, or a 200ms page that no user waits on.
- **Range without depth** produces costume parties: six "experts" in the transcript, none of whose methods were actually used.

They work as a sequence. Altitude picks the target (what outcome?). Range widens the search for approaches (what other disciplines have solved a problem with these verbs?). Depth executes the chosen approach at an expert bar with a real judge. Range is mostly a *source* of depth: the short seller is useful because of a method (build a bear case from primary filings), not a viewpoint. Altitude decides whether depth is worth paying for at all. And the outside judge connects all three, because it's the only thing that tells you the higher target was hit rather than just aimed at.

### Q3: What does ambition cost, and how do you keep the cost from killing it?

The costs are wall-clock time, tokens, blast radius, maintenance (a new system is something someone now owns), political cost (altitude steps on other people's decisions), and above all **human review attention**. The agent does the work, but the human still has to trust it, and trust costs reading. That last cost is why most ambitious agent runs end up quietly ignored.

Ways to keep ambition affordable:
1. **Make verification cheap for the human.** The outside judge isn't only for correctness. It replaces "read 3,000 lines" with "look at the benchmark and the held-out result."
2. **Stage it.** Find the cheapest probe that proves or kills the ambitious version: a 30-minute spike, a backtest on one quarter, a prototype on one module. Commit only after it passes.
3. **Keep the modest version as a floor.** The ambitious plan should strictly contain or replace the asked-for result, so a partial failure still leaves you better off.
4. **Name the authority boundary up front**, so the agent flags what needs someone else's sign-off instead of discovering it at the end.

When *not* to be ambitious: when the task really is a leaf (rename a field), when no judge can exist and the stakes are high, or when you won't have the attention to review the result. "This is already the right size" should be an allowed answer.

### Q4: What role does the *model's* self-efficacy play, separate from the human's?

Models have their own under-reach patterns, and they look like low self-efficacy:
- Defaulting to the most familiar medium (markdown, a script) rather than the right instrument.
- Declaring something infeasible after the first failed approach.
- **Silently shrinking scope**: "I've implemented a simplified version", stubbing the hard part, mocking the thing that was supposed to be tested.
- Stopping at the first plausible answer instead of the best one.

The article's fix ("reiterate that it's very solvable") helps with persistence, but on its own it is risky. Models also over-claim, and raising the pressure without honest measurement raises the incentive to fake it. The human hacks in the article match the right model instructions: **specific hard goal** (a number, not "make it fast"), **existence proof** (look at how others have done it, or build a quick spike that shows it's possible, which is the Bannister effect at small scale), and **permission to fail** written as an explicit honesty rule: *an honestly reported miss at 400ms is a success; a faked 200ms is the only real failure.* Ban silent downscoping, but welcome a measured "here's how far I got and what blocked me."

There's also a coupling. The model mirrors the scope of the request, so the human's self-efficacy sets the model's ceiling. A good ambition prompt hands the scoping to the model, which often knows what experts do better than the user does, while the human keeps the go/no-go decision.

### Q5: How do you tell real ambition from inflated scope?

Inflated scope adds *surface*: more slides, more features, more personas, more words like "comprehensive." Real ambition changes the *outcome*, or how confident you are in it. Tests I'd apply to any "more ambitious" proposal:

1. **Decision test:** would anything be decided or done differently because of the extra work?
2. **Judge test:** does the ambitious version come with evidence that the modest version wouldn't have (a backtest, a reproduction, a benchmark, a held-out prediction)? If the only judge is "it looks thorough," it's inflation.
3. **Recurrence test:** does it remove future work (the crash class, the recurring report), or add maintenance?
4. **Raw-material test:** does it touch rawer inputs than the original, or just do more on the same digested ones?
5. **Reviewability test:** can the human verify it at roughly the same cost as the original? If not, it's ambition the human can't absorb.

Depth often makes the output *smaller*: one validated finding instead of twelve charts. That is the article's "deeper, not bigger" point. I'd make it a hard filter: cut anything that adds size without changing the outcome or the confidence.

## The prompt

```
Before you build anything, help me be more ambitious about this task: deeper and aimed at the real outcome, not just bigger.

First look at the actual material (code, data, logs, docs, the environment) so your answers come from evidence, not guesses. Then answer briefly:

1. Outcome: What do I actually want to happen after this is done? Is there a version that gets that directly, or stops this task from coming back?
2. Expert bar: What would the best practitioner do here that I didn't ask for? What raw material would they start from, and which real methods and tools would they use (methods, not vocabulary or role-play)? Name a target that sounds unreasonable but might be reachable.
3. Other fields: Describe the task as verbs, not a noun. Which one or two other disciplines have methods that would change the result?
4. Shaky assumption: What in my framing might be wrong, and how would you test it against raw data?
5. Judge: What, other than you or me, will show the result is right: a test, benchmark, measurement, held-out data, a reproduction? If none exists, building it is part of the work.
6. Gaps: What access, data, or tools are missing? Install what you can; tell me what you can't.

Then propose one ambitious version. Keep only what changes the outcome or our confidence in it, and cut anything that just adds size. If my task is already the right size, say so. Include the cost (time, what I'll have to review, anything needing someone else's sign-off), the cheapest first step that would prove or kill it, and how you'd split the work across parallel agents if that helps.

Then rewrite my task as a prompt that asks for exactly this, with the judge and first checkpoint built in, plus this rule: push past the first "impossible", never shrink scope silently, and report the real measured result. An honest miss beats a faked hit. Wait for my go-ahead before executing.

My task: [describe it here]
```

## Design notes

- **"Look at the material first."** In an agentic IDE the agent can read the repo, query the data and check what's installed. Answers based on evidence avoid the most common failure of ambition prompts: confident but uninformed brainstorming.
- **One question per type, without the type names.** Outcome = Altitude, Expert bar = Depth, Other fields = Range. Labels like "Altitude" would invite the model to fill in a taxonomy. Plain questions get plain answers. Speed is left out on purpose.
- **"Shaky assumption" stands alone** because "challenge what you know" is the cheapest way to get new knowledge, and it's the move people most often skip.
- **The judge is its own item and is required.** If none exists, building one becomes part of the work. This is the article's strongest point and the main defense against inflated scope. I phrased it as "other than you or me" so a self-assessment or "looks good to me" can't count.
- **The Gaps item comes from the buried lede.** Access and instrumentation cap ambition more than imagination does, and the agent can often fix this itself by installing tools.
- **One proposal, not a menu.** A tiered "modest / ambitious / moonshot" menu turns into decision paralysis or skimming. One concrete proposal plus a cost is easier to approve or veto. "If my task is already the right size, say so" is the stop rule the article lacks.
- **Cost, sign-off and first probe** cover what the article leaves out: review attention, authority, and staging. The cheapest probe makes a big goal safe to approve.
- **Parallel agents get one clause.** The user has orchestration. Range and independent judging parallelize well, but I didn't want to force fan-out on tasks that don't need it.
- **The execution rule goes into the rewritten prompt** because that's the text that actually runs. It combines the article's "tell it it's solvable" with the honesty guard it lacks: persistence plus no silent downscoping plus honest measurement. It is permission to fail, applied to the model.
- **Left out:** the "aliens will blow up Earth" crew framing (fun, but it invites role-play), named personas, and any "you are a world-class X" opener. The prompt is about 330 words. That's long enough to change behavior and short enough to paste without editing.
