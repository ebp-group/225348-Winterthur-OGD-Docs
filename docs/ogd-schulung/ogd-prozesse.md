---
sidebar_position: 1
---

# Übersicht der OGD-Prozesse

```mermaid
flowchart LR
    do@{ label: "🗝️ Data Owner", shape: text}
    ogd@{ label: "🎯 Fachstelle OGD", shape: text}
    user@{ label: "🔧 Nutzende", shape: text}

    production["Produktion"]
    provide["Bereitstellung"]
    pub["Publikation"]
    portal@{ shape: paper-tape, label: "OGD-Portal"}
    usage["Datennutzung"]
    requests["Anfragen"]

    subgraph Erstellung
    production --> provide
    provide --> pub
    end

    subgraph "Zugang"
    pub --> portal
    end

    subgraph Nutzung
    portal --> usage
    end

    user -.-> usage
    user --> requests --> do
    requests --> ogd

    do -.-> production
    do -.-> provide
    do -.-> pub

    ogd-. unterstützt .->provide
    ogd-. unterstützt .->pub
    ogd-. unterstützt .->portal
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