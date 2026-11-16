## Purpose

Die Triage stuft jede Meldung ein und verteilt sie an interne Funktionen und externe Gegenstellen. Sie liegt beim Chef Nachrichtendienst und löst die Nachführung der Ablagen aus.

## ADDED Requirements

### Requirement: Triage nur durch Chef Nachrichtendienst
Das System SHALL die Einstufung und Verteilung einer Meldung ausschliesslich der Funktion Chef Nachrichtendienst erlauben.

#### Scenario: Berechtigte Triage
- **WHEN** der Chef Nachrichtendienst eine neue Meldung öffnet
- **THEN** kann er sie einstufen und verteilen

#### Scenario: Nicht berechtigte Funktion
- **WHEN** eine andere Funktion eine Meldung einstufen will
- **THEN** verweigert das System die Aktion

### Requirement: Einstufung
Das System SHALL jede Meldung bei der Triage als Schlüsselnachricht (dringend) oder Rohinformation/Nachricht einstufen.

#### Scenario: Schlüsselnachricht
- **WHEN** der Chef Nachrichtendienst eine Meldung als Schlüsselnachricht einstuft
- **THEN** wird sie hervorgehoben und in der Warteschlange und im Lage-Überblick priorisiert

### Requirement: Jede Meldung wird neu eingestuft
Das System SHALL jede Meldung, auch Antworten, Rückfragen und Abschlussmeldungen, einzeln einstufen und die Einstufung nicht von der Ursprungsmeldung erben.

#### Scenario: Folgemeldung
- **WHEN** eine Folgemeldung zu einer Schlüsselnachricht erfasst wird
- **THEN** ist sie zunächst nicht eingestuft und muss vom Chef Nachrichtendienst separat eingestuft werden

### Requirement: Optionale Bewertung
Das System SHALL optional eine Bewertung von Quelle und Information bei der Triage oder bei der Erfassung erlauben.

#### Scenario: Ohne Bewertung
- **WHEN** keine Bewertung eingetragen wird
- **THEN** wird die Meldung trotzdem eingestuft und verteilt

#### Scenario: Mit Bewertung
- **WHEN** der Chef eine Bewertung einträgt
- **THEN** wird sie mit der Meldung gespeichert und angezeigt

### Requirement: Verteilung an interne Funktionen
Das System SHALL eine eingestufte Meldung den gewählten internen Funktionen als Aufgabe im Postfach zuweisen.

#### Scenario: Zuweisung
- **WHEN** der Chef die Funktion Einsatz als Empfänger wählt
- **THEN** erscheint die Meldung im Postfach der Funktion Einsatz

### Requirement: Verteilung an externe Gegenstellen
Das System SHALL bei externen Empfängern die Meldung als Versandauftrag führen und Versand sowie Bestätigung manuell erfassbar machen.

#### Scenario: Versand eintragen
- **WHEN** eine Funktion eine Meldung an die Polizei telefonisch übermittelt und den Versand einträgt
- **THEN** zeigt die Meldung den Status "versandt" mit Zeitpunkt und Person

#### Scenario: Bestätigung eintragen
- **WHEN** die Polizei den Erhalt bestätigt und die Funktion das einträgt
- **THEN** zeigt die Meldung den Status "bestätigt"

#### Scenario: Offener Versand
- **WHEN** ein Versand nicht als versandt eingetragen ist
- **THEN** erscheint die Meldung in der Liste der offenen Versände

### Requirement: Ablagen auslösen
Das System SHALL bei der Triage die Nachführung von Journal, Karte, Tafeln und Kontrolle anstossen oder vorschlagen.

#### Scenario: Journal automatisch
- **WHEN** eine Meldung eingestuft wird
- **THEN** besteht ein Journaleintrag zur Meldung

#### Scenario: Tafelvorschlag
- **WHEN** die Meldung einen Auftrag enthält
- **THEN** schlägt das System einen Eintrag in der Auftragskontrolle vor, den der Chef bestätigt oder anpasst

### Requirement: Warteschlange der Triage
Das System SHALL dem Chef Nachrichtendienst die nicht eingestuften Meldungen nach Dringlichkeit und Alter sortiert zeigen.

#### Scenario: Mehrere offene Meldungen
- **WHEN** mehrere Meldungen auf Einstufung warten
- **THEN** stehen erkennbar dringende und ältere Meldungen oben
