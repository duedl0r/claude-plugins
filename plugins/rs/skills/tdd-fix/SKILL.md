---
name: tdd-fix
description: Fix a bug using TDD — write a failing test that proves the bug, verify RED, fix implementation, code review, commit
argument-hint: [bug description or docs/issue.md]
---

Fix the bug using Test-Driven Development.

Follow these steps exactly, in order. Do not skip steps.

## Step 0 — Load Issue (only if a file path was passed as argument)
If the argument looks like a file path (e.g. `docs/issue.md`), read that file now before proceeding.
The bug to fix is then described in that file plus our conversation.
If no file path was given, use the bug described in our conversation.

## Step 1 — Understand the Bug
Locate the relevant code. Understand what the implementation does wrong before writing any test.

## Step 2 — Write Failing Test
Write a single test that proves the bug exists — it must fail because the implementation is wrong, not because the feature is missing.

⚠️ IMMUTABILITY RULE: Once this test is committed, it must NEVER be modified in any phase. If you believe the test needs to change, STOP immediately and ask the user for explicit permission before touching it.

## Step 3 — Commit Test Only
Commit only the test file(s):
`test(scope): add failing test for [bug]`

## Step 4 — Verify RED
Run the full test suite and confirm the new test fails.

If the new test passes without any fix, STOP immediately and ask the user:

> "Test `[TestName::method]` ist bereits grün — ohne Fix.  
> Mögliche Ursachen: Bug existiert nicht mehr / Test prüft nicht das richtige Verhalten.  
> Was soll ich tun?  
> [E] Entfernen — Test beweist den Bug nicht  
> [U] Untersuchen — ich schaue warum er grün ist und berichte  
> [B] Behalten — bewusste Entscheidung, weiter mit dem Fix"

Wait for the user's answer before proceeding.

## Step 5 — Fix Implementation
Fix only the implementation code. Do NOT modify the test.

⚠️ IMMUTABILITY RULE: Do NOT modify the committed test file. If you believe the test needs to change, STOP immediately and ask the user for explicit permission before touching it.

## Step 6 — Run Tests & Iterate
Run the full test suite. The new test must pass. All previously passing tests must still pass.

Fix only implementation code until everything is green. Never modify test files. If stuck, report the problem to the user.

## Step 7 — Code Review
Run TWO passes over the changed implementation code:

**Pass 1 — Correctness:**
- Dead code, unnecessary complexity, or duplication
- Security issues (injection, validation, auth)
- Edge cases not covered by tests

**Pass 2 — Simplify (invoke the `simplify` skill):**
Run `/simplify` on the changed files. This runs a dedicated Opus agent focused on readability, redundancy, naming, and project-style consistency.

Fix any issues found in both passes before committing.

## Step 8 — Commit Fix
Once all tests are green and the review is clean, commit the fix:
`fix(scope): [bug description]`

## Step 9 — Abschlussarbeiten
Nach dem Commit: Räume alle Tracking-Dateien auf die während dieses Workflows erstellt oder verwendet wurden.

1. Suche nach `todo.md`, `TODO.md`, `docs/issue.md`, `docs/*.md` und ähnlichen Dateien im Projekt
2. Hake alle erledigten Punkte ab (Markdown-Checkboxen `- [ ]` → `- [x]`, oder streiche offene Einträge durch)
3. Melde kurz was abgehakt wurde — und falls noch offene Punkte übrig bleiben, liste sie explizit auf damit der User entscheiden kann was als nächstes zu tun ist
4. Committe die aktualisierten Dateien: `chore: update todo and issue tracking after [bug]`
