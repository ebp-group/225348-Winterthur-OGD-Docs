---
sidebar_position: 4
---

# Vermeidung des Personenbezugs 

Wenn bei einem Datensatz ein Personenbezug vorhanden ist und eine direkte Publikation nicht in Frage kommt, stehen Verfahren zur Verfügung, mit denen der Personenbezug zumindest soweit beseitigt oder reduziert werden kann, dass eine OGD-Publikation möglich wird (§ 5 Abs. 2 der Verordnung).  
Wichtig: Eine **Pseudonymisierung** bleibt grundsätzlich **personenbezogen** und fällt damit nicht unter „offene Verwaltungsdaten“, sofern nicht zusätzlich zur Pseudonymisierung weitere Massnahmen ergriffen werden.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs defaultValue="anonym" values={[
  { label: 'Anonymisierung',   value: 'anonym' },
  { label: 'Aggregation',      value: 'aggregation' },
  { label: 'De-Identifikation', value: 'deint' }
]}>

<TabItem value="anonym" label="Anonymisierung">
**Anonymisierung** bedeutet, dass sämtliche Identifikationsmerkmale so entfernt oder verändert werden, dass keine Rückschlüsse mehr auf einzelne Personen möglich sind – auch nicht durch Kombination mit anderen Datenquellen.  
Nach einer wirksamen Anonymisierung gelten die Daten nicht mehr als Personendaten im Sinne des Datenschutzgesetzes.  
**Beispiel (Schweiz):** Der Kanton Bern führt im Schulbereich eine Einführung in „Pseudonymisierung und Anonymisierung“ aus, wobei dort klar zwischen beiden Verfahren unterschieden wird. :contentReference[oaicite:0]{index=0}  
**Vorgehen:** Identifikatoren löschen oder ersetzen, Quasi-Identifikatoren generalisieren (z. B. Alter → Altersklasse), seltene Kombinationen suppressen, räumliche Auflösung verringern, ggf. Rauschen hinzufügen.  
**Hinweis:** Nur wenn Re-Identifikation für vernünftige Dritte faktisch ausgeschlossen ist, gelten die Daten als anonymisiert.
</TabItem>

<TabItem value="aggregation" label="Aggregation">
**Aggregation** fasst Einzelinformationen zu Gruppen, Räumen oder Zeitintervallen zusammen, um individuelle Merkmale zu verbergen.  
**Beispiel (Schweiz):** Der Kanton Zürich veröffentlicht offene Behördendaten nur, wenn sie «nicht schützenswert» sind – u. a. über die Aggregation von kleinen Gruppen. :contentReference[oaicite:1]{index=1}  
**Vorgehen:** Daten auf Gruppen- oder Gebietsebene veröffentlichen (z. B. Quartier statt Strasse, Monat statt Tag), kleine Fallzahlen < k suppressen oder mit Nachbarzellen kombinieren, Metadaten zur Aggregation dokumentieren.  
**Hinweis:** Aggregation reduziert das Risiko der Re-Identifikation stark, ist aber keine Garantie für vollständigen Schutz – Prüfung erforderlich.
</TabItem>

<TabItem value="deint" label="De-Identifikation">
**De-Identifikation** ist der Sammelbegriff für Verfahren, die darauf abzielen, alle direkt oder indirekt identifizierenden Merkmale systematisch zu entfernen oder zu verändern, sodass kein Personenbezug mehr besteht.  
**Beispiel (Schweiz):** Der „Data De-Identification: Phased Approach“ Report zeigt im Gesundheitsbereich in der Schweiz ein Vorgehen zur Risikobewertung und anschliessenden De-Identifikation. :contentReference[oaicite:2]{index=2}  
**Vorgehen:** Risikoanalyse durchführen → Identifikatoren & Quasi-Identifikatoren identifizieren → Kombinationen mit hohem Rückschlussrisiko gezielt behandeln → ggf. Anonymisierung/ Aggregation/ Rauschen anwenden → Dokumentation & Metadaten ergänzen.  
**Hinweis:** De-Identifikation umfasst häufig mehrere Methoden in Kombination – je nach Kontext.
</TabItem>

</Tabs>

:::tip
Weitere unterstützende Massnahmen zur Vermeidung des Personenbezugs sind das Hinzufügen von Zufallsrauschen (z. B. mittels **Differential Privacy**), das Unterdrücken kleiner Fallzahlen (Zell-Suppression) sowie die räumliche oder zeitliche Generalisierung von Daten.  
Diese Massnahmen können je nach Datentyp mit den obigen Verfahren kombiniert werden.
:::  
