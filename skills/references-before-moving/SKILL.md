---
name: references-before-moving
description: Before a file or symbol moves, is renamed, or is deleted, find everything that points at it and account for each one.
---

Applies to the structural changes already listed in `architecture-first-and-last`:
a file added, deleted, renamed or moved; what a file owns changing; an import
edge changing; a boundary crossing moving. Logic inside a function, a constant,
a bug fix or a comment triggers nothing.

**Before the move, list what points at the thing.** Not after, and not from
memory. The list goes in the change description, and every entry is either
updated in the same change or marked as deliberately left alone, with a reason.

## Where to search

Searching the symbol name finds the imports. **The breakage comes from the
references that are not code.** Search all of these, because each fails
differently and none of them fail at the moment of the move:

- the symbol name, for imports and call sites
- **the file path as a string**, for config, build files, scripts and CI
- the file or module name without its extension, for dynamic imports and loaders
- templates, UI files and notebooks, which reference by path and are not compiled
- test fixtures and data files loaded by name

The last three are where the expensive misses live. Nothing in them fails when
the file moves. They fail the next time someone runs that path, which may be a
different person on a different day, and by then the move no longer looks like
the cause.

## Accounting for each one

For each reference: updated here, or left alone and why. An unlisted reference
and a reference that did not need changing look identical afterwards, which is
why the second one has to be said out loud.

Done when every reference to the moved thing appears in the list, each is marked
updated or deliberately unchanged, and the search covered string paths and
non-code files rather than the symbol alone.
