# Documents and presentations

Read this when the task is mostly office work: decks, reports, briefs, spreadsheets, plans, board or business reviews, proposals.

## Outcome

Most business documents exist to produce a decision or an action. Ask what the meeting or the reader is supposed to *do* afterwards. Ambition goes up in steps. Aim for the highest step the user can own, and name the next one up:

1. **Update the document.** Fill in the template with this period's numbers. This is the baseline.
2. **Explain it.** Use the full underlying data to say what changed, why it changed, and what to do about it.
3. **Prepare the decision.** Find the few decisions that matter most right now and set out the options, with the evidence for and against each.
4. **Improve the mechanism.** Ask what the document is for, such as catching problems early or moving money and people to the right places. Then design a better way to do that, show from past data that it would have caught things sooner, and run it alongside the current process for a cycle.

If the format is required (a board, regulator or customer expects that exact artifact), keep it. Use the outcome question only to sharpen which decisions the document must force.

## Raw material

Go to the source data, not last period's slides:
- CRM, finance and product-analytics exports, and the raw event logs
- what customers actually said in their own words
- support tickets, sales notes and meeting transcripts

Ask the user for access where you don't have it, and name the exact export you need.

## Methods and tools

| Instead of… | A strong analyst or communicator would… |
|---|---|
| Markdown tables of totals | Load the data into a real tool (SQL, pandas, a notebook, a proper spreadsheet model) and run the analysis there |
| Averages | Cohort and segment breakdowns, trends with confidence ranges, and comparison with the same period last year |
| Assuming the usual story | Test the team's belief against the raw data. For example, "Is churn really an onboarding problem?" |
| Slides that list facts | One claim per slide, with the evidence underneath it, and the main point first |
| Charts by hand | Charts generated from the data, labeled so the point reads in five seconds |
| A static spreadsheet | Formulas, scenarios and sensitivity tables, so readers can see what moves the result |

**Visuals are part of the work.** If you can make charts, diagrams or real `.pptx`, `.xlsx` or `.docx` files, propose them, but in the rewritten prompt rather than now. If you can't, say what the user would need.

## Other fields worth borrowing from

- **Journalism:** lead with the news, source every claim, and include the fact that would most undermine the story.
- **Editing:** cut a third and see what the document lost.
- **Short selling:** build the strongest case *against* the plan from primary data.
- **Forensic accounting:** reconcile every headline number to its source.
- **Information design:** make the one chart that would make most of the deck unnecessary.
- **Motion or audio design:** only if the piece will be presented and the point can't be seen in a still image.

## Judges

- **A backtest.** Would this analysis or process have flagged last year's problems earlier?
- **A cold read.** Can someone from the intended audience who hasn't seen the work state the decision and the evidence for it in 30 seconds?
- **Reconciliation.** Every number traces to a source, and the totals match the system of record.
- **A red-team pass** by a separate agent or person who builds the case against the plan from the same raw data.

## Targets and vetoes

- **Targets:** decision-ready in ten minutes of reading; every number traceable to its source; one finding the team didn't already know, shown to hold on data not used to find it.
- **Vetoes:** accuracy, confidentiality, a required template or brand, the presenter's time slot.

## Traps

- **Forty slides, or a dashboard nobody asked for.** That's bigger, not deeper.
- **A cast of role-played experts "reviewing" the deck.** Use their methods instead.
- **Charts that decorate rather than prove.**
- **Changing a process the user doesn't own.** Flag who would need to agree.
