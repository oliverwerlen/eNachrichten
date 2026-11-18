## Purpose

Hilft dem Nachrichtendienst, schwer verständliche Meldungen zu klären. Die KI macht Vorschläge, die Originalmeldung bleibt unverändert, und der Mensch entscheidet.

## ADDED Requirements

### Requirement: Unklare Stellen markieren
Das System SHALL unklare, unvollständige oder widersprüchliche Stellen einer Meldung erkennen und im Meldungstext markieren.

#### Scenario: Unklare Angabe
- **WHEN** eine Meldung "Brücke gesperrt, glaub bei der Alp" enthält
- **THEN** markiert das System die Angabe als unklar und nennt den Grund

#### Scenario: Widerspruch
- **WHEN** eine Meldung zwei sich widersprechende Zeitangaben enthält
- **THEN** weist das System auf den Widerspruch hin

### Requirement: Vorschlag einer verständlichen Fassung
Das System SHALL zu einer Meldung eine verständliche Fassung vorschlagen, die den Inhalt nicht erweitert und Abkürzungen auflöst.

#### Scenario: Fassung vorschlagen
- **WHEN** eine Funktion die Klärung einer Meldung anfordert
- **THEN** zeigt das System die Originalfassung und den Vorschlag nebeneinander

#### Scenario: Keine Erfindung
- **WHEN** eine Information in der Originalmeldung fehlt
- **THEN** ergänzt das System sie nicht, sondern markiert die Lücke

### Requirement: Originalmeldung bleibt erhalten
Das System SHALL die Originalmeldung unverändert aufbewahren und eine Korrektur nur als neue Fassung mit Verweis auf die Originalfassung speichern.

#### Scenario: Vorschlag bestätigen
- **WHEN** eine berechtigte Funktion die vorgeschlagene Fassung bestätigt
- **THEN** entsteht eine neue Fassung, und die Originalfassung bleibt einsehbar

#### Scenario: Vorschlag verwerfen
- **WHEN** die Funktion den Vorschlag verwirft
- **THEN** bleibt die Meldung unverändert

### Requirement: Vorbelegung des Frageschemas
Das System SHALL die Felder des Frageschemas (Wann, Wer, Tut was, Wie, Wo, Umwelt) aus dem Freitext vorbelegen und anpassbar halten.

#### Scenario: Felder vorbelegt
- **WHEN** eine Funktion einen Freitext erfasst
- **THEN** schlägt das System Werte für die erkannten Fragen vor, die sich ändern lassen

#### Scenario: Frage nicht erkennbar
- **WHEN** zu einer Frage keine Angabe im Text steht
- **THEN** bleibt das Feld leer und wird als offen gekennzeichnet

### Requirement: Rückfragevorschläge
Das System SHALL bei Lücken eine Rückfrage vorschlagen, die als Meldung vom Typ Anfrage mit Verweis auf die Ursprungsmeldung erfasst werden kann.

#### Scenario: Rückfrage erzeugen
- **WHEN** eine Funktion einen Rückfragevorschlag übernimmt
- **THEN** entsteht eine Anfrage mit Verweis auf die Ursprungsmeldung, die der Triage zugeführt wird

### Requirement: Berechtigung zur Bestätigung
Das System SHALL die Bestätigung einer verständlichen Fassung dem Meldungsverfasser und dem Chef Nachrichtendienst vorbehalten.

#### Scenario: Nicht berechtigt
- **WHEN** eine andere Funktion eine Fassung bestätigen will
- **THEN** verweigert das System die Aktion

### Requirement: Keine Verzögerung der Triage
Das System SHALL die Triage einer Meldung nicht von der Klärung abhängig machen.

#### Scenario: Dringende Meldung
- **WHEN** eine Meldung als Schlüsselnachricht eingestuft werden soll, während die Klärung läuft
- **THEN** kann der Chef sie sofort einstufen und verteilen

### Requirement: Herkunft, Begründung und Protokoll
Das System SHALL zu jedem Vorschlag die Begründung anzeigen und angenommene, geänderte und verworfene Vorschläge mit Person und Zeit protokollieren.

#### Scenario: Begründung sehen
- **WHEN** eine Funktion einen Vorschlag öffnet
- **THEN** sieht sie, welche Stellen der Meldung zum Vorschlag geführt haben

### Requirement: Kennzeichnung maschinell erzeugter Inhalte
Das System SHALL maschinell vorgeschlagene Inhalte deutlich als solche kennzeichnen, bis sie bestätigt sind.

#### Scenario: Unbestätigter Vorschlag
- **WHEN** ein Vorschlag angezeigt wird
- **THEN** ist er als KI-Vorschlag und unbestätigt gekennzeichnet
