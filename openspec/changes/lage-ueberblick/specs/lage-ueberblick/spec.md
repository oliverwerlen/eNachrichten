## Purpose

Gibt Chef Nachrichtendienst, C Lage, Adjutant und SC jederzeit einen Gesamtüberblick über das Geschehen im Ereignis, mit Filter für das Relevante.

## ADDED Requirements

### Requirement: Gesamtsicht für Führungsfunktionen
Das System SHALL dem Chef Nachrichtendienst, C Lage, Adjutant und SC einen Lage-Überblick mit allen Meldungen des gewählten Ereignisses bereitstellen.

#### Scenario: Überblick öffnen
- **WHEN** der C Lage den Lage-Überblick öffnet
- **THEN** sieht er alle Meldungen des Ereignisses, auch jene, die nicht an ihn adressiert sind

### Requirement: Zugriff für andere Funktionen verweigern
Das System SHALL den Lage-Überblick den übrigen Funktionen nicht zugänglich machen.

#### Scenario: Nicht berechtigt
- **WHEN** die Funktion Kanzlei den Lage-Überblick öffnen will
- **THEN** verweigert das System den Zugriff

### Requirement: Relevanzfilter
Das System SHALL dem SC und dem Adjutant einen Relevanzfilter nach Einstufung, Thema, Ort, Absender, Funktion und Zeitraum bieten, ohne den Zugriff auf alle Meldungen zu entziehen.

#### Scenario: Filter setzen
- **WHEN** der SC nur Schlüsselnachrichten anzeigt
- **THEN** zeigt der Überblick diese und lässt sich mit einer Aktion wieder auf alle Meldungen erweitern

### Requirement: Gespeicherte Filter
Das System SHALL Filter pro Person speichern und wiederverwenden lassen.

#### Scenario: Filter wiederverwenden
- **WHEN** der Adjutant einen gespeicherten Filter wählt
- **THEN** wird er sofort angewendet

### Requirement: Hervorhebungen
Das System SHALL Schlüsselnachrichten, überfällige Einträge, offene Rückfragen und neue Änderungen auf Karte und Tafeln hervorheben.

#### Scenario: Neue Schlüsselnachricht
- **WHEN** eine Meldung als Schlüsselnachricht eingestuft wird
- **THEN** erscheint sie im Überblick hervorgehoben

### Requirement: Änderungen seit dem letzten Rapport
Das System SHALL die Änderungen seit dem Zeitpunkt des letzten Rapports als eigene Ansicht bereitstellen.

#### Scenario: Seit letztem Rapport
- **WHEN** der C Lage die Ansicht "seit letztem Rapport" wählt
- **THEN** zeigt das System neue Meldungen, Karten- und Tafeländerungen seit dem gespeicherten Rapportzeitpunkt

### Requirement: Lesender Zugriff
Das System SHALL das Mitlesen im Überblick vom Bearbeiten trennen, sodass das Lesen keine Zuständigkeit oder Aufgabe erzeugt.

#### Scenario: Mitlesen
- **WHEN** der SC eine nicht an ihn adressierte Meldung öffnet
- **THEN** wird sie nicht zu seiner Aufgabe und ändert ihren Status nicht
