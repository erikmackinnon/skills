You're one of six AI models that have each been given this same assignment on its own, in a separate thread. Your output will be compared with the others and combined into one final result, so think for yourself. Don't try to guess what the others will write.

## The article

Read this essay carefully, all of it:
https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/

Fetch it yourself with whatever web or shell tool you have. If you can't reach it, read the local plain-text copy at:
<workspace>/_source/article.txt (a local plain-text copy used only as a fallback during the run; not published)

## Who this is for

The user works with AI agents like you every day, in an agentic IDE. The agents have a real computer, a shell, the ability to install software, and multi-agent orchestration (spawning sub-threads in parallel). Their tasks are mostly software engineering, but they also cover research, writing, and general problem solving. They feel they could get far more out of these agents and want to aim higher.

## Your assignment

1. **Ponder.** Read the article and think about it properly. What is it really saying, beneath the four types (Speed, Altitude, Depth, Range) and the self-efficacy section? What's true about it? What does it leave out? Where would it break down?

2. **Ask yourself five questions, then answer them.** Write five questions that push your understanding beyond a summary of the article, and answer each one seriously. Good questions are ones you can't answer just by quoting the article. Examples of the kind of thing (don't copy these): where the advice fails, how the four types interact, what ambition costs, what part the *model's* self-efficacy plays as opposed to the human's, how to tell real ambition from inflated scope.

3. **Write the prompt.** Using what you've learned, write a reusable prompt the user can paste in at the start of a task with an AI agent, to raise their ambition for that task. It has to work across many tasks, with a slot where the user describes theirs. Purely as an illustration of the *shape* (don't treat it as a template you have to follow), such a prompt might begin with:

   > Before you start building, help me be more ambitious about this task.

   and end with:

   > Then rewrite my task as a prompt that asks for exactly this, and wait for my go-ahead before executing.
   >
   > My task: [describe it here]

   Make your own choices about structure, length, tone, and which ideas from the article matter most. Brevity is a feature: a prompt the user actually pastes beats a perfect one they skip. Keep in mind the article's warnings, too: no role-play in place of real methods, use outside judges, and depth is not the same as bigness.

## Save your work

Write everything to this Markdown file (create it; don't touch any other file in that folder, and don't read the other models' files):

`<workspace>/{{SLUG}}.md`

Use this structure:

```
# {{LABEL}}: Ambition reflections

## Reflections on the article
## Five questions
### Q1: ...
(answer)
... through Q5
## The prompt
(the final prompt in a fenced code block, exactly as the user should paste it)
## Design notes
(a short explanation of the choices behind your prompt: what you put in, what you left out, and why)
```

Don't quote long passages from the article. Short quotes are fine where they help.

## Your final reply

When the file is written, reply with: (a) the file path, (b) the final prompt verbatim in a fenced code block, and (c) 3 to 5 bullets on the most important ideas behind it. That reply goes back to the coordinating agent.
