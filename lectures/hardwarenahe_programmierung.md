# Hardwarenahe Programmierung
- Vorlesung: 13:30 Uhr GAB 344 (Hörsaal) -> https://cpp.homefgr.de/cpp-doc/2026/02_semesterplan.html
- Praktikum: 15:20 Uhr PKB 165a (Seminarraum)
- GitHub "WSL Token": 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
- Prüfungsvorleistung: 
  1. Pinnball Spiel (https://cpp.homefgr.de/cpp-doc/2026/pv1.html)
    --> Verteidung am 13.04 oder 20.04 
    --> Code bis MOntag 8:00 Uhr einreichen (freiwillig, kann aber auch direkt live vorgestellt werden)
  2. noch offen -> wenn erste bestanden, muss diese nicht unbedingt bestanden werden 

---

## Wiederholung Computerarchitektur (wichtig, aber nicht prüfungsrelevant)
- Buch: Computer Organization and Design

### Aufbau eines Rechners
- CPU:
    - Rechenwerk (ALU): Erhält Operand 1 & 2 (Parameter) sowie Befehl und führt aus -> Ergebnis geht wieder zurück an Register (jedes Register hat einen Namen)
    - spezielle Register: 
        - linkes Register -> PC: Welcher Befehl wird gerade ausgeführt? -> Holt sich Daten aus RAM, welche an Befehlsregister weitergegeben werden
        - rechtes Register -> Befehlsregister
    - sonstige Register:
        - Accumulator: Hier landen die Eingaben
    - RAM (Random Access Memory): verbunden mit CPU
        - jedes Byte (0 1 2 4 8 16 ...) hat eine Adresse
        - zwei Bereiche:
            - Textsegment
            - Datensegment
    - Computer Aufgaben: Eingabe - Verarbeitung - Sprünge - Ausgabe
    - Assembler Test: peterhigginson.co.uk/LMC
    - Wie entsteht ein Assembler?
        - mit Hochsprache nah am fachlichen Problem -> Compiler benötigt um Assembler zu erstellen
        - Assembler/Maschinensprache alles manuell, der einzige Weg um mit Hardware zu sprechen -> Übersetzt in Maschinencode (1 und 0)
        - Maschinencode steht in .exe -> landet im RAM
        - Schnittstelle zwischen Maschinencode und CPU -> ISA (Instruction Set Architecture): ARM oder x86

### Managed Languages vs Native Languages
- Interpreter: JavaScript
  - schrittweise Übersetzung des Bytecodes in zugehörigen Maschinencode -> pro Zeile/Einheit
  - Fehler treten zur Laufzeit auf
- Manages Languages: Java, JVM-Sprachen, C#, F#, ...
  - Laufzeitumgebung
    - Programme liegen in Plattform-unabhängiger Binärsprache vor (Java: Bytecode) -> für abstrakte CPU
    - Just-in-Time Compilierung (JIT -> am Chip compiliert)
    - Optimierung zur Laufzeit möglich
  - Vorteile JVM: 
    - Sandboxing/Abstraktion (Abgrenzung zur Hardware)
    - automatische Speicherverwaltung (verbraucht aber viel Speicher)
    - plattformunabhängig, solang JVM auf System läuft
  - GraalVM: Versuch Java in native Language zu compilieren
- Native Languages: C++
  - Ahead-of-Time Compilierung (AOT)
  - Binäry ist plattformunabhängig

---

## Kurs Einführung
- Lehrbuch: C++ programmieren von Ulrich Breymann
- Cheatsheet: https://cppreference.com/
- Welche Programme nutzen C++? Windows, Apple teilweise, Spiele
- Kritik: Sicherheitslücke durch Speicherverwaltung
- Alternative Programmiersprachen: Rust
- Simulator für populäre Micro-Controller: wokwi.com 
    - Echter C-Code kann per Copy/Paste eingefügt und getestet werden
- Speicher Micro-Controller: ca. 10 KB, 16 MHz -> Fensterheber, Smart Watch
- Objektorientierung würde zu viel Platz wegnehmen
- C++ 
    - Multiparadigmensprache (nicht ausschließlich objektorientiert)
    - Compiler:
        - Gnu Compiler Collection (GCC) -> läuft auf allen Plattformen
        - Glang
        - Microsoft Visual Studio  
    - erlaubt direkten Zugriff auf CPU, RAM, Betriebssystem
    - Von `C` über `C with classes` zu `C++` -> Ende 1998 erster `C++` Standard erschienen
    - ==Call by Value Sprache==
    - **Grundprinzip**: Wiederkehrende Probleme durch Algorithmen in den Standard-Bibliotheken lösen
        --> Algorithmen sind losgelöst von den Datentypen
        --> `#include <algorithm>` wird benötigt
    - Speicher holen mit `malloc(100)`
    - `std::cout` => console out
    - Modulsystem für Imports -> funktioniert noch nicht universell
    - `main()` mit Rückgabetype `int` und ohne `return` gibt automatisch 0 zurück -> Main braucht kein `return`
    - Begrifflichkeiten:
        - `std` = Namenspace
        - `::` = Namespace-Trenner
        - *Alternative*: `using namespace std`;
        - `endl` = end line
        - `<<` = Ausgabe
        - `#include` = Inkludieren von Header-Dateien
        - `auto` = Variable
        - Variable mit `_xxx` = Daten-Member (Member = Datenwert)
        - Bevor man in den Body des Constructors kommt, werden die Member default initialisiert, um im nächsten Schritt überschrieben zu werden (2x STO)
            --> zur Vermeidung: `explicit Spielkarte(int wert = 0) : _wert{ wert } {}` -> Wert wird nach Doppelpunkt direkt zugewiesen
        - `std::addressof` oder auch `&` = Speicheradresse
        - `explicit` 
            --> erfordert explizites Aufrufen des Konstruktors
        - `struct` = Structure Data Type (für einfache Datentypen ohne Members)
        - `int wert const { return _wert; }`
            --> `const` sagt dem RAM, dies ist ein Getter
            --> Memberinitialisierung (Zustand wird nicht verändert)
            --> Zustand eingefroren und kann nicht verändert werden (anders bei `final` in Java, hier kann via Setter der Wert verändert werden)
        - `const Spielkarte karte`
            --> konstante Variable (nur zur Laufzeit) 
            --> immutable
        - `[[nodiscard]]` = Ergebnis nicht wegschmeißen -> Aufruf der Methode ist sinnlos (Compiler weist darauf hin)
        - `throw std::domain_error{ std::format(...) }` = wir halten uns nicht an Eingabebereiche
        - Zeichenketten sind Arrays mit terminierender 0 --> `format` verwenden
        - `void mischen(Spielkarte kartenstapel[150])` 
            --> 150 = magic number
            --> Arrays kennen keine Länge (wie size(), length(), sizeof(), ...) --> keine Schleifen möglich (for, foreach, ...)
            --> Verwendung von Build-in-Arrays nur, wenn wirklich nötig --> möglichst vermeiden
        - ==Templates sind mächtig==
        - `std::vector<Spielkarte> kartenstapel` 
            --> Equivalent der ArrayList in Java
            --> Nutzung für Sammlung an Datentypen
            --> enthält keine Karten bei Aufruf von `mischen`--> es läuft kein Constructor Code, kein Default Constructur benötigt
            --> Vektor kennt keine Länge --> verbraucht zunächst keinen Speicher
            --> `kartenstapel.emplaceback(wert: 12)` --> man gibt nur Contructorwerte mit --> ruft automatisch Contructor auf und fügt Wert hinten am Array hinzu (forward deklaration)
                --> *Alternative*: `kartenstapel.pushback(Spielkarte{ 12 })`
            --> `kartenstapel.at(n:0) = Spielkarte{ wert: 12 }` prüft --> Ist der Wert nicht vorhanden, wird eine Exception geworfen
        - `std::array<Spielkarte, 150> kartenstapel` > `constexpr int anzahl_karten = 150;` > `mischen(std::array<Spielkarte, anzahl_karten> kartenstapel)`
            --> Festlegung der Länge des Arrays in der Typendeklaration des Templates, das ist fix
            --> verhält sich wie Build-in-Array mit der Info der Anzahl der enthaltenen Elemente
            --> `constexpr` = zur Compilierzeit konstant
            --> Elemente des übergebenen Objektes werden per Default Contructor konstruiert
        - Wenn das Array der Methode `mischen` übergeben wird, wird das Original-Array kopiert und die Kopie bearbeitet --> **Call by Value / Call by Copy** (Standard)
            - Wenn **Call by Reference** benötigt wird, muss dies als dieses ausgewiesen werden mit `&` (`std::addressof()`) am Übergabeparameter 
                --> `mischen(std::array<Spielkarte, anzahl_karten> &kartenstapel)`
                --> Wenn dies in der Methodesignatur angegeben wurde, wird dies von der IDE überall als Referenz ausgewiesen 
                --> In der Methode `mischen` wird die Referenz des riginalobjektes übergeben
            - *Alternative*: mit `*` (Pointer -> Adresse des Objektes) statt `&`
                --> `mischen(std::array<Spielkarte, anzahl_karten> *kartenstapel)`
                --> `(*kartenstapel)[0]` = Derefferenzieren eines Elementes 
                --> mehr Schreibarbeit
            - Lokalisierung des `&` ist egal, kann links oder rechts stehen, hauptsache das kaufmännische UND verweist auf Referenz
        - `std:shuffle(first: kartenstapel.begin(), last: Kartenstapel.end(), &g:gen)` 
            --> Mischen von Datenmengen
            --> Begin und Ende der Datenmenge sowie Zufallsgenerator (`&g:gen`) benötigt
            --> `#include <random>` wird benötigt
            --> *Alternative*: `std::ranges::shuffle(&r: kartenstapel, &g:gen)` --> range sucht sich selbst Anfang und Ende des übergebenen Objektes
        - `std::count_if(first: kartenstapel.begin(), last: kartenstapel.end(), pred: [](const auto &karte: const Spielkarte &) { return karte.wert() == -2; }))`
            --> `pred` = Prädikat = boolscher Wert
                --> Lamda-Ausdrücke beginnen immer mit `[]` --> Hierin stehen Variablen, die wir ins Lamda übergeben wolen, weil der Body darauf zugreift (capture clause)
                    --> `pred: [&erwarteter_wert](const auto &karte: const Spielkarte &) { return k... REQUIRE(anzahl == anzahl_spielkarten_pro_kartenwert.at(k: erwarteter_wert)); })` (Skyjo v4 Zeile 139)
                --> `(const auto &karte: const Spielkarte &)` --> `const` = nur konstande Memberfunktionen können aufgerufen werden --> nur Leserechte
                --> `{ return karte.wert() == -2; }` --> gibt zurück, ob der Wert -2 ist
        - auf leere Referenzen prüfen: `nullptr()`
---

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

## Praktikum
- Karte -> Klasse
- Spielfeld 3x4
- Nachzieh- & Ablagestapel
- Spieler