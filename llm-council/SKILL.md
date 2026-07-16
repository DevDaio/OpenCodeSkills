---
name: llm-council
description: Brainstorming mit mehreren Perspektiven. Use when user asks to "consult the council", "get different perspectives", "look at this from different angles", "compare approaches", or wants multiple viewpoints on a question before synthesizing a final recommendation.
---

# LLM Council

Nimm eine Frage des Users und betrachte sie aus verschiedenen Perspektiven, bevor du eine synthetisierte Empfehlung präsentierst.

## Modelle

Jedes Modell bekommt **alle Perspektiven** und bildet sich eine eigene Meinung. Erst dann diskutieren die Modelle und stimmen ab.

| Modell | Charakter |
|---|---|
| `opencode/big-pickle` | Big Pickle – pragmatisch, risikobewusst |
| `opencode/deepseek-v4-flash-free` | DeepSeek – schnell, analytisch |
| `opencode/mimo-v2.5-free` | MiMo – ausgewogen, menschenzentriert |
| `opencode/north-mini-code-free` | North – nüchtern, codenah |
| `opencode/nemotron-3-ultra-free` | Nemotron – visionär, futuristisch |

Fallbacks bei Rate-Limits (ebenfalls kostenlos):
`opencode/glm-4.7-free`, `opencode/minimax-m2.1-free`, `opencode/kimi-k2.5-free`

## Ablauf

### Phase 1: Perspektiven definieren

Die Standard-Perspektiven sind:
- Sicherheit & Robustheit
- Performance & Skalierbarkeit
- Wartbarkeit & Einfachheit
- Pragmatismus & Time-to-Market
- Future-Proof (Innovation)

Der User kann eigene Perspektiven vorgeben oder die Standards verwenden.

### Phase 2: Interne Abstimmung (pro Modell)

Jedes Modell wendet **alle** Perspektiven auf die Frage an, skizziert pro Perspektive eine Antwort und synthetisiert daraus eine eigene Position. Format:

```
## [Modellname]

**Sicherheit:** ...
**Performance:** ...
**Wartbarkeit:** ...
**Pragmatismus:** ...
**Future-Proof:** ...

**Eigene Position:** ...
```

### Phase 3: Modelldiskussion

Die fünf Positionen werden nebeneinander gestellt. Prüfe:
- Wo gibt es Konsens?
- Wo gibt es Widersprüche?
- Welche Argumente überzeugen am meisten?

Jedes Modell kann auf die Position der anderen reagieren (z.B. "Nemotron, dein Future-Proof-Argument ignoriert Wartbarkeit – North, wie siehst du das?").

### Phase 4: Gesamtabstimmung

Jedes Modell gibt eine finale Stimme ab (dafür / dagegen / Enthaltung). Die Mehrheit gewinnt.

### Phase 5: Synthese & Empfehlung

Fasse zusammen: Gemeinsamkeiten, Knackpunkte, und die finale Handlungsempfehlung an den User.

## Output-Format

**Angenommene Perspektiven:** [Liste]

### Interne Abstimmungen

**Big Pickle:**
- Sicherheit: ...
- Performance: ...
- ...
- **Position:** ...

**DeepSeek:**
- ...
- **Position:** ...

...

### Modelldiskussion

[Wechselseitige Argumente, Nachfragen, Gegenpositionen]

### Gesamtabstimmung

| Modell | Stimme |
|---|---|
| Big Pickle | Dafür |
| DeepSeek | Enthaltung |
| MiMo | Dafür |
| North | Dagegen |
| Nemotron | Dafür |
| **Ergebnis** | **3:1 – Angenommen** |

### Synthese & Empfehlung

[Zusammenfassung der Kernpunkte und Handlungsempfehlung]

## Beispiele

> "Consult the council: Soll ich Microservices oder ein Monolithen nehmen?"
>
> "Lass den Council auf meine Architektur schauen – Fokus auf Sicherheit und Skalierbarkeit."
>
> "What would the council say about this API design?"
