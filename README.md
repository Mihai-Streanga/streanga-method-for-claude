# The Streanga Method — working with Claude (Claude Code and claude.ai)

An HR and payroll specialist's method for building software with Claude, developed over six
months of work on six real projects: five products, and the method itself. Built for and tested
only with Claude.

The Streanga Method is a complete way of working with Claude, from the first idea to a tested,
maintained product. It covers both places where the work happens, **claude.ai**, where ideas are
researched, debated and decided, and **Claude Code**, where they are built, verified and kept in
order from one session to the next. It has a path for **new projects**, which start on the method
from their first commit, and for **existing projects**, which are brought onto it without losing
anything they already have. It runs all five products, and it is the sixth project itself:
maintained under its own rules, with its own tooling, tests, audits and release history, and
improved by the same loop it runs for the others.

## One method, four ways in

| | What it does | What it produces |
|---|---|---|
| **claude.ai, project mode** | An idea is debated until the author can decide whether to build it: three approaches weighed, the areas code can verify separated from those only a person can judge, a smallest first version, a pre-mortem and the one assumption that would make the project pointless. | A written brief that someone who never saw the conversation can read and act on, checked against a five-point gate. |
| **claude.ai, exploration mode** | Research and new ideas: a search plan, primary sources first, the author's ideas before Claude's, a verdict on every finding. | An exploration file with sources, verdicts and the searches made, checked against a six-point gate. |
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
  enforce the rules, a flow for moving between sessions, seven commands for repeatable work,
  templates for every starting file, and a catalogue of twenty verification and five
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

Measured on the six projects, from session transcripts, test runs and version history:

- **Better products.** The quality review found real defects in code that had passed every other
  check, and they were fixed the same day. On JA.S.Mine: a conversation that could be lost on an
  interrupted write, and a local server that accepted commands, including a paid run, from any web
  page. On SkyRoll: text from payroll files that reached the page unescaped, and an application
  that answered on the whole local network while showing real payroll data. Most of the SkyRoll
  defects were found by questions the method had added four days earlier, from the JA.S.Mine
  review.
- **Sessions that stay lean.** The start of a session is only 15–20% of what it processes; the
  rest is the conversation. Since the method set a ceiling on session growth, 2 sessions out of
  91 have passed 300,000 tokens of context, against 6 out of 29 before, and the median session
  peaks at 124,000 instead of 215,000. In the five products, none has passed it since.
- **Session start-up cost cut by 61–75%** on five projects, the method included, and by 23% on
  the sixth, which was already lean.
- **A new project in one session.** In end-to-end trials, setting up a new project took one
  session of about forty requests, about US$3 at API list prices, and produced a ready project of
  29 files with every rule checker clean.
- **An automated test suite in every project**, the method included: 410 tests on SkyRoll,
  written from the 71 independent recalculations and the guards already built into its engine;
  514 on Agent 051; 66 for the method's own tools.
- **Mechanisms hold where text does not.** An audit of the five products against their own rules
  found 26 breaches of rules that existed only as written instructions, and none of any rule
  backed by a permission, a check or a test. On one project, a commit convention went from 20
  misses out of 20 commits to 0 out of 39 once a tool enforced it.
- **A method that improves itself.** Ten versions in ten days, driven by 22 reports from the
  projects and from independent reviews, then version 2.0 after a two-day audit of the whole
  method: 68 findings, and every one that called for a change applied. On the way the manual
  shrank from 5,793 lines to about 4,500 while gaining the chat side, the quality review and a
  toolkit covered by 61 tests.

## Scale

| | |
|---|---|
| Time | six months, from the first project built in claude.ai to the method in its current form |
| Operating manual for Claude Code | 4,520 lines, with a catalogue of twenty verification and five architecture patterns |
| Working instructions for claude.ai | a full project prompt of 43 rules, reviewed over five rounds by an independent model |
| The method's own tooling | 66 automated tests, all passing |
| Versions of the method | eleven, from version 1 to version 2.1 |
| Written feedback | 22 reports, from the projects and from independent reviews |
| The six projects | 1,303 commits: 927 in the five products, 376 in the method |

Figures read on 8 October 2026; tests and versions on 10 October.

## The six projects

The five products are public; their test counts were taken on 8 October 2026 by running each
suite on a fresh clone of the public repository. The method is private: this repository presents
its architecture, principles and results.

| Project | What it does | Tests in the public repository |
|---|---|---|
| [SkyRoll](https://github.com/Mihai-Streanga/SkyRoll-public) | Monthly payroll verification: every figure recomputed independently, guards that stop a run on a bad input file. The public repository shows the architecture and a demonstration engine on synthetic data. The first project, designed in claude.ai. | 50 |
| [Agent 051](https://github.com/Mihai-Streanga/Agent051-public) | Reads job alert emails, checks every listing against your own criteria and ends with a short briefing of what is new and relevant | 451 |
| [JA.S.Mine](https://github.com/Mihai-Streanga/Jasmine-public) | A personal assistant that runs full-screen on a Windows laptop, with rooms for mail, news, a log of facts and three conversation styles | 49 checks in four suites, plus an integration test with Agent 051 |
| [Iris](https://github.com/Mihai-Streanga/Iris-public) | Local voice dictation for Windows: speech recognition on your own machine, text typed wherever the cursor is | 31, plus a corpus of recorded clips with an automatic verdict |
| [Mih.AI](https://github.com/Mihai-Streanga/DigitalTwin-public) | A personal digital twin: a local web app where you talk, by keyboard or by voice, with a model prompted from one person's writing | 23 |
| [The method](docs/ARCHITECTURE.md#5-the-sixth-project-a-method-that-improves-itself) | The method itself, run as a project: eleven versions, its own alignment, audits and toolkit, and the feedback loop that improves it | 66, in its private repository |

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
- **[Case study](docs/CASE_STUDY.md)** — the six projects on the method: cost, verification,
  rules, quality and the method's own evolution, with the numbers and how they were taken.

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
