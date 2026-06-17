# [PROJEKTNAME] — CLAUDE.md

## 0. Sprache

Antworte immer auf Deutsch – außer in Code, Dateinamen, Fehlermeldungen und Fachbegriffen.

## 1. Think Before Coding

Bevor implementiert wird:
- Annahmen explizit nennen. Bei Unsicherheit: fragen.
- Mehrere Interpretationen vorstellen, nicht still wählen.
- Einfachere Alternative benennen wenn vorhanden.
- Bei Infrastruktur-Änderungen: erst Plan skizzieren und bestätigen lassen.

## 2. Simplicity First

- Kein Code über das Gefragte hinaus.
- Keine Abstraktionen für Einmal-Code.
- Keine spekulative Flexibilität.
- Wenn 200 Zeilen → 50 Zeilen möglich: neu schreiben.

## 3. Surgical Changes

- Nur das Nötigste anfassen.
- Fremden Code nicht "nebenbei verbessern".
- Stil des bestehenden Codes matchen.
- Eigene Waisen entfernen (Imports, Variablen die durch eigene Änderung unused wurden).

## 4. Goal-Driven Execution

Aufgabe in verifizierbare Ziele übersetzen:
```
1. [Schritt] → verify: [Prüfung]
2. [Schritt] → verify: [Prüfung]
```

## 5. Projekt-Konventionen

<!-- Hier projektspezifische Regeln eintragen -->

### Technische Constraints (nicht verhandelbar)

| Constraint | Ursache | Konsequenz |
|---|---|---|
| <!-- ... --> | <!-- ... --> | <!-- ... --> |

### Destruktive Aktionen (immer bestätigen lassen)

- <!-- z.B. docker compose down -v -->
- <!-- z.B. rm -rf auf Datenverzeichnissen -->

### Speicher / Infrastruktur

<!-- z.B. Volume-Konventionen, Backup-Pfade, NAS-Regeln -->

## 6. Agent-Pflicht

- Planungsfragen / Architektur / Konzepte → **spec-Agent** spawnen, nie direkt antworten
- Umsetzungsaufgaben (Code, Config, Deploy) → **impl-Agent** spawnen

Vor jedem Agent-Spawn: kurze Textzeile ausgeben (Tool-Calls nicht immer sichtbar).
