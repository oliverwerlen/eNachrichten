## Why

Meldungen, besonders per Funk oder Telefon, sind oft schwer verständlich: Abkürzungen, unvollständige Sätze, Mundart, widersprüchliche Angaben. Das erschwert Triage und Weiterverarbeitung und führt zu Rückfragen und Fehleinstufungen. Eine KI soll Verständlichkeit herstellen helfen, ohne die Originalmeldung anzutasten.

## What Changes

- Die KI erkennt unklare, unvollständige oder widersprüchliche Stellen einer Meldung und markiert sie.
- Sie schlägt eine verständliche Fassung vor und befüllt das Frageschema (Wann, Wer, Tut was, Wie, Wo, Umwelt) aus dem Freitext vor.
- Sie schlägt bei Lücken Rückfragen vor, die als Meldung vom Typ Anfrage erfasst werden können.
- Die Originalmeldung bleibt unverändert erhalten. Eine Korrektur entsteht nur als neue Fassung nach Bestätigung durch eine berechtigte Funktion.
- Die Einstufung als Schlüsselnachricht oder Rohinformation bleibt beim Chef Nachrichtendienst, die KI schlägt sie nur vor (siehe `automatisierungsvorschlaege`).
- Alle Vorschläge nennen Herkunft und Begründung und werden protokolliert.

## Capabilities

### New Capabilities
- `ki-meldungsklaerung`: KI-Vorschläge zur Verständlichkeit von Meldungen: Markierung unklarer Stellen, verständliche Fassung, Frageschema-Vorbelegung und Rückfragevorschläge.

### Modified Capabilities
<!-- keine, siehe Hinweis in Impact -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `postfach-und-reaktionen`, `meldungskette-nachvollziehbarkeit`, `automatisierungsvorschlaege`.
- Ergänzt `automatisierungsvorschlaege`, ohne diese Spec zu ändern, weil sie noch ein offener Change ist.
- Offene Fragen: Wo läuft die KI und wohin gehen die Daten (Meldungen enthalten sensible Angaben, Anforderung: Betrieb in der Schweiz oder lokal, zu klären). Wer darf eine verständliche Fassung bestätigen (Annahme: der Meldungsverfasser oder der Chef Nachrichtendienst). Wie wird mit sehr dringenden Meldungen umgegangen (Annahme: die Vorschläge verzögern die Triage nicht). Welche Sprachen und Dialekte sind zu berücksichtigen (Annahme: Deutsch inklusive Walliser Ausdrücke, zu bestätigen).
