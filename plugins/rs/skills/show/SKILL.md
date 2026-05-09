---
name: show
description: Shows the recommended end-to-end development workflow
---

Show the following workflow to the user exactly as written, without any additional commentary:

## Workflow

1. `/rs:grill-me [idee kurz beschreiben]` — immer damit starten, nie zuerst Freitext schreiben
2. Claude interviewt systematisch
3. `/rs:write-tech-spec filename` oder `/rs:write-issue` — Dokument wird erstellt
4. `/clear` — Chat leeren (Tokens sparen, Kontext sauber halten)
5. `lies docs/filename.md` — Spec einlesen
6. `/rs:tdd` — Tests → Implementierung → Code Review → Commit

## /rs:grill-me
Interviewt mich systematisch über einen Plan bis wir ein gemeinsames Verständnis haben.

## /rs:write-tech-spec [filename]
Schreibt ein Tech Spec Dokument aus der Chat-History.

## /rs:write-issue [filename]
Schreibt ein kompaktes Issue-Ticket aus der Chat-History. Speichert als `docs/filename.md` (default: `docs/issue.md`).

## /rs:tdd
Umsetzung nach TDD: Tests schreiben → rot verifizieren → implementieren → grün iterieren → Code Review → committen → Abschlussarbeiten (todo.md & Issue-Files aktualisieren).
