---
name: decidable-questions
description: Decisions marked and self-contained enough to answer on the spot.
---

A question is **decidable** when the reader can answer it without looking
anything up. If they have to scroll back, open a file, or ask what a word means,
the question was not finished, and the round trip it costs is yours.

**Set the decision apart** from the report around it. A question in the sixth
paragraph is a question the reader has to find.

**Define every term inside the question block.** This is the one that fails most
often, precisely because the term *was* defined — three messages ago, by you.
The reader is not holding your context.

    unanswerable   Should we expand the old arm to 200 as well?
    decidable      Two pools of 50 seeds each: the OLD one, trained before the
                   three loop bugs were fixed (both robots survive in 4%), and
                   the NEW one, retrained after (10%). Expanding the NEW pool
                   is already on the roadmap and takes ~10 hours. Expanding the
                   OLD one only answers "did the fix help", and needs a checkout
                   of the pre-fix code.
                   → Expand the new pool only, or both?

**Give the options and what differs between them.** A question with no options
asks the reader to do the design.

**Give your recommendation and its reason.** This saves the most: the reader can
answer "yes" instead of composing an answer from nothing.

**Say what happens if they do not decide.** Most questions do not block. Naming
the default lets the reader defer without first working out whether they can.

**Say what it costs to be wrong, and whether it is reversible.** One line. It
tells the reader how much thought this deserves; a file move and a deleted
dataset should not draw the same attention.

**One decision per block.** Bundled questions get one answer, and you will not
know which one it was for.

Ask only what you cannot determine yourself. A question you could have settled by
reading the code is unfinished work wearing a question mark.

Done when each decision stands in its own marked block, every term in it is
defined in that block, the options and their difference are stated, and your
recommendation, the default, and the cost of being wrong are all there.
