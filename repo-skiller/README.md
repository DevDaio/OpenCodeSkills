# Repo Skiller

Baut ein strukturiertes Lern-Repository aus einem vorhandenen Codebase. Erzeugt annotierten Code, Dependency-Analysen, Konzept-Dokumente, Übungen und Referenzmaterial.

## Installation

```bash
# Für OpenCode (Mac/Linux)
cp -r repo-skiller ~/.config/opencode/skills/

# Für Claude Code (falls verwendet)
cp -r repo-skiller ~/.claude/skills/
```

## Aktivierung

Wird aktiviert bei:
- "Build a learning repository from this project"
- "Create a study guide for this codebase"
- "Deep dive dieses Repository"
- "Erstelle Übungen aus diesem Code"
- "Dokumentiere alle Dependencies"

## Output-Struktur

Das Skill erzeugt `Repo-Skillz/` im Ziel-Projektverzeichnis:

```
<PROJEKT>-learn/
├─ 00-UEBERSICHT/
│  ├─ README.md            (Willkommen, Lernziele)
│  ├─ ARCHITEKTUR.md       (Mermaid-Diagramm)
│  ├─ DEPENDENCY-GRAPH.md  (Abhaengigkeiten als Graph)
│  ├─ LERNPFAD.md          (Lern-Reihenfolge)
│  └─ GLOSSAR.md           (Fachbegriffe)
│
├─ 01-CORE-KONZEPTE/
│  ├─ konzept-1.md         (Deepwiki-Style)
│  └─ UEBUNGEN/
│
├─ 02-DEPENDENCIES/
│  ├─ <dependency-1>/
│  │  ├─ WAS-IST-DAS.md
│  │  ├─ WIE-NUTZEN.md
│  │  ├─ BEISPIELE/
│  │  └─ MINI-TUTORIAL.md
│
├─ 03-CODE-ERKLAERT/
│  └─ src/
│     └─ datei.js          (JEDER Block annotiert)
│
├─ 04-CODE-ZUM-NACHBAUEN/
│  ├─ src/              (TODOs statt Implementation)
│  └─ LOESUNGEN/
│
├─ 05-UEBUNGEN/
│  ├─ Level-1-Anfaenger/
│  ├─ Level-2-Mittel/
│  ├─ Level-3-Fortgeschritten/
│  └─ Level-4-Expert/
│
└─ 06-REFERENZ/
   ├─ API-REFERENCE.md
   ├─ CHEATSHEET.md
   ├─ TROUBLESHOOTING.md
   └─ WEITERFUEHRENDE-RESSOURCEN.md
```

## Arbeitsschritte

### 1. Analyse-Phase
- **Repo-Scan**: Alle Dateien erfassen (auch `.env.example`, `.gitignore`)
- **Dependencies parsen**: `package.json`, `requirements.txt`, `Cargo.toml`, `go.mod`, `Gemfile`
- **API-Endpunkte finden**, Environment-Vars dokumentieren, Configs parsen
- **Dependency-Tiefenanalyse**: WAS, WARUM, WO, WIE, ALTERNATIVEN, TUTORIAL

### 2. Code-Annotation
Jeder signifikante Code-Block bekommt einen detaillierten Kommentar-Header:

```javascript
/* ═══════════════════════════════════════════════════════
 * WAS: Kurzbeschreibung
 * ZWECK: Warum existiert das?
 * INPUT: Parameter
 * OUTPUT: Rueckgabewert
 * DEPENDENCIES: Verweise ins Lern-Repo
 * KONZEPTE: Verweise auf Konzept-Dokumente
 * WICHTIG: Edge Cases, Performance, Fehler
 * LERN-TIPP: Voraussetzungen
 * ═══════════════════════════════════════════════════════ */
```

### 3. Übungen (4 Levels)

| Level | Typen |
|-------|-------|
| 1 – Anfänger | Lückentexte, Multiple Choice, Debugging |
| 2 – Mittel | Funktion schreiben, Refactoring, Tests |
| 3 – Fortgeschritten | Performance, Edge Cases, Patterns |
| 4 – Expert | Mini-Projekt, Architektur, Code Review |

Jede Übung hat: `README.md` (Aufgabe) + `starter/` (Gerüst) + `solution/` (Musterlösung)

## Framework-Support

Erkannte Frameworks bekommen spezifische Tiefendokumentation:

| Framework | Dokumentierte Konzepte |
|-----------|----------------------|
| React | Alle Hooks, Lifecycle, Props/State, Context, Virtual DOM, Patterns |
| Vue | Composition API, Reactivity, Directives, Slots, Pinia |
| Angular | Modules, Components, DI, RxJS, Pipes, Guards |
| Django | MTV, ORM, Middleware, Views, Admin, Auth |
| Express | Middleware, Routing, Error Handling, Templates |
| Next.js | SSR/SSG/ISR, App Router, Server Components |
| Spring | IoC/DI, AOP, MVC, Security, Data JPA |

## Quality Checks

Der Skill führt automatische Checks durch:
- Vollständigkeit (alle Dateien, exports, imports)
- Kommentar-Qualität (Länge, Tiefe, Vollständigkeit)
- Cross-References (tote Links, fehlende Rückverweise)
- Didaktik (Progression, Wiederholung, kein Concept-Skipping)
- Übungs-Qualität (lösbar? Lösungen? Hints?)

## Dateistruktur (dieses Repo)

```
repo-skiller/
├── README.md       # Diese Datei — Dokumentation des Skills
└── SKILL.md        # Skill-Definition für OpenCode
```
