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
5. Neues Feature mit Tests: `/rs:tdd docs/filename.md` — iterativ pro Szenario: Test → RED → Impl → GREEN → Commit, dann Code Review
   Bugfix mit Tests: `/rs:tdd-fix docs/issue.md` — Bug-Test → RED → Fix → GREEN → Code Review → Commit
   Ohne Tests: `/rs:code docs/filename.md` — Implementierung → Code Review → Commit

## /rs:grill-me
Interviewt mich systematisch über einen Plan bis wir ein gemeinsames Verständnis haben.

## /rs:write-tech-spec [filename]
Schreibt ein Tech Spec Dokument aus der Chat-History.

## /rs:write-issue [filename]
Schreibt ein kompaktes Issue-Ticket aus der Chat-History. Speichert als `docs/filename.md` (default: `docs/issue.md`).

## /rs:tdd [docs/filename.md]
Liest optional eine Spec-Datei ein, dann iterativ pro Szenario: Test schreiben → rot verifizieren → implementieren → grün verifizieren → committen. Am Ende: Code Review → committen → Abschlussarbeiten.

## /rs:tdd-fix [docs/issue.md]
Liest optional eine Issue-Datei ein, dann: Bug-reproduzierenden Test schreiben → rot verifizieren → Implementation fixen → grün iterieren → Code Review → committen → Abschlussarbeiten.

## /rs:code [docs/filename.md]
Liest optional eine Spec-Datei ein, dann: direkt implementieren → Code Review → committen → Abschlussarbeiten. Für Projekte oder Features ohne Testinfrastruktur.
