---
name: repo-skiller
description: Use when a user asks you to build/analyze/create a complete learning repository, study guide, code walkthrough, tutorial, or annotated codebase from an existing project. Also use when asked to "deep dive" a repository, create exercises/workshops from code, document dependencies in detail, or build a structured learning path from source code. Do NOT use for simple code reviews, single-file explanations, or general questions about programming concepts.
---

# Code Learning Repository Builder

Build a complete, standalone learning repository from a target codebase. The output is a new directory named `Repo-Skillz` created inside the target project directory, containing deeply annotated code, dependency breakdowns, concept docs, graded exercises, and reference materials.

---

## 1. TIEFE ANALYSE-PHASE

### Repo-Scanning

1. **Inventarisiere ALLE Dateien** (auch versteckte: `.env.example`, `.gitignore`, `.editorconfig`, etc.)
2. **Parse Package-Manager-Dateien:**
   - `package.json` → dependencies, devDependencies, peerDependencies, versions
   - `requirements.txt` / `pyproject.toml` / `Pipfile`
   - `Cargo.toml` / `Cargo.lock`
   - `go.mod` / `go.sum`
   - `Gemfile` / `Gemfile.lock`
3. **Finde ALLE Dependencies** inkl. transitiver (check lock-files)
4. **Kategorisiere**: Production vs Dev vs Peer
5. **Finde API-Endpunkte** (bei Backend-Projekten)
6. **Dokumentiere Environment-Variables** (`.env.example`, `process.env`, `os.getenv`)
7. **Parse Config-Dateien**: `.eslintrc`, `tsconfig.json`, `vite.config.ts`, `Dockerfile`, `docker-compose.yml`, etc.

### Dependency-Tiefenanalyse — für JEDE Dependency erstelle einen Eintrag:

```
Feld          | Beschreibung
------------- | ------------
WAS MACHT ES? | Library-Zweck in 1-2 Sätzen
WARUM?        | Warum im Projekt nötig?
WO?           | Alle Dateien + Zeilen, die sie nutzen
WIE?          | Welche Funktionen/Methoden werden verwendet?
ALTERNATIVEN  | Vergleichbare Libraries
TUTORIAL      | Mini-Tutorial (Install → Setup → Beispiel)
```

### Framework-Spezial-Behandlung

Erkenne das Framework und dokumentiere dessen Core-Konzepte:

| Framework | Dokumentiere |
|-----------|-------------|
| React     | Alle Hooks, Lifecycle, Props/State, Context, Reconciliation, Virtual DOM, JSX, Event Handling, Conditional Rendering, Lists & Keys, Forms, Refs, Performance |
| Vue       | Composition API, Options API, Reactivity System, Directives, Lifecycle Hooks, Slots, Vuex/Pinia, Router |
| Angular   | Modules, Components, Services, Dependency Injection, RxJS, Pipes, Directives, Guards |
| Django    | MTV Pattern, ORM, Middleware, Views (FBV/CBV), Templates, Admin, Auth, Signals |
| Flask     | App Factory, Blueprints, Extensions, Request/Response Cycle, Templates, SQLAlchemy |
| Express   | Middleware, Routing, Error Handling, Template Engines, Static Files |
| Next.js   | SSR/SSG/ISR, App Router, Pages Router, Server Components, API Routes, Middleware |
| Spring    | IoC/DI, AOP, MVC, Security, Data JPA, Actuator, Configuration |

---

## 2. STRUKTUR-ERSTELLUNG

Erstelle folgende Ordner-Hierarchie im Zielverzeichnis:

```
📁 <PROJEKT>-learn/
├─ 📁 00-ÜBERSICHT/
│  ├─ README.md            (Willkommen! Wie nutzen? Lernziele)
│  ├─ ARCHITEKTUR.md       (Großes Bild mit Mermaid-Diagramm)
│  ├─ DEPENDENCY-GRAPH.md  (Mermaid graph der Abhängigkeiten)
│  ├─ LERNPFAD.md          (Reihenfolge zum Durcharbeiten)
│  └─ GLOSSAR.md           (Alle Fachbegriffe mit Definitionen)
│
├─ 📁 01-CORE-KONZEPTE/
│  ├─ konzept-1.md         (Deepwiki-Style — siehe §4)
│  ├─ konzept-2.md
│  └─ 📁 ÜBUNGEN/           (Konzept-spezifische Mini-Übungen)
│
├─ 📁 02-DEPENDENCIES/
│  ├─ 📁 <dependency-1>/
│  │  ├─ WAS-IST-DAS.md
│  │  ├─ WIE-NUTZEN.md
│  │  ├─ 📁 BEISPIELE/
│  │  └─ MINI-TUTORIAL.md
│  └─ 📁 <dependency-2>/ ...
│
├─ 📁 03-CODE-ERKLÄRT/      (Original-Code mit Kommentaren — siehe §3)
│  ├─ 📁 src/               (Spiegel der Original-Struktur)
│  │  ├─ datei1.js          (JEDER Block annotiert)
│  │  └─ datei2.js
│  └─ STRUKTUR-MAP.md       (Mermaid class/flow diagram)
│
├─ 📁 04-CODE-ZUM-NACHBAUEN/ (Todo-Versionen — siehe §3)
│  ├─ 📁 src/
│  │  ├─ datei1.js          (nur TODOs + Input/Output specs)
│  │  └─ datei2.js
│  └─ 📁 LÖSUNGEN/          (separat, nicht spicken!)
│
├─ 📁 05-ÜBUNGEN/
│  ├─ 📁 Level-1-Anfänger/
│  ├─ 📁 Level-2-Mittel/
│  ├─ 📁 Level-3-Fortgeschritten/
│  └─ 📁 Level-4-Expert/
│
└─ 📁 06-REFERENZ/
   ├─ API-REFERENCE.md
   ├─ CHEATSHEET.md
   ├─ TROUBLESHOOTING.md
   └─ WEITERFÜHRENDE-RESSOURCEN.md
```

---

## 3. KOMMENTIERUNG-STANDARD

### Für annotierten Code (`03-CODE-ERKLÄRT/`):

Jeder signifikante Block bekommt diesen Header:

```javascript
/* ═══════════════════════════════════════════════════════
 * 📦 WAS MACHT DIESER BLOCK?
 * Kurze Beschreibung (1-2 Sätze)
 *
 * 🎯 ZWECK:
 * Warum existiert das? Welches Problem löst es?
 *
 * 📥 INPUT:
 * - parameter1: Type - Beschreibung
 * - parameter2: Type - Beschreibung
 *
 * 📤 OUTPUT:
 * - Rückgabewert: Type - Was bedeutet es?
 *
 * 🔗 DEPENDENCIES:
 * - useState (React Hook) → siehe 02-DEPENDENCIES/react/hooks/useState.md
 * - lodash.debounce → siehe 02-DEPENDENCIES/lodash/debounce.md
 *
 * 💡 KONZEPTE:
 * - Debouncing → siehe 01-CORE-KONZEPTE/debouncing.md
 * - Event Handling → siehe 01-CORE-KONZEPTE/events.md
 *
 * ⚠️ WICHTIG ZU WISSEN:
 * - Edge Cases
 * - Performance-Implikationen
 * - Häufige Fehler
 *
 * 🎓 LERN-TIPP:
 * Was sollte man verstehen, bevor man das liest?
 * ═══════════════════════════════════════════════════════ */
```

Jede signifikante Zeile bekommt einen Inline-Kommentar.

### Für Todo-Versionen (`04-CODE-ZUM-NACHBAUEN/`):

```javascript
/* ═══════════════════════════════════════════════════════
 * 🎯 AUFGABE: [Kurze Beschreibung]
 *
 * 📥 ERWARTETER INPUT:
 * - parameter1: Type - Beschreibung
 *
 * 📤 ERWARTETER OUTPUT:
 * - Return: Type - Was soll rauskommen?
 *
 * 💭 HINWEISE:
 * 1. Schritt 1
 * 2. Schritt 2 beachten
 * 3. Edge Case X nicht vergessen!
 *
 * ✅ TEST:
 * Beispiel-Input → Erwarteter Output
 * ═══════════════════════════════════════════════════════ */

function beispielFunktion(param1, param2) {
    // TODO: Implementiere hier!
    // TIPP: Verwende Array.map() für...

    // TODO: Error Handling hinzufügen

    // TODO: Return-Statement
}
```

---

## 4. DEEPWIKI-INTEGRATION

Jede Concept-Seite (`01-CORE-KONZEPTE/<konzept>.md`) folgt diesem Template:

```markdown
# Konzept: <Name>

## 🎯 Was ist das?
[Erklärung in 2-3 Sätzen, für Anfänger verständlich]

## 🤔 Warum brauchen wir das?
[Motivation – welches Problem löst es?]

## 🔧 Wie funktioniert es?
[Technische Details mit Erklärungen]

## 💻 Code-Beispiele
[Mit Links zu echten Dateien im Repo!]
```js
// Kurzes, fokussiertes Beispiel
```

## 🔗 Verwandt mit:
→ [[Props]] — Daten von oben
→ [[Context API]] — Globaler State
→ [[Redux]] — Alternative
← [[Components]] — Nutzen State
← [[Hooks]] — Zugriff auf State

## 📍 Verwendet in:
- `src/components/Counter.js` (Zeile 15-30)
- `src/hooks/useAuth.js` (Zeile 8)
- `src/store/userSlice.js` (komplett)

## 🎓 Übungen:
→ [[Übung-State-1]] — Anfänger
→ [[Übung-State-2]] — Fortgeschritten

## 📚 Weiterführend:
- Official Docs Link
- Best Tutorial Link
- Video Link
```

---

## 5. ÜBUNGS-TYPEN

Erstelle Übungen in **4 Levels**, gemischt über die Formate:

| Level | Typen |
|-------|-------|
| **1 – Anfänger** | Lückentexte, Multiple Choice, "Was macht dieser Code?", Simple Debugging |
| **2 – Mittel** | Funktion von Scratch, Refactoring, Test schreiben, Mini-Feature |
| **3 – Fortgeschritten** | Performance optimieren, Edge Cases, Design Patterns, Integration |
| **4 – Expert** | Mini-Projekt, Architektur-Entscheidungen, Eigenentwurf, Code Review simulieren |

Jede Übung hat:
- **README.md** (Aufgabenstellung)
- **starter/** (Code-Gerüst)
- **solution/** (Musterlösung mit Erklärung)

---

## 6. QUALITÄTS-KONTROLLE

### Automatische Checks (vor Finalisierung prüfen):

```
PRE-FLIGHT:
├─ ✓ Alle Dateien erfasst?
├─ ✓ Jede Datei kommentiert?
├─ ✓ Jede Dependency erklärt?
├─ ✓ Alle Links funktionieren? (grep -r '→ \[')
├─ ✓ Glossar vollständig?
├─ ✓ Übungen lösbar?
├─ ✓ README verständlich?
└─ ✓ Lernpfad logisch?

DEEP CHECK:
├─ Kommentar-Qualität
│  ├─ Zu kurz? (< 20 Wörter pro Block)
│  ├─ Zu generisch? ("Dies ist eine Funktion")
│  └─ Alle Sections ausgefüllt?
│
├─ Cross-Reference Check
│  ├─ Tote Links finden
│  ├─ Fehlende Rückverweise
│  └─ Zirkuläre Abhängigkeiten
│
├─ Vollständigkeits-Check
│  ├─ Alle exports dokumentiert?
│  ├─ Alle imports erklärt?
│  ├─ Alle Funktionen kommentiert?
│  └─ Alle Klassen/Interfaces beschrieben?
│
└─ Didaktik-Check
   ├─ Progression sinnvoll?
   ├─ Wiederholung wo nötig?
   ├─ Keine Konzept-Sprünge?
   └─ Schwierigkeit angemessen?
```

### Manuelle Review-Fragen (für jede Datei):

- ❓ Würde ein Anfänger das verstehen?
- ❓ Sind alle Fachbegriffe erklärt?
- ❓ Gibt es genug Kontext?
- ❓ Sind Beispiele hilfreich?
- ❓ Fehlt wichtige Information?

### Für Dependencies:

- ❓ Ist klar, WARUM diese Library?
- ❓ Sind Alternativen erwähnt?
- ❓ Sind Breaking Changes dokumentiert?
- ❓ Gibt es Hands-On Tutorial?

### Für Übungen:

- ❓ Sind sie lösbar mit gegebenem Wissen?
- ❓ Gibt es Lösungen?
- ❓ Sind Hints hilfreich aber nicht zu viel?
- ❓ Progression sinnvoll (leicht → schwer)?

---

## 7. FRAMEWORK-SPEZIFISCHE TIEFE

### React
Dokumentiere: Alle Hooks (useState, useEffect, useMemo, useCallback, useRef, useContext, useReducer, useLayoutEffect, useImperativeHandle, useDebugValue, useDeferredValue, useTransition, useId, useSyncExternalStore, useActionState), Component Lifecycle (Mount/Update/Unmount), Props vs State, Context API, Reconciliation, Virtual DOM, JSX Syntax, Event Handling, Conditional Rendering, Lists & Keys, Forms (Controlled/Uncontrolled), Refs, Portals, Error Boundaries, Suspense, Performance (memo, useMemo, useCallback, Code Splitting), Patterns (Render Props, HOC, Compound Components).

### Backend-Framework (Express/Django/Flask/etc.)
Dokumentiere: Request/Response Cycle, Middleware System, Routing, Database Integration (ORM/ODM), Authentication, Authorization, Error Handling, Validation, Testing, Deployment, Security Best Practices (CORS, CSRF, XSS, SQL Injection).

---

## 7b. QUELLCODE-BESCHAFFUNG

Wenn kein lokaler Pfad zum Projekt angegeben wird:

1. **Suche nach offiziellen Docs**: Web-Suche nach `"<framework>" official documentation`, `"<framework>" docs`, `"<framework>" github`
2. **Bevorzugte Quellen**: Offizielle Doku-Seite, GitHub-Repo (README, Wiki), docs-Verzeichnis, offizielle Tutorials/Guides
3. **Extrahiere** aus den Docs: Core-Konzepte, API-Reference, Getting Started Guide, Beispiele, Architektur
4. **Fallback**: Wenn keine offiziellen Docs existieren, suche nach Community-Tutorials, Blog-Artikel oder YouTube-Videos
5. **Dokumentiere die Quellen** im Lern-Repo (06-REFERENZ/WEITERFÜHRENDE-RESSOURCEN.md)

## 8. AUSGABE-REGELN

1. **Zielverzeichnis**: `Repo-Skillz/` im Ziel-Projektverzeichnis. Wenn das Ziel z.B. `/Users/timo/projects/my-app` ist, erstelle `/Users/timo/projects/my-app/Repo-Skillz/`.
2. **Dateien maximieren, Token minimieren**: Erstelle lieber 50 kleine Fokus-Dateien als 5 riesige. Jede Dependency bekommt ein eigenes Verzeichnis. Jedes Konzept bekommt eine eigene Datei.
3. **Mermaid-Diagramme** für Architektur, Datenfluss, Component-Trees, Dependency-Graphen.
4. **Sprache**: Die Sprache der Ausgabe richtet sich nach der Sprache des Quellcodes und der Konvention des Projekts. Bei gemischten Projekten: Deutsch für Erklärungen, Englisch für Code.
5. **Keine künstlichen Vereinfachungen**: Erkläre korrekt, aber in zugänglicher Sprache.
6. **Nach Fertigstellung** (wenn explizit gewünscht): Führe die Quality-Checks aus §6 durch und berichte Ergebnisse.
