# GitHub App Workflow: Issue → @claude → PR → Merge

## Was ist das

Die Claude GitHub App (`claude-code-action`) ermöglicht es, Claude direkt aus GitHub-Issues
oder Pull Requests heraus zu beauftragen. Claude liest den Kontext, implementiert die Änderung
und erstellt automatisch einen PR — ohne lokale Claude-Instanz.

## Installation

1. GitHub Actions Workflow einrichten: `.github/workflows/claude.yml` im Repo anlegen
   (Vorlage: [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action))
2. `ANTHROPIC_API_KEY` als Repository-Secret hinterlegen
3. Optional: `claude-code-review.yml` für automatische Code-Reviews bei PRs

## Workflow

```
1. Issue erstellen  →  Wissen, Notiz, Aufgabe beschreiben
2. @claude mention  →  Auftrag formulieren (z.B. "Füge das unter konventionen/ ein")
3. Claude agiert    →  Erstellt Branch + Commit + PR automatisch
4. Review & Merge   →  Du prüfst den PR und mergst
```

## Anwendungsbeispiele

| Trigger | Auftrag | Ergebnis |
|---|---|---|
| Issue mit Notiz | `@claude Füge das als neue Datei unter konventionen/ ein` | PR mit neuer Datei |
| Issue mit Bug | `@claude Behebe diesen Fehler in guidelines/fallstricke.md` | PR mit Bugfix |
| PR öffnen | `@claude Review: Auf Konsistenz mit bestehenden Konventionen prüfen` | Review-Kommentar |

## Vorteile

- Kein lokaler Claude-Client nötig für Dokumentations-Updates
- Workflow direkt im Browser: Issue → PR → Merge
- Änderungshistorie bleibt sauber (jede Änderung als eigener PR)
- Ideal für dieses Repo: Learnings direkt als Issue notieren, Claude trägt sie ein

## Grenzen

- Claude kann keine Workflows in `.github/workflows/` ändern (GitHub-Permission-Limit)
- Komplexe Multi-File-Refactorings besser lokal mit Claude Code durchführen
- Kein Approve von PRs durch Claude möglich (Security-Constraint)

## Konvention für dieses Repo

Issues für neue Guidelines/Learnings mit diesem Format erstellen:
```
Titel: add: <kurze Beschreibung>

<Inhalt des Learnings>

@claude Füge das strukturiert an korrekter Stelle ein
```
