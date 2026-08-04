---
name: reuse-before-writing
description: Find the module, script, class or function that already does the job, and extend it. Look outside the project too, and judge whether an existing library fits before carving your own.
---

Before writing anything new, look for the thing that already does it. Two
sources, in this order: the code in this repo, then the libraries already in the
dependency list.

Search the repo by what the code **does**, not by the name you were about to
give it. The existing version will not be called what you would have called it.
Grep for the operation, the output filename, the library call it must wrap, the
config key it must read. A near-duplicate written under a different name is the
single most common way this rule gets broken.

When something close exists, **the default is to generalize it, not to copy it.**
Adding a parameter to an existing function beats a new function that shares most
of its body. A near-duplicate is a second source of truth: it does not break on
the day it is created, it breaks the day someone fixes a bug in one copy, and
both copies still run.

Generalizing is the wrong answer in three cases, and only these:

1. **The shared part is coincidence.** Two functions that happen to look alike
   today but answer different questions will diverge, and the merged version
   grows a flag per divergence. Similar shape is not the same job.
2. **The parameter would change what the function means.** A flag that makes one
   function do two things is two functions wearing one name. A flag that selects
   a value, a path or a format is fine.
3. **The existing one is load-bearing for results already produced.** Extending
   it changes numbers that are already reported. Then the honest move is a new
   one plus a note saying which runs used which.

**Never reimplement what a library already provides.** If the standard library,
or a package already in the dependency list, does it, use that. A hand-rolled
version is untested, misses the edge cases the library was patched for, and is
slower for no benefit. This applies hardest to the things that look easy: date
parsing, path handling, atomic file replacement, statistics, argument parsing,
retries, JSON streaming.

**Look outside the project before carving your own.** The repo and the installed
dependencies are the first two places to look, not the last. Search for what
already solves this, read what it actually covers, and judge the fit: how mature
it is, whether its scope matches yours, what it would pull in, what it would
constrain. Adding a new dependency needs the user's OK, so bring that judgment
while the design is still open, with what you found and why it does or does not
fit.

Hand-rolling can be the right call. What goes wrong is when it was never a call
at all: the first version gets written because writing it was the nearest move,
nobody compared it against what exists, and the gaps show up one bug at a time.

**Say what you found.** When you reuse something, name it. When you add a new
module despite a close existing match, name the match and say why extending it
was wrong, in terms of the three cases above. That judgment is the thing worth
reviewing, and it is invisible unless stated.

Done when nothing new duplicates behaviour that already exists in this repo or
in an installed dependency, anything substantial has been checked against what
exists outside the project with the fit judged out loud, and any new module names
the closest existing thing and says why it was not extended.
