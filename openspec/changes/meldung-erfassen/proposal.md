## Why

Der Meldezettel ist die zentrale Arbeitseinheit des Führungsstabs. Heute wird er von Hand geführt. Das System soll denselben Inhalt einheitlich erfassen, damit alle Ablagen daraus gespeist werden können.

## What Changes

- Digitale Abbildung des Meldezettels: Richtung (Eingang/Ausgang), Absender, Empfänger, Datum, Zeit, Meldungsnummer, Kanal, Meldungstyp, Betreff, Meldungsinhalt, Visum des Meldungsverfassers.
- Kanäle: Telefon, Fax, Funk, Message, E-Mail, Kurier, weitere frei wählbar.
- Meldungstypen: Mitteilung, Nachricht, Anfrage, Antwort, Auftrag, Vollzug, weitere frei wählbar.
- Geführte Erfassung mit dem Frageschema: Wann? Wer? Tut was? Wie? Wo? Wie ist die Umwelt?
- Zwei Zeitangaben: Ereigniszeit und Erfassungszeit.
- Automatische, eindeutige Meldungsnummer. Gespeicherte Meldungen werden nie überschrieben, Korrekturen sind neue Fassungen.
- Alle internen Funktionen können Meldungen erfassen.

## Capabilities

### New Capabilities
- `meldung-erfassen`: Erfassung von Meldungen entsprechend dem Meldezettel, mit Frageschema, Zeiten, Nummerierung und Fassungen.

### Modified Capabilities
<!-- keine -->

## Impact

- Kern des Systems. Alle Folge-Changes setzen die Meldung voraus.
- Abhängigkeiten: `ereignis-verwaltung`, `funktionen-und-sichtrechte`, `gegenstellen-adressbuch`.
- Offene Fragen: Soll das Frageschema Pflicht oder Hilfe sein (Annahme: Hilfe, einzelne Felder sind nicht zwingend). Soll eine Bewertung bei der Erfassung möglich sein (ja, optional, siehe `meldung-triage-verteilung`).
