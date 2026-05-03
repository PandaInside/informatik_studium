# Hardwarenahe Programmierung
- Vorlesung: 13:30 Uhr GAB 344 (Hörsaal) -> https://cpp.homefgr.de/cpp-doc/2026/02_semesterplan.html
- Praktikum: 15:20 Uhr PKB 165a (Seminarraum)
- GitHub "WSL Token": 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
- Prüfungsvorleistung: 
  1. Pinnball Spiel (https://cpp.homefgr.de/cpp-doc/2026/pv1.html)
    --> Verteidung am 20.04 --> bestanden
  2. noch offen 

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
        - Clang
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

## Begrifflichkeiten (Code-Beispiel: Skyjo)
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
    --> Es darf nur lesend darauf zugegriffen werden
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
    --> `constexpr` = Binary, zur Laufzeit konstant, wird vom Compilier ausgeführt
    --> Elemente des übergebenen Objektes werden per Default Contructor konstruiert
- Wenn das Array der Methode `mischen` übergeben wird, wird das Original-Array kopiert und die Kopie bearbeitet --> **Call by Value / Call by Copy** (Standard)
    - Wenn **Call by Reference** benötigt wird, muss dies als dieses ausgewiesen werden mit `&` (`std::addressof()`) am Übergabeparameter 
        --> `mischen(std::array<Spielkarte, anzahl_karten> &kartenstapel)`
        --> Wenn dies in der Methodesignatur angegeben wurde, wird dies von der IDE überall als Referenz ausgewiesen 
        --> In der Methode `mischen` wird die Referenz des Originalobjektes übergeben
    - *Alternative*: mit `*` (Pointer -> Adresse des Objektes) statt `&`
        --> `mischen(std::array<Spielkarte, anzahl_karten> *kartenstapel)`
        --> `(*kartenstapel)[0]` = Dereferenzieren eines Elementes 
        --> mehr Schreibarbeit
    - Lokalisierung des `&` ist egal, kann links oder rechts stehen, hauptsache das kaufmännische UND verweist auf Referenz
- `std:shuffle(first: kartenstapel.begin(), last: Kartenstapel.end(), &g:gen)` 
    --> Mischen von Datenmengen
    --> Begin und Ende der Datenmenge sowie Zufallsgenerator (`&g:gen`) benötigt
    --> `#include <random>` wird benötigt
    --> *Alternative*: `std::ranges::shuffle(&r: kartenstapel, &g:gen)` --> range sucht sich selbst Anfang und Ende des übergebenen Objektes
- `std::count_if(first: kartenstapel.begin(), last: kartenstapel.end(), pred: [](const auto &karte: const Spielkarte &) { return karte.wert() == -2; }))`
    --> `pred` = Prädikat = boolscher Wert
        --> Lamda-Ausdrücke beginnen immer mit `[]` --> Hierin stehen Variablen, die wir ins Lamda übergeben wollen, weil der Body darauf zugreift (capture clause)
            --> `pred: [&erwarteter_wert](const auto &karte: const Spielkarte &) { return k... REQUIRE(anzahl == anzahl_spielkarten_pro_kartenwert.at(k: erwarteter_wert)); })` (Skyjo v4 Zeile 139)
        --> `(const auto &karte: const Spielkarte &)` --> `const` = nur konstande Memberfunktionen können aufgerufen werden --> nur Leserechte
        --> `{ return karte.wert() == -2; }` --> gibt zurück, ob der Wert -2 ist
- auf leere Referenzen prüfen: `nullptr()`
- `static constexpr std::map<const int, const unsigned int> initialisiere_map_mit_anzahl_spielkarten_pro_kartenwert() noexcept {...}`
    --> Variable: `const std::map<const int, const unsigned int> anzahl_spielkarten_pro_kartenwert = initialisiere_map_mit_anzahl_spielkarten_pro_kartenwert();`
- `std::map<const int, const unsigned int>anzahl_spielkarten_pro_kartenwert { [0]={-2, 5}, [1]={-1, 10}, [2]={0, 15} }` 
    --> Einzelnes Map-Element ist vom Typ `std::pair<const int, const unsigned int>`
- `const unsigned int` = Integer hat kein Vorzeichen (wie jeder `int` bei Java)
    - Warum? Zweier-Kompliment --> MARKUS
- `anzahl_spielkarten_pro_kartenwert.incert(...)` oder alternativ `anzahl_spielkarten_pro_kartenwert[i] = ...` 
    --> packt ein `std:pair` in Map --> Typdeduktion
- `for( const auto &[ kartenwert: const int, anzahl_spielkarten: const unsigned int ] : anzahl_spielkarten_pro_kartenwert){...}` = Loop der Map (Skyjo 4 Zeile 60)
    --> "**Structured Binding**" => Zerlegung des Pairs mit `[...]` in Einzelteile, um `pair.first` und `pair.second` zu vermeiden und eine bessere Semantik zu gewährleisten
    --> Referenz mit `&`, weil Kopien sind aufwändiger als ein Verweis in die Map
    --> `kartenstapel.end()` = liefert Iterator zurück, der das Ende der Map angibt
- `return kartenstapel;`
    --> Warum wird eine Kopie zurückgegeben?
    --> `std::vector<Spielkarte> &erstelle_kartenstapel`: `std::vector<Spielkarte>` (lokale Variable ) <== main: `std::vector<Spielkarte> &kartenstapel` == `erstelle_kartenstapel();`
    --> Lokale Variable sind nach `return` prinzipiell weg -> bedarf lediglich einer CPU die Prozeduren aufrufen kann, kein Garbage Collector (bei Systemsprachen nicht vorhanden) nötig
    --> Callstack Pointer wird beim Verlassen einer Prozedur auf Ursprungsframe zurückgedreht und Speicher (für Spielkarte) wird freigegeben
    --> ==Keine Methoden bauen, die eine Referenz zurückgeben !!!==
    --> Bei Java ist es immer eine Referenz
- **Verschiebe-Semantik** = macht Kopieren effizient
- `.h` oder`.hpp` = Header-Dateien
    --> relevante Infos um Softwarekomponente verwenden zu können -> Schnittstellendefinition 
    --> Compiler braucht Infos wie Objekte aus Datensicht aussehen --> Welche Wert werden in der Methode übergeben?
    --> `extern const ...` = Daten stehen an anderer Stelle

    ``` C++
    class C {
        public:
        void f(); // Deklaration
    }
    ```

- `.cp` oder `.cpp` = Implementierungs-Dateien
    --> eigentlich Implementierung der Schnittstelle mit voll qualifiertem Methodennamen
    --> `static` = `private` Prozeduren
    ---> `#ifndef MEIN_SYMBOL #define MEIN_SYMBOL #endif` oder `#pragma once` --> ==One Definition Rule==

    ``` C++
    void C::f() {...} // Defintiion
    ```

- **Präprozessor** läuft vor Compiler, er implementiert alle Abhängigkeiten
- `call` macht neuen Callstack auf
- Linker füllt Lücken auf
- `namespace` (analog zu Packages in Java) ist anonym
- 4GB Addressraum
- statisches und dynamisches Linken
    - statisch = Code wird direkt geladen - Nachteil: größer
    - dynamisch = Code wird on demand geladen

## Dynamische Speicherverwaltung
- Beispiel: Inventar-Inhalt soll im Raum abgelegt werden, wenn Spieler stirbt. Container sind nicht erlaubt.
- `Item[] inventory = player.inventory();` geht nicht, weil Größe des Arrays zur Kompilierzeit bekannt sein muss
    - ging es, läge das Array im Callstack (-> lokale Variable)

    > **Callstack** = automatischer Speicher, der wiederverwendet wird und automatisch freigegeben wird
    > RAM-speicher im Datensegment, organisiert in Frames, jeder Frame steht für einen Prozeduraufruf, für die hier alle Variablen/Registerinhalte/etc. gespeichert wird
    > Heap und Callstacken wachsen aufeinander zu um sich so lang wie mögich nicht im Weg zu sein
    > Methoden zur Anreichung `push()` und Verringerung `pop()`
    > Rückrufaddresse für Prozeduren wird chronologisch immer in den ToS (Top of Stack) abgelegt > Speicher wird freigegeben, wenn eine Prozedur fertig ist > Speicher kann wiederverwendet werden (siehe Code-Beispiel)
    > Deshalb macht es keinen Sinn, eine Referenz auf lokale Variablen zurückzugeben

```C++
// Am Anfang und am Ende ist Callstack leer

prozedur_1 () {
    prozedur_2(); // Callstack 1. und 5. ToS
}
prozedur_2 () {
    prozedur_3(); // Callstack 2. und 4. ToS
}
prozedur_3 () {
    ... // Callstack 3. ToS
}
```

- Speicherkonflikte, wenn Callstack zu groß wird, können schwierig entdeckt werden (ausgewachsene Betriebssysteme können das), daher eigene Speicherverwaltung nötig
- Compiler berechnet Werte für Callstack-Frame, indem er lokale Variablen mit `size()` aufruft -> Der Wert landet dann im Assembler Code
- viel Programmiersprachen erlauben keine dynmaische Arrays (dynamische Länge) zur Compilzeit > ==lokalen Variablen müssen zur Compilezeit bestimmbar sein > im Callstack können nur Konstanten stehen==
- Array mit fixer Länge = Speicherverschwendung > nicht empfohlen
- Array kann im Heap abgelegt werden, dieser hat dynamischer Speicher
    - In Java erhält man dynamischen Speicher über new Ball()
        1. Alloziere (Reserviere) `sizeof(Ball)` Byte Heap-Speicher > lebt so lang bis es nicht mehr verwendet wird


- `Item[player.inventory().size()] inventory`

---

## PV1 Konzept (Prozedual)
- struct mit Konfigurationsdaten (GameConfig):
  - Spielfeld:
    - Breite (pf_width)
    - Höhe (pf_height) 
    - Head (pf_head_content)
    - Footer (pf_footer_content) --> lass ich offen für den variablen String "Won" oder "Loose"
  - Bricks:
    - Buchstabe (bricks_char)
    - Anzahl (bricks_count)
    - Position (bricks_x & bricks_y) → Array of structs
  - Paddle:
    - Buchstabe (paddle_char)
    - Länge (paddle_length)
    - Startpunkt (paddle_x)
  - Ball:
    - Buchstabe (ball_char)
    - Ausgangspunkt (ball_pos_x & ball_pos_y)
    - Abprall Multiplikator (ball_bounce_multiplier_x & ball_bounce_multiplier_y)
  - Handler:
    - Bewegung nach rechts: KEY_RIGHT oder D (move_right)
    - Bewegung nach links: KEY_LEFT oder A (move_left)
    - Spiel starten: S (game_start)
    - Spiel neustarten: R (game_reset)
    - Spiel pausieren: P (game_pause)
    - Spiel beenden: Q (game_quit)

- strcut für die Ball Lokalisierung (BallState):
  - ball_pos_x
  - ball_pos_y
  - ball_dir_x
  - ball_dir_y
  - ball_bounce_multiplier_x
  - ball_bounce_multiplier_y

- Funktion für Spiel-Initialisierung (Init):
  - Übergabe Konfig-Struct
  - Aufruf der Funktion RenderGame → Übergabe der Konfig
  - Aufruf der Funktion AddHandler → Übergabe der Konfig

- Funktion zum Rendern des Spielfeldes (RenderGame):
  - Zeichnen des Spielfeldes auf dem Terminal mittels Konfig 

- Funktion zu Initialisierung der Event Handler (AddHandler)
  - Anhängen der Funktionen für Tastatur-Events mittels Konfig

- Funktion zum Start des Spiels (GameStart)
- Funktion zum Reset des Spiels (GameReset)
- Funktion zum Pausieren des Spiels (GamePause)
- Funktion zum Beenden des Spiels (GameQuit)

- Funktion zur Paddle Bewegung (MovePaddle)
  - Steuerung des Paddles nach Links oder rechts, je nach Übergabe-Parameter

- Funktion zur Abfrage BallState (GetBallState)
  - Rückgabe des Structs BallState

- rekursive Funktion zur Ball Steuerung (ManageBallMovement)
    - Übergabe BallState
    - Aufruf ManageBrick-Funktion
    - Aufruf ManageBorder-Funktion
    - Aufruf ManagePaddle-Funktion, nur wenn wir uns in Zeile 1 befinden

- Funktion zur Steuerung von Kollisionen mit Brick (ManageBrickContact)
  - Jeder Brick hat einen Speicherplatz, der abgefragt werden kann → Ist ein Brick vorhanden wird aus dem Speicher 1 zurückgegeben, ist keiner vorhanden (zerstört) dann wird 0 zurückgegeben
  - Aufruf der Funktion IsBrick()
    - Wenn true: 
      - Aufruf Funktion CalculateDirections() → Übergabe BallState
      - Aufruf Funktion DestroyBrick() → Übergabe Pointer von Brick (Speicheradresse)
    - Wenn false: 
      - Aufruf Funktion CalculatePositions()
- Funktion zur Prüfung ob Element ein Brick ist und ob dieser existiert (IsBrick)
- Funktion zur Zerstörung von Bricks (DestroyBrick)

- Funktion zur Steuerung von Kollision mit Spielfeldrand (ManageBorderContact)
    - Aufruf Funktion CalculateDirections()

- Funktion zur Steuerung des Kontaktes mit Paddle (ManagePaddleContact)
    - Aufruf Funktion CalculateDirections()

- Funktion zur Änderung der Richtung (CalculateDirections)
- Funktion zur Änderung der Position (CalculatePositions)

### Ansätz aus der Code Review
- in C haben structs keine Memberfunktion, sind nur Funktionsdaten
- struct = alle Datenmember sind public > Geheimhaltungsprinzip aufgelöst > mit Constructor könnte man Datenmember auf private stellen

```C++
struct Ball {...}

class Ball {
    public:
    int pos_x;
    int pos_y;
    float velocity;

    Ball (int x, int y, float velocity) {...} // Default-Werte mitgeben > mit int x = 0
}

void init_ball(Ball &b, int x, int y, float vel) {// Alternative zum Constructor
    if(x ...) b.pos_x = x
}

void create_ball(int x, int y, float vel) {
    Ball b {.pos_x = x, ...}
    return b;
}

void main() {
    // Ball b {100, 50, 42.0f}

    Ball b; // Ball mit Default-Werten initialisiert
    b.pos_x = 100;
    b.pos_y = 50;
    b.velocity = 0.0f;

    init_ball(b, 100, 50, 42.0f); // Alternative zum Constructor

    Ball b2 = create_ball(200, 100, 23.0f) // Kopie, keine Referenz, weil lokale Variable auf Callstack liegt, nach Aufruf ist die Varible weg
}
```

- Wie sollte ein Getter gestaltet werden?
    - Referenz = Backdoor/Einfallstoor in SPielerstruktur, jeder Code kann Spielkarten verändern
    - Wenn Kopie zurückgegeben wird, dann neue Kopie
    - High Frenquency Trading: Keine Kopien, Referenzen benötigt > konstante Referenz (const &)
    - Alternativen:
        - Methode für Abfrage von Anzahl an Spielkarten
        - `using` für Typ Alias, hinter dem sich etwas "versteckt", um Zugriffe zu erleichtern
- Sonstige Anmerkungen:
    - ==Empfehlung: Nutzung von Standard-Bibliotheks-Methoden bevorzugen > Compiler versteht die Algorithmen und kann besser optimieren==
    - Operator um Wert nach rechts zu verschieben
    - Bei Java wird empfohlen Optional zu nutzen
    - `null` = bezieht sich auf Referenzdatentypen -> keine Speicheraddresse

    ``` C++
    int i;
    std::cin >> i; // console in (input stream), i wird eingelesen
    std::optional<char> read_character (std::istream &in) { // beinhaltet Character oder ist leer (Schrödingers Container), Char ist kein Referenzdatentyp, daher kann kein null zurückgegeben werden
        char result{};
        if(in >> result) { // etwas wird in result eingelesen
            return result;
        }
    in.clear // leeren
    in.ignore(std::numeric_limits<...>)
    return; //Auslieferung leeres Optional
    }
    ```

---

## Call by Reference

``` Mermaid
flowchart LR
    %% RAM Container
    subgraph RAM
        direction TB

        %% mischen Stack Frame (Referenz)
        subgraph mischen
            direction TB
            ref["Referenz auf std::array(Spielkarte,5)\n\naddressof(karten) = 0x7ffffffc5b20"]
        end

        %% main Stack Frame (Original)
        subgraph main
            direction TB
            arr["std::array(Spielkarte,5)\n\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n\naddressof(karten) = 0x7ffffffc5b20"]
        end
    end

    %% Reference Arrow
    ref -->|zeigt auf gleiche Adresse| arr
```

## Call by Value

```Mermaid
flowchart LR
    %% RAM Container
    subgraph RAM
        direction TB

        %% mischen Stack Frame (Kopie)
        subgraph mischen
            direction TB
            copy["Kopie von std::array(Spielkarte,5)\n\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n\naddressof(karten) = 0x7ffffffc5a00"]
        end

        %% main Stack Frame (Original)
        subgraph main
            direction TB
            arr["std::array(Spielkarte,5)\n\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n[Spielkarte]\n\naddressof(karten) = 0x7ffffffc5b20"]
        end
    end

    %% Copy Arrow
    arr -->|Kopie wird übergeben| copy
```

---

## PV2
### Feautures
