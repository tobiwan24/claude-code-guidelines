# Subagenten-System: spec + impl

## Problem

Claude agiert ohne Rollentreinung gleichzeitig als Planer und Umsetzer —
Implementierungsdetails dominieren die Konzeptdiskussion, oder umgekehrt.

## Zwei-Agenten-Modell

| Agent | Modell | Tools | Darf |
|---|---|---|---|
| **spec** | Opus (stärkstes Reasoning) | Read, WebSearch, WebFetch, Bash (read-only) | Lesen, Fragen stellen, Tradeoffs benennen |
| **impl** | Sonnet (schnell + günstig) | Bash, Read, Edit, Write, WebSearch, WebFetch | Schreiben, Ausführen, Deployen |

Templates: `../templates/agents/`

## Routing

Claude entscheidet anhand der Agent-`description`. Je präziser die Trigger-Formulierung,
desto zuverlässiger das automatische Routing.

**Beispiel spec-description:**
> "Einsatz wenn neue Features geplant, bestehende Specs geprüft, oder Konzepte hinterfragt werden sollen."

**Beispiel impl-description:**
> "Einsatz wenn konkrete Änderungen am Stack umgesetzt werden sollen."

## Orchestrator-Pattern

Ein dritter Agent (nur `Task`-Tool) delegiert an spec/impl und wartet auf Rückgabe:

```
Anfrage → Orchestrator
           ↓ wartet
           spec → liefert Plan
           ↓ erst dann
           impl → setzt um
           ↓
         Ergebnis
```

**Harte Garantie für Delegation:** Orchestrator bekommt *keine* Schreib-Tools.
Er kann physisch nicht selbst implementieren → muss delegieren.

## Enforcement-Stufen

1. **Tool-Entzug** (härte Garantie) — Orchestrator hat nur `Task`
2. **CLAUDE.md Agent-Pflicht-Sektion** — weiche, aber immer aktive Regel
3. **Präzise Agent-Beschreibungen** — verbessert automatisches Routing

Für Enforcement-Hierarchie allgemein: siehe `../guidelines/enforcement.md`
