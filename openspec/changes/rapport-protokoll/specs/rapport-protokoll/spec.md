## Purpose

Hält Verlauf und Beschlüsse jedes Rapports fest. Die Kanzlei führt das Protokoll, das nach Abschluss unveränderlich ist.

## ADDED Requirements

### Requirement: Protokoll pro Rapport
Das System SHALL zu jedem Rapport ein Protokoll mit Datum, Zeit, Rapporttyp, Teilnehmenden und Traktanden führen.

#### Scenario: Protokoll anlegen
- **WHEN** ein Rapport gestartet wird
- **THEN** besteht ein Protokoll zum Rapport, der Kanzlei zugewiesen

### Requirement: Protokollführung durch die Kanzlei
Das System SHALL das Protokoll durch die Funktion Kanzlei führen lassen.

#### Scenario: Eintrag verfassen
- **WHEN** die Kanzlei zu einem Traktandum einen Eintrag verfasst
- **THEN** wird er dem Traktandum zugeordnet

### Requirement: Vorschläge für Protokolleinträge
Das System SHALL Protokolleinträge aus den im Rapport entstandenen Beschlüssen, Anträgen, Aufträgen und Fragen vorschlagen, die die Kanzlei bestätigt oder anpasst.

#### Scenario: Beschluss übernehmen
- **WHEN** der SC einen Beschluss fasst
- **THEN** erscheint ein Protokollvorschlag, den die Kanzlei bestätigt

### Requirement: Verweis auf Meldungen
Das System SHALL Beschlüsse und Aufträge im Protokoll mit den daraus entstandenen Meldungen verknüpfen.

#### Scenario: Von Protokoll zu Meldung
- **WHEN** eine Funktion bei einem Beschluss die Meldung öffnet
- **THEN** wird die zugehörige Meldung mit Kette angezeigt

### Requirement: Abschluss und Unveränderlichkeit
Das System SHALL das Protokoll mit dem Abschluss durch die Kanzlei festschreiben und spätere Korrekturen nur als neue Fassung zulassen.

#### Scenario: Korrektur nach Abschluss
- **WHEN** die Kanzlei ein abgeschlossenes Protokoll korrigiert
- **THEN** entsteht eine neue Fassung, und die frühere bleibt einsehbar

### Requirement: Zugriff auf das Protokoll
Das System SHALL der Kanzlei Zugriff auf das Protokoll als ihr zugewiesene Aufgabe geben, ohne ihr den Zugang zur Lagepräsentation zu öffnen.

#### Scenario: Zugriff der Kanzlei
- **WHEN** die Kanzlei das Protokoll öffnet
- **THEN** sieht sie das Protokoll, nicht aber die Lagepräsentation des Rapportmodus
