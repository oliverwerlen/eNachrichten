## Why

Die Führungswand enthält vier Listen für Vorgänge mit Frist und Zuständigem: Auftragskontrolle, Sofortmassnahmen, Hilfegesuche an den Stab und Hilfegesuche des Stabes. Sie liegen in der Verantwortung des Nachrichtendienstes und werden heute von Hand geführt.

## What Changes

- Auftragskontrolle: N°, Auftrag (Zeit), Was – Wo – Womit, Prio, Wer, Bis wann, Status.
- Sofortmassnahmen als eigene Tafel: Auftrag (Zeit), Was – Wo, Wer, Bis wann, Status.
- Hilfegesuche an den Stab: Antragsteller, Was – Wo – Wieviel, Verantwortlich, Bis wann, Status.
- Hilfegesuche des Stabes: Ausgang (Zeit), Was – Wo – Wieviel, Beantragt bei, Termin, Bewilligt.
- Einträge werden aus Meldungen vorausgefüllt und können angepasst werden.
- Der Abschluss einer Meldungskette (Vollzug, Antwort) setzt den Status.
- Jede Zeile verweist auf die Ursprungsmeldung.

## Capabilities

### New Capabilities
- `tafeln-vorgangslisten`: Auftragskontrolle, Sofortmassnahmen, Hilfegesuche an den Stab, Hilfegesuche des Stabes.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `postfach-und-reaktionen`, `meldungskette-nachvollziehbarkeit`, `gegenstellen-adressbuch`.
- Wird von `fristueberwachung` und `rapport-lagerapport` genutzt.
- Offene Fragen: Bedeutung des farbigen Feldes neben "Bis wann" bei den Hilfegesuchen an den Stab (Annahme: Status). Werden Sofortmassnahmen und Aufträge getrennt geführt (Entscheid: ja, getrennte Tafeln).
