---
sidebar_position: 3
---

# Datenschutz-Hilfsmittel

Im Rahmen der Open Government Data (OGD) Strategie der Stadt Winterthur ist die Einhaltung des Datenschutzes von zentraler Bedeutung. Die Veröffentlichung von Verwaltungsdaten soll die Transparenz, Partizipation und Innovation fördern, darf jedoch die Rechte und Freiheiten betroffener Personen nicht verletzen.

Dieses Hilfsmittel zeigt, wie mit schützenswerten Daten umgegangen wird und welche rechtlichen Prüfschritte sowie technischen Massnahmen vor einer Publikation als Open Government Data nötig sind. Es soll als Leitfaden dienen, wenn Datenschutzbedenken im Raum stehen und wie diese gelöst werden können. Dazu stehen Best-Practices zur Verfügung, wie der Datenschutz gewährt werden kann, ohne die Datenqualität unnötig zu tangieren.

Der nachfolgende Entscheidungsbaum dient den Mitarbeitenden der Stadtverwaltung als praktisches Instrument zur schnellen Beurteilung eines Datensatzes. Er führt systematisch durch die relevanten Fragen – von der gesetzlichen Grundlage über den Umgang mit Personendaten bis hin zur Klärung von Urheber- und Nutzungsrechten – und zeigt klar auf, wann eine OGD-Publikation möglich ist und welche Schritte dafür erforderlich sind.

```mermaid
---
config:
  layout: elk
---
flowchart TD
    A@{ label: "Besteht eine **gesetzliche Grundlage** für die Publikation?<br><a href=\"https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/grundlagen\">[→ Grundlagen]</a>" } -- Ja --> B@{ label: "Enthält der Datensatz **Personendaten** oder lassen sich aus Sachverhalten Rückschlüsse auf Personen ziehen?<br><a href=\"https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/personenbezug\">[→ Personenbezug]</a>" }
    A -- Nein --> X1["Kein OGD. Prüfen: gesetzliche Grundlage schaffen oder Datensatz so transformieren, dass **kein Personenbezug** mehr besteht."]
    B -- Nein --> C["Sind die Daten **urheberrechtlich** geschützt?"]
    B -- Ja --> D["Handelt es sich um **besonders schützenswerte Personendaten**?"]
    D -- Ja --> E@{ label: "Erlaubt ein **formelles Gesetz** die Publikation dieser Daten?<br><a href=\"https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/rechtsgrundlagen\">[→ Rechtsgrundlagen]</a>" }
    D -- Nein --> F@{ label: "Sind **Vermeidungen des Personenbezugs** möglich, sodass **kein Personenbezug** mehr besteht?<br><a href=\"https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/vermeidung\">[→ Vermeidung des Personenbezugs ]</a>" }
    E -- Ja --> C
    E -- Nein --> X2["Kein OGD. Alternative: **Vermeidung des Personenbezugs**."]
    F -- Ja --> C
    F -- Nein --> X3["Kein OGD."]
    C -- Ja --> G["Wurden Rechte an die Stadt übertragen und **Persönlichkeitsrechte** gewahrt/verzichtet?"]
    C -- Nein --> H["Darf der Datensatz **kostenlos** bereitgestellt werden?"]
    G -- Ja --> H
    G -- Nein --> X4["Kein OGD, bis Rechte geklärt sind."]
    H -- Ja --> I["Ist **kommerzielle** und **nicht-kommerzielle** Nutzung erlaubt?"]
    H -- Nein --> Y1["Kein OGD"]
    I -- Ja --> J["Ist **Quellenangabe** obligatorisch?"]
    I -- Nein --> Y2["Kein OGD."]
    J -- Ja --> Z2["Publikation auf OGD mit Hinweis **Quellenangabe erforderlich**."]
    J -- Nein --> Z1["Der Datensatz kann auf OGD publiziert werden, es muss auf der Plattform aber der Vermerk angebracht werde, dass die Quellenangabe obligatorisch ist."]
    A@{ shape: rect}
    B@{ shape: rect}
    E@{ shape: rect}
    F@{ shape: rect}
    G@{ shape: rect}
    I@{ shape: rect}
     A:::neutral
     B:::neutral
     X1:::stop
     C:::neutral
     D:::neutral
     E:::neutral
     F:::neutral
     X2:::stop
     X3:::stop
     G:::neutral
     H:::neutral
     X4:::stop
     I:::neutral
     Y1:::stop
     J:::neutral
     Y2:::stop
     Z2:::ok
     Z1:::ok
    classDef ok fill:#e8f5e9,stroke:#2e7d32,color:#000
    classDef warn fill:#ffffff,stroke:#9e9e9e,color:#000
    classDef stop fill:#ffebee,stroke:#8b0000,color:#000
    classDef neutral fill:#ffffff,stroke:#000,color:#000
```
:::info
Kann eine Frage nicht klar beantwortet werden, steht die [Arbeitshilfe für Behörden zur Publikation von Daten als OGD] zur weiteren Erläuterung zur Verfügung.
:::
[Arbeitshilfe für Behörden zur Publikation von Daten als OGD]: https://www.bfs.admin.ch/bfs/de/home/dienstleistungen/ogd/dokumentation.assetdetail.11147071.html