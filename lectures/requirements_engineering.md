# Requirements Engineering
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

[!NOTE] Eine **Anforderung** ist gemäß IEEE:
> 1. Eine Bedingung oder Fähigkeit, die von einem Benutzer (Person oder System) zur Lösung eines Problems oder zur Erreichung eines Ziels benötigt wird.
> 2. Eine Bedingung oder Fähigkeit, die ein System oder Teilsystem erfüllen oder besitzen muss, um einen Vertrag, eine Norm, eine Spezifikation oder andere, formell vorgegebene Dokumente zu erfüllen.
> 3. Eine dokumentierte Repräsentation einer Bedingung oder Eigenschaft gemäß 1. oder 2.

[!NOTE] Stakeholder:
> Ein Stakeholder eines Systems ist eine Person oder Organisation, die **(direkt oder indirekt) Einfluss auf die Anforderungen des betrachteten Systems** hat.

[!NOTE] Requirements Engineering:
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

[!NOTE] Funktionale Anforderung:
> Ist eine Anforderung bezüglich eines Ergebnisses oder eines Verhaltens, das von einer Funktion eines Systems bereitgestellt werden soll.
> Verhaltens-, Struktur-, Funktionanforderungen

[!NOTE] Nicht-funktionale Anforderung
> ist ein Oberbegriff für Qualitätsanforderungen und Randbedingungen (Normen, juristische Anforderungen).
> Eine **Qualitätsanforderung** ist eine Anforderung, die sich auf ein Qualitätsmerkmal bezieht, das nicht durch funktionale Anforderungen abgedeckt wird. Sie legen die gewünschte Qualität fest und beeinflussen stark die Systemarchitektur. Normen (wie ISO) beschreiben, was Qualitätsmerkmale sind. 
> Eine **Randbedingung** ist eine Anforderung, die den Lösungsraum jenseits dessen einschränkt, was notwendig ist, um die funktionalen Anforderungen und die Qualitätsanforderungen zu erfüllen. Sie werden nicht umgesetzt und können nicht beeinflusst werden. Sie setzen die Umsetzungsmöglichkeiten ein. Sie können sich auf das betrachtete Sytem und/oder den Entwicklungsprozess beziehen.

## Foliensatz reqeng-le-2 (Bezug auf Praktikum 1)
### Systemkontext

[!NOTE] Systemkontext 
> Ist der Teil der Umgebung eines Systems, der für die Definition und das Verständnis der Anforderungen des betrachteten Systems relevant ist.
> Nicht relevante Anforderungen sollten dennoch dokumentiert sein, um später nachvollziehen zu können, dass diese abgewägt worden.

- Zweck des Systemkontextes (Einstiegsfragen bei Anforderungserhebung)
1. Was soll Teil des Sytems sein und was nicht?
2. Was hat einen direkten Bezug zum System?
- Aspekte im Systemkontext

### System- & Kontextgrenze

[!NOTE] Systemgrenze
> Sie separiert das geplante System von seiner Umgebung. Sie grenzt den im Rahmen des Entwicklungsprozesses gestaltbaren und veränderbaren Teil der Realität von Aspekten in der Umgebung ab, die durch den Entwicklungsprozess nicht verändert werden können.

[!NOTE] Kontextgrenze
> Sie separiert den relevanten Teil der Umgebung eines geplanten Systems vom irrelevanten Teil, d. h. dem Teil der Umgebung, der keinen Einfluss auf das geplante System und damit auch keinen Einfluss auf die Anforderungen dieses Systems hat.

- Grauzonen:
  - werden meist während der Entwicklung aufgedeckt
  - deren Zugehörigkeit muss noch geklärt werden

### Systemkontext dokumentieren
- Datenflussdiagramm
- Use-Case-Diagramm
- Klassendiagramm
