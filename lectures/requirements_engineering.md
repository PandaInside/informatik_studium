# Requirements Engineering (Praktikum Gruppe 7)
## Foliensatz reqeng-le-1
### Warum Requirements Engineering? (siehe Seite 6 ff)
- Urteilskraft / fachliche Bewertung ist wichtiger als nur Texte zu generieren
- Kontexte sollten sauber formuliert werden
- Einsatz von KI später im Prozess für Präzisierug und Perspektiven
- ==Erst verstehen, dann formulieren, dann beschleunigen.==
- Mehrheit der Fehler entsteht in der Analysephase / bei der Aufgabenklärung.
- Je früher man Fehler vermeiden kann, desto besser für das Endprodukt.
- Bei fehlenden Anforderungen handelt es sich meist um Trivialitäten, die als selbstverständlich erachtet werden.

### Zentrale Begrifflichkeiten

> **Eine Anforderung ist gemäß IEEE:**
> 1. Eine Bedingung oder Fähigkeit, die von einem Benutzer (Person oder System) zur Lösung eines Problems oder zur Erreichung eines Ziels benötigt wird.
> 2. Eine Bedingung oder Fähigkeit, die ein System oder Teilsystem erfüllen oder besitzen muss, um einen Vertrag, eine Norm, eine Spezifikation oder andere, formell vorgegebene Dokumente zu erfüllen.
> 3. Eine dokumentierte Repräsentation einer Bedingung oder Eigenschaft gemäß 1. oder 2.

> **Stakeholder:**
> Ein Stakeholder eines Systems ist eine Person oder Organisation, die **(direkt oder indirekt) Einfluss auf die Anforderungen des betrachteten Systems** hat.

> ** Requirements Engineering:**
> Ist ein systematischer und disziplinierter Ansatz zur Spezifikation und zum Management von Anforderungen mit den folgenden Zielen:
> 1. Die relevanten Anforderungen zu kennen, Konsens unter den Stakeholdern über die Anforderungen herzustellen, die Anforderungen konform zu vorgegebenen Standards zu dokumentieren und die Anforderungen systematisch zu managen.
> 2. Die Wünsche und Bedürfnisse der Stakeholder zu verstehen, zu dokumentieren sowie die Anforderungen zu spezifizieren und zu managen, um das Risiko zu minimieren, dass das System nicht den Wünschen und Bedürfnissen der Stakeholder entspricht.

### 4 Hauptätigkeiten
- Ermitteln
- Dokumentieren
- Prüfen und abstimmen
- Verwalten

### Vorgehensmodelle
- organisatorischer Rahmen für Systementwicklung
- klare Zielsetzung
- Unterscheidung von schwer- und leichtgewichtigen Modellen

### Kommunikationstheorie
#### Problematiken
- Unterschiedliche Begriffwelten
- Art des Kommunikationsmediums (mündlich / schrifltich)
- sprachliche Bequemlichkeit
- Implizites Vorwissen
  - vorausgesetztes Vorwissen
  - Vereinfachung im sprachlichen Ausdruck schüren Missverständnisse

### Fähigkeiten eines Requirement Engineers
- meist Outsourcing, das externe RE'ler ab vom Geschehen urteilen können
- nicht empfohlen Projektmanager zum RE'ler zu machen

### Arten von Anforderungen

> **Funktionale Anforderung:**
> Ist eine Anforderung bezüglich eines Ergebnisses oder eines Verhaltens, das von einer Funktion eines Systems bereitgestellt werden soll.
> Verhaltens-, Struktur-, Funktionanforderungen

> **Nicht-funktionale Anforderung:**
> ist ein Oberbegriff für Qualitätsanforderungen und Randbedingungen (Normen, juristische Anforderungen).
> Eine **Qualitätsanforderung** ist eine Anforderung, die sich auf ein Qualitätsmerkmal bezieht, das nicht durch funktionale Anforderungen abgedeckt wird. Sie legen die gewünschte Qualität fest und beeinflussen stark die Systemarchitektur. Normen (wie ISO) beschreiben, was Qualitätsmerkmale sind. 
> Eine **Randbedingung** ist eine Anforderung, die den Lösungsraum jenseits dessen einschränkt, was notwendig ist, um die funktionalen Anforderungen und die Qualitätsanforderungen zu erfüllen. Sie werden nicht umgesetzt und können nicht beeinflusst werden. Sie setzen die Umsetzungsmöglichkeiten ein. Sie können sich auf das betrachtete Sytem und/oder den Entwicklungsprozess beziehen.

## Foliensatz reqeng-nfas-addon
- ...

## Foliensatz reqeng-le-2
### Systemkontext

> **Systemkontext:**
> Ist der Teil der Umgebung eines Systems, der für die Definition und das Verständnis der Anforderungen des betrachteten Systems relevant ist.
> Nicht relevante Anforderungen sollten dennoch dokumentiert sein, um später nachvollziehen zu können, dass diese abgewägt worden.

- Zweck des Systemkontextes (Einstiegsfragen bei Anforderungserhebung)
1. Was soll Teil des Sytems sein und was nicht?
2. Was hat einen direkten Bezug zum System?
- Aspekte im Systemkontext

### System- & Kontextgrenze

> **Systemgrenze:**
> Sie separiert das geplante System von seiner Umgebung. Sie grenzt den im Rahmen des Entwicklungsprozesses gestaltbaren und veränderbaren Teil der Realität von Aspekten in der Umgebung ab, die durch den Entwicklungsprozess nicht verändert werden können.

> **Kontextgrenze:**
> Sie separiert den relevanten Teil der Umgebung eines geplanten Systems vom irrelevanten Teil, d. h. dem Teil der Umgebung, der keinen Einfluss auf das geplante System und damit auch keinen Einfluss auf die Anforderungen dieses Systems hat.

- Grauzonen:
  - werden meist während der Entwicklung aufgedeckt
  - deren Zugehörigkeit muss noch geklärt werden

### Systemkontext dokumentieren
- Datenflussdiagramm
- Use-Case-Diagramm
- Klassendiagramm

## Foliensatz reqeng-le-4
### Anforderungen dokumentieren

> **Anforderungsspezifikation** *(auch: Anforderungsdokument)*
> Ist eine systematisch dargestellte Sammlung von Anforderungen (typischerweise für ein System oder eine Komponente), die vorgegebenen Kriterien genügt.

### Gründe für Dokumentation
- zentrale Bedeutung von Anforderungen 
  - Eingrenzung Interpretationsspielräume / Mismatches
- rechtliche Relevanz 
  - Nachweisbarkeit für weniger Diskussionspotential 
  - Vorschriften festhalten
- Komplexität 
  - Nachvollziehbarkeit (Einarbeitung, Nacharbeiten -> Historie)
- Zugreifbarkeit 
  - fehlende Auskünfte aufgrund von Urlaub oder Fluktuation

### Arten der Dokumentation
#### Perspektiven von Anforderungen (Bezug auf Praltikum 1) > Seite 7
- Strukturperspektive
  - grobe Struktur
  - modellbasiert empfohlen
- Funktionsperspektive
  - Eingabe- und Ausgabedaten beschreiben
- Verhaltensperspektive
  - Zustandsautomat
  - Zustandswechsel hat Trigger, der diesen auslöst
  - unter welchen Bedingungen geht es weiter

#### Natürlichsprachliche Dokumentation

|Vorteile|Nachteile / potentielle Gefahren|
|---|---|
|Jedem verständlich.<br>Kein Erlernen einer Notation nötig.<br>Einsetzbar für alle Arten von Anforderungen.|Natürliche Sprache ist oft mehrdeutig oder missverständlich.<br>Unbeabsichtigtes Vermischen der Perspektiven von Anforderungen. ->  Einwegkanal: Man muss mit den erhaltenen Informationen arbeiten können.<br>Isolation der Anforderungen für nur eine Perspektive schwierig. -> Mischform|

#### Modelbasierte Dokumentation

|Vorteile|Nachteile / potentielle Gefahren|
|---|---|
|Anforderungen können isoliert in jeder der drei Perspektiven dokumentiert werden. -> verschiedene Werkzeuge<br>Kompakt und für geübten Leser Einarbeitungszeit kürzer<br>Vermeiden von Missverständnisen|Kein universaler Einsatz -> Hängt von Diagrammform ab.<br>Kenntnis der Notation nötig|

#### Mischform
- Anforderungsdokumente enthalten nicht nur Anforderungen
  - WICHTIG: Dokumentation von Entscheidungen für Nachweisbarkeit
  - Umfang der Erläuterungen eigenes Ermessen, aber sollte nachvolziehbar sein
  - Relevante Informationen, wie Randbedingungen, sollten notiert sein -> besser haben als brauchen
- Die Wahl der geeigneten Dokumentationsform ist von mehreren Faktoren abhängig
  - Welche Dokumentationsform ist für die Perspektive geeignet? Einheitlichkeit verwenden -> unterschiedliche Beschreibung von Perspektiven kritisch zu betrachten
  - Leserkreis sollte berücksichtigt werden -> Einheitlichkeit, strukturelle Nachvollziehbarkeit, bestimmtes Wissen vorwegnehmen, um Einarbeitungszeit zu vermeiden
  - zu dokumentierendes Wissen
- Typisch ist eine Kombination aus natürlichsprachlichen Anforderungen und konzeptuellen Modellen.
  - Schwächen der einen Dokumentationform werden durch die Stärken der anderen weitgehend ausgeglichen -> geeignetste aus jeder Dokumentationsform herausnehmen
  - Vorteile beider Dokumentationsformen werden genutzt
  - Beispiel: Diagramme mit mehr Details in natürlicher Sprache beschreiben/kommentieren -> doppelter Aufwand, aber gute Chance auf Eindeutigkeit

### Struktur eines Anforderungsdokumentes
#### Standardgliederungen
- Vorteile:
  - Hauptgrund: Wiedererkennungswert -> schnelle Erfassung des ausgewählten Inhaltes
  - einfache Wiederverwendung von Inhalten (Achtung: nötige kundenspezifische Anpassungen berücksichtigen)
  - Erleichtert Einarbeitung neuer Mitarbeiter
  - Selektives Lesen/Überprüfen von Anforderungsdokumenten
- Sie können und sollten an die projektspezifischen Randbedingungen angepasst werden

##### Rational Unified Process (RUP)
- für objektorientierte Softwaresysteme
- Auftraggeber erstellt Business Model
- Auftragnehmer nutzt Software Requirements Specification (SRS) für Anforderungsdokumentation

##### Volere
- Urpsrung: Karteikarten -> Jede Kateikarte hatte bestimmte Merkmale
- zugeschnitten auf objektorientierte Softwareentwicklung
- guter Blick auf das Gesamtsystem, nicht nur Anforderungen
- Viele vorgefertigte Schubladen, darunter einige, die sich nicht in anderen Standards wieder finden (z. B. „Kulturelle und politische Anforderungen“)

##### IEEE 830-1998
- Produktumfeld fehlt im Volere

##### V-Modell des Bundesministeriums
- Lastenheft = Anwendersicht, Gesamtheit der Forderungen -> Verhandlungsspielraum
- Pflichtenheft = Realisierungsvorgaben

#### Nicht-funktionale Anforderungen - Seite 18 ff

##### Qualitätsanforderungen
- Funktionalität -> Passt alles zusammen? Was kann das Produkt?
- Zuverlässigkeit -> 99,9 % Verfügbarkeit gewährleistet? Was ist, wenn ein Teil meines Systems ausfällt?
- Benutzbarkeit -> Schnittstelle Mensch/Maschine
- Effizienz -> Performance
- Änderbarkeit
- Übertragbarkeit

##### Umgang mit nicht-funktionalen Anforderungen
- geben Zusatzinformationen auf funktionale Anforderungen
- natürliche Sprache
- gleichzeitig mit funktionalen Anforderungen ermitteln & dokumentieren
- gleich wichtig wie funktionale Anforderungen
- Absprache mit Fachleuten/Stakeholdern
- für Architektur und AWS notwendig
- werden nicht alle unbedingt umgesetzt, schränken die Umsetzung allerdings ein ->
- müssen prüfbar/testbar sein

##### Qualitätskriterien
##### Glossar

## Foliensatz reqeng-le-5
### Kommunikationsmedium Sprache
### Sprachliche Effekte und ihre Vertreter
- Tilgung:
  - Dinge werden gar nicht bewusst wahrgenommen
  - werden demnach nicht beachtet (nicht spezifiziert, nicht dokumentiert)
  - unvollständige Informtaionen
  - Vertreter: ==unvollständig spezifizierte Bedingungen oder Prozesswörter==
  - Signalwörter (z.B. wenn...dann, anzeigen) sollten hinterfragt werden, um Missverständnisse und spätere Nachfragen zu vermeiden
  - Fehlen wissenswerte Informationen? W-Fragen stellen (z.B. Was, wem, wann wird angezeigt)
- Generalisierung:
  - Verallgemeinerungen führt zu Fehlern 
  - Vertreter: ==Substantive ohne Bezugsindex== oder ==Universalquantoren==
  - Signalwörter (z.B. Anwender, alle) führen zu lückenhaften Informationen, die näher erläutert werden sollten, inkl. Berücksichtigung von Ausnahmen
- Verzerrung:
  - realitätsverfälschende Aussagen
  - Vertreter: ==Nominalisierung==
  - Signalwörter (z.B. Speicherung, Archivierung) müssen an anderer Stelle im Anforderungsdokument ausreichend spezifiziert werden oder Anforderungen werden stattdessen mit Vollverben näher definiert

#### Stilregeln 
### Satzschablone

> **Satzschablone:** (Requirement Template)
> Ist ein Bauplan für die syntaktische Struktur einer einzelnen Anforderung.

#### Vorteile
#### Satzschablone
- Deutsche Satzschablone (Seite 22 && 25)
- Satzschablone mit Bedingung (Seite 28)
  - Eher voranstellen, weil man die Anforderung gleich anders liest, da man von Beginn an weiß, dass es an eine Bedingung geknüpft ist -> kann sonst schnell überlesen werden
  - Egal in welcher Reihenfolge man dies handhabt, es sollte stets einheitlich bleiben.
##### Typen der Funktionalität (Seite 26)

## Foliensatz reqeng-le-5-add-2
### Master-Schablonen

## Foliensatz reqeng-le-6
### Modelle

> **Modell:**
> Ist eine abstrakte Darstellung einer existierenden oder einer noch zu schaffenden Realität.

- 3 Ausprägungen von Anforderungen:
  - Ziele
  - Use Cases
  - Systemanforderungen
- 3 Hauptaspekte von Modellen
  - Abbild der Realität
    - nie 1:1, meist liegt der Fokus auf einem speziellen Problem
  - Verkürzung der Realität -> Folge von Punkt 1
  - Pragmatische Eigenschaft 
    - für die Lösung benötigte Eigenschaften, alle anderen sind nebensächlich
    - Requirements Engineer muss herausfiltern, was wichtig ist

#### Konzeptionelle Modellierungssprachen
- Syntax = Werkzeuge (UML-Modell)
- Semantik = Definition (UML Metamodell)

#### Anforderungsmodelle

> **Anforderungsmodell:**
> Ein konzeptionelles Modell, welches die Anforderungen eines Systems darstellt.

- Vorteile
  - Bildhaft dargestellte Informationen können im Gegensatz zu Fließtexten schneller erfasst und besser memoriert werden
  - Unterstützt den Analytiker durch Vorgaben darüber, was in welher Art und Weise abstrahiert werden muss
  - Definierter Fokus der Modellierungssprache ermöglicht effizierte Dokumentation

### Zielmodelle Seite 11-14
### Use Cases
- 06_Anwendungsfalldiagramm_Folien.pdf
- Unklarheiten gering halten

### Strukturperspektive (wird nicht näher behandelt, sollte klar sein)
#### UML Diagramme
- Datentypen haben in Anforderungen nichts zu suchen, diese sind technischer Art
- Wenn dann hält man dies als extra Anforderung natürlich-sprachlich fest

#### Entity Relationship Diagramme
- Betrachtung der Beziehungen zwischen gleichartigen Objekten oder gleichartigen Personen

### Funktionsperspektive
#### Aktivitätsdiagramme
- Modellierung von Abläufen
- Arten:
  - Einfacher Ablauf
  - Fork (Gabelung & Nebenläufigkeit) and Join (Vereinigung/Zusammenführung der Zweige)
    - **keine Parallelität**
    - Aktivitäten laufen unabhängig voneinander
    - Gabelung ohne Fork lässt Diskussionsspielraum, ob man beide Wege geht, aber Petri-Netze (veraltet) bieten die Möglichkeit der Auflösung dessen mit der Übergabe und Prüfung von Tokens
    - Bei Fork geht es nur weiter, wenn alle Zweige erfüllt wurden
    - Partitionen / Swimlanes zur Unterscheidung von Verantwortlichkeitsbereichen

    ![img](../assets/AktivitätsdiagrammPartitionen.png)

- Mehrere Aktivtäten von einem Punkt ausgehend erlaubt
- eine Prüfung hat mind. 2 Ergebnisse 
- bool'sche Logik nicht vorgeschrieben
- Notationselemente siehe Seite 40

#### Datenflussdiagramme
- Aktivitätsdiagramme sind sehr viel genauer, daher seltener verwendet
- Datenflussdiagramme beschreiben den Transport von Daten zwischen Prozessen, Datenspeichern und Personen, Personengruppen oder Systemen.
- kein Start- und Endpunkt

### Verhaltensdiagramme
#### UML-Zustandsdiagramme (Seite 44 ff && 04_Zustandsdiagramm_Folien)
- ermöglichen es, die Zustände eines Systems zu verschiedenen Zeitpunkten darzustellen und die Übergänge zwischen diesen Zuständen zu modellieren.
- Praktische Umsetzung mit Zustandautomaten / Zustandsmaschinen
  - entry / "aktivität": Wird beim Eingang in den Zustand ausgeführt
  - exit / "aktivität": Wird beim Verlassen des Zustands ausgeführt
  - do / "aktivität": Wird ausgeführt, Parameter sind erlaub
- Zustandsautomaten (theoretische Informatik) werden intensive bei der Entwicklung von Compilern eingesetzt
- Prioritäten von Prüfungen textuell transportieren (Prio 1, Prio 2, ...)

## Foliensatz reqeng-le-3
### Anforderungen ermitteln
> aufarbeiten

## Foliensatz reqeng-le-7
### Anforderungen prüfen (Review)
#### Inhalt prüfen
- Verfolgbarkeitn
  - Woher kommt die Anforderung? Wo führt sie hin?
- Korrektheit
  - fachliche Richtigkeit
  - Übereinstimmung mit tatsächlichen Bedürfnissen des Stakeholders
- Konsistenz
  - keine Wiedersprüche
- Lösungsneutralität
  - nicht zu technisch (keine festgelegte Datenbank)
- Überprüfbarkeit
  - "Das System soll schnell antworten" -> keine spezifische Wertangaben
- Notwendigkeit
  - keine Nice-to-have
  - gute Begründung vorlegen
- Vollständigkeit
  - "Das System soll den Kunden benachrichten" -> unvollständig

#### Dokumentation prüfen
- Konformität zur Dokumentenstruktur / zum Dokumentationsformat / mit Dokumentationsregeln
  - Schablonen verwenden
  - festes geregeltes Format nutzen
- Eindeutigkeit
- Verständlichkeit

#### Abgestimmtheit prüfen
- Abstimmung
  - transparent
  - kann gern nach Rollen gewichtet werden
- Abstimmung nach Änderungen
- Konflikte aufgelöst

#### Prinzipien
- Prinzip 1
- Prinzip 2
- Prinzip 3
- Prinzip 4
- Prinzip 5
  - Pilotsysteme zur Machbarkeitsprüfung der Anforderung
  - Vermindert das Risiko, dass Anforderungen nicht umsetzbar sind
  - Grenzen festlegen oder feststellen (Hosting, etc.)
- Prinzip 6
  - nicht zu viel verlangen, Prüfung ist statisch (Momentaufnahme), Anforderungen können sich ändern
  - Empfehlung: spätere Prüfung oder wiederholte Prüfung zu späterem Zeitpunkt
  - Wann?
    - viele neue Anforderungen, die das Gesamtsystem um echt Funktionalitäten erweitert
    - neues Wissen durch fortlaufendes RE
    - längerfristige Projekte
    - unbekannte Domäne


#### Techniken zur Prüfung von Anforderungen
- Stellungnahme
- Walthrough
- Inspektion

### Anforderungen abstimmen

## Foliensatz reqeng-le-8
### Anforderungen verwalten (optional Zusatzfolien)
- Attributtyp: -> Seite 11
  - Stabilität = erwartete Änderungswahrscheinlichkeit
  - Kritikalität = Schaden und Eintrittswahrscheinlichkeit
  - Priorität = Wichtigkeit bezogen auf ein definiertes Priorisierungsmerkmal
    - **Wichtig:** Priorität braucht einen Bezug, z.B. Markskzeptanz, Umsetzungsreihenfolge, Opportunitätskosten
- weitere Attributionstypen:
  - Aufwand
  - Status Inhalt
  - Status bzgl. Einigung
  - Juristische Verbindlichkeit
  - Status bzgl. der Überprüfung (z.B. Review)
  - Release
- **Nutzen:** Anforderungen werden nicht nur fahclich sondern auch organisatorisch strukturiert
 
 #### Modellbasierte Attibutierung
 - Anforderungen werden nach einem vorher festgelegten Modell mit Attributen versehen
 - Modell legt fest:
  - welche Anforderunstypen gibt es 
  - welche Attribute je Typ erlaubt oder verpflichtend sind
  - welche Werte erlaubt sind
  - welche Beziheungen zu anderen Artefakten erlaubt sind
- einfaches Anforderungsmodell:
  - Anforderung = hat ID, Name, Beschreibung, Status, Quelle
  - Funktionale Anforderung = hat zusätzliche Priorität, Release, Verantwortlichen
  - Qualitätsanforderung = hat zusätzlich Messkriterium, Akzeptanzwert
  - Status = Review, in Bearbeitung, etc...
- Priorisierungstechnik

#### Sichten auf Anforderungen (S. 15 ff.)
#### Priorisierung von Anforderungen (S. 21 ff.)
- Wiegers'sche Priorisierungsmatrix
  - Anforderungen, relativer Nutzen, relativer Nachteil
  - aus Nutzen und Nachteil entstehen relative Kosten
    - z.B. indem ich für jede Anforderung den Nutzen mit 2 und den Nachteil mit 1 gewichte
    - Werte werden kumuliert -> Gesamtzahl entspricht 100% -> prozentualer Wert für jede Anforderung kann errechnet werden
  - Relative Kosten und relatives Risiko selbst festlegen

#### Verfolgbarkeit von Anforderungen (S. 30 ff.)
#### Versionierung von Anforderungen (S.40 ff.)
#### Verwaltung von Anforderungsänderungen

## Foliensatz reqeng-le-9
### Werkzeugunterstützung

## Foliensatz reqeng-akzeptanzkriterien
### Akzeptanzkriterien
- Anforderungen beschreiben, was ein System leisten soll.
- Akzeptanzkriterien beschreiben, woran erkennbar ist, dass eine Anforderung erfüllt ist.
- Sie helfen dabei:
  - vage Aussagen zu präzisieren
  - ein gemeinsames Verständnis herzustellen
  - Entwicklung und Test zu orientieren
  - kann fachliche Akzeptanz nachvollziehbar machen

- Akzeptanz ist nicht dasselbe wie Prübarkeit
- Akzeptanz bedeutet
  - Eine Anforderung oder Lösung wird fachlich als erfüllt angenommen.
- Prübarkeit bedeutet:
  - Es kann objektiv festgestellt werden, ob eine Bedingung erfüllt ist. 

- Ein Akzeptanzkriterium legt fest, unter welchen Bedingungen eine Anforderung als erfüllt gilt
- gute Akzeptanzkriterien:
  - eindeutig
  - beobachtbar oder messbar (für Nutzergruppe, konkrete Informationen aggregieren)
  - realistisch
  - fachlich relevant
  - testbar
- **Ein Akzeptanzkriterium ersetzt die Anforderung nicht, sondern macht sie überprüfbar.**

- 2 unterschiedliche Prükriterien:
  - **Validierung**: Ist die richtige Lösung beschrieben?
  - **Verifikation**: Ist die beschriebene Lösung korrek realisiert?
- **Akzeptanzkriterien verbindlichen fachliche Erwartungen und spätere Prüfung.**

- Ohne Akzeptanzkriterium bleiben Anforderungen oft interpretationsanfällig.
- Beispiel 1:
  - Anforderung: "Das System soll benutzerfreundlich sein"
  - Problem:
    - Was soll benutzerfreundlich bedeuten?
    - Für welche Bentuzergruppe?
    - In welcher Situation?
    - Woran wird Erfolg erkannt?
- Beispiel 2:
  - Anforderung: "Das System soll es dem Kunden erleichtern, gewünschte Musik zu finden."
  - Akzeptanzkriterium: "90% der Testpersonen aus der Zielgruppe finden einen bekannten Musiktitel innerhalb von 6 Sekunden und mit höchstens 3 Aktionen"
- **Akzeptanzkriterien und nicht-funktionale Anforderungen sind nicht weit voneinander entfernt**

- Die Begrüdung erklärt, warum eine Anforderung existiert.
- Sie hilft dabei:
  - die eigentliche Absicht zu verstehen
  - passende Messgrößen zu finden
  - versteckte Mehrfachanforderungen zu erkennen
  - unnötige oder falsche Anforderungen zu hinterfragen
- Woran würde der Fachbereich erkennen, dass diese Anforderung nicht erfüllt ist?

- Gute Formulierungn enthalten mehr Details, z.B. sicher -> Passwort mit mindestens 12 Zeichen

- **Akzeptanzkriterien können Ziel- oder Grenzwerte enthalten**
- Nutzen:
  - Zielwert beschreibt die erwrtet Qualität
  - Grenzwert beschreibt die noch akzeptable Grenze
  - Ausnahme und Toleranzen werden sichtbar
  - wichtig für Tests und Überprüfbarkeit 

- Bei **funktionalwn Anforderungen** zählt, ob das fachliche Ergebnis korrekt ist.
- Beispiel: 
  - Anforderung: "Das System speichert Messwerte von Wetterstationen"
  - Akzeptanzkriterium: "Nach erfolgreiche Übertragung stimmen die im System gespeicherten Messwerte mit den von der Wetterstation gesendeten Messwerten überein."

- **Qualitätsanforderungen** (nicht-funktional) müssen so konkretisiert werden, dass ihre Erfüllung nachweisbar geprüft werden kann.
-  Beispiel:
  - Anforderung: "Das System soll gut bedienbar sein."
  - Akzeptanzkriterium: "Neue Benutzer können innerhalb von 30 Minuten einen Datensatz anlegen, ändern und löschen, ohne externe Hilfe zu verwenden."

- **Randbedingungen** (nicht-funktional) schränken die Zulässige Lösung ein.
- Beispiel:
  - Randbedingung: "Der Softwareanteil des Sytems muss unter Linuxs laufen"
  - Akzeotanzkriterium: "Alle freigegebenen Funktionen laufen korrekt unter der festgelegten Linux-Distribution und Version"

- **Ein Akzeptanzkriterium ist noch kein Testfall.**
  - beschreibt Bedingung für Akzeptanz
  - fachliche formuliert
  - relativ stabil
  - Input für Tests
- Testfall:
  - beschreibt konkrete Prüfschritte
  - operativ formuliert
  - kann je Testumgebung variieren
  - konkrete Durchführung der Prüfung
- **Akzeptanzkriterien sagen, was gelten muss. Testfälle beschreiben, wie es geprüft wird.**

- Wie Akzeptanzkriterien können formuliert werden? -> siehe Foliensatz Seite 19

[!NOTE] Akzeptanzkriterien
> konkretisieren fachliche Erwartungen
> reduzieren Interpretationsspielräume
> verbinden Anforderungen mit Tests
> unterstützen Entwicklung, Review und Abnheme
> Eine gute Anforderung sollte so formuliert sein, dass ihre Erfüllung nachvollziehbar geprüft werden kann.