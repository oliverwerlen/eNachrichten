## Purpose

Führt Zahlentafeln des Führungsstabs: Personen nach Ort und Zeit sowie Verpflegungsbestand pro Formation.

## ADDED Requirements

### Requirement: Tafel Evakuationen
Das System SHALL eine Tafel Evakuationen mit Zeit, Ort/Sektor und den Kategorien Patienten, Obdachlose, Evakuierte, Vermisste, Tote und Andere führen.

#### Scenario: Zählung erfassen
- **WHEN** eine Meldung 3 Verletzte im Sektor B nennt und der Chef den Vorschlag bestätigt
- **THEN** zeigt die Tafel für Sektor B und den Zeitpunkt 3 Patienten

### Requirement: Fortschreibung pro Ort und Zeit
Das System SHALL Zählungen pro Ort/Sektor fortschreiben und dabei frühere Stände erhalten.

#### Scenario: Neue Zählung
- **WHEN** für Sektor B eine neue Zählung eingetragen wird
- **THEN** zeigt die Tafel den aktuellen Stand und der frühere Stand bleibt im Verlauf einsehbar

### Requirement: Summen
Das System SHALL pro Kategorie die Summe über alle Orte des aktuellen Standes anzeigen.

#### Scenario: Summenzeile
- **WHEN** die Tafel mehrere Sektoren enthält
- **THEN** zeigt eine Summenzeile pro Kategorie die Gesamtzahl

### Requirement: Tafel Verpflegung
Das System SHALL eine Tafel Verpflegung mit dem Bestand pro Formation/Einheit (Führungsstab, Polizei, Feuerwehr, Sanität, Techn. Dienste, Zivilschutz, Armee, Obdachlose) führen.

#### Scenario: Bestand erfassen
- **WHEN** die Funktion Logistik den Bestand für die Feuerwehr einträgt
- **THEN** zeigt die Tafel den Bestand in der Spalte Feuerwehr

### Requirement: Automatisches Total
Das System SHALL für jede Zeile der Verpflegungstafel das Total automatisch berechnen.

#### Scenario: Totalberechnung
- **WHEN** Werte in mehreren Spalten geändert werden
- **THEN** wird das Total sofort neu berechnet

### Requirement: Vorbefüllung und Anpassung
Das System SHALL Zahlen aus Meldungen als Vorschlag vorausfüllen und anpassbar halten.

#### Scenario: Zahl korrigieren
- **WHEN** der Chef einen vorgeschlagenen Wert ändert
- **THEN** wird die Änderung gespeichert und protokolliert

### Requirement: Verweis auf Ursprungsmeldung
Das System SHALL jede Zählung mit ihrer Ursprungsmeldung verknüpfen.

#### Scenario: Herkunft öffnen
- **WHEN** eine Funktion bei einer Zählung die Herkunft öffnet
- **THEN** wird die Meldung mit Kette angezeigt

### Requirement: Verbindung zur Karte
Das System SHALL die Personenzahlen eines Sektors beim zugehörigen Schadengebiet auf der Karte verfügbar machen.

#### Scenario: Anzeige bei Schadengebiet
- **WHEN** ein Schadengebiet mit Sektor B verknüpft ist
- **THEN** zeigt die Karte die aktuellen Personenzahlen von Sektor B
