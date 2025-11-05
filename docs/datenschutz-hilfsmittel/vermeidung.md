---
sidebar_position: 5
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Vermeidung des Personenbezugs

**De-Identifikation** ist der Prozess, der dazu dient, zu verhindern, dass die **persönliche Identität einer Person offengelegt** wird, und sie gilt als einer der Hauptansätze zum Schutz der Datenprivatsphäre. Im Kern beinhaltet die De-Identifizierung von Daten das **Entfernen, Maskieren oder Ersetzen sensibler personenbezogener Daten (PII)** aus Datensätzen. Zu den gängigen Strategien gehört das **Löschen oder Maskieren direkter Kennungen** (wie Name, Adresse oder Geburtsdatum) sowie das **Unterdrücken oder Verallgemeinern von Quasi-Identifikatoren**. Dieser Prozess ist entscheidend, damit kantonale und städtische Verwaltungen Datenschutzbestimmungen einhalten können, wenn sie Daten für Analytik, Forschung oder Testzwecke veröffentlichen. De-identifizierte Daten ist ein Überbegriff, der sowohl **anonymisierte Daten** (bei denen die Re-Identifizierung unwiderruflich und ohne Schlüssel unmöglich ist) als auch **pseudonymisierte Daten** (bei denen die Re-Identifizierung prinzipiell durch eine vertrauenswürdige Stelle mithilfe eines separat gespeicherten Schlüssels möglich bleibt) umfasst. Der umgekehrte Vorgang der Identifizierung von Personen aus de-identifizierten Daten ist als Daten-Re-Identifizierung bekannt.

:::warning[Wichtig]
**Die Pseudonymisierung** der Daten ist **kein ausreichender Schutz** zur Vermeidung des Personenbezuges, da es sich bei pseudonymsiserten Daten noch immer um Personendaten handelt. Entsprechend können pseudonymisierte Daten nicht im OGD veröffentlicht werden.
:::

## Methoden zur Vermeidung des Personenbezugs

Die folgenden **vier Methoden** sollen die Mitarbeitenden dabei unterstützen, Datensätze so aufzubereiten, dass **keine Identifikation einzelner Personen möglich ist** und sie somit **als OGD veröffentlicht werden dürfen**. Entschieden werden kann je nach Situation, wo eine entsprechende Methode am einfachsten oder vielversprechendsten ist:

| Situation | Zweck | Geeignete Methode |
|---|---|---|
| Direkte Kennungen vorhanden (Name, Adresse, Kundennummer) | Entfernen persönlicher Identifikatoren | **Maskierung / Löschung** |
| Personenbezug soll dauerhaft ausgeschlossen werden | Endgültiges Entfernen des Bezuges | **Anonymisierung** |
| Präzise Werte erlauben Rückschluss auf Individuen | Genauigkeit kontrolliert reduzieren | **Generalisierung & Aggregation** |
| Mehrere Attribute ermöglichen Rückschluss in Kombination | Risiko messbar reduzieren | **K-Anonymität sicherstellen** |

---

---
id: de-identifikation-methoden
title: Methoden der De-Identifikation
sidebar_label: Methoden zur Vermeidung des Personenbezugs
description: Praktischer Leitfaden zur Anwendung von De-Identifikations-Techniken vor OGD-Publikation
sidebar_position: 13
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Methoden zur Vermeidung des Personenbezugs

Die folgenden **vier Methoden** unterstützen Mitarbeitende dabei, Datensätze so aufzubereiten, dass **keine Identifikation einzelner Personen möglich ist** und sie somit **als OGD veröffentlicht werden dürfen**.

Wähle die Methode entsprechend der Datenlage:

| Situation | Zweck | Geeignete Methode |
|---|---|---|
| Direkte Kennungen vorhanden (Name, Adresse, Kundennummer) | Entfernen persönlicher Identifikatoren | **1) Maskierung / Löschung** |
| Personenbezug soll dauerhaft ausgeschlossen werden | Endgültiges Entfernen des Bezuges | **2) Anonymisierung** |
| Präzise Werte erlauben Rückschluss auf Individuen | Genauigkeit kontrolliert reduzieren | **3) Generalisierung & Aggregation** |
| Mehrere Attribute ermöglichen Rückschluss in Kombination | Risiko messbar reduzieren | **4) K-Anonymität sicherstellen** |

---

<Tabs>

<TabItem value="masking" label="1) Maskierung / Löschung">

### Ziel
**Direkte Kennungen entfernen oder unkenntlich machen**, damit die Person nicht mehr direkt identifiziert werden kann.

### Typische direkte Identifikatoren
- Name
- Adresse
- Telefonnummer / E-Mail
- Kundennummer / Fallnummer
- Kontonummer, Versicherungsnummer etc.

### Vorgehen (Schritt für Schritt)
| Feld | Aktion | Beispiel |
|---|---|---|
| Name | löschen | `Müller Anna` → *(entfernt)* |
| Kundennummer | durch neutralen Code ersetzen | `K12345` → `Fall_001` |
| Adresse | auf Quartier-Ebene reduzieren | `Zürcherstrasse 14` → `Quartier Altstadt` |
| E-Mail | entfernen | `anna.mueller@...` → *(entfernt)* |

### Wichtig
- **Maskierung ohne Mapping-Schlüssel → geeignet für OGD**
- **Maskierung mit Mapping-Schlüssel → Pseudonymisierung → *nicht* OGD-fähig**

</TabItem>

<TabItem value="anonymization" label="2) Anonymisierung">

### Ziel
Der Personenbezug wird **irreversibel** entfernt.  
Keine Stelle besitzt einen Schlüssel zur Wiederherstellung.

### Eigenschaften anonymisierter Daten
| Merkmal | Bedeutung |
|---|---|
| irreversibel | keine Rückführung auf eine Person möglich |
| ohne Schlüssel | kein Mapping vorhanden |
| nicht mehr Personendaten | damit **OGD-publizierbar** |

### Umsetzung (praktisches Vorgehen)
1. **Alle direkten Identifikatoren entfernen**  
2. **Alle Quasi-Identifikatoren prüfen** (Alter, Postleitzahl, Zeitpunkte, Arbeitsort, etc.)
3. Wenn Kombinationen zu eindeutig → **Generalisation / Aggregation anwenden** (siehe nächster Tab)

### Check
> **Kann eine einzelne Person immer noch erkannt werden?**  
→ Wenn ja: **noch keine Anonymisierung.**

</TabItem>

<TabItem value="generalization" label="3) Generalisierung & Aggregation">

### Ziel
Verhinderung von Rückschlüssen durch **Reduktion der Genauigkeit** oder **Zusammenfassung von Werten**.

### Beispiele

| Vorher (personenbeziehbar) | Nachher (geeignet für OGD) |
|---|---|
| Alter = 41 | Altersgruppe: 40–44 |
| Einkommen = 92'450 | Einkommensklasse: 90'000–100'000 |
| Adresse = Marktgasse 12 | Quartier: Altstadt |
| Unfall 03.05.2023 13:44 | Ereigniszeit: Mai / Nachmittag |

### Praktische Schwellenwerte (Empfehlungen)
- **n < 5** Fälle → **zusammenfassen oder entfernen**
- **Räume** nicht kleiner als:
  - Stadtteil / Quartier
  - Oder **Raster ≥ 100m** (je nach Dichte)

### Umsetzung in 2 Minuten

</TabItem>

<TabItem value="kanon" label="4) K-Anonymität (Sicherheit durch Gruppengrösse)">

### Ziel
Sicherstellen, dass **mindestens k Personen** die gleiche Kombination von Merkmalen besitzen.

### Was bedeutet „k“?
`k = 5` bedeutet:  
Jede Merkmalskombination muss **mindestens 5 Datensätze** umfassen.

### Beispiel
| Altersgruppe | Quartier | Fälle | OGD-Freigabe |
|---|---|---|---|
| 18–25 | Altstadt | 12 | ✅ OK |
| 75–80 | Altstadt | 2 | ❌ zusammenfassen oder entfernen |

### Umsetzungsschritte
1. Identifiziere **Quasi-Identifikatoren**  
   (Alter + Ort + Zeitraum + Ereignisform)
2. Bilden von Kategorien
3. Prüfen: *gibt es Kombinationen mit n < k ?*
4. Zusammenfassen / vergröbern, bis n ≥ k

### Ergebnis
→ Der Datensatz ist **robust gegenüber Re-Identifikation**.

</TabItem>

</Tabs>

---

## Vorher / Nachher Beispiele aus der Praxis

| Feld | Vorher | Nachher |
|---|---|---|
| Unfallzeitpunkt | 03.05.2023 13:44 | Zeitraum: Mai / Nachmittag |
| Adresse | Marktgasse 12 | Quartier Altstadt |
| Alter | 47 | 45–50 |
| Beschreibung | „Nachbarin Huber meldete Lärm“ | „Eine Person meldete den Vorfall“ |

---

## Schnell-Check (30 Sekunden)

- ☐ Direkte Kennungen entfernt?
- ☐ Kleine Gruppen (n < 5) zusammengefasst?
- ☐ Ort oder Zeit **nicht zu präzise**?
- ☐ Freitext auf Personenhinweise geprüft?
- ☐ **Keine Re-Identifikation** möglich?

→ Wenn überall **Ja** → Datensatz kann veröffentlicht werden.

---

## Möchtest du jetzt auch:

| Option | Ergebnis | Dauer |
|---|---|---|
| ✅ Ich möchte Beispiele aus echten Winterthurer Datensätzen | Wir erstellen 3 konkrete Vorher/Nachher-Transformationen | 10–20 Minuten |
| ✅ Ich möchte eine Vorlage zur Prüfung (Excel / PDF) | Wiederverwendbares Prüfschema für Fachstellen | 5 Minuten |
| ✅ Ich möchte einen internen OGD-Review-Workflow | Klarer Prozess von Stelle → OGD-Team → Veröffentlichung | 10 Minuten |

Sag einfach:  
**"Bitte Beispiele aus …: Verkehr / Bevölkerung / Soziales / Gemischt"**  
Oder: **"Bitte Checklisten-Template erstellen"**.



:::info
[Guidance SPHN](https://sphn.ch/wp-content/uploads/2025/02/Data-de-identification-guidance-v2.0_20250214.pdf)
:::