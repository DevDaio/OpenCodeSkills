# LLM Council

Strukturiertes Brainstorming aus mehreren Perspektiven. Simuliert einen Rat aus KI-Modellen, die eine Frage diskutieren und eine gemeinsame Empfehlung aussprechen.

## Installation

```bash
# Für OpenCode (Mac/Linux)
cp -r llm-council ~/.config/opencode/skills/

# Für Claude Code (falls verwendet)
cp -r llm-council ~/.claude/skills/
```

## Aktivierung

Wird aktiviert bei Phrasen wie:
- "Consult the council"
- "Get different perspectives"
- "Look at this from different angles"
- "Compare approaches"
- "What would the council say"

## Der Rat

| Modell | Charakter |
|--------|-----------|
| `opencode/big-pickle` | Big Pickle – pragmatisch, risikobewusst |
| `opencode/deepseek-v4-flash-free` | DeepSeek – schnell, analytisch |
| `opencode/mimo-v2.5-free` | MiMo – ausgewogen, menschenzentriert |
| `opencode/north-mini-code-free` | North – nüchtern, codenah |
| `opencode/nemotron-3-ultra-free` | Nemotron – visionär, futuristisch |

**Fallbacks bei Rate-Limits:** `glm-4.7-free`, `minimax-m2.1-free`, `kimi-k2.5-free`

## Standard-Perspektiven

1. **Sicherheit & Robustheit** – Fehlertoleranz, Edge Cases, sichere Defaults
2. **Performance & Skalierbarkeit** – Latenz, Durchsatz, Ressourcenverbrauch
3. **Wartbarkeit & Einfachheit** – Clean Code, Dokumentation, geringe Komplexität
4. **Pragmatismus & Time-to-Market** – Schnelle Ergebnisse, praktikable Lösungen
5. **Future-Proof (Innovation)** – Neue Technologien, Erweiterbarkeit, Trends

Der User kann eigene Perspektiven vorgeben oder die Standards verwenden.

## Ablauf

### Phase 1: Perspektiven definieren
Die fünf Perspektiven (Standard oder benutzerdefiniert) werden festgelegt.

### Phase 2: Interne Abstimmung (pro Modell)
Jedes Modell wendet **alle** Perspektiven auf die Frage an und synthetisiert eine eigene Position.

```markdown
## [Modellname]

**Sicherheit:** ...
**Performance:** ...
**Wartbarkeit:** ...
**Pragmatismus:** ...
**Future-Proof:** ...

**Eigene Position:** ...
```

### Phase 3: Modelldiskussion
Die fünf Positionen werden verglichen:
- Wo gibt es Konsens?
- Wo gibt es Widersprüche?
- Welche Argumente überzeugen?

### Phase 4: Gesamtabstimmung
Jedes Modell stimmt ab: **Dafür / Dagegen / Enthaltung**. Die Mehrheit gewinnt.

### Phase 5: Synthese & Empfehlung
Zusammenfassung der Kernpunkte und einer klaren Handlungsempfehlung.

## Beispielausgabe

```
### Gesamtabstimmung

| Modell | Stimme |
|--------|--------|
| Big Pickle | Dafür |
| DeepSeek | Enthaltung |
| MiMo | Dafür |
| North | Dagegen |
| Nemotron | Dafür |
| **Ergebnis** | **3:1 – Angenommen** |

### Synthese & Empfehlung

Die Mehrheit empfiehlt den Monolithen mit klaren Modul-Grenzen.
Gründe: niedrigere initiale Komplexität, einfachere Deployment-Pipeline,
und die Möglichkeit bei Bedarf später einzelne Module auszugliedern.
```

## Dateistruktur

```
llm-council/
├── README.md       # Diese Datei — Dokumentation des Skills
└── SKILL.md        # Skill-Definition für OpenCode
```

## Anwendungsbeispiele

- "Consult the council: Soll ich Microservices oder einen Monolithen nehmen?"
- "Lass den Council auf meine Architektur schauen – Fokus auf Sicherheit und Skalierbarkeit"
- "What would the council say about this API design?"
- "Ich brauche verschiedene Perspektiven auf meine Datenbank-Wahl: PostgreSQL vs. MongoDB"
