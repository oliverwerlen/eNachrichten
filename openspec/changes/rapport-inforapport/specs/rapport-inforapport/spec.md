## Purpose

Der Inforapport ist ein kurzer Rapport mit Informationen für den mündlichen Vortrag. Er wird vom C Lage gehalten und vom Adjutanten geleitet.

## ADDED Requirements

### Requirement: Rapporttyp Inforapport
Das System SHALL im Rapportmodus den Rapporttyp Inforapport anbieten, zugänglich für Chef Nachrichtendienst, C Lage, Adjutant und SC.

#### Scenario: Inforapport starten
- **WHEN** der Adjutant einen Inforapport startet
- **THEN** zeigt das System die Informationsübersicht für den mündlichen Vortrag

#### Scenario: Nicht berechtigt
- **WHEN** eine andere Funktion den Inforapport öffnen will
- **THEN** verweigert das System den Zugriff

### Requirement: Stichwortliste statt Grafik
Das System SHALL im Inforapport die Informationen als knappe Stichwortliste ohne grafische Darstellung zeigen.

#### Scenario: Ansicht
- **WHEN** der C Lage den Inforapport hält
- **THEN** sieht er eine Liste der Informationen mit Zeit und Quelle, ohne Karte

### Requirement: Auswahl der Informationen
Das System SHALL dem C Lage Schlüsselnachrichten und Änderungen seit dem letzten Rapport vorschlagen und die Auswahl durch ihn erlauben.

#### Scenario: Information streichen
- **WHEN** der C Lage eine vorgeschlagene Information abwählt
- **THEN** erscheint sie nicht im Inforapport

### Requirement: Leitung durch den Adjutanten
Das System SHALL dem Adjutanten die Rapportleitung (Reihenfolge, Zeit, Abschluss) auch für den Inforapport bereitstellen.

#### Scenario: Abschluss
- **WHEN** der Adjutant den Inforapport abschliesst
- **THEN** wird der Rapportzeitpunkt gespeichert

### Requirement: Rückfragen und Aufträge als Meldungen
Das System SHALL Rückfragen und Aufträge aus dem Inforapport als Meldungen erfassen lassen, die den normalen Fluss durchlaufen.

#### Scenario: Rückfrage
- **WHEN** der SC im Inforapport eine Rückfrage stellt
- **THEN** wird eine Meldung vom Typ Anfrage erzeugt und der Triage zugeführt
