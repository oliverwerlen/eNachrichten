## Purpose

Erfasst Meldungen im Führungsstab entsprechend dem Meldezettel. Die Meldung ist die einzige Arbeitseinheit, aus der alle Ablagen, Tafeln und die Karte gespeist werden.

## ADDED Requirements

### Requirement: Meldungskopf erfassen
Das System SHALL für jede Meldung Richtung (Eingang oder Ausgang), Absender, Empfänger, Datum, Zeit und Meldungsnummer erfassen.

#### Scenario: Eingehende Meldung
- **WHEN** eine Funktion eine Meldung mit Richtung "Eingang" und Absender "Feuerwehr" erfasst
- **THEN** wird die Meldung mit Datum, Zeit und automatischer Nummer gespeichert

#### Scenario: Richtung fehlt
- **WHEN** eine Meldung ohne Richtung gespeichert werden soll
- **THEN** lehnt das System das Speichern ab

### Requirement: Kanal und Meldungstyp
Das System SHALL für jede Meldung einen Kanal (Telefon, Fax, Funk, Message, E-Mail, Kurier oder frei wählbar) und einen Meldungstyp (Mitteilung, Nachricht, Anfrage, Antwort, Auftrag, Vollzug oder frei wählbar) erfassen.

#### Scenario: Typ und Kanal wählen
- **WHEN** eine Funktion Kanal "Funk" und Typ "Auftrag" wählt
- **THEN** speichert das System beide Angaben mit der Meldung

#### Scenario: Freier Eintrag
- **WHEN** eine Funktion einen nicht vordefinierten Kanal eingibt
- **THEN** wird der Wert übernommen und für spätere Erfassungen angeboten

### Requirement: Betreff und Inhalt mit Frageschema
Das System SHALL Betreff und Meldungsinhalt erfassen und die Erfassung durch das Frageschema (Wann, Wer, Tut was, Wie, Wo, Wie ist die Umwelt) führen.

#### Scenario: Geführte Eingabe
- **WHEN** eine Funktion den Inhalt erfasst
- **THEN** stehen die sechs Fragen als Eingabehilfe zur Verfügung und der Inhalt wird als zusammenhängender Text gespeichert

#### Scenario: Frageschema nicht ausgefüllt
- **WHEN** einzelne Fragen unbeantwortet bleiben
- **THEN** kann die Meldung trotzdem gespeichert werden

### Requirement: Ereigniszeit und Erfassungszeit
Das System SHALL für jede Meldung die Ereigniszeit (wann geschah es) und die Erfassungszeit (wann wurde erfasst) getrennt speichern.

#### Scenario: Nachträgliche Erfassung
- **WHEN** eine Funktion eine Meldung mit einer früheren Ereigniszeit erfasst
- **THEN** werden beide Zeiten unterschieden gespeichert und angezeigt

### Requirement: Visum des Meldungsverfassers
Das System SHALL beim Speichern einer Meldung den Meldungsverfasser als Visum festhalten.

#### Scenario: Automatisches Visum
- **WHEN** eine angemeldete Funktion eine Meldung speichert
- **THEN** enthält die Meldung Person, Funktion und Zeitpunkt des Visums

### Requirement: Eindeutige Meldungsnummer
Das System SHALL jeder Meldung innerhalb des Ereignisses eine eindeutige, fortlaufende Nummer automatisch zuweisen.

#### Scenario: Nummernvergabe
- **WHEN** zwei Meldungen nacheinander gespeichert werden
- **THEN** erhalten sie aufeinanderfolgende, nicht wiederverwendete Nummern

### Requirement: Keine Überschreibung gespeicherter Meldungen
Das System SHALL gespeicherte Meldungen nie überschreiben. Änderungen entstehen als neue Fassung mit Verweis auf die vorherige Fassung.

#### Scenario: Meldung korrigieren
- **WHEN** eine Funktion den Inhalt einer gespeicherten Meldung korrigiert
- **THEN** entsteht eine neue Fassung, und die frühere Fassung bleibt einsehbar

### Requirement: Erfassung durch alle internen Funktionen
Das System SHALL allen internen Funktionen das Erfassen von Meldungen erlauben.

#### Scenario: Erfassung durch SC
- **WHEN** der SC eine Meldung erfasst
- **THEN** wird sie wie jede andere gespeichert und der Triage zugeführt
