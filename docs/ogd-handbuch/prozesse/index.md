---
sidebar_position: 3
---

# Übersicht der OGD-Prozesse

```mermaid
---
config:
  layout: dagre
---
flowchart TB
 subgraph S["OGD-Angebot"]
    direction TB
        ucApp(["Anwendungen"])
        ucDP(["Datenportal"])
        ucMD(["Metadata"])
        ucD(["Daten"])
        ucQA(["Fragen, Anfragen zu Daten"])
        ucFB(["Fehlermeldungen, Feedback"])
  end
    ucDP -.-> ucMD
    ucMD -.-> ucD
    rN["👤 Endnutzer"] ~~~ ucDP
    ucDP ~~~ rF["👤 FS Daten"] & rF
    rN -- erstellt --> ucApp
    rN -- findet, sichtet --> ucMD
    rN -- sichtet, bezieht, nutzt --> ucD
    rN -- stellt --> ucQA
    rN -- gibt --> ucFB
    rF -- verantwortet, betreibt --> ucDP
    rA["👤 OGD-Ansprechperson
  (Data Owner)"] -- pflegt, stellt bereit --> ucMD
    rA -- bereitet auf, stellt bereit --> ucD
    rF -- berät, unterstützt --- rA
     rN:::role
     rF:::role
     rA:::role
    classDef role stroke-width:0px

```


Bei der Veröffentlichung von Daten als offene Verwaltungsdaten können die in 
der Abbildung skizzierten drei Hauptakteure (Daten-Nutzende, Data Owner und das 
Fachstelle OGD) und die folgenden sechs Hauptprozesse unterschieden 
werden:

0. Produktion
0. Bereitstellung
0. Publikation
0. Anfragen
0. Support
0. Nutzung


Im Folgenden werden detaillierte Teilprozesse beschrieben, die zur Veröffentlichung offener Verwaltungsdaten nötig sind.

