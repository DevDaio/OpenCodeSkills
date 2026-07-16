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

## Installation

Jeden Skill als Ordner in das OpenCode-Skills-Verzeichnis kopieren:

```bash
cp -r <skill-name> ~/.config/opencode/skills/
```

## Struktur

```
opencode-skills/
├── README.md
├── exercism-java/     # Java-Übungen-Coach
│   ├── README.md
│   └── SKILL.md
├── llm-council/       # KI-Rat für Entscheidungen
│   ├── README.md
│   └── SKILL.md
├── syntax-drill/      # Syntax-Übungs-Generator
│   ├── README.md
│   ├── SKILL.md
│   └── JavaDrills_*.java
├── explain-code/      # Code-Erklärungen mit Diagrammen
│   ├── README.md
│   └── SKILL.md
└── repo-skiller/      # Lern-Repo-Builder
    ├── README.md
    └── SKILL.md
```

## Lizenz

MIT — frei zur Weiternutzung und Anpassung.
