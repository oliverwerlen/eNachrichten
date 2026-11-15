## Purpose

Das Journal bildet alle Meldungen des Ereignisses chronologisch und unveränderlich ab und dient als lückenlose Aufzeichnung des Geschehens.

## ADDED Requirements

### Requirement: Automatische Journalführung
Das System SHALL für jede eingestufte Meldung automatisch einen Journaleintrag führen.

#### Scenario: Eintrag nach Triage
- **WHEN** der Chef Nachrichtendienst eine Meldung einstuft
- **THEN** besteht ein Journaleintrag mit Nummer, Zeit, Absender, Empfänger, Betreff und Einstufung

### Requirement: Chronologische Anzeige
Das System SHALL das Journal chronologisch nach Ereigniszeit oder wahlweise nach Erfassungszeit anzeigen.

#### Scenario: Sortierung wechseln
- **WHEN** eine Funktion von Ereigniszeit auf Erfassungszeit wechselt
- **THEN** ordnet das System die Einträge entsprechend neu

### Requirement: Unveränderliches Journal
Das System SHALL Journaleinträge weder löschen noch überschreiben und Korrekturen als neue Fassung mit Verweis führen.

#### Scenario: Korrektur
- **WHEN** eine Meldung korrigiert wird
- **THEN** zeigt das Journal die neue Fassung und kennzeichnet die frühere als ersetzt

### Requirement: Filter und Suche im Journal
Das System SHALL das Journal nach Einstufung, Typ, Richtung, Absender, Empfänger, Kanal, Zeitraum und Stichwort filtern lassen.

#### Scenario: Filter nach Schlüsselnachrichten
- **WHEN** eine Funktion nach Schlüsselnachrichten filtert
- **THEN** zeigt das Journal nur diese

### Requirement: Verweis auf Meldung
Das System SHALL jeden Journaleintrag mit der zugehörigen Meldung samt Kette verknüpfen.

#### Scenario: Eintrag öffnen
- **WHEN** eine Funktion einen Journaleintrag öffnet
- **THEN** sieht sie die vollständige Meldung und deren Kette

### Requirement: Sicht nach Funktion
Das System SHALL das vollständige Journal dem Chef Nachrichtendienst, C Lage, Adjutant und SC zeigen und den übrigen Funktionen nur Einträge ihrer zugewiesenen und eigenen Meldungen.

#### Scenario: Eingeschränkte Sicht
- **WHEN** die Funktion Kanzlei das Journal öffnet
- **THEN** enthält es nur ihr zugewiesene und von ihr erfasste Meldungen
