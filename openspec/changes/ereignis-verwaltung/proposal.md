## Why

Der Regionale Führungsstab Lötschental (RFS) braucht eine einheitliche, nachvollziehbare Abbildung der Tätigkeiten des Nachrichtendienstes. Alle Meldungen, Tafeln, Karten und Rapporte beziehen sich auf ein konkretes Ereignis. Ohne Ereignisse als oberste Ordnungsebene lassen sich Daten nicht trennen, archivieren oder nach einem Einsatz auswerten.

## What Changes

- Einführung des Ereignisses als oberste Ebene. Jede Meldung gehört zu genau einem Ereignis. Journal, Tafeln, Karte, Postfächer, Zeitplanung und Rapporte hängen am Ereignis.
- Genau ein Ereignis ist vorausgewählt (aktiv). In der Regel ist nur ein Ereignis aktiv.
- Nicht aktive Ereignisse dienen der Archivierung und sind nur lesbar.
- Das aktive Ereignis ist in jeder Ansicht sichtbar, damit keine Meldung im falschen Ereignis erfasst wird.

## Capabilities

### New Capabilities
- `ereignis-verwaltung`: Ereignisse anlegen, aktivieren, archivieren; Zuordnung aller Daten zu genau einem Ereignis.

### Modified Capabilities
<!-- keine -->

## Impact

- Grundlage für alle weiteren Changes. Jede Spec setzt ein gewähltes Ereignis voraus.
- Abhängigkeiten: keine.
- Offene Fragen: Dürfen mehrere Ereignisse gleichzeitig aktiv sein? Ausgangslage: in der Regel eines, parallele sind möglich. Wie wird eine versehentlich falsch zugeordnete Meldung korrigiert (Verschieben als protokollierte Korrektur, siehe `meldungskette-nachvollziehbarkeit`)?
