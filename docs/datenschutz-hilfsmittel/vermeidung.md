---
sidebar_position: 4
---

# Vermeidung des Personenbezugs 

:::note
Die Vermeidung des Personenbezugs ist ein wichter Schritt in der datenschutzkonformen Veröffentlichung von Daten.
:::

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


<Tabs queryString="metadata">

<TabItem value="anonym" label="Anonymisierung">
**Anonymisierung** bedeutet, dass sämtliche Identifikationsmerkmale so entfernt oder verändert werden, dass keine Rückschlüsse mehr auf einzelne Personen möglich sind – auch nicht durch Kombination mit anderen Datenquellen.  
Nach einer wirksamen Anonymisierung gelten die Daten nicht mehr als Personendaten im Sinne des Datenschutzgesetzes. Typische Methoden sind Generalisierung (z. B. Altersklassen statt Geburtsdatum), Aggregation, Rauschen oder die Unterdrückung seltener Werte. Eine Re-Identifikation muss für vernünftige Dritte faktisch ausgeschlossen sein.
</TabItem>

<TabItem value="aggregation" label="Aggregation">
**Aggregation** fasst Einzelinformationen zu Gruppen, Räumen oder Zeitintervallen zusammen, um individuelle Merkmale zu verbergen.  
Beispiele sind statistische Auswertungen pro Stadtquartier, Altersgruppe oder Monat statt auf Personen- oder Tagesebene. Aggregation senkt das Risiko der Re-Identifikation erheblich und ist eine häufige Methode bei OGD-Publikationen, etwa in Statistik- oder Geodatenportalen.
</TabItem>

<TabItem value="de-int" label="De-Identifikation">
**De-Identifikation** ist der übergeordnete Begriff für alle Verfahren, die einen Personenbezug aus Datensätzen entfernen oder verschleiern.  
Sie umfasst sowohl Anonymisierung als auch Pseudonymisierung und beschreibt den Prozess der systematischen Entfernung direkter Identifikatoren (z. B. Namen, Adressen, AHV-Nummern) und indirekter Merkmale, die Rückschlüsse zulassen könnten. Ziel ist, dass der Datensatz keinen oder nur noch minimalen Bezug zu einer identifizierbaren Person aufweist.
</TabItem>

</Tabs>

:::tip
Weitere unterstützende Massnahmen zur Vermeidung des Personenbezugs sind das Einfügen von Zufallsrauschen (Differential Privacy), die Unterdrückung kleiner Fallzahlen (Zell-Suppression) sowie die räumliche oder zeitliche Generalisierung von Daten.  
Sie können je nach Datentyp mit den obigen vier Verfahren kombiniert werden.
:::
