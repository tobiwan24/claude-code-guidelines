# Agent-Kennzeichnung

Damit Agent-Nutzung in der Ausgabe immer erkennbar ist — unabhängig davon,
ob Tool-Call-Blöcke in der IDE sichtbar sind.

## Zwei Ebenen der Kennzeichnung

### Ebene 1: Ankündigung durch Haupt-Claude (vor dem Spawn)

Haupt-Claude gibt vor jedem Agent-Aufruf eine Textzeile aus:
```
> Delegiere an **[spec]** (Planung/Architektur)...
> Delegiere an **[impl]** (Umsetzung)...
```

### Ebene 2: Selbstkennzeichnung des Agents (in jeder Antwort)

Jeder Agent beginnt seine Antwort mit einem festen Header — keine Ausnahme:
```
> **[spec]**
> **[impl]**
```

Beide Ebenen zusammen: auch wenn Ebene 1 vergessen wird, ist Ebene 2 immer vorhanden.

## Dateinamen-Konvention

Alle Markdown-Dateien, die ein Agent erstellt, tragen einen Präfix:

| Agent | Präfix | Beispiel |
|---|---|---|
| spec | `spec_` | `spec_monitoring.md` |
| impl | `impl_` | `impl_nextcloud-update.md` |
| Haupt-Claude | kein Präfix | `plan.md` |

Damit ist auf den ersten Blick erkennbar, welcher Agent eine Datei erstellt hat —
auch Wochen nach der Erstellung.
