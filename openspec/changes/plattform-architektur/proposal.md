## Why

Die Plattform soll cloud-nativ und kostengünstig betrieben werden und ohne Nutzung kaum Kosten verursachen. Die technischen Rahmenbedingungen (Serverless, kein ECS, Angular in S3, Cognito mit AGOV, Aurora, Bedrock, unveränderbare Ablage) wurden vorgegeben. Sie müssen als verbindliche Randbedingungen festgehalten werden, damit alle Changes und die spätere Umsetzung darauf aufbauen und die Pipeline sie prüfen kann.

## What Changes

- Rechenleistung ausschliesslich serverless mit Lambda-Funktionen. Kein ECS und keine dauerhaft laufenden Server oder Container.
- Frontend mit Angular als statische Anwendung, ausgeliefert aus S3 über ein Content-Delivery-Netz.
- Das Frontend greift nur über die eigene API auf Daten zu, nie direkt auf die Datenbank. Jeder Aufruf trägt die Identität der angemeldeten Person.
- Anmeldung über Cognito mit AGOV (Details in `authentifizierung-agov-cognito`).
- Datenhaltung in Aurora PostgreSQL serverless mit Scale-to-zero (Details in `plattform-betrieb-kosten`). Zugriff ohne dauerhafte Verbindungen und ohne Komponenten mit festen Grundkosten.
- Aurora-Fähigkeiten werden genutzt, wo möglich: Geodaten, Ähnlichkeitssuche, Volltextsuche, zeilenbasierte Zugriffskontrolle. Kein separater Such- oder Vektordienst.
- Meldungen werden in einem getrennten, unveränderbaren Speicher abgelegt (Details in `meldung-originalarchiv`).
- KI über Bedrock, nur über eine zentrale Komponente mit Kostenprüfung (Details in `plattform-betrieb-kosten`).
- Zeitgesteuerte Aufgaben über einen Zeitplaner ausserhalb der Datenbank, nur bei aktivem Ereignis.
- Infrastruktur als Code, reproduzierbar, getrennte Ressourcen für Produktion und Test.
- Logs ohne Meldungsinhalte und Personendaten, mit begrenzter Aufbewahrung.
- Externe Dienste: swisstopo-Karten direkt im Browser, MeteoSchweiz und Bedrock nur über serverseitige Komponenten.

## Capabilities

### New Capabilities
- `plattform-architektur`: Verbindliche technische Randbedingungen der Plattform (Serverless, Frontend, API, Datenhaltung, Archiv, KI, Aufgabenplanung, Infrastruktur, Logging).

### Modified Capabilities
<!-- keine -->

## Impact

- Gilt für alle übrigen Changes. Konkretisiert `plattform-betrieb-kosten`, `authentifizierung-agov-cognito`, `meldung-originalarchiv`, `nfa-barrierefreiheit-performance-sicherheit`.
- Geprüft in der AWS-Dokumentation: Aurora Serverless skaliert auf 0 ACU mit Auto-Pause, die RDS Data API und Aurora Serverless sind in der Region Zürich verfügbar (PostgreSQL ab 16.3 deckt alles ab, PostgreSQL 17.4 oder höher ebenso), die Data API begrenzt Antworten auf 1 MiB und weckt eine pausierte Datenbank. Cognito kann OIDC-Anbieter anbinden. S3 Object Lock im Compliance-Modus kann auch vom Root-Benutzer nicht umgangen werden.
- Nicht geprüft: Anbindung von AGOV an Cognito, Row-Level Security zusammen mit der Data API, Modellverfügbarkeit von Bedrock in der Zielregion, Preise.
- Offene Fragen:
  - Datenstandort Region Zürich: Ist er verbindlich (Annahme: ja, noch zu bestätigen)?
  - Wahl des Werkzeugs für Infrastruktur als Code (Design).
  - Live-Aktualisierung des Postfachs: Abfragen in kurzen Abständen oder Push (Annahme: Abfragen genügen).
  - Ablage grosser Anhänge: Hochladen über die API oder direkt in den Speicher mit zeitlich begrenzter Berechtigung.
  - Bereitstellung über GitLab des Kantons gemäss Lieferprozess und Anbindung der Pipeline.
  - Ausfallbetrieb bei Netz- oder Stromausfall im Tal (siehe `nfa-barrierefreiheit-performance-sicherheit`).
