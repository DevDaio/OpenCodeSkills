# Skills

Meine Sammlung von [OpenCode](https://opencode.ai) Skills.

## Skills

| Skill | Beschreibung |
|-------|-------------|
| [exercism-java](./exercism-java/) | Hilft beim Lösen von Exercism Java-Aufgaben durch Fragen statt fertige Lösungen |
| [llm-council](./llm-council/) | Mehrere KI-Perspektiven auf eine Frage, Diskussion und Abstimmung |
| [syntax-drill](./syntax-drill/) | Generiert Lückentext-Übungen für Java-Syntax-Training |
| [explain-code](./explain-code/) | Erklärt Code mit Alltags-Analogien und ASCII-Diagrammen |
| [repo-skiller](./repo-skiller/) | Baut komplette Lern-Repositories aus vorhandenem Code |
| [cavecrew](./cavecrew/) | Delegiert Teilaufgaben an Sub-Agents (Investigator, Builder, Reviewer) – spart Kontext |
| [caveman](./caveman/) | Ultra-kompakte Kommunikation (~75% weniger Token) |
| [caveman-commit](./caveman-commit/) | Komprimierte Commit-Messages im Conventional-Commits-Format |
| [caveman-compress](./caveman-compress/) | Komprimiert Memory-Files in Caveman-Format |
| [caveman-help](./caveman-help/) | Quick-Reference für alle Caveman-Modi |
| [caveman-review](./caveman-review/) | Ultra-kompakte Code-Review-Kommentare |
| [caveman-stats](./caveman-stats/) | Zeigt reale Token-Ersparnis der Caveman-Modi |
| [customize-opencode](./customize-opencode/) | Editiert Opencode-eigene Konfiguration (opencode.json, Agents, Skills, MCP) |
| [repo-to-comprehensive-walkthrough](./repo-to-comprehensive-walkthrough/) | 8-stufiger Lernpfad (Archäologie → Integration) mit Anti-Patterns |
| [repo-learn-walkthrough-deepwiki](./repo-learn-walkthrough-deepwiki/) | DeepWiki-Caveman + AgbACheck Edition des Walkthrough-Generators |

## Installation

Jeden Skill als Ordner in das OpenCode-Skills-Verzeichnis kopieren:

```bash
cp -r <skill-name> ~/.config/opencode/skills/
```

## Struktur

```
opencode-skills/
├── README.md
├── exercism-java/           # Java-Übungen-Coach
│   ├── README.md
│   └── SKILL.md
├── llm-council/             # KI-Rat für Entscheidungen
│   ├── README.md
│   └── SKILL.md
├── syntax-drill/            # Syntax-Übungs-Generator
│   ├── README.md
│   ├── SKILL.md
│   └── JavaDrills_*.java
├── explain-code/            # Code-Erklärungen mit Diagrammen
│   ├── README.md
│   └── SKILL.md
├── repo-skiller/            # Lern-Repo-Builder
│   ├── README.md
│   └── SKILL.md
├── cavecrew/                # Sub-Agent-Delegation
│   └── SKILL.md
├── caveman/                 # Kompakt-Kommunikation
│   └── SKILL.md
├── caveman-commit/          # Commit-Messages
│   └── SKILL.md
├── caveman-compress/        # Memory-Kompression
│   └── SKILL.md
├── caveman-help/            # Caveman-Referenz
│   └── SKILL.md
├── caveman-review/          # Kompakt-Review
│   └── SKILL.md
├── caveman-stats/           # Token-Statistiken
│   └── SKILL.md
├── customize-opencode/      # Opencode-Konfiguration
│   └── SKILL.md
├── repo-to-comprehensive-walkthrough/  # 8-stufiger Lernpfad (Variante)
│   └── SKILL.md
└── repo-learn-walkthrough-deepwiki/    # DeepWiki-Caveman-Edition
    └── SKILL.md
```

## Lizenz

MIT — frei zur Weiternutzung und Anpassung.
