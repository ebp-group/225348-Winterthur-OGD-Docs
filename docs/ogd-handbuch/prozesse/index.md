---
sidebar_position: 3
---

# Übersicht der OGD-Prozesse

```mermaid
---
config:
  layout: elk
  look: neo
---
flowchart TB
 subgraph S["<b><span style=font-size:26px>OGD-Angebot</span></b>"]
    direction TB
        ucApp["Anwendungen"]
        ucDP["Datenportal"]
        ucMD["Metadata"]
        ucD["Daten"]
        ucQA["Fragen, Anfragen zu Daten"]
        ucFB["Fehlermeldungen, Feedback"]
  end
    ucDP -.-> ucMD
    ucMD -.-> ucD
    rN["👤 Daten-Nutzende"] -- nutzt --> ucDP
    ucDP ~~~ rF["👤 FS Daten"] & rF
    rN -- erstellt --> ucApp
    rN -- findet, sichtet --> ucMD
    rN -- sichtet, bezieht, nutzt --> ucD
    ucApp -- nutzt --> ucD
    rN -- meldet --> ucQA
    rN -- gibt --> ucFB
    rF -- verantwortet, betreibt --> ucDP
    rA["👤 OGD-Ansprechperson<br>Data Owner"] -- pflegt, stellt bereit --> ucMD
    rA -- bereitet auf, stellt bereit --> ucD
    rF -- berät, unterstützt --- rA

    ucD@{ shape: rect}
    classDef role stroke-width:1px,stroke:#000,fill:#fff,color:#000
    style ucApp fill:#ffffff,stroke:#000,color:#000
    style ucDP fill:#ffffff,stroke:#000,color:#000
    style ucMD fill:#ffffff,stroke:#000,color:#000
    style ucD fill:#ffffff,stroke:#000,color:#000
    style ucQA fill:#ffffff,stroke:#000,color:#000
    style ucFB fill:#ffffff,stroke:#000,color:#000
    style rN fill:#ffffff,stroke:#000,color:#000
    style rF fill:#ffffff,stroke:#000,color:#000
    style rA fill:#ffffff,stroke:#000,color:#000
    style S stroke:#000,fill:#fff,color:#000

```


Bei der Veröffentlichung von Daten als offene Verwaltungsdaten können die in 
der Abbildung skizzierten drei Hauptakteure (Daten-Nutzende, Data Owner und das 
FS Daten) und die folgenden fünf Hauptprozesse unterschieden 
werden:

1. [Produktion](/ogd-handbuch/prozesse/produktion)
2. [Bereitstellung](/ogd-handbuch/prozesse/bereitstellung)
1. [Publikation](/ogd-handbuch/prozesse/publikation)
1. [Anfragen](/ogd-handbuch/prozesse/anfragen)
1. [Support](/ogd-handbuch/prozesse/support)


Im Folgenden werden detaillierte Teilprozesse beschrieben, die zur Veröffentlichung offener Verwaltungsdaten nötig sind.
Auf den vorgelagerten Hauptprozess «Produktion» wird nicht weiter eingegangen, da dieser sehr spezifisch für jeden Datensatz ist.
Bei OGD handelt es sich immer um eine Sekundärnutzung von Daten, die bereits angefallen sind.
Eine separate Erhebung von Daten für OGD ist nicht vorgesehen.

