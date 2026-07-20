# Skills

Sammlung von [OpenCode](https://opencode.ai) Skills.

## Skills

| Skill | Beschreibung | Autor |
|-------|-------------|-------|
| [stepwise](./stepwise/) | Projektphasen-Begleitung für das Invoice-Management (Spring Boot, JPA, Thymeleaf) | selbst erstellt |
| [exercism-java](./exercism-java/) | Hilft beim Lösen von Exercism Java-Aufgaben durch Fragen statt fertige Lösungen | selbst erstellt |
| [llm-council](./llm-council/) | Mehrere KI-Perspektiven auf eine Frage, Diskussion und Abstimmung | selbst erstellt |
| [syntax-drill](./syntax-drill/) | Generiert Lückentext-Übungen für Java-Syntax-Training | selbst erstellt |
| [explain-code](./explain-code/) | Erklärt Code mit Alltags-Analogien und ASCII-Diagrammen | selbst erstellt |
| [repo-skiller](./repo-skiller/) | Baut komplette Lern-Repositories aus vorhandenem Code | selbst erstellt |
| [repo-to-comprehensive-walkthrough](./repo-to-comprehensive-walkthrough/) | 8-stufiger Lernpfad (Archäologie → Integration) mit Anti-Patterns | selbst erstellt |
| [repo-learn-walkthrough-deepwiki](./repo-learn-walkthrough-deepwiki/) | DeepWiki-Caveman + AgbACheck Edition des Walkthrough-Generators | selbst erstellt |
| [cavecrew](./cavecrew/) | Delegiert Teilaufgaben an Sub-Agents – spart Kontext | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
| [caveman](./caveman/) | Ultra-kompakte Kommunikation (~75% weniger Token) | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
| [caveman-commit](./caveman-commit/) | Komprimierte Commit-Messages im Conventional-Commits-Format | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
| [caveman-compress](./caveman-compress/) | Komprimiert Memory-Files in Caveman-Format | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
| [caveman-help](./caveman-help/) | Quick-Reference für alle Caveman-Modi | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
| [caveman-review](./caveman-review/) | Ultra-kompakte Code-Review-Kommentare | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
| [caveman-stats](./caveman-stats/) | Zeigt reale Token-Ersparnis der Caveman-Modi | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) |
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
├── stepwise/                         # Selbst erstellt
├── exercism-java/                    # Selbst erstellt
├── llm-council/                      # Selbst erstellt
├── syntax-drill/                     # Selbst erstellt
├── explain-code/                     # Selbst erstellt
├── repo-skiller/                     # Selbst erstellt
├── repo-to-comprehensive-walkthrough/  # Selbst erstellt
├── repo-learn-walkthrough-deepwiki/    # Selbst erstellt
├── customize-opencode/               # Selbst erstellt
├── cavecrew/                         # JuliusBrussee/caveman
├── caveman/ + -commit, -compress, -help, -review, -stats  # JuliusBrussee/caveman
└── ...

## Lizenz

MIT — frei zur Weiternutzung und Anpassung.
