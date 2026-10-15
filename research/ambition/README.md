# How Ambition was made

The [Ambition skill](../../skills/ambition/) started as an experiment on 15 October 2026. Six AI models each read the same essay on their own and were asked to think hard about it. A coordinating agent then combined what they produced into one skill.

## The source

Felix Rieseberg, **[How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/)**, published 13 October 2026. None of the essay is reproduced here; read it at the link.

## The process

1. **One brief, six models, separate threads.** Every model received the identical [brief](brief.md) (`{{SLUG}}` and `{{LABEL}}` were filled in per model). Each was told to work independently and not to read the others' output.
2. **Ponder, then question.** Each model wrote its reflections on the essay, then asked itself five questions meant to push past a summary and answered them.
3. **Write a prompt.** Each wrote a reusable prompt to raise ambition at the start of any task, along with notes on its design choices.
4. **Synthesize.** A coordinating agent (Claude Opus 5.5) read all six, noted where they agreed and where they disagreed, and merged them into one prompt. The reasoning is in [SYNTHESIS.md](SYNTHESIS.md).
5. **Turn it into a skill.** The combined prompt became the skill's procedure. The models' deeper reasoning became the reference guides, which load only when needed.

## The six write-ups

| Model | Effort | Write-up | Standout idea |
|---|---|---|---|
| GPT-6-Astra | high | [gpt-6-astra-high.md](gpt-6-astra-high.md) | Aim at the constraint that limits the outcome. Another agent agreeing is not validation. |
| GPT-6.1-Sol | xhigh | [gpt-6.1-sol-xhigh.md](gpt-6.1-sol-xhigh.md) | Set an effort limit and a stopping rule. Disprove the riskiest assumption cheaply. |
| Grok 4.7 | high | [grok-4.7-high.md](grok-4.7-high.md) | Give every hard target a veto. "Where are you fluent but wrong?" Keep the artifact when it *is* the point. |
| Claude Fable 5.1 | high | [fable-5.1-high.md](fable-5.1-high.md) | Pick one primary axis. Put the judge before the target. "If it should stay small, say so and stop." |
| Muse Wonder Full | max | [muse-wonder-full-max.md](muse-wonder-full-max.md) | "Belief is lent to the search, not to the conclusion." What to do when no judge exists. |
| Claude Opus 5.5 | high | [opus-5.5-high.md](opus-5.5-high.md) | Ambition is capped by the best check the agent can run. "An honest miss beats a faked hit." |

## What they agreed on

All six models independently treated several ideas as central, even though the essay gives each of them a sentence or two at most:
- **The outside judge carries the whole approach.** Telling a model a hard goal is reachable is only safe when something other than the model can say no.
- **The real cost of ambition is the human's review time,** not compute.
- **"Stay small" has to be an allowed answer.** Otherwise the prompt is only safe on tasks you already know are big.
- **Deeper, not bigger.** Real ambition often makes the output *smaller*.

## Notes

- The write-ups are the models' own work, published as written. They were produced for one person, the skill's author, so "the user" in them means him.
- [SYNTHESIS.md](SYNTHESIS.md) contains the two prompts (full and compact) that came before the skill. The skill extends them with task-type detection, capability checks and the reference guides.
- The brief offered a local plain-text copy of the essay as a fallback in case a model couldn't fetch the page. It isn't published here. One model (Opus 5.5) used it.
- Model names and effort levels are as configured in the [bb](https://bb.dev) agent IDE where the experiment ran.
