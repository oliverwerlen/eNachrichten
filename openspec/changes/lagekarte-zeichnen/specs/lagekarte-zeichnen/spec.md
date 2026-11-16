## Purpose

Ergänzt die Lagekarte um frei gezeichnete Elemente für Sachverhalte, die sich nicht mit Symbolen abbilden lassen.

## ADDED Requirements

### Requirement: Zeichenwerkzeuge
Das System SHALL Werkzeuge für Linien, Flächen, Pfeile und Textnotizen auf der Lagekarte anbieten.

#### Scenario: Fläche zeichnen
- **WHEN** eine berechtigte Funktion eine Fläche um ein Gebiet zeichnet
- **THEN** erscheint die Fläche auf der gewählten Ebene

### Requirement: Farbe nach Kategorie
Das System SHALL gezeichneten Elementen die Farbe der gewählten Kategorie (bestehend, Einsatz, Gefahr, Auswirkung) nach den Farbregeln des Kurzmanuals zuweisen.

#### Scenario: Gefahr zeichnen
- **WHEN** ein Element als Gefahr gezeichnet wird
- **THEN** wird es orange dargestellt

### Requirement: Zuordnung zu Ebene und Zeit
Das System SHALL jedes gezeichnete Element einer Ebene und einer Ereigniszeit zuordnen.

#### Scenario: Zeitstand
- **WHEN** der Kartenstand zu einem früheren Zeitpunkt angezeigt wird
- **THEN** zeigt die Karte nur Elemente, die zu diesem Zeitpunkt bestanden

### Requirement: Verweis auf Meldung
Das System SHALL gezeichnete Elemente optional mit einer Meldung verknüpfen.

#### Scenario: Element mit Herkunft
- **WHEN** ein Element aus einer Meldung entsteht
- **THEN** ist die Meldung vom Element aus erreichbar

### Requirement: Änderungen nachvollziehbar
Das System SHALL Änderungen und Löschungen gezeichneter Elemente protokollieren, ohne frühere Zeitstände zu verändern.

#### Scenario: Element löschen
- **WHEN** ein Element gelöscht wird
- **THEN** bleibt es in früheren Zeitständen sichtbar und der Löschvorgang ist protokolliert
