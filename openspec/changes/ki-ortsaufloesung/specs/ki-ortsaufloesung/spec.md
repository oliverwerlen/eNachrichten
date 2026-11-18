## Purpose

Erkennt Ortsangaben in Meldungen, löst sie zu Positionen auf der Karte auf und schlägt dem Nachrichtendienst Kartenobjekte vor. Die Bestätigung bleibt beim Menschen.

## ADDED Requirements

### Requirement: Ortsangaben erkennen
Das System SHALL im Meldungstext Ortsangaben erkennen und im Text hervorheben.

#### Scenario: Flurname erkannt
- **WHEN** eine Meldung "Lawine bei der Alp Fafleralp" enthält
- **THEN** hebt das System "Fafleralp" als Ortsangabe hervor

#### Scenario: Keine Ortsangabe
- **WHEN** der Text keine Ortsangabe enthält
- **THEN** erzeugt das System keinen Kartenvorschlag

### Requirement: Auflösung zur Kartenposition
Das System SHALL erkannte Ortsangaben zu einer Position auf der swisstopo-Karte auflösen.

#### Scenario: Eindeutiger Ort
- **WHEN** eine Ortsangabe genau einem Ort entspricht
- **THEN** zeigt das System die Position auf der Karte als Vorschlag

### Requirement: Mehrdeutige Orte
Das System SHALL bei mehrdeutigen Ortsangaben mehrere Kandidaten zur Auswahl anbieten und keinen automatisch wählen.

#### Scenario: Gleicher Name
- **WHEN** ein Ortsname an mehreren Stellen vorkommt
- **THEN** zeigt das System die Kandidaten mit Lage und lässt die Funktion wählen

### Requirement: Anzeige der Sicherheit
Das System SHALL zu jeder Auflösung angeben, wie sicher sie ist und ob es sich um einen Punkt oder ein Gebiet handelt.

#### Scenario: Unsichere Auflösung
- **WHEN** die Auflösung unsicher ist
- **THEN** kennzeichnet das System den Vorschlag als unsicher

### Requirement: Nicht auflösbare Orte
Das System SHALL bei nicht auflösbaren Ortsangaben darauf hinweisen und das manuelle Setzen auf der Karte ermöglichen.

#### Scenario: Unbekannter Ort
- **WHEN** ein Ort nicht gefunden wird
- **THEN** weist das System darauf hin, und die Funktion kann die Position selbst auf der Karte setzen

### Requirement: Koordinatenangaben
Das System SHALL im Text genannte Koordinaten übernehmen und die Position ohne Auflösung vorschlagen.

#### Scenario: Koordinaten im Text
- **WHEN** eine Meldung Landeskoordinaten nennt
- **THEN** schlägt das System genau diese Position vor

### Requirement: Kartenvorschlag mit Symbol und Zeit
Das System SHALL aus Ort und Sachverhalt der Meldung einen Kartenvorschlag mit Symbol, Position und Ereigniszeit erzeugen, vorausgefüllt und anpassbar.

#### Scenario: Vorschlag anpassen
- **WHEN** der Chef Nachrichtendienst Symbol oder Position ändert
- **THEN** wird die Anpassung gespeichert und protokolliert

### Requirement: Bestätigung vor Eintrag
Das System SHALL ein Objekt erst nach Bestätigung durch den Chef Nachrichtendienst auf der Lagekarte führen.

#### Scenario: Ohne Bestätigung
- **WHEN** ein Vorschlag nicht bestätigt wird
- **THEN** erscheint kein Objekt auf der Karte

#### Scenario: Bestätigung
- **WHEN** der Chef einen Vorschlag bestätigt
- **THEN** erscheint das Objekt mit Verweis auf die Meldung

### Requirement: Verknüpfung von Text und Karte
Das System SHALL Ortsangabe im Text und Kartenobjekt wechselseitig verknüpfen.

#### Scenario: Vom Text zur Karte
- **WHEN** eine Funktion auf die Ortsangabe klickt
- **THEN** zentriert die Karte auf die Position

### Requirement: Wiederverwendung des Ortes
Das System SHALL den aufgelösten Ort als Standort für Wetteransichten und für Ort/Sektor in den Tafeln anbieten.

#### Scenario: Ort für Wetter
- **WHEN** ein Ort aufgelöst und bestätigt ist
- **THEN** kann er als beobachteter Standort für die Prognose gewählt werden

### Requirement: Kennzeichnung und Protokoll
Das System SHALL maschinell erzeugte Vorschläge deutlich als solche kennzeichnen und angenommene, geänderte und verworfene Vorschläge mit Person und Zeit protokollieren.

#### Scenario: Verwerfen
- **WHEN** eine Funktion einen Vorschlag verwirft
- **THEN** wird das protokolliert und der Vorschlag nicht erneut gemacht
