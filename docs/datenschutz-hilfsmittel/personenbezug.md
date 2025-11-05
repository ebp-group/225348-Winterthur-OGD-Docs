---
sidebar_position: 4
---

# Personenbezug
Vor jeder Veröffentlichung offener Verwaltungsdaten ist zu prüfen, **ob ein Personenbezug besteht**.  
Dieses Kapitel hilft, zu erkennen, wann Daten als personenbezogen gelten und welche Schritte dann folgen.

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

## Wann gilt ein Datensatz als anonym?

Ein Datensatz ist **anonymisiert**, wenn **keine Person auch mit vernünftigem Aufwand identifiziert werden kann**.  
Sobald eine Re-Identifikation technisch oder durch Zusatzwissen möglich wäre, gelten die Daten weiterhin als personenbezogen.

:::note
**Praxisregel:**  
Wenn eine Person mit allgemein zugänglichen Informationen oder durch Kombination mehrerer Merkmale erkennbar wäre, gilt der Datensatz als **personenbezogen**.
:::

## Vorgehen bei Personenbezug

Wenn der Datensatz (direkt oder indirekt) Personenbezug enthält, gilt folgendes Vorgehen:

1. **Gesetzliche Grundlage prüfen**  
   → Besteht eine explizite Rechtsgrundlage für die Veröffentlichung?  
2. **Schutzmassnahmen prüfen**  
   → Kann der Personenbezug durch Anonymisierung, Aggregation oder De-Identifikation beseitigt werden?  
3. **Wenn nein:**  
   → **Keine Veröffentlichung als OGD**  
4. **Wenn ja:**  
   → Veröffentlichung nach dokumentierten Schutzmassnahmen (vgl. [→ Vermeidung des Personenbezugs](./vermeidung)).

:::note[**Kurzcheck Personenbezug**]
1. Enthält der Datensatz Informationen über Einzelpersonen?  
2. Lassen sich durch Kombination Rückschlüsse auf Personen ziehen?  
3. Können die Daten ohne unzumutbaren Aufwand anonymisiert werden?

→ Nur **anonymisierte oder aggregierte Daten** dürfen als OGD veröffentlicht werden.
:::