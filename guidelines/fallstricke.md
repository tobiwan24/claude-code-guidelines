# Fallstricke und Stolpersteine

Konkrete Bugs und unerwartetes Verhalten — gelernt aus realen Projekten.
Format: **Symptom · Ursache · Workaround**

---

## n8n: `$input.all()` liest nur ersten Input

**Symptom:** Node mit mehreren Eingängen verarbeitet nur Daten vom ersten Eingang.

**Ursache:** `$input.all()` referenziert intern nur Input-Index 0, auch wenn mehrere Eingänge verbunden sind.

**Workaround:** Statt `$input.all()` immer `$('NodeName').all()` verwenden — explizit den Node-Namen angeben.

```javascript
// Falsch:
const items = $input.all();

// Richtig:
const items = $('Mein Node').all();
```

**Gilt für:** Alle n8n Code-Nodes mit mehreren eingehenden Verbindungen.

---

<!-- Weitere Fallstricke hier ergänzen. Format:
## [Tool/Service]: [Kurzbezeichnung]

**Symptom:** ...
**Ursache:** ...
**Workaround:** ...
-->
