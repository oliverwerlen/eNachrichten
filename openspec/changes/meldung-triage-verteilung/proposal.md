## Why

Jede Meldung, auch von Funktionen im Stab, geht durch die Triage des Chefs Nachrichtendienst. Dort wird entschieden, wie dringend sie ist und wer sie erhält. Das ist die Schleuse, die den einheitlichen, nachvollziehbaren Fluss sicherstellt.

## What Changes

- Triage durch den Chef Nachrichtendienst: Einstufung als Schlüsselnachricht (dringend) oder Rohinformation/Nachricht.
- Jede neue Meldung wird frisch eingestuft, auch Folgemeldungen.
- Optionale Bewertung von Quelle und Information.
- Verteilung (Kopie an): interne Funktionen (Postfach) und externe Gegenstellen (Versand ausserhalb des Systems).
- Bei externen Empfängern trägt die Funktion Versand und Bestätigung von Hand ein.
- Ablagehinweise: Journal, Karte, Tafeln, Kontrolle, die der Chef bei der Triage anstösst.
- Warteschlange der unbearbeiteten Meldungen, nach Dringlichkeit und Alter sortiert.

## Capabilities

### New Capabilities
- `meldung-triage-verteilung`: Einstufung, optionale Bewertung, Verteilung an interne und externe Empfänger, Warteschlange.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `funktionen-und-sichtrechte`, `gegenstellen-adressbuch`.
- Wird von `postfach-und-reaktionen`, `ei-journal`, den Tafeln und der Karte genutzt.
- Offene Fragen: Wer vertritt den Chef Nachrichtendienst bei Abwesenheit (Annahme: Zuweisung der Funktion pro Ereignis). Ob "Tabellen" und "Kontrolle" auf dem Meldezettel die Wandtafeln meinen (Annahme: ja).
