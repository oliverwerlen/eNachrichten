## Why

Der Nachrichtendienst soll nachvollziehbar arbeiten. Wer eine Aussage in einer Tafel, auf der Karte oder im Rapport sieht, muss zur Quelle zurückfinden und die ganze Entwicklung nachlesen können.

## What Changes

- Jede Folgemeldung verweist auf die Ursprungsmeldung. So entstehen Meldungsketten (Auftrag, Rückfrage, Antwort, Vollzug).
- Kettenansicht pro Meldung mit Verlauf, Einstufung, Verteilung, Reaktionen und Versand.
- Rückverfolgung von jedem abgeleiteten Eintrag (Tafel, Karte, Journal, Rapport) zur Ursprungsmeldung.
- Lückenlose Ereignishistorie: wer, wann, was, woher.
- Korrektur falsch zugeordneter Meldungen als protokolliertes Verschieben.

## Capabilities

### New Capabilities
- `meldungskette-nachvollziehbarkeit`: Verweise zwischen Meldungen, Kettenansicht, Rückverfolgung abgeleiteter Einträge, Historie.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `postfach-und-reaktionen`, `meldung-triage-verteilung`.
- Wird von allen Tafeln, der Karte, dem Journal und dem Rapport genutzt.
- Offene Fragen: Wie werden Ketten abgeschlossen dargestellt (Annahme: Kette gilt als abgeschlossen, wenn die Abschlussmeldung eingestuft ist).
