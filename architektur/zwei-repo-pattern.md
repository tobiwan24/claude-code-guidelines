# Zwei-Repo-Pattern: Planung ↔ Implementierung

## Problem

Wenn Specs, Plandateien und produktive Implementierungsdateien im selben Repo liegen,
vermischen sich Commit-Historien, und Claude arbeitet in beiden Modi gleichzeitig ohne klare Trennung.

## Regel

**Zwei getrennte Repos:** eines für Planung/Dokumentation, eines für produktive Dateien.

## Aufbau

```
planungs-repo/          ← Specs, Entscheidungen, n8n-Workflow-JSONs, Docs
implementierungs-repo/  ← Produktive Konfigurationsdateien, Docker-Compose, Scripts
```

## Commit-Reihenfolge

1. Änderung in Planungs-Repo committen (Was und Warum)
2. Implementierung in Implementierungs-Repo committen (Wie)
3. Remote deployen

Nie umgekehrt — der Plan ist die Quelle der Wahrheit.

## Vorteile

- Planungs-History bleibt lesbar (kein Rauschen durch Config-Bumps)
- Implementierungs-Repo kann auf Remote-Server gepullt werden ohne Docs-Ballast
- Claude weiß in welchem Repo er gerade ist und was er darf

## Konvention für Claude

In CLAUDE.md des Planungs-Repos:
```
Bei Änderungen: erst planungs-repo/ committen, dann implementierungs-repo/
```

In CLAUDE.md des Implementierungs-Repos:
```
Nach jeder Änderung: git commit vorschlagen
Niemals Produktivdateien überschreiben ohne vorherigen Diff
```
