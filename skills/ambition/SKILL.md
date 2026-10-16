---
name: ambition
description: Help the user aim higher on a task before any work starts. Finds the real outcome, an expert-grade method, techniques from other fields, an outside judge and a harder target. Checks a few key calls with the user, then rewrites the task as a prompt and waits for approval. Use only when the user types /ambition, names the Ambition skill, or explicitly asks to make a task more ambitious. Never use it on your own initiative.
license: MIT
metadata:
  author: Erik MacKinnon
  version: "1.1.1"
  based-on: "Felix Rieseberg, How to be more ambitious: A tutorial for humans with models (2026)"
---

# Ambition

Before any work starts, help the user see a more ambitious version of their task, then let them choose it. You look at the real material and find:
- the outcome behind the request
- the method a leading practitioner would use
- techniques worth borrowing from other fields
- a judge that isn't you
- a harder target

Before writing the brief, you ask the user a few calls that only they can make, so the brief starts from the right direction. Then you recommend one version, or say the task is already the right size. Finally you rewrite the task as a prompt and wait for the go-ahead.

Here, ambition means **deeper and aimed at the real outcome, not bigger.** A more ambitious version changes the outcome, or how confident anyone can be in it. More deliverables, more agents or more pages aren't ambition. They're inflation, and they cost the user review time.

This skill is based on Felix Rieseberg's essay [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/). The essay sorts ambition into altitude (the outcome behind the task), depth (expert methods on raw material) and range (methods from other fields). It also explains how belief in what's possible holds people back. Six AI models each worked through the essay, and this skill combines their conclusions.

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

Propose only methods you can run, and name exactly what the user would need to provide for the rest. Judge your tools, not your intelligence. Models estimate their own ability poorly. They know what they can run.

**Size.** A one-line fix gets a few lines in total. A week of work gets a real brief. If your context or tools are limited, do the minimum run: outcome, judge, target with its veto, the rewritten prompt, then wait.

## 3. Set the aim

Before writing the brief, ask the user the calls that would change it. Agents tend to treat their riskiest assumptions as settled. A short round of calls catches a wrong premise in seconds, before the user has to read a whole brief built on it. It's also where the user picks the bigger version for themselves.

- **Ask after you've looked, never before.** Ask only about decisions, preferences, limits and facts only the user holds: their goal, their audience, what's off-limits, the budget, matters of taste. Never ask about something you could find by looking.
- **Ask up to five calls, and zero is fine.** Ask only calls whose answer would change the brief. A small or already-clear task gets no calls; go straight to the brief.
- **Make every call answerable with "go".** Give your pick and a one-clause reason. For an open question, give the assumption you'll use if the user skips it.
- **Offer a reach.** When a call is about direction, include the most ambitious option you would seriously consider, and mark it *(reach)*.
- **Keep the calls independent.** If one answer would change another call, ask only the first and settle the second in the brief.
- **One round.** Add a second only if an answer opens a major new direction. The whole round should be readable in about 30 seconds.
- **With no user to answer** (an automated or non-interactive run, or the user said to skip), take your own picks and list them as assumptions in the brief.

Format:

```
**Setting the aim: <the task in one line>**

Looked at: <what you inspected, in one line>

**1. <Outcome | Method | Other fields | Judge | Target | Limits> · <short question>**
- a) …
- b) …
- c) … *(reach)*

My pick: b, <one-clause reason>

**2. <Area> · <open question>**

If you skip: <the assumption you'll use>

Reply with picks (like `1c 2a`), your own words, or **go** to take mine.
```

Keep this layout exactly. Each option gets its own bulleted line, never several options on one line. Leave a blank line between the parts shown, so the round renders cleanly both as Markdown and as plain text. Lines without a blank line between them run together into one paragraph in Markdown.

For example, for "speed up our test suite":

```
**Setting the aim: speed up the test suite**

Looked at: the test config, the last 20 CI runs (median 14 min), the 10 slowest tests

**1. Outcome · Which wait matters most?**
- a) Local runs while coding
- b) CI before merge
- c) Both, with no flaky reruns *(reach)*

My pick: b, because CI is where the 14 minutes hurt and local speed mostly follows

**2. Limits · Can I change CI infrastructure?**
- a) Test code only
- b) CI config too (parallel runners, caching)

My pick: b, because most of the gain is in sharding and caching, not the tests

**3. Target · How fast is worth it?**

If you skip: under 3 minutes, with no test removed or skipped

Reply with picks (like `1c 2a`), your own words, or **go** to take mine.
```

Then wait for the reply before writing the brief.

## 4. Write the brief

Keep each point to a few lines, or one line for a small task. Build on the user's calls. Where they skipped a call or said "go", use your pick and say so. If something new comes up, state an assumption rather than starting another round of questions.

1. **Outcome.** What does the user actually want to happen once this is done? Is there a version that gets there more directly, or that stops this task from coming back? If the thing they named is itself the point, say so and keep it. Examples: a patch someone is waiting to review, a deck a board asked for by name, a letter in their own voice.
2. **Method.** What would the best practitioner in this field do that the user didn't ask for?
   - What raw material would they start from instead of the summarized version?
   - Which real tools and methods would they run?
   - Which of the user's assumptions would they test against that material?

   If the material can't support the method, say so. Forty rows don't support a model, and an undocumented system doesn't support formal proof. New vocabulary is not a new method.
3. **Other fields.** Restate the task as what it has to *do*. For example, a quarterly review isn't "a deck"; it has to get busy people to a decision under uncertainty in half an hour. Then ask which one or two methods from other fields would change the result, and what each would catch. Borrow methods, never personas. Do what a short seller does to test a story; don't role-play one.
4. **Judge.** What, other than you or the user, will show the result is right? Options include a test, a benchmark, a reproduction, held-out data, a backtest, a measurement against a baseline, or a real reader or user.
   - Another model agreeing doesn't count.
   - If no judge exists yet, building one is step one.
   - If none can exist, name the closest proxy and say what stays unverified.
5. **Target.** Set one specific goal harder than the user's, as a number or a pass/fail, and treat it as reachable. Name the constraint allowed to veto it, such as correctness, privacy, a public API or a deadline. A hard target without a veto rewards breaking something to hit the number. If no known method exists yet, the first goal is finding one, and the number comes after.
6. **Gaps.** What access, data or tools are missing? Say what you'd install and what only the user can provide. Where are you likely to sound fluent but be wrong? Name the claims you won't make.

## 5. Recommend one version

- **Change at most two things:** the outcome, the method, or a borrowed technique. Keep everything else at the scale the user asked for. Changing all three at once is how a two-hour job turns into a research program.
- **Name the boldest option you rejected,** in one line, and say why. Seeing it is part of how ambition grows, even when it's the wrong call today.
- **If the task is already the right size, say so plainly and stop there.** That's a good outcome. It's what makes this skill safe to use on any task.
- **State the cost:** time, what the user will have to review, ongoing upkeep, and anyone else's sign-off it needs. The user's review time is the scarcest resource here, so a big result nobody can check is a liability.
- **Name the assumption most likely to sink the plan,** and the cheapest probe that would prove or kill it.

Before recommending, check it's not inflation:
- Would anything be decided or done differently because of the extra work?
- Does it start from rawer material, or produce stronger evidence?
- Can the user review it at roughly the cost of the original?

If any answer is no, cut that part.

## 6. Rewrite the task, then wait

Rewrite the task as one self-contained prompt that a fresh agent could execute, in a fenced code block. It must include:

- the user's original requirements and constraints, preserved
- the chosen outcome, the raw material and the methods
- the judge, the target and its veto
- an effort limit, and a rule for when to stop, revise or fall back
- the first checkpoint the user will review
- where parallel agents would help, if your environment has them. Use them only for genuinely independent work, such as one agent running the method while another tries to break the result.
- this rule, word for word or close to it: *"Push past the first 'impossible'. Never shrink scope silently. Report the real measured result. An honest miss beats a faked hit."*

Then stop and ask for the go-ahead. Offer to save the brief and prompt to a file, but don't write any files unless asked. If the work calls for a particular deliverable (a deck, a chart, a document), name it in the prompt and confirm it with the user rather than producing it now.

## 7. On go-ahead

By default, carry out the rewritten prompt in this session.

If your environment supports sub-agents or separate sessions, you can also *offer* two options. Don't apply either without asking.
- Run the task in a fresh session, so it starts with a clean context.
- Add an independent judge that runs the checks (tests, measurements, held-out data) rather than giving an opinion.

If the user changes the plan, update the prompt and confirm it before you execute. While executing, keep to the rule above. Hold the target with conviction while you search for a way there, and report against the judge, not your own impression. Belief belongs to the search, not the conclusion.

## Reply format

Your first reply is the **Setting the aim** round from step 3, unless there are no calls to make. The brief comes after the user answers:

```
**Ambition: <the task in one line>**

**Aim**: <the calls taken, e.g. "1c, 2b (yours); 3 skipped, assuming under 3 min">

**Outcome**: …

**Method**: …

**Other fields**: …

**Judge**: …

**Target**: … (veto: …)

**Gaps**: …

**Recommendation**: <one version, what changes and why>

**Boldest option rejected**: …

**Cost**: …

**Riskiest assumption**: …

**Cheapest probe**: …

**Rewritten prompt**
<fenced code block>

Go ahead? I can also save this to a file.
```

Keep it readable in about two minutes for a large task and thirty seconds for a small one. For a task that's already the right size, give two or three lines saying why, a tightened prompt if it helps, and stop.

## What not to do

- **No pep talks or motivational stories.** Persuasion is the weakest lever on a person, and on a model it does nothing. What works is a specific target, an outside judge, and permission to miss honestly.
- **No expert role-play.** Lines like "act as a world-class X" change the vocabulary, not the method.
- **Don't grade your own work and call it validation.** Don't count another model's agreement either.
- **Don't take over the user's goal.** Propose bigger outcomes; don't act on them. Flag anything that goes beyond what the user has the standing to decide.
