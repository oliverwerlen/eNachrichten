## Purpose

Legt Meldungen, ihre Fassungen und die Entscheide rund um sie unveränderbar und prüfbar ab. Das Archiv ist die Quelle der Wahrheit für das, was gemeldet und entschieden wurde.

## ADDED Requirements

### Requirement: Original bei der Erfassung ablegen
Das System SHALL das Original jeder Meldung samt Anhängen bei der Erfassung unveränderbar ablegen, bevor die Weiterverarbeitung (Triage, Tafeln, Karte, Journal) beginnt.

#### Scenario: Eingehende Meldung
- **WHEN** eine Funktion eine eingehende Meldung speichert
- **THEN** ist das Original mit Anhängen abgelegt, und erst danach steht die Meldung der Triage zur Verfügung

#### Scenario: Ausgehende Meldung
- **WHEN** eine Funktion eine ausgehende Meldung speichert
- **THEN** wird auch diese Meldung unveränderbar abgelegt

### Requirement: Unveränderbarkeit
Das System SHALL abgelegte Originale in der produktiven Umgebung während 10 Jahren vor Änderung und Löschung schützen, ohne Ausnahme für Administratoren.

#### Scenario: Änderungsversuch
- **WHEN** eine Funktion, ein Administrator oder ein Prozess ein abgelegtes Original ändern will
- **THEN** wird die Änderung verweigert

#### Scenario: Löschversuch vor Fristende
- **WHEN** jemand ein abgelegtes Original vor Ablauf der 10 Jahre löschen will
- **THEN** wird das Löschen verweigert

### Requirement: Testumgebung ohne Aufbewahrungspflicht
Das System SHALL in der Testumgebung eine kurze Aufbewahrungsfrist verwenden, nach der Testdaten gelöscht werden können.

#### Scenario: Testdaten bereinigen
- **WHEN** eine berechtigte Person Testdaten nach Ablauf der kurzen Frist löscht
- **THEN** sind sie entfernt

### Requirement: Fassungen ablegen
Das System SHALL jede Korrektur einer Meldung als neue Fassung mit Verweis auf die vorherige Fassung unveränderbar ablegen und frühere Fassungen erhalten.

#### Scenario: Meldung korrigieren
- **WHEN** eine berechtigte Funktion eine Meldung korrigiert
- **THEN** entsteht eine neue abgelegte Fassung, und das Original bleibt unverändert abrufbar

### Requirement: Entscheidungshistorie
Das System SHALL Einstufung, Verteilung, Quittierung, Reaktion, Abschluss, Versandbestätigung, Freigabe oder Ablehnung von KI-Kosten sowie Bestätigung oder Verwerfen eines KI-Vorschlags als unveränderbare Ereigniseinträge mit Person, Funktion und Zeit ablegen.

#### Scenario: Einstufung festhalten
- **WHEN** der Chef Nachrichtendienst eine Meldung als Schlüsselnachricht einstuft
- **THEN** besteht ein unveränderbarer Eintrag mit Person, Zeit und Ergebnis

#### Scenario: Verworfener KI-Vorschlag
- **WHEN** eine Funktion einen KI-Vorschlag verwirft
- **THEN** besteht ein unveränderbarer Eintrag dazu

### Requirement: Prüfsumme und Integritätsprüfung
Das System SHALL zu jedem abgelegten Original und jeder Fassung eine Prüfsumme führen und eine Prüfung ermöglichen, die Veränderungen aufdeckt.

#### Scenario: Prüfung bestanden
- **WHEN** die Integrität einer Meldung geprüft wird und das Original unverändert ist
- **THEN** meldet das System die Prüfung als bestanden

#### Scenario: Abweichung
- **WHEN** die Prüfsumme nicht mit dem abgelegten Original übereinstimmt
- **THEN** meldet das System die Abweichung und hebt sie für den Chef Nachrichtendienst hervor

### Requirement: Lückenlose Nummerierung
Das System SHALL Meldungsnummern ohne Lücken vergeben und fehlende Nummern erkennen.

#### Scenario: Lücke erkannt
- **WHEN** zwischen zwei abgelegten Meldungen eine Nummer fehlt
- **THEN** meldet das System die Lücke zur Klärung

### Requirement: Wiederherstellung aus dem Archiv
Das System SHALL die Anwendungsdaten (Journal, Tafeln, Karte, Rapporte) aus den abgelegten Originalen und Ereigniseinträgen wiederherstellen können.

#### Scenario: Datenverlust
- **WHEN** die Anwendungsdaten eines Ereignisses verloren gehen
- **THEN** lassen sie sich aus den abgelegten Originalen und Ereigniseinträgen neu aufbauen

### Requirement: Sicherung bei Ausfall der Weiterverarbeitung
Das System SHALL eine Meldung auch dann sichern, wenn die Weiterverarbeitung ausfällt, und die Verarbeitung nachholen.

#### Scenario: Ausfall nach Ablage
- **WHEN** das Original abgelegt ist und die Weiterverarbeitung fehlschlägt
- **THEN** bleibt das Original erhalten, und die Meldung wird nachträglich verarbeitet

### Requirement: Abgleich verwaister Originale
Das System SHALL abgelegte Originale ohne zugehörige Meldung erkennen und zum Abgleich melden, ohne sie zu löschen.

#### Scenario: Verwaistes Original
- **WHEN** ein abgelegtes Original keine zugehörige Meldung hat
- **THEN** erscheint es in der Liste zum Abgleich

### Requirement: Lesezugriff nach Sichtrechten
Das System SHALL berechtigten Funktionen den Lesezugriff auf Originale und Fassungen nach den Sichtrechten gewähren und keine Funktion mit Schreib- oder Löschzugriff auf das Archiv ausstatten.

#### Scenario: Originalansicht
- **WHEN** eine berechtigte Funktion das Original einer Meldung öffnet
- **THEN** sieht sie das abgelegte Original und alle Fassungen

### Requirement: Kennzeichnung gesperrter Meldungen
Das System SHALL im System sichtbar machen, dass ein Original unveränderbar abgelegt ist, mit Ablagezeit und Prüfstatus.

#### Scenario: Anzeige
- **WHEN** eine Funktion eine Meldung öffnet
- **THEN** zeigt das System Ablagezeit und Prüfstatus des Originals
