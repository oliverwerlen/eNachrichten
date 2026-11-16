## Purpose

Plant und zeigt den Führungsrhythmus des Stabes in einem Tages- und Wochenraster.

## ADDED Requirements

### Requirement: Tagesplanung
Das System SHALL eine Tagesplanung mit Stundenraster von 00:00 bis 23:00 und der Angabe Wer – Was führen.

#### Scenario: Eintrag in die Tagesplanung
- **WHEN** eine Funktion einen Rapport um 11:00 einträgt
- **THEN** erscheint der Eintrag im Stundenraster bei 11:00

### Requirement: Wochenplanung
Das System SHALL eine Wochenplanung von Montag bis Sonntag mit Datum führen.

#### Scenario: Eintrag in die Wochenplanung
- **WHEN** eine Funktion für Dienstag einen Besuch einträgt
- **THEN** erscheint er am Dienstag mit dem Datum

### Requirement: Eintragsarten
Das System SHALL die Eintragsarten Termin, Phase, Rapport, Gespräch, Führungstätigkeit, Beschluss, Information, Kontrolle und Einsatzbeginn unterscheiden.

#### Scenario: Art wählen
- **WHEN** eine Funktion die Art "Rapport" wählt
- **THEN** wird der Eintrag entsprechend gekennzeichnet

### Requirement: Vorbefüllung aus Meldungen und Rapport
Das System SHALL Einträge aus Meldungen und Rapportbeschlüssen vorausfüllen und anpassbar halten.

#### Scenario: Termin aus Meldung
- **WHEN** eine Meldung einen Termin nennt
- **THEN** schlägt das System einen Eintrag mit Datum, Zeit und Beteiligten vor

### Requirement: Wiederkehrende Einträge
Das System SHALL wiederkehrende Einträge (zum Beispiel tägliche Rapporte) erlauben.

#### Scenario: Täglicher Rapport
- **WHEN** ein Rapport täglich um 18:00 definiert wird
- **THEN** erscheint er an jedem Tag des Ereignisses

### Requirement: Nächster Rapport
Das System SHALL beim Abschluss eines Rapports den nächsten Rapport als Termin eintragen.

#### Scenario: Rapport schliessen
- **WHEN** der Adjutant den nächsten Rapport festlegt
- **THEN** erscheint der Termin in der Zeitplanung

### Requirement: Verweis auf Ursprung
Das System SHALL Einträge mit ihrer Ursprungsmeldung oder dem Rapport verknüpfen.

#### Scenario: Herkunft öffnen
- **WHEN** eine Funktion bei einem Eintrag die Herkunft öffnet
- **THEN** wird die Meldung oder der Rapport angezeigt
