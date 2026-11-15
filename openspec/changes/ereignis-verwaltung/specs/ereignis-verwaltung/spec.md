## Purpose

Ereignisse bilden die oberste Ordnungsebene des Systems. Jede Meldung und jedes daraus entstehende Artefakt gehört zu genau einem Ereignis. Aktive Ereignisse werden bearbeitet, archivierte dienen der Nachvollziehbarkeit.

## ADDED Requirements

### Requirement: Ereignis anlegen
Das System SHALL das Anlegen eines Ereignisses mit mindestens Bezeichnung, Ort und Beginn erlauben.

#### Scenario: Neues Ereignis anlegen
- **WHEN** eine berechtigte Funktion ein Ereignis mit Bezeichnung, Ort und Beginn erfasst
- **THEN** existiert das Ereignis mit dem Status "aktiv" oder "archiviert" gemäss Auswahl und ist in der Ereignisliste sichtbar

#### Scenario: Pflichtangaben fehlen
- **WHEN** eine Funktion ein Ereignis ohne Bezeichnung speichern will
- **THEN** lehnt das System das Speichern ab und nennt die fehlende Angabe

### Requirement: Vorausgewähltes aktives Ereignis
Das System SHALL zu jedem Zeitpunkt genau ein Ereignis als Standardereignis vorauswählen, das beim Öffnen des Systems aktiv ist.

#### Scenario: Start mit aktivem Ereignis
- **WHEN** eine Funktion das System öffnet und ein aktives Standardereignis existiert
- **THEN** ist dieses Ereignis ausgewählt und alle Ansichten beziehen sich darauf

#### Scenario: Standardereignis wechseln
- **WHEN** eine berechtigte Funktion ein anderes Ereignis als Standardereignis festlegt
- **THEN** ist nur noch dieses Ereignis als Standard markiert und der Wechsel ist protokolliert

### Requirement: Aktives Ereignis jederzeit sichtbar
Das System SHALL das gewählte Ereignis in jeder Ansicht deutlich sichtbar anzeigen.

#### Scenario: Anzeige in jeder Ansicht
- **WHEN** eine Funktion eine beliebige Ansicht öffnet (Postfach, Tafel, Karte, Rapport)
- **THEN** zeigt die Ansicht Bezeichnung und Status des gewählten Ereignisses an

### Requirement: Zuordnung zu genau einem Ereignis
Das System SHALL jede Meldung und jedes daraus abgeleitete Artefakt genau einem Ereignis zuordnen.

#### Scenario: Meldung erfassen
- **WHEN** eine Funktion eine Meldung erfasst
- **THEN** wird die Meldung dem gewählten Ereignis zugeordnet und erscheint nur dort

#### Scenario: Abgeleitete Artefakte
- **WHEN** aus einer Meldung ein Tafeleintrag, Kartenobjekt oder Journaleintrag entsteht
- **THEN** gehört der Eintrag zum selben Ereignis wie die Meldung

### Requirement: Archivierte Ereignisse nur lesbar
Das System SHALL archivierte Ereignisse für Berechtigte lesbar halten und jede Änderung an ihren Inhalten verweigern.

#### Scenario: Ereignis archivieren
- **WHEN** eine berechtigte Funktion ein aktives Ereignis archiviert
- **THEN** sind dessen Inhalte weiterhin einsehbar und nicht mehr änderbar

#### Scenario: Änderung am archivierten Ereignis
- **WHEN** eine Funktion eine Meldung in einem archivierten Ereignis erfassen oder ändern will
- **THEN** verweigert das System die Aktion und weist auf den Archivstatus hin

### Requirement: Mehrere Ereignisse parallel
Das System SHALL mehrere nicht archivierte Ereignisse gleichzeitig zulassen, wobei genau eines als Standard gilt.

#### Scenario: Zweites Ereignis aktiv
- **WHEN** ein zweites Ereignis angelegt wird, während ein anderes aktiv ist
- **THEN** bleibt das bisherige Standardereignis ausgewählt, bis eine berechtigte Funktion es wechselt
