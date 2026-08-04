---
name: architecture-first-and-last
description: Read CODE_ARCH.md before planning any code change, and update it in the same commit whenever a file moved, what a file owns changed, an import edge changed, or a boundary crossing moved. Use before planning or writing code, and again before committing one.
---

**Two moments, and the second one is the one that gets skipped.** Read
`CODE_ARCH.md` before the plan; update it in the commit that changes the code.
Skipping the first is loud — you get stuck, or you place something badly and
someone says so. Skipping the second is silent: nothing breaks today, and the
next person plans against a description that is no longer true.

**The gate.** Before writing or editing code, you must be able to answer, without
looking: what the layers are, which way the dependencies point, which file owns
the thing you are about to touch, and what breaks if you put it in the wrong
place. If you cannot, **you are not in the writing phase yet.** Stop, say so,
and do the analysis.

Guessing placement is the expensive kind of wrong. A function in the wrong
module still runs, still passes tests, and costs its price later as a circular
import, a duplicated helper, or a layer reaching into one it should not know
about. Nothing fails at the moment the mistake is made, which is exactly why it
has to be prevented rather than caught.

## The analysis

Read the code. Do not infer the architecture from filenames, the README, or a
directory listing, because those describe the intent and the code describes what
is. Follow the real entry points from the top: the CLI, the main loop, the
request handler, the test fixtures.

Write the result to **`CODE_ARCH.md`** at the root of the workspace you write
code in.

## Shape: a short part that is read, a long part that is searched

This split is the whole design. Keep them apart and neither one grows into the
other.

**The head is read before every change, and must stay under about 40 lines.**
Four things, in this order:

1. **What the system does**, one paragraph, plain words.
2. **Layers and direction**, at most five lines. Which way dependencies point,
   and the specific edges that are forbidden. Record only what is true today.
   If the project has no enforced layering, write that instead of inventing one:
   a described boundary that does not exist is worse than an admitted absence,
   because it will be cited.
3. **Seams**, at most five lines. Where control or data crosses a boundary:
   threads, processes, I/O, a framework's callbacks. These are where the
   expensive bugs live and where a placement mistake is least reversible.
4. **Placement guide**, the questions to ask to land on one filename. Not a list
   of cases.

**The table is searched, never read end to end**, so its length does not cost
anything. One line per file, and one line is a hard limit:

    path | status | what it owns, and what it must not do

Anything that will not fit on the line does not belong in this file. The limit
is the mechanism, not a style preference: the moment the table stops being
scannable it stops being consulted, and an unconsulted document drifts.

**`status` is one of four**, and this column is why the table is worth having:

    live     on a path that current runs execute
    parked   kept deliberately, not executed now
    dead     nothing reaches it; belongs in the cleanup backlog
    tool     standalone analysis or verification script, not part of the system

Without it, parked and dead code reads as current architecture and the next
person places new work next to it.

## Using it

**Read the head before every code plan**, including small ones. The plan names
the file each change lands in and why that file owns it. If it cannot, the
analysis is incomplete, not the plan.

**Search the table before writing anything new.** It is the index that
`reuse-before-writing` needs: scanning one line per file for what already does
the job is faster than grep and it covers the standalone scripts, which is where
near-duplicates actually get written. This is also what keeps the document
honest, since a table that gets consulted daily has its drift noticed.

**Keep it current in the same commit as the change.** A document that gets
followed is as load-bearing as code: when it is wrong, the next person writes
the wrong thing, and nothing fails. If the code and the file disagree, the code
wins and the file is fixed immediately, not added to a backlog.

**What counts as a trigger.** Do not re-decide this per change; it is a
checklist, and the point of a checklist is that it is not re-argued:

1. A file added, deleted, renamed or moved → its row.
2. What a file owns, or what it must not do, changed → its row.
3. A status changed (live / parked / dead / tool) → its row.
4. An import edge between packages added or removed → **Layers and direction**.
5. A boundary crossing added, removed or moved: a thread, a process, an I/O
   point, a framework callback → **Seams**.
6. A new kind of thing now has an obvious home, or lost one → **Placement
   guide**.

Everything else — logic inside a function, a constant, a bug fix, a comment —
triggers nothing. If a change touches none of the six, say so rather than
leaving it unstated, because "the document was not updated" and "the document
did not need updating" look identical afterwards.

**Describe structure and responsibility, never behaviour detail.** Line numbers,
parameter lists, algorithms and constants belong in the code, and copying them
here creates a second source of truth that drifts silently. The test is whether
a routine refactor would invalidate the sentence. If yes, it does not belong.

**State the gaps.** What you did not read, and what did not fit the description,
goes at the bottom in plain words. An admitted gap is useful; a smoothed-over one
is a trap.

Done when the head is under 40 lines and covers the four things, every code file
has one line in the table with a status and what it owns, nothing in the file
would be invalidated by a routine refactor, the gaps are stated, and the current
plan names the owning file for each change and justifies it from the head.
