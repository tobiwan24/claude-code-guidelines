# Claude Code Guidelines

Persönliche, projektübergreifende Best Practices für die Arbeit mit Claude Code —
destilliert aus realen Projekten, bewusst abstrakt gehalten für Wiederverwendbarkeit.

## Wie nutzen

- **Neues Projekt starten:** `templates/CLAUDE.md` kopieren, projektspezifisch ergänzen
- **Agents einrichten:** `templates/agents/` kopieren, Platzhalter füllen
- **Nachschlagen:** `guidelines/` für Verhaltensregeln, `konventionen/` für Namensschemas, `architektur/` für Strukturmuster

## Inhalt

| Datei | Inhalt |
|---|---|
| [architektur/zwei-repo-pattern.md](architektur/zwei-repo-pattern.md) | Planungs-Repo ↔ Implementierungs-Repo trennen |
| [architektur/subagenten-system.md](architektur/subagenten-system.md) | spec+impl Agents, Orchestrator-Pattern |
| [templates/CLAUDE.md](templates/CLAUDE.md) | Kopierbares CLAUDE.md-Template |
| [templates/agents/spec-agent.md](templates/agents/spec-agent.md) | Template: Planungs-Agent (read-only) |
| [templates/agents/impl-agent.md](templates/agents/impl-agent.md) | Template: Implementierungs-Agent (schreibend) |
| [guidelines/enforcement.md](guidelines/enforcement.md) | Hierarchie: Hooks > Tool-Entzug > CLAUDE.md > Memory |
| [guidelines/operative-regeln.md](guidelines/operative-regeln.md) | Wiederkehrende Verhaltensregeln |
| [guidelines/fallstricke.md](guidelines/fallstricke.md) | Konkrete Bugs und Stolpersteine |
| [konventionen/agent-kennzeichnung.md](konventionen/agent-kennzeichnung.md) | Response-Header und Dateinamen-Schema |
| [konventionen/datei-laenge.md](konventionen/datei-laenge.md) | Max. Länge von Markdown-Dateien für Claude |

## Pflege-Konvention

Neues Learning aufnehmen wenn:
- ein Verhaltensfehler von Claude mehr als einmal auftrat
- ein Muster sich in mehreren Projekten bewährt hat
- eine Architekturentscheidung einen messbaren Unterschied machte

Format pro Learning: **Problem → Regel → Begründung**

Datei-Länge: max. 125–150 Zeilen pro `.md`. Bei Überschreitung aufteilen oder eindampfen.
