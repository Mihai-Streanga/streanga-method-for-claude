# The Streanga Method — working with Claude (Claude Code and claude.ai)

An HR and payroll specialist's method for building software with Claude, developed over six
months of work on seven real projects: five products, a prototype, and the method itself. Built for and tested
only with Claude.

The Streanga Method is a complete way of working with Claude, from the first idea to a tested,
maintained product. It covers both places where the work happens, **claude.ai**, where ideas are
researched, debated and decided, and **Claude Code**, where they are built, verified and kept in
order from one session to the next. It has a path for **new projects**, which start on the method
from their first commit, and for **existing projects**, which are brought onto it without losing
anything they already have. It runs the five products and the prototype, and it is the seventh project itself:
maintained under its own rules, with its own tooling, tests, audits and release history, and
improved by the same loop it runs for the others.

## One method, five ways in

| | What it does | What it produces |
|---|---|---|
| **claude.ai, project mode** | An idea is debated until the author can decide whether to build it: three approaches weighed, the areas code can verify separated from those only a person can judge, a smallest first version, a pre-mortem and the one assumption that would make the project pointless. | A written brief that someone who never saw the conversation can read and act on, checked against a seven-point gate. |
| **claude.ai, exploration mode** | Research and new ideas: a search plan, primary sources first, the author's ideas before Claude's, a verdict on every finding. | An exploration file with sources, verdicts and the searches made, checked against a seven-point gate. |
| **claude.ai, review mode** | A built project is held against its starting idea before each version: is it still used, how each of its claims stood up, and what the next version should aim at. | A review that the version waits for, with the improvements it calls for. |
| **Claude Code, new project** | One set-up session: the brief is read, a short interview asks only what it leaves open, and the project's whole working environment is created from the method and proven to work. | A ready project in a single commit: instructions, permissions, checks, measuring tools, commands, and the files that carry the work from one session to the next. |
| **Claude Code, existing project** | A fixed sequence of sessions, one kind of change in each: audit, environment, a test safety net, tools, content, publication, report back. | The same environment as a new project, with everything the project already had kept. |

The brief is the only thing that crosses from the chat into the build. It becomes the new
project's founding text, so what was decided in the conversation is checked against what was
built. **[The architecture](docs/ARCHITECTURE.md)** shows how all the parts fit together.

## What the method gives a project

- **Rules that hold.** Rules that matter are enforced by a mechanism: a permission, a check that
  stops a commit, a test that fails. Instructions alone are followed most of the time; mechanisms
  are followed every time.
- **Proof instead of reports.** A claim counts together with the output of the command that
  supports it. Every check says what it covers and what it does not.
- **Continuity across sessions.** The agent remembers nothing between sessions, so the state of
  the work, its decisions and their reasons live on disk, where the next session starts from.
- **Measured cost.** The cost of a session's start, of whole sessions and of paid API calls is
  measured from the session's own records, and decisions about cost are made on those numbers.
- **A ready-made toolkit.** A new project starts with tools for measuring cost, checks that
  enforce the rules, a flow for moving between sessions, nine commands for repeatable work,
  templates for every starting file, and a catalogue of twenty-one verification and five
  architecture patterns, each proven in one of the projects.
- **Verification chosen per area.** Arithmetic is recomputed by independent code on every run;
  voice, design and tone are judged in use, by a person.
- **A quality review.** Beyond following its rules, the code is read for whether it is good,
  including what happens when something fails. Findings are fixed in the product.
- **A second pair of eyes.** Work that matters is reviewed by a separate instance that sees only
  the result, never the conversation that produced it.
- **A defined end.** Every repeatable task starts with a written condition for "done", and a
  project version is closed by a fixed sequence of nine steps.
- **A way back to the method.** Each project reports what it learned, and the method changes on
  that evidence, so a good solution found in one project reaches all of them.

## Results

Measured on the projects, from session transcripts, test runs and version history:

- **Better products.** The quality review found real defects in code that had passed every other
  check, and they were fixed the same day. On JA.S.Mine: a conversation that could be lost on an
  interrupted write, and a local server that accepted commands, including a paid run, from any web
  page. On SkyRoll: text from payroll files that reached the page unescaped, and an application
  that answered on the whole local network while showing real payroll data. Most of the SkyRoll
  defects were found by questions the method had added four days earlier, from the JA.S.Mine
  review. On HarnessCraft, four quality reviews in three days: the second found four defects in
  what happens when something fails, and the third found all four closed.
- **Sessions that stay lean.** The start of a session is only 15–20% of what it processes; the
  rest is the conversation. In the first week after the method set a ceiling on session growth,
  2 sessions out of 91 passed 300,000 tokens of context, against 6 out of 29 before, and the
  median session peaked at 124,000 instead of 215,000. In the products, none passed it.
- **Session start-up cost cut by 61–75%** on five of the six projects brought onto the method,
  the method included, and by 23% on the sixth, which was already lean.
- **A new project, on the method from day one.** Setting up a project takes one session: in
  end-to-end trials, about forty requests and about US$3 at API list prices, for a ready project
  of 29 files with every rule checker clean. HarnessCraft, the first project started this way,
  went from its set-up commit on 10 October to its version 1.0 on 26 October, with 318 tests, six
  audits, four quality reviews and a review against its starting idea on the way. Across its 69
  sessions the median first request is 12,575 tokens, and the start of each request is about a
  tenth of all it processed.
- **An automated test suite in every project**, the method included: 410 tests on SkyRoll,
  written from the 71 independent recalculations and the guards already built into its engine;
  514 on Agent 051; 320 on HarnessCraft; 273 for the method's own tools.
- **Mechanisms hold where text does not.** An audit of the five products against their own rules
  found 26 breaches of rules that existed only as written instructions, and none of any rule
  backed by a permission, a check or a test. On one project, a commit convention went from 20
  misses out of 20 commits to 0 out of 39 once a tool enforced it.
- **A method that improves itself.** Ten versions in ten days, driven by 22 reports from the
  projects and from independent reviews, then version 2.0 after a two-day audit of the whole
  method: 68 findings, and every one that called for a change applied. On the way the manual
  shrank from 5,793 lines to about 4,500 while gaining the chat side, the quality review and a
  toolkit covered by 61 tests. Version 3, on 26 October, cut what a new project's set-up reads
  from the manual by more than half.

## Scale

| | |
|---|---|
| Time | six months, from the first project built in claude.ai to the method in its current form |
| Operating manual for Claude Code | 2,828 lines, with its templates in separate files and a catalogue of twenty-one verification and five architecture patterns |
| Working instructions for claude.ai | a full project prompt of 45 rules in three modes, reviewed over five rounds by an independent model |
| The method's own tooling | 273 automated tests, all passing |
| Versions of the method | twelve, from version 1 to version 3 |
| Written feedback | 38 reports and conversation records, from the projects, from real chat conversations and from independent reviews |
| The seven projects | 2,108 commits: 1,414 in the other six projects, 694 in the method |

Figures read on 27 October 2026.

## The seven projects

The five products and HarnessCraft are public; their test counts were taken by running each suite
on a fresh clone of the public repository, on 8 October 2026 and, for HarnessCraft, on 27 October.
The method is private: this repository presents its architecture, principles and results.

| Project | What it does | Tests in the public repository |
|---|---|---|
| [SkyRoll](https://github.com/Mihai-Streanga/SkyRoll-public) | Monthly payroll verification: every figure recomputed independently, guards that stop a run on a bad input file. The public repository shows the architecture and a demonstration engine on synthetic data. The first project, designed in claude.ai. | 50 |
| [Agent 051](https://github.com/Mihai-Streanga/Agent051-public) | Reads job alert emails, checks every listing against your own criteria and ends with a short briefing of what is new and relevant | 451 |
| [JA.S.Mine](https://github.com/Mihai-Streanga/Jasmine-public) | A personal assistant that runs full-screen on a Windows laptop, with rooms for mail, news, a log of facts and three conversation styles | 49 checks in four suites, plus an integration test with Agent 051 |
| [Iris](https://github.com/Mihai-Streanga/Iris-public) | Local voice dictation for Windows: speech recognition on your own machine, text typed wherever the cursor is | 31, plus a corpus of recorded clips with an automatic verdict |
| [Mih.AI](https://github.com/Mihai-Streanga/DigitalTwin-public) | A personal digital twin: a local web app where you talk, by keyboard or by voice, with a model prompted from one person's writing | 23 |
| [HarnessCraft](https://github.com/Mihai-Streanga/HarnessCraft-public) | A prototype that assesses skill in working with AI, built to help recruiters: scores from a candidate's projects, a practical test and an interview, with an interview guide. The first project started on the method from its first commit. | 281, plus 2 skipped with the reason: one needs private files, one is the author's own case |
| [The method](docs/ARCHITECTURE.md#5-the-seventh-project-a-method-that-improves-itself) | The method itself, run as a project: twelve versions, its own alignment, audits and toolkit, and the feedback loop that improves it | 273, in its private repository |

Each product repository holds, at its root, the instructions Claude Code reads when it works
there: the project's map, commands and rules, for example in
[Iris](https://github.com/Mihai-Streanga/Iris-public) and [Agent 051](https://github.com/Mihai-Streanga/Agent051-public). They hold each project's own
rules; the method's working rules stay private.

## Read more

- **[Architecture](docs/ARCHITECTURE.md)** — the chat side, the build side, the paths for new and
  existing projects, the ready-made toolkit, the quality review, and how the method improves
  itself.
- **[Principles](docs/PRINCIPLES.md)** — the ten principles the method is built on, each with the
  real situation that produced it.
- **[Case study](docs/CASE_STUDY.md)** — in two parts: the six existing projects brought onto
  the method, and HarnessCraft, the new project started on it. Cost, verification, rules, quality
  and the method's own evolution, with the numbers and how they were taken.

## About the author

Mihai Streanga is an HR and payroll specialist with more than ten years of full-cycle payroll
work, who builds tools that automate HR work with Claude. The first of them, SkyRoll, was designed
and built in claude.ai; the work then moved to Claude Code, and the method grew out of both. It
is how the work is organised: the domain expert stays the architect and the judge of every
result, and Claude does the building.

## Contact

[LinkedIn](https://www.linkedin.com/in/mihai-%C5%9Ftreang%C4%83-aa3a2b176/)

---

© 2026 Mihai Streanga. All rights reserved.
