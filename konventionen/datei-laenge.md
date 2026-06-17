# Dateilänge für Claude-lesbare Markdown-Dateien

## Regel

Markdown-Dateien, die Claude lesen soll (CLAUDE.md, Specs, Agent-Prompts, Guidelines),
dürfen **maximal 125–150 Zeilen** lang sein.

## Warum

- Längere Dateien erhöhen die Wahrscheinlichkeit, dass Claude relevante Abschnitte
  übersieht oder falsch gewichtet
- Kurze, dichte Dateien zwingen zur Priorisierung des Wesentlichen
- Leichter zu pflegen und aktuell zu halten

## Was tun bei Überschreitung

1. **Aufteilen:** Thematisch trennbare Abschnitte in eigene Dateien auslagern
2. **Eindampfen:** Datei neu lesen und auf das Wesentliche reduzieren —
   was würde ein erfahrener Entwickler weglassen?
3. **Beispiele kürzen:** Code-Snippets auf das Minimum reduzieren

## Regelmäßige Re-Analyse

Specs und Guidelines sollten periodisch re-analysiert werden:
- Gibt es veraltete Regeln, die nicht mehr gelten?
- Gibt es Redundanzen zwischen Dateien?
- Welche Abschnitte wurden nie gebraucht?

**Faustregel:** Wenn eine Datei seit 4 Wochen nicht geändert wurde, lohnt sich ein Blick.

## Ausnahmen

Templates (z.B. `templates/CLAUDE.md`) dürfen länger sein — sie werden nicht direkt
von Claude gelesen, sondern kopiert und dann projektspezifisch angepasst.
