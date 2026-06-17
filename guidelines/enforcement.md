# Enforcement-Hierarchie

Wie zuverlässig lässt sich ein Verhalten bei Claude erzwingen?

## Hierarchie (stärkste → schwächste)

### 1. Hooks — deterministisch
Shell-Skripte, die *vor* Claudes Antwort laufen. Kein Modell, kein Halluzinieren.

**UserPromptSubmit-Hook:** analysiert jede Nachricht und injiziert Text.
```json
"hooks": {
  "UserPromptSubmit": [{
    "matcher": "",
    "hooks": [{ "type": "command", "command": "python pfad/zum/skript.py" }]
  }]
}
```
Das Skript hängt z.B. `"Du MUSST spec-Agent nutzen."` vor den Prompt.

### 2. Tool-Entzug — physische Unmöglichkeit
Orchestrator bekommt nur das `Task`-Tool → kann selbst nichts schreiben/lesen.
Delegation ist keine Entscheidung mehr, sondern die einzige Option.

### 3. CLAUDE.md — stärkste weiche Methode
Immer im Kontext-Fenster, überschreibt laut Header Standardverhalten.
Claude *kann* es ignorieren — tut es selten, aber es ist keine Garantie.

**Regel:** Kritische Verhaltensregeln in CLAUDE.md UND Memory schreiben (Dual-Write).

### 4. Memory — persistent, aber ignorierbar
Wird beim Start geladen, bleibt über Sitzungen erhalten.
Schwächer als CLAUDE.md weil nicht im primären System-Prompt.

### 5. Prompt — am schwächsten
Nur für die aktuelle Nachricht wirksam. Keine Persistenz.

## Faustformel

| Ziel | Methode |
|---|---|
| Claude soll es *nie* tun können | Tool-Entzug |
| Claude soll es *immer* tun | Hook |
| Claude soll es *in der Regel* tun | CLAUDE.md |
| Claude soll es *heute* tun | Prompt |
