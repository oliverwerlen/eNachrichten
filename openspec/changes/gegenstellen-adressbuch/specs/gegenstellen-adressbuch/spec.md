## Purpose

Führt die externen Organisationen, mit denen der Führungsstab Meldungen austauscht, mit Kontaktpersonen und Kanälen. Gegenstellen sind Adressaten und Absender, keine Systembenutzer.

## ADDED Requirements

### Requirement: Gegenstelle erfassen
Das System SHALL das Erfassen einer Gegenstelle mit Organisationsname, Kontaktperson und mindestens einem Kanal erlauben.

#### Scenario: Gegenstelle anlegen
- **WHEN** eine Funktion Polizei mit Kontaktperson und Funkkanal erfasst
- **THEN** ist die Gegenstelle im Adressbuch auffindbar

#### Scenario: Angaben fehlen
- **WHEN** eine Gegenstelle ohne Organisationsnamen gespeichert werden soll
- **THEN** lehnt das System das Speichern ab

### Requirement: Vordefinierte Gegenstellen
Das System SHALL mit den Gegenstellen Kantonales Führungsorgan (C RFO), Polizei, Feuerwehr, Sanität, Zivilschutz und Technischer Betrieb vorbelegt sein.

#### Scenario: Erstanwendung
- **WHEN** das Adressbuch erstmals geöffnet wird
- **THEN** enthält es diese sechs Gegenstellen

### Requirement: Kanäle pro Gegenstelle
Das System SHALL pro Gegenstelle mehrere Kanäle (Telefon, Funk, E-Mail, Kurier, Message, Fax) mit Kontaktangabe speichern.

#### Scenario: Mehrere Kanäle
- **WHEN** eine Gegenstelle mit Telefon und Funk erfasst wird
- **THEN** stehen beide Kanäle bei der Auswahl für eine Meldung zur Verfügung

### Requirement: Auswahl in Meldungen und Tafeln
Das System SHALL Gegenstellen als Absender, Empfänger, Antragsteller, Beauftragte und Mittelgeber auswählbar machen.

#### Scenario: Auswahl als Absender
- **WHEN** eine Funktion eine eingehende Meldung erfasst
- **THEN** kann sie die Gegenstelle aus dem Adressbuch als Absender wählen

### Requirement: Keine Anmeldung für Gegenstellen
Das System SHALL Gegenstellen weder Anmeldung noch Postfach bereitstellen.

#### Scenario: Gegenstelle als Empfänger
- **WHEN** eine Meldung an eine Gegenstelle adressiert wird
- **THEN** wird sie im System erfasst und die Übermittlung erfolgt ausserhalb des Systems

### Requirement: Änderungen nachvollziehbar
Das System SHALL Änderungen an Gegenstellen protokollieren und bestehende Meldungen unverändert auf die Gegenstelle im Stand zum Erfassungszeitpunkt verweisen lassen.

#### Scenario: Kontaktperson wechselt
- **WHEN** die Kontaktperson einer Gegenstelle geändert wird
- **THEN** zeigen bestehende Meldungen weiterhin die Kontaktperson zum Zeitpunkt der Erfassung
