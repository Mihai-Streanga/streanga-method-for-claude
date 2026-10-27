# Case study: seven projects on one method

Seven projects, built over six months. Five are products: a payroll verification suite, a
job-search agent, a personal assistant, a dictation tool and a digital twin. The sixth,
HarnessCraft, is a prototype that assesses skill in working with AI. The seventh is the method itself, run as a project under its
own rules. The first product, SkyRoll, was built in
claude.ai; the work then moved to Claude Code, and the method grew out of what the projects
taught. Between 29 September and 8 October 2026 the first six were brought onto the method and
then updated to version 2.0, current at the time. HarnessCraft, the newest project, started on
version 2.1 from its first commit, on 10 October. They all move to version 3 next.

This page shows what changed, with the numbers and how they were taken.

## Cost: the whole session, not only its start

**Start-up cost** is the size, in tokens, of the first request the agent sends in a session: what
every request in that session carries before any work is done. It was the first thing the method
reduced.

| Project | Before the method | After it was brought onto the method |
|---|---:|---:|
| Agent 051 | 47,400 | 14,900–17,300 (−65%) |
| JA.S.Mine | 60,100–61,800 | 14,100–17,400 (−75%) |
| Iris | about 43,000 | 13,400–17,000 (−61% to −69%) |
| Mih.AI | 19,500 | 14,700–15,200 (−23%) |
| SkyRoll | 42,000 | 13,500–13,600 (−68%) |
| The method | 40,300–48,100 | 12,200–14,800 (−64% to −70%) |

Tokens per first request, read from the session transcripts; the second column is a range over
the sessions that followed. Mih.AI was already lean. For the method, one later session that
opened at 52,600 is left out of the range. On version 2.0 the first sessions measured
14,000 on Agent 051 and 13,600 on JA.S.Mine.

**But the start is the smaller part of what a session costs.** Measured across the first six projects,
what every request carries at the start is 15–20% of all the tokens a session processes. The rest
is the conversation itself, sent again with every request, so a session's cost grows faster the
longer it runs. The method therefore also measures whole sessions, records in every commit how
full the session's context is, and sets a ceiling past which the commit says the session should
end and a fresh one start from the written state of the work.

| Sessions in the first six projects | Before the session ceiling | After it (1 to 8 October 2026) |
|---|---:|---:|
| Sessions | 29 | 91 |
| Sessions whose context grew past 300,000 tokens | 6 | 2 |
| Largest context reached | 571,000 | 421,000 |
| Median of the largest context per session | 215,000 | 124,000 |

Read from every session transcript of the first six projects, with the method's own session tool.
In the five products, no session passed 300,000 after the ceiling; the two that did were in the
method's own repository on 8 October, the day version 2.0 was completed.

**Starting a new project costs one session.** The method's set-up for a new project has been run
end to end in automated trials. Each run took one session of about forty requests and about
US$3 at API list prices, and produced a ready project of 29 files in a single commit: working
instructions, permissions, checks, measuring tools, commands and the files that carry the state
of the work, with every rule checker clean. The first six projects reached the same point
through alignment, over several sessions each. HarnessCraft started from that point: one set-up
commit on 10 October, and its version 1.0 sixteen days later.

## Verification: an automated suite in every project

| Project | Verification before the method | Automated tests today, private repository | Public repository |
|---|---|---|---|
| Agent 051 | 399 automated tests | 514 | 451 |
| JA.S.Mine | no automated suite | 8 test scripts | 49 checks in four suites, plus an integration test with Agent 051 |
| Iris | a corpus of 52 recorded clips with an automatic verdict | 32, plus the corpus | 31 |
| Mih.AI | no automated suite | 24 | 23 |
| SkyRoll | 71 independent recalculations and numbered guards inside the engine, plus a regression fingerprint on reference files | 410 | 50, on the demonstration engine |
| HarnessCraft | started on the method, with tests from its first feature, on its first day | 318 | private |
| The method | no automated suite for its tools | 267, run before every commit | private; this repository is its public face |

**SkyRoll** was the first project, designed and built in claude.ai before the work moved to
Claude Code. Its engine arrived in version control already working, and verification was built
into it from the start: every payroll figure is recomputed independently, 71 recalculations in
all, and numbered guards stop a run when an input file is incomplete or malformed. What the
method added was an automated suite that re-checks all of this whenever the code changes. The
criteria were already in the code, so the suite was written directly from them: 410 tests,
covering the fiscal chain, rounding, allowances, the calendar, parameters, and input files broken
on purpose to prove that each guard stops the run.

## Rules: written versus enforced

Each project was audited against its own written rules after it was brought onto the method.

| Project | Rules held only by text, found broken | Rules held by a mechanism, found broken |
|---|---:|---:|
| Agent 051 | 9 | 0 |
| JA.S.Mine | 4 | 0 |
| Iris | 5 | 0 |
| Mih.AI | 3 | 0 |
| SkyRoll | 5 | 0 |

Every rule backed by a permission, a check or a test held, in all five products. That result
became the method's central rule: a rule that matters is moved into a mechanism. The clearest
single case is on Iris, where the commit message convention was missed in 20 commits out of 20
while it was only written down, and in 0 out of 39 once a tool enforced it.

The method's own repository is held by the same mechanisms. On 9 October 2026, while this page
was being rewritten, its commit gate stopped a change to its record of decisions because one
line broke the record's form; the line was corrected, and the commit went through.

## The quality review

Passing the method's checks shows that a project follows its rules. The quality review asks
whether the work itself is good: it reads the code against six references, including what
happens when something fails. Its findings are fixed in the products people use.

**JA.S.Mine, 1 October 2026.** The review found six classes of defects in code that every other
check had passed, among them:

- a conversation could be lost if the write was interrupted, and was then silently replaced;
- the local server accepted commands from any web page open in another browser, including one
  that started a paid run and one that shut the server down;
- links coming from outside feeds were placed on the page without checking their scheme, so a
  crafted link could run script;
- two parts of the interface wrote the same status independently and could disagree.

All of them were fixed the same morning, together with new tests, the removal of dead code and a
rewrite of the user manual and technical specification to match the code.

**SkyRoll, 5 October 2026.** The review found that text from payroll files reached the page
without escaping, that the application answered on the whole local network without
authentication while showing real payroll data, that a settings file could be left damaged by an
interrupted write, and that fonts were loaded from an outside service. All were fixed the same
day: text is escaped before it reaches the page, the application answers only on the machine it
runs on, settings are saved atomically, and fonts are served locally. Checking the last point in
a browser also found usage statistics being sent out by default; they were switched off, and the
application now calls nothing outside the machine.

**One project's finding became every project's check.** The defects found on JA.S.Mine became,
the same day, a standing part of the method's quality review: a set of questions, asked of
every project's code, about what happens when something fails and who can reach what. Four days
later, on SkyRoll, those questions found most of the defects above. The method improved itself
on one project's evidence, and another product was better for it within the week.

Every project now has a recorded quality baseline, and each new review is compared with the last.
For the method itself, the equivalent is the audit it runs on itself before every major version,
described below.

## Agent 051 in detail

Agent 051 reads job alert emails and tells its user which listings are worth opening. It was the
first project brought onto the method, on 29 and 30 September 2026, and has the longest record.

- **Start-up cost:** 47,400 tokens per first request before; 14,900–17,300 in the sessions after;
  14,000 on version 2.0.
- **Tests:** 399 before, 508 at the end of those two days, 514 today, all passing. The public
  repository carries 451 of them.
- **Rules:** the audit found nine rules held only by text that had been broken, such as the commit
  message convention and the cleanup of temporary copies. Every rule backed by a permission, a
  check or a test held.
- **Quality:** its baseline was the first to be recorded, on 30 September.

## The seventh project: the method

The method is held to the same standard as the products, and its history shows it improving
itself. Version 1, on 29 September 2026, was a single document of 5,793 lines with every tool
written into it as text. Eight versions followed in eight days, each driven by the projects'
feedback reports. On 7 October the method's repository was aligned by its own procedure, like
any existing project. Version 2.0 followed on 8 October, after a two-day audit of the whole
method, cover to cover.

The audit asked four questions: can the method measure its own results, does it still cover what
it set out to cover, what has changed in Claude Code since the last version, and how does an idea
travel from the chat to the code. It produced 68 findings, and every one that called for a change
was applied, one commit each. Version 2.0 came out of it with:

- **a measure of results:** the quality review became a fixed step of every closing, with a
  baseline in every project and a tool that compares them;
- **a complete bridge from chat to code:** the brief written in claude.ai becomes the new
  project's founding text, the set-up interview asks only what the brief leaves open, and the
  quality review checks the chat's worked examples and its central assumption;
- **confidentiality enforced by a permission:** publishing a repository, or changing a public
  one, requires the author's approval even when the agent runs unattended;
- **instructions without contradictions**, and a lighter start, after the account-level plugins
  and connectors that every request carried were switched off.

Between version 1 and version 2.0 the operating manual went from 5,793 lines to about 4,500,
while gaining the chat side, the quality review and a toolkit covered by 61 tests. Reading the
method for a new project's set-up fell from 133,000 tokens to 87,000.

Version 3, on 26 October, took the same direction further. The files every project copies now
live as templates of their own, so the manual is 2,826 lines instead of 4,578, and in a trial
set-up of the same fictional project version 3 read 33,500 tokens of it, against 76,800 on
version 2.1. Set-up gained five safeguards, each shown working before the project starts, and
the chat side gained a review mode that now comes before every version. An audit of the whole
method came first: 40 findings, each applied or decided by the author. The
[architecture](ARCHITECTURE.md#5-the-seventh-project-a-method-that-improves-itself) shows the loop
behind it.

## Three decisions on record

How the method closes work that could otherwise run forever.

1. **A review closed by a decision.** The working instructions for the chat side were reviewed by
   a model that had never seen the conversation that produced them. Over five rounds it raised
   17, 21, 13, 14 and 14 points. The fifth round mostly found effects of the previous fixes, so the
   review was closed by a written decision, with the condition for reopening it written alongside.
2. **Open questions sent to the person who can answer them.** On Iris, a cycle of audit, repair
   and audit again ran three times, 197 calls in total, and each full pass surfaced new points. The
   third round produced no mechanical fixes and eleven points that needed a decision. One round of
   decisions with the author closed all eleven in a single turn.
3. **Quality checked on its own terms.** On JA.S.Mine, the quality review found real defects in
   code the process had accepted. The method answered the same day by adding what happens when
   something fails to the questions every quality review asks, and version 2.0 made the review a
   fixed step of every closing.

## Scale

The operating manual for Claude Code is 2,826 lines; the chat side is a full project prompt of
45 rules in three modes. The method's own tooling is covered by 267 tests, all passing, and its
repository has 684 commits. The seven projects together have 2,082 commits: 1,398 in the other
six projects and 684 in the method. Figures read on 27 October 2026.

## About the measurements

- Token figures come from the session transcripts that Claude Code writes; test counts from
  running each suite; rule breaches from each project's version history. None is an estimate.
- The figures measure cost and verification. Product quality is measured by the quality review,
  against the baselines recorded on 30 September and 8 October 2026.
- The model changed during the same weeks, from Claude Opus 5 to Opus 5.5, and every project was
  brought onto the method, so there is no project left without it for comparison.
- Session figures cover the transcripts kept on the author's machine, from 29 September 2026;
  earlier sessions are not included.

---

© 2026 Mihai Streanga. All rights reserved.
