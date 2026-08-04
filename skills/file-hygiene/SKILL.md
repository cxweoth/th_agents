---
name: file-hygiene
description: Take responsibility for what a file is called, where it goes, and what state you leave it in.
---

Every directory and file written to disk must be identifiable **from its name
alone**, by someone who was not in the conversation that produced it. That
someone includes you, six months from now, and anyone reading the repo without
the thread that named it.

**Name for the content, not for the run or the order it was made in.**

    fig3.png                        exp_b_v2/              out.json
    symmetric_layout_tt_box.png     frozen_agent_a/        charger_occupancy.json

**No internal codenames.** No `B1`, no `run_2`, no initials, no ticket numbers,
no abbreviations that only exist in one person's head. If decoding the name
needs the conversation, the name is wrong. The same applies to what goes
*inside*: a column called `mode_c` is the same failure one level down.

**Keep the discriminating variable in the name.** When several artifacts differ
by one thing, that thing belongs in the name and nothing else does. Five files
differing only in seed should differ only by `seed_0` … `seed_4`. Reading the
directory listing should tell you what the sweep varied.

**Categorise before the files accumulate, not after.** Directory structure
carries the grouping, so the filename does not have to: put the condition in
the directory and the content in the file, rather than flattening both into one
long name. Decide the layout when the first file is written, because renaming
later breaks every path already recorded in a config, a log or a report.

**Place into the structure that already exists.** Before writing, look at where
sibling artifacts live and put this one with them. Starting a new location next
to one that already fits is how a tree turns into a pile: every single decision
looks reasonable, and a flat directory of sixty items is what they add up to.
If nothing fits, say so in the reply instead of quietly opening a new category.
That is a decision, and it is the user's.

If the project defines an output schema or layout, that wins over anything here.
Follow it, and if the artifact does not fit it, say so rather than inventing a
sibling convention next to it.

Mechanics: lowercase, underscores, no spaces, no characters that need quoting in
a shell path. Dates as `YYYYMMDD` so they sort. Do not put a timestamp in the
name unless time is the discriminating variable, since a timestamp is exactly
the kind of name that carries no meaning.

**Say where you put it.** Every time an artifact is written, give its full path
in the reply. A file nobody can find was not delivered.

**Scratch goes to the session scratchpad, not into the repository.** A file that
was never written into the working tree needs no name, no home, and no
explanation later: intermediate data, trial scripts, extracted text, one-off
analysis output.

## Before the task ends

A well-named file in the right directory can still be litter. The other half of
the responsibility is what state you leave it in, and that is checked at the end,
not while writing.

Look at what you wrote — `git status` where there is a repository, the list of
paths otherwise. Every file **you** touched is in one of three states:

- **committed** — it is part of the work
- **deliberately ignored** — covered by `.gitignore` on purpose, and you can say
  which rule
- **deleted** — it was scratch and it is gone

Anything of yours outside those three gets named in your reply with one line on
why it stays. A stranded file reads as work-in-progress forever: six months on,
nobody can tell whether the patch was applied, whether the log mattered, or
whether that figure was the final one.

**Account only for what you touched.** In a shared repository other people's
untracked files are their work in progress, not litter. Report them if they look
stranded, and leave them alone.

Done when every path written can be understood from the path alone, the
discriminating variable is in the name, related artifacts share a directory
rather than a filename prefix, every path has been reported to the user, and
every file you touched has been left in one of the three states above.
