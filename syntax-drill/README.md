# Syntax Drill

Syntax-Übungen im Drill-Format (Lückentext / Fehler korrigieren) für Java, Python und andere Sprachen.

## Installation

```bash
# Für OpenCode (Mac/Linux)
cp -r syntax-drill ~/.config/opencode/skills/

# Für Claude Code (falls verwendet)
cp -r syntax-drill ~/.claude/skills/
```

## Aktivierung

Wird aktiviert bei Phrasen wie:
- "Mach mir drills"
- "Übungen"
- "Aufgaben"
- "Syntax training"

## Format

Jede Übung ist eine eigenständige `.java`-Datei (oder andere Sprache), die der User direkt editieren und kompilieren kann.

```java
// Aufgabe N: Kurzer Titel
//
// Beschreibung, was zu tun ist.

public class AufgabeN {
    public static void main(String[] args) {
        // Code mit ____ als Lücke
    }
}
```

- `____` = auszufüllende Lücke (Typ, Operator, Methodenname, etc.)
- Code enthält gezielte Fehler (fehlende Semikolons, falsche Datentypen, falsche Operatoren)
- Aufgaben steigen im Schwierigkeitsgrad
- Dateiname = Klassenname → direkt kompilierbar mit `javac`

## Themen (Java)

| Nr | Datei | Themen |
|----|-------|--------|
| 1 | `JavaDrills_1_Intro` | `main`, `System.out.println`, Kommentare, Syntax-Grundlagen |
| 2 | `JavaDrills_2_Variables_Datatypes` | `int`, `double`, `String`, `boolean`, `final`, Deklaration |
| 3 | `JavaDrills_3_Operations` | `+`, `-`, `*`, `/`, `%`, `++`, Konkatenation, Casting |
| 4 | `JavaDrills_4_Conditions` | `if`, `else`, `else-if`, `&&`, `\|\|`, Ternary |
| 5 | `JavaDrills_5_Loops` | `for`, `while`, `do-while`, `break`, `continue` |
| 6 | `JavaDrills_6_Arrays` | Deklaration, Index, for-each, 2D-Arrays |
| 7 | `JavaDrills_7_Methods` | Parameter, Rückgabe, Overloading, Varargs |
| 8 | `JavaDrills_8_Classes_Objects` | Attribute, Konstruktor, Getter/Setter, `static` |
| 9 | `JavaDrills_9_Exceptions` | `try-catch`, `finally`, `throws`, eigene Exceptions |
| 10 | `JavaDrills_10_Collections` | `ArrayList`, `HashMap`, for-each, `entrySet` |

## Erweiterung

Neue Drills folgen dem Schema: `Sprache_Nr_Thema_AufgabeX.java`
- 6 Aufgaben pro Thema, je eine `.java`-Datei (Aufgabe 1-4 Grundlagen, 5-6 Bonus/Challenge)
- Aufgabenstellung als `//`-Kommentar am Kopf der Datei

## Dateistruktur

```
syntax-drill/
├── README.md
├── SKILL.md
├── JavaDrills_1_Intro.java
├── JavaDrills_2_Variables_Datatypes.java
├── JavaDrills_3_Operations.java
├── JavaDrills_4_Conditions.java
├── JavaDrills_5_Loops.java
├── JavaDrills_6_Arrays.java
├── JavaDrills_7_Methods.java
├── JavaDrills_8_Classes_Objects.java
├── JavaDrills_9_Exceptions.java
└── JavaDrills_10_Collections.java
```

## Verwendung

```bash
# Eine Übung bearbeiten
vim JavaDrills_5_Loops.java

# Kompilieren und testen
javac JavaDrills_5_Loops.java && java JavaDrills_5_Loops
```

Jede Datei enthält die Aufgabenstellung als Kommentar und `____`-Marker für die auszufüllenden Code-Stellen. Der User ersetzt die Lücken durch den korrekten Code und kompiliert die Datei.
# OpenCodeSkills
