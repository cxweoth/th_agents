---
name: reply-shape
description: Check, then conclusion, then decision, with every claim labelled by how it is known.
---

The reader reads from the bottom up. The last block is the first thing seen and
often the only thing. Order every reply accordingly:

    Check
    ---
    Conclusion, status at its end
    ---
    Decision

Label each section: the words Check, Conclusion and Decision in bold, each on
its own line at the top of its block.

A `---` goes between two sections only when both are there. No check section
means no `---` above the conclusion; no decision means none below it, and the
conclusion is the last thing on screen.

## Check

What you checked before answering, and for anything you are about to ask, what
you tried before asking. Four lines in total, as bullets, not prose. If you
checked nothing there is no check section: say in the conclusion that it is a
judgement, rather than padding this block with reasoning.

**Say what you did not check.** Whenever you know of a layer next to the one you
looked in, name it, marked, on one of those lines. Looking in one directory
leaves the sibling directories; counting in one file leaves the other files; a
tool that answered leaves the question of what else produces that answer.

    checked the base condition has no n50 pool; did NOT look under the other
    conditions, and that is where it was

Without this the block reports only what was looked at, so four verified lines
read as "this was verified", and the reader cannot see the dozens of things
beside them that nobody looked at. That gap is invisible by construction: it is
the one thing a record of your work will never contain unless you put it there.

## Conclusion

The finding, stated once, in the first sentence of this block. Reasons follow
it; evidence follows them.

Mark how each claim is known. The three are not interchangeable, and stating one
as another is the failure this exists to prevent:

- **measured**: a number that came out of a run, a grep, a test. Name where it
  came from.
- **derived**: computed from other numbers. Say so, and from what. A derived
  number worn as a measured one gets acted on with confidence it has not earned.
- **guessed**: a judgement with nothing behind it. Say so and stop; do not
  dress it in a number.

When the data cannot settle a question, say it cannot, and name what would.
"No difference" and "not enough data to see a difference" are different claims,
and only one of them is usually true.

Disagreement leads with the other position stated accurately, then the specific
point of departure. Restating it wrong first makes the rest unreadable.

Status lines end this block, and only when the reader asks, or when a thread
changed hands, or when something finished. Not every reply. Three lines:

    done      what just finished, one line
    where     where that sits in the whole task, e.g. 3 of 12, batch 1 of 2
    next      whose move it is, and whether the reader is blocked

`next` names a state, not a routing: **working** (carrying on without input),
**blocked** (nothing moves until they answer), **waiting** (someone else owes
something and you have other work meanwhile), **done** (the whole task, not this
step). With several threads open, one line per thread, and mark which are
blocked.

## Decision

Last, and standing alone. This block is the one place repetition is correct.

Never point upward, and that starts with the question itself. A demonstrative
(this, that, the three, the above) has its meaning outside the block, so the
reader is sent scrolling before reaching the options. Name the subject in the
question, and write each option out in full.

The test: read the block with everything else covered. Any noun that needs the
rest of the reply is a pointer, whether or not you wrote the word "above".

When you are unsure what the reader meant and a lot of work rides on it, that
reading *is* the decision block: state how you understood them and ask before
starting. It does not go at the top, because a misunderstanding declared where
nobody looks is not a checkpoint.

`decidable-questions` governs what goes in this block. This skill only fixes
where it goes.

## Length

Say each thing once, in one place. Keep the stronger of a bold lead and the body
that repeats it. **No `##` headings in a reply**: a bold-led paragraph is the
largest unit, which caps duplication at two levels instead of three.

When it runs long, cut in this order:

1. restatement
2. qualifications that do not change what the reader does
3. alternatives you are not recommending; the options inside a decision block
   are required and are not alternatives in this sense

Never cut a number, a file path, a counter-example, or an assumption you are
relying on. Those carry the most and cost the least, and cutting them is how
brevity turns into vagueness.

Scope: conversation only. Letters to other agents, files under `shared/`,
reading reports and bridge reports keep their own formats. Where a project
mandates PREP for written reports, PREP keeps those and this keeps the
conversation.

Done when the reply is in that order, every section present is labelled and
separated by a `---`, the last block stands alone, every claim says how it is
known, and no fact appears at two levels.
