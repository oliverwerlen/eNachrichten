## Why

Jede Funktion soll im System ihre zugewiesenen Meldungen sehen, bearbeiten und erledigen können. Eine Reaktion darauf führt, wo sie inhaltlich ist, zu einer neuen Meldung, die denselben Fluss durchläuft.

## What Changes

- Postfach pro Funktion mit zugewiesenen und selbst erfassten Meldungen, Frist und Status.
- Statuswechsel (neu, gelesen, in Arbeit) erzeugen keine Meldung.
- Reaktionen: quittieren ("ok", reine Kenntnisnahme, keine Meldung), Rückfrage stellen (neue Meldung), abschliessen ("erledigt", erzeugt eine Abschlussmeldung).
- Antworten auf eine Meldung sind möglich.
- Neue Meldungen aus Reaktionen verweisen auf die Ursprungsmeldung und durchlaufen die Triage.

## Capabilities

### New Capabilities
- `postfach-und-reaktionen`: Postfach, Statuslauf, Quittieren, Rückfrage, Antwort, Abschluss.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `funktionen-und-sichtrechte`.
- Verbindet sich mit `meldungskette-nachvollziehbarkeit` und `fristueberwachung`.
- Offene Fragen: Bedeutung von "ok" und "erledigt" (Annahme: "ok" ist Kenntnisnahme ohne Meldung, "erledigt" entspricht "abgeschlossen" und erzeugt die Abschlussmeldung).
