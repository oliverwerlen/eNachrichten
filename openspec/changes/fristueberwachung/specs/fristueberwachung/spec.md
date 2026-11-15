## Purpose

Erkennt Fristüberschreitungen bei Aufträgen, Hilfegesuchen und Terminen und macht sie den Zuständigen und der Führung sichtbar.

## ADDED Requirements

### Requirement: Überwachte Einträge
Das System SHALL Fristen in der Auftragskontrolle, den Sofortmassnahmen, den Hilfegesuchen, der Zeitplanung und den Postfächern überwachen.

#### Scenario: Frist gesetzt
- **WHEN** ein Eintrag mit "Bis wann" gespeichert wird
- **THEN** wird die Frist überwacht

### Requirement: Warnstufen
Das System SHALL die Stufen "bald fällig" und "überfällig" unterscheiden und unterschiedlich kennzeichnen.

#### Scenario: Bald fällig
- **WHEN** die Frist innerhalb der eingestellten Vorwarnzeit liegt
- **THEN** erscheint der Eintrag als "bald fällig"

#### Scenario: Überfällig
- **WHEN** die Frist abgelaufen und der Eintrag nicht abgeschlossen ist
- **THEN** erscheint der Eintrag als "überfällig"

### Requirement: Einstellbare Vorwarnzeit
Das System SHALL die Vorwarnzeit pro Ereignis einstellbar halten.

#### Scenario: Vorwarnzeit ändern
- **WHEN** eine berechtigte Funktion die Vorwarnzeit auf 30 Minuten setzt
- **THEN** gilt die Stufe "bald fällig" ab 30 Minuten vor Ablauf

### Requirement: Hinweis an Zuständige und Führung
Das System SHALL überfällige Einträge der zuständigen Funktion und dem Chef Nachrichtendienst anzeigen.

#### Scenario: Hinweis
- **WHEN** ein Auftrag der Funktion Einsatz überfällig wird
- **THEN** sehen Einsatz und der Chef Nachrichtendienst den Hinweis

### Requirement: Sichtbarkeit im Lage-Überblick und Rapport
Das System SHALL überfällige Einträge im Lage-Überblick und im Traktandum Aufträge des Rapports hervorheben.

#### Scenario: Rapport
- **WHEN** das Traktandum Aufträge aktiv ist
- **THEN** stehen überfällige Einträge oben und sind gekennzeichnet

### Requirement: Abschluss beendet die Überwachung
Das System SHALL die Überwachung eines Eintrags beenden, sobald er abgeschlossen ist.

#### Scenario: Vollzug trifft ein
- **WHEN** ein Vollzug den Eintrag abschliesst
- **THEN** verschwindet die Fristwarnung
