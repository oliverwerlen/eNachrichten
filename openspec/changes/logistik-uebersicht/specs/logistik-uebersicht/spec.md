## Purpose

Gibt der Funktion Infrastruktur/Logistik eine Übersichtsseite über Unterkünfte, Verpflegung, Obdachlose und ihre offenen Aufgaben.

## ADDED Requirements

### Requirement: Übersichtsseite Logistik
Das System SHALL der Funktion Infrastruktur/Logistik eine Übersichtsseite mit ihren Verantwortungsbereichen bereitstellen.

#### Scenario: Seite öffnen
- **WHEN** die Funktion Logistik die Übersicht öffnet
- **THEN** zeigt die Seite Unterkünfte, Verpflegung, Obdachlose und offene Aufträge

### Requirement: Unterkünfte
Das System SHALL Unterkünfte mit Standort, Plätzen, Belegung und Kontakt führen.

#### Scenario: Belegung ändern
- **WHEN** die Logistik die Belegung einer Unterkunft ändert
- **THEN** zeigt die Übersicht die freien Plätze

### Requirement: Verpflegung
Das System SHALL den Verpflegungsbestand pro Formation aus der Verpflegungstafel anzeigen.

#### Scenario: Bestand sehen
- **WHEN** die Übersicht geöffnet wird
- **THEN** zeigt sie die aktuellen Bestände und das Total

### Requirement: Obdachlose und Evakuierte
Das System SHALL die Zahlen Obdachlose und Evakuierte nach Ort/Sektor aus der Evakuationstafel anzeigen.

#### Scenario: Anzeige nach Sektor
- **WHEN** die Übersicht geöffnet wird
- **THEN** zeigt sie die aktuellen Zahlen pro Sektor

### Requirement: Offene Aufträge und Hilfegesuche
Das System SHALL der Logistik die ihr zugewiesenen offenen Aufträge und Hilfegesuche mit Frist anzeigen.

#### Scenario: Offener Auftrag
- **WHEN** der Logistik ein Auftrag zugewiesen ist
- **THEN** erscheint er auf der Übersicht mit Frist und Status

### Requirement: Eingeschränkte Sicht
Das System SHALL der Logistik in der Übersicht nur Daten zeigen, die ihr nach den Sichtrechten zustehen.

#### Scenario: Fremde Meldung
- **WHEN** eine Meldung der Logistik nicht zugewiesen ist
- **THEN** erscheint sie nicht in ihrer Übersicht
