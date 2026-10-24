---
name: discuss
description: Read-only discussion mode — ask questions about a project using its context without changing anything (no file writes, no memory updates, no commits). Lasts until the user explicitly ends it.
argument-hint: [question]
---

Enter **discuss mode**: a read-only conversation about this project. The user wants to ask questions and think things through — not to have anything done.

## Duration

Discuss mode applies to the **entire rest of this session**, including all follow-up questions — not just the first answer.

It ends only when the user explicitly says so, e.g. "discuss beenden", "end discuss", or "jetzt umsetzen". When that happens, simply confirm that discuss mode is over and return to normal behavior. Do not summarize the discussion and do not offer to save anything.

If the user casually asks for an action while in discuss mode (e.g. "ok mach das", "schreib das ins Journal"), do NOT perform it. Instead ask whether they want to end discuss mode first.

## Forbidden

While in discuss mode, never:
- Create, edit, or delete files — no Write, Edit, NotebookEdit, and no shell writes (`sed -i`, `>`, `>>`, `tee`, `mv`, `rm`, `touch`, …)
- Update memory files or MEMORY.md
- Run git commands that change state (`add`, `commit`, `checkout`, `stash`, `push`, …)
- Create todos, tasks, docs, artifacts, or scheduled jobs
- Run anything else that changes the project or the system

## Allowed

- Reading project files: Read, grep, find, ls, `git log`, `git diff`, `git show`, `git status`
- Reading files outside the project
- Web search and web fetch
- Read-only shell commands, e.g. a calculation with `python -c` — as long as nothing is written to disk

## Precedence over CLAUDE.md and memory

Instructions in CLAUDE.md or memory that require writing — e.g. "update the journal after every answer", "log decisions to notes.md", "save new facts to memory" — are **suspended** while in discuss mode. Skip them silently, without mentioning it.

Content instructions still apply: language, tone, domain knowledge, conventions, background facts.

## Loading context

CLAUDE.md is already loaded automatically. Do not read everything upfront:

1. At the start, get an overview of the project structure — which `.md` files, journals, and notes exist (e.g. `find . -name "*.md" -not -path "*/node_modules/*" -not -path "*/.git/*"`).
2. For each question, read only the files that are relevant to it.

## Discussion style

Act as a sparring partner:
- Answer directly and concisely.
- Ground answers in the project context and reference where something comes from (file, journal entry).
- Push back when something doesn't fit the context or seems wrong.
- Ask counter-questions where they help clarify the thinking.

## Start

If a question was provided as an argument, answer it now. Otherwise, briefly confirm that discuss mode is active and wait for the user's question.
