---
sidebar_position: 5
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Vermeidung des Personenbezugs

Dieses Kapitel erläutert die **Methodik und Umsetzung** im Detail. Es baut auf dem einfachen Einstieg unter **Personenbezug** auf und bietet konkrete Schritte, Beispiele und Kriterien.

## So werden Daten anonymisiert

Neben den konkreten Methoden zur Vermeidung des Personenbezugs ist es wichtig, dass die De-Identifizierung als strukturierter Prozess innerhalb der Verwaltung verstanden wird. Ziel ist ein **nachvollziehbarer, wiederholbarer Ablauf**, der sicherstellt, dass alle potenziell personenbezogenen Daten erkannt, geprüft und korrekt behandelt werden.

Die folgende Übersicht orientiert sich an einem **risikobasierten De-Identifikationsansatz** gemäss den Datenschutzgrundsätzen der Schweiz. Sie zeigt, wie Verwaltungen systematisch vorgehen können, um den Personenbezug zuverlässig zu vermeiden und Datensätze OGD-tauglich aufzubereiten:

| Schritt | Beschreibung | Ziel / Ergebnis |
|---|---|---|
| **1. Zweck & Umfang bestätigen** | Konkretes **Publikationsziel** (OGD ja/nein), **Rechtsgrundlage** und **benötigte Granularität** für **das bereits gewählte Dataset** festlegen. Prüfen, ob wirklich Einzeldaten nötig sind oder Aggregatdaten genügen. | Klarer Rahmen für Datenschutz und Nutzbarkeit |
| **2. PII-/QI-Screening** | Im **gewählten Dataset** Identifikatoren (PII) und **Quasi-Identifikatoren (QI)** identifizieren und kennzeichnen (z. B. Alter, PLZ, Datum/Uhrzeit, Geokoordinaten). | Relevante Risiken sind vollständig erfasst |
| **3. Felder taggen** | PII/QI-Spalten mit **einheitlichen Tags** (z. B. `pii`, `qi`) versehen; Entscheid-/Audit-Notizen anfügen. | Einheitliche Grundlage für die Umsetzung |
| **4. Methode wählen** | Passende Maßnahme je Feld/Kombination festlegen: **Maskierung/Löschung**, **Anonymisierung**, **Generalisierung/Aggregation**, **K-Anonymität/L-Diversität**. | Wirksame, zweckmäßige De-Identifizierungsstrategie |
| **5. De-Identifikation umsetzen** | Schritte **reproduzierbar** anwenden (Script/Workflow), inkl. Parameter (Klassen, Raster, `k`-Wert). **Audit-Trail** führen. | Personenbezug wird systematisch entfernt |
| **6. Validieren & freigeben** | **Re-Identifikationsrisiko** prüfen (z. B. `k &lt; 5`), **Utility-Checks** (Kennzahlen/Analysen bleiben sinnvoll), **Freitext & Metadaten** kontrollieren. **Freigabe** dokumentieren. | Datenschutzkonform, nutzbar, OGD-bereit |

:::note[Hinweis]
Die De-Identifizierung sollte **nicht als einmalige Massnahme**, sondern als **kontinuierlicher Prozess** verstanden werden, sollte die Veröffentlichung der Daten kein einmaliges Ereigniss sein. Regelmäßige Überprüfung, Standardisierung (z. B. über Tagging-Schemas) und Automatisierung helfen, langfristig konsistente, sichere und OGD-taugliche Datenflüsse zu gewährleisten.
:::

## Methoden zur Vermeidung des Personenbezugs

Die folgenden **vier Methoden** sollen die Mitarbeitenden dabei unterstützen, Datensätze so aufzubereiten, dass **keine Identifikation einzelner Personen möglich ist** und sie somit als OGD veröffentlicht werden dürfen. Entschieden werden kann je nach Situation, wo eine entsprechende Methode am einfachsten oder vielversprechendsten ist:

| Situation | Zweck | Empfohlene Methode zur De-Identifikation |
|---|---|---|
| Direkte Kennungen vorhanden (Name, Adresse, Kundennummer) | Entfernen persönlicher Identifikatoren | **Maskierung / Löschung** |
| Personenbezug soll dauerhaft ausgeschlossen werden | Endgültiges Entfernen des Bezuges | **Anonymisierung** |
| Präzise Werte erlauben Rückschluss auf Individuen | Genauigkeit kontrolliert reduzieren | **Generalisierung & Aggregation** |
| Mehrere Attribute ermöglichen Rückschluss in Kombination | Risiko messbar reduzieren | **K-Anonymität sicherstellen** |

<Tabs>

<TabItem value="masking" label="Maskierung / Löschung">

### Ziel
**Direkte Kennungen entfernen oder unkenntlich machen**, damit die Person nicht mehr direkt identifiziert werden kann.

### Typische direkte Identifikatoren
- Name
- Adresse
- Telefonnummer / E-Mail
- Kontonummer, Versicherungsnummer, Sozialversicherungsnummer etc.

### Vorgehen (Schritt für Schritt)
| Feld           | Aktion                               | Beispiel                                      |
|--------------- |--------------------------------------|-----------------------------------------------|
| Name           | löschen                              | `Müller Anna` → *(entfernt)*                  |
| AHV-Nummer   | durch neutralen Code ersetzen        | `AHV-123` → `Person_001`                         |
| Adresse        | eine Ebene reduzieren        | `Dienerstrasse 8` → `Kreis 4`     |
| E-Mail         | entfernen                            | `anna.mueller@...` → *(entfernt)*             |
| Telefonnummer  | entfernen (oder Teilmaskierung)      | `079 123 45 67` → *(entfernt)*                |

**Wichtig**
- **Maskierung ohne Mapping-Schlüssel → geeignet für OGD**
- **Maskierung mit Mapping-Schlüssel → Pseudonymisierung → *nicht* OGD-fähig**

**Hinweise:** 
- **Freitextfelder prüfen** → In Kommentaren/Bemerkungen enthaltene Namen oder Kennungen ebenfalls entfernen oder anonymisieren (ggf. automatische Suche mit Tools zur Personenerkennung *Named Entity Recognition* einsetzen).
- **Metadaten bereinigen** → Sicherstellen, dass z.B. Dateinamen, Dokument-Eigenschaften oder Tabellenblatt-Namen keine personenbezogenen Angaben (wie Namen) mehr enthalten.
- **Konsistenz wahren** → Bei Ersatz von IDs (Pseudonymisierung) darauf achten, dass derselbe Code konsistent verwendet wird, um Zusammenhänge in den Daten zu erhalten – allerdings diese Zuordnung (Mapping) nicht mit veröffentlichen.

</TabItem>

<TabItem value="anonymization" label="Anonymisierung">

### Ziel
Der Personenbezug wird **irreversibel** entfernt.  
Keine Stelle (auch nicht der ursprüngliche Dateninhaber) besitzt einen Schlüssel zur Wiederherstellung.

### Eigenschaften anonymisierter Daten
| Merkmal                 | Bedeutung                                                |
|-------------------------|----------------------------------------------------------|
| irreversibel            | keine Rückführung auf eine Person möglich                |
| ohne Schlüssel          | kein Mapping vorhanden (niemand kann re-identifizieren)  |
| nicht mehr Personendaten | damit **OGD-publizierbar** (fällt nicht unter Datenschutz) |

### Umsetzung (praktisches Vorgehen)
1. **Alle direkten Identifikatoren entfernen** (siehe Tab "Maskierung").  
2. **Quasi-Identifikatoren ermitteln und prüfen** – also Merkmale, die einzeln oder in Kombination Personen eingrenzen können (z.B. Alter, Postleitzahl, Geburtsdatum, Geschlecht, Beruf, zeitliche Angaben, Arbeitsort etc.).
3. Falls bestimmte Kombinationen noch zu eindeutig sind → **Generalisierung / Aggregation anwenden** (siehe nächster Tab), d.h. Werte weniger präzise machen oder zusammenfassen.
4. Wenn nach Generalisierung weiterhin Identifikationsrisiken bestehen → **weitere Anonymisierungstechniken einsetzen**: z.B. **Unterdrückung** (Suppression: problematische Einzelwerte oder ganze Datensätze entfernen) oder **Randomisierung** (zufällige Änderungen einbauen: Werte leicht verfälschen, zwischen Datensätzen vertauschen oder kontrolliert Rauschen hinzufügen, um individuelle Muster zu verwischen).

### Check
> **Kann eine einzelne Person immer noch erkannt werden?**  
→ Wenn ja: **noch keine ausreichende Anonymisierung!** Weitere Generalisierung oder Entfernung von Merkmalen nötig.

**Hinweise:** 
- **Externe Daten berücksichtigen** → Bedenken, dass Angreifer auch andere Quellen nutzen könnten. Wenn eine Person durch Kombination aus unseren Daten *und* extern verfügbaren Informationen (z.B. Social Media, Telefonbuch, Register) identifizierbar wäre, müssen entsprechende Merkmale weiter verallgemeinert oder entfernt werden.
- **Keine Pseudonym-Schlüssel behalten** → Falls ein Datensatz intern pseudonymisiert wurde, dürfen die Zuordnungs-Tabellen nicht mit veröffentlicht werden. Idealerweise vernichtet man Mapping-Tabellen nach interner Nutzung, um echte Anonymität zu gewährleisten.
- ***Differential Privacy* (fortgeschritten)** → Bei sehr großen Datenmengen oder der Bereitstellung rein statistischer Daten kann Differential-Privacy-Technik erwogen werden. Dabei wird kontrolliertes statistisches Rauschen zu Daten bzw. Abfragen hinzugefügt, um die Privatsphäre mathematisch zu garantieren (wird z.B. in offiziellen Statistiken erprobt).

</TabItem>

<TabItem value="generalization" label="Generalisierung / Aggregation">

### Ziel
Verhinderung von Rückschlüssen durch **Reduktion der Genauigkeit** oder **Zusammenfassung von Werten**. Einzelangaben werden verallgemeinert, sodass individuelle Details nicht mehr hervortreten.

### Beispiele

| Vorher (personenbeziehbar)    | Nachher (anonymisiert, OGD-geeignet)      |
|-------------------------------|-------------------------------------------|
| Alter = 41                    | Altersgruppe: 40–44                       |
| Einkommen = 92'450            | Einkommensklasse: 90'000–100'000          |
| Adresse = Marktgasse 12       | Wohnort: Quartier Altstadt                |
| Unfall am 03.05.2023, 13:44   | Ereigniszeit: Mai, 2023                   |

### Praktische Schwellenwerte (Empfehlungen)
- **Mindesthäufigkeit**: Kategorien mit **n &lt; 5** Fällen → **zusammenfassen oder entfernen** (keine Veröffentlichung von Zellen mit &lt; 5 Fällen, um Individualisierbarkeit zu vermeiden).
- **Räumliche Auflösung**: Keine Ortsangaben präziser als **Stadtteil/Quartier** (bei geringer Bevölkerungsdichte eher noch gröber) – alternativ Geodaten auf ein **Raster ≥ 100 m** runden.
- **Zeitliche Auflösung**: Zeitangaben nicht zu fein – ggf. nur **Monat oder Quartal** statt exaktes Datum; Tageszeit grob (z.B. "Nachmittag" statt 13:44 Uhr).
- **Numerische Werte kappen/klassen**: Hohe Detailgenauigkeit reduzieren – z.B. Einkommen in Klassen angeben, Alter in 5-Jahres-Bänder einteilen, extreme Werte **„top-coden“** (z.B. "80+ Jahre" als höchste Kategorie).
- **Ausreißer behandeln**: Falls einzelne Datensätze immer noch einzigartig sind (z.B. einzige Person >100 Jahre alt), diese Werte weiter verallgemeinern oder ggf. aus dem veröffentlichbaren Datensatz ausschließen.
- **Aggregierung statt Details**: Gegebenenfalls **Daten nur aggregiert** bereitstellen (z.B. Summen oder Durchschnittswerte pro Gruppe statt individuelle Einzeldaten), um personenbeziehbare Details vollständig zu vermeiden.

### Umsetzung in 2 Minuten
In der Praxis lässt sich Generalisierung oft schnell umsetzen. Beispielsweise können bereits in Tabellenkalkulationen durch Kategorienbildung oder Pivot-Tabellen Daten zusammengefasst werden (Altersklassen definieren, Adressen auf Gebietseinheiten mappen etc.). Wichtig ist, vorab sinnvolle Klassen und Schwellenwerte festzulegen. Auch einfache Skripte oder SQL-Abfragen können genutzt werden, um Werte zu runden oder zu gruppieren. Durch diese Maßnahmen wird in kurzer Zeit eine deutlich höhere Anonymität erreicht, ohne die Gesamtaussage der Daten zu verlieren.

</TabItem>

<TabItem value="kanon" label="K-Anonymität (Gruppengrößen-Schutz)">

### Ziel
Sicherstellen, dass **mindestens k Personen** die gleiche Kombination von potenziell identifizierenden Merkmalen aufweisen. Dadurch ist keiner allein anhand dieser Merkmale herausgreifbar.

### Was bedeutet „k“?
`k = 5` bedeutet:  
Jede mögliche Merkmalskombination (über die definierten Quasi-Identifikatoren) muss **mindestens 5 Datensätze** umfassen. Einzelne Personen "verstecken" sich also in einer Gruppe von mindestens 5 mit denselben Merkmalsausprägungen.

### Beispiel
Angenommen, Alter und Ort seien zwei Quasi-Identifikatoren in einem Datensatz:

| Altersgruppe | Quartier  | Anzahl Datensätze | OGD-Freigabe?             |
|--------------|-----------|-------------------|---------------------------|
| 18–25        | Altstadt  | 12                | *OK* (n=12 ≥ k=5)      |
| 75–80        | Altstadt  | 2                 | *nicht ok* (n=2 &lt; k=5) |

In obigem Beispiel müsste die Gruppe "75–80 im Quartier Altstadt" weiter zusammengefasst oder unterdrückt werden, bis pro Zelle mindestens 5 Fälle vorhanden sind (z.B. Alterskategorie erweitern oder diese Datenkategorie nicht veröffentlichen).

### Umsetzungsschritte
1. **Quasi-Identifikatoren (QI) festlegen** – Identifiziere die Kombination von Merkmalen (z.B. Alter + Wohnort + Zeitraum + Ereignisart), die gemeinsam eine Person potentiell identifizierbar machen könnten.
2. **Kategorien bilden** – Lege sinnvolle Klassifizierungen/Generalisierungen für diese Merkmale fest (siehe vorheriger Tab für Beispiele).
3. **Häufigkeiten prüfen** – Analysiere den Datensatz dahingehend, ob alle Kombinationen der Quasi-Identifikatoren mit mindestens *k* Datensätzen vorkommen.
4. **Anpassen bis Regel erfüllt** – Falls nein: Kategorien weiter vergröbern oder seltene Kombinationen unterdrücken, bis **jede** Merkmalskombination ≥ k Einträge enthält.

### Ergebnis
→ Der Datensatz erfüllt K-Anonymität und ist damit **robust gegenüber Re-Identifikation** anhand dieser Merkmale.

**Hinweise:** 
- **Wahl von k**: Üblich sind Werte wie k=3, k=5 oder k=10 – je höher *k*, desto stärker der Datenschutz, allerdings umso mehr Detailverlust. Für offene Daten wird oft mindestens k=5 empfohlen.
- **L-Diversität & Co.**: K-Anonymität schützt vor Identifikation über Quasi-Identifikatoren, berücksichtigt aber nicht die Verteilung sensibler Inhalte. Ergänzend kann z.B. eine **L-Diversität** gefordert werden (jede Gruppe weist mindestens L unterschiedliche Werte eines sensitiven Attributes auf), damit nicht alle Personen einer k-Gruppe z.B. dieselbe Diagnose haben. Noch weitergehend stellt **T-Closeness** sicher, dass die Verteilung eines sensitiven Merkmals in jeder Gruppe der Verteilung im Gesamtdatensatz ähnelt. Solche erweiterten Maßnahmen können sinnvoll sein, wenn sensible persönliche Informationen im Datensatz enthalten sind.

</TabItem>

</Tabs>

---

:::tip[Schnell-Check]

- ☐ Direkte Kennungen entfernt (PII/QI)?
- ☐ Kleine Gruppen (n &lt; 5) zusammengefasst?
- ☐ Ort oder Zeit aggregiert oder generalisiert?
- ☐ Freitext auf Personenhinweise geprüft?
- ☐ Keine Re-Identifikation möglich?

→ Wenn überall ein **Ja** gesetzt werden kann, kann der Datensatz kann veröffentlicht werden.
:::

---

:::info[Dokumentation]

- **Programming Differential Privacy – Kapitel 10 (Python/SQL):**  
  https://programming-dp.com/chapter1.html  
- **SPHN (2025): Data De-identification Guidance v2.0:**  
  https://sphn.ch/wp-content/uploads/2025/02/Data-de-identification-guidance-v2.0_20250214.pdf  
- **OECD (2023): Practical Approaches to Anonymisation and De-identification:**  
  https://www.oecd.org/digital/privacy/practical-approaches-to-anonymisation.pdf  

:::
