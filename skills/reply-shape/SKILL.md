---
name: reply-shape
description: Check, then conclusion, then plan, then decision, with every claim labelled by how it is known.
---

The reader reads from the bottom up. Order every reply:

    Check
    ---
    Conclusion, status at its end
    ---
    Plan          (work of more than one step)
    ---
    Decision      (a real fork only)

Bold the section name at the top of its block. A `---` only between two blocks
that are both present.

**Check** — four bullets: what you checked, and for anything you are about to
ask, what you tried before asking. One bullet says what you did **not** check:
the layer beside the one you looked in whose answer would have changed the
conclusion, not the first unchecked thing that comes to mind.

    checked the base condition has no n50 pool; did NOT look under the other
    conditions, and that is where it was

Checked nothing? Then no Check block: say in the conclusion that it is a
judgement.

**Conclusion** — the finding in the first sentence, reasons after it, evidence
after them. Label every claim **measured** (name the run, grep or test),
**derived** (say from what) or **guessed** (say so, and do not dress it in a
number). "Not enough data to see a difference" is not "no difference".
Disagreement leads with the other position stated accurately.

End with status lines when a thread changed hands or something finished, not
otherwise:

    done      what just finished
    where     where that sits in the whole task
    next      working | blocked | waiting | done — one line per open thread

**Plan** — the path from here to the thing being built, in `task-list-format`.
Mark which steps are forks; say what each step is waiting on. A plan not written
down is not held across turns.

**Decision** — last, standing alone, governed by `decidable-questions`. Not
every reply has one. No demonstrative pointing outside the block: read it with
everything else covered, and any noun that needs the rest of the reply is a
pointer.

**Length** — say each thing once. No `##` headings. When it runs long, cut
restatement, then qualifications that change nothing the reader does, then
alternatives you are not recommending. Never cut a number, a path, a
counter-example, or an assumption you are relying on.

Scope: conversation only. Letters to other agents, files under `shared/` and
reading reports keep their own formats.

Done when the reply is in that order, each block present is labelled, every
claim says how it is known, and multi-step work carries a plan with its forks
marked.
