# claude-config

TH's Claude Code configuration, shared across machines. Three things live here
and nothing else:

    CLAUDE.md        the always-loaded instructions: reply shape, task lists, code skills
    skills/          8 skills, one directory each
    settings.json    skillOverrides, disableBundledSkills, permissions

## Why this is a separate repo and not `~/.claude` itself

`~/.claude/` holds `.credentials.json`, every project's conversation
transcripts under `projects/`, and a 2800-line shell history. Making that
directory a repo puts a credentials file one `git add -A` away from a remote.
The 52 KB that is worth sharing lives here instead.

⚠️ **Never add `~/.claude/projects/` to this repo.** Those are per-project
memories. Carrying one project's memory to another machine's agent injects the
wrong context, and some of those memories are written for a different agent in
the same project.

## Setting it up on a machine

`skills/` is a directory, so it links. Windows junctions need no administrator
rights (verified 2026-08-04).

```powershell
git clone git@github.com:cxweoth/th_agents.git C:\Users\th\research\claude-config

# move any existing skills aside rather than deleting them
Move-Item ~\.claude\skills ~\.claude\skills_before_sync   # skip if absent

New-Item -ItemType Junction -Path ~\.claude\skills `
         -Target C:\Users\th\research\claude-config\skills

Copy-Item C:\Users\th\research\claude-config\CLAUDE.md     ~\.claude\
Copy-Item C:\Users\th\research\claude-config\settings.json ~\.claude\
```

Check it took: `(Get-ChildItem ~\.claude\skills).Count` should print 8.

## The two files are copies, not links

`CLAUDE.md` and `settings.json` are files, and a junction only spans
directories. A hard link would work until an editor saved by replacing the file
rather than writing in place, which is the common case, so they are copied.

**After editing either one, copy it back here and push.** `skills/` needs no
such step; it is the same directory on both sides.

Observed churn on the day this was set up: `skills/` changed three times, the
two files once each. The thing that moves is the thing that is linked.

## One thing to watch

`settings.json` contains no key, token or absolute path today, which is why it
is safe here. That is a fact about the current contents, not a property of the
file. Check before adding to it.
