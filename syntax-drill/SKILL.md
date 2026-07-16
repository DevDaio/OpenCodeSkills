---
name: syntax-drill
description: Generiert Syntax-Übungen im Drill-Format (Lückentext / Fehler korrigieren) für Java, Python usw. Verwende diesen Skill, wenn der User sagt "mach mir drills", "übungen", "aufgaben" oder "syntax training". Erstellt .java-Dateien mit Aufgabenstellung als //-Kommentar und Code mit ____.
---

# Syntax-Drill

Erstellt Lückentext-Übungen im Java-Drill-Format als `.java`-Dateien.
Jede Datei enthält genau eine Aufgabe, die der User direkt editieren und mit `javac` kompilieren kann.

## Format

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
- Aufgaben steigen sich im Schwierigkeitsgrad
- Dateiname = Klassenname + `.java` → direkt kompilierbar

## Themenabdeckung (Java)

| Nr | Datei | Themen |
|----|-------|--------|
| 1 | JavaDrills_1_Intro | main, print, Kommentare, Syntax-Grundlagen |
| 2 | JavaDrills_2_Variables_Datatypes | int, double, String, boolean, final, Deklaration |
| 3 | JavaDrills_3_Operations | +, -, *, /, %, ++, Konkatenation, Casting |
| 4 | JavaDrills_4_Conditions | if, else, else-if, &&, ||, Ternary |
| 5 | JavaDrills_5_Loops | for, while, do-while, break, continue |
| 6 | JavaDrills_6_Arrays | Deklaration, Index, for-each, 2D-Arrays |
| 7 | JavaDrills_7_Methods | Parameter, Rückgabe, Overloading, Varargs |
| 8 | JavaDrills_8_Classes_Objects | Attribute, Konstruktor, getter/setter, static |
| 9 | JavaDrills_9_Exceptions | try-catch, finally, throws, eigene Exceptions |
| 10 | JavaDrills_10_Collections | ArrayList, HashMap, for-each, entrySet |

## Erweiterung

Neue Drills folgen dem Schema: `Sprache_Nr_Thema_AufgabeX.java`
- 6 Aufgaben pro Thema, je eine `.java`-Datei
- Aufgabe 1-4: Grundlagen, Aufgabe 5-6: Bonus/Challenge
- Aufgabenstellung als `//`-Kommentar am Kopf der Datei

## Referenz-Dateien

Die vorhandenen JavaDrills liegen unter `~/code/Java/JavaDrills/java/` als Referenz.
Neue Drills bitte im selben Stil im Zielverzeichnis des Users anlegen.
