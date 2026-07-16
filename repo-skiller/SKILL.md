---
name: repo-skiller
description: Use when a user asks you to build/analyze/create a complete learning repository, study guide, code walkthrough, tutorial, or annotated codebase from an existing project. Also use when asked to "deep dive" a repository, create exercises/workshops from code, document dependencies in detail, or build a structured learning path from source code.
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

| Feld | Beschreibung |
|------|-------------|
| WAS MACHT ES? | Library-Zweck in 1-2 Sätzen |
| WARUM? | Warum im Projekt nötig? |
| WO? | Alle Dateien + Zeilen, die sie nutzen |
| WIE? | Welche Funktionen/Methoden werden verwendet? |
| ALTERNATIVEN | Vergleichbare Libraries |
| TUTORIAL | Mini-Tutorial (Install → Setup → Beispiel) |

### Framework-Spezial-Behandlung

Erkenne das Framework und dokumentiere dessen Core-Konzepte:

| Framework | Dokumentiere |
|-----------|-------------|
| React | Alle Hooks, Lifecycle, Props/State, Context, Reconciliation, Virtual DOM, JSX, Event Handling, Conditional Rendering, Lists & Keys, Forms, Refs, Performance |
| Vue | Composition API, Options API, Reactivity System, Directives, Lifecycle Hooks, Slots, Vuex/Pinia, Router |
| Angular | Modules, Components, Services, Dependency Injection, RxJS, Pipes, Directives, Guards |
| Django | MTV Pattern, ORM, Middleware, Views (FBV/CBV), Templates, Admin, Auth, Signals |
| Flask | App Factory, Blueprints, Extensions, Request/Response Cycle, Templates, SQLAlchemy |
| Express | Middleware, Routing, Error Handling, Template Engines, Static Files |
| Next.js | SSR/SSG/ISR, App Router, Pages Router, Server Components, API Routes, Middleware |
| Spring | IoC/DI, AOP, MVC, Security, Data JPA, Actuator, Configuration |

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
│  ├─ konzept-1.md         (Deepwiki-Style)
│  ├─ konzept-2.md
│  └─ 📁 ÜBUNGEN/
│
├─ 📁 02-DEPENDENCIES/
│  ├─ 📁 <dependency-1>/
│  │  ├─ WAS-IST-DAS.md
│  │  ├─ WIE-NUTZEN.md
│  │  ├─ 📁 BEISPIELE/
│  │  └─ MINI-TUTORIAL.md
│  └─ 📁 <dependency-2>/ ...
│
├─ 📁 03-CODE-ERKLÄRT/      (Original-Code mit Kommentaren)
│  ├─ 📁 src/
│  │  ├─ datei1.js
│  │  └─ datei2.js
│  └─ STRUKTUR-MAP.md
│
├─ 📁 04-CODE-ZUM-NACHBAUEN/ (Todo-Versionen)
│  ├─ 📁 src/
│  │  ├─ datei1.js
│  │  └─ datei2.js
│  └─ 📁 LÖSUNGEN/
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
 *
 * 📤 OUTPUT:
 * - Rückgabewert: Type - Was bedeutet es?
 *
 * 🔗 DEPENDENCIES:
 * - useState (React Hook)
 *
 * 💡 KONZEPTE:
 * - Debouncing
 *
 * ⚠️ WICHTIG ZU WISSEN:
 * - Edge Cases, Performance, Häufige Fehler
 *
 * 🎓 LERN-TIPP:
 * Was sollte man verstehen, bevor man das liest?
 * ═══════════════════════════════════════════════════════ */
```

### Für Todo-Versionen (`04-CODE-ZUM-NACHBAUEN/`):

```javascript
/* ═══════════════════════════════════════════════════════
 * 🎯 AUFGABE: [Kurze Beschreibung]
 * 📥 ERWARTETER INPUT:
 * 📤 ERWARTETER OUTPUT:
 * 💭 HINWEISE:
 * ✅ TEST:
 * ═══════════════════════════════════════════════════════ */

function beispielFunktion(param1, param2) {
    // TODO: Implementiere hier!
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
## 🤔 Warum brauchen wir das?
## 🔧 Wie funktioniert es?
## 💻 Code-Beispiele
## 🔗 Verwandt mit:
## 📍 Verwendet in:
## 🎓 Übungen:
## 📚 Weiterführend:
```

---

## 5. ÜBUNGS-TYPEN

| Level | Typen |
|-------|-------|
| 1 – Anfänger | Lückentexte, Multiple Choice, "Was macht dieser Code?", Simple Debugging |
| 2 – Mittel | Funktion von Scratch, Refactoring, Test schreiben, Mini-Feature |
| 3 – Fortgeschritten | Performance optimieren, Edge Cases, Design Patterns, Integration |
| 4 – Expert | Mini-Projekt, Architektur-Entscheidungen, Eigenentwurf, Code Review |

Jede Übung hat: **README.md**, **starter/**, **solution/**

---

## 6. QUALITÄTS-KONTROLLE

Pre-Flight Checks:
- Alle Dateien erfasst? Kommentiert? Jede Dependency erklärt?
- Alle Links funktionieren? Glossar vollständig?
- Übungen lösbar? README verständlich? Lernpfad logisch?

---

## 7. AUSGABE-REGELN

1. **Zielverzeichnis**: `Repo-Skillz/` im Ziel-Projektverzeichnis
2. **Dateien maximieren, Token minimieren**: 50 kleine Fokus-Dateien > 5 riesige
3. **Mermaid-Diagramme** für Architektur, Datenfluss, Component-Trees
4. **Sprache**: Nach Konvention des Projekts (DE für Erklärungen, EN für Code)
5. **Keine künstlichen Vereinfachungen**

---

## Source

`~/.claude/skills/repo-skiller/SKILL.md`
