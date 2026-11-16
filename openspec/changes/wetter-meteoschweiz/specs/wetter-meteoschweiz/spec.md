## Purpose

Stellt dem Führungsstab Wetterprognosen je Standort von MeteoSchweiz bereit und führt Warnungen als Meldungen in den normalen Fluss. Alle Angaben nennen Quelle, Abrufzeit und Gültigkeit.

## ADDED Requirements

### Requirement: Prognose je Standort
Das System SHALL für einen gewählten Standort die Prognose von MeteoSchweiz mit Werten über den Prognosezeitraum anzeigen.

#### Scenario: Prognose für Einsatzort
- **WHEN** eine Funktion bei einem Einsatzort die Prognose öffnet
- **THEN** zeigt das System die Prognosewerte für diesen Standort im zeitlichen Verlauf

### Requirement: Standortauswahl
Das System SHALL als Standorte die im System vorhandenen Orte (Einsatzorte, Unterkünfte, Sektoren, Kartenobjekte, Gemeinden) und frei gesetzte Punkte auf der Karte anbieten.

#### Scenario: Freier Punkt
- **WHEN** eine Funktion auf der Karte einen Punkt wählt
- **THEN** zeigt das System die Prognose für diesen Punkt

### Requirement: Beobachtete Standorte
Das System SHALL Standorte als beobachtet markieren lassen und deren Prognosen gesammelt anzeigen.

#### Scenario: Mehrere Standorte
- **WHEN** drei Standorte als beobachtet markiert sind
- **THEN** zeigt die Wetterübersicht alle drei nebeneinander

### Requirement: Quelle, Abrufzeit und Gültigkeit
Das System SHALL jede Wetterangabe mit der Quelle "MeteoSchweiz", der Abrufzeit und dem Gültigkeitszeitraum kennzeichnen.

#### Scenario: Herkunft sichtbar
- **WHEN** eine Prognose angezeigt wird
- **THEN** sind Quelle, Abrufzeit und Gültigkeit sichtbar

### Requirement: Aktualisierung
Das System SHALL Prognosen regelmässig aktualisieren und das Aktualisierungsintervall anzeigen.

#### Scenario: Neue Prognose
- **WHEN** MeteoSchweiz eine neue Prognose bereitstellt
- **THEN** aktualisiert das System die Anzeige und die Abrufzeit

### Requirement: Ausfall der Verbindung
Das System SHALL bei nicht erreichbarer Quelle die letzte Prognose mit deutlichem Hinweis auf ihr Alter anzeigen.

#### Scenario: Keine Verbindung
- **WHEN** der Abruf fehlschlägt
- **THEN** zeigt das System die letzte Prognose mit Abrufzeit und dem Hinweis "nicht aktuell"

### Requirement: Wetterebene auf der Karte
Das System SHALL die Prognose als Ebene auf der Lagekarte anzeigbar machen, ohne den Zeitstand der Lage zu verändern.

#### Scenario: Ebene einblenden
- **WHEN** eine Funktion die Wetterebene aktiviert
- **THEN** erscheinen die Prognosewerte der beobachteten Standorte auf der Karte

### Requirement: Warnungen als Meldung
Das System SHALL Warnungen und wesentliche Wetterumschwünge als automatisch erzeugte Meldung (Richtung Eingang, Absender MeteoSchweiz) der Triage zuführen.

#### Scenario: Neue Warnung
- **WHEN** MeteoSchweiz eine Warnung für einen beobachteten Standort ausgibt
- **THEN** entsteht eine Meldung mit Quelle und Abrufzeit, die der Chef Nachrichtendienst einstuft und verteilt

#### Scenario: Keine Doppelmeldung
- **WHEN** dieselbe Warnung unverändert erneut abgerufen wird
- **THEN** entsteht keine neue Meldung

#### Scenario: Warnung ändert sich
- **WHEN** eine bestehende Warnung höher gestuft wird
- **THEN** entsteht eine Folgemeldung mit Verweis auf die frühere Meldung

### Requirement: MeteoSchweiz als Gegenstelle
Das System SHALL MeteoSchweiz als externe Gegenstelle im Adressbuch führen.

#### Scenario: Absender
- **WHEN** eine Wettermeldung erzeugt wird
- **THEN** ist MeteoSchweiz der Absender aus dem Adressbuch

### Requirement: Wetter im Rapport
Das System SHALL dem C Lage ermöglichen, die Wetterlage in die Orientierung des Lagerapports und in den Inforapport aufzunehmen.

#### Scenario: Wetter auswählen
- **WHEN** der C Lage die Wetterlage für den Rapport auswählt
- **THEN** erscheint sie mit Quelle und Abrufzeit in der Orientierung

### Requirement: Wetter in der Zeitplanung
Das System SHALL beim Planen eines Eintrags die Prognose für Ort und Zeit anzeigen.

#### Scenario: Einsatzfenster
- **WHEN** eine Funktion einen Eintrag für einen Standort plant
- **THEN** sieht sie die Prognose für den gewählten Zeitraum

### Requirement: Simulierte Daten im Prototyp
Das System SHALL im Prototyp simulierte Wetterdaten verwenden können, wobei die Datenquelle von der Anzeige getrennt ist und deutlich als Simulation gekennzeichnet wird.

#### Scenario: Simulation
- **WHEN** der Prototyp mit simulierten Daten läuft
- **THEN** kennzeichnet jede Wetteransicht die Daten als simuliert
