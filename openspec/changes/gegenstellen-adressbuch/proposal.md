## Why

Der Führungsstab arbeitet mit externen Organisationen zusammen: Kantonales Führungsorgan (C RFO), Polizei, Feuerwehr, Sanität, Zivilschutz, Technischer Betrieb und bei Bedarf Armee, Nachbarregionen und Medien. Sie sind Absender und Empfänger von Meldungen, aber keine Benutzer des Systems. Das Tool ist hauptsächlich intern.

## What Changes

- Ein Adressbuch externer Gegenstellen mit Organisation, Kontaktpersonen und erreichbaren Kanälen.
- Gegenstellen sind als Absender und Empfänger in Meldungen und als Antragsteller, Beauftragte oder Bereitsteller in Tafeln wählbar.
- Gegenstellen haben keine Anmeldung und kein Postfach.
- Nicht im Umfang: ein Portal oder Zugang für externe Organisationen.

## Capabilities

### New Capabilities
- `gegenstellen-adressbuch`: Verwaltung externer Gegenstellen mit Kontakt und Kanal, Auswahl in Meldungen und Tafeln.

### Modified Capabilities
<!-- keine -->

## Impact

- Wird von `meldung-erfassen`, `meldung-triage-verteilung`, `tafeln-vorgangslisten` und `tafeln-ressourcen` verwendet.
- Abhängigkeiten: `ereignis-verwaltung` (optional, Gegenstellen können ereignisübergreifend gelten).
- Offene Fragen: Gelten Gegenstellen ereignisübergreifend oder pro Ereignis? Annahme: ereignisübergreifend, mit Möglichkeit, sie pro Ereignis auszublenden.
