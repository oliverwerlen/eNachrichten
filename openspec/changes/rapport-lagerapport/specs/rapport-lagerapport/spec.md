## Purpose

Führt den Stab durch den Lagerapport und stellt alle wesentlichen Informationen seit dem letzten Rapport grafisch dar.

## ADDED Requirements

### Requirement: Rapportmodus Lagerapport
Das System SHALL einen Rapportmodus mit dem Rapporttyp Lagerapport bereitstellen, der nur dem Chef Nachrichtendienst, C Lage, Adjutant und SC zugänglich ist.

#### Scenario: Rapport starten
- **WHEN** der Adjutant einen Lagerapport startet
- **THEN** öffnet sich die Rapportleitung mit der Traktandenliste

#### Scenario: Nicht berechtigt
- **WHEN** eine andere Funktion den Rapportmodus öffnen will
- **THEN** verweigert das System den Zugriff

### Requirement: Ablauf des Lagerapports
Das System SHALL den Ablauf Rapportziel, Orientierung, Konzepte, Anträge, Aufträge, Fragen, Kommunikation und Nächster Rapport als Traktandenliste führen.

#### Scenario: Traktanden in Reihenfolge
- **WHEN** der Adjutant das Rapportziel abschliesst
- **THEN** wechselt die Ansicht zur Orientierung

### Requirement: Verantwortliche je Traktandum
Das System SHALL je Traktandum die vorgesehenen Beteiligten anzeigen: Rapportziel SC, Orientierung C Lage / SC / alle, Konzepte Stab, Anträge SC / Stab, Aufträge Kontrolle / SC, Fragen alle, Kommunikation Information / SC.

#### Scenario: Anzeige
- **WHEN** das Traktandum Anträge aktiv ist
- **THEN** werden SC und Stab als Beteiligte genannt

### Requirement: Rapportleitung durch den Adjutanten
Das System SHALL dem Adjutanten Traktandenliste, Zeit, Weiterschalten und Rapportabschluss bereitstellen.

#### Scenario: Weiterschalten
- **WHEN** der Adjutant zum nächsten Traktandum schaltet
- **THEN** zeigt die Ansicht das nächste Traktandum mit der passenden Darstellung

### Requirement: Vortragssicht des C Lage
Das System SHALL dem C Lage für die Orientierung eine Vortragssicht mit dem Lagebild bereitstellen.

#### Scenario: Orientierung
- **WHEN** das Traktandum Orientierung aktiv ist
- **THEN** zeigt die Vortragssicht Karte und Änderungen seit dem letzten Rapport

### Requirement: Grafische Darstellung seit dem letzten Rapport
Das System SHALL alle wesentlichen Informationen seit dem letzten Rapport grafisch darstellen (Karte, Tafeländerungen, Schlüsselnachrichten, Überfälliges).

#### Scenario: Änderungen auf der Karte
- **WHEN** die Orientierung beginnt
- **THEN** hebt die Karte neue und geänderte Objekte seit dem letzten Rapport hervor

### Requirement: Vorschlag des Wesentlichen
Das System SHALL dem C Lage vor Rapportbeginn einen Vorschlag der wesentlichen Informationen machen, den er auswählen und ergänzen kann.

#### Scenario: Auswahl treffen
- **WHEN** der C Lage einen vorgeschlagenen Punkt abwählt
- **THEN** erscheint er nicht im Rapport

### Requirement: Beschlüsse als Meldungen
Das System SHALL Beschlüsse, Aufträge, Anträge und Fragen aus dem Rapport als Meldungen erfassen lassen, die den normalen Fluss durchlaufen.

#### Scenario: Auftrag im Rapport
- **WHEN** der SC im Rapport einen Auftrag erteilt
- **THEN** wird eine Meldung vom Typ Auftrag erzeugt und der Triage zugeführt

### Requirement: Nächster Rapport und Rapportzeitpunkt
Das System SHALL beim Rapportabschluss den nächsten Rapport in die Zeitplanung eintragen und den Rapportzeitpunkt als Bezug für die nächste Änderungsansicht speichern.

#### Scenario: Abschluss
- **WHEN** der Adjutant den Rapport mit einem nächsten Termin abschliesst
- **THEN** erscheint der Termin in der Zeitplanung und der Zeitpunkt ist gespeichert
