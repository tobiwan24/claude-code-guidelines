# Claude GitHub App: Issue-gesteuerter Workflow

## Problem

Wissensnotizen und kleine Änderungen bleiben im Kopf oder in losen Dateien —
kein strukturierter Weg, sie direkt ins Repo zu überführen ohne lokale Umgebung.

## Lösung: Claude als GitHub-nativer Assistent

Die [Claude GitHub App](https://github.com/apps/claude) reagiert auf `@claude`-Mentions
in Issues und Pull Requests und setzt Aufgaben direkt als PR um.

## Installation

1. [Claude GitHub App](https://github.com/apps/claude) öffnen → **Install**
2. Repository auswählen (z.B. `claude-code-guidelines`)
3. Workflow-Datei `.github/workflows/claude.yml` wird automatisch angelegt

Voraussetzung: Anthropic API Key als Repository-Secret `ANTHROPIC_API_KEY`.

## Workflow

```
Du erstellst ein Issue
        ↓
Du schreibst @claude + Auftrag ins Issue
(z.B. "Füge das als neue Datei unter konventionen/ ein")
        ↓
Claude analysiert, erstellt Branch + PR mit Änderung
        ↓
Du reviewst den PR und mergst
```

### Beispiel-Issue

```
Titel: add: Konvention für Commit-Messages

@claude Füge folgende Konvention als neue Datei `konventionen/commit-messages.md` ein:

Commits immer im Format: `typ: kurze Beschreibung`
Typen: feat, fix, docs, refactor, test
Kein Punkt am Ende. Imperativ. Max. 72 Zeichen.
```

Claude erstellt daraus automatisch einen PR mit der neuen Datei.

## Grenzen

| Kann Claude | Kann Claude nicht |
|---|---|
| Dateien erstellen / ändern | Workflows in `.github/workflows/` ändern |
| PRs erstellen | PRs mergen oder approven |
| Fragen beantworten | Externe Systeme steuern |

## Regel

**Auftrag im Issue = vollständige Spec.**
Claude hat keinen weiteren Kontext außer Issue-Body und Repo-Inhalt.
Schreibe den `@claude`-Auftrag so, dass er ohne Rückfragen umsetzbar ist.
