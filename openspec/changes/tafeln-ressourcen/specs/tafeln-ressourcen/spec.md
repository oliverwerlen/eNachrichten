## Purpose

Führt die verfügbaren und die eingesetzten Mittel des Einsatzes und bildet den Wechsel zwischen beiden Zuständen nachvollziehbar ab.

## ADDED Requirements

### Requirement: Tafel Verfügbare Mittel
Das System SHALL eine Tafel Verfügbare Mittel mit Organisation, Kontaktperson, Mittel personell, Mittel materiell und Ab wann führen.

#### Scenario: Mittel melden
- **WHEN** eine Meldung bereitstehende Mittel einer Gegenstelle nennt und der Chef den vorgeschlagenen Eintrag bestätigt
- **THEN** erscheint die Zeile in Verfügbare Mittel

### Requirement: Tafel Eingesetzte Mittel
Das System SHALL eine Tafel Eingesetzte Mittel mit Organisation, Einsatzort, Mittel personell, Mittel materiell und Bis wann führen.

#### Scenario: Mittel im Einsatz
- **WHEN** ein Auftrag verfügbare Mittel an einen Einsatzort bindet und der Chef bestätigt
- **THEN** erscheint die Zeile in Eingesetzte Mittel mit Einsatzort und Frist

### Requirement: Übergang verfügbar zu eingesetzt
Das System SHALL beim Einsatz von Mitteln diese in der Tafel Verfügbare Mittel abziehen und in Eingesetzte Mittel aufnehmen.

#### Scenario: Teileinsatz
- **WHEN** von 12 verfügbaren Angehörigen 8 eingesetzt werden
- **THEN** zeigt Verfügbare Mittel 4 und Eingesetzte Mittel 8

### Requirement: Rückkehr in die Verfügbarkeit
Das System SHALL bei Abschluss eines Einsatzes die Mittel auf Bestätigung hin wieder als verfügbar führen.

#### Scenario: Einsatz beendet
- **WHEN** ein Vollzug mit Rückmeldung eingestuft und bestätigt wird
- **THEN** wechseln die Mittel zurück in Verfügbare Mittel mit neuem "Ab wann"

### Requirement: Vorbefüllung aus Meldungen
Das System SHALL Einträge aus Meldungen vorausfüllen und anpassbar halten.

#### Scenario: Anpassen
- **WHEN** der Chef eine vorausgefüllte Mengenangabe korrigiert
- **THEN** wird die Korrektur gespeichert und protokolliert

### Requirement: Organisationen aus dem Adressbuch
Das System SHALL für Organisation und Kontaktperson die Einträge des Adressbuchs anbieten.

#### Scenario: Auswahl
- **WHEN** eine Funktion einen Eintrag erfasst
- **THEN** kann sie Organisation und Kontaktperson aus dem Adressbuch wählen

### Requirement: Verweis auf Ursprungsmeldung
Das System SHALL jede Zeile mit ihrer Ursprungsmeldung verknüpfen.

#### Scenario: Herkunft öffnen
- **WHEN** eine Funktion bei einer Zeile die Herkunft öffnet
- **THEN** wird die Meldung mit Kette angezeigt

### Requirement: Pflege durch den Nachrichtendienst
Das System SHALL die Tafeln durch den Nachrichtendienst führen lassen und der Funktion Einsatz die Ansicht erlauben.

#### Scenario: Ansicht für Einsatz
- **WHEN** die Funktion Einsatz die Tafeln öffnet
- **THEN** sieht sie die Mittel gemäss ihren Sichtrechten, ändert sie aber nicht ohne Berechtigung
