## Purpose

Stellt die Lage räumlich auf einer digitalen Karte dar, gemäss dem Kurzmanual Kartenführung, mit Symbolen, Ebenen und Zeitstand. Die Karte wird vom Nachrichtendienst geführt und aus Meldungen gespeist.

## ADDED Requirements

### Requirement: swisstopo als Basiskarte
Das System SHALL als Basiskarte die Karten von swisstopo anzeigen und den Bereich des Regionalen Führungsstabs Lötschental als Ausgangsansicht wählen.

#### Scenario: Karte öffnen
- **WHEN** eine Funktion die Lagekarte öffnet
- **THEN** zeigt das System die swisstopo-Karte im Ausschnitt des Lötschentals

### Requirement: Kartenkopf nach Manual
Das System SHALL auf der Karte Titel (Basisplan), Datum und Uhrzeit (Ereigniszeit) und Koordinatenangaben darstellen.

#### Scenario: Kartenstand anzeigen
- **WHEN** die Karte angezeigt wird
- **THEN** sind Titel, Ereigniszeit und Koordinatenreferenz sichtbar

### Requirement: Symbole nach Kurzmanual
Das System SHALL Symbole der Kategorien Formationen, Stäbe, Einrichtungen, Bewegungen, Gefahren und Auswirkungen auf Gebiete, Verkehrswege, Objekte und Personen sowie Grenzen anbieten.

#### Scenario: Symbol setzen
- **WHEN** eine berechtigte Funktion ein Symbol der Kategorie Gefahren setzt
- **THEN** erscheint es an der gewählten Stelle

### Requirement: Farbregeln
Das System SHALL Symbole nach den Farbregeln des Manuals darstellen: schwarz bestehende Situation, blau Stäbe, Formationen, Einrichtungen und Bewegungen, orange Gefahren, rot Auswirkungen.

#### Scenario: Automatische Farbe
- **WHEN** ein Symbol der Kategorie Auswirkungen gesetzt wird
- **THEN** wird es rot dargestellt und die Farbe lässt sich nicht frei ändern

### Requirement: Partnerzugehörigkeit
Das System SHALL Formationen und Stäbe nach Partnerzugehörigkeit mit der Hintergrundfarbe des Manuals kennzeichnen (Polizei weiss, Feuerwehr rot, Sanität blau, Zivilschutz orange, weitere nach Manual).

#### Scenario: Formation der Feuerwehr
- **WHEN** ein Symbol einer Feuerwehrformation gesetzt wird
- **THEN** erhält es den roten Hintergrund

### Requirement: Zusatzzeichen
Das System SHALL für Formationssymbole die Zusatzangaben Bezeichnung des Partners, nähere Kennzeichnung, Nummerierung oder Ortsbezeichnung und Zusatzangaben erfassen.

#### Scenario: Zusatzzeichen erfassen
- **WHEN** eine Funktion ein Feuerwehrsymbol mit Kennzeichnung "Pionier", Nummer "2" und Ort "Blatten" setzt
- **THEN** zeigt das Symbol diese Angaben

### Requirement: Bewegungen
Das System SHALL Bewegungen als beabsichtigt, durchgeführt oder laufend unterscheiden.

#### Scenario: Status einer Verschiebung
- **WHEN** eine beabsichtigte Verschiebung durchgeführt wird
- **THEN** wechselt das Symbol auf den Status "durchgeführt" mit Zeitpunkt

### Requirement: Ebenen und Zeitstand
Das System SHALL Kartenobjekte in Ebenen führen und einen Kartenstand zu einer wählbaren Ereigniszeit darstellen können.

#### Scenario: Früherer Zeitstand
- **WHEN** eine Funktion einen früheren Zeitpunkt wählt
- **THEN** zeigt die Karte den Stand zu diesem Zeitpunkt und kennzeichnet ihn als historisch

### Requirement: Kartenvorschlag aus Meldung
Das System SHALL aus einer Meldung mit Ort ("Wo") und Sachverhalt ("Tut was") einen vorausgefüllten Kartenvorschlag mit Symbol, Ort und Zeit erzeugen, den der Chef Nachrichtendienst bestätigt oder anpasst.

#### Scenario: Vorschlag bestätigen
- **WHEN** der Chef einen Vorschlag bestätigt
- **THEN** wird das Objekt auf der Karte geführt mit Verweis auf die Meldung

#### Scenario: Vorschlag anpassen
- **WHEN** der Chef Symbol oder Ort ändert
- **THEN** wird die Anpassung gespeichert und nachvollziehbar protokolliert

### Requirement: Verweis auf Meldung
Das System SHALL jedes Kartenobjekt mit der Ursprungsmeldung verknüpfen.

#### Scenario: Herkunft anzeigen
- **WHEN** eine Funktion ein Kartenobjekt auswählt
- **THEN** kann sie die Ursprungsmeldung öffnen

### Requirement: Personenübersicht beim Schadengebiet
Das System SHALL beim Schadengebiet die Personenzahlen (Patienten, Vermisste, Tote) als Übersicht aus den Evakuationen anzeigen können.

#### Scenario: Schadengebiet mit Personen
- **WHEN** ein Schadengebiet ausgewählt wird
- **THEN** zeigt das System die Personenzahlen des zugehörigen Sektors aus der Evakuationstafel

### Requirement: Pflege durch den Nachrichtendienst
Das System SHALL Änderungen an der Karte dem Nachrichtendienst vorbehalten und anderen Funktionen die Ansicht gemäss Sichtrechten erlauben.

#### Scenario: Änderung durch andere Funktion
- **WHEN** eine nicht berechtigte Funktion ein Objekt ändern will
- **THEN** verweigert das System die Änderung
