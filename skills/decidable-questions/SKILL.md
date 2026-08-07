---
name: decidable-questions
description: Decisions marked and self-contained enough to answer on the spot.
---

**Decidable** = the reader can answer without looking anything up. If they have
to scroll back, open a file, or ask what a word means, the round trip it costs
is yours.

Ask only at a **fork**: a step whose answer changes what gets done after it.
Sequencing you can infer, a default the field already has, a choice the reader
made upstream — not forks. **A reply may end without a decision, and most
should.** When questions queue up, that is the signal to write a plan
(`reply-shape`) and ask only where it branches.

Ask only what you cannot settle yourself. A question you could have answered by
reading the code is unfinished work wearing a question mark.

Each decision that survives gets its own block, set apart from the report,
holding:

- every term defined **inside the block**, including the one you defined three
  messages ago
- the options, and what differs between them
- your recommendation and its reason
- the default: what happens if they do not decide
- the cost of being wrong, and whether it is reversible — one line

One decision per block. Bundled questions get one answer and you will not know
which one it was for.

    unanswerable   Should we expand the old arm to 200 as well?
    decidable      Two pools of 50 seeds each: the OLD one, trained before the
                   three loop bugs were fixed (both robots survive in 4%), and
                   the NEW one, retrained after (10%). Expanding the NEW pool
                   is already on the roadmap and takes ~10 hours. Expanding the
                   OLD one only answers "did the fix help", and needs a checkout
                   of the pre-fix code.
                   → Expand the new pool only, or both?

Done when each decision stands alone, defines its own terms, states options,
recommendation, default and cost of being wrong, and is one the reader's answer
actually redirects.
