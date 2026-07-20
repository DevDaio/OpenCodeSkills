# stepwise – Projektphasen-Begleitung

Begleitet dich durch die Phasen des Invoice-Management-Projekts — durch gezielte Fragen, Tipps und Denkanstöße statt fertige Lösungen.

## Installation

```bash
cp -r stepwise ~/.config/opencode/skills/
```

## Aktivierung

Der Skill wird **automatisch aktiviert**, wenn du im Invoice-Management-Projekt arbeitest:
- `src/main/java/` mit Spring Boot-Klassen
- `build.gradle` mit Spring Boot-Dependencies

## Funktionsweise

| Phase | Beschreibung |
|-------|-------------|
| 0. Kein Code | Nie fertigen Code zeigen — nur Konzepte und Doku-Verweise |
| 1. SSOT | Die Projektstruktur ist die Single Source of Truth |
| 2. Schrittweise | Phase für Phase vorgehen |
| 3. Fragen stellen | Konkrete Fragen, die zum nächsten Denkschritt führen |
| 4. Tipps bei Bedarf | Doku-Stellen und Konzepte nennen, wenn der User feststeckt |
| 5. Ressourcen | Verweise auf Spring-Doku, Baeldung, JavaDoc |

## Dateistruktur

```
stepwise/
├── README.md       # Diese Datei — Dokumentation des Skills
└── SKILL.md        # Skill-Definition für OpenCode
```

## Relevante Konzepte

- JPA: @Entity, @OneToMany, JpaRepository
- Spring MVC: @Controller, @GetMapping, Model
- Thymeleaf: th:each, th:text, th:object
- Security: BCryptPasswordEncoder, SecurityFilterChain
