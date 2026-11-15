## Why

Zwei Tafeln der Führungswand führen Zahlen: die Evakuationen (Personen pro Ort und Zeit) und der Verpflegungsbestand pro Formation. Die Personenzahlen speisen auch die Personenübersicht auf der Karte.

## What Changes

- Tafel Evakuationen: Zeit, Ort/Sektor, Patienten, Obdachlose, Evakuierte, Vermisste, Tote, Andere.
- Tafel Verpflegung: Bestand pro Formation/Einheit (Führungsstab, Polizei, Feuerwehr, Sanität, Techn. Dienste, Zivilschutz, Armee, Obdachlose) mit automatischem Total.
- Zahlen werden aus Meldungen vorgeschlagen, vorausgefüllt und anpassbar.
- Jede Zeile verweist auf die Ursprungsmeldung.
- Verknüpfung der Personenzahlen mit der Karte.

## Capabilities

### New Capabilities
- `tafeln-zaehltafeln`: Evakuationen und Verpflegung mit Zahlen pro Ort/Zeit beziehungsweise pro Formation.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `meldungskette-nachvollziehbarkeit`.
- Verwandt: `lagekarte`, `logistik-uebersicht`, `rapport-lagerapport`.
- Offene Fragen: Was in den Zeilen der Verpflegungstafel steht (Annahme: Verpflegungsarten, zu bestätigen). Datenschutz bei Personendaten, nur Zahlen oder auch Namen (Annahme: nur Zahlen).
