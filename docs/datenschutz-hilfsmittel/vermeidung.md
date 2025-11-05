---
sidebar_position: 5
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Vermeidung des Personenbezugs

## De- Identifikation
**De-Identifikation** ist der Prozess, der dazu dient, zu verhindern, dass die **persönliche Identität einer Person offengelegt** wird, und sie gilt als einer der Hauptansätze zum Schutz der Datenprivatsphäre. Im Kern beinhaltet die De-Identifizierung von Daten das **Entfernen, Maskieren oder Ersetzen sensibler personenbezogener Daten (PII)** aus Datensätzen. Zu den gängigen Strategien gehört das **Löschen oder Maskieren direkter Kennungen** (wie Name, Adresse oder Geburtsdatum) sowie das **Unterdrücken oder Verallgemeinern von Quasi-Identifikatoren**. Dieser Prozess ist entscheidend, damit kantonale und städtische Verwaltungen Datenschutzbestimmungen einhalten können, wenn sie Daten für Analytik, Forschung oder Testzwecke veröffentlichen. De-identifizierte Daten ist ein Überbegriff, der sowohl **anonymisierte Daten** (bei denen die Re-Identifizierung unwiderruflich und ohne Schlüssel unmöglich ist) als auch **pseudonymisierte Daten** (bei denen die Re-Identifizierung prinzipiell durch eine vertrauenswürdige Stelle mithilfe eines separat gespeicherten Schlüssels möglich bleibt) umfasst. Der umgekehrte Vorgang der Identifizierung von Personen aus de-identifizierten Daten ist als Daten-Re-Identifizierung bekannt.

:::warning[Wichtig]
Die Pseudonymisierung der Daten ist kein ausreichender Schutz zur Vermeidung des Personenbezuges, da es sich bei pseudonymsiserten Daten noch immer um Personendaten handelt. Entsprechend können pseudonymisderte Daten nicht im OGD veröffentlicht werden.
:::

## Methoden zur Vermeidung des Personenbezugs

Die folgenden **vier Methoden** sollen die Mitarbeitenden dabei unterstützen, Datensätze so aufzubereiten, dass **keine Identifikation einzelner Personen möglich ist** und sie somit **als OGD veröffentlicht werden dürfen**.

Wähle die Methode entsprechend der Datenlage:

| Situation | Zweck | Geeignete Methode |
|---|---|---|
| Direkte Kennungen vorhanden (Name, Adresse, Kundennummer) | Entfernen persönlicher Identifikatoren | **1) Maskierung / Löschung** |
| Personenbezug soll dauerhaft ausgeschlossen werden | Endgültiges Entfernen des Bezuges | **2) Anonymisierung** |
| Präzise Werte erlauben Rückschluss auf Individuen | Genauigkeit kontrolliert reduzieren | **3) Generalisierung & Aggregation** |
| Mehrere Attribute ermöglichen Rückschluss in Kombination | Risiko messbar reduzieren | **4) K-Anonymität sicherstellen** |

---

:::info
[Guidance SPHN](https://sphn.ch/wp-content/uploads/2025/02/Data-de-identification-guidance-v2.0_20250214.pdf)
:::