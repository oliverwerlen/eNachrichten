## Purpose

Legt Qualitätsanforderungen an Zugänglichkeit, Geschwindigkeit, Sicherheit und Ausfallbetrieb fest, die für alle Funktionen des Systems gelten und in der Pipeline prüfbar sind.

## ADDED Requirements

### Requirement: Barrierefreiheit WCAG 2.1 AA
Das System SHALL alle Oberflächen nach WCAG 2.1 Stufe AA gestalten.

#### Scenario: Automatische Prüfung
- **WHEN** die Pipeline eine Änderung prüft
- **THEN** werden Barrierefreiheitsprüfungen ausgeführt und Verstösse gegen Stufe AA lassen die Prüfung scheitern

#### Scenario: Tastaturbedienung
- **WHEN** eine Person nur die Tastatur verwendet
- **THEN** sind alle Funktionen erreichbar und der Fokus ist sichtbar

### Requirement: Kontrast und Darstellung
Das System SHALL Informationen nicht allein über Farbe vermitteln, auch nicht bei den Farben der Kartensymbole und Warnstufen.

#### Scenario: Farbunabhängige Kennzeichnung
- **WHEN** eine Warnstufe oder Symbolkategorie angezeigt wird
- **THEN** ist sie zusätzlich durch Text oder Form erkennbar

### Requirement: Core Web Vitals
Das System SHALL für Ladegeschwindigkeit, Reaktionsfähigkeit und visuelle Stabilität die Schwellen "gut" der Core Web Vitals einhalten.

#### Scenario: Performance-Prüfung
- **WHEN** die Pipeline die Performance prüft
- **THEN** scheitert die Prüfung, wenn ein Wert die Schwelle "gut" überschreitet

### Requirement: Reaktionszeit im Einsatz
Das System SHALL häufige Aktionen (Meldung speichern, Postfach öffnen, Triage-Entscheid) mit unmittelbarer Rückmeldung an die Person bestätigen.

#### Scenario: Meldung speichern
- **WHEN** eine Person eine Meldung speichert
- **THEN** erhält sie eine sofortige Bestätigung oder eine verständliche Fehlermeldung

### Requirement: Verschlüsselung
Das System SHALL Daten bei der Übertragung und bei der Speicherung verschlüsseln.

#### Scenario: Unverschlüsselter Zugriff
- **WHEN** jemand versucht, unverschlüsselt auf das System zuzugreifen
- **THEN** wird der Zugriff verweigert oder auf eine verschlüsselte Verbindung umgeleitet

### Requirement: Minimale Berechtigungen
Das System SHALL jeder Komponente und jeder Funktion nur die Rechte geben, die sie benötigt.

#### Scenario: Zugriff ausserhalb der Rechte
- **WHEN** eine Funktion auf Daten zugreift, die ihr nicht zustehen
- **THEN** verweigert das System den Zugriff, auch bei direktem Aufruf der Schnittstelle

### Requirement: Schutz der Personendaten
Das System SHALL Personendaten (Vermisste, Verletzte, Tote) nur Funktionen anzeigen, die sie nach den Sichtrechten sehen dürfen, und den Zugriff protokollieren.

#### Scenario: Zugriff protokollieren
- **WHEN** eine Funktion Personendaten öffnet
- **THEN** wird der Zugriff mit Person und Zeit protokolliert

### Requirement: Prüfung auf Schwachstellen
Das System SHALL in der Pipeline Abhängigkeiten und Code auf bekannte Schwachstellen prüfen und bei schweren Funden die Auslieferung verhindern.

#### Scenario: Schwere Schwachstelle
- **WHEN** die Pipeline eine schwere Schwachstelle findet
- **THEN** wird die Auslieferung gestoppt

### Requirement: Deutsche Oberfläche
Das System SHALL alle Oberflächentexte und Fehlermeldungen auf Deutsch anzeigen.

#### Scenario: Fehlermeldung
- **WHEN** ein Fehler auftritt
- **THEN** erscheint eine verständliche Meldung auf Deutsch

### Requirement: Ausfallbetrieb
Das System SHALL einen Papier-Fallback unterstützen, bei dem der Meldezettel ausgedruckt und nach Wiederherstellung nacherfasst werden kann.

#### Scenario: Meldezettel drucken
- **WHEN** eine Funktion den Meldezettel ausdruckt
- **THEN** entspricht der Ausdruck dem bekannten Zettel mit allen Feldern

#### Scenario: Nacherfassung
- **WHEN** nach einem Ausfall Zettel nacherfasst werden
- **THEN** wird die Ereigniszeit der Papiermeldung übernommen und die Erfassungszeit getrennt gespeichert

### Requirement: Rückverfolgbarkeit der Anforderungen
Das System SHALL jede Anforderung auf die Anforderung der Auftraggeberin zurückführen lassen.

#### Scenario: Verweis prüfen
- **WHEN** eine Spezifikation geprüft wird
- **THEN** enthält jede Anforderung einen Verweis auf die zugrunde liegende Anforderung
