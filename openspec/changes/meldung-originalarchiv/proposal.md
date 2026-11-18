## Why

Die Meldungen sind der Kern des Systems. Sie müssen unveränderbar und nachvollziehbar abgelegt sein, damit später belegbar ist, was gemeldet wurde, wer wie darauf reagiert hat und warum etwas so lief. Auf PROD gilt eine Aufbewahrung von 10 Jahren.

## What Changes

- Das Original jeder Meldung (eingehend und ausgehend, mit Anhängen) wird bei der Erfassung unveränderbar abgelegt, bevor die Weiterverarbeitung beginnt.
- Jede Korrektur ist eine neue Fassung, die ebenfalls unveränderbar abgelegt wird. Frühere Fassungen bleiben bestehen.
- Die Entscheide rund um eine Meldung werden als unveränderbare Ereigniseinträge geführt: Einstufung, Verteilung, Quittierung, Reaktion, Abschluss, Versandbestätigung, Freigabe von KI-Kosten, Bestätigung oder Verwerfen eines KI-Vorschlags.
- Prüfsummen erlauben, die Unveränderlichkeit jederzeit zu belegen. Meldungsnummern laufen ohne Lücke, fehlende Nummern werden erkannt.
- Die Anwendungsdaten (Journal, Tafeln, Karte, Rapporte) sind abgeleitet und lassen sich aus den abgelegten Originalen und Ereigniseinträgen wiederherstellen.
- PROD: Aufbewahrung von 10 Jahren ohne Möglichkeit zur Änderung oder Löschung, auch nicht für Administratoren. Testumgebung: keine Anforderung zur Aufbewahrung, Daten müssen löschbar sein.

## Capabilities

### New Capabilities
- `meldung-originalarchiv`: Unveränderbare, prüfbare Ablage von Meldungen, Fassungen und Entscheidungshistorie.

### Modified Capabilities
<!-- keine, siehe Hinweis in Impact -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldungskette-nachvollziehbarkeit`, `meldung-triage-verteilung`, `postfach-und-reaktionen`, `ei-journal`.
- Konkretisiert die Anforderungen "unveränderlich" aus `meldung-erfassen`, `ei-journal` und `meldungskette-nachvollziehbarkeit`, ohne diese offenen Changes zu ändern.
- Vorgesehene Technik (gehört ins Design, nicht in die Spec): Ablage in S3 mit Object Lock und Versionierung, Prüfsummen und Verweise in der Datenbank, Compliance-Modus mit 10 Jahren auf PROD, Governance-Modus mit kurzer Frist auf der Testumgebung. Vor PROD ist der gesamte Ablauf auf der Testumgebung durchzuspielen, weil der Compliance-Modus nicht umkehrbar ist.
- Offene Fragen:
  - Datenschutz: Zehn Jahre unlöschbar kollidiert möglicherweise mit Löschpflichten für Personendaten. Rechtliche Klärung vor dem Betrieb auf PROD nötig.
  - Umfang: Welche abgeleiteten Daten (Rapportprotokolle, Tafelstände) müssen zusätzlich 10 Jahre unveränderbar sein (Annahme: Rapportprotokolle ja, übrige Daten sind wiederherstellbar).
  - Anhänge: Art und Grösse (Fotos, Audio) und ob sie ebenfalls gesperrt werden (Annahme: ja).
  - Speicherklasse für ältere Ereignisse und Kosten über 10 Jahre.
  - Umgang mit verwaisten Originalen, wenn die Weiterverarbeitung fehlschlägt (Annahme: erkennen und abgleichen, nicht löschen).
