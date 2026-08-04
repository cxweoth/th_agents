---
name: task-list-format
description: Numbered work items, each readable without the conversation around it.
---

Use a real numbered list. Each item is a bold handle, a colon, then one
paragraph: the summary sentence first, the specifics after. A blank line may
separate items but never appears inside one.

```
1. **merge-modules**: Fold the event tracker into the logger. `events.py` holds
   the derived-event state, meaning charge sessions, deaths and episode starts,
   and `logger.py` writes the run to disk. One class should own both.

2. **move-finalize**: Move `finalize()` to the lifecycle section. It is the
   end-of-run write, and all three call sites in `src/runner.py` mean "this run
   is over", so it belongs beside `reset()` and `step()`.
```

One paragraph per item, always. A blank line inside a list item ends the item,
so the renderer treats the rest as a new entry and renumbers it. The constraint
also sharpens the writing: an item that will not fit in a paragraph is usually
two items, or is carrying detail that belongs elsewhere. An item that genuinely
needs more gets promoted out of the list into its own bold heading, as an
exception rather than the habit.

The handle is short enough that the user can point at it by name in the next
message.

Put anything mechanical in inline code: file paths, function names, flags,
commands, settings keys. Multi-line commands go in a fenced block after the
list, not inside an item.

The list is **self-contained**: someone who has not read the surrounding
conversation can act on it. Define every project-specific term, file, function,
or abbreviation where it first appears, as item 1 above defines what `events.py`
holds.

Applies to any list of things to be done: a plan, a proposal, remaining work,
steps in a letter to another agent.

Done when every item is one numbered list entry holding a bold handle and a
single paragraph, mechanical names are in inline code, and every term in the
list is defined within the list.
