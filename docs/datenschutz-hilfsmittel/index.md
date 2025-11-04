---
sidebar_position: 3
---

# Datenschutz-Hilfsmittel
:::info

Dieses Hilfsmittel zeigt, wie mit schützenswerten Daten umgegangen wird und welche technischen Massnahmen vor einer Publikation als Open Government Data nötig sind. 

:::
```mermaid
flowchart TD
  A["Besteht eine **gesetzliche Grundlage** für die Publikation?<br/><a href='#grundlagen'>[→ Grundlagen]</a>"] -->|Ja| B["Enthält der Datensatz **Personendaten** oder lassen sich aus Sachverhalten Rückschlüsse auf Personen ziehen?<br/><a href='#was-ist-personenbezug'>[→ Personenbezug]</a>"]
  A -->|Nein| X1["Kein OGD. Prüfen: gesetzliche Grundlage schaffen oder Datensatz so transformieren, dass **kein Personenbezug** mehr besteht."]

  B -->|Nein| C["Sind die Daten **urheberrechtlich** geschützt?<br/><a href='#urheberrecht-lizenzen'>[→ Urheberrecht/Lizenzen]</a>"]
  B -->|Ja| D["Handelt es sich um **besonders schützenswerte Personendaten**?<br/><a href='#besondere-kategorien'>[→ Besondere Kategorien]</a>"]

  D -->|Ja| E["Erlaubt ein **formelles Gesetz** die Publikation dieser Daten?<br/><a href='#rechtsgrundlagen'>[→ Rechtsgrundlagen]</a>"]
  D -->|Nein| F["Sind **Anonymisierung/Aggregation** möglich, sodass **kein Personenbezug** mehr besteht?<br/><a href='#anonymisierung'>[→ Anonymisierung]</a>"]

  E -->|Ja| C
  E -->|Nein| X2["Kein OGD. Alternative: **Anonymisieren/Pseudonymisieren**, interne Nutzung oder Zugriffssteuerung."]
  F -->|Ja| C
  F -->|Nein| X3["Kein OGD."]

  C -->|Ja| G["Wurden Rechte an die Stadt übertragen und **Persönlichkeitsrechte** gewahrt/verzichtet?<br/><a href='#urheberrecht-lizenzen'>[→ Urheberrecht/Lizenzen]</a>"]
  C -->|Nein| H["Darf der Datensatz **kostenlos** bereitgestellt werden?<br/><a href='#lizenzen-preise'>[→ Lizenzen/Preise]</a>"]

  G -->|Ja| H
  G -->|Nein| X4["Kein OGD, bis Rechte geklärt sind."]

  H -->|Ja| I["Ist **kommerzielle** und **nicht-kommerzielle** Nutzung erlaubt?<br/><a href='#lizenzauswahl'>[→ Lizenzwahl]</a>"]
  H -->|Nein| Y1["OGD möglich, aber mit **klaren Nutzungsbedingungen** (nicht-kommerziell).<br/><a href='#lizenzauswahl'>[→ Lizenzwahl]</a>"]

  I -->|Ja| J["Ist **Quellenangabe** obligatorisch?<br/><a href='#lizenzauswahl'>[→ Lizenzwahl]</a>"]
  I -->|Nein| Y2["OGD möglich, aber **Nutzungseinschränkungen** dokumentieren."]

  J -->|Ja| Z2["Publikation auf OGD mit Hinweis **Quellenangabe erforderlich**."]
  J -->|Nein| Z1["Publikation auf OGD möglich. Empfohlen: **offene Standardlizenz** (z. B. ODbL, CC BY)."]

  classDef ok fill:#0aa,stroke:#066,color:#fff;
  classDef warn fill:#fa0,stroke:#b60,color:#000;
  classDef stop fill:#888,stroke:#444,color:#fff;

  class Z1,Z2,Y1,Y2 ok;
  class X1,X2,X3,X4 stop;
```

Hier soll die Datensouveränität, Löschfristen und Datensicherheit, wie auch der Schutz angesprochen und State- of the Art Ansätze geliefert werden - dies wird in Anlehnung an den [OGD-Masterplan] der Schweiz.

[OGD-Masterplan]: https://data.europa.eu/sites/default/files/2025-06/2024_odm_factsheet_switzerland.pdf

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs queryString="metadata">
  <TabItem value="ansaetze" label="Ansätze">
    Dies sind Ansätze.
  </TabItem>
  <TabItem value="bestpractices" label="Best- practices">
    Dies sind best- practices.
  </TabItem>
</Tabs>

TODOs:

- [ ] Grundlagen erarbeiten
- [ ] Beispiel für Re-Identifikation zeigen (siehe z.B. https://spatialists.ch/posts/2025/07/01-differential-privacy-being-wrong-on-purpose/index.html, https://programming-dp.com/)
- [ ] Beispiel für Aggregation und andere Anonymisierungsmethoden zeigen
- [ ] Beispiel für Pseudonymisierung (z.B. Hunderegister Stadt Zürich, https://data.stadt-zuerich.ch/dataset/sid_stapo_aktueller_hundebestand_monat_od1003)
- [ ] Flowchart à la https://handbook.opendata.swiss/de/content/glossar/bibliothek/ogd-richtlinien.html, evtl. mit Absprungpunkten zu verschiedenen Unterkapiteln, Mermaid siehe https://mermaid.js.org/syntax/flowchart.html, oder https://github.com/ebp-group/225348-Winterthur-OGD-Docs/edit/main/docs/ogd-handbuch/prozesse/index.md





