# Hard cases

Read this when a call is hard. Typical situations:
- no judge seems possible
- a target could be faked
- the "ambitious" version might just be bigger
- you're unsure the task should grow at all
- the target might be too timid

## Depth or inflation?

Real ambition changes the outcome, or how confident anyone can be in it. Inflation adds surface. Test the proposal:

- **Decision.** Would anything be decided or done differently because of the extra work?
- **Raw material.** Does it start from rawer inputs than the original, or just produce more output from the same summarized ones?
- **Method.** Would a practitioner recognize the method by name, or only the tone?
- **Judge.** Does it come with evidence the modest version lacked? If the only judge is "it looks thorough", it's inflation.
- **Subtraction.** Real ambition often *drops* the default artifact: the table becomes a query, the report becomes a running check. Inflation keeps everything and adds more.
- **Recurrence.** Does it remove future work, or create upkeep?
- **Reviewability.** Can the user check it at roughly the cost of the original?

Depth often makes the output *smaller*: one validated finding instead of twelve charts.

## When to keep the scope

Keeping the scope as written is correct when:

- **The artifact is the commitment.** Someone is waiting on that specific patch, deck, letter or proof. Ask whether a different artifact would disappoint the person who requested it.
- **The bigger outcome has no owner.** Nobody within reach can say yes to it. Label it a proposal and ship what the user can ship.
- **The bigger outcome leaves no signal.** If success would only show up in other people's later behavior, with no data, build or decision to show it, it's a slogan.
- **The goal is learning.** The user is doing it to build their own skill or judgment.
- **Failure would be costly or irreversible,** and there's no judge.
- **The task is genuinely trivial,** and speed is all it needs.

Keeping the scope never means lowering the aim. Put the reach into depth: rawer input, a sharper judge, and a result an expert would learn from.

## Depth or timidity?

The more common failure is the opposite of inflation: the same work a plain request would get, just checked more carefully. Watch for:

- **A target the obvious approach already meets.** If a competent plain attempt would hit it, it isn't a target.
- **A correctness floor posing as a target.** "No errors" and "every value traceable" are requirements or vetoes.
- **A "bold" option that only adds features.** A date picker, a dashboard or a settings panel is surface, not reach.
- **The safe option as the default pick,** with the ambitious one offered as a stretch nobody takes.
- **An easy hit.** If the target fell on the first try, it was too low. Say so and name the next level.

The pinnacle is what the best in the field would call excellent. If the user needs 5 seconds, aim for 200 milliseconds.

## How hard targets get faked

Telling a model a hard goal is reachable doesn't give it confidence. It closes off the easy exits: the caveat, the smaller plan, the refusal. That helps when a real path exists and an outside judge can reject a false arrival. Without a judge, it produces fake success. Watch for these:

- **The proxy moves; the real thing doesn't.** A latency number improves because a cache got warm. A test passes because it checks a mock. A model "predicts" because the train/test split leaked.
- **Success claimed in prose.** Nothing was run; the reply explains why the goal is achievable and offers a plan.
- **A real number, paid for by an unnamed constraint.** Correctness broke, a lock was added, an accessibility feature was cut. That's why every target needs a veto.
- **Agreement without change.** The model agrees the goal is reasonable, then returns the original work dressed in ambitious adjectives.

**On complex tasks, find the method before chasing the number.** Goal-setting research finds that hard, specific goals beat "do your best", but only when there's a working strategy and feedback. When the performer doesn't yet know how to do the task, a hard outcome goal narrows attention onto the number and makes things worse. A learning goal ("find the procedure") works better. So when no method is known yet, make finding one the first goal.

**A measured miss is a success; a faked hit is the only real failure.** Keep going past the first "impossible", never shrink scope silently, and report against the judge.

## What makes a judge independent

Independence has to reach the evidence and the failure modes, not just come from a separate process.

- A second agent that sees your framing can repeat your blind spots. Give it the sources or the raw material, not your conclusions.
- A test suite can encode the same mistaken assumption as the code it tests.
- Held-out data stops being independent once you tune against it.
- A benchmark can be external and still reward the wrong thing.

**The key test:** could this judge return an answer you don't want? If every possible result can be described as success, find a better judge.

## When no judge can exist

This is common in writing, strategy, design and taste. Don't drop the rule; build partial judges and be honest about the remainder.

- **Backtests:** state the strategy or signal in advance, then score it against history it didn't use.
- **Sealed predictions:** write down what you expect to happen by a given date, before you look.
- **Triangulation:** trace every key claim to a primary source that actually says it.
- **Blind comparison:** compare against the modest version, using criteria written in advance.
- **Small samples:** show early samples so the user can calibrate their taste cheaply.

When even those fail, change what kind of ambition you aim for. Aim for a map, not a verdict: the options, the questions that decide between them, the strongest counter-case. Label what's verified, what's inferred and what's taste.

## Four kinds of "can't"

When a task looks impossible, work out which kind it is before pushing:

1. **Beyond current capability** in this particular direction. Models are much stronger in some areas than others.
2. **A missing tool, data or access.** Install it, or ask for it.
3. **A missing judge.** You can't tell a good attempt from a bad one. Build the judge first.
4. **An unclear outcome.** "Can't" really means "won't guess your values". Ask, or state an assumption.

Only a wrongly low estimate of what's possible responds to "keep going". The other three need the specific fix.

## Cost and authority

- **The scarcest resource is the user's review time,** not compute. Unreviewed ambitious output is inventory, not leverage.
- **A durable automation creates a durable obligation:** credentials, monitoring and an owner when its inputs change.
- **Reframing the outcome can go beyond what the user owns.** Flag anything that needs someone else's sign-off.
- **The safest pattern** is an ambitious direction, a disposable first step, and running the new version *alongside* the current one rather than replacing it, expanding only after the probe passes its judge.

## Parallel agents

Use them when the work is genuinely independent and the results can be checked cheaply. For example, one agent runs the borrowed method on the raw material while another tries to break the result. Keep the choice of outcome with one owner, usually the user, because a committee of agents produces five outcomes and no decision. Agreement between agents still needs checking, especially when they started from the same inputs. Giving agents personalities adds nothing but noise to the transcript.
