## Why

Ein Krisenstab ist selten aktiv, muss dann aber sofort und zuverlässig funktionieren. Die Kosten sollen in der Ruhezeit gegen null gehen, im Einsatz spielen sie keine Rolle. Zusätzlich verursacht die KI verbrauchsabhängige Kosten, die effizient gehalten und ab bestimmten Schwellen manuell freigegeben werden müssen.

## What Changes

- Zwei Betriebsmodi: Ruhe (kein aktives Ereignis) mit minimalen Kosten, und Ereignis aktiv mit dauerhafter Verfügbarkeit ohne Weckverzögerung.
- Der Modus folgt dem Ereignis: Aktivieren schaltet auf Einsatzbetrieb, Archivieren auf Ruhe. Zusätzlich eine Aktion "Stab aufbieten", die das System vorab bereit macht.
- Umgebungen: Produktion und eine Testumgebung. Die Testumgebung ist in der Ruhezeit kostenlos bis auf Speicher.
- Aufgaben, die Daten brauchen (zum Beispiel Wetterabruf, Fristprüfung), laufen nur bei aktivem Ereignis.
- Kostenkontrolle für KI: Vorabschätzung pro Aufruf, Schwellen pro Aufruf, pro Ereignis und pro Zeitraum, manuelle Freigabe bei Überschreitung, Messung von Verbrauch und Kosten, Ausschalter. Der manuelle Ablauf läuft bei fehlender Freigabe weiter.
- Kostensicht pro Ereignis.

## Capabilities

### New Capabilities
- `plattform-betrieb-kosten`: Betriebsmodi, Umgebungen, Verfügbarkeit im Einsatz und Kostenkontrolle der KI.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `ereignis-verwaltung`, `funktionen-und-sichtrechte`, `automatisierungsvorschlaege`, `ki-meldungsklaerung`, `ki-ortsaufloesung`, `wetter-meteoschweiz`, `fristueberwachung`.
- Vorgesehene Technik (gehört ins Design): Serverless-Architektur ohne ECS (Lambda, API Gateway), Angular-Frontend in S3 mit CloudFront, Aurora Serverless v2 PostgreSQL in der Region Zürich mit Scale-to-zero (Auto-Pause) in Ruhe und Mindestkapazität im Einsatz, Zugriff über die RDS Data API ohne VPC und Proxy, Aurora-Funktionen wo möglich (PostGIS, pgvector, Volltext, Row-Level Security), Aufgabenplanung über EventBridge Scheduler statt pg_cron, KI über Bedrock mit zentralem Kostentor. Die Verfügbarkeit von Data API, Serverless und Auto-Pause in Zürich ist laut AWS-Dokumentation gegeben, Auto-Pause ist beim Aufbau mit `describe-orderable-db-instance-options` zu bestätigen.
- Abweichung vom Lieferprozess: Dieser nennt DEV und INT, hier gibt es nur eine Testumgebung. Review und Abnahme finden dort nacheinander statt, das Demo-Szenario muss zurücksetzbar sein.
- Offene Fragen:
  - Wer gibt KI-Kosten frei und ab welchen Stufen (Annahme: Chef Nachrichtendienst bei kleinen, SC bei grossen Überschreitungen).
  - Höhe der Schwellen, abhängig vom Meldungsvolumen pro Tag (nicht bekannt).
  - Verhalten bei Überschreitung: nur Freigabe verlangen (Annahme) oder KI ganz abschalten.
  - Zählung der Tokens vorab (genaue Zählung oder Schätzung aus der Textlänge).
  - Datenschutz und Datenstandort der KI-Verarbeitung (Region Zürich, Cross-Region-Inference innerhalb der EU), Verfügbarkeit der Modelle in der Zielregion.
  - Kontingente von Bedrock im Einsatz, vor dem Pilot zu erhöhen.
  - Ob und wie ein Ausfall der Cloud (Netz, Strom im Tal) durch einen Papier-Fallback abgedeckt wird.
