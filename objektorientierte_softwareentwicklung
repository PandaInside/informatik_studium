# Objektorientierte Programmierung

## Anforderungen an Software

### Wartbarkeit
- lesbarer Code → sinnvolle Bezeichnungen
- ausreichend dokumentieren → JavaDoc
- kein doppelter Code
- Änderung Anforderung → Änderungen nur an einer Stelle
- Änderung in Klasse → keine unerwarteten Querbeeinflussungen
- Änderung an Klasse → erfordert nicht, zahlreiche andere Klassen zu studieren

### Austauschbarkeit
- bekannte Schnittstellen nutzen → kann genutzt werden, ohne wissen zu müssen, wie es genau programmiert ist
- gegen Schnittstellen programmieren → bei konstanten Schnittstellen, schneller Austausch
- Datenkapselung → Verborgenes Innenleben → Änderungen jederzeit, ohne dass rufende Klassen geändert werden müssen

**→ Datenkapselung** 
- **Richtlinien:**
	- Attribute private → Zugriff nur über get() und set()
	- keine Referenzen auf interne Hilfsobjekte nach außen geben
- **Folge:**
	- Interne Repräsentation kann später geändert werden, ohne dass andere Klassen zu ändern sind.
- **Beispiel:** 
	- Hash-Algorithmus & Kollisionauflösung 
	- Kollision in kryptographischen Hash-Funktionen tritt auf, wenn zwei unterschiedliche Eingabedaten denselben Hash-Wert erzeugen. 
	- Beeinträchtigt Integrität und Sicherheit von Systemen, die auf der Unveränderlichkeit von Hash-Werten beruhen.

## Kohäsion & Kopplung

### Kohäsion
Anzahl und Vielfalt der Aufgaben, für die eine einzelne Einheit verantwortlich ist.

##### Ziel: Hohe Kohäsion
- Klasse/Methode kümmert sich um genau eine Aufgabe.
- In Klasse gespeicherte Daten sollen genau eine Sache beschreiben.
- Methoden beschäftigen sich damit, diese Daten zu verarbeiten.
- Ermöglicht ...
	- Verständnis, was Klasse/Methode  macht.
	- beschreibende Namen zu verwenden
	- Wiederverwendbarkeit von Klassen/Methoden
	- leichtere Testbarkeit von Methoden

### Kopplung
- Gibt an, wie stark Klassen oder Module voneinander abhängig sind.
- Wenn zwei Klassen in vielen Aspekten **stark voneinander abhängen**, sprechen wir von einer **engen/hohen Kopplung**.
- Hohe Kopplung entsteht, wenn Sachverhalte nicht sinnvoll zusammengefasst werden.

##### Ziel: Lose Kopplung

### Zusammenhänge
- Werden zu wenige Klassen entworfen werden diese unübersichtlich und machen sie zu viel (Kohäsion niedrig).
- Werden zu viele Klassen entworfen gibt es viele Beziehungen (Kopplung hoch)
- **Geheimnisprinzip (Information Hiding):** 
	- Details einer Klasse sollen vor externem Zugriff verborgen bleiben (für Schutz & Unabhängigkeit)
	- klar definierte Schnittstelle (Methoden) für den Zugriff von außen bereitgestellt → kontrollierter Zugriff mit Zugriffmodifikatoren `private`, `protected` und `public`
	- Verhindert, dass andere Teile des Programms Daten in einen inkonsistenten Zustand versetzen → Änderungen können vorgenommen werden ohne den aufrufenden Code anpassen zu müssen

##  Entwurfsprinzipien
Prinzipien, um ein System in Teilsysteme zu zerlegen

1. **Jedes Teilsystem hat eine klar umrissene fachliche / technische Aufgabe**
	- Anwendungsfälle clustern
	- UML (Unified Modeling Language) → standardisierte, grafische Modellierungssprache zur Visualisierung, Spezifikation, Konstruktion und Dokumentation von Software-Systemen und Geschäftsprozessen.
<br>
2. Möglichst **wenig Abhängigkeiten** zwischen Teilsystemen
<br>
3. **Keine Redundanzen**
	- Neues Teilsystem, wenn Funktionalität mehrfach benötigt wird.
	- Redundanzen ...
		- sind Zeichen von schlechtem Entwurf
		- erschwert die Wartung
		- führt zu weiteren Fehlern bei Wartung

### Entwurfsregeln
- Eine Methode ist zu lang, wenn sie mehr als eine logische Aufgabe erledigt.
- Ein Klasse ist zu komplex, wenn sie mehr als eine Sache repräsentiert.
- **Entwurf nach Zuständigkeiten** für lose Kopplung:
	- Frage: In welche Klasse gehört eine Methode?
	- Die Klasse, die für die Daten verantwortlich ist, sollte sie auch verarbeiten.

## Vorsatz: Clean Code
### Einführung
##### Warum?
- Code wird häufiger gelesen als geschrieben
- Softwarekosten zu 80-90% durch Wartung
- Klarheit
- Lesbarkeit = Produktivität
- Einfachheit
- Trennung von Verantwortlichkeiten
- Wiederverwendbarkeit
- Bugvermeidung

##### Prinzipien
- **KISS** – Keep it simple, stupid
	- Komplexität vermeiden
	- Code soll selbsterklärend sein
<br>
- **DRY** – Don't repeat yourself
	- Duplizierter Code ist schwer zu warten und fehleranfällig
<br>
- **YAGNI** – You ainʼt gonna need it
	- Keine Features implementieren, nur weil sie "vielleicht später gebraucht werden"
	- Jede unnötigt Funktion erzeugt Kosten
<br>
- **SRP** – Single Responsibility Principle
	- Eine Klasse / Methode = eine Verantwortung
<br>
- **SoC** – Separation of Concerns
	- Trennung von UI, Business Logik, Persistenz und Infrastruktur
	- Mehr Wiederverwendbarkeit, klare Architektur, weniger Abhängigkeiten
<br>
- **SLA** – Single Level of Abstraction
	- In einer Methode sollen alle Schritte dieselbe Abstraktionsebene haben
	<br>
	```Java
	validate( order );
	double total = 0;
	for( Item i : order.items() ) {
		total += i.price();
	}
	repo.save( order, total );
	email.send( order.customer().email(), "Danke!" );
	```
		
	**↓**
	
	```Java
	public void processOrder( Order order ) {
		validate( order );
		double total = calculateTotal( order );
		saveOrder( order, total );
		notifyCustomer( order );
	}
	```
<br>
- **Tell, donʼt ask**
	- Vermeidung Trainwreck (= Anti-Pattern, bei dem mehrere Methodenaufrufe hintereinander verkettet werden)
	- Verletzt "Law of Demeter"
	<br>
	```Java
	if( user.getAddress().getCity().equals("Berlin") ) { ... }
	```
		
	**↓**
	
	```Java
	if ( user.livesIn("Berlin") ) { ... }
	```
	<br>
	- Objekte sollen Verantwortung tragen, nicht nur Daten halten
<br>
- **Law of Demeter** (Entwurfsrichtlinie)
	- Eine Klasse sollte möglichst wenig Kontakt zu „entfernten“ Codeteilen haben.
	- Eine Methode M der Klasse K sollte nur zugreifen müssen auf:
		- Methoden von K selbst
		- Methoden der beim Aufruf von M übergebenen Parameter
		- Methoden der mit K assoziierten Objekte (also die "unmittelbaren Nachbarn")
		- Methoden von Objekten, die M erzeugt
<br>
- **Favor Composition over Inheritance**
	- Komposition ist flexibler als Vererbung
		<br>
	```Java
	class FastCar extends Engine { ... }
	```
	→ Enge Kopplung
	
	**↓**
	
	```Java
	class FastCar {
		private Engine engine;
	}
	```
	<br>
	→ Lose Kopplung, testbar, erweiterbar
<br>
- **PoLA** - Principle of Least Astonishment
	- Code soll keine Überraschungen verursachen
	- API-Verhalten soll erwartbar sein
	- Beispiel: Methoden sollten keine versteckten Seiteneffekte haben
		<br>
	```Java
	public class UserRepository {
		public User findById(String id) {
			// Überraschung:
			// Wir machen hier einen Remote-Call ins Internet,
			// warten 3 Sekunden, und verwenden nebenbei einen lokalen Cache
			sleep(3000);
			return cache.get(id);
		}
	}
	```
	- Problem: 
		- Entwickler, der `findById` aufruft, erwartet eine schnelle Antwort (meist aus einer DB oder einem Cache). 
		- Dass die Methode "überraschend" einen Remote-Call ins Internet macht, ohne dass dies im Namen (z.B. `findRemoteById`) oder in der Dokumentation steht, führt zu schwer zu findenden Performance-Bugs an anderen Stellen im Code.
		- Außerdem erwartet niemand, dass eine scheinbare Lese-Operation das gesamte Programm für 3 Sekunden einfriert.
		- Wenn 100 Nutzer gleichzeitig eine Anfrage stellen, sind 100 Threads für 3 Sekunden belegt. Das führt sehr schnell zum Stillstand der gesamten Anwendung (Thread Exhaustion).

### SOLID
##### Single Responsibility Principle (SRP)
- Eine Klasse oder Methode soll genau **eine Verantwortung** haben.

##### Open/Closed Principle (OCP)
- Software soll **offen für Erweiterungen** sein, aber **geschlossen für Modifikationen**.
- Verhalten erweitern, ohne bestehenden Code ändern zu müssen

##### Liskov Substitution Principle (LSP)
- Subklassen müssen sich **wie ihre Basisklasse verhalten**, ohne Überraschungen.
- Eine Unterklasse muss komplett austauschbar sein

##### Interface Segregation Principle (ISP)
- Code soll **keine größeren Interfaces implementieren** müssen, als er tatsächliche braucht.
- Viele kleine Interfaces statt einem riesigen.

##### Dependency Inversion Principle (DIP)
- High-Level-Code darf **nicht von konkreten Implementierungen abhängen**.
- Abhängigkeit immer von Abstraktionen, nicht von Details (z.B. Interfaces nutzen).

### Refactoring
- Bei Überarbeitung von Klassen oder Methoden, wird meist Code hinzugefügt, wodurch diese länger werden können.
- Refactoring dient der Verbesserung der Programmstruktur, um Kohäsion und lose Kopplung zu erhalten
- Sollte getrennt von anderen Änderungen erfolgen. Erst Refactoring, ohne Änderungen an Funktionalität.
- Tests sollte davor und danach durchgeführt werden, um Fehler zu vermeiden.

### Magic String & Magic Number
- Ein Wert, welcher einer Methode ohne Kontext (also nicht als Variable) übergeben wird.
- Vermeide "magische Strings", nutze stattdessen Enums.

	```Java
	if( commandWord.equals('hilfe') ) {
		printHelp();
	} else if( commandWord.equals('gehe') ) {
		goRoom(command);
	} else if( commandWord.equals('umsehen') ) {
		System.out.println(...);
	} else if( commandWord.equals('ende') ) {
		wantToQuit = quit(command);
	}
	```
	
	**↓**
	
	```Java
	public enum Direction {
		NORDEN,
		SUEDEN,
		OSTEN,
		WESTEN
	}
	```
<br>
- Vermeide "magische Zahlen".

	```Java
	double bruttoPreis( double preis ) {
		return preis * 1.17;
	}
	```
	
	**↓**
	
	```Java
	static finl double MEHRWERTSTEUERSATZ = 17;
	
	double buttoPreis( double preis ) {
		return preis * ( 100 + MEHRWERTSTEUERSATZ ) / 100;
	}
	```
<br>
- Vermeide `if` bzw. `switch`, wenn es sich auch mit Vererbung lösen lässt!

	![](assets/Vererbung.png)
<br>
- Vermeide null (= kein Referenzwert) als möglichen Wert, insbesondere als Rückgabewert oder als Parameter bei einem Funktionsaufruf!
- Null-Objekt, wenn kein gültiger Wert (Spiel: Kommando) eingegeben wurde. Ersetzt Rückgabe von null. 
- **Vorteil:** Kein Test auf null mehr nötig.

	![](assets/NullObjekt.png)

### Optionals
- Vermeidung `null` als Rückgabewert durch Optionals ("Kisten") - instanziierte Objekte, die entweder leer oder mit einem Wert sind.

	```Java
	/**
	* @return erreichter Zielraum, <null> wenn es in die angegebene Richtung keinen Ausgang gibt.
	*/
	public Room getExit( String direction ) {
		return exit.get( direction );
	}
	
	Room nextRoom = currentRoom.getExit( direction );
	if( nextRoom == null ) {
		Syste.out.println( "Da ist keine Tür" );
	} else {
		setCurrentRoom( nextRoom );
		System.out.println( nextRoom.getLongDescription() );
	}
	```
	
	**↓**
	
	- Argument ist ein Objekt: Liefert Kiste mit diesem Objekt
	- Argument ist null: Liefert leere Kiste
	
	**↓**
	
	```Java
	import java.urtil.Optional;
	
	/**
	* @ return Raum, der bei Bewegung in eine Richtung erreicht wird.
	*/
	public Optional<Room> getExit( String direction) {
		Optional<Room> optionalRoom = Optional.ofNullable( exits.get( direction ) );
		return optionalRoom;
	}
	```
<br>

- `getOrDefault(schluessel,Standardwert)`
	- liefert den Wert zurück, der in der Map unter dem Schlüssel gespeichert ist oder - wenn es keinen solchen Eintrag gibt - den Standardwert.

		```Java
		public Optional<Command> get( String word ) {
			Optional>Command> matchingCommandObject = Optional.ofNullable( ( Command ) commands.get( word ) );
			return matchingCommandObject;
		}
		```
		
		**↓**
		
		- Nimm das Objekt aus dem Optional. 
		- Sollte das Optional leer sein, nimm ersatzweise ein Null Command.
		
		**↓**
		
		```Java
		Optional<Command> command = commands.get( word1 );
		Command commandObject = command.orElse( new NullCommand() );
		commandObject.setSecondWord( word2 );
		return commandObject;
		```
<br>
- `Optionals`
	- Ersetzen von Rückgabewerten von Methoden, die unter Umständen null liefern können
	- `ifPresentOrElse` besser als `isPresent` / `get`
	- nicht als "normale" Attribute verwenden
	- nur in Ausnahmefällen als Parameter von Methodenaufrufen

## Inversion of Control
Die Kontrolle über Abhängigkeiten wird abgegeben.

### Inversion of Control
- Unsere Kommandos (z.B. GoCommand) bekommen einen Listener, der ausgelöst wird, wenn auf eine Schaltfläche gedrückt wird.
- Allgemein spricht man von einer **Rückruf-Schnittstelle (callback interface)**: Unser Programm bietet die Möglichkeit aufgerufen zu werden.
- Damit steuern GUI-Ereignisse den Programmablauf, nicht mehr fester Code im Programm

### Kopplung an System.out rauswerfen
- Alle Ausgaben werden durch den Aufruf einer Methode printSomething ersetzt.
- Die kann dann passend implementiert werden, z.B. zur Ausgabe des Textes in ein GUI-Textfenster.
- Zusätzlich kann man bei Änderungen des Zustands, weitere Änderungen an der GUI vornehmen.
- **Änderungen sind nur noch an einer Stelle nötig.**

```Java
printSomething( "Type 'help' if you need help." );
printSomething( "" );
printLocationInfo();
printSomething( "" );

private void printSomething( String text ) {
	System.out.println( text );
}
```

- Ausgabelogik (printSomething) gehört nicht in Game!
- Die Implementierung von printSomething soll austauschbar sein.
- Damit kann das Spiel mit verschiedenen GUIs laufen.

![](assets/Austauschbarkeit.png)

### Dependency Injection
- Die Möglichkeit, Abhängigkeiten zur Laufzeit festzulegen.
- Die Abhängigkeit soll nicht über ein festes "new" einprogrammiert sein.
- Trotzdem brauchen wir natürlich zur Laufzeit ein konkretes GUI-Objekt.

| Art                            | Beschreibung                                                                                                                                                                                                                                                      | Vorteile                                                                                                                                     | Nachteile                                                                                                   |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Contructor Injection           | Statt der "richtigen" Klasse wird eine Stub-Klasse (Platzhalter für eine noch nicht implementierte oder komplexe Komponente, die in Tests feste Rückgabewerte liefert) genutzt.<br>DI kann überall angewendet werden, wo Objekt instanziiert wird.                | + Erzwingt Vollständigkeit der Abhängigkeiten bei Instanziierung<br>+ Fördert Unveränderlichkeit<br>+ Erleichtert das Testen<br>+ Sicherheit | - Kann bei einer großen Anzahl von Abhängigkeiten unübersichtlich werden                                    |
| Setter Injection               | Grundregel: Arbeite wenn immer möglich mit komplett instanziierten Objekten.<br>Folgerung: Im Konstruktor wird zumindest ein "Standard"-Objekt erzeugt, so dass die Anwendung auch lauffähig ist, wenn die betr. Attribute nie per set-Anweisung geändert wurden. | + Einfügen von Abhängigkeiten über Setter-Methoden nach der Bean-Erstellung nützlich für **optionale Abhängigkeiten**<br>+ Flexibilität      | - Birgt das Risiko, dass Beans teilweise ohne notwendige Konfigurationen genutzt werden<br>- weniger sicher |
| Field Injection                | Abhängigkeiten werden direkt über Annotationen (wie `@Autowired`) in private Klassenfelder injiziert, ohne Setter oder Konstruktoren zu benötigen.                                                                                                                | + Bekannt für **Einfachheit**, da sie direkte Injections ohne Setter und Constructor erlaubt                                                 | - Führt zu einer **schwierigen Testbarkeit** und potentiellen Missachtung des SOLID-Prinzips                |
| Dependency Injection Container | Objekt, das für die Instanziierung und Konfiguration anderer Objekte (sogenannter Dienste) verantwortlich ist.                                                                                                                                                    |                                                                                                                                              |                                                                                                             |
| Service Locator                | Die Klasse Game fragt zur Laufzeit bei einem "allwissenden" Register (Registry) nach den benötigten Abhängigkeiten.<br>Man spricht dann von **Dependency Loopkup**.                                                                                               |                                                                                                                                              |                                                                                                             |

### Parameter-Objekte
- bündelt mehrere Daten für eine spezifische Funktion in einem einzigen Objekt. 
- reduziert bzw. bündelt die Anzahl der Parameter in Methodensignaturen.
- gestaltet Code übersichtlicher
- verbessert die Struktur

```Java
public interface GUI {
	public void printSomething( String text );
	public void showNextRoom( Room room );
	public voidshowNewInventory( List<Item> items );
}
```

**↓**

```Java
public interface GUI {
	public void showNewSituation( String text, Room room, List<Item> items, int TimeLeft );
}
```

**↓**

```Java
public interface GUI {
	public void showNewSituation( Situation s );
}
```

##### Allgemeines Wissen
- **Objektübergabe:** nicht nur primitive Werte, sondern auch Instanzen von Klassen (Objekte) als Parameter an Methoden übergeben
- **Methodenparameter:** dienen als Platzhalter im Methodenkopf und werden beim Aufruf mit Werten initialisiert.
- **Call-by-Value:** Der Wert des Parameters wird übergeben.
- **Call-by-Reference:** Bei Objekten wird in der Regel eine Referenz (Speicheradresse) übergeben, wodurch Änderungen am Objekt innerhalb der Methode Auswirkungen auf das ursprüngliche Objekt haben.
- **Unterschied zu Attributen:** Während Attribute (Felder) den Zustand eines Objekts dauerhaft speichern, sind Parameter lokale Variablen, die nur während der Ausführung einer Methode gültig sind.

## Top Java Fehler
1. **NullPointerException (NPE)**
	- Zugriff auf `null` Referenz
<br>
2. **Off-by-One / IndexOutOfBound**
	- Falsche Schleifenbedingungen oder Indexgrenze
	<br>
	```Java
	for ( int i = 0; i <= arr.length; i++ ) { ... }
	```
<br>
3. **ConcurrentModificationException**
	- Änderung während Iteration (Schleife) über Collection (abstraktes Objekt)
	- Folge: Die Struktur der Liste wird während des Durchlaufs instabil
	- Lösung: Sicherer ist ...
		- Nutzung eines Iterators (`iterator.remove()`)
		- Erstellen einer Kopie der Liste 
		- Zwischenspeichern der Änderungen in einer separaten Liste
	<br>
	```Java
	for ( String s : list ) list.remove( s );
	```
	
	**↓**
	
	```Java
	for ( Iterator<String> it = list.iterator(); it.hasNext(); ) {
		if ( it.next().isBlank() ) it.remove();
	}
	```
<br>
4. **== statt .equals()**
	- Vergleich von Referenzen statt echten Werten
<br>
5. **Ressourcen-Leak**
	- Stream oder Reader nie geschlossen → ungenutzte Ressourcen bleiben belegt
	- Folge: Erschöpfung Systemkapazitäten, Leistungseinbußen, Programmabstürze
<br>
6. **Falsche Verwendung von Generics**
	- Raw Types oder unsichere Casts
	<br>
	```Java
	List list = new ArrayList();
	list.add("Hi");
	Integer i = ( Integer ) list.get( 0 ); // ClassCastException
	```
	
	**↓**
	
	```Java
	List<String> list = new ArrayList<>();
	String s = list.get( 0 );
	```
<br>
7. **Fehlender oder inkonsistenter `hashCode()`**
- Zwei Objekte sind laut `equals()` gleich, aber landen in unterschiedlichen Buckets.
- Mit korrektem `hashCode()` erkennt HashSet bzw. HashMap das Objekt als gleichwertig. 
- Lösung:
	- `equals()` und `hashCode()` müssen dieselben Felder berücksichtigen. Wenn zwei Objekte nach `equals()` gleich sind, müssen sie laut Java-Spezifikation auch den gleichen `hashCode()` liefern.
	- Die Methoden hashCode und equals haben immer einen ähnlichen Aufbau und sind somit Boilerplate Code.
	- Beim Entwickeln von Entity-Komponenten, müssen Sie immer an die hashCode- und equals-Methoden denken. Beide müssen gemeinsam überschrieben werden, um logische Gleichheit und korrekte Funktionalität zu gewährleisten - also Inkonsistenzen zu vermeiden.
<br>
8. **ClassCastException**
	- Downcasting ist das explizite Umwandeln einer Referenz von einem Supertyp (Elternklasse) in einen Subtyp (Kindklasse), um auf spezifische Methoden der Kindklasse zuzugreifen.
	- **Notwendigkeit:** Wird verwendet, wenn ein Objekt, das als Supertyp behandelt wurde (z.B. in einer Liste), wieder in seinen ursprünglichen, spezifischeren Typ umgewandelt werden muss.
	- `instanceof` überprüft, ob das Objekt tatsächlich vom Zieltyp ist, bevor der Cast durchgeführt wird.
<br>
9. **ArithmeticException**
	- Division durch 0 oder Überlauf
<br>
10. **Uninitialisierte Variablen / Felder**
	- Nutzung vor Zuweisung
	<br>
	```Java
	int total;
	System.out.println( total );
	```
	
	**↓**
	
	```Java
	int total = 0;
	System.out.println( total );
	```
<br>
11. **String Fehler / Immutability (Unveränderlichkeit von erstellten Daten)**
- Strings unverändert, weil Ergebnis ignoriert
	<br>
	```Java
	String s = "Hi";
	s.concat( " there" );
	System.out.println( s ); // "Hi"
	```
	
	**↓**
	
	```Java
	String s = "Hi";
	s = s.concat( " there" );
	System.out.println( s ); // "Hi there"
	```
<br>
12. **Falsche Collection-Typen**
- Nutzung veralteter Klassen
<br>
13. **Fehlerhafte Exception-Behandlung**
- Exception verschluckt
	<br>
	```Java
	try {
		process();
	} catch ( Exception e ) {}
	```
	
	**↓**
	
	```Java
	try {
		process();
	} catch ( IOException e ) {
		log.warn( "Fehler: {}", e.getMessage() );
		throw e;
	}
	```
<br>
- **Fehlerbehandlungsstrategien:**
	- Java erlaubt unterschiedliche Strategien, wie mit Fehlern umgegangen wird.
	- Die Wahl bestimmt Stabilität, Fehlersichtbarkeit und Benutzererlebnis.
	
	| Strategie   | Verhalten                                                                                             | Verwendung                                                                                                                                                                                                                                     | Vorteil                  | Nachteil                                                                                | Beispiel                   |
	| ----------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | --------------------------------------------------------------------------------------- | -------------------------- |
	| Fail Silent | Fehler ignorieren<br>Fehler wird verschluckt → System läuft aber scheinbar weiter.                    | Unkritischen UI- oder Logging-Fehlern (selten sinnvoll).                                                                                                                                                                                       | keine Unterbrechung      | Fehler bleibt verborgen<br>Schwer zu debuggen<br>Datenverlust<br>inkonsistenter Zustand | ![](assets/FailSilent.png) |
	| Fail Fast   | Fehler sofort melden und sichtbar machen<br>Stoppt Ausführung früh, sobald Inkonsistenz erkannt wird. | API-Verträgen<br>Validierungen<br>Kritische Invarianten (= unveränderliche Bedingungen, Eigenschaften oder Größen, <br>die während der Ausführung eines Algorithmus, einer Transformation oder bei Koordinatensystemwechseln konstant bleiben) | Fehler leicht auffindbar | ggf. Absturz                                                                            | ![](assets/FailFast.png)   |
	| Fail Safe   | Trotz Fehler sicher weiterarbeiten.<br>System bleibt lauffähig, nutzt Default- oder Ersatzwerte.      | Systemdiensten<br>Hintergrundjobs<br>Caches                                                                                                                                                                                                    | Robust im Betrieb        | evtl. falsche Daten                                                                     | ![](assets/FailSafe.png)   |
<br>
- Merke: Fail Fast im Code - Fail Safe im System
- Entwickle so, dass Fehler früh erkannt werden, aber das Gesamtsystem stabil bleibt.
<br>
14. **Float- / Double-Vergleich**
- Direkter Vergleich von Gleitkommazahlen
	<br>
	```Java
	if( a == b )
	```
	
	**↓**
	
	```Java
	if (Math.abs(a - b) < 1e-6)
	```
<br>
15. **Immutability missachtet**
- Mutable Rückgabe erlaubt externe Änderung
	<br>
	```Java
	class Order {
		List<String> items = new ArrayList<>();
		List<String> getItems() {
			return items;
		}
	}
	```
	
	**↓**
	
	```Java
	class Order {
		private final List<String> items = new ArrayList<>();
		List<String> getItems() {
			return List.copyOf( items );
		}
	}
	```
<br>
16. **Seiteneffekt Call-by-Value (Referenzen)**
- Methoden verändern übergebene Objekte unerwartet
- Java übergibt immer Call-by-Value, auch bei Objekten → Referenz wird kopiert, nicht das Objekt
	<br>
	```Java
	class Person {
		String name;
		
		void setName( String n ) {
			name = n;
		}
	}
	
	void modify( Person p ) {
		p.setName( "Anna" ); // wirkt auf Originalobjekt
		p = new Person(); // nur lokale Variable neu
	}
	
	Person u = new Person();
	u.setName( "Max" );
	modify( u );
	System.out.println( u.name ); // Ergebnis: "Anna" → Seiteneffekt
	```
	
	**↓**
	
	- Keine Mutationen an Eingabeobjekten
	- Immutable Klassen oder defensive Kopien
	- Neue Instanz zurückgeben statt Original ändern
	
	**↓**
	
	```Java
	Person.rename( Person p, String newName ) {
		return new Person( newName );
	}
	```
<br>
17. **Thread-Safety: typische Fehler & Strategien**
- Mehrere Threads greifen gleichzeitig auf dieselben Objekte oder Collections zu
- Folge: Race Conditions, inkonsistente Zustände, Exceptions
	<br>
	```Java
	class Counter {
		private int count = 0;
		void inc() {
			count++; // kein Schutz
		}
	}
	
	Counter c = new Counter();
	Runnable r = () -> IntStream.range( 0, 1000 ).forEach( i -> c.inc() );
	new Thread( r ).start();
	new Thread( r ).start();
	System.out.println( c.count ); // Ergebnis unbestimmt
	```
<br>
- **Lösungsstrategien:**
	1. Synchronisation
		<br>
		```Java
		synchronized void inc() {
			count++;
		}
		```
	<br>
	2. Atomare Klassen
		<br>
		```Java
		class SafeCounter {
			private final AtomicInteger count = new AtomicInteger();
			void inc() {
				count.incrementAndGet();
			}
		}
		```
	<br>
	3. Thread-Sichere Collections
	
		| Typ                    | Beschreibung                     |
		| ---------------------- | -------------------------------- |
		| `CopyOnWriteArrayList` | snapshot-basiert, faile-safe     |
		| `ConcurrentHashMap`    | segmentbasiert synchronisiert    |
		| `BlockingQueue`        | thread-safe für Product/Consumer |

	4. Immutability
		- Unveränderliche Objekte = automatisch thread-safe
		- Keine gemeinsamen veränderlichen Zustände
		- Builder oder Factory nutzen statt Setter

## Manuelle Code Reviews
### Kriterien für Reviews von Anforderungen
- Ist für jede Anforderung ein Abnahmekriterium definiert?
- Wird wirklich die Anforderung beschrieben (statt der Lösung)?
- Verständlich?
- Mit dem Kunden abgestimmt?
- Aktualität? Anforderungen können sich ständig ändern.
- Klarheit, von wem die Anforderung kommt?
- Begründung für die Anforderung?

### Kriterien für Reviews von Pull-Requests
- Bezieht sich der Pull-Request auf ein einziges Thema?
- Selbsterklärende Commit-Messages?
- Ausreichend Tests & Dokumentation?
- Code-Kriterien:
	- einfach
	- Einhaltung Geheimnisprinzip
	- selbst-sprechende Methodennamen (keine Überraschungen)
	- kein toter Code ("für später" oder nicht benötigt)

### Allgemeines
- Systematische Untersuchung des Quellcodes zur Fehleridentifikation
- **Ziele:**
	- Qualitätssicherung der Software
	- Wissenstransfer (Weiterbildung und Verteilung des Wissens)
- Erkennen von:
	- Fehler in Anforderungen oder Programm
	- Abweichung von ==Programmrichtlinien==
	- Unzureichende Wartbarkeit / schlechte Design
	- usw.
- **Voraussetzung:** ==lesbarer Code==
- **Probleme:**
	- unangenehm für Beteiligten
	- Gefühl ungerechter oder gar persönlicher Kritik
	- Wahrnehmung als aufgezwungener, unnötiger Schritt
	- Auffassung als Misstrauen des Managements
	- kann zu Wettkampf führen
- **Vermeidung:**
	- Als Reviewer beachten:
		- Aussagen lieber als Nachfragen formulieren
		- Loben
	- Als Entwickler beachten:
		- Review macht nur seine Arbeit
		- Lernerfahrung
		- keine Defensivität
		- Unterstützung bei Einhaltung der Programmierrichtlinien

##### Lesbarer Code (Style Guide)
- Style Guide definiert visuelle Formatierung
- selbst-sprechende Bezeichner
- Namenskonventionen (z.B. Dateiname-JJ-MM-TT)
- Einrückungen
- Klammern verwenden
- Kommentare, Dokumentation, grafische Modelle

> [!QUOTE] James O. Coplien
> "You should name a variable using the same care with which you name a first-born child"

##### Programmierrichtlinien
- sollten allen Beteiligten bekannt sein
- sollten von allen akzeptiert werden
- müssen fortlaufen aktualisiert werden
- definieren Struktur, Best Practices und Sicherheit

##### Code Reviews ohne direktes Aufeinandertreffen
- Anmerkungen an Code schreiben
- Vorteil: 
	- keine direkte Rückmeldung notwendig
	- mitunter effektiver als Meetings

##### Verbindung Reviews & Versionierung
- Integration Versionsverwaltung in Review-Prozess
- Änderungen für Reviewer leichter zu verstehen, da sie sich auf den gleichen Änderungszweck beziehen (sollten)
- Strenge Form: Review von zwei Entwicklern bevor Code versioniert wird
- wichtiges Ergebnis: kollektiver Code-Besitz (man lernt den Code anderer kennen)

### Formale Code Review
- genau geplanter Prozess mit mehreren Teilnehmern und Phasen
- Code in mehreren Meeting Zeile für Zeile untersuchen
- Vorteil: gründlich, viele Fehler werden gefunden
- Nachteil: zeitaufwändig

##### Phasen formaler Reviewprozesse
1. **Planung**
	- Auswahl beteiligter Personen & Rollenbesetzung
	- Festlegung Eingangskriterien (z.B. Dokumentation, Prüfunterlagen, Zeitplan) & Ausgangskriterien (Protokollierung, Fehlerbehebung, Kennzahlen zur Optimierung des Reviewprozesses, Abnahme)
2. **Kick-Off**
	- Verteilung der Dokumente
	- Erläuterung der Ziele & des Prozesses
	- Prüfung Vorbedingungen (Eingangskriterien)
3. **Individuelle Vorbereitung**
	- Notierung potentieller Fehler, Fragen, Kommentare
4. **Reviewsitzung**
	- Diskussion & Protokollierung Ergebnisse
	- Empfehlungen oder Entscheidung über Fehler
5. **Rework (Überarbeitung)**
	- Beheben gefundener Fehler
6. **Follow Up (Nachbearbeitung)**
	- Überprüfung Rework
	- Besprechung eventuell noch offener Punkte

### Leichtgewichtige Code Review
- Varianten:
	- Zweiter Entwickler lässt sich Code vom Autor erklären
	- E-Mail bei Quellcode-Checkin
	- Paarprogrammierung → Kernpraktik bei Extreme Programming (XP)
- Vorteil: geringerer Zeitaufwand und durchaus effektiv
- oft Teil des normalen Entwicklungsprozesses

## Automatische Code Reviews
### Qualität der Fehlererkennung
![](assets/QualitätFehlererkennung.png)

### Verfahren
- Kontrollflussanalyse
	- Kontrollfluss als Grapg
	- Beispiel: Gibt es tote Codefragmente?
- Datenflussanalyse
	- Programm als abstrakter Automat
	- Beispiel: Feldzugriff außerhalb der Feldgrenzen
- Heuristiken / Muster
	- leerer catch-Block, switch ohne break

### Werkzeuge
- Entwicklungsumgebung / Java-Compiler
	- Compileroption **-XLint**
	- Eclipse: Window > Preferences > Java > Compiler > Errror/Warnings (auch projektspezifisch möglich)
- CheckStyle
	- Ursprünglicher Zweck: Code-Formatierung und Kommentare untersuchen
	- Stärke: **Analyse von JavaDoc Kommentaren**
	- Open-Source-Tool, das Code anhand konfigurierbarer Regeln prüft.
	- Möglichkeit eigene Regeln (XML) zu definieren und Code damit zu testen.
- PMD
	- **Erkennung Duplikate und Verletzungen von Stilrichtlinien**
	- Möglichkeit der Anpassung von Regeln (XML) & Prioritäten von Fehlern
	- Eigene Regeln relativ leicht zu ergänzen
	- technologiespezifische Regeln (z.B. für Spring Boot)
	- XML-Konfiguration erlaubt Ausschluss bestimmter Codeteile von Prüfung
- Spotbugs
	- **Analysiert den Java-Bytecode**
	- Stärken im Finden von Null-Pointern oder nicht geschlossenen Streams
	- Erweiterung für Auffinden von Sicherheitsproblemen: FindSecurityBugs
- SolarLint
<br>
- **Weitere Werkzeuge** (für Smells auf Modellebene)
	- JCSC = Java Stilrichtlinien
	- DoctorJ → untersucht JavaDoc und findet u.a. Schreibfehler
	- Simian → findet Code-Duplikate in zahlreichen Sprachen
	- JLint = Programmfluss-Analyse
<br>
- Reviews der Architektur
	- für Design-Probleme, wie zyklische Abhängigkeiten zwischen Paketen, gibt es eigene Werkzeuge:
		- JDepend
		- ClassCycle
<br>
- Visualisierungen (software-Cities)
<br>
- SonarQube → integriert zahlreiche Werkzeuge für Codeanalyse, Softwaremetriken, Testabdeckung, fehlende Kommentare, etc. und unterstützt viele Sprachen

### Code Smells
Zeichen für schlechtes Design, die in einem Review erkannt werden sollten:
- Boole'sche Werte als Argumente eines Methodenaufrufs
	<br>
	```Java
	findCandidates( personList, true )
	```
	<br>
	
	- Kohäsion der Methode?
	- Erledigt sie, abhängig von dem übergebenen Boole'schen Wert, mehr als eine Aufgabe?
<br>
- Lange Boole'sche Ausdrücke
	<br>
	```Java
	if( person.age() >= 18 && ( !person.hatGebuehrenBefreiung() || person.istGewerbetreibender() ) ) { ... }
	```
	
	**↓**
	
	```Java
	if( istGebuehrenpflichtig( person ) ) { ... }
	
	// zugehörige Methode
	istGebuehrenpflichtig ( person p ) { ... }
	```
<br>
- Lange Parameterlisten → Lösung: Parameter-Objekte
<br>
- Methode gibt Werte zurück, die laut privater Konvention eine bestimmte Bedeutung haben
	<br>
	```Java
	returnValue = command.execute();
	switch( returnValue ) {
	/** 1-3 werden von goCommand zurückgegeben
	* 1 = erfolgreicher Raumwechsel
	* 2 = keine richtungsangabe
	* 3 = kein Ausgang in gegebener Richtung */
	case 1: break;
	case 2: 
		System.out.println( "Welche Richtung?" );
		break;
	case 3: 
		System.out.println( "Es gibt keinen Ausgang zu " + commanFromParser.getSecondWord() );
		break;
	```
<br>
- Doppelte Codefragmente
	- verpasste Gelegenheit für Abstraktion (Auslagern von mehrfach genutzter Funktionalität in eine Methode / Klasse)

## Komplexität
### Bedeutungen
- Schwierigkeit der umzusetzende Aufgabe
- Kosten & Zeit für Programmierprojekt (inkl. Wartung)
- Laufzeit-Komplexität (O-Notation)
	- beschreibt, wie viele Schritte ein Algorithmus benötigt, um ein Problem in Abhängigkeit der Eingangsgröße n zu lösen
	- Die **O-Notation** hilft uns den **Aufwand eines Algorithmus abstrakt** und elegant zu **beschreiben** und die Komplexität einzuschätzen. Sie **abstrahiert diese Komplexität** und hilft, **Algorithmen zu vergleichen**
	
	![](assets/ONotation.png)
	<br>
	- Merke: Bei Aneinanderreihung von Operationen, kann Gesamtkomplexität als Summe notiert werden, wobei **der stärkste Summand das Wachstumsverhalten dominiert**
	<br>
	- O( 1 ): konstante Laufzeit 
		- Rückgabe eines Elements eines Arrays unabhängig von dessen Länge
		<br>
		```Java
		def elementzugriff( arr, index ):
			return arr[index]
		```
		<br>
	- O( n ): Lineare Laufzeit
		- Rückgabe jedes Element eines Arrays
		<br>
		```Java
		def schleife( arr ) :
			for i in range( len( arr ) ):
				print( arr[ i ] )
		```
		<br>
	- O( n<sup>2</sup> ): Quadatische Laufzeit
		<br>	
		```Java
		def schleife( arr ):
			for i in range( len( arr ) ):
				for j in range( len( arr ) ):
					print( arr[ i ] )
		```
		<br>
	- O( log( n ) ): Logarithmische Laufzeit
		- Binäre Suche
		<br>
		```Java
		def binaere_suche( arr, zielwert ):
			untere_grenze, obere_grenze = 0, len( arr )
			while untere_grenze < obere_grenze:
				mitte = ( untere_grenze + obere_grenze ) // 2
				
				if arr[ mitte ] == zielwert:
					return mitte
				elif arr[ mitte ] < zielwert:
					untere_grenze = mitte + 1
				else:
					obere_grenze = mitte
		```
		<br>
	- O( 2<sup>n</sup> ): Exponentielle Laufzeit
		- Letzte Zeile: Pro Funktionsaufruf, werden zwei weitere Aufruf erzeugt → **Vervielfältigung** verdoppelt Anzahl der Aufrufe in jedem Schritt
		<br>
		```Java
		def finbonacci( m ):
			if m == 0:
				return 0
			elif m == 1:
				return 1
			return finonacci( m -1 ) + fibonacci( m - 2 )
		```
		<br>
	- O( n! ): Faktoriell (König der Komplexitäten)
		- Fakultätsberechnung → Permutationen: Jede mögliche Reihenfolge der Elemente
		<br>
		```Java
		from itertools import permutations
		
		def generate_permutations( arr ):
			return list( permutations( arr ) )
		```
		<br>

- ==Schwierigkeit für einen anderen Programmierer, das Programm zu verstehen==
- ==Zahl der benötigten Testfälle, um eine vorgegebene Testabdeckung (etwa C<sub>1</sub>) zu erreichen==

### Komplexitätsmetrik
- Eine Komplexitätsmetrik m ordnet eine Programm oder Programmteil eine reelle Zahl (das Komplexitätsmaß oder die Komplexität) zu. Sie ist also eine Funktion.

##### Zählmetriken
- Zählen der Programmzeilen (Lines of Code) → keine Kommentar- oder Leerzeilen
- Zählen der genutzten Variablen

##### Weighted Methods per Class (WMC)
- Summe der Komplexitäten aller Methoden einer Klasse

##### Cyclomatic Number (Zyklomatische Komplexität)
- von McCabe, 1976 vorgeschlagen, heute am häufigsten verwendet
- Zählen der möglichen logischen Verzweigungen in einem Programm basierend auf dem Kontrollflussgraphen
	- Sequenzielles Programm: Kanten = Knoten - 1
	- Verzweigungen: Differenz `Kanten - Knoten` steigt
- <span style="color:red">CC = Kanten im KFG - Knoten im KFG + 2</span>
- <span style="color:red">CC = Entscheidungspunkte + 1</span> → zählt Anzahl der Entscheidungen in einem Programm

```Java
int anzahl( int[] a, int[] b ) {
	int result = 0;
	int aindex = 0;
	while( aindex < a.length ) {
		int bindex = 0;
		while( bindex < b.length ) {
			if( a[ aindex ] == b[ bindex ] ) {
				result++;
			}
			bindex++;
		}
		aindex++;
	}
	return result;
}
```

![](assets/cfg.png)

###### Eigenschaften
- **obere Schranke für Zahl der Testfälle**, die für eine vollständige Zweigüberdeckung (C<sub>1</sub> - Überdeckung) nötig sind
- geeignet, um **Komplexität aus Sicht des Testens zu messen** → muss nicht notwendig etwas über Verständlichkeit aussagen
- **Zusammenhang zwischen CC und dem Wartungsaufwand** wurde in mehreren Studien bewiesen
- Ratschlag von McCabe: **CC sollte 10 nicht übersteigen**
- Ein **höherer Wert** bedeutet, dass das **Fehlerrisiko erhöht** ist und **mehr Testfälle notwendig** sind, um den Code vollständig zu testen


> [!NOTE] Nice to know
> Software für Programm im Eisenbahntunnel unter dem Ärmelkanal musste CC ≤ 20 haben, um Abnahmetest zu bestehen.

###### Schwächen
- CC = 13, trotzdem ist der Code leicht zu verstehen:
	<br>
	```Java
	switch( monat ) {
		case 1: 
			return "Januar";
			break;
		case 2:
			return "Feburar";
			break;
		...
		case 12:
			return "Dezember";
			break;
	}
	```
	<br>
- Komplexität wird in den Daten "versteckt"
	- CC = 14 - 11 + 2 = 5:
		```Java
		if(pkt > 3) {
			note = "mangelhaft";
		} else {
			note = "ungenügend"
		}
		if(pkt > 5) {
			note = "befriedigend";
		}
		if(pkt > 7) {
			note = "gut";
		}
		if(pkt > 9) {
			note = "sehr gut";
		}
		```
		
		![](assets/NotenKnoten.png)
	<br>
	- CC = 1:
		```Java
		HashMap<Integer, String> notenskala = new HashMap<>(Integer, String);
		
		notenskala.put( 10, "sehr gut" );
		notenskala.put( 9, "gut" );
		notenskala.put( 8, "gut" );
		...
		
		note = notenskala.get( pkt );
		```
		
		![](assets/NotenKnoten2.png)
	<br>

###### Diskussion
- CC wurde entwickelt für prozedurale Sprachen, wo jede Entscheidung den Code "schwieriger" macht
- CC bezieht "Kompliziertheit" der verwendeten Datenstrukturen nicht mit ein
- CC bezieht für OOP wichtige Kriterien nicht ein:
	- Kopplung
	- Entscheidungen, die aus Polymorphie resultieren
		- Polymorphie ist eng mit Vererbung verbunden und ermöglicht es, spezialisierte Unterklassen als Objekte einer allgemeineren Oberklasse (Basisklasse/Interface) zu behandeln. → werden über gemeinsame Schnittstelle angesprochen

### Messung von Verständlichkeit und Wartbarkeit
##### Größenmaß
- Zahl der Klassen

##### Kopplung
- **Kopplung zwischen Klassen (*Coupling Between Object Classes, CBO*):** 
	- Zahl der Klassen, zu denen eine bestimmte Klasse eine Assoziation hat
	- Eine Klasse mit vielen Assoziationen muss aber nicht unbedingt schlecht sein: Wenn eine Klasse oft aufgerufen wird, ist das ein Zeichen von Wiederverwendung – und das ist etwas Gutes!
- **Kopplung für ein Softwaresystem:**
	$$ \frac{Zahl der Assoziationen}{Zahl der Klassen} $$
	- betrachtet gesamtes Softwaresystem
	- schon während des Entwurfs (am Klassendiagramm) ist eine schlechte Architektur (hohe Kopplung) erkennbar
- **Fazit:**
	- Mit Zeit steigt die Kopplung
	- Refactoring dient der Verringerung der Komplexität
	- Welche Klassen sollten geändert werden? Die, die besonders viel zur Kopplung beitragen. Wir brauchen also eine Metrik für die Kopplung einzelner Klassen.

###### Information Flow Complexity (IFC)
- Für jedes Modul (z.B. Klasse) M einer Klasse bestimmen wir:
	- fan-in( M ) = Zahl der Datenübergaben der Art anderes Modul → M
	- fan-out( M ) = Zahl der Datenübergaben der Art M → anderes Modul
	$$ IFC = LOC( M ) * (fan-in( M ) * fan-out( M ))^2$$
- **Diskussion:**
	- belohnt hierarchische/baumartige Struktur
	- bestraft Klassen, die sowohl viel aufgerufen werden als auch viel andere Klassen aufrufen
	- Bibliotheksklassen, die nur aufgerufen werden, haben zwar einen hohen Fan-In, aber einen niedrigen Fan-Out und somit eine niedrige IFC
	- **Die Klassen mit hoher IFC sind auffallend häufig Quelle von Problemen**

##### Vererbung
- Tiefe des Vererbungsbaumes (*depth of inheritance tree, DIT*)
- Zahl der Unterklassen (*number of children, NOC*)

##### Kohäsion
- ***Lack of Cohesion Metric (LCOM)*** misst, wie wenig zusammenhängend die Methoden innerhalb einer Klasse sind. 
	- hoher LCOM-Wert → Methoden haben "wenig miteinander zu tun" → geringe Kohäsion (schwacher Zusammenhang) → Klasse erfüllt zu viele unabhängige Aufgaben und sollte aufgeteilt werden → Verletzung des Single Responsibility Principle (SRP)
- Betrachtet für jede Methode M<sub>i</sub> (i = 1, ..., n) einer Klasse die Menge der Attribute A<sub>i</sub> die diese Methode liest oder schreibt.
- Betrachte nun für all (n - 1)<sup>2</sup> / 2 Paare von Methoden (M<sub>i</sub>, M<sub>k</sub>) mit i ≠ k die Durchschnittsmenge A<sub>ik</sub> = A<sub>i</sub> ∩ A<sub>k</sub>
- LCOM = Zahl der leeren Durchschnitte A<sub>ik</sub> - Zahl der nichtleeren Durchschnitte A<sub>ik</sub> (oder 0, falls der Wert negativ ist)

	![](assets/LCOM.png)

## Patterns (Muster)
- **Eine Lösung für wiederkehrende Probleme**
- Muster müssen so allgemein formuliert sein, dass die nicht nur für eine bestimmte Situation anwendbar sind, sondern für eine ganze Reihe von ähnlichen Situationen.
- Ein Muster ist eine **dreiteilige Regel**, die die **Beziehung zwischen** einem bestimmten **Kontext**, einem **Problem** und einer **Lösung** ausdrückt.

	![](assets/Muster.png)

- Erfahrungen werden in wiederverwendbarer Form dokumentiert.
- Muster ermöglichen das wiederholte Nutzen von Lösungen, die sich als gut erwiesen.
- Entwickeln einer einheitlichen Terminologie zur Beschreibung wiederkehrender Sachverhalte und Lösungen.

### Forces (Kräfte)
- Softwareprojekte scheitern häufig an Nichtbeachtung nicht-funktionaler Anforderungen
- Grund: Nicht-funktionale Anforderungen "verteilen sich" über das gesamte System
- Muster dient dazu, die bestehenden Anforderungen miteinander in Einklang zu bringen

### Sinn von Mustern
- Bekannte funktionierende, gut dokumentierte Problemlösungen können wiederverwendet werden (**konserviertes Wissen**)
- gute Hilfe für Einsteiger
- Vokabular, um häufig auftretende Strukturen in der Software zu benennen.


> [!QUOTE] GoF Buch:
> "Entwurfsmuster machen ein System weniger komplex, indem sie Ihnen erlauben, auf einer höheren Ebene als der der Entwurfs- oder Programmiersprache zu sprechen. Entwurfsmuster erhöhen das Niveau, auf welchem Sie entwerfen und den Entwurf mit Ihren Kollegen diskutieren"

> [!QUOTE] Christopher Alexander
> "A pattern language is nothing more than a precise way of describing someone's experience"

> [!NOTE] Wichtig:
> Es wird nicht nur gesagt, wie ein Problem gelöst wird, sondern auch begründet, warum dies gerade so gemacht wird.

## Design Patterns (Entwurfsmuster)
- Gute Entwürfe für wiederkehrende objektorientierte Modellierungsprobleme.
- Jeder gut Softwareentwickler kennt schon Entwurfsmuster - sie sind nur in den Systemen "versteckt". 
- Im objektorientierten Entwurf existieren für viele häufig wiederkehrende Detailanforderungen allgemeine Entwurfsmuster:
	- für Objektstrukturen (z.B. Singleton) → Erzeugermuster (*Creational Patterns*)
	- für Verhaltensweisen von Objekten (z.B. Iteration) → Verhaltensmuster (*Behavioral Patterns*)
	- für die Kooperation zwischen Objekten (z.B. Fassade, Adapter, MVC) → Strukturmuster (*Structural Patterns*)

### Template
##### Standard
| Mustername                          | Beschreibung                                                                                                                                                                                                                                                            |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kontext                             |                                                                                                                                                                                                                                                                         |
| Problem                             |                                                                                                                                                                                                                                                                         |
| Kräfte (*Forces*)                   | Was hat Einfluss auf die Wahl der Lösung? Wie hängen die Einflüsse voneinander ab?<br>Konflikt-Beispiel: "Nutzer will einfach Config" vs. "Nutzer will sichere Config"<br>Die Lösung muss eine Balance zwischen den Kräften herstellen.                                 |
| Lösung                              | Wie werden die Kräfte durch die Lösung aufgelöst? Warum gerade so?<br>Detaillierte Lösung, UML-Diagramme, Codebeispiele                                                                                                                                                 |
| Konsequenzen                        | Ausdrückliche Beschreibung, wie sich der Einsatz des Musters auf die Balance der Kräfte auswirkt.<br>Beispiel: "Das System wird ausfallsicherer, aber langsamer und weniger flexibel zu ändern"<br>Der Leser kann abwägen, ob das Muster für seine Zwecke geeignet ist. |
| Bekannte Anwendungen (*Known Uses*) | Faustregel:<br>Ein Muster ist kein Muster, wenn nicht mindestens 3 Anwendungen belegt sind.<br>Muster werden entdeckt, nicht erfunden.                                                                                                                                  |
| Verwandte Muster                    |                                                                                                                                                                                                                                                                         |

##### Nach GoF
| Mustername       | Beschreibung                                             |
| ---------------- | -------------------------------------------------------- |
| Intent           | Zweck des Musters: Was macht es?                         |
| Also Known As    |                                                          |
| Motivation       | Problem an einem Beispiel erklärt.                       |
| Applicability    | Kontext: Situationen, in denen das Muster nützlich ist.  |
| Structure        | Klassendiagramm                                          |
| Participants     | beteiligte Klassen und Objekte. Wer ist wofür zuständig? |
| Collaborations   | Wie arbeiten Klassen und Objekte zusammen?               |
| Consequences     | Vor- und Nachteile, Varianten                            |
| Implementation   | Techniken für die Implementierung, mögliche Fallen       |
| Sample Code      |                                                          |
| Known Uses       |                                                          |
| Related Patterns | Alternativlösungen, Kombinationen von Mustern                                                         |

### Null-Objekt (Muster)
- Definiert eine Klasse, die nichts zu tun hat. Die Verwendung dieser Klasse vermeidet `null`-Referenzen.
- Problem: 
	- Werden Methoden auf Objekten aufgerufen, die möglicherweise nicht existieren, gibt es üblicherweise Abfrage der Art `object != null`. 
	- Ein Vergessen des Tests kann zu Fehlern führen.
- Lösung: 
	- Man implementiert eine spezielle Null-Klasse, die dieselben Methoden wie die eigentliche Klasse hat. 
	- Diese Operationen sind entweder leer oder so implementiert, dass die fachlich nichts tun.
	- Immer, wenn eine `null`-Referenz auftauchen könnte, weist man eine Instanz dieser Null-Klasse zu.
	- Die Variable enthält somit immer ein gültiges Objekt.
	- Die Abfrage `object != null` entfällt

| Vorteile                                                                                                      | Nachteile                                                                              |
| ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| + `null`-Referenzen werden vermieden<br>+ Code wird lesbarer, da Abfragen auf mögliche `null`-Werte entfallen | - einiger Aufwand, wenn das Muster nachträglich in bestehende Programme eingefügt wird |

##### Diagramm
![](assets/NullObjectPattern.png)

### Observer (Entwurfsmuster "Beobachter")
- Bekannt aus JavaFX
	- GUI Elemente werden beobachtet
	- Callback-Funktionen reagieren auf Ereignisse (EventHandler)
	- Change-Listener reagieren auf Datenänderungen
- Man will **auf Zustandsänderungen eines Objektes reagieren**
- Idee: Ein Objekt, das an einer Zustandsänderung interessiert ist, registriert sich. Dieses Objekt ist dann Beobachter.
- Wenn sich der Zustand ändert, werden alle Beobachter benachrichtigt, indem eine (per Interface vorgegebene) Methode auf jedem Beobachter aufgerufen wird.

##### Snippet

```Java
public class Temperaturdaten {
	private float tempAussen;
	private float tempPool;
	private float[] tempZimmer; // pro Zimmer
	private HashSet<Beobachter> beobachterliste;
	
	float getTemperaturAussen() { ... }
	float getTemperaturPool() { ... }
	float getTemperaturZimmer(int zimmernr) { ... }
	
	public void beobachterHinzufuegen( Beobachter b ) {
		beobachterliste.add( b );
	}
	public void beobachterEntfernen( Beobachter b ) {
		beobachterliste.remove( b );
	}
	private void alleBeobachterInformieren() {
		for (Beobachter o: beobachterliste) {
			o.aktualisieren(this);
		}
}
```

##### Diagramm
![](assets/ObserverPattern.png)

### Model-View-Controller (Architekturmuster)
- Dieselben Daten werden auf verschiedene Weisen angezeigt → mehrere Views
- Dieselben Daten können auf verschiedene Weisen geändert werden → mehrere Controller
- Die Unterstützung mehrerer Views und Controller soll keinen Einfluss auf die Kernfunktionen der Anwendung (die im Model programmiert sind) haben.

	![](assets/MVC.png)

**Model:**
- stellt den aktuellen Zustand der Geschäftsdaten dar
- beantwortet Anfragen nach dem aktuellem Zustand
- informiert die Views über Zustandsänderungen
- stellt Methoden zur Verfügung, um den aktuellen Zustand zu ändern

**View:**
- stellt den Inhalt der Daten dar
- fragt das Model nach dem aktuellen Zustand bzw. kann sich als Observer für Zustandsänderungen beim Model registrieren
- sollte Model-Daten nur lesen, aber keine Änderungen vornehmen
- kann dem Controller Zugriff auf Methoden zur Darstellung erlauben

**Controller:**
- nimmt Eingaben des Benutzers und der Umgebung entgegen
- interpretiert diese Eingaben und wandelt sie in Methodenaufrufe an das Model (zur Änderung der Daten) oder an die View (zur Änderung der Darstellung) um.

**Zusammengefasst:**
- Das Modell ruft nie direkt Methoden auf View oder Controller auf → Einzige Ausnahme: Benachrichtigung des Observers)
- Also muss das Model keine Details von View oder Controller wissen.
- Das Model ist somit einfacher zu entwickeln und zu testen. 
- View bzw. Controller können bei konstantem Model ausgetauscht werden.

##### Snippet

```Java
public class Raumstatus {
	float Temperatur;
	bool heizt; // true -> Anlage heizt
	bool kuehlt; // true -> Anlage kühlt
} // (Konstruktor weggelassen)

public class Klimaanlage {
	private Raumstatus[] status; // pro Zimmer
	public static final ZIMMERZAHL = 400;
	public Klimaanlage{
		status = new Raumstatus[ZIMMERZAHL];
	}
	
	float getZimmertemperatur(int zimmernr) { ... }
	void heizen(int zimmernr) { ... }
	void kuehlen(int zimmernr) { ... }
	void aus(int zimmernr) { ... }
}
```

##### Diagramm
![](assets/MVCPattern.png)

### Strategy (Entwurfsmuster "Strategie")
- Welcher Algorithmus (von mehreren möglichen) genau verwendet wird, wird zur Laufzeit entschieden
- Über eine set-Methode kann die modellierte Eigenschaft später geändert werden → der Algorithmus ändert sich mit.
- Die Algorithmen sind in getrennten Klassen programmiert, Änderungen werden so leichter
- Grundidee:
	1. Identifiziere die teile der Anwendung, die sich ändern können.
	2. Trenne das, was konstant bleibt, von dem, was sich ändern kann. Dazu wird das, was sich ändert, in eigene Klasse gepackt.

##### Diagramm
![](assets/StrategyPattern2.png)
![](assets/StrategyPattern.png)

### State (Entwurfsmuster "Zustand")
- Nutzung: Immer, wenn sich eine Operation je nach Zustand eines Objektes anders auswirken soll
- Beispiel: Je nach Zustand soll sich eine Methode anders verhalten → Modellierung einer Klasse für den Zustand als Strategie-Klasse

| Vorteile                                         | Nachteile                     |
| ------------------------------------------------ | ----------------------------- |
| Neue Zustände lassen sich problemlos hinzufügen. | Zahl der Klassen erhöht sich. |

##### Snippet

```Java
private void drueckeKnopf3 {
	switch( zustand ) {
		case 2:
			Stunden++;
			break;
		case 4:
			Minuten++;
			break;
		…
	}
}
```

##### Diagramm
![](assets/StatePattern2.png)
![](assets/StatePattern.png)

### Decorator (Entwurfsmuster "Dekorierer")
- Einsatzzweck: Einer Klasse sollen zur Laufzeit weitere Zusätze/Verhaltensweisen in beliebiger Kombination hinzugefügt werden können.
- Ein Dekorierer erbt von derselben Klasse wie das Objekt, das er dekoriert.
- Vererbung sicher hier die Übereinstimmung der Typen.
- Ein Dekorierer hat eine Instanzvariable, in der das Objekt steht, das er dekoriert.

##### Snippet

```Java
// Aufruf
public class Eisladen {
	public static void main( String args[] ) {
		Eiswaffel e1 = new LeereEiswaffel( ... );
		Eiswaffel e2 = new SchokoEiskugel( e1 );
		Eiswaffel e3 = new SchokoStreusel( e2 );
		Eiswaffel e4 = new Schirmchen( e3 );
		...
		System.out.println( e4.druckeZusatzstoffe() );
	}
}

// Eiswaffel
public abstract class Eiswaffel {
	public abstract int berechnePreis();
	public abstract String druckeZusatzstoffe();
}

// leere Eiswaffel
public class LeereEiswaffel extends Eiswaffel {
	private final int PREIS_EISWAFFEL = ...;
	
	// Konstruktor
	public LeereEiswaffel ( ... ) { ... }
	
	int berechnePreis() {
		return PREIS_EISWAFFEL;
	}
	String druckeZusatzstoffe() {
		return "Zusatzstoffe der Eiswaffel...";
	}
}

// Dekorierer
public abstract class Dekorierer extends Eiswaffel {
	Eiswaffel dekoriertesObjekt;
	
	// Konstruktor
	public Dekorierer (Eiswaffel packMichEin) {
		this.dekoriertesObjekt = packMichEin;
	}
}

// spezifischer Dekorierer
public class Schirmchen extends Dekorierer {
	private final int PREIS_SCHIRMCHEN = ...;
	
	// Konstruktor
	public Schirmchen( ... ) { ... }
	
	int berechnePreis() {
		return dekoriertesObjekt.berechnePreis() + PREIS_SCHIRMCHEN;
	}
	String druckeZusatzstoffe() {
		StringBuilder sb = new StringBuilder();
		sb.append( dekoriertesObjekt.druckeZusatzstoffe() );
		sb.append( "Schirmchen bitte nicht mitessen..." );
		return sb.toString();
	}
}
```

##### Diagramm
![](assets/DecoratorPattern.png)

### Builder (Entwurfsmuster "Erbauer")
- trennt die schrittweise Konstruktion komplexer Objekte von deren Darstellung
- ermöglicht, mit demselben Erstellungsprozess unterschiedliche Repräsentationen zu erzeugen, und vermeidet überladene Konstruktoren.

##### Snippet

```Java
// unschöner Kontruktor
Kunde kunde1 = new Kunde( "Erna", "Wichtig", "Dr.", "Hallo", "Bahnhofstr. 1", "", "Mannheim", "Deutschland", true, false, false);

// verständlicher
Kunde kunde2 = new Kunde.KundeErbauer("Erna", "Wichtig").titel("Dr.").anrede("Hallo").adresse("Bahnhofstr. 1").adresszusatz("").ort("Mannheim"). istGeschaeftskunde(true).
istSelbstabholer(false).istWiederverkaeufer(false).erzeugePerson();

// noch besser, wenn nur relevante Parameter genutzt werden
Kunde kunde2 = new Kunde.KundeErbauer("Erna", "Wichtig").titel("Dr.").istGeschaeftskunde(true).erzeugePerson();
```

### Façade (Entwurfsmuster "Fassade")
- Um ein gewünschtes Ergebnis zu erzielen, müssen verschiedene Schnittstellen nacheinander angesprochen werden
- Verbirgt die Komplexität hinter einer einfachen, einheitlichen Schnittstelle
- Wenn sich **Schnittstellen der implementierenden Klassen ändern**, kann die **Fassade-Schnittstelle trotzdem konstant** gelassen werden, d.h. auch das rufende Programm bleibt konstant.
- Grundidee: (→ siehe Strategie)
	1. Identifiziere die Teile der Anwendung, die sich ändern können.
	2. Trenne das, was konstant bleibt, von dem, was sich ändert. Dazu wird das, was sich ändert, in eigene Klasse gepackt.

##### Snippet

```Java
// Aufruf
public class Buchungssystem {
	public static void main( String[] args ) { // anreise und abreise erfragen
		ReisebueroFassade f = new ReisebueroFassade();
		f.printReisevorschlag( anreise, abreise );
	}
}

// Fassade
public class ReisebueroFassade {
	private Hotelreservierung hr;
	private Flugbuchung fb;
	private Mietwagenreservierung mr;
	
	public void printReisevorschlag( Date from, Data to ) {
		System.out.println( hr.findHotels( anreise, abreise ) );
		System.out.println( fb.findFluege( anreise, abreise ) );
		System.out.println( mr.findMietwagen( anreise, abreise ) );
	}
}

// aufzurufende Methoden
public class HotelReservierung {
	public ArrayList<Hotel> findHotels(Date anreise, Date abreise) {
		// Hotels ausgeben
	}
}
public class FlugBuchung {
	public ArrayList<Flug> findFluege(Date anreise, Date abreise) {
		// Flüge ausgeben
	}
}
public class MietwagenBuchung {
	public ArrayList<Mietwagen> findMietwagen(Date anreise, Date abreise) {
		// Mietwagen ausgeben
	}
}
```

##### Diagramm
![](assets/FassadePattern2.png)
![](assets/FassadePattern.png)

### Proxy (Entwurfsmuster)
- Wir möchten einen Dienst nutzen
- Proxy (Stellvertreter) ...
	- kann diesen Dienst nutzen
	- kann möglicherweise darüber hinaus noch zusätzliche Dinge (Virenprüfung, Lastverteilung, Berechtigungsprüfung, Caching, Filtern unerwünschter Inhalte)
	- tut so, als wäre er der Dienst selbst
- Der Proxy kann somit auf dieselbe Weise aufgerufen werden wie der eigentliche Dienst

##### Beispiel
- Entwurfsvorgabe: Einsatz einer Klasse, deren Erzeugung oder Nutzung "teuer" (zeit- und ressourcenintensiv) ist
- Reiseportal → Abfrage von Tarifen und Verfügbarkeiten bei Flugbuchungen
- Zugriff auf Server der Fluggesellschaft nötig
	- Zeitaufwändiger als Zugriff in eigenem System
	- Möglichkeit administrativer Einschränkungen (Begrenzung Anfrage-Kontingent, Kosten pro Anfrage)
	- Verfügbarkeitsrisiko

##### Diagramm
![](assets/ProxyPattern.png)

### Caching Proxy
- Lösungsansatz:
	- soweit möglich ohne die "teuren" Daten auskommen und diese zwischenspeichern, um sie wiederverwenden zu können
- Proxy-Muster:
	- Anwendung arbeitet mit Proxy-Objekt, das genauso aussieht wie das "echte" Datenobjekt, aber intern nur bei Bedarf "teures" Objekt nutzt (neuer API-Call)

##### Diagramm
![](assets/CachingProxyPattern.png)

### Remote Proxy ("Entfernter Proxy")
- Wunsch: Verwendung der Methoden eines entfernten Objektes, als würde es sich um ein lokales Objekt handeln und das möglichst ohne zusätzlichen Code
- Aufrufende und gerufene Methode müssten sich kümmern um ...
	- Netzwerkverbindung
	- Serialisierung und Deserialisierung
	<br>
> [!NOTE] Merke:
> ==Serialisierung== wandelt den Zustand von Objekten in ein transportables Format (Byte-Strom, JSON, XML) um, um sie zu speichern oder zu übertragen.
> Die ==Deserialisierung== stellt das Objekt aus diesem Format wieder her. Dies ist essenziell für die Persistierung von Daten, Webservices und Remote Procedure Calls (RPC).
	<br>
	- Reaktion auf Netzwerkfehler
- Proxy-Objekte kümmern sich um die netzwerkspezifischen Dinge

##### Diagramm
![](assets/RemoteProxyPattern.png)

##### Standards für Kommunikation in OO-Systemen
- **Java RMI** (Remote Method Invocation) ist eine API zur Entwicklung verteilter Anwendungen, die es ermöglicht, Methoden von Objekten in einer anderen Java Virtual Machine (JVM), ggf. auf anderen Hosts, aufzurufen. RMI nutzt Stubs und Skeletons für die Kommunikation, oft über die RMI-Registry (Port 1099).
- **CORBA** (unabhängig von Programmiersprachen)
	- C = Common
	- ORB = Object Request Broker → hier versteckt sich Middleware → Vermittler von Objekten
	- A = Architekture
- **Windows Communication Foundation** (.NET-Welt)

##### Remote Method Invocation (RMI)
- Der Server stellt ein entferntes Objekt mit Methoden zur Verfügung
- Der Server meldet diese Objekt bei einem **Namendienst (Registry)** an. Dieser gibt dem angebotenen Objekt einen Namen.
- Der Client fragt den Namensdient nach einem entfernten Objekt und nutzt dieses.

##### Registry (Entwurfsmuster)
![Registry](assets/RegistryPattern.png)

##### Server
- Instanziiert Remote Objects und registriert sie in der RMI-Registry
	<br>
	```Java
	import java.rmi.AlreadyBoundException;
	import java.rmi.RemoteException;
	import java.rmi.registry.LocateRegistry;
	import java.rmi.registry.Registry;
	
	public class Server {
		public static void main( String args[] ) throws RemoteException, AlreadyBoundException {
			/*
			* Erzeugt eine auf Port 1099 lauschende RMI-Registry und 
			* registriert das Skeleton unter dem Namen "KlimaHotel"
			*/
			Registry reg = LocateRegistry.createRegistry( 1099 );
			reg.bind( "KlimaHotel", new EntfernteKlimaanlage() );
		}
	}
	```

##### Client
- verwendet die Funktionalität des Remote Objects
	<br>
	```Java
	import java.rmi.registry.LocateRegistry;
	import java.rmi.RemoteException;
	import java.rmi.NotBoundException;
	import java.rmi.registry.Registry;
	
	public class UeberwachungsClient {
		public static void main( String[] args ) throws RemoteException, NotBoundException {
		/**
		* Stellt Verbindung zur RMI-Registry her (man kann als Parameter den Host anegeben, auf dem die Registry läuft),
		* und ruft den Stub namens "KlimaHotel" ab, der das Remote Interface "KlimeanlageUeberwachen" implementiert
		*/
		Registry reg = LocateRegistry.getRegistry();
		KlimaanlageUeberwachen ferneKlimaanlage = ( KlimaanlageUeberwachen )
		reg.lookup( "KlimaHotel" );
		/**
		* Ruft die getStatus()-Methode des Stubs auf, die per RMI die getStatus()-Methode des Remote Objects aufruft
		*/
		System.out.println( ferneKlimaanlage.getStatus() );
		}
	}
	```

##### Parameterübergabe und Wertrückgabe
- Als Parameter / Rückgabewerte verwendete Klassen müssen ...
	- `java.io Serializable` implementieren
	- lokal und remote vorhanden sein

##### Gegenüberstellung Remote Proxy & Registry
| Eigenschaft | Remote Proxy                                                                                                  | Registry                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Funktion    | Lokaler Stellvertreter<br>Implementiert dieselbe Schnittstelle wie das echt entfernte Objekt                  | Fungiert als Telefonbuch<br>Ordnet einen Namen einem Remote Proxy zu                  |
| Aufgabe     | Nimmt Aufruf vom Client entgegen, serialisiert die Parameter und senden sie an den Server.                    | Registriert (bind/rebind) und sucht (lookup) entfernte Objekte                        |
| Interaktion | Der Client ruft Methoden auf dem Remote Proxy auf, welche diese transparent an das echte Objekt weiterleitet. | Der Client fragt die Registry nach einem Objekt und erhält einen Remote Proxy zurück. |
| Fazit       | Hilt beim Nutzen des Dienstes                                                                                 | Hilft beim Finden des Dienstes                                                                                      |

### Adapter
- Verbindet zwei Klassen mit **inkompatiblen Schnittstellen**
- Ziel: Ein CLient kann eine Klasse nutzen, obwohl deren API nicht passt
- Der Adapter **implementiert die erwartete Schnittstelle** und **delegiert** die Aufrufe intern an ein anderes Objekt

→ Schnittstellen übersetzen, ohne bestehende Klassen zu verändern

##### Struktur
- **Client** nutzt das `Target`-Interface
- **Adapter** implementiert Target
- **Adaptee** ist die bestehende Klasse mit unpassender API
- **Adapter enthält eine Referenz auf Adaptee** (Komposition)
- Adapter wandelt Aufrufe von `Target` in Aufrufe von Adaptee um

→ Komposition statt Mehrfachvererbung - ideal für Sprachen wie Java

##### Vorteile
- Bestehender Code bleibt unverändert
- Lose Kopplung: Client hängt nur von `Target` ab
- Mehr Flexibilität als Klassenadapter
- Funktioniert auch dann, wenn mehrere unterschiedliche Adaptee-Klassen unterstützt werden sollen

→ Objektadapter sind die häufigste Form des Adapter-Patterns in modernen OOP-Sprachen

##### Diagramm
![](assets/Adapter-Design-Pattern.webp)

## Proxy, Caching Proxy und Adapter

| Eigenschaft   | Proxy                                                                                                                         | Caching Proxy                                                                                                                                                                                                                                                    | Adapter                                                                                                                                |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Beschreibung  | **Gleiche Schnittstelle** wie das "echte" Objekt, aber dazwischen sitzt ein **Stellvertreter, der Zugriff/Verhalten steuert** | Spezialfall von Proxy: **Proxy + Cache**, um teure Aufrufe zu vermeiden.<br>Proxy, dessen Zusatzverhalten "Merken & Wiederverwenden" ist                                                                                                                         | **Macht zwei inkompatible Schnittstellen kompatibel.** Man passt die "Form des Steckers" an.<br>"Übersetzer" zwischen zwei Interfaces. |
| Zweck         | Zugriff kontrollieren oder Zusatzverhalten transparent einschieben                                                            | **Performance & Last reduzieren** (DB, HTTP, Compute)                                                                                                                                                                                                            | Integration von Komponenten mit **unterschiedlichen APIs**                                                                             |
| Mechanik      | -                                                                                                                             | Cache Key, TTL (time to live)/Invalidation,<br>ggf. Stale-While-Revalidate = HTTP-Caching-Strategie, die veraltete (stale) Inhalte aus dem Cache sofort anzeigt,<br>während im Hintergrund asynchron eine Aktualisierung (revalidate) vom Server abgerufen wird. | -                                                                                                                                      |
| Schnittstelle | Proxy und Real Subject implementieren **dieselbe API**                                                                        | -                                                                                                                                                                                                                                                                | Adapter **bietet die erwartete API** nach außen und **ruft intern die fremde API auf**                                                 |
| Fokus         | -                                                                                                                             | -                                                                                                                                                                                                                                                                | **Übersetzung** / Mapping von Methoden & Datenstrukturen, ggf. Semantik-Anpassung                                                      |
| Risiken       | -                                                                                                                             | Stale Date, Cache Invalidation, Konsistentfragen                                                                                                                                                                                                                 | -                                                                                                                                      |
| Beispiele     | Remote Proxy (Client stub), Access Control (Security Proxy), Lazy Loading (Virtual Proxy)                                     | HTTP Reverse Proxy (Nginx), clientseitiger Service, der GET Ergebnisse cached                                                                                                                                                                                    | Altes Legacy-API in neues Interface einpassen, Drittanbieter-Bibliothek unter eigener Domain-Schnittstelle kapseln                     |

##### Strukturmuster Spring
| Eigenschaft                     | Proxy                                                                                                                                                                                                                               | Caching Proxy                                                                                                                                                                                                 | Adapter                                                                                                                                                                |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wo wir er in Spring eingesetzt? | Innerhalb des SpringApplicationContext<br>Springerzeugt **stellvertretende Objekte (Proxies)** für Beans<br>Aufrufer spricht scheinbar mit der Bean, tatsächlich aber mit dem Proxy                                                 | Auf Service- oder Respository-Methoden<br>Innerhalb des Spring Cache Abstraction<br>Technisch: Ebenfalls ein Spring-Proxy mit Cache-Logik "dazwischen"                                                        | An den Grenzen des Systems<br>Typisch: Integration externer Systeme, Zugriff auf fremde APIs, Legacy-Systeme                                                           |
| Wofür wird er verwendet?        | **Querschnittsfunktionalität (cross-cutting concerns)**: Transaktionsmanagement, Security, Logging (→ Was ist AOP)<br>Der Proxy ruft vor/nach der eigentlichen Methode zusätzliche Logik auf<br>Er delegiert dann an die echte Bean | Performance<br>Reduzierung von Datenbankzugriffen, Remote-Calls, teuren Berechnungen<br>Der Proxy entscheidet: Cache Hit → Ergebnis direkt zurück, Cache Miss → echte Methode aufrufen und Ergebnis speichern | Unterschiedliche Schnittstellen, Datenmodelle und Semantik<br>Der Adapter bietet die eigene, erwartete Schnittstelle<br>Er übersetzt intern Daten, Fehler und Konzepte |
| Was ist typisch?                | Gleiche öffentliche Schnittstelle wie echte Bean<br>Transparenz für den Aufrufer<br> Fokus auf **Kontrolle, Überwachung, Erweiterung des Verhaltens**                                                                               | Fokus auf **Wiederverwendung von Ergenissen**<br>Zusätzliche Themen: Cache-Key, Invalidation, Konsistenz                                                                                                      | Nach außen: eigenes Domain-Interface<br>Nach innen: Nutzung einer fremden API<br>Fokus auf **Kompatibilität, Entkopplung, Austauschbarkeit**                                                                                                                                                                       |

→ Zusammenspiel:
- Adapter kapselt externe Systeme (REST)
- Spring legt um den Adapter einen Proxy für Security / Retry / Metrics
- Optional zusätzlicher Caching Proxy für häufige Lesenzugriffe

→ Typische Probleme
- Proxy: Selbst-Invocation (Selbstaufruf) umgeht den Proxy
- Caching-Proxy: Falsche Cache-Keys, veraltete Daten
- Adapter: Zu "dünn" (nur Durchreichen) oder zu "fett" (versteckte Fachlogik)

> [!NOTE] Merke:
> Proxy kontrolliert,
> Caching Proxy merkt sich,
> Adapter übersetzt.

## Java IO vs. Java NIO
- Input/Output ist zentraler Bestandteil vieler Anwendungen
- Klassisches `java.io` ist einfacher, aber blockierend
- `java.nio` wurde eingeführt, um leistungsfähigere, skalierbare IO-Prozesse zu ermöglichen
- Besonders relevant für Server, Netzwerkanwendungen und hohe Datenmengen

| Eigenschaft          | Java IO                                                                                                                                                                                         | Java NIO                                                                                                                                                                                                                                                                                                                                                                     |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Programmiermodell    | **Stream-basiert**<br>Daten fließen Byte für Byte oder Zeichen für Zeichen<br>**Blockierende IO**: Methoden warten, bis Daten verfügbar sind<br>1 Thread pro Verbindung<br>Einfach und intuitiv | **Buffer-basiert**<br>Arbeiten mit Blöcken (Buffers) statt einzelnen Bytes<br>**Nicht-blockierendes IO möglich (NIO-Selector-Modell)**<br>Ideal für parallele Verbindungen                                                                                                                                                                                                   |
| Komplexität          | **einfach**                                                                                                                                                                                     | **höher**                                                                                                                                                                                                                                                                                                                                                                    |
| Verhalten            | Thread wartet, bis eine Operation abgeschlossen ist<br>Jede Verbindung → eigen Thread typisch<br>Einfach, aber bei vielen Verbindungen ineffizient                                              | Lese-/Schreiboperationen kehren sofort zurück<br>Ein Thread kann mehrere Channels überwachen/verwalten<br>Skalierbarkeit für Server mit Tausenden Clients                                                                                                                                                                                                                    |
| Streams vs. Channels | Einseitig (InputStream, OutputStream)<br>Keine gemeinsame Ressource fürs Lesen & Schreiben<br>**pro Verbindung 1 Thread** → einfach, skaliert schlecht bei vielen Clients                       | Bidirektional (z.B. SocketChannel, FileChannel)<br>Effiziente Übertragung mittels `transferTo()`/`transferFrom()`<br>Direkter Speicherzugriff möglich (Direct Buffer)                                                                                                                                                                                                        |
| Buffer-Konzept       | -                                                                                                                                                                                               | Ein `ByteButter` repräsentiert einen Datenblock:<br>`capacity` - Gesamtkapazität<br>`position` - aktuelle Position<br>`limit` - Grenze des schreib-/lesbaren Bereichs<br>Operationen: `flip()`, `clear()`, `compact()`<br>→ ermöglicht feinere Kontrolle über die Datenverarbeitung                                                                                          |
| Charset & Encoding   | Typen wie `InputStreamReader`, `OutputStreamReader` konvertieren Zeichen ↔ Bytes<br>Hohe Abstraktion, aber weniger Kontrolle<br>**Performance okay**                                            | `CharsetEncoder` / `CharsetDecoder`<br>**Hohe Performance** & explizite Steuerung                                                                                                                                                                                                                                                                                            |
| Wann wählen?         | **Kleine Programme**<br>Skripte, Tools<br>Einfachheit ist wichtiger als Leistung<br>Wenige parallele Streams                                                                                    | Server mit vielen gleichzeitigen Verbindungen<br>File-Transfer mit hoher Performance<br>Netzwerkprotokolle<br>Zero-copy-Mechanismen (= optimieren Datenübertragungen durch Minimierung redundantes Kopieren von Daten zwischen Anwendung (User Space) und Betriebssystemkern (Kernel Space))<br>Echtzeitanwendungen<br>Ideal für Chat-Server, HTTP-Server, Protokoll-Engines |
| Patterns             | Paradebeispiel für Decorator<br>Gemeinsames Interface<br>Weiterleiten derselben Methode (`read`, `write`)<br>Dekorierbare Ketten                                                                | Verzichtet weitgehend auf Decorator<br>Unterschiedliche Typen mit unterschiedlichen Rollen<br>`Channel` liest → `Buffer` speichert → `Selector` überwacht→Komponenten werden **zusammengesetzt**, nicht dekoriert<br>Nutzt eher Adapter oder Reactor, nicht Decorator                                                                                                        |
| ==Fazit==            | ==intuitiv, für typische Anwendungen gut geeignet==<br>==Ideal für einfache, modulare, dekorierbare IO==                                                                                        | ==High-Performance-IO, skalierbar, aber komplexer==<br>==Ideal für skalierbare, nicht-blockierende Systeme==                                                                                                                                                                                                                                                                 |

> [!NOTE] Wichtig:
> NIO ersetzt IO nicht vollständig

### Decorator mit Java IO
- gemeinsame Oberklasse `InputStream` / `OutputStream`
- Erweiterung durch Filter-Dekoratoren
- Verhalten wird schichtweise hinzugefügt

##### Warum funktioniert das bei java.io so gut?
- IO-Streams haben eine **lineare Datenflussstruktur**
- Alle Streams teilen sich die gleiche Abstraktion
- Einfaches Weiterreichen von Methodenaufrufen: `read()`, `write()`, `close()`
- Modulare Erweiterbarkeit: Buffering, Datentyp-Konvertierung, Kompression, Verschlüsselung
- Perfekt geeignet für dekorative Schichten

##### Warum nutzt java.nio keinen Decorator?
- basiert auf völlig anderen Design
	- Channels (für IO)
	- Buffers (für Daten)
	- Selectors (für Events)
- Diese Komponenten haben **keine gemeinsame abstrakte Basisklasse**, auf die sich ein Decorator setzen könnte.
- Kein "Onion-Stack" wie in java.io

### Nachteile Java NIO
1. Nicht alle Anwendungsfälle profitieren von NIO
	- kleine Tool
	- Einfaches Datei-IO
	- Zeilenorientierte Textverarbeitung
	- Interaktives Konsolen-IO (Scanner, BufferedReader)
	- Für solche Aufgaben ist IO oft **einfacher , verständlicher und ausreichend.**
2. Java NIO ist komplexer
	- Buffer haben Position / Limit / Capacity
	- Selectors benötigen Event-basierte Logik
	- Fehleranfälliger für Anfänger
	- Overkill für triviale Anwendungen
	- NIO ist **mächtig, aber nicht immer praktisch**
3. Manche API-Bereiche weiterhin auf Java IO
	- `ObjectInputStream` / `ObjectOutputStream`
	- Viele ältere Bibliotheken und Frameworks
	- Manche High-Level-APIs setzen IO voraus
	- **IO bleibt ein unverzichtbarer Bestandteil des Java-Ökosystems**

## Streams als Anwendung des Decorator Patterns
- Modellierung des Dateisystems in Java mit Objekten der Klasse `java.io.File`
- `java.nio.file.Files` erlaubt weitere Dinge, z.B. Zugriff auf entfernte Dateisysteme

![](assets/Streams.png)

### Herausforderungen bei Dateiübertragung
- **verschiedene Datenformate**: Bytes oder Unicode-Zeichen
- viele **verschiedene Datenquellen und -senken**: Dateisystem, Datenstrukturen, Netzwerk, andere Threads
- viele **verschiedene Datentypen**: primitive Typen, Strings, Klassen (eigene oder von Java)
- viele **verschiedene Vor-/Nachverarbeitungsmöglichkeiten**: puffern, codieren, komprimieren...
<br>
- eigene Lösung dieser Herausforderungen wäre aufwendig, oft redundant und u.U. nicht plattformunabhängig

### Lösung: Datenströme
- Können Daten von einer Datenquelle empfangen und/oder Daten an eine Datenquelle senden

	![](assets/Streams2.png)

- Eine bestimmte Stream-Klasse weiß, wie ein bestimmtes Problem (Quellen-/Senkentyp, Datentyp, Verarbeitung) zu lösen ist.
- Entwickler muss sich nicht um Details kümmern, sondern ruft einfach Methoden wie "lesen" oder "schreiben" auf.

##### Grundlegende (abstrakter) Stream-Klassen
| Datenflussrichtung/Datenformat | Bytestreams    | Zeichenstreams (Unicode-Zeichen) |
| ------------------------------ | -------------- | -------------------------------- |
| Eingabestreams                 | `InputStream`  | `Reader`                         |
| Ausgabestreams                 | `OutputStream` | `Writer`                         |

##### Eingabestreams (abstrakt)
![](assets/EIngabeStreams.png)

##### Eigenschaften von Streams
- Streams sollten mit `close()` geschlossen werden. 
  Am besten: try-with-resources
- Lesen und Schreiben blockiert Ausführung (des Threads)
	- Methoden warten, bis etwas gelesen oder geschrieben wurde
	- Achtung: falls keine zu lesenden Daten vorliegen, steht read() !
	- `available()` blockiert nicht und kann zur Prüfung verwendet werden, um zu lesende Daten vorliegen

![](assets/UML.png)

- <span style="color:red">OutputStreams</span> etc. ist eine abstrakte Klasse
- Es ist z.B. noch nicht bekannt, was beim Aufruf von `close()` eigentlich zu tun ist (Datei schließen? netzwerk-Socket schließen?)

##### konkrete Streams
- Unterklassen zur Erfüllung bestimmter Aufgaben
	- Lesen/Schreiben aus/in Datenquellen/-senken
	- Umwandlung der Daten im Stream
	- Ein/-Auslesen verschiedener Java-Datentypen
- Oft müssen mehrere (aber nicht unbedingt alle) dieser Aufgaben gelöst werden

![](assets/Streams3.png)

##### Streams zum Medien Zugriff
![](assets/StreamsMedienZugriff.png)

![](assets/UML2.png)

- Bsp: <span style="color:red">FileOutputStream</span> ist eine konkrete Unterklasse der abstrakten Klasse OutputStream
- Hier ist nun z.B. implementiert, was `close()` tut (eine Datei schließen).

##### Verwendung Medien Streams
![](assets/VerwendungMedienStreams.png)

```Java  
import java.io.*;  

try( FileWriter fw = new FileWriter( "Datei.txt" ) ) {  
	fw.write( "Bitte speichere mich!" );  
} catch( IOException e ) {  
	System.err.println( "Konnte Datei nicht erstellen" );  
	e.printStackTrace();  
}
```

##### Streams zur Verknüpfung von Streams
![](assets/StreamsFürStreams.png)

##### Streams zur Verarbeitung von Daten
![](assets/StreamsFürDatenverarbeitung.png)

![](assets/UML3.png)

- <span style="color:red">FilterOutputStream</span> ist eine Klasse, von der verschiedene spezielle Filter (so heißen die Klassen zur Verarbeitung) erben

##### Streams zur Ein-/Ausgabe von primitiven Typen & Objekten
![](assets/StreamsPrimitiveTypen.png)

##### Verwendung von Datenstreams
![](assets/Datenstreams.png)

##### Motivation: Objektserialisierung
- Objekte existieren nur im Speicher, solange Programm läuft
- dauerhafte Speicherung / Datenaustausch erfordert Festlegung eines Formats.
- Textformat (toString) jedoch meist nicht geeignet
- besser: Speicherung / Austausch in wohldefiniertem Byte-Format
	- Struktur, Inhalte und verknüpfte Objekte vollständig rekonstruierbar
	- Speichern = Objekt-Serialisierung / Laden = Objekt-Deserialisierung
- Alternative: XML, JSON

###### Verwendung von Objektstreams
![](assets/Objektstreams.png)

###### Beispiel Objektserialisierung
- FileOutputStream kann Bytes in eine Datei schreiben
- ObjectOutputStream kann Objekte in Bytes wandeln

```Java
try(ObjectOutputStream oos = new ObjectOutputStream( new FileOutputStream( "objekte.ser" ) ); ) {
	oos.writeInt( 12345 );
	oos.writeObject( "Heute ist " );
	oos.writeObject( new Date() );
} catch( IOException e ) { ... }
```

![](assets/OutputStream.png)

- FileInputStream kann Bytes aus einer Datei lesen
- ObjectInputStream kann Bytes in Objekte wandeln

```Java
try( ObjectInputStream ois = new ObjectInputStream( new FileInputStream( "objekte.ser" ) ); ) {
	int i = ois.readInt();
	String s = ( String ) ois.readObject();
	Date d = ( Date ) ois.readObject();
}
catch ( IOException e ) { ... }
```

![](assets/InputStream.png)

###### Bedingungen Objektserialisierung
- Lesen muss in gleicher Reihenfolge wie Schreiben erfolgen.
- Klasse muss Interface Serializable implementieren.
- bei Übergabe an writeObject automatisch gespeichert:
	- Werte der nicht-statischen und nicht-transienten Attribute
	- referenzierte Objekte (rekursiv)
- alternativ ist (De-)Serialisierung selbst implementierbar (writeObject / readObject überschreiben)
- statische Variable serialVersionUID setzen!

######  System Ein- & ausgabe
- Klasse <span style="color:red">java.lang.System</span> hat folgende Attribute:
	- `public static final PrintStream out`
	• `public static final PrintStream err`
	• `public static final InputStream in`
- <span style="color:red">System</span>.out
	- mit Datensenke "Standardausgabe" (i.d.R. Bildschirm) verknüpft
	- PrintStream, dessen Methoden print() und println() für alle Datentypen überladen sind, um Zeichen-Ausgabe zu erzeugen
- <span style="color:red">System</span>.err
	- mit Senke "Standard-Fehlerausgabe" (i.d.R. Bildschirm) verknüpft
- <span style="color:red">System</span>.in
	- mit Datenquelle "Standardeingabe" (i.d.R. Tastatur) verknüpft
	- InputStream, aus dem durch geeignete Verknüpfung Eingaben eingelesen werden können

###### Beispiel: Lesen von Benutzereingaben
- InputStream System.in stellt Eingaben als Bytes bereit
- InputStreamReader kann Zeichen aus Byte-Strings lesen
- BufferedReader kann Zeichen zeilenweise lesen

```Java
try( BufferedReader eingabe = new BufferedReader( new InputStreamReader( System.in ) ); ) {
	String s = eingabe.readLine();
} catch( IOException e ) { 
	...
} catch( NumberFormatException e ) {
	...
}
```

![](assets/BspNutzereingabe.png)

###### Hack zum Testen von System.out.print;
```Java
private final ByteArrayOutputStream out = new ByteArrayOutputStream();

@BeforeEach
public void setUpStreams() {
	System.setOut(new PrintStream(out));
}

@Test
public void TestSysout() {
	System.out.print( "hello" );
	out.flush();
	assertEquals( "hello", out.toString() );
}
```

## Extensible Markup Language (XML)
- Format zur Verarbeitung strukturierter Daten in Dateien
- textuelle Darstellung (kein Binärformat)
- mögliches Serialisierungsformat

	![](assets/XML1.png)

### Eigenschaften
- Wohlgeformtheit (syntaktisch korrekt)
	- öffnende Tags (`<elem>`) müssen geschlossen werden (`</elem>`)
	- Ausnahme: Elemente ohne Inhalt (´<elem/>´)
	- Elemente müssen verschachtelt werden, ohne zu überlappen
- Validaität (gültig, grammatikalisch korrekt)
	- Document Type Definition (DTD) oder XML-Schema (XSD) legt „Grammatikregeln“ fest
	- Diese bestimmen, welche Elemente in welchen Kombinationen (Reihenfolge, Verschachtelung) ein XML-Dokument enthalten darf
	- Die DTD / das Schema kann am Beginn des Dokuments angegeben werden, um Programmen mitzuteilen, wie das Dokument aufgebaut sein sollte.
	- Wird keine DTD / kein Schema angegeben, so wird nicht auf Validität geprüft

### Document Type Defintion
- Die DTD wird in einem eigenen Dokument gespeichert.
- Um in einem XML-Dokument auf die DTD zu verweisen, wird ein DOCTYPE-Tag unmittelbar nach der XML-Deklaration gesetzt:
	<br>
	```XML
	<!DOCTYPE wurzelelement SYSTEM "quelle"	[optionale Definitionen]>
	```
	<br>
- Als Quelle kann der Dateiname oder die URL des DTD-Dokuments angegeben werden

![](assets/XML2.png)
![](assets/DTD.png)
![](assets/DTD2.png)

### XML Design
##### Attribute oder Elemente?
- Häufige Frage bei der Entwicklung von XML-Strukturen: 
  Modellierung von Daten als Element oder Attribut?

![](assets/XML3.png)

| Stilrichtlinien | Unter-Element                                                                                                                                                                                       | Attribut                                                                                                                                                 |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Modellierung    | Wenn die Daten weitere Elemente enthalten können ( `The <br>J2EE</b> Tutorial`)<br>Wenn die Daten mehrere Zeilen umfassen können<br>Wenn das Element mehrfach auftreten kann (z.B. mehrere Autoren) | Wenn die Daten kurze, einfache, selten veränderte String sind<br>Wenn die Daten aus einer begrenzten Wertemenge stammen (Überprüfung anhand DTD möglich) |
| Empfehlung      | Wenn die Daten fachlicher Natur sind, mit denen der Benutzer arbeitet<br>Wenn die Daten Inhalt des "Behältnis"-Elements sind                                                                        | Wenn die Daten technischer Natur sind, die nur das System braucht<br>Wenn die Daten Eigenschaften des "Behältnis"-Elements sind                                                                                                                                                         |

##### Entitäten definieren und verwenden
- In XML Dokumenten können Entitäten als "Textbausteine" verwendet werden (Format: `&entitätsname;`)
	- bekannte Entitäten in HTML

	| XML       | Klartext |
	| --------- | -------- |
	| `&lt;`    | `<`      |
	| `&gt;`    | `>`      |
	| `&amp;`   | `&`      |
	| `&quot;`  | `"`      |
	| `&apos;`  | `'`      |
	| `&auml;`  | `ä`      |
	| `&Auml;`  | `Ä`      |
	| `&szlig;` | `ß`      |

- Definition eigener Entitäten in der DTD mit `<!ENTITY name inhalt>`
- Beispiel:
	- Defintion in DTD: `<!ENTITY semester "WS 23/24">`
	- Verwendung im Dokument: `Vorlesung im &semester;`
	- Wird beim Einlesen zu: `Vorlesung im WS 23/24`
