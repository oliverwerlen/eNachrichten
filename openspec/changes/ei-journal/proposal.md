## Why

Das Ei-Journal (Eingangsjournal) ist die chronologische Ablage aller Meldungen und liegt in der Verantwortung des Nachrichtendienstes. Es bildet die Grundlage der Nachvollziehbarkeit und wird heute von Hand nachgeführt.

## What Changes

- Das Journal führt alle Meldungen des Ereignisses chronologisch, automatisch aus der Triage.
- Es ist unveränderlich. Korrekturen sind neue Fassungen mit Verweis.
- Anzeige nach Ereigniszeit und nach Erfassungszeit, mit Filter und Suche.
- Jeder Journaleintrag verweist auf die Meldung samt Kette.
- Das Journal ist nur für Chef ND, C Lage, Adjutant und SC vollständig einsehbar, übrige Funktionen sehen ihre eigenen Meldungen.

## Capabilities

### New Capabilities
- `ei-journal`: Chronologisches, unveränderliches Journal aller Meldungen des Ereignisses.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `meldungskette-nachvollziehbarkeit`.
- Offene Fragen: Ob "Ei-Journal" ausschliesslich eingehende oder alle Meldungen führt. Annahme: alle, mit Filter nach Richtung.
