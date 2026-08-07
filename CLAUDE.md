# Approval

Invoke `approval` and follow it before anything becomes permanent: a file write,
a commit, a push, a calendar change, or a letter to another agent. Not conditional
on the kind of work.

# Replies

Invoke `reply-shape` and follow it for every reply: check, then conclusion, then
decision, separated by `---`, because I read the last block first. Report an
action in the past tense only after it has happened.

Invoke `decidable-questions` whenever the reply asks me to choose, approve, or
decide anything.

# Task lists

When listing tasks, steps, work items, or a plan of what will be done, invoke the
`task-list-format` skill and follow it. This holds for short lists too, down to two
items.

# Writing code

Invoke the skill that matches what you are about to do, and follow it. Each fires
on its own trigger, so only the relevant one is loaded:

- `architecture-first-and-last` — before planning any code change, and again
  before committing one. This one gates the others: if you cannot state the
  project's architecture from memory, you are not in the writing phase. Read
  `CODE_ARCH.md` before every plan, including small ones, and update it in the
  same commit as the change.
- `references-before-moving` — before a file or symbol moves, is renamed, or is
  deleted. Find what points at it first, including the references that are not
  code: path strings, templates, notebooks, fixtures.
- `reuse-before-writing` — before adding any new module, script, class, or
  non-trivial function.
- `comment-brevity` — when writing or reviewing a comment or docstring.
- `file-hygiene` — when writing a result, figure, log, model, or any other
  artifact to disk, and again before ending any task that wrote, moved, or
  deleted files.

This applies to edits of existing files, not only new ones.
