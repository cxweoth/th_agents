# What earns a place in `skills/`

Drafted 2026-08-07 by Planner, for TH to edit. The judgement is TH's; this file
only makes the judgement repeatable.

## Why this file exists

The eight skills currently here grew out of a side conversation with the dozo RA
on the Windows machine. They work. But nothing records **why** they earned a slot,
which means nothing can tell us when one has stopped earning it, and nothing tells
a future proposal what it has to clear.

There is no "skills owner" role and there should not be one. The pattern that
already works in this system is `northstar-bridge/docs/drift-protocol.md`: nobody
is a drift officer, the protocol simply requires every report to declare its own
deviations, and the RAs check themselves. This file is the same move applied to
agent configuration.

Anyone who hits a real friction can propose a skill: TH, Planner, or a project RA.
The bar is below.

---

## The five criteria

A proposal must clear all five. Failing one is a reason to not add it, not a reason
to argue harder.

### 1. It fires on a real, recurring friction

Name the friction and give at least two dated instances where it actually happened.
Not "replies could be clearer" but "on 2026-08-04 and 2026-08-06 the decision was
buried in the middle of a long reply and TH had to scroll back to find it."

A skill written for a friction that has not happened yet is a guess, and guesses
accumulate into a config nobody can reason about.

### 2. It is falsifiable

You must be able to look at an output and say whether the skill was followed. If
two readers would disagree, the skill is a mood, not a rule.

Test: write down what a violation looks like. If you cannot, stop here.

### 3. It changes behaviour rather than describing good behaviour

`reply-shape` changes behaviour: it moves the decision to the bottom, which is a
different physical arrangement of the text. "Be clear and helpful" describes good
behaviour and changes nothing, because the model already believes it is being clear
and helpful.

Test: could an agent that is already trying its best still fail to comply by
accident? If no, it is a description.

### 4. Its cost is proportional to its value

Anything loaded on every turn has to earn that. The cheap lever already in
`settings.json` is `skillOverrides: name-only`, which keeps a skill's name in
context and loads the body only when invoked. Six of the eight use it.

Ask: does this need to be resident, or is a name enough? Default to name-only.
A skill that must be resident needs a reason stated in the proposal.

### 5. It does not conflict with an existing skill

Check the current set before proposing. Two skills that pull in different
directions produce worse output than either alone, and the conflict usually
surfaces months later as "the agent ignores this rule sometimes."

If it overlaps, the right move is often to edit the existing skill rather than
add a second one.

---

## Evaluating a skill with one user

A/B testing does not work here. There is one user, the tasks are never comparable,
and a newly installed rule always feels effective for the first week. Anything
claiming an A/B result on n=1 is measuring novelty.

What does work is the discipline already used for experiments in this system:
**pre-register, run for a fixed period, review honestly.**

1. **Before installing**, write one sentence: *what should visibly change, and in
   what kind of situation.* Be specific enough that "it did not change" is a
   possible finding.
2. **Run it for a fixed period.** Two weeks is usually enough for a reply-level
   skill; a code-level skill may need to wait for the next real code task.
3. **Review against what you wrote**, not against how it feels now. Include the
   boring outcome: "no visible difference" is a result and it is the most common one.
4. **Keep or remove.** Do not let it drift in an undecided state, which is how a
   skill list turns into sediment.

Record the pre-registration and the review in the same commit message or in the
skill's own file. If it is not written down, step 3 becomes a memory test and
memory will confirm whatever you hoped for.

---

## Removal

A list that only grows gets blunter. Remove a skill when any of these hold:

- The friction it addressed no longer occurs, and has not for a while
- It has been silently violated repeatedly with no consequence, which means it is
  not load-bearing
- It has been superseded by a better-scoped skill
- It fails criterion 4 in practice: the context it consumes is not returning value

Removal is cheap and reversible: git history keeps it. Treat removal as
maintenance, not as admitting a mistake.

---

## Worked examples

### Passes: `reply-shape`

1. **Real friction**: TH reads the last block first, and decisions were being
   buried mid-reply.
2. **Falsifiable**: either the reply is ordered Check / Conclusion / Plan / Decision
   with `---` separators, or it is not.
3. **Changes behaviour**: it is a physical rearrangement, not an exhortation. An
   agent trying its best still gets the order wrong without the rule.
4. **Cost**: name-only. The body loads when invoked.
5. **No conflict**: `decidable-questions` governs what goes in the decision block;
   `reply-shape` only governs where that block sits. The two are explicitly
   scoped against each other inside the skill itself.

**Observed effect (TH, 2026-08-07)**: 「我做決定還有清楚度有上升」. Note that this is
one user's impression after one day, which is exactly the kind of evidence the
review process above is designed to distrust. It should still be reviewed at the
end of a fixed period.

### Fails: a hypothetical "be concise" skill

1. Friction is real (replies do run long), so it passes 1.
2. **Fails 2**: two readers will disagree about whether any given reply was concise.
3. **Fails 3**: it describes a preference. Every agent already believes it is being
   concise.

The fix is to convert it into something falsifiable and behavioural, which is what
`reply-shape`'s Length section already does: say each thing once, no `##` headings,
and a stated cut order when it runs long. That is a rule you can check.

---

## Proposing a skill

Open a PR or just write the file, with a short block at the top of the proposal:

```
Friction:        what keeps going wrong, with two dated instances
Violation looks like:  how you would know it was ignored
Behavioural?     what an agent doing its best would still get wrong
Cost:            resident or name-only, and why
Conflicts:       which existing skills it touches
Pre-registration: what should visibly change, and by when it will be reviewed
```

Six lines. If the six lines are hard to write, the skill is not ready, and that is
the point of the form.
