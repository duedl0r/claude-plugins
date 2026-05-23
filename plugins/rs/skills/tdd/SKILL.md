---
name: tdd
description: Implement a feature using iterative Test-Driven Development — one scenario at a time, RED → GREEN → commit, repeat
argument-hint: [docs/filename.md or feature description]
---

Implement the feature using iterative Test-Driven Development (TDD).

Work through all scenarios automatically — happy path first, then edge cases, then error cases. For each scenario, complete one full RED → GREEN cycle before moving to the next.

Follow these steps exactly, in order. Do not skip steps.

## Step 0 — Load Spec (only if a file path was passed as argument)
If the argument looks like a file path (e.g. `docs/spec.md`), read that file now before proceeding.
The feature to implement is then described in that file plus our conversation.
If no file path was given, use the feature described in our conversation.

Plan the scenarios to cover (happy path → edge cases → error cases). Do not show this list to the user — just work through them.

---

## Iterative Cycle (repeat for each scenario)

### Cycle Step 1 — Write One Test
Write a single unit test for the next scenario.
Do NOT write any implementation code yet.

⚠️ IMMUTABILITY RULE: Once a test is committed, it must NEVER be modified in any phase — neither when writing new tests nor during implementation. If you believe a committed test needs to change, STOP immediately and ask the user for explicit permission before touching it.

### Cycle Step 2 — Commit Test Only
Commit only the new test file(s):
`test(scope): add test for [scenario]`

### Cycle Step 3 — Verify RED
Run the full test suite and confirm the new test fails.

If the new test passes without implementation, STOP immediately and ask the user:

> "Test `[TestName::method]` ist bereits grün — ohne Implementierung.  
> Mögliche Ursachen: Feature existiert schon teilweise / Test prüft nichts Sinnvolles.  
> Was soll ich tun?  
> [E] Entfernen — Test bringt keinen TDD-Wert  
> [U] Untersuchen — ich schaue warum er grün ist und berichte  
> [B] Behalten — bewusste Entscheidung, weiter mit dem nächsten"

Wait for the user's answer before proceeding.

### Cycle Step 4 — Implement
Write only enough implementation code to make this test pass.

⚠️ IMMUTABILITY RULE: Do NOT modify any previously committed test file. If you believe a test needs to change, STOP immediately and ask the user for explicit permission before touching it.

### Cycle Step 5 — Verify GREEN
Run the full test suite. All previously passing tests must still pass. The new test must now pass.

If a previously passing test is now broken, fix the implementation — never the tests.

### Cycle Step 6 — Commit Implementation
`feat(scope): implement [scenario]`

### → Next scenario
Return to Cycle Step 1 for the next scenario. Continue until all scenarios are covered.

---

## Step 1 — Code Review
Once all scenarios are done, run TWO passes over all implementation code:

**Pass 1 — Correctness:**
- Dead code, unnecessary complexity, or duplication
- Security issues (injection, validation, auth)
- Edge cases not covered by tests

**Pass 2 — Simplify (invoke the `simplify` skill):**
Run `/simplify` on the changed files. This runs a dedicated Opus agent focused on readability, redundancy, naming, and project-style consistency.

Fix any issues found in both passes before committing.

## Step 2 — Commit Review Fixes
If any fixes were made during review:
`refactor(scope): apply review fixes for [feature]`

## Step 3 — Abschlussarbeiten
Nach dem Commit: Räume alle Tracking-Dateien auf die während dieses Workflows erstellt oder verwendet wurden.

1. Suche nach `todo.md`, `TODO.md`, `docs/issue.md`, `docs/*.md` und ähnlichen Dateien im Projekt
2. Hake alle erledigten Punkte ab (Markdown-Checkboxen `- [ ]` → `- [x]`, oder streiche offene Einträge durch)
3. Melde kurz was abgehakt wurde — und falls noch offene Punkte übrig bleiben, liste sie explizit auf damit der User entscheiden kann was als nächstes zu tun ist
4. Committe die aktualisierten Dateien: `chore: update todo and issue tracking after [feature]`
