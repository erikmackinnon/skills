# Research and analysis

Read this when the task is mostly about answering a question from data or sources: market or user research, data analysis, investigations, literature reviews, technical due diligence, "find out why X".

## Outcome

- **What changes depending on the answer?** Name the decision, belief or next action that the research feeds. If nothing would change, the research is the wrong size.
- **When there's no single answer,** aim for a map rather than a verdict: the options, the questions that decide between them, the strongest counter-case, and what evidence would settle each one.
- **A finding beats a summary.** The ambitious version produces something the user didn't know before: an early signal, a hidden cause, an assumption that turns out false.

## Raw material

Use primary sources: the dataset itself, raw logs, original papers and their data, filings, transcripts, source code. Avoid abstracts, dashboards and other people's summaries. If the summarized version is all you can reach, say so and treat its claims as unverified.

## Methods and tools

| Instead of… | A strong researcher would… |
|---|---|
| Reading until it feels done | Write the hypotheses, and what each one predicts, *before* looking |
| Accepting the team's belief | Try to reproduce that belief from the raw data, in a way that could fail |
| Fitting on all the data | Hold out data not used to pick the claim, and test on it once |
| Correlations | Base rates, and comparison or causal designs where the data allows (difference-in-differences, natural experiments) |
| A single source | Triangulate. Every key claim should trace to a source that actually says it |
| Describing the past | Simulate it: build a model that reproduces last year from the logs, then look for the earliest signal nobody knew about, and check that it predicts on unseen data |

Use real tools, such as SQL, Python or R, notebooks and statistical libraries, instead of prose arithmetic. Install them if you can.

## Other fields worth borrowing from

- **Intelligence analysis:** weigh every plausible explanation against the evidence, and look for what each would rule out.
- **Epidemiology:** find who is exposed, what the base rate is, and what else could explain the pattern.
- **Journalism:** ask who says this, how they would know it, and where the document is.
- **Short selling:** follow the incentives, and look for what would have to be hidden.
- **Forecasting:** state predictions with probabilities and dates, so reality can score them.

## Judges

- Held-out data, used once. Every time you tune against it, it stops being independent.
- Sealed predictions: write down what you expect to observe by a given date, before you look.
- An independent source check by a separate agent that is given the sources but not the draft's conclusions.
- Replication with a different method or dataset that reaches the same answer.

## Targets and vetoes

- **Targets:** an early-warning signal that fires earlier than the team's current one; a prediction that holds on data not used to find it; every key claim traced to a primary source.
- **Vetoes:** data leakage, sample size, privacy and consent, and the real limits of the source material.

## Traps

- **A sophisticated model on thin data.** When the material can't support the method, say so, and either get more data or stop.
- **A literature review that only grows.** Length is not depth.
- **Fluent synthesis presented as findings.** Label what is verified, what is inferred and what is opinion.
- **Charts without a claim behind them.**
