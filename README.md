# Sébastien Puech

I am part of the team coordinating AI transformation at an international humanitarian NGO of
4,000 staff. I trained as a computer science engineer; today agents write the code, and my job is
to decide what gets built, and to know whether it works.

That second half turned out to be the hard part, and it is what these repositories are about.

## What is here

**[claude-guardrails](https://github.com/sebastienpuech/claude-guardrails)** — the guardrails that
keep a coding agent from doing damage. Each one comes from an incident that actually happened, and
each is covered by a test that tries to defeat it. One red-team pass found 17 bypasses: 14 were
closed, and the 3 that cannot be closed are documented as such rather than quietly dropped.

**[agent-eval-harness](https://github.com/sebastienpuech/agent-eval-harness)** — turning a user
complaint into a prompt change is easy. Knowing whether the change helped, on cases the patch
author never saw, is not. This engine refuses its own patches: one regression on a held-out case
rejects a fix, however much the rest improves.

## How to judge this quickly

Both repositories run their own checks in seconds, with no model calls. The commands are in each
README, and CI runs them on every push, so you can see the last result before deciding whether to
clone anything. `claude-guardrails` needs nothing but Python; `agent-eval-harness` needs two
packages. Run them and disagree with the numbers rather than take them on trust — that is the
point.

Both also carry a section saying what they do *not* do. The most important line in either one is
that the judge used to score quality is weakly calibrated. Scored against one human annotator in
September 2026, it reached a kappa of 0.27, and the same model with no grid did as well; the
details are in the `agent-eval-harness` README. Until that number improves, every quality figure
I publish is internally consistent and externally unproven. Improving it is the current piece of
work. A bad number that is documented beats no measurement at all.

## What I am actually claiming

Not that these tools are novel. Eval platforms pin baselines and flag regressions; that ground is
well occupied, and both READMEs name the tools that occupy it.

What I have is narrower: a former operations director who measures agent work instead of trusting
it.
Deterministic gates rather than a model grading itself. Held-out sets hidden from whatever wrote
the patch. Guardrails attacked on purpose, with the failures published. And a dated record of
what broke, what changed because of it, and what was tried and rejected.

One thing these repositories cannot show you: the system that runs in production, with real users
and real consequences, belongs to my employer and is not published. What is here is the tooling
and the method around that work, not the work itself. Judge it as such.

The dated record is the part I would look at first, if I were you.
