---
name: repo-comprehensive-walkthrough
description: >
  Generate a complete comprehensive walkthrough from any software repository.
  Full 8-level progression with exercises, checkpoints, anti-patterns, and crate
  guides. Working code is replaced by guided TODO/pseudocode blocks — student
  implements everything themselves. Senior dev + didactic style.
  Trigger: "comprehensive walkthrough", "full walkthrough", "repo learning",
  "codebase walkthrough", "complete walkthrough", "deep walkthrough", "code-along".
---

## OUTPUT-PFAD

Der generierte Walkthrough wird IMMER unter `$HOME/Stack_Teacher/[projektname]-learn/`
abgelegt. Dieser Ordner ist der zentrale Lernort des Users.

# NEUES VERSTÄNDNIS: Jede Datei, Jeder Block, Im Detail

Dieser Skill generiert einen **komplett kommentierten Lernpfad** durch ein Repo.

**Kernprinzip:** Nicht nur "was code tut", sondern **WARUM** er so geschrieben ist,
welche Alternativen es gäbe, und was der Entwickler dabei gedacht hat.

JEDE Datei bekommt eine eigene Analyse-Seite mit:
- **Kommentaren**: Was passiert hier Zeile für Zeile?
- **Erklärung**: Warum wurde das genau so gemacht? (Design-Entscheidung)
- **TODOs**: Was müsste der Lernende selbst schreiben?
- **Tipps**: Häufige Fehler, Stolperfallen, Best Practices
- **Projekt-Kontext**: Wie hängt dieser Code mit dem Rest zusammen?

## NACHBAU — 1:1-Repo-Kopie mit Code durch Kommentare ersetzt

Der **Nachbau** ist der Praxisteil. Der `nachbau/`-Ordner spiegelt die
**exakte Ordnerstruktur des Original-Repos** wider — jede Datei existiert
am selben Pfad wie im Original.

**Aber:** Jeder Code-Block in jeder Datei ist durch Kommentare ersetzt:
- **Erklärung**: Was tut dieser Code-Abschnitt?
- **Anweisung**: Wie schreibe ich ihn? (Signatur, Schritte, SQL, ...)
- **Tipps**: Stolperfallen, Best Practices
- **INPUT/OUTPUT**: Was nimmt der Codeblock entgegen, was produziert er?

Der Lernende öffnet die Datei, liest die Kommentare und schreibt den
fehlenden Code **direkt in die Datei** hinein. So entsteht nach und nach
das komplette Programm.

### Regel: `nachbau/` spiegelt das Repo 1:1

```
# statt:
nachbau/main.rs
nachbau/async_services.rs

# richtig:
nachbau/Backend/API/src/main.rs
nachbau/Backend/API/src/service_modules/async_services.rs
nachbau/Frontend/ACM_Frontend/src/api.js
nachbau/DB/createTables.sql
nachbau/docker-compose.yml
```

So kann der Lernende Datei für Datei das gesamte Projekt nachbauen,
ohne sich erst überlegen zu müssen, wo welche Datei hingehört.

Die 8-Level-Struktur ist NUR eine grobe Orientierung. Der Fokus liegt auf
**tiefem Verständnis jeder Datei**.

## Output Structure (Rahmen, nicht Zwang)

[projektname]-learn/
├── README.md
├── _reference/              (original repo)
├── _hints/                  (Tipps pro Schritt, nur bei Bedarf)
├── _solutions/              (vollständige Lösungen, nur bei Bedarf)
├── 00-archaeology/
│   ├── PROJECT-DNA.md       (one-line, motivation, Entscheidungs-Tabelle)
│   ├── TECH-STACK.md        (Abhängigkeiten + Begründung jeder Wahl)
│   └── STRUCTURE.md         (Ordner-Anatomie, jede Datei erklärt)
│
├── 01-foundation/           (Einstiegspunkt, erste Datei)
├── 02-core-algorithm/       (Business-Logik)
├── 03-data-structures/      (Typen, Enums, Traits)
├── ...                      (beliebig viele, je nach Projekt)
│
│   Jeder Ordner enthält pro Datei:
│   ├── FILE-NAME.md         ← HAUPTANALYSE (siehe Template unten)
│   ├── code-snippets/       (TODO-Blöcke zum Selberschreiben)
│   └── exercises/           (Übungen)
│
├── nachbau/                 ← **1:1-Repo-Spiegelung, Code durch Kommentare ersetzt**
│   ├── Backend/API/src/     (gleiche Pfade wie im Original-Repo)
│   │   ├── main.rs
│   │   └── service_modules/async_services.rs
│   ├── Frontend/.../api.js
│   ├── DB/createTables.sql
│   └── ...
│
└── agbacheck/               (Architektur-Review, Entscheidungen, Muster)

## Datei-Analyse-Template (DAS IST DER KERN)

Jede Datei bekommt eine eigene `.md`-Datei mit folgendem Aufbau:

```
# `dateiname.rs` — [Kurzbeschreibung: Was macht diese Datei?]

## Einordnung ins Projekt
_Welche Rolle spielt diese Datei? Wer ruft sie auf? Was hängt von ihr ab?_

## Code-Rundgang (Block für Block)

### Block 1: [Name, z.B. "Imports und Module"]
```
[ORIGINALCODE oder PSEUDOCODE]
```
**WAS passiert hier?**
_[Ausführliche Erklärung jeder Zeile]_

**WARUM wurde das so gemacht?**
_[Design-Entscheidung: Warum diese Crate? Warum dieser Ansatz?]_

**TIPPS**
- [Häufiger Fehler / Stolperfalle]
- [Alternative wäre gewesen...]
- [Performance-Aspekt]

**TODO**
- [Was der Lernende hier machen soll]

**ZUSAMMENHANG**
_Wie hängt dieser Code-Mit anderen Dateien zusammen?_
```

### Block 2: [nächste logische Einheit]
...
```

## Code-Replacement (für code-snippets/)

Jeder Block im code-snippets/-Ordner folgt diesem Schema:

```
// ============================================================
// BLOCK: <Funktion/Typ-Name>
// WAS:    <1-2 Sätze, was dieser Codeabschnitt tut>
// WARUM:  <1-2 Sätze, warum dieser Ansatz gewählt wurde>
// ============================================================
//
// TIPPS:
//   - <Tipp 1>
//   - <Tipp 2>
//
// TODO: <Konkrete Arbeitsanweisung>
// Z.B.: "Schreibe die Funktion get_user_by_email, die ...
//        Nutze sqlx::query_as mit fetch_optional.
//        Der Fehlerfall wird mit ? propagiert."
//
// ~~~ Struktur ~~~
// - Funktion: async fn get_user_by_email(pool: &PgPool, email: &str)
// - Rückgabe: Result<Option<User>, sqlx::Error>
// - SQL: SELECT * FROM "user" WHERE emailadress = $1
// - Nutze fetch_optional (weil User existieren könnte oder nicht)
```

## Verhältnis in der Page

| Element | Anteil | Beschreibung |
|---------|--------|-------------|
| Kontext/WARUM | ~40% | Warum existiert dieser Code? Welches Problem löst er? |
| Code-Analyse | ~30% | Zeile für Zeile, Block für Block |
| TODOs | ~20% | Konkrete Aufgaben für den Lernenden |
| Tipps | ~10% | Best Practices, Stolperfallen, Alternativen |

## Nachbau-Template (pro Datei, 1:1-Pfadtreu)

Jede Datei im `nachbau/`-Ordner liegt **am selben Pfad wie im Original-Repo**.
Ihr gesamter Code ist durch Kommentare ersetzt: Jeder logische Block bekommt
Erklärung + Anweisung + Tipp + INPUT/OUTPUT.

Schema pro Datei:

```
// ============================================================
// DATEI: main.rs
// BAUE DIESE DATEI VOLLSTÄNDIG NACH
// ============================================================
//
// 🎯 ZIEL
// Der Server startet auf Port 3000, verbindet sich mit PostgreSQL,
// registriert 13 API-Routen und startet den Monitoring-Loop.
//
// ╔════════════════════════════════════════════════════════════╗
// ║  INPUT (was hereinkommt)                                  ║
// ║  - DATABASE_URL aus .env oder Umgebungsvariable           ║
// ║  - HTTP-Requests (JSON-Body, Query-Parameter)             ║
// ╚════════════════════════════════════════════════════════════╝
// ╔════════════════════════════════════════════════════════════╗
// ║  OUTPUT (was rausgeht)                                    ║
// ║  - JSON-Responses (LoginRes, ErrorRes, Vec<EndpointExt>)  ║
// ║  - HTTP-Statuscodes (200, 201, 401, 404, 409, 500)       ║
// ╚════════════════════════════════════════════════════════════╝
//
// ─── 1. MODULE ───
// Deklariere das Modul "service_modules"
//
// ─── 2. IMPORTS ───
// - axum: Router, Json, extract::State, extract::Query
// - axum::routing: get, post, put, delete
// - axum::http::Method
// - serde: Deserialize, Serialize
// - service_modules::async_services
// - sqlx::PgPool
// - std::sync::Arc
// - tower_http::cors::{Any, CorsLayer}
//
// ─── 3. APPSTATE ───
// struct AppState { pool: PgPool }
//
// ─── 4. REQUEST-TYPEN (10 Stück, alle #[derive(Deserialize)]) ───
//   CreateAccountReq  { email, password }
//   LoginReq          { email, password }
//   ChangePasswordReq { userid, old_password, new_password }
//   ChangeEmailReq    { userid, new_email }
//   DeleteAccountReq  { userid }
//   AddEndpointReq    { userid, url }
//   SetIntervallReq   { endpointid, seconds }
//   DeleteEndpointReq { endpointid }
//   UpdateEndpointReq { endpointid, url }
//   IdParam           { id }
//   (Hinweis: ChangePasswordReq hat i32, obwohl userid ein Integer ist)
//
// ─── 5. RESPONSE-TYPEN (2 Stück, #[derive(Serialize)]) ───
//   LoginRes { userid: i32, emailadress: String }
//   ErrorRes { error: String }
//
// ─── 6. HANDLER (alle async fn) ───
//   handle_healthcheck        → GET /acm
//   handle_create_account     → POST /acm/createAccount
//   handle_login              → POST /acm/login
//   handle_home               → GET /acm/home?id=N
//   handle_user               → GET /acm/user?id=N
//   handle_change_password    → PUT /acm/user/changePassword
//   handle_change_email       → PUT /acm/user/changeEmail
//   handle_delete_account     → DELETE /acm/user/deleteAccount
//   handle_add_endpoint       → PUT /acm/addEndpoint
//   handle_set_intervall      → PUT /acm/setIntervall
//   handle_delete_endpoint    → PUT /acm/deleteConfirm
//   handle_update_endpoint    → PUT /acm/updateEndpoint
//   handle_log                → GET /acm/log?id=N
//
//   Jeder Handler:
//   - Nimmt State<Arc<AppState>> + ggf. Json<Body> oder Query<Params>
//   - Gibt Result<Json<...>, (StatusCode, Json<ErrorRes>)> zurück
//   - Ruft async_services::* auf und wandelt Fehler mit map_err
//   - Handler-Rückgabetypen:
//     healthcheck              → Json<serde_json::Value>
//     login, create_account    → Result<Json<LoginRes>, ...>
//     home                     → Result<Json<Vec<EndpointExtended>>, ...>
//     user                     → Result<Json<User>, ...>
//     change_password/email    → Result<Json<serde_json::Value>, ...>
//     delete_account/add/etc.  → Result<Json<serde_json::Value>, ...>
//     log                      → Result<Json<Vec<Log>>, ...>
//
// ─── 7. MAIN-FUNKTION ───
//   #[tokio::main]
//   async fn main() -> Result<(), sqlx::Error>
//   - dotenv::dotenv().ok()
//   - DATABASE_URL aus env var (Fallback postgres://admin:admin@localhost:5432/mydb)
//   - PgPoolOptions::new().max_connections(5).connect(&database_url)
//   - pool.clone() für Monitoring-Loop
//   - tokio::spawn(async move { async_services::run_monitoring_loop(pool).await })
//   - Arc::new(AppState { pool })
//   - CorsLayer: allow_origin(Any), allow_methods([GET,POST,PUT,DELETE]), allow_headers(Any)
//   - Router::new() mit 13 Routen, .layer(cors), .with_state(state)
//   - Tokio::net::TcpListener::bind("0.0.0.0:3000")
//   - axum::serve(listener, app).await.unwrap()
```

## SPEZIALFALL: Framework oder Sprache

Wenn das Ziel-Repo ein **Framework** (z.B. Quickshell, Qt, React, Axum) oder eine
**Sprache** ist, gilt **NICHT** der 1:1-Nachbau-Ansatz.

### Stattdessen: Anwendungsübungen & Beispiele

Der Lernende will das Framework/die Sprache **nutzen** lernen — nicht die
Framework-Interna nachbauen.

- **Kein `nachbau/`** mit 1:1-Repo-Spiegelung
- **Stattdessen `projects/`** mit mehreren Praxisprojekten, die das Framework
  von einfach bis komplex anwenden
- Jedes Projekt hat:
  - **Konkrete Aufgabenstellung** ("Baue eine Statusleiste mit ...")
  - **Schritt-für-Schritt-Anleitung**
  - **Code-Gerüst** (skeleton) mit TODOs
  - **Lösung** in `_solutions/`
- Architektur-Analyse (`00-archaeology/`) bleibt erhalten — der Lernende muss
  verstehen, wie das Framework aufgebaut ist, um es richtig zu nutzen
- Die restliche Level-Struktur (01-foundation, 02-core-algorithm, ...) fokussiert
  sich auf **API-Oberflächen und Konzepte**, nicht auf Implementierungs-Details

### Beispiel: Quickshell

```
quickshell-learn/
├── README.md
├── 00-archaeology/
│   ├── PROJECT-DNA.md
│   ├── TECH-STACK.md
│   └── STRUCTURE.md
├── 01-foundation/
│   ├── QML-AND-QUICKSHELL.md          # Grundkonzepte: QtQuick + Quickshell
│   ├── FIRST-SHELL.md                 # Minimales Shell-Setup
│   └── exercises/
│       └── hello-world-shell/
├── 02-widgets-and-panels/
│   ├── PANEL-BASICS.md                # Panel-Fenster, LayerShell
│   ├── WIDGET-OVERVIEW.md             # MarginWrapper, ClipRect, etc.
│   └── exercises/
│       └── simple-statusbar/
├── 03-wayland-integration/
│   ├── WORKSPACE-TRACKING.md
│   ├── TOPLEVEL-MANAGEMENT.md
│   └── exercises/
│       └── workspace-bar/
├── 04-services/
│   ├── IO-AND-DBUS.md
│   ├── AUDIO-PIPEWIRE.md
│   └── exercises/
│       └── audio-mixer/
├── 05-real-world/
│   ├── ANIMATIONS.md
│   ├── THEMING.md
│   └── exercises/
│       └── full-desktop-shell/
├── projects/
│   ├── 01-hello-bar/
│   ├── 02-workspace-widget/
│   ├── 03-system-tray/
│   ├── 04-audio-control/
│   └── 05-full-shell/
├── _reference/              (original repo)
├── _hints/
└── _solutions/
```

### Entscheidungsregel

| Repo-Typ | Ansatz | Output-Ordner |
|----------|--------|---------------|
| Anwendung / API / Tool | 1:1-Nachbau | `nachbau/` |
| Framework / Library / Sprache | Anwendungsübungen | `projects/` |

Prüfe anhand der Repo-Beschreibung und des Codes: Ist dies ein Framework/Library,
das/die primär **von anderem Code importiert/verwendet** wird? → `projects/`
Ist es eine **eigenständige Anwendung**? → `nachbau/`

## Quality Checklist

- Jede Datei hat eine eigene Analyse-Seite
- Jeder Code-Block wird mit "WAS" und "WARUM" erklärt
- TODOs sind konkret und ausführbar
- Tipps sind praxisnah (keine Binsenweisheiten)
- Zusammenhänge zwischen Dateien werden erklärt
- Lernender versteht am Ende nicht nur den Code, sondern auch die **Entscheidungen dahinter**
- **nachbau/ spiegelt Repo-Struktur 1:1** (gleiche Ordner, gleiche Dateinamen)
- **nachbau/ enthält NUR Kommentare** — kein ausführbarer Code!
- Jeder Kommentar-Block enthält: Erklärung + Anweisung + Tipp + INPUT/OUTPUT
