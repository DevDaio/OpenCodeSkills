# Explain Code

Erklärt Code mit visuellen Diagrammen und Alltags-Analogien.

## Installation

```bash
# Für OpenCode (Mac/Linux)
cp -r explain-code ~/.config/opencode/skills/

# Für Claude Code (falls verwendet)
cp -r explain-code ~/.claude/skills/
```

## Aktivierung

Wird aktiviert bei:
- "Explain how this code works"
- "Wie funktioniert das?"
- "Kannst du mir diesen Code erklären?"
- "What does this function do?"
- "Teach me about this codebase"

## Methode

Jede Code-Erklärung folgt einem bewährten 4-Schritte-Ansatz:

### 1. Analogie
Starte mit einem Vergleich aus dem Alltag, der das Kernkonzept greifbar macht.

> "Eine HashMap ist wie ein Kleiderschrank mit beschrifteten Schubladen — du öffnest die Schublade 'Socken' und findest sofort alles, was du suchst, ohne die anderen Schubladen durchwühlen zu müssen."

### 2. Diagramm
ASCII-Art oder Mermaid-Diagramm, das Fluss, Struktur oder Beziehungen visualisiert.

```
        Request
           |
        [Router]
        /      \
   [Auth]    [Validation]
       \        /
      [Controller]
           |
       [Service]
           |
      [Database]
```

### 3. Schritt-für-Schritt
Zeilenweise Erklärung des Code-Ablaufs — was passiert wann und warum.

### 4. Gotcha
Hervorhebung einer typischen Fehlerquelle oder missverständlichen Stelle.

> "Achtung: `==` vergleicht bei Strings die Referenz, nicht den Inhalt. Nutze `.equals()`!"

## Beispiel

Bei einer Erklärung von `useEffect` in React:

```
Analogie: useEffect ist wie ein Wecker, den du stellst, bevor du
das Haus verlässt. Du sagst ihm "wann" (die Dependencies) und
"was dann passieren soll" (der Callback).

       Komponente mountet
              │
     useEffect wird registriert
              │
        [ Warte auf Änderungen ]
              │
     Dependency geändert? ──nein──→ weitermachen
              │ja
     Callback ausführen
              │
     Cleanup vom vorherigen Lauf
              │
     Neuer Effekt läuft
```

## Dateistruktur

```
explain-code/
├── README.md       # Diese Datei — Dokumentation des Skills
└── SKILL.md        # Skill-Definition für OpenCode
```

## Stil

- **Konversationell** – wie eine Erklärung unter Entwicklern, nicht wie ein Lehrbuch
- **Mehrere Analogien** bei komplexen Konzepten für verschiedene Lernzugänge
- **Keine Fachbegriffe ohne Erklärung** – jedes neue Konzept wird eingeführt, bevor es verwendet wird
