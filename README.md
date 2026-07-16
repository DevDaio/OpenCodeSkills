# Skills

Sammlung von [OpenCode](https://opencode.ai) Skills.

## Skills

| Skill | Beschreibung | Autor |
|-------|-------------|-------|
| [exercism-java](./exercism-java/) | Hilft beim Lösen von Exercism Java-Aufgaben durch Fragen statt fertige Lösungen | selbst erstellt |
| [llm-council](./llm-council/) | Mehrere KI-Perspektiven auf eine Frage, Diskussion und Abstimmung | selbst erstellt |
| [syntax-drill](./syntax-drill/) | Generiert Lückentext-Übungen für Java-Syntax-Training | selbst erstellt |
| [explain-code](./explain-code/) | Erklärt Code mit Alltags-Analogien und ASCII-Diagrammen | selbst erstellt |
| [repo-skiller](./repo-skiller/) | Baut komplette Lern-Repositories aus vorhandenem Code | selbst erstellt |
| [repo-to-comprehensive-walkthrough](./repo-to-comprehensive-walkthrough/) | 8-stufiger Lernpfad (Archäologie → Integration) mit Anti-Patterns | selbst erstellt |
| [repo-learn-walkthrough-deepwiki](./repo-learn-walkthrough-deepwiki/) | DeepWiki-Caveman + AgbACheck Edition des Walkthrough-Generators | selbst erstellt |
| [cavecrew](./cavecrew/) | Delegiert Teilaufgaben an Sub-Agents – spart Kontext | [OpenCode Built-in](https://opencode.ai) |
| [caveman](./caveman/) | Ultra-kompakte Kommunikation (~75% weniger Token) | [OpenCode Built-in](https://opencode.ai) |
| [caveman-commit](./caveman-commit/) | Komprimierte Commit-Messages im Conventional-Commits-Format | [OpenCode Built-in](https://opencode.ai) |
| [caveman-compress](./caveman-compress/) | Komprimiert Memory-Files in Caveman-Format | [OpenCode Built-in](https://opencode.ai) |
| [caveman-help](./caveman-help/) | Quick-Reference für alle Caveman-Modi | [OpenCode Built-in](https://opencode.ai) |
| [caveman-review](./caveman-review/) | Ultra-kompakte Code-Review-Kommentare | [OpenCode Built-in](https://opencode.ai) |
| [caveman-stats](./caveman-stats/) | Zeigt reale Token-Ersparnis der Caveman-Modi | [OpenCode Built-in](https://opencode.ai) |
| [customize-opencode](./customize-opencode/) | Editiert Opencode-eigene Konfiguration | selbst erstellt |

## Installation

Jeden Skill als Ordner in das OpenCode-Skills-Verzeichnis kopieren:

```bash
cp -r <skill-name> ~/.config/opencode/skills/
```

## Struktur

```
opencode-skills/
├── README.md
├── exercism-java/                    # Selbst erstellt
├── llm-council/                      # Selbst erstellt
├── syntax-drill/                     # Selbst erstellt
├── explain-code/                     # Selbst erstellt
├── repo-skiller/                     # Selbst erstellt
├── repo-to-comprehensive-walkthrough/  # Selbst erstellt
├── repo-learn-walkthrough-deepwiki/    # Selbst erstellt
├── customize-opencode/               # Selbst erstellt
├── cavecrew/                         # OpenCode Built-in
├── caveman/ + -commit, -compress, -help, -review, -stats  # OpenCode Built-in
└── ...

## Lizenz

MIT — frei zur Weiternutzung und Anpassung.
