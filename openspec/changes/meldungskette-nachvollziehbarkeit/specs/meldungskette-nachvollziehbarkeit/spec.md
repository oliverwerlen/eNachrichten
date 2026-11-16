## Purpose

Macht jede Aussage im System bis zur Ursprungsmeldung rückverfolgbar und zeigt die Entwicklung einer Sache als Kette von Meldungen.

## ADDED Requirements

### Requirement: Verweis auf Ursprungsmeldung
Das System SHALL jede Folgemeldung mit einem Verweis auf die Meldung verknüpfen, aus der sie entstanden ist.

#### Scenario: Vollzug zu Auftrag
- **WHEN** ein Vollzug zu einem Auftrag erfasst wird
- **THEN** verweist er auf den Auftrag und der Auftrag zeigt den Vollzug als Folgemeldung

### Requirement: Kettenansicht
Das System SHALL zu jeder Meldung die gesamte Kette (Ursprung und alle Folgemeldungen) mit Typ, Zeit, Verfasser und Status darstellen.

#### Scenario: Kette öffnen
- **WHEN** eine Funktion bei einem Auftrag die Kettenansicht öffnet
- **THEN** sieht sie Rückfragen, Antworten und den Vollzug in zeitlicher Reihenfolge

### Requirement: Rückverfolgung abgeleiteter Einträge
Das System SHALL jeden aus einer Meldung abgeleiteten Eintrag (Tafelzeile, Kartenobjekt, Journaleintrag, Rapportaussage) mit der Ursprungsmeldung verknüpfen und den Sprung dorthin ermöglichen.

#### Scenario: Von der Tafel zur Meldung
- **WHEN** eine Funktion bei einer Zeile der Auftragskontrolle die Herkunft öffnet
- **THEN** zeigt das System die Ursprungsmeldung samt Kette

#### Scenario: Von der Karte zur Meldung
- **WHEN** eine Funktion ein Kartenobjekt auswählt
- **THEN** kann sie die Meldung öffnen, aus der das Objekt entstand

### Requirement: Ereignishistorie
Das System SHALL zu jeder Meldung festhalten, wer sie wann erfasst, eingestuft, verteilt, geändert oder abgeschlossen hat.

#### Scenario: Historie einsehen
- **WHEN** eine Funktion die Historie einer Meldung öffnet
- **THEN** sind alle Schritte mit Person, Funktion und Zeit sichtbar

### Requirement: Unveränderliche Historie
Das System SHALL Historieneinträge weder löschen noch verändern.

#### Scenario: Löschversuch
- **WHEN** eine Funktion einen Historieneintrag löschen will
- **THEN** bietet das System diese Möglichkeit nicht an

### Requirement: Meldung zwischen Ereignissen verschieben
Das System SHALL eine falsch zugeordnete Meldung durch eine berechtigte Funktion in ein anderes Ereignis verschieben lassen und die Verschiebung mit Begründung protokollieren.

#### Scenario: Falsches Ereignis
- **WHEN** der Chef Nachrichtendienst eine Meldung in das richtige Ereignis verschiebt und eine Begründung angibt
- **THEN** erscheint sie im Zielereignis, und die Historie beider Ereignisse nennt die Verschiebung
