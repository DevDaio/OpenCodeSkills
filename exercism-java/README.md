# Exercism Java Skill

Hilft, Exercism Java-Aufgaben eigenständig zu lösen — durch gezielte Fragen, Tipps und Denkanstöße statt fertige Lösungen.

## Installation

Kopiere den Ordner `exercism-java/` in dein OpenCode-Skills-Verzeichnis:

```bash
# Für OpenCode (Mac/Linux)
cp -r exercism-java ~/.config/opencode/skills/

# Für Claude Code (falls verwendet)
cp -r exercism-java ~/.claude/skills/
```

## Aktivierung

Der Skill wird **automatisch aktiviert**, wenn der Kontext auf eine Exercism Java-Aufgabe hindeutet:
- Dateien in `src/main/java/*.java` mit einer teilweise implementierten Klasse
- Eine `README.md` im Elternverzeichnis, die "Exercism" oder "Instructions" enthält

## Funktionsweise

| Phase | Beschreibung |
|-------|-------------|
| 0. Kein Code | Nie fertigen Code zeigen — nur Konzepte, Methoden und Hinweise nennen |
| 0.1 SSOT | Die `README.md` der Aufgabe ist die Single Source of Truth |
| 1. Kontext lesen | `README.md` analysieren, Methode identifizieren |
| 2. Schrittweise | Methode für Methode vorgehen |
| 3. Fragen stellen | Konkrete Fragen, die zum nächsten Denkschritt führen |
| 4. Tipps bei Bedarf | `Math.min()`, 0-Index, etc., wenn der User feststeckt |
| 5. Learnings ablegen | Nach Abschluss als Tabelle in `~/exercism/Exercism-Exercise-Learnings/<level>.md` speichern |
| 6. README pflegen | Vault-README mit neuer Übung aktualisieren |

## Dateistruktur

```
exercism-java/
├── README.md       # Diese Datei — Dokumentation des Skills
└── SKILL.md        # Skill-Definition für OpenCode
```

## Wichtige Java-Konzepte (aus dem Skill)

- **Arrays sind 0-indexiert**: `arr[0]` ist das erste, `arr[arr.length-1]` das letzte Element
- **`Math.min(a, b)`**: Gibt den kleineren von zwei Werten zurück
- **`length` vs `length()`**: Array → Feld, String → Methode
- **Instanz vs. statisch**: Nicht-statische Methoden brauchen Instanzvariablen
- **`break`**: Bricht Schleifen vorzeitig ab

## Integration

Der Skill speichert Learnings in `~/exercism/Exercism-Exercise-Learnings/` im Tabellenformat:

```markdown
# java/hello-world

Datum: 2026-07-15

| Thema | Erkenntnis |
|-------|------------|
| Klassen | Jede Java-Klasse braucht eine main-Methode zum Start |
| Strings | `System.out.println()` gibt Text auf der Konsole aus |
```

## Eigenes Lern-Vault

Das Learning-Vault unter `~/exercism/Exercism-Exercise-Learnings/` enthält:
- Eine Datei pro absolvierter Übung (`<track>/<slug>.md`)
- Eine zentrale `README.md` mit Übersicht aller Übungen
