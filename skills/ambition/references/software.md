# Software tasks

Read this when the task is mostly about code: bugs, features, performance, refactors, infrastructure, tooling, CI.

## Outcome

- **From a fix to a class of failure.** "Fix this crash" often really means "stop this kind of crash from reaching users". "Make this test pass" often means "make this module trustworthy".
- **From a fix to a loop that runs without the user.** The most durable version sets up an ongoing process so the user doesn't have to hand you each instance. It might keep a service crash-free, keep the build green, or keep dependencies current.
  - That only works once the plumbing exists: crash reports you can fetch, a map from release to commit, and machines or containers where you can reproduce and verify a fix.
  - Building that plumbing *is* the ambitious move. Name it and price it.
- **When to stay on the artifact.** If someone is waiting on this specific patch, migration or API, keep it. Put the ambition into how it's built and how it's proven.

## Raw material

Start from what the system produced, not what someone wrote about it:
- stack traces, core dumps, logs and traces
- production profiles and real inputs
- `git log` and `git blame`, plus related issues and their history
- the failing CI run itself, not the ticket summary

## Methods and tools

| Instead of… | A strong engineer would… |
|---|---|
| Reading code and guessing | Write a failing test or a minimal reproduction first |
| Hunting for the bad commit | Run `git bisect` against a reproduction |
| Optimizing by intuition | Profile first: flame graphs, `perf`, `py-spy`, browser devtools, `EXPLAIN ANALYZE` |
| A few hand-picked tests | Property-based testing (Hypothesis, fast-check), fuzzing, or differential testing against a reference implementation |
| Trusting coverage numbers | Mutation testing, to see whether the tests can actually fail |
| "Seems faster" | A benchmark with warmup and repeated runs (hyperfine, criterion, pytest-benchmark), compared against a baseline |
| Fixing one platform | Reproducing on every supported platform, in containers or VMs if needed |

Install what's missing if you're able to, and say so in the brief.

## Other fields worth borrowing from

- **Site reliability:** error budgets and service-level objectives, so "reliable" becomes a number.
- **Epidemiology:** cluster incidents by shared exposure (version, platform, feature flag) before treating cases one at a time.
- **Manufacturing:** error-proofing (poka-yoke). Make the bad state impossible to reach rather than catching it later.
- **Security:** threat modeling, to see who could abuse the change and how.
- **User research:** task-based tests with a real user, for anything with a UI.

## Judges

- A test that fails before the change and passes after it, in CI, not only on your machine.
- A benchmark on representative workloads against a recorded baseline, plus a correctness check, so a speedup can't come from a broken result.
- A reproduction of the original failure, shown gone on every platform that matters.
- Mutation score or fuzzing time with no new crashes.
- For a loop that runs over time: the metric it's meant to hold (crash-free sessions, build success rate), watched over real time.

## Targets and vetoes

- **Targets:** 10× rather than 2×; p95 latency under a hard number; no flaky tests; a whole class of bug ruled out by construction.
- **Vetoes:** correctness, public API compatibility, security, data integrity, readability for the next maintainer, new dependency weight.

## Traps

- **A rewrite or a new framework** when the real fix is small. That's inflation, not depth.
- **Tests that check a mock** instead of the behavior, or benchmarks that measure a cache.
- **Silent downscoping:** "I implemented a simplified version", or skipping the hard platform.
- **A fancy method the system can't support,** such as formal proofs for a codebase with no specification.
