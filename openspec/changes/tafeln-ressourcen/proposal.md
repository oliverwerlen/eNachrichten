## Why

Der Führungsstab muss wissen, welche Mittel verfügbar und welche eingesetzt sind. Zwei Tafeln der Führungswand bilden das ab. Mittel wechseln zwischen beiden Zuständen und sind meist Mittel externer Organisationen.

## What Changes

- Tafel Verfügbare Mittel: Organisation, Kontaktperson, Mittel (personell, materiell), Ab wann.
- Tafel Eingesetzte Mittel: Organisation, Einsatzort, Mittel (personell, materiell), Bis wann.
- Übergang von verfügbar zu eingesetzt (und zurück) über Aufträge und Rückmeldungen, als bestätigter Vorschlag.
- Einträge aus Meldungen vorausgefüllt und anpassbar.
- Organisationen aus dem Adressbuch der Gegenstellen.
- Jede Zeile verweist auf die Ursprungsmeldung.

## Capabilities

### New Capabilities
- `tafeln-ressourcen`: Verfügbare Mittel, Eingesetzte Mittel und ihr Übergang.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `gegenstellen-adressbuch`, `meldungskette-nachvollziehbarkeit`.
- Wird von `logistik-uebersicht` und `rapport-lagerapport` genutzt.
- Offene Fragen: Mengenangaben bei Personal und Material (Annahme: Zahl plus Bezeichnung). Wie werden Teilmengen bei einem Einsatz abgebildet (Annahme: Aufteilung der Zeile).
