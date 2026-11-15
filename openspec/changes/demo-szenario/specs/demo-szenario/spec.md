## Purpose

Stellt ein fiktives, durchgehendes Beispielereignis bereit, mit dem alle Bereiche des Prototyps geprüft und vorgeführt werden können.

## ADDED Requirements

### Requirement: Fiktives Ereignis
Das System SHALL ein fiktives Demo-Ereignis mit Bezeichnung, Ort im Lötschental und Beginn bereitstellen.

#### Scenario: Demo laden
- **WHEN** der Prototyp mit dem Demo-Szenario gestartet wird
- **THEN** ist das Demo-Ereignis aktiv und vorausgewählt

### Requirement: Ausschliesslich fiktive Daten
Das System SHALL im Demo-Szenario ausschliesslich erfundene Meldungen, Personen und Organisationen verwenden.

#### Scenario: Keine realen Daten
- **WHEN** das Szenario geladen wird
- **THEN** enthält es keine realen Personendaten

### Requirement: Abdeckung der Meldungen
Das System SHALL im Szenario alle Meldungstypen und Kanäle sowie Schlüsselnachrichten und Rohinformationen enthalten.

#### Scenario: Typen vorhanden
- **WHEN** das Szenario geladen ist
- **THEN** enthält es mindestens eine Meldung je Typ und Kanal

### Requirement: Abdeckung der Ketten
Das System SHALL im Szenario Ketten mit Auftrag und Vollzug, Anfrage und Antwort sowie Rückfragen enthalten.

#### Scenario: Offene und abgeschlossene Ketten
- **WHEN** das Szenario geladen ist
- **THEN** enthält es abgeschlossene Ketten und offene mit überfälliger Frist

### Requirement: Abdeckung von Tafeln und Karte
Das System SHALL im Szenario Einträge in allen neun Tafeln und Objekte auf der Lagekarte enthalten, mit Verweis auf ihre Meldungen.

#### Scenario: Tafeln gefüllt
- **WHEN** das Szenario geladen ist
- **THEN** enthält jede Tafel mindestens einen Eintrag

### Requirement: Abdeckung der Funktionen
Das System SHALL im Szenario alle neun internen Funktionen mit zugewiesenen Personen und Meldungen enthalten.

#### Scenario: Postfächer gefüllt
- **WHEN** das Szenario geladen ist
- **THEN** enthält jedes Postfach mindestens eine zugewiesene Meldung

### Requirement: Rapporte im Szenario
Das System SHALL im Szenario einen abgeschlossenen Rapport mit Protokoll und einen vorbereiteten, noch nicht gehaltenen Rapport enthalten.

#### Scenario: Rapportdaten
- **WHEN** das Szenario geladen ist
- **THEN** ist ein Rapport mit Protokoll abrufbar und für den nächsten Rapport sind Änderungen seit dem letzten sichtbar

### Requirement: Zurücksetzbar
Das System SHALL das Demo-Szenario auf den Ausgangszustand zurücksetzen können.

#### Scenario: Zurücksetzen
- **WHEN** eine berechtigte Funktion das Szenario zurücksetzt
- **THEN** wird der Ausgangszustand wiederhergestellt
