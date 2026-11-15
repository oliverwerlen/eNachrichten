## Why

Der C Lage muss über Geschehnisse und Meldungen laufend auf dem Laufenden sein. Auch SC und Adjutant sehen alle Meldungen, brauchen aber einen Filter für das, was für sie relevant ist.

## What Changes

- Lage-Überblick für Chef Nachrichtendienst, C Lage, Adjutant und SC: alle Meldungen des Ereignisses im Mitlesen, ohne Postfachpflicht.
- Relevanzfilter, speicherbar, für SC und Adjutant. Der Zugriff auf alles bleibt erhalten.
- Hervorhebung von Schlüsselnachrichten, Überfälligem, offenen Rückfragen und Änderungen auf Karte und Tafeln.
- Änderungen seit dem letzten Rapport als Ausgangspunkt für den Lagerapport.
- Der Adjutant dient als Bindeglied zwischen SC und Nachrichtendienst.

## Capabilities

### New Capabilities
- `lage-ueberblick`: Laufende Gesamtsicht mit Relevanzfilter und Änderungen seit dem letzten Rapport.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `funktionen-und-sichtrechte`, `meldung-triage-verteilung`, `lagekarte`, `tafeln-vorgangslisten`.
- Grundlage für `rapport-lagerapport` und `rapport-inforapport`.
- Offene Fragen: Welche Filterkriterien (Annahme: Einstufung, Thema, Ort, Absender, Funktion, Zeitraum). Soll das System Vorschläge für Relevanz machen (Annahme: ja, die Person entscheidet).
