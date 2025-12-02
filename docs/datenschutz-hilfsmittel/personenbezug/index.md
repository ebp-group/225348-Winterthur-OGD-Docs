---
sidebar_position: 4
---

# Personenbezug
Vor jeder Veröffentlichung offener Verwaltungsdaten ist zu prüfen, **ob ein Personenbezug besteht**.  
Dieses Kapitel bietet einen **einfachen Einstieg**: Woran erkenne ich Personendaten – und wie bereite ich das **bereits ausgewählte Dataset** schnell und datenschutzkonform für OGD auf?

:::warning
Ein Datensatz gilt als **personenbezogen**, wenn er direkt oder indirekt einer natürlichen Person zugeordnet werden kann.
:::

## Was sind Personendaten?

Gemäss dem **Bundesgesetz über den Datenschutz (revDSG)** und dem **Gesetz über Information und Datenschutz (IDG ZH)** sind Personendaten:

> *Alle Angaben, die sich auf eine bestimmte oder bestimmbare natürliche Person beziehen.*

Eine Person gilt als **bestimmbar**, wenn sie direkt identifiziert werden kann oder sich durch Kombination mehrerer Merkmale identifizieren lässt.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs queryString="personenbezug">
<TabItem value="direkt" label="Direkter Personenbezug">
Direkter Personenbezug liegt vor, wenn eine Person unmittelbar erkannt werden kann.  
Typische Beispiele:
- Name, Adresse, Telefonnummer, E-Mail-Adresse  
- Personal- oder AHV-Nummer  
- Fahrzeugkennzeichen, Identifikationsnummern  
- Koordinaten eines einzelnen Grundstücks oder Gebäudes  
</TabItem>
<TabItem value="indirekt" label="Indirekter Personenbezug">
Indirekter Personenbezug entsteht, wenn aus scheinbar neutralen Informationen Rückschlüsse auf einzelne Personen möglich sind.  
Beispiele:
- Kombination von Alter, Beruf und Quartier  
- Einzelfälle in kleinen Gruppen (z. B. nur eine Ärztin in einem Dorf)  
- Sensor- oder Zähldaten, die Bewegungen einzelner Fahrzeuge oder Geräte zeigen  
- Datensätze mit seltenen Merkmalen („alle über 90-Jährigen im Stadtteil X“)  
</TabItem>
</Tabs>

## Normalfall: in 3 Schritten zur OGD-Freigabe

De-Identifikation bezeichnet alle Massnahmen, mit denen personenbezogene Informationen so verändert werden, dass keine Identifikation von Personen mehr möglich ist. Dazu gehören insbesondere das Entfernen direkter Kennungen (z. B. Name, Adresse) sowie das Generalisieren oder Unterdrücken von Quasi-Identifikatoren (z. B. Alter, Ort, Zeit).

Das Ziel ist sicherzustellen, dass Daten für Analyse, Forschung oder als Open Government Data genutzt werden können, ohne die Privatsphäre zu verletzen. De-identifizierte Daten können auch anonymisierte Daten umfassen, bei denen eine Re-Identifikation nicht mehr möglich ist.

:::warning[Wichtig]
**Die Pseudonymisierung** der Daten ist **kein ausreichender Schutz** zur Vermeidung des Personenbezugs, da es sich bei pseudonymsiserten Daten noch immer um Personendaten handelt. Entsprechend können pseudonymisierte Daten nicht im OGD veröffentlicht werden.
:::

1. **Direkte Kennungen löschen**  
   Namen, Adressen, E-Mails, Telefonnummern, IDs (AHV, Konto, Fallnummer) **entfernen oder maskieren**.
2. **Quasi-Identifikatoren generalisieren**  
   z. B. **Altersklassen** (5-Jahres-Bänder), **räumlich** (Quartier statt Adresse / Raster ≥ 100 m), **zeitlich** (Monat/Quartal statt exaktes Datum/Uhrzeit).
3. **Gruppenbildung sicherstellen (k-Anonymität)**  
   Jede veröffentlichte Kombination soll **mindestens k Fälle** enthalten (empfohlen **k ≥ 5**; für besonders schützenswerte Daten höhere Schwellen).

### Schnellverfahren (Orientierung)

| Situation | Zweck | Empfohlene Methode |
|---|---|---|
| Direkte Kennungen vorhanden (Name, Adresse, Kundennummer) | Entfernen persönlicher Identifikatoren | **Maskierung / Löschung** |
| Präzise Werte erlauben Rückschluss auf Individuen | Genauigkeit kontrolliert reduzieren | **Generalisierung & Aggregation** |
| Mehrere Attribute ermöglichen Rückschluss in Kombination | Risiko messbar reduzieren | **K-Anonymität sicherstellen** |

:::note
Wenn nach diesen Schritten **Re-Identifikationsrisiken** bestehen, ist das Dataset im aktuellen Zustand **nicht OGD-fähig**. Nutzen Sie die **Vertiefung** für weitere Massnahmen.
:::

## Checkliste Personenbezug

- ☐ Enthält der Datensatz direkte Kennungen?  
- ☐ Lassen Kombinationen indirekte Identifikation zu (kleine Gruppen, seltene Merkmale)?  
- ☐ Wurden Ort/Zeit **ausreichend aggregiert** und Gruppen mit **k ≥ 5** sichergestellt?  
- ☐ Sind Freitexte und Metadaten auf Personenhinweise geprüft?

→ Nur **anonymisierte oder ausreichend aggregierte** Daten dürfen als OGD veröffentlicht werden.
---
:::info[Weiterführende Vertiefung]
Für Methodik, Beispiele und detaillierte Umsetzung:  
**[→ Vermeidung des Personenbezugs (Vertiefung)](./personenbezug/vermeidung)**
:::