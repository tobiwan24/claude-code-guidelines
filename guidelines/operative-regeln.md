# Operative Regeln

Reflexe die Claude *jedes Mal* zeigen soll — unabhängig vom Projekt.
Format: **Regel · Auslöser · Begründung**

---

## Checkmarks in Plandateien sofort setzen

**Regel:** Erledigte Punkte sofort von `- [ ]` zu `- ✅` ändern — nicht am Ende der Session.

**Auslöser:** Sobald ein Schritt abgeschlossen ist.

**Begründung:** Verzögertes Markieren führt zu inkonsistentem Status, besonders bei Unterbrechungen.

---

## Aktuellen Abschnitt mit ❗ kennzeichnen

**Regel:** `❗` vor den Abschnitt setzen, an dem aktuell gearbeitet wird. Bei Wechsel verschieben.

**Auslöser:** Beginn jeder Arbeitsphase in einer Plandatei.

**Begründung:** Schnelle Orientierung beim Wiederaufnehmen einer unterbrochenen Session.

---

## Git-Commit nach Infrastruktur-Änderung vorschlagen

**Regel:** Nach jeder Änderung an produktiven Config-Dateien (Compose, Caddyfile, Scripts) `git commit` vorschlagen.

**Auslöser:** Jede Datei-Änderung im Implementierungs-Repo.

**Begründung:** Ohne explizite Erinnerung wird der Commit oft vergessen, besonders bei längeren Sessions.

---

## Textzeile vor Agent-Spawn ausgeben

**Regel:** Vor jedem Subagent-Aufruf eine sichtbare Zeile ausgeben:
`> Delegiere an **[spec]**...` / `> Delegiere an **[impl]**...`

**Auslöser:** Jeder `Agent`-Tool-Call.

**Begründung:** Tool-Call-Blöcke sind in der VSCode-Extension nicht immer sichtbar.
Der Agent selbst kennzeichnet seine Antwort zusätzlich (siehe `../konventionen/agent-kennzeichnung.md`).

---

## Dual-Write für kritische Regeln

**Regel:** Kritische operative Regeln in *beiden* Systemen dokumentieren: Memory-Datei UND CLAUDE.md.

**Auslöser:** Immer wenn eine neue Regel als "kritisch" eingestuft wird.

**Begründung:** Memory wird nicht immer geladen; CLAUDE.md ist immer im Kontext.
Redundanz verhindert Regelverlust bei Context-Switches.
