[work in progress]

# Daten
Die Daten basieren auf den Plenarprotokollen des deutschen Budnestags aus der 20. Wahlperiode. Da die Wahlperiode zum Zeitpunkt der Auswertung noch nicht beendet ist, ist die Auswertung vorläufig.
Insgesamt waren zum Zeitpunkt der Auswertung 170 Plenarprotokolle verfügbar. Diese wurden von der Website des deutschen Bundestages als xml-Dateien gescraped und anschließend in einzelne Redebeiträge zerlegt.


# Methode
Für die Klassifikation wurde das Modell *PopBERT* verwendet, siehe: huggingface-link

Für die Auswertung wurde jeder Redebeitrag zunächst mit spacy (Modell: n_german_news_sm) in Sätze zerlegt. Anschließend wurde für jeden Satz mit PopBERT die Werte für die vier Populismus-Dimensionen berechnet.
Anschließend wird über alle Sätze des Beitrags gemittelt, also für jede Dimension der Durchschnitt der Werte über alle Sätze berechnet. Diese vier Durchschnitts-Werte pro Redebeitrag finden sich in der Datei Populismuswerte.csv.


# Probleme
Ein Problem ist, dass die Standardisierung (Berechnung eines Mittelwerts pro Beitrag) dazu führt, dass es einen spezifischen Problemfall gibt: Sehr kurze Beiträge mit einem sehr populistischen Satz bekommen in der entsprechenden Kategorie einen sehr hohen Wert.
In einer Wiederholung der Auswertung müsste man hier nachbessern und ein geeigneteres Standardisierungsverfahren finden. 
Für die aktuelle Auswertung wurden Beiträge mit einer Länge von unter 100 Wörtern nicht berücksichtigt, um die Ergebnisse nicht zu verzerren. Übrig bleiben 17500 Beiträge.
