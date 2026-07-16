---
name: repo-learn-walkthrough
description: >
  Generate learn walkthrough from any repo where working code is replaced with
  guided pseudocode/TODO instructions. Learner implements each step themselves.
  Includes AgbACheck validation. Multi-level structure: overview → entry → core-types
  → algorithm → deps → modules → errors → tests → build-it → agbacheck.
  Trigger: "deepwiki walkthrough", "learn walkthrough", "agbacheck", "repo walkthrough",
  "generate walkthrough", "create walkthrough", "code-along", "codier-lernen".
---

## OUTPUT-PFAD

Der generierte Walkthrough wird IMMER unter `$HOME/Stack_Teacher/[repo]-learn/`
abgelegt. Dieser Ordner ist der zentrale Lernort des Users.

# NEU: Detail-Analyse statt Stufen-Dogma

**Altes Denken:** Lernender geht stur 10 Stufen durch.
**Neues Denken:** JEDE Datei wird komplett auseinandergenommen. Der Lernende versteht
_was_ passiert, _warum_ es so gemacht wurde, und bekommt klare TODOs + Tipps.

Die Ordner-Struktur (00-overview, 01-entry, ...) ist nur eine grobe Sortierung.
Der eigentliche Inhalt ist die **Datei-für-Datei-Tiefenanalyse**.

## Kernprinzip

Jede relevante Datei im Repo bekommt eine eigene Analyse-Seite mit:

```
[dateiname]-analysis.md
├── WAS:    Was macht diese Datei? (1 Satz)
├── WARUM:  Warum gibt es sie? Welches Problem löst sie?
├── KONTEXT: Wer importiert/ruft sie auf? Wovon hängt sie ab?
├── CODE-BLOCKS:
│   ├── Block 1: [Imports] — WAS + WARUM + TIPPS + TODO
│   ├── Block 2: [Typdefinitionen] — WAS + WARUM + TIPPS + TODO
│   ├── Block 3: [Funktion X] — WAS + WARUM + TIPPS + TODO
│   └── ...
├── ZUSAMMENFASSUNG: Was haben wir gelernt?
└── ÜBUNGEN: 2-3 Aufgaben zum Vertiefen
```

## Jeder Code-Block

Jeder logische Abschnitt im Code wird einzeln betrachtet:

```
### Block: [Funktions-/Typ-Name]

[CODE als Kommentar/Pseudocode]

**WAS passiert hier?**
_Erklärung auf Zeilen-Ebene: Was tut dieser Code konkret?_

**WARUM wurde das so gemacht?**
_Welche Alternative gab es? Warum diese Lösung? Welches Problem wird gelöst?_

**TIPPS**
- Häufige Fehler bei diesem Pattern
- Performance-Implikationen
- Sicherheitsaspekte
- Lesbarkeit/Wartbarkeit

**TODO**
- Was der Lernende selbst schreiben soll
- Konkrete Anweisungen: Signatur, Parameter, Return, Fehlerbehandlung

**ZUSAMMENHANG**
_Wie interagiert dieser Code mit anderen Dateien? Wer ruft ihn auf?_
```

## Code-Replacement Pattern

```
// ============================================================
// BLOCK: create_account
// WAS:   Legt neuen User in der DB an
// WARUM: bcrypt-Hash, damit Passwörter nie im Klartext stehen
// ============================================================
//
// TIPPS:
//   - sqlx::query_as mit RETURNING * gibt das eingefügte Row zurück
//   - $1, $2 sind Platzhalter (bindet Werte sicher gegen SQL-Injection)
//   - Der Fehlerfall (z.B. UNIQUE-Verletzung) wird mit ? nach oben gereicht
//
// TODO: Implementiere create_account
//   - Parameter: pool: &PgPool, email: &str, password: &str
//   - SQL: INSERT INTO "user" (emailadress, password) VALUES ($1, $2) RETURNING *
//   - Rückgabe: Result<User, sqlx::Error>
//   - Nutze query_as mit fetch_one
```

## NACHBAU — 1:1-Repo-Kopie, Code durch Kommentare ersetzt

Der `nachbau/`-Ordner spiegelt die **exakte Ordnerstruktur des Original-Repos**.
Jede relevante Datei liegt am selben Pfad — aber ihr Code ist vollständig
durch Kommentare ersetzt.

Jeder Kommentar-Block pro Code-Abschnitt:
- **INPUT/OUTPUT**: Was geht rein, was kommt raus?
- **Erklärung**: Was tut dieser Abschnitt?
- **Anweisung**: Wie schreibe ich ihn?
- **Tipps**: Stolperfallen, Alternativen

### Wichtig: 1:1-Pfadtreue

```diff
- FALSCH: nachbau/main.rs
+ RICHTIG: nachbau/Backend/API/src/main.rs
+ RICHTIG: nachbau/Frontend/ACM_Frontend/src/api.js
```

Der Lernende baut so **das gesamte Projekt** an den originalen Pfaden nach.

### Nachbau-Template (pro Datei)

```
// ============================================================
// DATEI: main.rs
// BAUE DIESE DATEI VOLLSTÄNDIG NACH
// ============================================================
//
// ╔════════════════════════════════════════════════════════════╗
// ║  INPUT                                                     ║
// ║  Was nimmt diese Datei/Programm entgegen?                 ║
// ╚════════════════════════════════════════════════════════════╝
// - DATABASE_URL aus .env oder Umgebungsvariable
// - HTTP-Requests (JSON-Body, Query-Parameter)
//
// ╔════════════════════════════════════════════════════════════╗
// ║  OUTPUT                                                    ║
// ║  Was produziert diese Datei?                               ║
// ╚════════════════════════════════════════════════════════════╝
// - JSON-Responses (LoginRes, ErrorRes, Vec<EndpointExtended>)
// - HTTP-Statuscodes (200, 401, 404, 409, 500)
//
// ─── 1. MODULE & IMPORTS ───
// ...
//
// ─── 2. TYPEN ───
// ...
//
// ─── 3. FUNKTIONEN ───
// ...
```

## AgbACheck (optional, nicht mehr obligatorisch pro Level)

Nur noch ein Ordner `agbacheck/` am Ende mit den wichtigsten Analyse-Fragen.
Nicht mehr pro Level.

## Verhältnis

| Element | Anteil |
|---------|--------|
| WAS/WARUM (Kontext) | ~50% |
| Code (Pseudocode/TODOs) | ~30% |
| Tipps | ~20% |

## Quality Checklist

- JEDE Datei hat eigene Analyse
- JEDER Code-Block in der Datei wird separat erklärt
- "WARUM" ist PFLICHT (nicht nur "WAS")
- Tipps sind konkret und praxisnah
- Zusammenhänge zwischen Dateien werden sichtbar
- Lernende verstehen Design-Entscheidungen, nicht nur Syntax
- **nachbau/ spiegelt Repo-Struktur 1:1** (gleiche Pfade wie Original)
- **nachbau/ enthält NUR Kommentare** — jeder Block: INPUT/OUTPUT + Erklärung + Anweisung + Tipp
