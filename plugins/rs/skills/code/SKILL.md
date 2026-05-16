---
name: code
description: Implement a feature without TDD — directly implement, code review, commit. Use when no test infrastructure exists.
argument-hint: [docs/filename.md or feature description]
---

Implement the feature directly, without writing tests.

Follow these steps exactly, in order. Do not skip steps.

## Step 0 — Load Spec (only if a file path was passed as argument)
If the argument looks like a file path (e.g. `docs/spec.md`), read that file now before proceeding.
The feature to implement is then described in that file plus our conversation.
If no file path was given, use the feature described in our conversation.

## Step 1 — Implement
Write the implementation code.

## Step 2 — Code Review
Run TWO passes over the implementation code:

**Pass 1 — Correctness:**
- Dead code, unnecessary complexity, or duplication
- Security issues (injection, validation, auth)
- Edge cases

**Pass 2 — Simplify (invoke the `simplify` skill):**
Run `/simplify` on the changed files. This runs a dedicated Opus agent focused on readability, redundancy, naming, and project-style consistency.

Fix any issues found in both passes before committing.

## Step 3 — Commit Implementation
`feat(scope): implement [feature]`

## Step 4 — Abschlussarbeiten
Nach dem Commit: Räume alle Tracking-Dateien auf die während dieses Workflows erstellt oder verwendet wurden.

1. Suche nach `todo.md`, `TODO.md`, `docs/issue.md`, `docs/*.md` und ähnlichen Dateien im Projekt
2. Hake alle erledigten Punkte ab (Markdown-Checkboxen `- [ ]` → `- [x]`, oder streiche offene Einträge durch)
3. Melde kurz was abgehakt wurde — und falls noch offene Punkte übrig bleiben, liste sie explizit auf damit der User entscheiden kann was als nächstes zu tun ist
4. Committe die aktualisierten Dateien: `chore: update todo and issue tracking after [feature]`
