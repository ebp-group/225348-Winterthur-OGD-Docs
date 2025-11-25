---
sidebar_position: 2
---

# Bereitstellung

## Auswahl OGD-Kandidaten

```mermaid
---
config:
  layout: elk
---
flowchart TB
    stKoord(["Koordination der Abklärungen initiieren"]) ---> stId(["Identifikation von Daten"])
    stId ---> stInfo(["Informationen zu Kriterien liefern"])
    stInfo ---> dR{"Rechtliche Abklärung nötig?"}
    dR -- Ja --> stRA(["Rechtliche Abklärung vornehmen"])
    dR -- Nein --> stPrio(["Selektion und Priorisierung der OGD-Kandidaten"])
    stRA ---> stPrio
    stPrio ---> pInit[["Initiale Datenaufbereitung"]]
```

### Koordination der Abklärungen initiieren

Die OGD-Ansprechpersonen identifizieren und nominieren die für die Abklärungen relevanten Personen (Fachpersonen, Stakeholder) beim Data Owner, informieren über das Vorhaben und vereinbaren frühzeitig Meilensteine.
Sie stellen eine Vorlage für die Datenübersicht zur Verfügung.
Diese beinhaltet Kriterien, welche für die Identifikation und Bewertung von OGD-Kandidaten relevant sind. 

:::info[Support durch OGD Kompezenzzentrum]
* Vorlage für die Datenübersicht mit Beurteilungskriterien
* Beratung zur Initiierungsphase
:::

### Identifikation von Daten

Die von der OGD-Ansprechperson involvierten Personen des Data Owners tragen vorhandene und geplante Datenbestände (Datensätze, Datensammlungen oder Datenbanken) des Data Owners in die zur Verfügung gestellte Vorlage ein. 
Datenbestände, die bereits als offene Verwaltungsdaten publiziert wurden, sollen hier ebenfalls eingetragen werden. 

:::info[Support durch OGD Kompezenzzentrum]
* Liste mit bereits publizierten offenen Verwaltungsdaten
:::

### Informationen zu Kriterien liefern

Nach der Identifikation der Datenbestände des Data Owners erfolgt deren Bewertung durch die Fachpersonen des Data Owners bezüglich Schutzbedürfnissen und Priorisierungskriterien.
Dabei werden folgende Fragen beantwortet: 

* **Schützbedürfnisse**: Besteht einer oder mehrere Schützbedürfnisse für die Daten (siehe auch Kapitel [«Nicht zu veröffentlichende Daten»](/ogd-handbuch/grundsaetze#nicht-veroeffentlichende-daten))
* **Priorisierungskriterien**
    * Wie hoch ist der Aufwand für die Abklärungen der Verwendbarkeit des Datenbestands für OGD? Ist mit weitergehenden, allenfalls komplexen  Abklärungen unter Einbezug weiterer Fachpersonen zu rechnen oder liegt eine relativ klare Ausgangslage vor?
    * Wie hoch ist der Aufwand für die Veröffentlichung des Datenbestands? 
    * Ist er aus einem System oder einer Datenbank extrahierbar? Um welchen Datentyp handelt es sich (Sachdaten, Geodaten, Echtzeitdaten, andere)? Existiert eine Programmierschnittstelle? 
    * Ist dokumentiertes Fachwissen zur Verwendung der Daten (Metadaten) vorhanden? 
    * Ist die Datenhoheit eindeutig? Besitzt der Data Owner das alleinige Nutzungsrecht? 
    * Werden die Datenbestände bereits – allenfalls in ähnlicher Form – andernorts veröffentlicht? Oder werden sie in ähnlicher Qualität bereits auf kantonaler oder nationaler Ebene publiziert?
    * Wie gilt es bezüglich Datenqualität zu beachten? 
    * Ist eine hohe Nachfrage vorhanden bzw. zu erwarten? Wie sind das öffentliche Interesse und die gesellschaftliche Relevanz einzustufen?

Die OGD-Ansprechperson trägt die Bewertungen in der Datenübersicht zusammen und ergänzt diese bei Bedarf. 

### Rechtliche Abklärung vornehmen

Sollte es Unsicherheiten geben bezüglich der rechtlichen Einschätzung eines Datenbestandes, so ist eine rechtliche Abklärung durch Fachjuristinnen bzw. Fachjuristen (Rechtsdienst) sinnvoll. 

Mögliche Fragestellungen: 
* Haben wir sämtliche Rechte an den Daten? 
* Welche rechtlichen Einschränkungen müssen beachtet werden? 
* Unterliegen die Daten Geheimhaltungspflichten oder sonstigen rechtlichen Beschränkungen? 
* Sind Einschränkungen bei Nutzungsbedingungen vorhanden? Ist beispielsweise eine Quellenangabe zwingend notwendig?
* Handelt es sich um Personendaten (Daten mit Personenbezug) bzw. lassen sich Rückschlüsse auf Personen oder Unternehmen daraus ableiten? 
* Müssen generell oder bei gewissen Ausprägungen technische Massnahmen (z.B. Anonymisierung) ergriffen werden, um den Datenschutz zu gewährleisten? 
* Wie stark müssen Daten aggregiert werden, um den Datenschutz zu gewährleisten?

Für Fragen rund um den Datenschutz sollte auch das [**Datenschutz-Hilfsmittel**](/datenschutz-hilfsmittel) konsultiert werden.

### Selektion und Priorisierung der OGD-Kandidaten

Basierend auf den gesammelten und konsolidierten Einschätzungen erarbeitet die OGD-Ansprechperson eine Selektion und eine Priorisierung: 
* **Selektion**: Unterteilung der Datensätze in OGD-Kandidaten (als offene Verwaltungsdaten zu veröffentlichen) und Nicht-OGD-Kandidaten (nicht als offene Verwaltungsdaten zu veröffentlichen), gemäss den Ergebnissen zu den Abklärungen zu Schutzbedürfnissen. 
* **Priorisierung**: Erstellen einer Abfolge – basierend auf den Einschätzungen zu den Priorisierungskriterien – in der OGD-Kandidaten als offene Verwaltungsdaten publiziert werden sollen. Daten, die mit wenig Aufwand veröffentlicht werden können und vergleichsweise hohe Relevanz für Daten-Nutzende haben, sollen prioritär veröffentlicht werden. 


## Initiale Datenaufbereitung

```mermaid
---
config:
  layout: elk
---
flowchart TB
    stInhalt(["Inhaltliche Datensatzdefinition"]) ---> stLi(["Lieferkanal definieren"])
    stLi ---> stAuf(["Aufbereitung der Daten als offene Verwaltungsdaten"])
    stAuf ---> stMeta(["Aufbereitung von Metadaten"])
    stMeta ---> stDQ(["Sicherstellen der Datenqualität"])
    stDQ ---> dDQ{"Datenqualität i.O.?"}
    dDQ -- Ja --> stDeploy(["Datenlieferung"])
    dDQ -- Nein --> stAuf
    stDeploy ---> pInit[["Qualitätssicherung und Freigabe"]]
    
```

### Inhaltliche Datensatzdefinition

Konkrete inhaltliche Bestimmung der Inhalte, des Umfangs und der Struktur des zu veröffentlichen Datensatzes, meist in Absprache mit dem OGD Kompetenzzentrum. 
Mögliche Fragestellungen sind:
* Welche Datenausprägungen (Attribute), Klassifizierungen, Zeiträume oder räumliche Ausprägungen sollen verwendet werden?

Im Grundsatz sollen offene Verwaltungsdaten so detailliert und so umfangreich wie möglich aber dennoch den Datenschutzvorschriften entsprechend veröffentlicht werden. 
Mögliche Auflagen und Einschränkungen aus den vorhergehenden Abklärungen sind zu berücksichtigen. 

### Lieferkanal definieren

Die Definition des Lieferkanals und des Ablageorts der Daten und der Metadaten erfolgt zwischen dem OGD Kompetenzzentrum und dem Data Owner unter der Leitung des OGD Kompetenzzentrum.
Lieferkanal und Ablageort können je nach Datentyp (siehe Beschreibung nachfolgende Aktivität) unterschiedlich sein.
Bei der Definition des Lieferkanals und Ablageorts soll bereits an die künftigen Datenaktualisierungen gedacht werden. 

### Aufbereitung der Daten als offene Verwaltungsdaten

Der Datenaufbereitungsprozess soll von Anfang an möglichst so gestaltet werden, 
dass er für künftige Datenaktualisierungen automatisiert ablaufen kann. 

Gemäss OGD-Veröffentlichungsprinzipien [^1] sollten die Daten bereits in maschinenlesbarer Struktur und wenn möglich in offenen Datenformaten geliefert werden. 
Je nach Datentyp sind die Aufbereitungsprozesse anders und unterschiedlich aufwändig: 

* **Geodaten**: Geodaten werden nach standardisiertem Prozess via die Geodateninfrastruktur zur Verfügung gestellt
* Programmierschnittstellen: Bei Vorhandensein einer  Programmierschnittstelle müssen keine Daten aufbereitet, sondern lediglich der Zugriff auf die Schnittstelle gewährleistet werden. 
* Sachdaten: Sachdaten entsprechen in der Regel maschinenlesbaren Listen. Durch ein professionelles Datenmanagement bei Data Ownern kann der Aufwand bei der Datenaufbereitung stark reduziert werden. Sofern die Sachdaten aus einem bestehenden System (Datenbank oder Data Warehouse, DWH) exportiert werden können, lässt sich der Datenaufbereitungsprozess einfach automatisieren.

:::info[Support durch OGD Kompezenzzentrum]
* Unterstützung beim Datenaufbereitungsprozess, insbesondere in der Automatisierung. 
:::

### Aufbereitung von Metadaten

### Sicherstellen der Datenqualität

### Datenlieferung


## Datenaktualisierung

## Qualitätssicherung und Freigabe

[^1]: Veröffentlichungsprinzipien: [Ten Principles for opening up Government Information (Sunlight Foundation)](https://sunlightfoundation.com/policy/documents/ten-open-data-principles/)