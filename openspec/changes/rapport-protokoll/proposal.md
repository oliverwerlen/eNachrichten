## Why

Die Kanzlei führt die Protokolle des Stabes. Aus jedem Rapport entstehen Beschlüsse, Aufträge und Anträge, die festgehalten und nachvollziehbar sein müssen.

## What Changes

- Rapportprotokoll zu jedem Lager- und Inforapport.
- Protokolleinträge pro Traktandum werden vorgeschlagen und von der Kanzlei bestätigt.
- Beschlüsse und Aufträge im Protokoll verweisen auf die daraus entstandenen Meldungen.
- Das Protokoll ist unveränderlich nach Abschluss. Korrekturen sind neue Fassungen.
- Die Kanzlei sieht das Protokoll als ihr zugewiesene Aufgabe.

## Capabilities

### New Capabilities
- `rapport-protokoll`: Protokoll der Rapporte durch die Kanzlei mit Verweisen auf Beschlüsse und Meldungen.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `rapport-lagerapport`, `rapport-inforapport`, `postfach-und-reaktionen`.
- Offene Fragen: Soll die Kanzlei im Rapport mitschreiben können, ohne die Lagepräsentation zu sehen, oder bekommt sie das Protokoll nur als Aufgabe (Annahme: nur als Aufgabe mit Zugriff auf das Protokoll).
