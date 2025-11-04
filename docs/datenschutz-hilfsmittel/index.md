---
sidebar_position: 3
---

# Datenschutz-Hilfsmittel
:::info

Dieses Hilfsmittel zeigt, wie mit schützenswerten Daten umgegangen wird und welche technischen Massnahmen vor einer Publikation als Open Government Data nötig sind. 

:::
```mermaid
flowchart TD
  A["Besteht eine **gesetzliche Grundlage** für die Publikation?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/grundlagen'>[→ Grundlagen]</a>"] -->|Ja| B["Enthält der Datensatz **Personendaten** oder lassen sich aus Sachverhalten Rückschlüsse auf Personen ziehen?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/was-ist-personenbezug'>[→ Personenbezug]</a>"]
  A -->|Nein| X1["Kein OGD. Prüfen: gesetzliche Grundlage schaffen oder Datensatz so transformieren, dass **kein Personenbezug** mehr besteht."]

  B -->|Nein| C["Sind die Daten **urheberrechtlich** geschützt?"]
  B -->|Ja| D["Handelt es sich um **besonders schützenswerte Personendaten**?"]

  D -->|Ja| E["Erlaubt ein **formelles Gesetz** die Publikation dieser Daten?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/rechtsgrundlagen'>[→ Rechtsgrundlagen]</a>"]
  D -->|Nein| F["Sind **Vermeidungen des Personenbezugs** möglich, sodass **kein Personenbezug** mehr besteht?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/vermeidung'>[→ Vermeidung des Personenbezugs ]</a>"]

  E -->|Ja| C
  E -->|Nein| X2["Kein OGD. Alternative: **Vermeidung des Personenbezugs**, interne Nutzung oder Zugriffssteuerung."]
  F -->|Ja| C
  F -->|Nein| X3["Kein OGD."]

  C -->|Ja| G["Wurden Rechte an die Stadt übertragen und **Persönlichkeitsrechte** gewahrt/verzichtet?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/urheberrecht-lizenzen'>[→ Urheberrecht/Lizenzen]</a>"]
  C -->|Nein| H["Darf der Datensatz **kostenlos** bereitgestellt werden?"]

  G -->|Ja| H
  G -->|Nein| X4["Kein OGD, bis Rechte geklärt sind."]

  H -->|Ja| I["Ist **kommerzielle** und **nicht-kommerzielle** Nutzung erlaubt?<br/><a href='https://ebp-group.github.io/225348-Winterthur-OGD-Docs/datenschutz-hilfsmittel/lizenzauswahl'>[→ Lizenzwahl]</a>"]
  H -->|Nein| Y1["OGD möglich, aber mit **klaren Nutzungsbedingungen** (nicht-kommerziell)"]

  I -->|Ja| J["Ist **Quellenangabe** obligatorisch?"]
  I -->|Nein| Y2["OGD möglich, aber **Nutzungseinschränkungen** dokumentieren."]

  J -->|Ja| Z2["Publikation auf OGD mit Hinweis **Quellenangabe erforderlich**."]
  J -->|Nein| Z1["Publikation auf OGD möglich. Empfohlen: **offene Standardlizenz** (z. B. ODbL, CC BY)."]

  classDef ok fill:#e8f5e9,stroke:#2e7d32,color:#000;
  classDef warn fill:#ffffff,stroke:#9e9e9e,color:#000;
  classDef stop fill:#ffebee,stroke:#8b0000,color:#000;

  class Z1,Z2,Y1,Y2 ok;
  class X1,X2,X3,X4 stop;
```
Kann eine Frage nicht klar beantwortet werden, steht die [Arbeitshilfe für Behörden zur Publikation von Daten als OGD] zur weiteren Erläuterung zur Verfügung.

[Arbeitshilfe für Behörden zur Publikation von Daten als OGD]: https://www.bfs.admin.ch/bfs/de/home/dienstleistungen/ogd/dokumentation.assetdetail.11147071.html

## TODOs:

- [ ] Grundlagen erarbeiten
- [ ] Beispiel für Re-Identifikation zeigen (siehe z.B. https://spatialists.ch/posts/2025/07/01-differential-privacy-being-wrong-on-purpose/index.html, https://programming-dp.com/)
- [ ] Beispiel für Aggregation und andere Anonymisierungsmethoden zeigen
- [ ] Beispiel für Pseudonymisierung (z.B. Hunderegister Stadt Zürich, https://data.stadt-zuerich.ch/dataset/sid_stapo_aktueller_hundebestand_monat_od1003)
- [ ] Flowchart à la https://handbook.opendata.swiss/de/content/glossar/bibliothek/ogd-richtlinien.html, evtl. mit Absprungpunkten zu verschiedenen Unterkapiteln, Mermaid siehe https://mermaid.js.org/syntax/flowchart.html, oder https://github.com/ebp-group/225348-Winterthur-OGD-Docs/edit/main/docs/ogd-handbuch/prozesse/index.md







