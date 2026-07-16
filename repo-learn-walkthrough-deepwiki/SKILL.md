Skill: Repo-Learn-Walkthrough (DeepWiki-Caveman + AgbACheck Edition)
Aufbau
plain
Copy
[repo]-learn/
├── README.md                    # 10 Zeilen: Was? Wie starten?
├── 00-overview/
│   ├── what-is-this.md          # 1 Absatz Projekt + 1 Absatz Problem
│   ├── tech-stack.md            # Tabelle: Crate | Warum | Alternative
│   └── architecture.md          # Mermaid-Diagramm + 5 Zeilen Text
├── 01-entry/
│   ├── main.md
│   ├── cargo-toml.md
│   └── first-run.md
├── 02-core-types/
│   ├── structs-enums.md
│   ├── traits.md
│   └── impl-blocks.md
├── 03-algorithm/
│   ├── logic-flow.md
│   ├── key-functions.md
│   └── complexity.md
├── 04-deps/
│   ├── [crate-1].md
│   ├── [crate-2].md
│   └── compare.md
├── 05-modules/
│   ├── module-tree.md
│   ├── api-design.md
│   └── re-exports.md
├── 06-errors/
│   ├── error-types.md
│   ├── propagation.md
│   └── handling-strategy.md
├── 07-tests/
│   ├── unit-tests.md
│   ├── integration-tests.md
│   └── mocks.md
├── 08-build-it/
│   ├── walkthrough.md
│   ├── exercises.md
│   └── final-challenge.md
├── 09-agbacheck/                # ← NEU
│   ├── architecture-review.md   # Struktur-Validierung
│   ├── design-decisions.md      # Trade-off-Analyse
│   ├── refactor-candidates.md   # Verbesserungspotenziale
│   ├── patterns-check.md        # Pattern-Konsistenz
│   └── evolution-path.md        # Zukunftsszenarien
└── _reference/
    └── [Original-Repo]
AgbACheck (09-agbacheck/)
architecture-review.md
Markdown
Copy
Code
Preview
# Architecture Review

## Layer-Check
| Layer | Datei | Verantwortung | Clean? |
|---|---|---|---|
| Entry | main.rs | CLI-Parsing, Runtime-Start | Ja |
| Core | lib.rs | Öffentliche API | Ja |
| Logic | parser.rs | Business-Regeln | Ja |
| Data | protocol.rs | Typen, Serde | Ja |

## Dependency-Richtung
protocol.rs → parser.rs → lib.rs → main.rs
plain
Copy
Keine Rückwärts-Abhängigkeit? Prüfe mit:
```bash
cargo modules generate graph | grep "ERROR"
Kopplung
protocol.rs kennt nur std
parser.rs kennt protocol.rs + serde
main.rs kennt alles (erlaubt)
Frage
Welche Datei ändert sich am häufigsten? Sollte isoliert sein.
plain
Copy

---

### design-decisions.md
```markdown
# Design Decisions

| Entscheidung | Context | Trade-off | Alternative |
|---|---|---|---|
| `tokio` statt `rayon` | 1000+ Dateien | Memory-Effizienz vs. Einfachheit | `rayon` bei <100 Dateien |
| Custom Parser statt `nom` | Einfache Grammatik | Kontrolle vs. Wartung | `nom` bei komplexer Grammatik |
| `Vec<u8>` statt `Bytes` | Kein Sharing nötig | Einfachheit vs. Zero-Copy | `bytes` bei Netzwerk-I/O |

## Check
Jede Entscheidung dokumentiert? Ja / Nein
Jede Alternative evaluiert? Ja / Nein
refactor-candidates.md
Markdown
Copy
Code
Preview
# Refactor Candidates

## Code-Smell 1
`src/scanner.rs:45` – `unwrap()` in Produktions-Code.

```rust
// JETZT
let config = read_config(path).unwrap();

// BESSER
let config = read_config(path)
    .with_context(|| format!("Config: {}", path))?;
Code-Smell 2
src/parser.rs:120 – Funktion > 50 Zeilen.
Aufteilen in:
parse_header()
parse_body()
validate_checksum()
Priorität
Table
#	Smell	Aufwand	Impact
1	unwrap()	10 min	Hoch
2	Funktion zu lang	30 min	Mittel
plain
Copy

---

### patterns-check.md
```markdown
# Patterns Check

## Konsistenz
| Pattern | Wo verwendet? | Überall gleich? |
|---|---|---|
| Error-Propagation (`?`) | parser.rs, scanner.rs | Ja |
| Builder-Pattern | config.rs | Nein – nur hier |
| Trait-Objects (`dyn`) | – | Nicht verwendet |

## Abweichungen
`src/main.rs:23` – `match` statt `?`. Warum?

```rust
// INKONSISTENT
match do_something() {
    Ok(v) => v,
    Err(e) => { eprintln!("{}", e); std::process::exit(1); }
}

// KONSISTENT
do_something().context("Fehler")?;
Empfehlung
Einheitliche Error-Strategie: anyhow in main, thiserror in Lib.
plain
Copy

---

### evolution-path.md
```markdown
# Evolution Path

## Jetzt
Single-Threaded Parser, Sync-I/O.

## Schritt 1: Parallelisierung
`rayon` für CPU-bound Workloads.

## Schritt 2: Streaming
`tokio::fs` + `tokio::io::AsyncBufRead` für große Dateien.

## Schritt 3: Plugin-System
`libloading` + Trait-Objects für externe Parser.

## Schritt 4: Distributed
`tokio` + `tonic` für Worker-Nodes.

## Frage
Welcher Schritt passt zum aktuellen Design ohne Rewrite?
Checkpoint-Integration
Jeder Level (01-08) endet mit einem Mini-AgbACheck:
Markdown
Copy
Code
Preview
## AgbACheck

- [ ] Dieses Modul hat keine Rückwärts-Abhängigkeit zu main.rs
- [ ] Alle `unwrap()` sind dokumentiert oder ersetzt
- [ ] Funktionen < 50 Zeilen oder begründete Ausnahme
- [ ] Fehler-Handling konsistent mit restlichem Projekt
- [ ] Ein neuer Entwickler versteht die Struktur in 5 Minuten
Prompt für die KI
"Analysiere Repository [URL]. Erstelle Learn-Walkthrough im DeepWiki-Style, Caveman-Edition.
Struktur: 00-overview, 01-08 modul-für-modul, 09-agbacheck.
AgbACheck muss enthalten:
architecture-review.md: Layer-Check, Dependency-Richtung, Kopplungsanalyse
design-decisions.md: Jede Kernentscheidung mit Context + Trade-off + Alternative
refactor-candidates.md: Code-Smells mit Jetzt/Besser-Vergleich, Priorisierung
patterns-check.md: Pattern-Konsistenz über das Repo, Abweichungen markieren
evolution-path.md: 3-4 mögliche Evolutionsschritte, passend zum aktuellen Design
Jeder Level 01-08 endet mit Mini-AgbACheck (5 Checkboxen).
Stil: Kurz, direkt, Stichpunkte, Tabellen, Code. Keine Sätze über 15 Wörter."
