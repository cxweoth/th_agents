---
name: comment-brevity
description: Write the succinct and compact comment that still lands, cut anything the code already says, and move anything long into a design doc with a pointer.
---

A comment has to earn its lines. Default to one. The test is not "is this
true", it is "does the next reader need this, and is this the shortest form
that still lands".

**Cut anything the code already says.** A comment that renames the line below it
is worse than no comment, because it is a second thing to keep in sync and
nothing will fail when it drifts. If the comment restates the code, the fix is
usually a better name, not a better comment.

**Length ladder**, in order of preference:

1. **No comment.** The name says it.
2. **One line.** The common case. A trap, a unit, a non-obvious constraint.
3. **Two or three lines.** A real hazard that costs a reader an hour, or a
   rejected alternative that someone will otherwise try again.
4. **Anything longer moves out.** Put it in the design doc and leave a one-line
   pointer to it. A ten-line block in a source file is a design note that landed
   in the wrong place.

**One rare exception: a comment that carries evidence may be long.** Measured
numbers, a rejected alternative with the reason, a workaround with the
constraint that forces it. These are long because deleting them causes a real
regression that no test would catch. They are rare. When you write one, say in
the comment itself what breaks if it is removed, so the next person cutting
comments can tell it apart from padding.

**Docstrings**: one line saying what it returns or does. Add lines only for
things the signature cannot carry, a precondition, a side effect, which thread
it runs on. Do not restate the parameters, and do not write a parameter table
for a three-parameter function.

Brevity is about length, not content. It composes with the separate rule about
what belongs in a comment at all, meaning "why is it this way and what breaks if
it changes", rather than "what used to be here", which belongs in version
control.

Done when no comment restates the code, every comment is the shortest form that
still lands, anything longer than about three lines has either moved to a design
doc with a pointer left behind or states what breaks if it is deleted, and
docstrings carry only what the signature cannot.
