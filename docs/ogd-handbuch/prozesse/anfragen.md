---
sidebar_position: 4
---

# Anfragen

## Anfragen zu Daten

Anfragen von Daten-Nutzenden lassen sich grob in zwei Kategorien einteilen:  
* Anfragen für die Publikation von neuen offenen Verwaltungsdaten 
* Verständnisfragen zu bereits veröffentlichten offenen Verwaltungsdaten 

 Das OGD-Kompetenzzentrum beantwortet Anfragen von Daten-Nutzenden möglichst selbst
 Falls dies nicht möglich ist, werden die Data Owner um ein Feedback gebeten und gegebenenfalls der Prozess zur Bereitstellung von neuen Daten angestossen. 

```mermaid
---
config:
  layout: elk
---
flowchart TB
    stAsk["Anfrage stellen"] ---> dInde["Kann das OGD-Kompetenzzentrum die Anfrage beantworten?"]
    dInde -- Ja --> stForm["Antwort auf Anfrage formulieren"]
    stForm ---> stAnswer["Rückmeldung an Daten-Nutzende"]
    dInde -- Nein --> dPub["Anfrage für Publikation von Daten?"]
    dPub -- Ja --> pAuswahl["Auswahl OGD-Kandidaten"]
    dPub -- Nein --> stFeedback["Feedback für Daten-Nutzende formulieren"]
    pAuswahl ---> stFeedback
    stFeedback ---> stAnswer
    stAsk@{ shape: rect}
    dInde@{ shape: decision}
    stForm@{ shape: rect}
    stAnswer@{ shape: rect}
    dPub@{ shape: decision}
    pAuswahl@{ shape: subproc}
    stFeedback@{ shape: rect}
      pAuswahl:::ok
      stForm:::ok
      dPub:::stop
      dInde:::neutral
      stFeedback:::neutral
      stAnswer:::neutral
      stAsk:::neutral
    classDef ok fill:#e8f5e9,stroke:#000,color:#000
    classDef stop fill:#ffebee,stroke:#000,color:#000
    classDef neutral fill:#ffffff,stroke:#000,color:#000

```

### Anfrage stellen

Anfragen können über sämtliche Kontaktmöglichkeiten zum OGD-Kompetenzzentrum gemeldet werden.
Gegenüber den Daten-Nutzenden tritt das OGD-Kompetenzzentrum als SPOC (<span class="nospell">_Single Point of Contact_</span>) auf und triagiert die Anfragen nach Zuständigkeit und Dringlichkeit.

### Antwort auf Anfrage formulieren 

Wenn möglich wird die Anfrage direkt vom OGD-Kompetenzzentrum beantwortet.

### Feedback für Daten-Nutzende formulieren

In einigen Fällen muss auf das Fachwissen oder die Entscheidungskompetenz der Data Owner zurückgegriffen werden, um eine Anfrage zu beantworten.
In diesem Fall leitet das OGD-Kompetenzzentrum die Anfrage weiter mit der Bitte um entsprechende Abklärungen und Feedback. 

### Rückmeldung an Daten-Nutzende

Daten-Nutzende sollen in jedem Fall eine Antwort auf Anfragen erhalten.
In der Regel wird die Antwort auf eine Anfrage vom OGD-Kompetenzzentrum an Daten-Nutzende weitergegeben.
Data Ownern steht es selbstverständlich frei, sich selbst direkt mit den Daten-Nutzenden auszutauschen. 

## Fehler melden 

Ein Spezialfall einer Anfrage ist die Meldung eines Fehlers.
Dabei stellen Daten-Nutzende fest, dass Daten oder Metadaten fehlerhaft, unplausibel, unvollständig oder unverständlich sind.
Solche Rückmeldungen sind essenziell, um die Qualität von offenen Verwaltungsdaten laufend zu verbessern.
Sie sollten, wenn möglich und sinnvoll berücksichtigt werden.

Das OGD-Kompetenzzentrum prüft in einem ersten Schritt, ob gemeldete Sachverhalte während des Publikationsprozesses entstanden sind.
Solche werden vom OGD-Kompetenzzentrum selbst behoben.
Andernfalls erfolgt eine Rückmeldung an den Data Owner, so dass eine Aktualisierung der Daten oder der Metadaten vorgenommen werden kann. 

```mermaid
---
config:
  layout: elk
  look: neo
---
flowchart TB
    stAsk["Fehler melden"] ---> stAnalyse["Fehler analysieren"]
    stAnalyse ---> dPub["Fehler im Publikationsprozess?"]
    dPub -- Ja --> stFix["Fehlerbehebung"]
    dPub -- Nein --> stAnalyse2["Fehler analysieren"]
    stFix ---> stAnswer["Rückmeldung an Daten-Nutzende"]
    stAnalyse2 ---> dUpdate["Aktualisierung der Daten/Metadaten nötig?"]
    dUpdate -- Ja --> pAkt["Datenaktualisierung"]
    dUpdate -- Nein --> stAnswer
    pAkt --> stAnswer

    stAsk@{ shape: rect}
    stAnalyse@{ shape: rect}
    dPub@{ shape: decision}
    stFix@{ shape: rect}
    stAnalyse2@{ shape: rect}
    stAnswer@{ shape: rect}
    dUpdate@{ shape: decision}
     stAsk:::neutral
     stAnalyse:::neutral
     dPub:::neutral
     stFix:::ok
     stAnalyse2:::stop
     stAnswer:::neutral
     dUpdate:::neutral
     pAkt:::ok
    classDef ok fill:#e8f5e9,stroke:#000,color:#000
    classDef stop fill:#ffebee,stroke:#000,color:#000
    classDef neutral fill:#ffffff,stroke:#000,color:#000

```

### Fehler melden

Fehler können über sämtliche Kontaktmöglichkeiten dem OGD-Kompetenzzentrum gemeldet werden. 

### Fehler analysieren

Gegenüber Daten-Nutzenden tritt das OGD-Kompetenzzentrum als SPOC (<span class="nospell">_Single Point of Contact_</span>)auf und triagiert Fehlermeldungen nach Zuständigkeit und Dringlichkeit.
Das OGD-Kompetenzzentrum versucht nachzuvollziehen, welcher Fehler in welchem Teilprozess vorgefallen ist. Falls der Fehler nicht im Publikationsprozess aufgetreten ist, müssen Fehlermeldungen an die zuständigen Data Owner delegiert und von diesen analysiert und gegebenenfalls behoben werden.

### Fehlerbehebung

Wenn Fehler während des Publikationsprozesses entstanden sind, können diese vom OGD-Kompetenzzentrum eigenständig behoben und korrigiert werden. 

### Rückmeldung an Daten-Nutzende

Daten-Nutzende sollen in jedem Fall eine Antwort auf ihre Fehlermeldungen erhalten. 
In der Regel wird die Antwort auf eine Fehlermeldung vom OGD-Kompetenzzentrum an die Daten-Nutzende weitergegeben.
Data Ownern steht es selbstverständlich frei, sich selbst direkt dazu mit den Daten-Nutzenden auszutauschen.
