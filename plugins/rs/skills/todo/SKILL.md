---
name: todo
description: Add a todo item to TODO.md and commit it. Use during coding sessions to capture tasks without breaking flow.
argument-hint: <todo text>
---

Add a todo item to TODO.md and commit it.

## Step 0 — Validate Input

If no argument was provided, stop immediately and tell the user:
> "Usage: /rs:todo <text>  
> Example: /rs:todo Fix the auth bug"

## Step 1 — Find Repo Root

Run `git rev-parse --show-toplevel` to find the repo root.

If the command fails (not a git repo), stop and tell the user:
> "No git repository found. /rs:todo requires a git repo."

## Step 2 — Ensure TODO.md Exists

Check if `TODO.md` exists at the repo root.

If it does not exist, create it with this content:
```
# TODO

```

## Step 3 — Append the Todo Item

Append this line at the end of `TODO.md`:
```
- [ ] <argument text>
```

Make sure there is a newline before the new entry if the file doesn't end with one.

## Step 4 — Commit

Stage only `TODO.md` (do not touch any other files):
```
git add <repo-root>/TODO.md
```

Commit with the message:
```
todo: <argument text>
```

Do NOT stage or commit any other files, even if the working tree is dirty.
