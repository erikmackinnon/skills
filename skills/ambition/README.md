# Ambition

**A skill that has your AI agent help you aim higher on a task, before it starts building.**

Most of us hand agents the task we can already picture: fix this crash, make these slides, write this doc. The agent does exactly that, competently. Ambition stops first and asks what a more ambitious version would look like. It doesn't mean *bigger*. It means aimed at the outcome you actually want, done with the methods a field-leading expert would use, and checked by something other than the model's own opinion.

Then it rewrites your task as a prompt and waits for your go-ahead.

```
/ambition speed up our test suite
/ambition prepare the Q3 board update
/ambition write the launch announcement for v2
/ambition                ← mid-conversation: apply it to the current work
```

## What it does

1. **Looks at the real material first:** code, data, logs, drafts. Its suggestions come from evidence, not guesses.
2. **Works out what kind of task this is** (software, documents and presentations, research, writing or something else) and what the agent can actually do in your setup. It only proposes methods it can run.
3. **Writes a short brief:**
   - **Outcome:** what you actually want to happen. Is there a more direct route, or one that stops this task coming back?
   - **Method:** what a top practitioner would do, starting from which raw material, with which real tools.
   - **Other fields:** one or two techniques borrowed from other disciplines. Methods, never role-play.
   - **Judge:** what other than you or the model will show it's right (a test, benchmark, holdout or real user).
   - **Target:** one harder goal, plus the constraint that's allowed to veto it.
   - **Gaps:** missing access or tools, and where the model is likely to be fluent but wrong.
4. **Recommends one version.** It names the boldest option it rejected, the cost (including *your* review time), and the cheapest test that could kill the idea. Or it tells you the task is already the right size, and stops.
5. **Rewrites your task as a prompt** with the judge, target, stopping rule and first checkpoint built in. Then it **waits for your go-ahead.**

The rewritten prompt carries one rule into execution: *push past the first "impossible", never shrink scope silently, report the real measured result. An honest miss beats a faked hit.*

## What it won't do

- Run on its own. It only fires when you ask for it.
- Inflate your task. "Deeper, not bigger" is the core test, and "this is already the right size" is a valid answer.
- Role-play experts, give pep talks, or let the model grade its own work.
- Write files into your project uninvited. It offers to save.

## Install

Ambition follows the [Agent Skills](https://agentskills.io) standard, so it works with Claude Code, Codex, Cursor, OpenCode, bb and other agents that support skills.

**With the [skills CLI](https://github.com/vercel-labs/skills):**

```bash
npx skills add erikmackinnon/skills --skill ambition        # this project
npx skills add erikmackinnon/skills --skill ambition -g     # all your projects
```

**Manually:** copy the `skills/ambition` folder into your agent's skills directory, for example:
- Claude Code: `~/.claude/skills/`
- Codex: `~/.agents/skills/`
- Cursor: `~/.cursor/skills/`
- bb: `~/.bb/skills/`

## Credit

Ambition is built on Felix Rieseberg's essay **[How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/)**. It describes ambition along three lines: *altitude* (the outcome behind the task), *depth* (expert methods on raw material) and *range* (methods from other fields). It also covers how much our belief in what's possible holds us back. Read it; it's short and good.

This skill is an independent interpretation. It is not affiliated with or endorsed by Felix Rieseberg.

## How it was made

Six AI models (GPT-6-Astra, GPT-6.1-Sol, Grok 4.7, Claude Fable 5.1, Muse Wonder Full and Claude Opus 5.5) each read the essay independently. Each asked itself five questions to push past a summary, answered them, and wrote its own ambition prompt. A coordinating agent then combined the six into one.

The models agreed on a few things the essay mentions only in passing:
- an outside judge carries the whole approach
- the real cost of ambition is the human's review time
- "stay small" has to be an allowed answer

Their full write-ups and the synthesis are in [`research/ambition/`](../../research/ambition/).

## License

[MIT](../../LICENSE)
