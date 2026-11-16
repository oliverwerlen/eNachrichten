## Purpose

Führt die vier Vorgangslisten der Führungswand, jede mit Frist, Zuständigem und Status, und speist sie aus Meldungen.

## ADDED Requirements

### Requirement: Auftragskontrolle
Das System SHALL eine Auftragskontrolle mit Nummer, Auftragszeit, Was-Wo-Womit, Priorität, Wer, Bis wann und Status führen.

#### Scenario: Auftrag erscheint
- **WHEN** der Chef Nachrichtendienst einen vorgeschlagenen Eintrag zu einem Auftrag bestätigt
- **THEN** steht der Auftrag mit allen Spalten in der Auftragskontrolle

### Requirement: Sofortmassnahmen als eigene Tafel
Das System SHALL Sofortmassnahmen in einer eigenen Tafel mit Auftragszeit, Was-Wo, Wer, Bis wann und Status führen, getrennt von der Auftragskontrolle.

#### Scenario: Sofortmassnahme erfassen
- **WHEN** eine Meldung als Sofortmassnahme bestätigt wird
- **THEN** erscheint sie in der Tafel Sofortmassnahmen und nicht in der Auftragskontrolle

### Requirement: Hilfegesuche an den Stab
Das System SHALL eine Tafel für Hilfegesuche an den Stab mit Antragsteller, Was-Wo-Wieviel, Verantwortlich, Bis wann und Status führen.

#### Scenario: Gesuch einer Gegenstelle
- **WHEN** eine eingehende Anfrage der Feuerwehr als Hilfegesuch bestätigt wird
- **THEN** erscheint sie mit Antragsteller Feuerwehr und der verantwortlichen Funktion

### Requirement: Hilfegesuche des Stabes
Das System SHALL eine Tafel für Hilfegesuche des Stabes mit Ausgangszeit, Was-Wo-Wieviel, Beantragt bei, Termin und Bewilligt führen.

#### Scenario: Gesuch an Kanton
- **WHEN** der Stab ein Gesuch an das Kantonale Führungsorgan stellt
- **THEN** erscheint es mit "Beantragt bei: Kantonales Führungsorgan" und leerem Feld "Bewilligt"

#### Scenario: Bewilligung eintragen
- **WHEN** die Antwort mit Bewilligung eintrifft und eingestuft wird
- **THEN** wird "Bewilligt" mit Zeitpunkt gesetzt

### Requirement: Vorbefüllung aus Meldungen
Das System SHALL Einträge aus Meldungen vorausfüllen und dem Nachrichtendienst zur Bestätigung oder Anpassung anbieten.

#### Scenario: Anpassen
- **WHEN** der Chef ein vorausgefülltes Feld ändert
- **THEN** wird die Änderung gespeichert und protokolliert

### Requirement: Status aus Meldungskette
Das System SHALL den Status eines Eintrags aus der zugehörigen Meldungskette ableiten (offen, in Bearbeitung, abgeschlossen).

#### Scenario: Vollzug trifft ein
- **WHEN** zu einem Auftrag ein Vollzug eingestuft wird
- **THEN** wechselt der Eintrag auf "abgeschlossen"

### Requirement: Priorität und Frist
Das System SHALL Priorität und Frist ("Bis wann") je Eintrag führen und Einträge nach beiden sortieren lassen.

#### Scenario: Sortierung
- **WHEN** eine Funktion die Auftragskontrolle nach Frist sortiert
- **THEN** stehen die Einträge mit der frühesten Frist oben

### Requirement: Verweis auf Ursprungsmeldung
Das System SHALL jede Zeile mit ihrer Ursprungsmeldung verknüpfen.

#### Scenario: Herkunft öffnen
- **WHEN** eine Funktion bei einer Zeile die Herkunft öffnet
- **THEN** wird die Meldung mit Kette angezeigt

### Requirement: Pflege durch den Nachrichtendienst
Das System SHALL die Tafeln durch den Nachrichtendienst führen lassen und den übrigen Funktionen die Ansicht nach Sichtrechten erlauben.

#### Scenario: Änderung durch Fremde
- **WHEN** eine nicht berechtigte Funktion einen Eintrag ändern will
- **THEN** verweigert das System die Änderung
