# Case study: seven projects on one method

Seven projects, built over six months, in two groups.

**Six existing projects, brought onto the method.** Five are products: a payroll verification
suite, a job-search agent, a personal assistant, a dictation tool and a digital twin. The sixth is
the method itself, run as a project under its own rules. The first product, SkyRoll, was built in
claude.ai; the work then moved to Claude Code, and the method grew out of what the projects
taught. Between 29 September and 8 October 2026 these six were brought onto the method and then
updated to version 2.0, current at the time.

**One new project, on the method from its first commit.** HarnessCraft, a prototype that assesses
skill in working with AI, was debated in claude.ai and set up on version 2.1 of the method on
10 October. It is the first project that never had to be brought onto the method: it had on its
first day what the others gained through alignment, and it is where the method shows its full
value.

All seven move to version 3 next. This page shows what changed, with the numbers and how they
were taken: first for the projects brought onto the method, then for the one that started on it.

# Part 1. Existing projects, brought onto the method

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

## Verification: an automated suite in every project

| Project | Verification before the method | Automated tests today, private repository | Public repository |
|---|---|---|---|
| Agent 051 | 399 automated tests | 514 | 451 |
| JA.S.Mine | no automated suite | 8 test scripts | 49 checks in four suites, plus an integration test with Agent 051 |
| Iris | a corpus of 52 recorded clips with an automatic verdict | 32, plus the corpus | 31 |
| Mih.AI | no automated suite | 24 | 23 |
| SkyRoll | 71 independent recalculations and numbered guards inside the engine, plus a regression fingerprint on reference files | 410 | 50, on the demonstration engine |
| The method | no automated suite for its tools | 273, run before every commit | private; this repository is its public face |

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

# Part 2. A new project: HarnessCraft, on the method from its first commit

HarnessCraft assesses how a candidate works with AI, to help recruiters with a skill that is new
to the job market. It reads a candidate's project from its version history against written rules,
adds a structured interview and a practical test, and gives each part an equal share of the
result, with an interview guide for the recruiter. The program calls no AI model: scores and
questions come from written rules. Version 1.0 is a prototype, not yet calibrated on real
candidates.

It is the first project to go the method's whole way: an idea debated in claude.ai, a written
brief, one set-up session, then building, auditing and reviewing on the method from the first
day. Every figure below was taken with the method's own tools, from the project's own records.

## From set-up to version 1.0 in sixteen days

| When | What happened |
|---|---|
| 10 October 2026 | The idea debated in claude.ai, in project mode; the brief became the project's founding text. The same day, one set-up session on version 2.1 of the method and a single commit: instructions, permissions, checks, measuring tools, commands and the files that carry the state of the work. Tests came with the first feature. |
| 16 October | A first full audit of the project, in the method's standard form. |
| 16 to 21 October | Five more audits and four quality reviews, each review compared with the last. |
| 22 October | A review in the chat, holding the built project against the idea it started from. |
| 26 October | Version 1.0, declared by the author: 414 commits and 318 tests. |
| 27 October | A public copy, derived from the private repository and checked on a fresh clone. |

**Starting a project costs one session.** The method's set-up has also been run end to end in
automated trials: each run took one session of about forty requests and about US$3 at API list
prices, and produced a ready project of 29 files in a single commit, with every rule checker
clean. The projects in Part 1 reached the same point through alignment, over several sessions
each; HarnessCraft started from it.

## Cost: lean from the first session

| | HarnessCraft |
|---|---:|
| Sessions, from set-up to today | 69 |
| Median first request of a session | 12,575 tokens |
| Share of all processed tokens carried by the start of each request | about 10% |

Read from every HarnessCraft session transcript with the method's session tool. The median
start sits at the low end of what the projects in Part 1 reached only after alignment, and the
start is about a tenth of what the sessions processed, against 15–20% in those projects: the
work itself takes the rest.

## Verification from the first feature

| | HarnessCraft |
|---|---|
| Automated tests, private repository | 320, all passing (318 at version 1.0) |
| Public repository | 281, plus 3 skipped with the reason |
| Continuous integration | the suite runs on GitHub on every push that changes code |

Tests were written with the code from the first day. Of the first 83 commits that added or fixed
product code, 74 came with tests; the project then added a commit check that refuses a
change to the product without a test, unless the message says why. The check went back to the
method, and every new project now starts with it.

## Audited and reviewed while it was built

**Six audits in six days.** One full audit on 16 October, then five more, up to 21 October. The
points each audit raised were settled before the next: on 21 October a single round of decisions
by the author settled 44 of them, and all were in the code the same day.

**Four quality reviews in three days.** From 19 to 21 October the code was read against the
method's references, each review compared with the one before. The second found four defects in
what happens when something fails, among them the interview guide and the test sheet written
straight over the old files, with no protection against an interrupted write, and two saves that
could reach the disk in the wrong order while the screen said "saved". The third review found all
four closed; the fourth found no new ones. From the third review on, every rule breach reported
in one review was closed by the next.

**Rules written before the result.** The rules for each calibration round were fixed before it
ran, and they held after it. A code-quality measure matched the author's blind ranking on 8 of
12 projects, against a threshold of 10 set in advance; it stays in the report as information,
outside the score, and the threshold stayed where it was.

## Held against its starting idea

Before version 1.0, the project was reviewed in the chat's review mode, claim by claim against
the brief it started from. Each claim got a verdict with its evidence: held, held in a narrower
form, changed, or dropped. Five improvements came out of the review, and all five were made before
the version was tagged. One of them sets how the project speaks of its own result: its project sheet matches the
author's blind ranking at the threshold, 10 of 12 projects, with a single rater, and every public
text says exactly that.

## What travelled back to the method

HarnessCraft's notes to the method, numbered HC1 to HC56, were worked through for version 3,
along with the commit check above. Its first claude.ai conversation was also the method's second
real test of the chat side, and confirmed the fixes made after the first. The new project and the
method improved each other in the same weeks.

# Across the seven projects

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

The operating manual for Claude Code is 2,828 lines; the chat side is a full project prompt of
45 rules in three modes. The method's own tooling is covered by 273 tests, all passing, and its
repository has 694 commits. The seven projects together have 2,108 commits: 1,414 in the other
six projects, 433 of them in HarnessCraft, and 694 in the method. Figures read on 27 October 2026.

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
