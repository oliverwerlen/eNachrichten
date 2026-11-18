## Purpose

Stellt sicher, dass nur berechtigte Personen das System nutzen und dass jede Aktion einer Person und einer Funktion zugeordnet ist. Die Anmeldung erfolgt über AGOV.

## ADDED Requirements

### Requirement: Anmeldung über AGOV
Das System SHALL Personen ausschliesslich über AGOV anmelden und keine eigenen Passwörter verwalten.

#### Scenario: Erfolgreiche Anmeldung
- **WHEN** eine Person sich über AGOV erfolgreich authentifiziert
- **THEN** wird sie im System angemeldet und erhält die ihr zugewiesenen Funktionen

#### Scenario: Anmeldung fehlgeschlagen
- **WHEN** die Authentifizierung über AGOV fehlschlägt
- **THEN** verweigert das System den Zugriff

### Requirement: Zugriff nur mit zugewiesener Funktion
Das System SHALL einer angemeldeten Person nur dann Zugriff auf ein Ereignis geben, wenn ihr für dieses Ereignis mindestens eine Funktion zugewiesen ist.

#### Scenario: Person ohne Funktion
- **WHEN** sich eine Person ohne zugewiesene Funktion anmeldet
- **THEN** sieht sie keine Inhalte und erhält den Hinweis, dass keine Funktion zugewiesen ist

### Requirement: Funktionen im System geführt
Das System SHALL die Zuweisung von Funktionen pro Ereignis im System führen und Änderungen ohne erneute Anmeldung wirksam machen.

#### Scenario: Funktionswechsel mitten im Einsatz
- **WHEN** einer Person eine zusätzliche Funktion zugewiesen wird
- **THEN** hat sie die Rechte der neuen Funktion, ohne sich neu anmelden zu müssen

### Requirement: Zuweisung durch berechtigte Funktion
Das System SHALL die Zuweisung von Funktionen auf berechtigte Funktionen beschränken und jede Zuweisung mit Person, Zeit und Grund protokollieren.

#### Scenario: Unberechtigte Zuweisung
- **WHEN** eine nicht berechtigte Funktion eine Zuweisung ändern will
- **THEN** verweigert das System die Änderung

### Requirement: Aktionen einer Person zuordnen
Das System SHALL jede Aktion mit der angemeldeten Person und der handelnden Funktion verknüpfen.

#### Scenario: Visum
- **WHEN** eine Person eine Meldung erfasst
- **THEN** enthält das Visum die Person und die Funktion, in der sie handelt

### Requirement: Wahl der handelnden Funktion
Das System SHALL einer Person mit mehreren Funktionen erlauben, die handelnde Funktion zu wählen und anzuzeigen.

#### Scenario: Mehrere Funktionen
- **WHEN** eine Person als C Lage und Chef Nachrichtendienst zugewiesen ist
- **THEN** zeigt das System die aktuell gewählte Funktion an und protokolliert sie bei jeder Aktion

### Requirement: Sitzung und Abmeldung
Das System SHALL Sitzungen nach einer konfigurierbaren Dauer ablaufen lassen und eine Abmeldung jederzeit erlauben.

#### Scenario: Abmelden
- **WHEN** eine Person sich abmeldet
- **THEN** wird die Sitzung beendet und weitere Anfragen verlangen eine neue Anmeldung

### Requirement: Sperre einer Person
Das System SHALL berechtigten Funktionen erlauben, eine Person zu sperren, mit sofortiger Wirkung.

#### Scenario: Person sperren
- **WHEN** eine berechtigte Funktion eine Person sperrt
- **THEN** werden deren laufende Sitzungen beendet und weitere Zugriffe verweigert

### Requirement: Zugriffsprotokoll
Das System SHALL Anmeldungen, fehlgeschlagene Versuche und Zuweisungsänderungen protokollieren.

#### Scenario: Fehlversuch
- **WHEN** eine Anmeldung fehlschlägt
- **THEN** besteht ein Protokolleintrag mit Zeit und Grund

### Requirement: Kein Zugang für Externe
Das System SHALL externen Organisationen keinen Zugang bereitstellen.

#### Scenario: Externe Gegenstelle
- **WHEN** eine Person einer externen Organisation ohne Funktion zugreift
- **THEN** wird der Zugriff verweigert
