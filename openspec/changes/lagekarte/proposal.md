## Why

Die Nachrichtenkarte (Na-Karte) wird heute nur bedingt digital geführt. Neu soll sie digital und nach dem Kurzmanual Kartenführung (AMZ Kanton Zürich) geführt werden. Sie ist Teil der Lage und liegt in der Verantwortung des Nachrichtendienstes.

## What Changes

- Digitale Lagekarte auf Basis der Karten von swisstopo.
- Kartenkopf nach Manual: Titel (Basisplan), Datum und Uhrzeit (Ereigniszeit), Koordinatenkreuze.
- Symbole nach Kurzmanual mit festen Farbregeln: schwarz bestehende Situation, blau Stäbe, Formationen, Einrichtungen und Bewegungen, orange Gefahren, rot Auswirkungen. Partnerfarben für Hintergründe (Polizei weiss, Feuerwehr rot, Sanität blau, Zivilschutz orange usw.).
- Symbolkategorien: Formationen, Stäbe, Einrichtungen, Bewegungen (beabsichtigt, durchgeführt, laufend), Gefahren, Auswirkungen auf Gebiete, Verkehrswege, Objekte, Personen, Grenzen.
- Zusatzzeichen (Partner, Kennzeichnung, Nummer, Zusatzangabe).
- Ebenen (analog zu den Pausen) mit Momentaufnahme pro Ereigniszeit.
- Vorschläge aus Meldungen (Wo, Tut was, Wann), vorausgefüllt und anpassbar, bestätigt durch den Nachrichtendienst.
- Jedes Kartenobjekt verweist auf die Ursprungsmeldung.
- Anzeige der Personenbergungsübersicht beim Schadengebiet (verknüpft mit den Evakuationen).

## Capabilities

### New Capabilities
- `lagekarte`: Digitale Lagekarte mit swisstopo-Basis, Symbolen nach Kurzmanual, Ebenen, Zeitstand und Kartenvorschlägen.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `meldungskette-nachvollziehbarkeit`.
- Verwandt: `tafeln-zaehltafeln` (Personen), `lage-ueberblick`, `rapport-lagerapport`.
- Externe Abhängigkeit: swisstopo-Kartendienst. Nach aktuellem Kenntnisstand sind die Geodaten frei nutzbar. Das ist vor der Umsetzung zu prüfen.
- Offene Fragen: Koordinatensystem (Annahme: Landesvermessung LV95, die Kreuze im Manual nennen ältere Werte). Genauer Kartenausschnitt für das Lötschental. Welche Symbole sind im Prototyp vollständig vorhanden (Annahme: alle des Manuals).
