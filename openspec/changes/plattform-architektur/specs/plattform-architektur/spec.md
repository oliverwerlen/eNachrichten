## Purpose

Legt die verbindlichen technischen Randbedingungen der Plattform fest, damit sie cloud-nativ, kostengünstig und ohne Nutzung nahezu kostenfrei betrieben werden kann. Die Randbedingungen sind prüfbar und gelten für alle Funktionen.

## ADDED Requirements

### Requirement: Serverless-Rechenleistung
Das System SHALL seine Rechenleistung ausschliesslich mit Lambda-Funktionen erbringen und keine ECS-Dienste, dauerhaft laufenden Server oder Container betreiben.

#### Scenario: Prüfung der Infrastruktur
- **WHEN** die Infrastruktur geprüft wird
- **THEN** enthält sie keine ECS-Dienste und keine dauerhaft laufenden Rechner

#### Scenario: Keine Nutzung
- **WHEN** das System nicht genutzt wird
- **THEN** läuft keine Rechenleistung der Anwendung

### Requirement: Frontend als statische Anwendung
Das System SHALL das Frontend als Angular-Anwendung bereitstellen, die aus einem S3-Speicher über ein Content-Delivery-Netz verschlüsselt ausgeliefert wird.

#### Scenario: Aufruf der Anwendung
- **WHEN** eine Person die Anwendung aufruft
- **THEN** werden die statischen Dateien über eine verschlüsselte Verbindung aus dem Content-Delivery-Netz geliefert

#### Scenario: Direkter Speicherzugriff
- **WHEN** jemand den Speicher des Frontends direkt aufrufen will
- **THEN** ist er nicht öffentlich zugänglich

### Requirement: Zugriff nur über die API
Das System SHALL allen Zugriff des Frontends auf Daten über die eigene API führen und dem Frontend keinen direkten Zugriff auf Datenbank, Archiv oder KI gewähren.

#### Scenario: Aufruf mit Identität
- **WHEN** das Frontend eine Anfrage an die API sendet
- **THEN** trägt sie die Identität der angemeldeten Person, die vor der Ausführung geprüft wird

#### Scenario: Anfrage ohne Identität
- **WHEN** eine Anfrage ohne gültige Identität eintrifft
- **THEN** wird sie abgewiesen, bevor Fachlogik ausgeführt wird

### Requirement: Prüfung von Rechten serverseitig
Das System SHALL Funktion, Sichtrechte und Ereigniszugehörigkeit serverseitig prüfen und sich nicht auf Angaben des Frontends verlassen.

#### Scenario: Manipulierte Anfrage
- **WHEN** das Frontend eine Funktion angibt, die der Person nicht zugewiesen ist
- **THEN** wird die Anfrage abgelehnt

### Requirement: Anmeldung über Cognito mit AGOV
Das System SHALL die Anmeldung über Amazon Cognito mit Anbindung an AGOV führen, gemäss `authentifizierung-agov-cognito`.

#### Scenario: Anmeldung
- **WHEN** eine Person das System aufruft
- **THEN** erfolgt die Anmeldung über Cognito und AGOV

### Requirement: Relationale Datenhaltung mit Scale-to-zero
Das System SHALL seine Daten in einer serverlosen relationalen Aurora-PostgreSQL-Datenbank halten, die in der Ruhezeit auf null Rechenkapazität pausieren kann.

#### Scenario: Ruhezeit
- **WHEN** kein Ereignis aktiv ist
- **THEN** darf die Datenbank pausieren und verursacht nur Speicherkosten

#### Scenario: Zugriff auf pausierte Datenbank
- **WHEN** eine Anfrage auf die pausierte Datenbank trifft
- **THEN** wird die Datenbank geweckt, und die Anfrage wird nach dem Wiederanlaufen verarbeitet

### Requirement: Datenbankzugriff ohne feste Grundkosten
Das System SHALL aus den Lambda-Funktionen ohne dauerhafte Datenbankverbindungen und ohne Komponenten mit festen Grundkosten (zum Beispiel NAT-Gateway oder Verbindungsproxy) auf die Datenbank zugreifen.

#### Scenario: Prüfung der Komponenten
- **WHEN** die Infrastruktur geprüft wird
- **THEN** enthält sie keine Komponenten, die ohne Nutzung laufende Kosten verursachen, ausser Speicher

### Requirement: Begrenzte Antwortgrösse
Das System SHALL umfangreiche Abfragen seitenweise liefern, sodass keine Antwort die Grenze des Datenbankzugriffs von 1 MiB überschreitet.

#### Scenario: Langes Journal
- **WHEN** das Journal mehr Einträge enthält, als in eine Antwort passen
- **THEN** liefert die API die Einträge seitenweise

### Requirement: Nutzung der Datenbankfähigkeiten
Das System SHALL Geodaten, Ähnlichkeitssuche, Volltextsuche und die zeilenbasierte Zugriffskontrolle mit den Fähigkeiten der Datenbank umsetzen und keinen separaten Such-, Vektor- oder Geodienst betreiben.

#### Scenario: Suche
- **WHEN** eine Person im Journal nach einem Stichwort sucht
- **THEN** liefert die Datenbank das Ergebnis, ohne einen weiteren Suchdienst

#### Scenario: Ähnliche Meldung
- **WHEN** das System ähnliche frühere Meldungen sucht
- **THEN** erfolgt die Suche in der Datenbank

### Requirement: Zugriffskontrolle auch in der Datenbank
Das System SHALL Sichtrechte zusätzlich zur Anwendungslogik auf der Ebene der Datenbankzeilen durchsetzen.

#### Scenario: Direkter Abfrageversuch
- **WHEN** eine Abfrage Daten verlangt, die der handelnden Funktion nicht zustehen
- **THEN** liefert die Datenbank diese Zeilen nicht

### Requirement: Getrennter unveränderbarer Speicher
Das System SHALL Originale von Meldungen in einem vom Frontend-Speicher getrennten, unveränderbaren Speicher ablegen, gemäss `meldung-originalarchiv`.

#### Scenario: Ablage
- **WHEN** eine Meldung erfasst wird
- **THEN** wird das Original in diesen Speicher geschrieben, bevor sie weiterverarbeitet wird

### Requirement: KI über zentrale Komponente
Das System SHALL KI-Aufrufe (Bedrock) ausschliesslich über eine zentrale serverseitige Komponente ausführen, die Kosten schätzt, Schwellen prüft und Verbrauch zählt.

#### Scenario: Aufruf aus dem Frontend
- **WHEN** das Frontend eine KI-Auswertung anfordert
- **THEN** wird sie über die zentrale Komponente ausgeführt und geprüft

#### Scenario: Umgehung
- **WHEN** eine andere Komponente die KI direkt aufrufen will
- **THEN** ist ihr das nicht erlaubt

### Requirement: Zeitgesteuerte Aufgaben ausserhalb der Datenbank
Das System SHALL periodische Aufgaben über einen Zeitplaner ausführen und nicht über Aufgaben innerhalb der Datenbank, und nur bei aktivem Ereignis.

#### Scenario: Wetterabruf
- **WHEN** ein Ereignis aktiv ist
- **THEN** startet der Zeitplaner den Abruf in den vorgesehenen Abständen

#### Scenario: Kein Ereignis
- **WHEN** kein Ereignis aktiv ist
- **THEN** startet der Zeitplaner keine Aufgaben

### Requirement: Externe Dienste
Das System SHALL swisstopo-Karten direkt vom Browser laden und Daten von MeteoSchweiz sowie Aufrufe von Bedrock nur über serverseitige Komponenten beziehen.

#### Scenario: Karte
- **WHEN** die Lagekarte angezeigt wird
- **THEN** lädt der Browser die Kartenkacheln von swisstopo

#### Scenario: Wetter
- **WHEN** die Wetterdaten abgerufen werden
- **THEN** ruft eine serverseitige Komponente MeteoSchweiz auf und das Frontend erhält nur das Ergebnis

### Requirement: Datenstandort
Das System SHALL Daten und Verarbeitung in der AWS-Region Europe (Zurich) halten, soweit die verwendeten Dienste dort verfügbar sind, und jede Abweichung ausweisen.

#### Scenario: Prüfung der Region
- **WHEN** die Infrastruktur geprüft wird
- **THEN** liegen alle Ressourcen in der Region Zürich oder die Abweichung ist begründet und dokumentiert

### Requirement: Infrastruktur als Code
Das System SHALL seine Infrastruktur vollständig als Code beschreiben und reproduzierbar bereitstellen.

#### Scenario: Neue Umgebung
- **WHEN** eine Umgebung aus dem Code bereitgestellt wird
- **THEN** entspricht sie der beschriebenen Konfiguration ohne manuelle Schritte

### Requirement: Getrennte Umgebungen
Das System SHALL Produktion und Test mit getrennten Ressourcen, Daten und Berechtigungen betreiben.

#### Scenario: Zugriff aus Test
- **WHEN** eine Komponente der Testumgebung auf Daten der Produktion zugreifen will
- **THEN** wird der Zugriff verweigert

### Requirement: Logs ohne Inhalte
Das System SHALL in Protokollen keine Meldungsinhalte und keine Personendaten ablegen und die Aufbewahrung der Protokolle begrenzen.

#### Scenario: Fehler bei der Verarbeitung
- **WHEN** ein Fehler protokolliert wird
- **THEN** enthält der Eintrag Kennungen und Fehlerart, aber keine Meldungsinhalte oder Personendaten

#### Scenario: Aufbewahrungsdauer
- **WHEN** Protokolle die festgelegte Dauer überschreiten
- **THEN** werden sie automatisch entfernt
