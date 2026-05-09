---
name: tdd
description: Implement a feature using strict Test-Driven Development — write failing tests, verify RED, implement, code review, commit
argument-hint: [feature description]
---

Implement the feature described in our conversation using strict Test-Driven Development (TDD).

Follow these steps exactly, in order. Do not skip steps.

## Step 1 — Write Unit Tests
Write comprehensive unit tests for the feature. Cover happy paths, edge cases, and error cases.
Do NOT write any implementation code yet.

## Step 2 — Commit Tests Only
Commit only the test files using Conventional Commits format, e.g.:
`test(scope): add failing tests for [feature]`

## Step 3 — Verify Tests Are RED
Run the full test suite and confirm ALL new tests fail.

If any new test passes without implementation, STOP immediately and for each such test ask the user:

> "Test `[TestName::method]` ist bereits grün — ohne Implementierung.  
> Mögliche Ursachen: Feature existiert schon teilweise / Test prüft nichts Sinnvolles.  
> Was soll ich tun?  
> [E] Entfernen — Test bringt keinen TDD-Wert  
> [U] Untersuchen — ich schaue warum er grün ist und berichte  
> [B] Behalten — bewusste Entscheidung, weiter mit dem nächsten"

Wait for the user's answer for each non-red test before proceeding.
Only continue to Step 4 once every remaining test is confirmed RED.

## Step 4 — Implement
Write the implementation code.

⚠️ STRICT RULE: Do NOT modify any test file during implementation.
If you believe a test needs to change, STOP immediately and ask the user for explicit permission before touching it.

## Step 5 — Run Tests & Iterate
Run the tests. Fix only implementation code until all tests pass.
Never modify test files. If stuck, report the problem to the user.

## Step 6 — Code Review
Run TWO passes over the implementation code:

**Pass 1 — Correctness:**
- Dead code, unnecessary complexity, or duplication
- Security issues (injection, validation, auth)
- Edge cases not covered by tests

**Pass 2 — Simplify (invoke the `simplify` skill):**
Run `/simplify` on the changed files. This runs a dedicated Opus agent focused on readability, redundancy, naming, and project-style consistency.

Fix any issues found in both passes before committing.

## Step 7 — Commit Implementation
Once all tests are green and the review is clean, commit the implementation:
`feat(scope): implement [feature]`

## Step 8 — Abschlussarbeiten
Nach dem Commit: Räume alle Tracking-Dateien auf die während dieses Workflows erstellt oder verwendet wurden.

1. Suche nach `todo.md`, `TODO.md`, `docs/issue.md`, `docs/*.md` und ähnlichen Dateien im Projekt
2. Hake alle erledigten Punkte ab (Markdown-Checkboxen `- [ ]` → `- [x]`, oder streiche offene Einträge durch)
3. Melde kurz was abgehakt wurde — und falls noch offene Punkte übrig bleiben, liste sie explizit auf damit der User entscheiden kann was als nächstes zu tun ist
4. Committe die aktualisierten Dateien: `chore: update todo and issue tracking after [feature]`
