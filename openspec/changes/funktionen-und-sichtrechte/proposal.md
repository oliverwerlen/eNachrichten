## Why

Im Regionalen Führungsstab Lötschental übernehmen feste Funktionen unterschiedliche Aufgaben. Jede Funktion soll im System sehen und tun können, was zu ihrer Rolle gehört. Ohne klare Funktionen und Sichtrechte lassen sich Postfächer, Triage und Rapportzugang nicht festlegen.

## What Changes

- Neun interne Funktionen: Chef Nachrichtendienst, Mitarbeitende Nachrichtendienst, C Lage, Adjutant, SC (Stabschef), C Info, Einsatz, Infrastruktur/Logistik, Kanzlei.
- Funktionen werden pro Ereignis Personen zugewiesen. Eine Person kann mehrere Funktionen halten, und Zuweisungen sind änderbar (Schichtwechsel, Stellvertretung).
- Sichtrechte: Chef ND, C Lage, Adjutant und SC sehen alle Meldungen des Ereignisses. Die übrigen Funktionen sehen nur zugewiesene und eigene Meldungen.
- Zugang zum Rapportmodus (Lagepräsentation, Inforapport-Übersicht) haben Chef ND, C Lage, Adjutant und SC.
- Jede interne Funktion kann Meldungen erfassen, über eine eigene Oberfläche.
- Externe Organisationen sind keine Funktionen und haben keinen Zugang (siehe `gegenstellen-adressbuch`).

## Capabilities

### New Capabilities
- `funktionen-und-sichtrechte`: Funktionskatalog, Zuweisung pro Ereignis, Sichtrechte, Rapportzugang, funktionsspezifische Oberflächen.

### Modified Capabilities
<!-- keine -->

## Impact

- Grundlage für `postfach-und-reaktionen`, `lage-ueberblick` und alle `rapport-*`-Changes.
- Abhängigkeiten: `ereignis-verwaltung`.
- Offene Fragen: Rechte, Tafeln und Karte zu ändern, ausser beim Nachrichtendienst. Zugriff der Kanzlei auf das Rapportprotokoll (siehe `rapport-protokoll`). Bedeutung der Abkürzung "Chef Lage" gegenüber "Chef Nachrichtendienst" (kann dieselbe Person sein).
- Hinweis zum Datenschutz: Personendaten zu Vermissten, Verletzten und Toten erfordern nach Funktion geregelte Sichtbarkeit.
