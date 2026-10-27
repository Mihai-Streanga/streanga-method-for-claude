# Principles

The ten principles the Streanga Method is built on. Each one says what it asks for, why, and the
real situation it came from: every principle below was earned on one of the projects built
with the method, the method itself included, and each changed how those projects work.

They hold on both surfaces. In claude.ai, every conversation starts with its stopping condition
(1), facts are searched or marked as unverified (3), the brief separates what code can verify
from what only the author can judge (5), the finished brief is tested in a fresh chat that sees
only the document (6), and nothing counts until it is written to a file (10). In Claude Code,
all ten apply, and several are held by a mechanism.

## 1. Write the stopping condition before you start

Anything that can be repeated (a rewrite, a review, a round of generation) gets a written
condition for "done" before the first attempt: what counts as accepted, how many tries, and what
happens when the tries run out. Work then ends because the result meets the condition, and a real
"good enough" can be told apart from a tired one.

*Where it comes from:* an early technical specification went through about thirty rewrites with no
definition of "finished", and an image generation task ran for two days on a path that could not
succeed. Both had the same missing piece. Since then every repeatable task in the method opens with
its acceptance condition, and a specification is written to it from the first draft.

The condition holds when the result disappoints. On HarnessCraft, the rules for each calibration
round were fixed before the round ran. A code-quality measure then matched the author's blind
ranking on 8 of 12 projects, against a threshold of 10 set in advance; it stays in the report as
information, outside the score, and the threshold stayed where it was.

## 2. Rules that matter are enforced by a mechanism

A rule written in the agent's instructions is followed most of the time. A rule that matters is
also held by something that cannot forget: a permission the agent does not have, a check that
stops a commit, a test that fails. When a written rule keeps being missed, it moves into a
mechanism.

*Where it comes from:* the five products were audited against their own rules. Rules that existed
only as text had been missed 26 times across the five; rules backed by a mechanism, never. On one
project the commit message convention went from 20 misses out of 20 commits to 0 out of 39 once a
tool enforced it. On another, a shell quoting trap that had damaged file paths three times in two
days stopped completely the day it became an automatic check.

## 3. Measure, then decide

A number that drives a decision comes from a measurement, run and reproduced, and the measurement
is named next to the number. Estimates and readings of source code are recorded as what they are.

*Where it comes from:* a cost estimated at 2,261 tokens measured 845. In another case, a share
predicted at 59% from a constant in the tool's own code measured 12%, because other branches of
the code applied first. Both decisions were taken on the measured value, and the method now asks
for the measurement before the decision.

## 4. A mechanical check proves exactly what it checks

A list of forbidden words, a pattern search, a passing linter: each answers one precise question.
So every report of a check says what it covers and what it leaves to a person, and "nothing found"
is read as "nothing found by this check".

*Where it comes from:* a writing guide's word list came back clean on a document that still broke
the guide's main rule about meaning in 66 places. The answer was a second search, for the sentence
shapes the rule produces, run alongside the word list. Together they caught what the list alone
could not.

## 5. Decide verification per area of the work

Different parts of a project are proven in different ways. Voice, design and tone are judged in
use, by a person. Arithmetic and data transformations are proven by code that recomputes them
independently, every time. The choice is made area by area.

*Where it comes from:* SkyRoll, the payroll verification project, was designed in claude.ai with
verification built into its engine: 71 independent recalculations and numbered guards that stop
a run on a bad input. Those checks ran whenever the tool ran, but nothing re-ran them when the
code changed. Deciding verification area by area made the gap visible, and because the criteria
were already in the code, a suite of 410 automated tests was written directly from them. Any
change to the arithmetic can now be checked against all of them with one command.

## 6. A second instance with no shared context catches real errors

The instance that did the work reads the result through its own intention. Work that matters is
judged by a second instance that has only the result in front of it.

*Where it comes from:* the working instructions for the claude.ai side of the method were given to
a colleague's model that had never seen the conversation that produced them. Over five rounds it
raised 17, 21, 13, 14 and 14 points, among them pairs of rules that asked for different things in
the same situation. Each of those conflicts was resolved, and independent review is now a
standard step for work that matters.

## 7. Inventions need somewhere to travel to

A good solution found in one project stays there unless there is a place it is carried to and a
route back from every project to that place. The method is that place: projects report what they
learned, and the method changes on that evidence.

*Where it comes from:* a factual audit of the five products found their best inventions — a test
suite running in under two seconds, a versioned test corpus with an automatic verdict, a cost
counter for paid API calls — each living in one project, or two at most. Through the method, a
test suite now runs in every project, and the cost counter in every one that calls a paid API.

The route works fast. On 1 October 2026 a quality review of JA.S.Mine found defects that every
other check had passed; the same day, the kinds of defect it found became a standing part of the
method's quality review. Four days later, that addition found the same kinds of defect on
SkyRoll, and they were fixed the same day. Thirty-eight written reports and conversation records
have travelled this route so far, and the method's versions up to 3 are what they produced.

## 8. A method must be able to lose rules

Everything written into a method adds to it. A method that can also retire rules stays readable
and useful as it grows. A rule is retired with its reasons written down, so it is recognised if
someone proposes it again.

*Where it comes from:* a measurement instrument was retired after three cycles, with its reasons
on record: it had been used up by its own construction, its threshold came from outside, and
maintaining it cost as much as what it measured. What was still worth measuring is now checked
with two questions instead of twenty. The method holds itself to the same rule: between version 1
and version 2.0 its manual went from 5,793 lines to about 4,500, while gaining the chat side, the
quality review and a tested toolkit; version 3 brought it to 2,826, with the files every project
copies kept as templates of their own.

## 9. The AI proposes, code computes, a person decides

Numbers and irreversible actions belong to deterministic code and to the person responsible. The
agent writes the code and explains it; the person who knows the domain says whether the result is
right, and settles the questions that analysis alone keeps open.

*Where it comes from:* a cycle of automated audit and repair was run three times, 197 calls in
total, and each full pass surfaced new points. A single round of decisions with the author closed
the eleven open points in one turn. The method now routes open questions to the person who can
decide them.

HarnessCraft is built the same way. It assesses how a candidate works with AI, yet the program
calls no AI model: every score and every interview question comes from written rules, and the
recruiter writes the conclusion.

## 10. What exists only in the conversation is lost

Decisions, findings and the state of the work are written to files and committed the same day.
The next session starts from what is on disk, because the agent carries nothing between sessions.

*Where it comes from:* a session's handover note was written in the conversation and never saved,
and a day of work had to be reconstructed from the version history. Since then the state of the
work is on disk before a session ends, in every project.

---

© 2026 Mihai Streanga. All rights reserved.
