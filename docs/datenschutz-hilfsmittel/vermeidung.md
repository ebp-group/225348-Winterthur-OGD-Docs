---
sidebar_position: 5
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Vermeidung des Personenbezugs

Dieses Kapitel zeigt, wie Datensätze so aufbereitet werden, dass **kein Personenbezug** mehr besteht.  
Gemäss **Art. 5 der OGD-Verordnung der Stadt Winterthur** gilt:  
**Pseudonymisierte Daten bleiben personenbezogen** und dürfen **nicht** als Open Government Data veröffentlicht werden.  
Eine Publikation ist nur zulässig, wenn der Personenbezug durch geeignete **technische Massnahmen vollständig beseitigt** wurde.

:::tip
**Zielbild:** *So offen wie möglich, so geschützt wie nötig.*  
Erst nach einer wirksamen **Anonymisierung**, **Aggregation** oder **De-Identifikation** gelten Daten als OGD-tauglich.  
Leitplanken liefern die [OGD-Richtlinien von opendata.swiss](https://handbook.opendata.swiss/de/content/glossar/bibliothek/ogd-richtlinien.html)
und der [Leitfaden OGD für Geodaten (SIK-GIS / BFS, PDF)](https://www.sik.ch/fileadmin/user_upload/Leitfaden_OGD_Geodaten.pdf).
:::

<Tabs defaultValue="anonym" values={[
  { label: 'Anonymisierung', value: 'anonym' },
  { label: 'Aggregation', value: 'aggregation' },
  { label: 'De-Identifikation (Prozess)', value: 'deint' },
]}>

<TabItem value="anonym" label="Anonymisierung">

## Anonymisierung

**Was:** Entfernt oder verändert alle identifizierenden Merkmale so, dass **keine Re-Identifikation** mehr möglich ist. Danach gelten die Daten **nicht** mehr als Personendaten.  

**Wann einsetzen:**  
- Wenn Einzeldatensätze (z. B. Meldungen, Messwerte, Zählungen) potenziell Rückschlüsse auf Personen erlauben.  
- Wenn sensible Attribute (z. B. Gesundheits-, Bewegungs- oder Standortdaten) veröffentlicht werden sollen.

**Vorgehen (Winterthur-spezifisch):**
1. **Identifikatoren identifizieren:** direkte (Name, Kennzeichen) & Quasi-Identifikatoren (Alter, Zeitpunkt, Koordinate).  
2. **Direkte Identifikatoren entfernen**, Quasi-IDs **generalisieren**:  
   - Alter → 5- oder 10-Jahresklassen  
   - Datum/Zeit → Woche oder Monat  
   - Adresse → Quartier oder 250-m-Raster  
3. **Seltene Kombinationen schützen:**  
   - Unterdrücke Gruppen mit *n < 5* (Primär-Suppression)  
   - ergänze Sekundär-Suppression, um Rückrechnung zu verhindern  
4. **Rauschen (Noise)**: kleine Zufallsabweichungen ± 1 auf Zählwerten oder Differential-Privacy-Ansatz mit dokumentiertem ε-Wert.  
5. **Räumliche Generalisierung:**  
   - Punkte auf **250–500 m-Raster** oder **statistische Quartiere** runden, keine Hausnummern.  
   - Geometrien vereinfachen (Douglas-Peucker > 20 m Toleranz).  
6. **Re-ID-Test:** Stichprobe – können Personen durch Kombination mit öffentlichen Quellen identifiziert werden? Falls ja → Schritte 2–5 nachschärfen.  
7. **Metadaten ergänzen:** beschreibe die angewandten Schutzmassnahmen, *k*-Schwelle, Rastergrösse und Rauschen.  

**Beispiel:**  
- *Stadt Zürich – „Zürich schaut hin“*: Meldedaten werden vollständig **anonymisiert** veröffentlicht, ohne persönliche Angaben.  
  👉 [data.stadt-zuerich.ch/dataset/sid_zuerich_schaut_hin](https://data.stadt-zuerich.ch/dataset/sid_zuerich_schaut_hin)

**Hilfsmittel & Referenzen:**  
- [OGD-Richtlinien opendata.swiss](https://handbook.opendata.swiss/de/content/glossar/bibliothek/ogd-richtlinien.html)  
- [SIK-GIS/BFS Leitfaden OGD für Geodaten (PDF)](https://www.sik.ch/fileadmin/user_upload/Leitfaden_OGD_Geodaten.pdf)  
- [EDÖB – Technische und organisatorische Massnahmen (TOM)](https://www.edoeb.admin.ch/edoeb/de/home/datenschutz/gesetzgebung/technical-and-organisational-measures.html)

</TabItem>

<TabItem value="aggregation" label="Aggregation">

## Aggregation

**Was:** Zusammenfassen von Einzelwerten zu **Gruppen, Räumen oder Zeitintervallen**, um individuelle Muster zu verbergen.

**Wann einsetzen:**  
- Bei städtischen Mess-, Nutzungs- oder Zähldaten (Verkehr, Umwelt, Energie, Meldesysteme).  
- Wenn Einzelfälle oder kleine Gruppen Rückschlüsse auf Personen erlauben würden.

**Vorgehen (Winterthur-spezifisch):**
1. **Aggregations­ebenen wählen:**  
   - Räumlich: **Quartiere**, **statistische Zonen** oder **250 m-Raster**.  
   - Zeitlich: **Woche**, **Monat** oder **Quartal** statt einzelne Tage.  
2. **Schwellwert anwenden:**  
   - Keine Veröffentlichung von Gruppen mit *n < 5*.  
   - Zusammenlegung benachbarter Zellen oder Zeiträume.  
3. **Kennzahlen verwenden:** Mittel-, Median-, Quantil- oder Prozentwerte; Top/Bottom-Coding (z. B. „≥ 90 Jahre“).  
4. **Kategorien bündeln:** seltene Ausprägungen zu „Andere“ oder „übrige Kategorien“ zusammenfassen.  
5. **Metadaten ergänzen:** Aggregationslogik, Zeitbezug, Zellgrösse und aktualisierte Frequenz dokumentieren.  

**Beispiel:**  
- *Open Data Zürich (Kanton Zürich)*: Bevölkerung, Verkehr und Sozialdaten werden **aggregiert** nach Gemeinde, Quartier oder Monat veröffentlicht.  
  👉 [zh.ch – Leitlinien Open Data](https://www.zh.ch/de/politik-staat/opendata/leitlinien.html)  
  👉 [data.stadt-zuerich.ch](https://data.stadt-zuerich.ch)

**Hilfsmittel & Referenzen:**  
- [Leitlinien „Offene Daten publizieren“ – Kanton Zürich](https://www.zh.ch/de/politik-staat/opendata/leitlinien.html)  
- [SIK-GIS/BFS Leitfaden OGD für Geodaten (PDF)](https://www.sik.ch/fileadmin/user_upload/Leitfaden_OGD_Geodaten.pdf)

</TabItem>

<TabItem value="deint" label="De-Identifikation (Prozess)">

## De-Identifikation (Prozess)

**Was:** Ein strukturierter Prozess, um den Personenbezug durch Kombination mehrerer Massnahmen (Anonymisierung, Aggregation, Suppression, Rauschen) zu **eliminieren**.  

**Wann einsetzen:**  
- Bei komplexen Datensätzen mit mehreren Quasi-Identifikatoren (z. B. Verkehr, Energie, Sensorik, Verwaltungsregister).  
- Wenn einfache Anonymisierung nicht genügt.

**Vorgehen (Winterthur-spezifisch):**
1. **Zweck & Rechtsgrundlage** gemäss OGD-Verordnung festhalten.  
2. **Variablenklassierung:** direkt identifizierend / quasi-identifizierend / sensitiv / frei.  
3. **Risikobewertung:** Wahrscheinlichkeit der Re-Identifikation (z. B. *k* ≥ 5 Personen pro Gruppe).  
4. **Massnahmen umsetzen:**  
   - Generalisierung: z. B. Quartier statt Adresse.  
   - Aggregation: Monatswerte statt Tageswerte.  
   - Suppression: Zellen mit *n < 5* entfernen + Sekundär-Suppression.  
   - Rauschen: ± 1 auf Counts oder DP-Noise.  
5. **Iterative Prüfung:** Re-ID-Test; falls Risiko > Schwelle, Massnahmen nachschärfen.  
6. **Dokumentation:** Methode, Parameter und Risikobewertung im internen Publikationsdossier hinterlegen; Hinweis in Metadaten.  
7. **Freigabeprozess:** Dateneigner → Kompetenzzentrum OGD → Veröffentlichung im Portal → Monitoring durch Kompetenzzentrum.  

**Beispiel:**  
- *Swiss Personalized Health Network (SPHN)*: „Data De-Identification – Phased Approach“ (2022) zeigt den Schweizer Best Practice-Prozess zur stufenweisen De-Identifikation – von der Risikoanalyse bis zur Publikation.  
  👉 [SPHN – Data de-identification (PDF)](https://sphn.ch/wp-content/uploads/2022/05/Data-de-identification-Phased-approach-v1.0.pdf)

**Hilfsmittel & Referenzen:**  
- [SPHN – Data de-identification (PDF)](https://sphn.ch/wp-content/uploads/2022/05/Data-de-identification-Phased-approach-v1.0.pdf)  
- [EDÖB – Technische und organisatorische Massnahmen (TOM)](https://www.edoeb.admin.ch/edoeb/de/home/datenschutz/gesetzgebung/technical-and-organisational-measures.html)  
- [SIK-GIS/BFS Leitfaden OGD für Geodaten (PDF)](https://www.sik.ch/fileadmin/user_upload/Leitfaden_OGD_Geodaten.pdf)

</TabItem>

</Tabs>

---

## Winterthur-Checkliste (Schnellhilfe)

1. **Personenbezug prüfen** → Wenn ja, Art. 5 anwenden und eine Vermeidungsstrategie wählen.  
2. **Städtische Ebenen** verwenden: Quartiere, statistische Zonen, 250/500 m-Raster, Monatswerte.  
3. **Schwelle *n < 5***: Zellen suppressen oder zusammenlegen.  
4. **Rauschen**: ± 1 auf Counts; Differential Privacy nur bei sensiblen Zählwerten.  
5. **Metadaten vollständig**: Angaben zu Aggregation, Raster, k-Wert, Rauschen, Update-Rhythmus, Lizenz.  
6. **Gatekeeping:** Vor Erstpublikation durch das **Kompetenzzentrum OGD** prüfen lassen; bei Zweifeln Datenschutzstelle einbeziehen.

:::note
**Warum keine Pseudonymisierung als OGD?**  
Gemäss Art. 5 bleiben pseudonymisierte Daten personenbezogen – sie dürfen nicht veröffentlicht werden.  
Nur nach wirksamer **Anonymisierung**, **Aggregation** oder **De-Identifikation** dürfen Daten als OGD freigegeben werden.
:::
