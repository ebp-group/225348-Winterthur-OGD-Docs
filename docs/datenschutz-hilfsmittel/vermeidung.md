---
sidebar_position: 4
---

# Vermeidung des Personenbezugs 

Wenn bei einem Datensatz ein Personenbezug vorhanden ist und eine direkte Publikation nicht in Frage kommt, stehen Verfahren zur Verfügung, mit denen der Personenbezug zumindest soweit beseitigt oder reduziert werden kann, dass eine OGD-Publikation möglich wird (§ 5 Abs. 2 der Verordnung).  
Wichtig: Eine **Pseudonymisierung** bleibt grundsätzlich **personenbezogen** und fällt damit nicht unter „offene Verwaltungsdaten“, sofern nicht zusätzlich zur Pseudonymisierung weitere Massnahmen ergriffen werden.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

Dieses Kapitel zeigt, **wie** Datensätze für OGD so aufbereitet werden, dass **kein Personenbezug** mehr besteht.  
Gemäss Art. 5 der OGD-Verordnung gilt: **Pseudonymisierte Daten bleiben personenbezogen** und sind **nicht** als OGD zu veröffentlichen; eine Publikation kommt nur in Frage, wenn der Personenbezug **wirksam beseitigt** wird (z. B. durch Anonymisierung/Aggregation).

:::tip
**Zielbild:** *So offen wie möglich, so geschützt wie nötig.*  
Erst **nach** wirksamer Vermeidung des Personenbezugs (Anonymisierung/Aggregation/De-Identifikation) sind Daten OGD-tauglich. Leitplanken liefern die **OGD-Richtlinien** von opendata.swiss und Fachleitfäden zu De-Identifikation/Schutzmassnahmen.
:::

<Tabs defaultValue="anonym" values={[
  { label: 'Anonymisierung', value: 'anonym' },
  { label: 'Aggregation', value: 'aggregation' },
  { label: 'De-Identifikation (Prozess)', value: 'deint' },
]}>

<TabItem value="anonym" label="Anonymisierung">

## Anonymisierung

**Was:** Entfernt/verändert Identifikatoren so, dass **keine Re-Identifikation** für vernünftige Dritte mehr realistisch ist; anschliessend gelten die Daten **nicht** mehr als Personendaten.

**Wann einsetzen:**  
- Punkt-/Einzeldatensätze (Events/Einträge) mit potenziell identifizierenden Merkmalen (Zeit, Ort, seltener Beruf etc.).  
- Sensible Attribute, die nur nach **Maskierung** oder **Generalisierung** veröffentlichbar sind. 

**Vorgehen (Winterthur-spezifisch):**
1. **Identifikatoren inventarisieren**: direkte (Name, Kennzeichen) & Quasi-Identifikatoren (Alter, genaue Zeit, Hausnummer, exakte Koordinate).  
2. **Direkte IDs entfernen**; Quasi-IDs **generalisieren**:  
   - Alter → **5/10-Jahresklassen**; Datum/Zeit → **Woche/Monat**; Adresse → **Quartier/250-m-Raster**.  
3. **Seltene Kombinationen schützen**:  
   - **Primär-Suppression** für Gruppen mit **n < 5**; ggf. **Sekundär-Suppression**, damit Rückrechnung unmöglich bleibt.  
4. **Rauschen** auf Zählwerten (bei Bedarf): ±1 mit dokumentierter Methode; für anspruchsvolle Fälle **Differential Privacy** mit kleinem ε und kurzer, laienverständlicher Erklärung in den Metadaten. 
5. **Räumliche Generalisierung**: Punkt-Koordinaten **snappen** auf **250/500-m-Raster** oder **Stadt-Quartiere** (keine Hausnummern). **Geometrien vereinfachen** (keine Eingänge/Privatflächen erkennbar). Leitfaden für Geodaten-OGD beachten.
6. **Re-ID-Check**: Stichprobe mit offen verfügbaren Quellen (Stadtplan, Firmenregister) – wenn identifizierbar → Schritt 2–5 schärfen.  
7. **Metadaten** ergänzen: Welche Felder wurden entfernt/gebündelt? Welche Schwellen (k), Toleranzen, Raster? Verweis auf Richtlinie. 

**Beispiel (Schweiz):**  
- **„Zürich schaut hin“**: Meldedaten werden **anonym** bereitgestellt; personenbezogene Angaben sind entfernt, Veröffentlichung erfolgt mit klaren Metadaten/Hinweisen. Vorgehen zeigt, dass sensible Inhalte nur **ohne Personenbezug** publiziert werden. 
**Referenzen & Hilfsmittel:**  
- OGD-Richtlinien (Bund): Publishing-Orientierung & Schutzvorbehalte. 
- SIK-GIS/ BFS-Leitfaden **OGD für Geodaten**: Umgang mit räumlichen Daten & Anwendbarkeit von OGD. 
- **EDÖB/TOM-Leitfaden**: organisatorische Massnahmen flankierend zur Technik.

</TabItem>

<TabItem value="aggregation" label="Aggregation">

## Aggregation

**Was:** Einzelinformationen werden **auf Gruppen-, Raum- oder Zeitniveau** zusammengefasst; Individualmuster verschwinden, Aussage bleibt nutzbar.

**Wann einsetzen:**  
- Städtische Zähl-/Nutzungsdaten (Verkehr, Umwelt, Meldesysteme), bei denen Einzelereignisse Personenbezug erzeugen könnten.

**Vorgehen (Winterthur-spezifisch):**
1. **Ebenen definieren**:  
   - **Räumlich:** **Quartiere/Statistische Zonen** oder **250-m-Raster** (kein Kanton-Level).  
   - **Zeitlich:** **Woche** oder **Monat** statt Tag/Uhrzeit.  
2. **Schwellwerte**: Keine Veröffentlichung von Gruppen mit **n < 5**; **Merge** mit Nachbarzelle/-periode.  
3. **Kennzahlen**: Mittel/Median/Quantile; **Top/Bottom-Coding** (z. B. Alter ≥ 90).  
4. **Sonderfälle** (Events, seltene Kategorien): zusätzliche **Kategorie-Binning** (z. B. Berufsgruppen zusammenfassen).  
5. **Qualitäts-/Bias-Hinweis** in den Metadaten (Auswirkung der Aggregation, MAUP-Hinweis, Stand/Update-Rhythmus).  
6. **Portal-Praxis**: Bereitstellung über Stadt-/Kantonskatalog, Synchronisierung zu opendata.swiss; kantonale Leitlinien geben den Publikationsprozess vor. :contentReference[oaicite:10]{index=10}

**Beispiel (Schweiz):**  
- **Offene Daten Zürich (Kanton/ Stadt)**: Publiziert werden **aggregierte** Statistiken und geclusterte Geo-Daten; die Leitlinien betonen, dass **nicht-schützenswerte** Inhalte veröffentlicht werden und Schutzmassnahmen vorzuziehen sind. 
**Referenzen & Hilfsmittel:**  
- Kanton Zürich **Leitlinien „Offene Daten publizieren“**: Prozess & Anforderungen (auch für städtische Kontexte gut übertragbar). 
- SIK-GIS/BFS-Leitfaden Geodaten-OGD (Aggregation/Generalisierung bei Geodaten). 

</TabItem>

<TabItem value="deint" label="De-Identifikation (Prozess)">

## De-Identifikation (Prozess)

**Was:** Strukturiertes **Risikomanagement** zur Entfernung/Maskierung von Identifikatoren; kombiniert Methoden (Anonymisierung, Aggregation, Suppression, Rauschen), bis **kein** Personenbezug mehr besteht.

**Wann einsetzen:**  
- Bei **komplexen** Datensätzen (mehrere Quasi-IDs), iteratives Vorgehen nötig (z. B. Bewegungs-/Sensorikdaten, verknüpfte Fachdaten).

**Vorgehen (Winterthur-spezifisch):**
1. **Use-Case & Rechtsgrundlage** festhalten (OGD-Publikation; Art. 5).  
2. **Variablenklassierung:** direkt identifizierend / quasi-identifizierend / sensitiv / frei.  
3. **Risikobewertung** (Re-ID): kleine Gruppen, Ausreisser, Linkage-Risiken; Schwelle festlegen (z. B. *k* = 5).  
4. **Massnahmen wählen:**  
   - Generalisation (z. B. Quartier statt Adresse),  
   - Aggregation (Woche/Monat; 250-m-Raster),  
   - Suppression (Primär+Sekundär),  
   - Rauschen (z. B. ±1 Count),  
   - Top/Bottom-Coding.  
5. **Iteration & Test**: Re-ID-Risiko erneut prüfen; ggf. Parameter nachschärfen.  
6. **Dokumentation & Metadaten:** Methode/Schwellen klar beschreiben; Link zur internen Prüfdoku setzen.  
7. **Freigabeprozess**: Dateneigner → Kompetenzzentrum OGD (Gatekeeping/Standards) → Veröffentlichung + Monitoring. 

**Beispiel (Schweiz):**  
- **SPHN „Data de-identification – phased approach“**: Schweizer Leitdokument für stufenweises De-Identifizieren inkl. **Template** und **Regeln** (übertragbar auf kommunale Datenaufbereitung). 

**Referenzen & Hilfsmittel:**  
- SPHN De-Identifikation (Report + Template). 
- EDÖB-Leitfaden **TOM** (flankierende organisatorische Massnahmen). 
- BFS/OGD Geodaten-Leitfaden (für den Raumbezug).

</TabItem>

</Tabs>

---

## Winterthur-Checkliste (Schnellhilfe)

- **Personenbezug?** Falls ja → Art. 5 prüfen und **Vermeidung** umsetzen.  
- **Städtische Ebenen** nutzen (nie „Kanton“): **Quartier/Statistische Zone**, **250/500-m-Raster**, **Woche/Monat**.  
- **Schwelle**: Keine Zellen/Kombinationen mit **n < 5**; ggf. Sekundär-Suppression.  
- **Rauschen** sparsam und nachvollziehbar (±1 Count); für heikle Fälle DP-Ansatz kurz erläutern & dokumentieren.
- **Metadaten** nach OGD-Richtlinien pflegen (Schutzmassnahmen, Datenstand, Update-Rhythmus, Lizenz). 
- **Gatekeeping:** Vor Erstpublikation **Kompetenzzentrum OGD** einbeziehen; bei Zweifeln **Datenschutzstelle**.

:::note
**Warum keine Pseudonymisierung als OGD?**  
Nach Art. 5 bleibt **pseudonymisiert** = **personenbezogen**. Eine OGD-Publikation ist nur nach **wirksamer Anonymisierung/Aggregation/De-Identifikation** zulässig.
:::
