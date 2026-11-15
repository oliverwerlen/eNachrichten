## Purpose

Das System unterstützt den Nachrichtendienst mit Vorschlägen aus Meldungen. Jeder Vorschlag wird vom Menschen bestätigt, angepasst oder verworfen.

## ADDED Requirements

### Requirement: Vorschläge statt automatischer Änderung
Das System SHALL Änderungen an Tafeln, Karte, Einstufung und Verteilung ausschliesslich als Vorschlag erzeugen und erst nach Bestätigung durch eine berechtigte Funktion anwenden.

#### Scenario: Vorschlag bestätigen
- **WHEN** der Chef Nachrichtendienst einen Tafelvorschlag bestätigt
- **THEN** wird der Eintrag erstellt, mit Verweis auf die Meldung

#### Scenario: Ohne Bestätigung
- **WHEN** ein Vorschlag nicht bestätigt wird
- **THEN** ändern sich Tafeln und Karte nicht

### Requirement: Vorschlag der Einstufung und Verteilung
Das System SHALL für eine neue Meldung eine Einstufung und eine Verteilung vorschlagen.

#### Scenario: Dringende Meldung
- **WHEN** eine Meldung Anzeichen einer Schlüsselnachricht enthält
- **THEN** schlägt das System diese Einstufung vor und der Chef entscheidet

### Requirement: Dublettenhinweis
Das System SHALL auf mögliche Dubletten hinweisen und den Vergleich der Meldungen zeigen.

#### Scenario: Ähnliche Meldung
- **WHEN** zwei Meldungen denselben Sachverhalt am selben Ort beschreiben
- **THEN** weist das System darauf hin und lässt sie verknüpfen oder getrennt lassen

### Requirement: Vorschläge für Karte und Tafeln
Das System SHALL aus Meldungen Vorschläge für Kartenobjekte und Einträge in den Tafeln erzeugen und vorausgefüllt anpassbar anzeigen.

#### Scenario: Vorausgefüllter Eintrag
- **WHEN** eine Meldung einen Auftrag mit Frist und Verantwortlichem enthält
- **THEN** wird ein Eintrag mit diesen Werten vorgeschlagen und lässt sich vor der Bestätigung ändern

### Requirement: Rapportentwurf
Das System SHALL einen Rapportentwurf aus den wesentlichen Änderungen vorschlagen.

#### Scenario: Entwurf
- **WHEN** der C Lage einen Rapport vorbereitet
- **THEN** erhält er einen Entwurf, den er ändern kann

### Requirement: Herkunft und Begründung
Das System SHALL zu jedem Vorschlag die Herkunftsmeldung und die Grundlage des Vorschlags anzeigen.

#### Scenario: Begründung anzeigen
- **WHEN** eine Funktion einen Vorschlag öffnet
- **THEN** sieht sie die Meldung und die Begründung

### Requirement: Protokollierung
Das System SHALL angenommene, geänderte und verworfene Vorschläge mit Person und Zeit protokollieren.

#### Scenario: Verwerfen
- **WHEN** eine Funktion einen Vorschlag verwirft
- **THEN** wird das protokolliert und der Vorschlag erscheint nicht erneut
