---
sidebar_position: 3
---

# Datenschutz-Hilfsmittel

Im Rahmen der Open Government Data (OGD) Strategie der Stadt Winterthur ist die Einhaltung des Datenschutzes von zentraler Bedeutung. Die Veröffentlichung von Verwaltungsdaten soll die Transparenz, Partizipation und Innovation fördern, darf jedoch die Rechte und Freiheiten betroffener Personen nicht verletzen.

Dieses Hilfsmittel zeigt, wie mit schützenswerten Daten umgegangen wird und welche rechtlichen Prüfschritte sowie technischen Massnahmen vor einer Publikation als Open Government Data nötig sind. Es soll den Mitarbeitenden der Stadt Winterthur als Leitfaden dienen, wenn Datenschutzbedenken im Raum stehen und wie diese gelöst werden können. Dazu stehen Best-Practices zur Verfügung, wie der Datenschutz gewährt werden kann, ohne die Datenqualität unnötig zu tangieren.

Der nachfolgende Entscheidungsbaum dient den Mitarbeitenden der Stadtverwaltung als praktisches Instrument zur schnellen Beurteilung eines Datensatzes. Er führt systematisch durch die relevanten Fragen – von der gesetzlichen Grundlage über den Umgang mit Personendaten bis hin zur Klärung von Urheber- und Nutzungsrechten – und zeigt klar auf, wann eine OGD-Publikation möglich ist und welche Schritte dafür erforderlich sind.

```mermaid
---
config:
layout: elk
---
flowchart TD

  A["Besteht eine <b>gesetzliche Grundlage</b> für die Publikation?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/grundlagen'>→ Grundlagen</a>"]
  B["Enthält der Datensatz <b>Personendaten</b> oder lassen sich aus Sachverhalten Rückschlüsse auf Personen ziehen?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/personenbezug/personenbezug'>→ Personenbezug</a>"]
  C["Sind die Daten <b>urheberrechtlich</b> geschützt?"]
  D["Handelt es sich um <b>besonders schützenswerte Personendaten</b>?"]
  E["Erlaubt ein <b>formelles Gesetz</b> die Publikation dieser Daten?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/rechtsgrundlagen'>→ Rechtsgrundlagen</a>"]
  F["Sind <b>Vermeidungen des Personenbezugs</b> möglich, sodass <b>kein Personenbezug</b> mehr besteht?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/personenbezug/vermeidung'>→ Vermeidung des Personenbezugs</a>"]
  G["Wurden Rechte an die Stadt übertragen und <b>Persönlichkeitsrechte</b> gewahrt/verzichtet?"]
  H["Darf der Datensatz <b>kostenlos</b> bereitgestellt werden?"]
  I["Ist eine <b>kommerzielle</b> und <b>nicht-kommerzielle</b> Nutzung erlaubt?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/nutzungsbedingungen'>→ Nutzungsbedingungen</a>"]
  J["Ist die <b>Quellenangabe</b> obligatorisch?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/nutzungsbedingungen'>→ Nutzungsbedingungen</a>"]

  X1["Kein OGD. Gesetzliche Grundlage schaffen."]
  X2["Kein OGD. Alternative: <b>Vermeidung des Personenbezugs</b>."]
  X3["Kein OGD."]
  X4["Kein OGD, bis Rechte geklärt sind."]
  Y1["Kein OGD."]
  Y2["Kein OGD."]
  Z1["Publikation auf OGD. (Kein Pflicht-Hinweis zur Quellenangabe)"]
  Z2["Publikation auf OGD mit Hinweis: <b>Quellenangabe erforderlich</b>."]

  A -->|Ja| B
  A -->|Nein| X1
  B -->|Nein| C
  B -->|Ja| D
  D -->|Ja| E
  D -->|Nein| F
  E -->|Ja| C
  E -->|Nein| X2
  F -->|Ja| C
  F -->|Nein| X3
  C -->|Ja| G
  C -->|Nein| H
  G -->|Ja| H
  G -->|Nein| X4
  H -->|Ja| I
  H -->|Nein| Y1
  I -->|Ja| J
  I -->|Nein| Y2
  J -->|Ja| Z2
  J -->|Nein| Z1

  classDef ok fill:#e8f5e9,stroke:#2e7d32,color:#000;
  classDef stop fill:#ffebee,stroke:#8b0000,color:#000;
  classDef neutral fill:#ffffff,stroke:#000,color:#000;

  class A,B,C,D,E,F,G,H,I,J neutral;
  class X1,X2,X3,X4,Y1,Y2 stop;
  class Z1,Z2 ok;
```
:::info
Kann eine Frage nicht klar beantwortet werden, steht entweder die [Arbeitshilfe für Behörden zur Publikation von Daten als OGD] oder die [Datenschutzstelle der Stadt Winterthur] zur weiteren Klärung zur Verfügung.
:::
[Arbeitshilfe für Behörden zur Publikation von Daten als OGD]:https://www.bfs.admin.ch/bfs/de/home/dienstleistungen/ogd/dokumentation.assetdetail.11147071.html
[Datenschutzstelle der Stadt Winterthur]:https://stadt.winterthur.ch/gemeinde/behoerden-und-recht/datenschutz