# Prüfungsvorleistung 2

**Studierende:** Lisa Oschmann, Amer Abu Al Enen

## Thema: Datenbank (z. B. Key-Value-Store wie Redis)
- Ziel ist die Entwicklung eines Key-Value-Stores in C++. 
- Das System implementiert CRUD-Operationen (Create, Read, Update, Delete) zur Verwaltung von Schlüssel-Wert-Paaren im Arbeitsspeicher. 
- Eine strukturierte API in Form einer Database-Klasse kapselt den Datenzugriff und stellt alle CRUD-Operationen bereit. 
- Persistenz wird durch das Speichern und Laden der Daten in bzw. aus einer Datei gewährleistet. 
- Die Interaktion erfolgt über eine Konsolenanwendung. 
- Optional ist als Erweiterung (Ausbaustufe 2) eine Remote-API über TCP vorgesehen, die Clients den Zugriff auf die Datenbank über das Netzwerk ermöglicht.

## Erste Besprechung (27.04.26 mit Prof. Grimm)
1. Soll es Netzwerkfähig sein, sodass auch mehrere Maschinen darauf zugreifen können?
- Erstmal lokal mit CRUD Methoden und Persistenz
- Wenn Aufbaustufe 1 zu unterkomplex, dann Remote Zugriff über TCP ergänzen

2. Sollen wir TTL (time-to-live) einbauen?
- optional

3. Welche Datentypen sollen unterstützt werden? Nur Strings oder auch Listen?
- erstmal nur Strings abspeichern
- optionale Erweiterung: Unterstützung weiterer Datentypen (z.B. JSON)

4. Sollen wir eine UI bauen?
- Nein