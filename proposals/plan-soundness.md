# PROPOSAL: `plan-soundness`

Status: **not installed.** Sitting here until criterion 1 is filled in.
Proposals live in `proposals/` and only move into `skills/` once the form below
is complete. See `SKILL-CRITERIA.md`.

```
Friction:         ⚠️ BLANK. TH observed 2026-08-07 that "agent 不太會做 plan",
                  across code plans, experiment plans, and time-block plans.
                  Criterion 1 needs two dated instances, naming which kind of
                  plan and what specifically was wrong. Only TH can fill this.
                  If it cannot be filled, this proposal stops here.

Violation looks like:  A plan where no step is marked as the one that blocks the
                  rest, or where a step's output cannot be named as a thing you
                  could show someone.

Behavioural?      Yes. An agent doing its best still writes "investigate X, then
                  improve Y", because nothing tells it that a step without a
                  showable output is not a step.

Cost:             name-only. Loads when a plan is being written.

Conflicts:        Composes with `task-list-format`, which governs the shape of a
                  list and says nothing about whether the plan is sound. Partially
                  overlaps `architecture-first-and-last` for code changes; that
                  skill keeps the read-the-architecture-first rule and this one
                  does not repeat it.

Change scope:     One addition.

Pre-registration: Later plans visibly contain a named blocking step and a stated
                  exclusion. Review 2026-08-21, two weeks after install. A
                  finding of "no visible change" is a result and means remove it.
```

---

## Why one skill and not three

The three kinds of plan (code, experiment, time-block) fail in different-looking
ways, but the five rules below are the same for all three. Three skills sharing
eighty percent of their text would fail criterion 5 on conflict and criterion 4
on cost.

What is genuinely kind-specific stays where it already lives: reading the
architecture before a code change belongs to `architecture-first-and-last`, and
pre-registered criteria for an experiment belong in the experiment's own
directive. If this skill survives its review, kind-specific extensions are cheap
to add then.

---

## Draft skill text

```markdown
---
name: plan-soundness
description: A plan names what blocks it, what each step produces, when it is done, and what it excludes.
---

`task-list-format` governs how a plan is written. This governs whether it is
worth following. A plan can satisfy every formatting rule and still be a list of
intentions.

Five rules. Each is checkable by looking at the plan.

## 1. Name the step that blocks the rest

Exactly one step usually decides whether the others happen at all: a fact you do
not have, a person who has to answer, a check that could invalidate everything
downstream. Mark it.

Unmarked, a plan reads as a smooth sequence and then stalls at step three, and
the stall looks like bad luck rather than something that was visible from the
start.

## 2. Put the cheapest disqualifying check first

If some check could make the whole plan unnecessary, it goes first, however
unsatisfying that is. Order by what could kill the plan divided by what it costs,
not by what feels like the natural beginning.

    0. Can the agent's own body appear in its camera view at all?
       If not, the "it was looking at itself" reading is dead and steps 1 to 3
       are unnecessary.
    1. Is the curiosity term elevated over the window?
    2. Render what it actually saw.

Step 0 costs minutes and can retire the rest. It goes before the interesting work,
not after it.

## 3. Every step produces something you could show someone

"Investigate the logging" is not a step. "A list of every place the run writes to
disk, with the three that write outside `results/` marked" is a step.

Test: name the artifact. If the answer is a state of mind rather than a thing,
the step is not ready and usually splits into two.

## 4. State the stopping condition

What has to be true for this to be finished. Without it a plan cannot be
completed, only abandoned, and abandoned plans stay on the list forever looking
like debt.

## 5. Say what you are deliberately not doing

Name the adjacent thing that a reader would expect to see and that you chose to
leave out, and say why in a clause.

This is the same move as `reply-shape`'s "say what you did not check", and it
defends against the same failure: a complete-looking artifact whose edges are
invisible, so nobody can see the choice that was made.

## Length

A plan that needs more than about seven steps is usually two plans, or one plan
plus a pile of detail that belongs in whatever the first step produces.

Done when the plan marks its blocking step, leads with the cheapest check that
could retire it, names an artifact for every step, states what finished looks
like, and says what it leaves out.
```
