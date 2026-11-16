## Why

Die Tätigkeiten des Nachrichtendienstes sollen, wo möglich, automatisiert werden. Die Entscheidung bleibt beim Menschen. Das System macht Vorschläge, die vorausgefüllt und anpassbar sind.

## What Changes

- Vorschläge, die der Mensch bestätigt, ändert oder verwirft: Einstufung, Verteiler, Dubletten, Kartensymbole, Tafeleinträge, Rapportentwurf, Vorschläge für die Protokolleinträge.
- Jeder Vorschlag nennt seine Herkunft (Meldung) und lässt sich ohne Folgen verwerfen.
- Angenommene und verworfene Vorschläge werden protokolliert.
- Keine vollautomatische Änderung von Tafeln, Karte oder Verteilung ohne Bestätigung.

## Capabilities

### New Capabilities
- `automatisierungsvorschlaege`: Vorschläge aus Meldungen mit Bestätigung durch den Menschen.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `lagekarte`, die Tafeln, `rapport-lagerapport`.
- Offene Fragen: Wie die Vorschläge technisch entstehen (regelbasiert oder mit KI), das gehört ins Design. Im Prototyp reicht eine nachvollziehbare Simulation.
