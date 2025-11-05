---
title: Rechtsgrundlagen
sidebar_position: 2
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Rechtsgrundlagen

Dieses Kapitel fasst die **verbindlichen Regeln** für die Veröffentlichung von Daten als Open Government Data (OGD) in Winterthur zusammen – **knapp**, **praxisnah** und **prüfbar**.

:::tip
**Kurz gesagt:** Offenheit ist der Standard (**Open by Default**), Datenschutz hat Vorrang.  
Nur **nicht-schützenswerte**, **strukturierte** Daten mit korrekten **Metadaten** dürfen als OGD publiziert werden.
:::

---

<Tabs defaultValue="ueberblick" values={[
  {label: 'Überblick', value: 'ueberblick'},
  {label: 'Ausschlussgründe', value: 'ausschluss'},
  {label: 'Zuständigkeiten', value: 'rollen'},
  {label: 'Nutzung & Lizenzen', value: 'lizenzen'}
]}>

<TabItem value="ueberblick">

## 1) Überblick – gesetzliche Basis

**Städtische Grundlage:** Open-Government-Data-Verordnung (OGD-V) der Stadt Winterthur (Entwurf 2025, Inkrafttreten 2026).  
Sie stützt sich auf:

- § 14 ff. **IDG ZH** (Informations- und Datenschutzgesetz):  
  <https://www.zh.ch/de/politik-staat/opendata/informations-und-datenschutzgesetz.html>
- **Gemeindeordnung Winterthur**, Art. 32:  
  <https://stadt.winterthur.ch/themen/stadt-und-politik/rechtliches/gemeindeordnung>
- **Informationsverordnung (InfV)**, Art. 2:  
  <https://stadt.winterthur.ch/themen/stadt-und-politik/rechtliches/informationsverordnung>

**Bundesrecht (ergänzend):**

- **Datenschutzgesetz (revDSG)**: <https://www.fedlex.admin.ch/eli/cc/2022/568/de>  
- **EMBAG** (Einsatz elektronischer Mittel): <https://www.fedlex.admin.ch/eli/cc/2023/176/de>

### Grundsätze (OGD-V)
- **Art. 1/2** Zweck & Geltungsbereich: Transparenz, Innovation, Partizipation; strukturiere Verwaltungsdaten.  
- **Art. 4** Open by Default: Publikation, sofern kein legitimer Ausschlussgrund besteht.  
- **Art. 5** Grenzen: Schutzgründe (Datenschutz, Urheber, Amtsgeheimnis etc.).  
- **Art. 7–12** Verfahren, Qualität, Metadaten, Aktualisierung.  
- **Art. 16** Nutzung & Lizenzen (kostenfrei, CC0 als Standard).  
- **Art. 17** Haftung.

</TabItem>

<TabItem value="ausschluss">

## 2) Ausschlussgründe & Schutzmassnahmen (Art. 5)

**Publikation ist ausgeschlossen**, wenn einer der Punkte zutrifft:

| Grund | Was heisst das? | Beispiel |
|---|---|---|
| **Personendaten** | Direkt oder indirekt identifizierbar | Einwohnermeldedaten, Zählerstände, Einzelfall-Sensorik |
| **Überwiegende Interessen** | Gefährdung von Verfahren, Sicherheit, Aufsicht | Sicherheitsinfrastruktur, laufende Untersuchungen |
| **Urheberrechte Dritter** | Keine Nutzungsrechte vorhanden | lizenziertes Karten-/Foto-Material |
| **Amts-/Vertragsgeheimnis** | Gesetzlich/vertraglich geschützt | interne Entscheidungsgrundlagen, vertrauliche Absprachen |

### Wenn ein Schutzbedarf besteht
- **Technische Massnahmen** (Art. 5 Abs. 2) ermöglichen OGD **nur**, wenn **kein Personenbezug mehr übrig bleibt**:
  - **Anonymisierung** (Entfernung/Generalisierung von Identifikatoren)  
  - **Aggregation** (Raum/Zeit/Gruppen)  
  - **Weglassen** sensibler Felder  
- **Pseudonymisierung** gilt als **personenbezogen** → **nicht** OGD-tauglich.

:::note
Praktische Anleitung: siehe [Vermeidung des Personenbezugs](./vermeidung) und [Personenbezug erkennen](./personenbezug).
:::

### Verhältnismässigkeit
Ist der Aufwand der Schutzmassnahmen **unverhältnismässig** und das öffentliche Interesse **gering**, kann auf Veröffentlichung verzichtet werden.

</TabItem>

<TabItem value="rollen">

## 3) Zuständigkeiten, Qualität, Metadaten (Art. 6–12)

| Rolle | Aufgaben |
|---|---|
| **Verwaltungsstellen/Ämter** | Identifizieren, prüfen, aufbereiten, klassifizieren (Art. 8–11); **Open by Design** beachten. |
| **OGD-Ansprechperson** | Koordination im Amt, Qualität & Metadaten, Schnittstelle zum Kompetenzzentrum. |
| **Kompetenzzentrum OGD** (Fachstelle Daten, ASE) | Beratung, Richtlinien/Standards, Gatekeeping vor Erstpublikation, Koordination Bund/Kanton (Art. 7). |

### Veröffentlichungsanforderungen
- **Strukturiert & maschinenlesbar** (z. B. CSV, JSON, GeoPackage).  
- **Metadaten nach DCAT-AP CH** (Beschreibung, Herkunft, Aktualität, Lizenz, Kontakt).  
- **Aktualisierung festlegen** (Art. 12): Rhythmus bei Erstpublikation definieren.  
- **Publikationsweg:** kantonales Datenportal → Spiegelung nach **opendata.swiss**.

:::tip
**Checkliste vor Freigabe**
1) Personenbezug ausgeschlossen?  
2) Schutzmassnahmen dokumentiert (k-Schwelle, Raster, Aggregation)?  
3) Metadaten vollständig (DCAT-AP CH)?  
4) Aktualisierungsrhythmus definiert?  
5) Lizenz korrekt (siehe Tab „Nutzung & Lizenzen“)?
:::

</TabItem>

<TabItem value="lizenzen">

## 4) Nutzung & Lizenzen (Art. 16)

### Grundsatz
- **Kostenfrei** zugänglich; **Bearbeitung, Weiterverbreitung und kommerzielle Nutzung** sind erlaubt.

### Standardlizenz
- **CC-Zero (CC0 / Public Domain)** – Standard in Winterthur.  
  Entspricht auf opendata.swiss **„Freie Nutzung“**.

### Zulässige Einschränkungen (Ausnahmen, mit Begründung & Genehmigung)
1) **Quellenangabe (CC-BY)** verpflichtend, und/oder  
2) **Bewilligung für kommerzielle Nutzung** erforderlich.

Beides muss in den **Metadaten** hinterlegt sein (Feld `license`) und erscheint auf **opendata.swiss** als Symbol.  
→ Details & visuelle Varianten im Kapitel **[Grundlagen → Nutzungsbedingungen](./grundlagen)**.

:::note
**Haftung (Art. 17):** Die Stadt haftet nicht für Schäden aus der Nutzung; Nutzende sind für Interpretation/Weiterverarbeitung verantwortlich.
:::

</TabItem>

</Tabs>

[revDSG]:https://www.fedlex.admin.ch/eli/cc/2022/568/de