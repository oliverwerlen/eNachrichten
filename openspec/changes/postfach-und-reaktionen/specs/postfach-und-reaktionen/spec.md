## Purpose

Jede interne Funktion bearbeitet ihre zugewiesenen Meldungen im Postfach und reagiert darauf. Inhaltliche Reaktionen erzeugen neue Meldungen, reine Statuswechsel nicht.

## ADDED Requirements

### Requirement: Postfach pro Funktion
Das System SHALL jeder internen Funktion ein Postfach mit den ihr zugewiesenen und von ihr erfassten Meldungen des gewählten Ereignisses zeigen.

#### Scenario: Zugewiesene Meldungen
- **WHEN** eine Meldung der Funktion Logistik zugewiesen wird
- **THEN** erscheint sie im Postfach der Logistik

### Requirement: Postfachanzeige
Das System SHALL im Postfach pro Meldung Nummer, Betreff, Einstufung, Frist und Status anzeigen und nach Dringlichkeit und Frist sortieren.

#### Scenario: Sortierung
- **WHEN** das Postfach mehrere Meldungen enthält
- **THEN** stehen Schlüsselnachrichten und Meldungen mit früher Frist oben

### Requirement: Statuswechsel ohne Meldung
Das System SHALL die Statuswechsel "neu", "gelesen" und "in Arbeit" erlauben und dabei keine neue Meldung erzeugen.

#### Scenario: Meldung öffnen
- **WHEN** eine Funktion eine neue Meldung öffnet
- **THEN** wechselt der Status auf "gelesen", ohne dass eine Meldung entsteht

#### Scenario: Statuswechsel nachvollziehbar
- **WHEN** der Status wechselt
- **THEN** werden Person, Funktion und Zeit im Verlauf der Meldung gespeichert

### Requirement: Quittieren
Das System SHALL eine Funktion eine zugewiesene Meldung mit "ok" quittieren lassen, wobei die Quittierung als Kenntnisnahme festgehalten wird und keine neue Meldung erzeugt.

#### Scenario: Kenntnisnahme
- **WHEN** eine Funktion eine Mitteilung mit "ok" quittiert
- **THEN** gilt die Meldung für diese Funktion als zur Kenntnis genommen und es entsteht keine neue Meldung

### Requirement: Rückfrage als neue Meldung
Das System SHALL beim Stellen einer Rückfrage eine neue Meldung vom Typ Anfrage erzeugen, die auf die Ursprungsmeldung verweist.

#### Scenario: Rückfrage stellen
- **WHEN** die Funktion Einsatz zu einem Auftrag eine Rückfrage stellt
- **THEN** entsteht eine neue Meldung mit Verweis auf den Auftrag, die der Triage zugeführt wird

### Requirement: Antworten
Das System SHALL das Antworten auf eine Meldung erlauben, wobei die Antwort eine neue Meldung vom Typ Antwort mit Verweis auf die Ursprungsmeldung ist.

#### Scenario: Antwort erfassen
- **WHEN** eine Funktion auf eine Anfrage antwortet
- **THEN** entsteht eine neue Antwortmeldung, die der Triage zugeführt wird

### Requirement: Abschliessen erzeugt Abschlussmeldung
Das System SHALL beim Abschliessen ("erledigt") einer zugewiesenen Meldung eine Abschlussmeldung (Vollzug oder Antwort) erzeugen, die auf die Ursprungsmeldung verweist.

#### Scenario: Auftrag abschliessen
- **WHEN** die Funktion Einsatz einen Auftrag als erledigt abschliesst
- **THEN** entsteht eine Meldung vom Typ Vollzug mit Verweis auf den Auftrag, und sie durchläuft die Triage

### Requirement: Neue Meldungen durchlaufen den Fluss
Das System SHALL jede aus einer Reaktion entstandene Meldung dem gleichen Ablauf unterwerfen (Triage, Verteilung, Ablagen).

#### Scenario: Wirkung auf Folgeartefakte
- **WHEN** eine Abschlussmeldung eingestuft wird
- **THEN** kann sie die Auftragskontrolle, die Tafeln, die Karte und das Journal beeinflussen
