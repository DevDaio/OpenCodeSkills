---
name: explain-code
description: Explains code with visual diagrams and analogies. Use when explaining how code works, teaching about a codebase, or when the user asks "how does this work?"
---

# Explain Code Skill

When explaining code, always include:

1. **Start with an analogy**: Compare the code to something from everyday life
2. **Draw a diagram**: Use ASCII art to show the flow, structure, or relationships
3. **Walk through the code**: Explain step-by-step what happens
4. **Highlight a gotcha**: What's a common mistake or misconception?

Keep explanations conversational. For complex concepts, use multiple analogies.

## Output Format — Große Leinwand (Big Canvas)

Bei jeder Code-Erklärung dieser Art → **Mermaid-Diagramme in einer einzigen `.md`-Datei**.

### Struktur (10 Sektionen):
1. **Gesamtbild** (Architektur-Übersicht) — `graph TD` mit allen Layern
2. **Vollständige Routenkarte** (alle Routen mit Auth-Gates) — `flowchart LR`, gruppiert in public/protected/unprotected
3. **Anfrage-Lebenszyklus** (sequenzielle Abläufe) — `sequenceDiagram` mit `alt`-Blöcken, `Note over`
4. **Komponentenbaum** (Hierarchie) — `graph TD`, parent/child, gestrichelte Linien für Props
5. **Datenfluss** (komplette PUT/GET/DELETE-Durchläufe) — `sequenceDiagram` mit allen Teilnehmern
6. **Überwachungs-Schleife** (Timer-basiertes Monitoring) — `flowchart` mit `subgraph` für Loop
7. **Datenbank-Schema** (Tabellen + Beziehungen) — `classDiagram`, 5 Tabellen mit Cardinalities
8. **Sitzungs-Zustand** (Token-Lebensdauer) — `flowchart`, client-side + server-side subgraphs
9. **Frontend-Abfrage-Mechanismen** (Polling) — `flowchart LR`, 4 Polling-Strategien
10. **Start/Konfiguration** (Boot-Sequenz) — `flowchart TD`, dotenv → pool → create tables → spawn → serve

### Mermaid-Syntax-Regeln (fixiert):
| Regel | Beschreibung |
|-------|-------------|
| **Kein `\"` im Labeltext** | `HO["{status: ok}"]` — nie `HO["{\"status\":\"ok\"}"]` |
| **Keine 3+ Dashs bei Pfeilen** | `-->>` gültig, `--->>` ungültig (`API-->>FEZ` statt `API--->>FEZ`) |
| **Labels auf Deutsch** | `Nutzer`, `Endpunkt`, `Sitzungen`, `Abfrage` — nie `User`, `Endpoint`, `Sessions`, `Query` |
| **Keine `&lt;`/`&gt;` im Message-Text** | Nur in `[...]`-Node-Labels erlaubt (flowchart/graph). In `sequenceDiagram`-Messages → Klartext |
| **`<br/>` nur in `[...]`** | In `graph TD`/`flowchart`-Nodes. Nicht in `sequenceDiagram`-Messages |
| **`---` als Sektionen-Trenner** | Zwischen Mermaid-Blöcken, nicht innerhalb |
| **Zustands-Tabelle nach jedem Graphen** | Markdown-Tabelle mit: Aspekt / Wert / Details |

### Mermaid-Pfeil-Typen (nur diese):
- `->` / `-->` / `->>` / `-->>` / `-x` / `--x` / `-.->`
- Kein `--->` / `--->>` / `---->`

### Farben (CSS-Style-Block):
```mermaid
style NODE fill:#HEX,color:#fff
```

### Datei-Struktur (am Ende):
Anhang mit Baum-Ansicht der relevanten Dateien.

## Source

`~/.claude/skills/explain-code/SKILL.md`