## Purpose

Definiert die internen Funktionen des Führungsstabs, ihre Zuweisung an Personen pro Ereignis und was jede Funktion sehen und tun darf.

## ADDED Requirements

### Requirement: Katalog der internen Funktionen
Das System SHALL die Funktionen Chef Nachrichtendienst, Mitarbeitende Nachrichtendienst, C Lage, Adjutant, SC (Stabschef), C Info, Einsatz, Infrastruktur/Logistik und Kanzlei kennen.

#### Scenario: Funktionen verfügbar
- **WHEN** eine Funktion zugewiesen werden soll
- **THEN** stehen genau diese neun Funktionen zur Auswahl

### Requirement: Zuweisung pro Ereignis
Das System SHALL Funktionen pro Ereignis Personen zuweisen, wobei eine Person mehrere Funktionen halten kann.

#### Scenario: Person mit mehreren Funktionen
- **WHEN** eine Person als C Lage und als Chef Nachrichtendienst zugewiesen wird
- **THEN** hat sie die Rechte und Ansichten beider Funktionen

#### Scenario: Wechsel mitten im Ereignis
- **WHEN** eine Funktion einer anderen Person zugewiesen wird
- **THEN** gelten die Rechte sofort für die neue Person und der Wechsel ist mit Zeitpunkt protokolliert

### Requirement: Vollsicht für Führungsfunktionen
Das System SHALL dem Chef Nachrichtendienst, C Lage, Adjutant und SC alle Meldungen des gewählten Ereignisses anzeigen.

#### Scenario: Vollsicht
- **WHEN** der SC das Ereignis öffnet
- **THEN** sieht er alle Meldungen, auch solche, die nicht an ihn adressiert sind

### Requirement: Eingeschränkte Sicht übrige Funktionen
Das System SHALL Mitarbeitenden Nachrichtendienst, C Info, Einsatz, Infrastruktur/Logistik und Kanzlei nur die ihnen zugewiesenen und selbst erfassten Meldungen anzeigen.

#### Scenario: Nicht zugewiesene Meldung
- **WHEN** die Funktion Einsatz die Meldungsliste öffnet
- **THEN** enthält sie nur Meldungen, die ihr zugewiesen wurden oder die sie selbst erfasst hat

### Requirement: Rapportzugang
Das System SHALL den Rapportmodus (Lagepräsentation und Inforapport-Übersicht) nur dem Chef Nachrichtendienst, C Lage, Adjutant und SC zugänglich machen.

#### Scenario: Zugriff verweigert
- **WHEN** die Funktion Logistik den Rapportmodus öffnen will
- **THEN** verweigert das System den Zugriff

### Requirement: Meldungen erfassen für alle internen Funktionen
Das System SHALL jeder internen Funktion das Erfassen von Meldungen über eine ihrer Funktion angepasste Oberfläche erlauben.

#### Scenario: Erfassung durch Logistik
- **WHEN** die Funktion Logistik eine Meldung erfasst
- **THEN** wird sie wie jede andere Meldung der Triage zugeführt

### Requirement: Funktionsspezifische Oberflächen
Das System SHALL jeder Funktion eine Startansicht bereitstellen, die auf ihre Aufgaben ausgerichtet ist.

#### Scenario: Startansicht der Logistik
- **WHEN** die Funktion Logistik das System öffnet
- **THEN** zeigt die Startansicht zugewiesene Meldungen und die Logistik-Übersicht
