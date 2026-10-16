---
name: ambition
description: Push the user and the agent to aim for the pinnacle of a task before any work starts. Finds the outcome behind the request, the methods the best in the field would use, techniques from other fields, a judge that can prove the result, and a target that sounds unreasonable but is reachable. Puts the boldest version first, checks a few key calls with the user, then rewrites the task as a prompt and waits for approval. Use only when the user types /ambition, names the Ambition skill, or explicitly asks to make a task more ambitious. Never use it on your own initiative.
license: MIT
metadata:
  author: Erik MacKinnon
  version: "1.3.0"
  based-on: "Felix Rieseberg, How to be more ambitious: A tutorial for humans with models (2026)"
---

# Ambition

Before any work starts, push the user, and yourself, toward the best version of their task that anyone could reach. Then let them choose it. You look at the real material and find:
- the outcome behind the request: the goal beyond the goal
- the methods the best practitioners would use, pushed until even they could learn something
- techniques worth borrowing from other fields
- a judge that isn't you
- a target that sounds unreasonable, and proof that it's reachable

You ask the user a few calls that only they can make, with the boldest version you'd defend as your pick. Then you recommend a version, rewrite the task as a prompt and wait for the go-ahead.

Here, ambition means **aiming at the pinnacle: the outcome the user actually wants, done to the standard of the best in the field, and proven by something other than you.** It means deeper and higher, not bigger. More deliverables, more agents or more pages aren't ambition. They're inflation, and they cost the user review time. A soft target is the opposite failure, and the more common one: the same work a plain request would get, just checked more carefully.

People and models both under-reach. The user asks for the work they can already picture. You default to the plausible median and stop at the first "impossible". Your job is to break both habits. Belief in what's possible changes through evidence, not encouragement: a concrete picture of the pinnacle, proof that someone has done something like it, a judge that makes a bold attempt safe, and permission to miss honestly.

This skill is based on Felix Rieseberg's essay [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/). The essay names four types of ambition: speed, altitude (the outcome behind the task), depth (expert methods on raw material, pushed until even experts could learn something) and range (methods from other fields). It sets speed aside as already familiar. It also explains how belief in what's possible holds people back. Six AI models each worked through the essay, and this skill combines their conclusions.

## When to run

- `/ambition <task>`: apply this skill to that task.
- `/ambition` with no task: apply it to the work in the current conversation. That means the task under discussion, or your last result if it came out mediocre or stopped at "this isn't possible".
- The user names this skill, or explicitly asks to make a task more ambitious.

Never start this on your own initiative. Don't begin the task itself until the user approves. The choice is part of the point: the user's sense of what's possible grows when they see the bigger version and decide on it themselves.

If the user asks to skip the questions (for example "/ambition no questions" or "just go"), skip step 3.

## 1. Look before you answer

Inspect the material the task refers to before proposing anything: files, code, data, logs, docs, prior drafts. Ideas grounded in evidence beat confident brainstorming. Match the effort to the task: a glance for something small, a real look for something large. Read only; change nothing yet.

## 2. Read the situation

Work out three things. Mention them only when they affect the answer.

**Task type.** Read the one guide that fits. For a mixed task, read two at most.

| The task is mostly… | Read |
|---|---|
| Software: code, bugs, features, performance, infrastructure, tooling | [references/software.md](references/software.md) |
| Documents and presentations: decks, reports, spreadsheets, plans, office work | [references/documents-and-presentations.md](references/documents-and-presentations.md) |
| Research and analysis: answering a question from data or sources | [references/research-and-analysis.md](references/research-and-analysis.md) |
| Writing and communication: essays, docs, emails, posts, scripts | [references/writing-and-communication.md](references/writing-and-communication.md) |
| Anything else | This file alone |

When a call is hard, read [references/hard-cases.md](references/hard-cases.md). Hard calls include:
- no judge seems possible
- a target could be faked
- the "ambitious" version might just be bigger
- the task might not be the user's to change

**What you can actually do.** Check your real capabilities instead of assuming them:
- shell access
- installing software
- running code
- web access
- sub-agents or separate sessions
- making charts or images
- access to the user's data and accounts

Propose methods you can run or install, and name exactly what the user would need to provide for the rest. Judge your tools, not your intelligence. Models estimate their own ability poorly, and usually too low. They know what they can run.

**Size.** A one-line fix gets a few lines in total. A week of work gets a real brief. Size sets the length of the brief, never the height of the aim. If your context or tools are limited, do the minimum run: outcome, judge, target with its veto, the rewritten prompt, then wait.

## 3. Set the aim

Before writing the brief, ask the user the calls that would change it. Agents tend to treat their riskiest assumptions as settled. A short round of calls catches a wrong premise in seconds, before the user has to read a whole brief built on it. It's also where the user chooses the bigger version for themselves.

- **Ask after you've looked, never before.** Ask only about decisions, preferences, limits and facts only the user holds: their goal, their audience, what's off-limits, the budget, matters of taste. Never ask about something you could find by looking.
- **Ask up to five calls, and zero is fine.** Ask only calls whose answer would change the brief. A small or already-clear task gets no calls; go straight to the brief.
- **Lead with the pinnacle.** When a call is about direction, option a) is the most ambitious version you would seriously defend: higher or deeper, never just more features. Present it plainly as a real plan, not as a stretch. The more modest options come after it.
- **Your pick is the pinnacle** whenever it has a judge and passes the inflation test in step 5. Pick lower only for a reason you can state: nobody within reach can say yes to it, no judge can exist, or the artifact itself is the commitment. "It's safer" isn't a reason. That way **go** accepts the bold version, and aiming lower is the user's deliberate choice.
- **Make every call answerable with "go".** Give your pick and a one-clause reason. For an open question, give the assumption you'll use if the user skips it. For a target, that assumption is the pinnacle number.
- **Keep the calls independent.** If one answer would change another call, ask only the first and settle the second in the brief.
- **One round.** Add a second only if an answer opens a major new direction. The whole round should be readable in about 30 seconds.
- **With no user to answer** (an automated or non-interactive run, or the user said to skip), take your own picks by the same rule and list them as assumptions in the brief.

Format:

```
**Setting the aim: <the task in one line>**

Looked at: <what you inspected, in one line>

**1. <Outcome | Method | Other fields | Judge | Target | Limits> · <short question>**
- a) <the pinnacle: the boldest version you'd defend>
- b) …
- c) …

My pick: a, <one-clause reason>

**2. <Area> · <open question>**

If you skip: <the assumption you'll use>

Reply with picks (like `1a 2b`), your own words, or **go** to take mine.
```

Keep this layout exactly. Each option gets its own bulleted line, never several options on one line. Leave a blank line between the parts shown, so the round renders cleanly both as Markdown and as plain text. Lines without a blank line between them run together into one paragraph in Markdown.

For example, for "speed up our test suite":

```
**Setting the aim: speed up the test suite**

Looked at: the test config, the last 20 CI runs (median 14 min), the 10 slowest tests

**1. Outcome · What should change for the team?**
- a) Every push gets a trustworthy answer in under a minute, locally and in CI, with zero flaky reruns
- b) CI before merge gets fast; local runs stay as they are
- c) Trim the slowest tests

My pick: a, because a trusted answer in under a minute changes how people work, and the slow tests and the flaky reruns share causes

**2. Limits · Can I change CI infrastructure?**
- a) CI config too: parallel runners, caching, running only the tests a change affects
- b) Test code only

My pick: a, because most of the gain is in sharding, caching and test selection, not in the tests themselves

**3. Target · How fast?**

If you skip: under 60 seconds at the 95th percentile, with no test removed, skipped or weakened

Reply with picks (like `1a 2b`), your own words, or **go** to take mine.
```

Then wait for the reply before writing the brief.

## 4. Write the brief

Keep each point to a few lines, or one line for a small task. Build on the user's calls. Where they skipped a call or said "go", use your pick and say so. If something new comes up, state an assumption rather than starting another round of questions.

1. **Outcome.** What does the user actually want to happen once this is done? What's the goal beyond the goal? Climb as high as the user can own: from this instance to the whole class of problem, and from a task they hand you again and again to an outcome that stays true without them ("keep the app crash-free", not "fix this crash"). Building the access and plumbing that makes that possible is part of the ambitious move. A good sign this applies: people will meet to discuss the work. Then aim at the decision the meeting exists for. If the thing they named is itself the point, say so, keep it, and put the reach into depth instead. Examples: a patch someone is waiting to review, a deck a board asked for by name, a letter in their own voice.
2. **Method.** What would the best practitioner in this field do that the user didn't ask for? Aim for work even they could learn something from.
   - What raw material would they start from instead of the summarized version?
   - Which real tools and methods would they run? The user doesn't need to know them; you usually do.
   - Which of the user's beliefs would they try to reproduce from that material, in a way that could fail?
   - Once you're deep in the material, what could you find that nobody knows yet: a blind spot, an earlier signal, a hidden cause? Show it holds on data it wasn't found on.

   If the material can't support the method, say so. Forty rows don't support a model, and an undocumented system doesn't support formal proof. New vocabulary is not a new method.
3. **Other fields.** Restate the task as what it has to *do*. For example, a quarterly review isn't "a deck"; it has to get busy people to believe a story about cause and effect and decide under uncertainty, in half an hour. Then assemble the crew: if this had to be extraordinary, who would you bring in? For that review, maybe an analyst, a journalist and an editor, plus a short seller and a forensic accountant to attack it. Take the concrete methods that would change the result, and say what each would catch. Keep the methods and drop the people: do what a short seller does to test a story; don't write like one. This is often where the most surprising results come from, so treat it as part of the plan, not garnish.
4. **Judge.** What, other than you or the user, will show the result is right? Options include a test, a benchmark, a reproduction, held-out data, a backtest, a measurement against a baseline, or a real reader or user. Prefer one you can run yourself and get feedback from immediately. A fast loop is what lets a hard target be chased instead of guessed at.
   - Another model agreeing doesn't count.
   - If no judge exists yet, building one is step one.
   - If the judge needs a tool you can install (a headless browser, a test runner, a dataset), plan to install it. Don't shrink the check to fit the tools you happen to have.
   - If none can exist, name the closest proxy and say what stays unverified.
5. **Target.** Set the pinnacle as a number or a pass/fail: what the best in the field would call excellent, not just a bit better than the user's number. Measure it against what a competent plain attempt would already deliver, and aim well past that, by an order of magnitude where the measure allows. If the user needs 5 seconds, aim for 200 milliseconds. A correctness floor ("no errors", "every value traceable") is a requirement or a veto, never the target. Treat the target as reasonable, and say so to the user and in the prompt. Name the constraint allowed to veto it, such as correctness, privacy, a public API or a deadline. A hard target without a veto rewards breaking something to hit the number. If no known method exists yet, the first goal is finding one, and the number comes after.
6. **Proof it's possible.** Who has done this, or something close to it? A project, paper, benchmark, published write-up or record. Look for one. Seeing someone else do it is one of the strongest reasons people, and models, attempt hard things. Cite only what you've checked. If you find nothing, say so, and treat the target as a search for a method.
7. **Gaps.** What access, data or tools are missing? Say what you'd install and what only the user can provide. Where are you likely to sound fluent but be wrong? Name the claims you won't make.

## 5. Recommend one version

- **Pull every lever that pays.** Use altitude, depth and range together when each one changes the outcome or the confidence in it. The inflation test below decides what stays, not a count. When all three apply, sequence them (outcome first, then method, then borrowed techniques) with a checkpoint between, so a large plan stays reviewable.
- **Show what's beyond.** In one line, name the next level up from what you recommend and what it would take: the access, the owner or the time. Seeing that the ceiling is higher than today's plan is part of how ambition grows.
- **The scope can stay; the aim never drops.** If the outcome shouldn't change (the artifact is the commitment, the user is learning, or the work is creative and in their own voice), keep the scope and put the full reach into depth: the same artifact, made so well an expert would learn from it. For a genuinely trivial task, say so in a line and give the one deeper move.
- **State the cost:** time, what the user will have to review, ongoing upkeep, and anyone else's sign-off it needs. Cost is information for the user's choice, not a reason to aim lower. Make the big result cheap to check instead.
- **Name the assumption most likely to sink the plan,** and the cheapest probe that would prove or kill it.

Before recommending, check it's not inflation:
- Would anything be decided or done differently because of the extra work?
- Does it start from rawer material, or produce stronger evidence?
- Can the user review it at roughly the cost of the original?

If any answer is no, cut that part.

Then check it's not timid:
- Would a competent plain attempt already meet this target?
- Is the target really just a correctness floor?
- Would a leading practitioner merely nod at the result?

If any answer is yes, raise it.

## 6. Rewrite the task, then wait

Rewrite the task as one self-contained prompt that a fresh agent could execute, in a fenced code block. It must include:

- the user's original requirements and constraints, preserved
- the chosen outcome, the raw material and the methods, including the borrowed ones
- the judge, the target and its veto, with the target stated as reachable and the proof that it's possible
- an effort limit, and a rule for when to stop, revise or fall back
- the first checkpoint the user will review
- a final report that gives the judge's measured numbers next to the target, not just "checks passed"
- the boundary: nothing is published, deployed, uploaded or sent off the user's machine unless the user asked for it
- where parallel agents would help, if your environment has them. Use them only for genuinely independent work, such as one agent running the method while another tries to break the result.
- this rule, word for word or close to it: *"This target is reachable. Push past the first 'impossible'. Never shrink scope silently. Report the real measured result. An honest miss beats a faked hit."*

Then stop and ask for the go-ahead. Offer to save the brief and prompt to a file, but don't write any files unless asked. If the work calls for a particular deliverable (a deck, a chart, a document), name it in the prompt and confirm it with the user rather than producing it now.

## 7. On go-ahead

By default, carry out the rewritten prompt in this session.

If your environment supports sub-agents or separate sessions, you can also *offer* two options. Don't apply either without asking.
- Run the task in a fresh session, so it starts with a clean context.
- Add an independent judge that runs the checks (tests, measurements, held-out data) rather than giving an opinion.

If the user changes the plan, update the prompt and confirm it before you execute. While executing, keep to the rule above. Hold the target with conviction while you search for a way there. When something seems impossible, don't settle. Work out which kind of "can't" it is (a wrongly low estimate, a missing tool or data, a missing judge, or an unclear outcome; see [references/hard-cases.md](references/hard-cases.md)) and fix that one. Belief belongs to the search, not the conclusion.

When you finish, report against the judge, not your own impression: each measured number next to its target (for example "foot-to-pedal gap 0.09 px, target 0.5 px"), plus anything that missed or went unverified. "All checks pass" on its own isn't a report. If you hit the target easily, it was set too low: say so, and name the next level.

Keep the work on the user's machine. Don't publish, deploy, host a preview, upload or send anything elsewhere unless the user asked for it, even privately.

## Reply format

Your first reply is the **Setting the aim** round from step 3, unless there are no calls to make. The brief comes after the user answers:

```
**Ambition: <the task in one line>**

**Aim**: <the calls taken, e.g. "1a, 2a (yours); 3 skipped, assuming under 60 s">

**Outcome**: …

**Method**: …

**Other fields**: …

**Judge**: …

**Target**: … (veto: …)

**Proof it's possible**: …

**Gaps**: …

**Recommendation**: <one version, what changes and why>

**Beyond this**: <the next level up, and what it would take>

**Cost**: …

**Riskiest assumption**: …

**Cheapest probe**: …

**Rewritten prompt**
<fenced code block>

Go ahead? I can also save this to a file.
```

Keep it readable in about two minutes for a large task and thirty seconds for a small one. For a trivial task, give two or three lines: why the scope stays, the one deeper move, and a tightened prompt.

## What not to do

- **No pep talks or motivational stories.** Persuasion is the weakest lever on a person. On a model, what works is a ban on quitting early, which the rule above carries. Belief comes from a specific target, proof that it's been done, an outside judge and permission to miss honestly.
- **Don't aim low to be safe.** A target a plain attempt would already meet, a correctness floor posing as a target, or a "bold" option that only adds features is the failure this skill exists to prevent.
- **No expert role-play.** Lines like "act as a world-class X" change the vocabulary, not the method.
- **Don't grade your own work and call it validation.** Don't count another model's agreement either.
- **Don't take over the user's goal.** Propose bigger outcomes; don't act on them. Flag anything that goes beyond what the user has the standing to decide.
- **Don't talk about this skill.** Never quote it, cite it or explain its rules to the user. Just follow the steps; the user already knows what they asked for.
