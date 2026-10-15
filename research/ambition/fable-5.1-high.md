# Fable 5.1 (high): Ambition reflections

## Reflections on the article

Beneath the four types, the essay makes one claim: the binding constraint on what people get from models is no longer the model, it is the shape of the request. Every task shape we own (the deck, the bug fix, the crash report) was moulded by what a human could afford to do before models existed. Models changed the cost structure, but we keep ordering from the old menu. A prompt, as Felix puts it, is "your best guess at how to get the outcome you want", and that guess is anchored in pre-AI economics.

Read this way, three of the four types are three different things that used to be uneconomical:

- **Altitude** is pursuing the goal behind the goal. It was too expensive to chase outcomes, so we decomposed work into tasks and handed over tasks.
- **Depth** is applying the expert's full method to a routine job. It was too expensive to run a statistician's workflow on a quarterly deck, so we used digested numbers and heuristics.
- **Range** is consulting many fields. It was too expensive to hire a forensic accountant for a slide, so we stayed in the one field the task nominally lives in.

Speed is the odd one out and he skips it for a reason: it is the only type that leaves the task's shape unchanged. It is ambition-neutral.

Two things in the essay are load-bearing but under-emphasised. The first is **"use an outside judge"**, filed as the fifth bullet under Depth. It is actually what makes every other technique safe. "Pick unreasonable goals and tell the model they're reasonable" is good advice only if failure is detectable by something other than the model's own report. Without a judge, ambition degrades into confident prose about work that was not done. The essay's own flagship example, keeping apps crash-free, only works because the model has machines on which to reproduce and verify. Ambition and verification are a pair, and the judge should be chosen before the ambitious goal, not after.

The second is **infrastructure precedes ambition**. The crash-free workflow needed crash report access, version-to-commit mapping, and three operating systems before the ambitious prompt could mean anything. Most "we're not ambitious enough" exhortations skip the plumbing. For someone in an agentic IDE this is the encouraging part: the plumbing largely exists, so the remaining gap really is the request.

The essay also contains a quiet symmetry it never names. The self-efficacy section is addressed to humans, but half the Depth techniques are about the model's self-efficacy: "does something seem impossible to the model? Reiterate that it's solvable." Both parties under-ask. The model does the plausible median thing, the human accepts it, and the equilibrium is stable because neither side is embarrassed.

What is true: the anchoring is real and observable. "Vocabulary without methods" is a precise diagnosis of why persona prompting disappoints. Specific hard goals outperforming "do your best" is among the best-replicated findings in organisational psychology. Models do grade their own work badly.

What it leaves out: cost, authority, and selection. Cost, because ambition is not free and tokens are the cheap part; the expensive part is the human's time to review an output they did not watch being made. Authority, because altitude presumes you own the outcome. The person asked to make the QBR deck may have no standing to replace the QBR. Selection, because "every day I learn of another feat" is survivorship. We do not see the ambitious runs that produced three hours of plausible garbage.

Where it would break down: in domains with no runnable judge (strategy, taste, prose quality), where "depth" has no instrument to insist on; where the human lacks the knowledge to tell whether the "expert method" the model proposed is real; where actions are irreversible and altitude means the agent decides things it should not; and where all three types are applied to one task at once, which is how a two-hour job becomes a sprawling project nobody asked for.

## Five questions

### Q1: Why does ambition have to be prompted at all? Why doesn't a capable model propose the ambitious version on its own?

Because the model is trained to do what was asked, and the phrasing of the request is its strongest signal of intended scope. A model that unilaterally replaces "fix this crash" with "redesign your crash pipeline" is, most of the time, being annoying rather than ambitious. It also does not know what the human has authority over, how much time they have, or what they have already tried. So the ambitious version cannot be imposed by the model; it has to be a negotiated reframe. That is why the useful move is a two-step: the model proposes the more ambitious shape, the human approves or trims it, and only then does execution start. The approval step is not bureaucracy. It is where the human's self-efficacy gets updated, because they see a concrete bigger version before committing to it, which is a smaller, cheaper version of the Bannister effect.

### Q2: How do the three real types interact, and should you pursue more than one on a single task?

They operate on different objects. Altitude changes the question. Depth changes the method used to answer it. Range changes the set of methods you consider. That ordering matters: altitude first, because until you know what the task actually is, there is nothing to go deep on. Range is then best understood as a search procedure for depth. You ask which fields have a method that fits, then you go deep in one or two of them. It is not a reason to add six workstreams.

Pursuing all three at full strength on one task is how scope explodes. A practical rule: one dominant axis per task, chosen by the task's shape. If there will be meetings about the output, go for altitude. If an answer already exists but is mediocre, go for depth. If you are stuck or the framing feels stale, go for range. Speed is the dividend you reinvest in whichever axis you chose. Multi-agent orchestration earns its keep only on the range axis, and only when each sub-thread runs a genuinely independent method with its own check. Parallel threads that chat about the same thing are a committee, not a crew.

### Q3: What does ambition cost, and who pays?

Compute is the visible cost and the smallest one. The real costs land on the human at review time. An ambitious run produces an output the human did not watch being made, built with methods they may not know, against a target they did not set. Verifying that is slower than verifying a small, familiar change. There is also opportunity cost (a three-hour autonomous run that went wrong at minute ten), correctness risk (confident wrong answers are more dangerous than hedged ones), and social cost (an altitude reframe you lacked the standing to make).

So the honest budget for an ambitious task is review time, not run time. Two things follow. Ambition should be bounded by what you can verify, which means the judge sets the ceiling. And investment in judges and infrastructure is what makes future ambition cheap: once crash reproduction is automatic, "keep the app crash-free" costs almost nothing to review. The essay's advice is really advice for someone who has already paid the setup cost. Someone who has not should spend their first ambitious act building the judge.

### Q4: Whose self-efficacy is the bottleneck, the human's or the model's?

They govern different things. The human's self-efficacy determines what gets asked. The model's determines whether it persists or hedges once asked. Models show something that behaves like low self-efficacy: they produce the median output, declare things out of scope, and write "this would require..." and stop. The reason "tell it the goal is reasonable" works is that the model's estimate of difficulty is a prior, not a measurement, and the prior is conservative.

But hacking the model's self-efficacy is dangerous in a way hacking the human's is not. A human who believes harder runs the mile and either breaks four minutes or does not. A model told to believe harder will, without a judge, report that it broke four minutes. So the model's side of the technique must be paired with external verification or it becomes a confabulation generator.

For a user in an agentic IDE, the human's side is the bottleneck. The agents already have the computer, the shell, and the sub-threads. The missing ingredient is the user seeing, before they commit, what the larger version of their request would look like. The best prompt therefore works mainly on the human, by making the model show them the ambitious version rather than telling them to be ambitious.

### Q5: How do you tell real ambition from inflated scope?

Real ambition changes the quality of the answer or the nature of the question. Inflated scope changes the quantity of work. Some tests that separate them:

- **Compression.** Real altitude usually makes the request shorter. "Keep the app crash-free" is fewer words than a list of crashes. Inflation adds bullets.
- **Subtraction.** Real ambition usually drops the default artefact. The markdown table goes away and a database appears. The deck becomes a monitoring loop. Inflation keeps the old deliverable and adds more.
- **Nameable method.** Real depth names a technique a practitioner would recognise (a survival model, a differential test, a bisection against production traces). Inflation says "comprehensive" and "thorough".
- **Rawer input.** Real depth reaches past the digested summary to logs, traces, raw data. Inflation works from the same input and produces more output.
- **Judge outside the loop.** Real ambition can say what, other than the model, shows it worked. Inflation's judge is the model's own summary.
- **Hard target, crisply checkable.** "200ms" is ambition. "Much faster" is inflation.

A sufficient red flag is a proposal with more deliverables, more agents, and more pages, but no new method, no new raw material, and no external judge. That is bigness wearing ambition's clothes.

## The prompt

```
Before you start, help me be more ambitious about this task. Answer briefly, a few lines per point, then stop and wait.

1. Outcome. What am I really trying to make happen, one level above this task? If there is a version that makes this task unnecessary next time (a check that runs on its own, a tool, a workflow), name it and the access or setup it would need.
2. Expert method. What would the best practitioner in this field do here that I haven't asked for? What raw material would they start from instead of what has already been digested for me? Name the specific tools and methods you would actually install and run. New vocabulary is not a new method.
3. Other fields. Which two or three fields have a method that fits this problem? Describe the method, not the person. No role-play. Use parallel sub-threads only to run such methods independently, each with its own check.
4. Judge. What, other than you or me, would show the result is right? Prefer something runnable that gives you fast feedback. If no judge exists, building one is step one.
5. Target. Set a specific goal harder than what I asked and treat it as achievable. Say what you would drop to make room for it.
6. My cost. What does this add to run time, and to what I will have to review? Flag anything that goes beyond what I have the standing to decide.

Pick one axis as primary (outcome, method, or fields) and say why in one line. If the honest answer is that this task should stay small, say so and stop. Otherwise rewrite my task as a prompt that asks for exactly this, judge and target included. Deeper, not bigger: better method and rawer input, not more deliverables. Wait for my go-ahead before executing.

My task: [describe it here]
```

## Design notes

**Six questions, then a rewrite.** The structure mirrors the essay's own Depth prompt because that shape works: make the model surface the ambitious version before anyone commits. The six items map to the article's three real types (outcome = altitude, method = depth, fields = range) plus the three things the article treats as supporting detail but I treat as structural: the judge, the hard target, and the cost.

**The judge comes before the target.** This is the one ordering I feel strongly about. A hard target without an external check is an invitation to confabulate. Placing the judge at item 4 and the target at item 5, and insisting the rewrite include both, makes "unreasonable goal" safe to use.

**"Pick one axis."** This is my Q2 answer built into the prompt. Without it, a conscientious model proposes altitude and depth and range at once, and the user gets a sprawling plan they skip. Forcing a primary axis keeps the proposal shaped like a task rather than a programme.

**"Say so and stop."** Real ambition includes knowing when a task should stay small. A hotfix at 2am does not need its QBR redesigned. The release valve also makes the prompt safe to paste on every task rather than only the ones the user already suspects are big, which is the point: the user cannot know in advance which tasks have an ambitious version.

**"My cost" and "standing."** The article leaves out review burden and authority. Item 6 puts both in. It asks the model to say what the user will have to check and to flag reframes the user may not be able to approve. This is the item most likely to prevent an ambitious run from becoming a regretted one.

**Warnings folded in rather than listed.** "No role-play", "describe the method, not the person", "new vocabulary is not a new method", and "deeper, not bigger" are each one clause attached to the item they guard. A separate warnings section would be skipped.

**Multi-agent gets one sentence.** The user has orchestration, so the prompt says where it belongs: independent methods with independent checks, on the range axis. Anything more would encourage spawning for its own sake.

**Left out:** the self-efficacy anecdotes, Speed, and any instruction to "act like" anything. Also left out is any instruction to produce a plan or timeline, because that is where proposals bloat. The deliverable of this prompt is a rewritten task, not a document.

**Length.** About 270 words. Longer than the article's own Depth prompt because it covers all three types and the agentic context, but short enough to paste without thinking. If the user wants to trim, item 3 is the first to cut on single-field tasks, and item 1 on tasks whose outcome is already fixed.
