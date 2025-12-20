# Smart Office Occupancy Detection
### An End-to-End Machine Learning Pipeline for HVAC Energy Optimization

## Projektüberblick
Gebäude sind für einen erheblichen Teil des weltweiten Energieverbrauchs verantwortlich, insbesondere durch Heizungs-, Lüftungs- und Klimaanlagen (HVAC). Dieses Projekt implementiert eine ML Pipeline zur Erkennung der Raumbelegung basierend auf IoT-Sensordaten. 

Durch die präzise Erkennung, ob ein Raum belegt ist, können Gebäudemanagementsysteme den Energieverbrauch dynamisch anpassen. Dies ermöglicht eine erhebliche Kostensenkung, während der Nutzerkomfort gewahrt bleibt.

## Kernfunktionen
* **Zeitreihen-Data-Engineering:**
    * Robuster Umgang mit Sensordrift und Zeitabgleich (Rundung auf die nächste Minute).
    * Logik zur Ausreißererkennung für unphysikalische Sensorwerte (z. B. Temperaturspitzen > 50°C).
    * Lineare Interpolation und Backwards Filling für fehlende Werte, um die Integrität der Zeitreihen zu gewährleisten.
* **Feature Engineering:**
    * **Cyclic Time Encoding:** Transformation von Zeitstempeln in Sinus- und Cosinuswellen, um die zirkuläre Natur eines 24-Stunden-Tages abzubilden.
    * **Physikalische Trends ($CO_2$-Delta):** Implementierung von 15-minütigen Lag-Features, um den schnellen $CO_2$-Anstieg beim Betreten eines Raumes zu erfassen.
    * **Domain-Integration:** Automatisierte Feiertagserkennung mithilfe der `holidays`-Library und Definition von Kernarbeitszeiten.
* **Modellierung & Validierung:**
    * Vergleichendes Benchmarking von Logistischer Regression, Random Forest und Histogram-based Gradient Boosting.
    * Nutzung von TimeSeriesSplit, um Data Leakage zu verhindern und sicherzustellen, dass das Modell über chronologische Daten hinweg gut generalisiert.

## Wirtschaftliche Bewertung & KPI-Validierung
* **Threshold-Tuning:** Eine benutzerdefinierte Logik, die Energiekosten (€) gegen den Nutzerkomfort (Minuten Frieren pro Tag) abwägt.
* **KPI-Metriken:** Validierung basierend auf ROC-AUC und insbesondere Recall, um False Negatives zu minimieren (Steigerung der Nutzerzufriedenheit).
* **Kosten-Nutzen-Analyse:** Berechnung der tatsächlichen Heizlaufzeit und der damit verbundenen Kosten für jedes Modell, um die effizienteste Lösung zu identifizieren.

## Tech Stack
* **Sprache:** Python 3.13
* **Bibliotheken:** `scikit-learn`, `pandas`, `numpy`, `plotly`, `matplotlib`, `holidays`

## Projektherkunft & Danksagung
Dieses Projekt wurde im Rahmen des Moduls **„Data Mining & Machine Learning 1“** an der **Hochschule Karlsruhe (HKA)** entwickelt.
* **Autoren:** Markus, Govind, Elias
* **Akademischer Kontext:** B.Sc. Data Science, Winter 2025/26
* **Datenquelle:** Vom Fachbereich für die Entwicklung akademischer Use Cases bereitgestellt.
