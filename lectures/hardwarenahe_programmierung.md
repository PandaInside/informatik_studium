# Hardwarenahe Programmierung
- Vorlesung: 13:30 Uhr GAB 344 (Hörsaal) -> https://cpp.homefgr.de/cpp-doc/2026/02_semesterplan.html
- Praktikum: 15:20 Uhr PKB 165a (Seminarraum)
- GitHub "WSL Token": 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

## Einführung
- Welche Programme nutzen C++? Windows, Apple teilweise, Spiele
- Kritik: Sicherheitslücke durch Speicherverwaltung
- Alternative Programmiersprachen: Rust
- Simulator für populäre Micro-Controller: Wokwi
    - Echter Code kann per Copy/Paste eingefügt und getestet werden
- Speicher Micro-Controller: ca. 10 KB, 16 MHz -> Fensterheber, Smart Watch
- Objektorientierung würde zu viel Platz wegnehmen
- C++ 
    - Multiparadigmensprache (nicht ausschließlich objektorientiert)
    - erlaubt direkten Zugriff auf CPU, RAM, Betriebssystem
    - Von `C` über `C with classes` zu `C++` -> Ende 1998 erster `C++` Standard erschienen
    - Speicher holen mit `malloc(100)`
    - `std::cout` => console out
    - Modulsystem für Imports -> funktioniert noch nicht universell
    - `main()` mit Rückgabetype `int` und ohne `return` gibt automatisch 0 zurück -> Main braucht kein `return`
    - Begrifflichkeiten:
        - `std` = Namenspace
        - `::` = Namespace-Trenner
        - Alternative: `using namespace std`;
        - `endl` = end line
        - `<<` = Ausgabe
        - `#include` = Inkludieren von Header-Dateien
        - `auto` = Variable
        - Variable mit `_xxx` = Daten-Member
        - `std::addressof` oder auch `&` = Speicheradresse
        - `explicit` -> erfordert explizites aufrufen des Konstruktors
        - `struct` = Structure Data Type (für einfache Datentypen ohne Members)
    - Lehrbuch: C++ programmieren von Ulrich Breymann
    - Cheatsheet: https://cppreference.com/
    - Compiler:
        - Gnu Compiler Collection (GCC) -> läuft auf allen Plattformen
        - Glang
        - Microsoft Visual Studio  

``` C++
#include <iostream>
#include <print>

// void demo();

// typedef long mein_size_t;

int main() {
    // Klassisches C++:
    // std::cout << "Hello C++" << std::endl;
    // std::cout << "Hello C++" << std::endl;

    // std:: Angabe vermeiden
    // using namespace std::cout;
    // using namespace std::endl;
    // cout << "Hello C++" << endl;
    // std::print("Hello C++\n");
    // std::println("Hello C++");

    // double f = 3.14; // klassisches C++
    // auto f{3.14}; // universelle Initialisierung
    // cout << "f=" << f << "\n";

    demo();
}

#include <fmt/core.h>

void demo() {
    int i{42};
    auto j{i + 10}

    std::println("i={}", i);
    std::println("j={}", j);

    auto hacking = std::addressof(i);

    *(hacking - 1) = 99;

    std::println("i={}", i);
    std::println("j={}", j);

}
```

---

## 

---

## Praktikum
- Karte -> Klasse
- Spielfeld 3x4
- Nachzieh- & Ablagestapel
- Spieler